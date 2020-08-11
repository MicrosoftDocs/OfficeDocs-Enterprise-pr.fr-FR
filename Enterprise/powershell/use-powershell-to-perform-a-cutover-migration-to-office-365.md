---
title: Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Découvrez comment utiliser PowerShell pour déplacer le contenu d’un système de courrier source en une seule fois en effectuant une migration à basculement vers Microsoft 365.
ms.openlocfilehash: fde0795b767f908fb0d1dcc5ce17a0bb50235d8e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606220"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez migrer le contenu des boîtes aux lettres utilisateur à partir d’un système de messagerie source vers Microsoft 365 en une seule fois à l’aide d’une migration à basculement. Cet article décrit les tâches correspondant à une migration de messagerie à basculement à l'aide d'Exchange Online PowerShell. 
  
En examinant la rubrique, [ce que vous devez savoir sur une migration de courrier à basculement vers Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), vous pouvez obtenir une vue d’ensemble du processus de migration. Lorsque le contenu de cet article vous est familier, utilisez celui-ci pour commencer la migration de boîtes aux lettres d'un système à l'autre.
  
> [!NOTE]
> Vous pouvez également utiliser le Centre d'administration Exchange pour effectuer la migration à basculement. Voir [effectuer une migration à basculement de la messagerie vers Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur les autres facteurs qui influent sur la durée de migration des boîtes aux lettres vers Microsoft 365, consultez la rubrique performance de la [migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-cutover-migration"></a>Étape 1 : Préparez une migration à basculement
<a name="BK_Step1"> </a>

- **Ajoutez votre organisation Exchange locale en tant que domaine accepté de votre organisation Microsoft 365.** Le service de migration utilise l’adresse SMTP de vos boîtes aux lettres locales pour créer l’ID d’utilisateur et l’adresse de messagerie Microsoft Online Services pour les nouvelles boîtes aux lettres Microsoft 365. La migration échoue si votre domaine Exchange n’est pas un domaine accepté ou le domaine principal de votre organisation Microsoft 365. Pour plus d’informations, consultez [la rubrique Verify Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configurez Outlook Anywhere sur votre serveur Exchange local** Le service de migration de messagerie utilise RPC sur HTTP ou Outlook Anywhere pour se connecter à votre serveur Exchange local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange 2010, 2007 et 2003, consultez les rubriques suivantes :
    
  - [Exchange 2010 : Activer Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007 : Procédure d'activation d'Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003 : Scénarios de déploiement RPC sur HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Procédure de configuration d'Outlook Anywhere avec Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > La configuration d'Outlook Anywhere doit être réalisée à l'aide d'un certificat émis par une autorité de certification (CA) approuvée. Il ne peut être configuré à l'aide d'un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :
    
  - Utilisez Microsoft Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.
    
  - Utilisez l'[analyseur de connectivité à distance Exchange](https://www.testexchangeconnectivity.com/) de Microsoft pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.
    
  - Dans Exchange Online PowerShell, exécutez les commandes suivantes.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Attribuez à un compte d'utilisateur local les autorisations nécessaires pour accéder aux boîtes aux lettres de votre organisation Exchange.** Le compte d’utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange locale (également appelé administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous souhaitez migrer vers Microsoft 365. Ce compte d'utilisateur permet de créer un point de terminaison de migration pour votre organisation locale.
    
    La liste suivante montre les privilèges administratifs requis pour migrer des boîtes aux lettres à l'aide d'une migration à basculement. Trois options sont possibles.
    
  - L'administrateur de migration doit être membre du groupe **Administrateurs de domaine** dans Active Directory au sein de l'organisation locale.
    
    Ou
    
  - L'administrateur de migration doit disposer de l'autorisation **FullAccess** pour chaque boîte aux lettres locale.
    
    Ou
    
  - L'administrateur de migration doit disposer de l'autorisation **Receive As** pour la base de données de boîtes aux lettres locale stockant les boîtes aux lettres d'utilisateurs.
    
- **Désactivez la messagerie unifiée.** Si les boîtes aux lettres locales que vous migrez sont activées pour la messagerie unifiée, vous devez désactiver cette dernière avant de procéder à la migration. Une fois la migration terminée, vous pouvez activer la messagerie unifiée sur les boîtes aux lettres.
    
- **Groupes de sécurité et délégués** Le service de migration de messagerie ne peut pas détecter si les groupes Active Directory sur site sont des groupes de sécurité ou non, et donc ne peuvent pas mettre en service les groupes migrés en tant que groupes de sécurité dans Microsoft 365. Si vous souhaitez avoir des groupes de sécurité dans votre client Microsoft 365, vous devez d’abord configurer un groupe de sécurité à extension messagerie vide dans votre client Microsoft 365 avant de commencer la migration à basculement. En outre, cette méthode de migration déplace uniquement les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie et les groupes à extension messagerie. Si un autre objet Active Directory, tel qu’un utilisateur qui n’est pas migré vers Microsoft 365, est affecté en tant que gestionnaire ou délégué à un objet en cours de migration, il doit être supprimé de l’objet avant la migration.
    
### <a name="step-2-create-a-migration-endpoint"></a>Étape 2 : Créez un point de terminaison de migration
<a name="BK_Step2"> </a>

Pour migrer le courrier électronique correctement, Microsoft 365 doit se connecter au système de courrier source et communiquer avec celui-ci. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Pour créer un point de terminaison de migration Outlook Anywhere, afin d'effectuer une migration à basculement, commencez par vous [connecter à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Dans Exchange Online PowerShell, exécutez les commandes suivantes :
  
```
$Credentials = Get-Credential
```

Cet exemple utilise la cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) pour obtenir et tester les paramètres de connexion au serveur Exchange local, puis utilise ces paramètres de connexion pour créer le point de terminaison de migration appelé « CutoverEndpoint ».
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.
  
#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « CutoverEndpoint » :
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Étape 3 : Créez le lot de migration à basculement
<a name="BK_Step3"> </a>

La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

Cet exemple de code crée également un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'un seul lot de migration à basculement à la fois.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Pour vérifier que vous avez créé un lot de migration pour une migration à basculement, exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le nouveau lot de migration :
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Étape 4 : Démarrez le lot de migration à basculement
<a name="BK_Step4"> </a>

Pour lancer le lot de migration dans Exchange Online PowerShell, exécutez la commande suivante. Cela crée un lot de migration appelé « CutoverBatch ».
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Si le traitement d’un lot de migration a démarré, son état dans le tableau de bord de migration est Synchronisation. Pour vérifier que le traitement d’un lot de migration a commencé à l’aide d’Exchange Online PowerShell, exécutez la commande suivante :
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Étape 5 : acheminer votre courrier électronique vers Microsoft 365
<a name="BK_Step5"> </a>

Les systèmes de messagerie utilisent un enregistrement DNS appelé enregistrement MX pour identifier l'emplacement de remise des messages électroniques. Pendant le processus de migration de la messagerie, votre enregistrement MX pointe vers votre système de messagerie source. Une fois la migration de la messagerie vers Microsoft 365 terminée, il est temps de faire pointer votre enregistrement MX sur Microsoft 365. Cela permet de s’assurer que le courrier électronique est remis à vos boîtes aux lettres Microsoft 365. En déplaçant l'enregistrement MX, vous pouvez également désactiver votre ancien système de messagerie lorsque vous êtes prêt. 
  
Pour plusieurs fournisseurs DNS, il existe des instructions spécifiques pour [modifier votre enregistrement MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Si votre fournisseur DNS n'est pas inclus, ou si vous souhaitez avoir une idée des instructions générales, vous avez également accès à des [instructions générales sur les enregistrements MX](https://go.microsoft.com/fwlink/?LinkId=397449).
  
Il faut compter jusqu'à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l'enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : [Étape 6 : Supprimez le lot de migration à basculement](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Étape 6 : Supprimez le lot de migration à basculement
<a name="Bk_step6"> </a>

Une fois que vous avez modifié l’enregistrement MX et vérifié que tous les messages sont acheminés vers les boîtes aux lettres Microsoft 365, informez-les aux utilisateurs que leur courrier va vers Microsoft 365. Après cela, vous pouvez supprimer le lot de migration à basculement. Avant de supprimer le lot de migration, vérifiez les points suivants.
  
- Tous les utilisateurs utilisent des boîtes aux lettres Microsoft 365. Après la suppression du lot, les messages envoyés à des boîtes aux lettres sur le serveur Exchange local ne sont pas copiés dans les boîtes aux lettres Microsoft 365 correspondantes.
    
- Les boîtes aux lettres Microsoft 365 ont été synchronisées au moins une fois après leur envoi direct par le courrier. Pour ce faire, assurez-vous que la valeur de la zone heure de la dernière synchronisation du lot de migration est plus récente que celle de l’envoi de messages démarré directement aux boîtes aux lettres Microsoft 365.
    
Pour supprimer le lot de migration « CutoverBatch » dans Exchange Online PowerShell, exécutez la commande suivante :
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Section 7 : Attribuez des licences utilisateur
<a name="BK_Step7"> </a>

 **Activez les comptes d’utilisateur Microsoft 365 pour les comptes migrés en affectant des licences.** Si vous n'attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour attribuer une licence dans le centre d’administration 365 de Microsoft, consultez la rubrique [attribuer ou](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)supprimer l’attribution des licences.
  
### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration
<a name="BK_Step8"> </a>

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres** Une fois que toutes les boîtes aux lettres locales sont migrées vers Microsoft 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Microsoft 365 afin de permettre aux utilisateurs de se connecter facilement à leurs nouvelles boîtes aux lettres Microsoft 365 avec Outlook et les clients mobiles. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui que vous utilisez pour votre organisation Microsoft 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l’enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.
    
    Si vous conservez votre serveur Exchange, vous devez également vous assurer que l’enregistrement CNAMe DNS de découverte automatique doit pointer vers Microsoft 365 dans le DNS interne et externe après la migration afin que le client Outlook se connecte à la boîte aux lettres appropriée.
    
    > [!NOTE]
    >  Dans Exchange 2007, Exchange 2010 et Exchange 2013, vous devez également définir  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` sur `Null`. 
  
    Microsoft 365 utilise un enregistrement CNAMe pour implémenter le service de découverte automatique pour les clients Outlook et mobiles. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :
    
  - **Alias :** autodiscover
    
  - **Cible :** autodiscover.outlook.com
    
    Pour plus d’informations, reportez-vous [à la rubrique ajouter des enregistrements DNS pour connecter votre domaine](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Désactivez des serveurs Exchange locaux.** Une fois que vous avez vérifié que tous les courriers électroniques sont acheminés directement vers les boîtes aux lettres Microsoft 365, et que vous n’avez plus besoin de conserver votre organisation de messagerie locale ou si vous ne prévoyez pas d’implémenter une solution d’authentification unique (SSO), vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.
    
    Pour plus d’informations, voir les commandes suivantes :
    
  - [Modifier ou supprimer Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Procédure de suppression d'une organisation Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Procédure de désinstallation d'Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

