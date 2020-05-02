---
title: Utiliser PowerShell pour effectuer une migration intermédiaire vers Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Résumé : Découvrez comment utiliser Windows PowerShell pour effectuer une migration intermédiaire vers Office 365.'
ms.openlocfilehash: 846704ff32a8f6e4012e93b67ec2a921d4c9ac51
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004517"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Utiliser PowerShell pour effectuer une migration intermédiaire vers Office 365

Vous pouvez migrer progressivement le contenu des boîtes aux lettres des utilisateurs vers Office 365 à partir d'un système de messagerie source à l'aide d'une migration intermédiaire.
  
Cet article décrit les tâches nécessaires pour effectuer une migration de messagerie intermédiaire à l'aide d'Exchange Online PowerShell. La rubrique [Ce que vous devez savoir sur une migration de messagerie intermédiaire vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487) présente le processus de migration. Une fois familiarisé avec son contenu, reportez-vous au présent article pour migrer des boîtes aux lettres d'un système de messagerie vers un autre.
  
> [!NOTE]
> Vous pouvez également utiliser le Centre d'administration Exchange pour effectuer la migration intermédiaire. Voir [Effectuer une migration intermédiaire de la messagerie vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d'informations sur les autres facteurs affectant la durée de migration des boîtes aux lettres vers Office 365, consultez la rubrique [Performances de migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Des autorisations doivent vous être attribuées que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-staged-migration"></a>Étape 1 : Préparez une migration intermédiaire

Avant de migrer les boîtes aux lettres vers Office 365 en utilisant une migration intermédiaire, vous devez apporter certaines modifications à votre environnement Exchange.
  
 **Configurer Outlook Anywhere sur votre Exchange Server local** Le service de migration de la messagerie utilise Outlook Anywhere (également appelé RPC sur HTTP) pour se connecter à votre Exchange Server local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange Server 2007 et Exchange 2003, consultez les rubriques suivantes :
  
- [Exchange 2007 : Procédure d'activation d'Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Procédure de configuration d'Outlook Anywhere avec Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Vous devez utiliser un certificat émis par une autorité de certification (AC) approuvée pour votre configuration Outlook Anywhere. Outlook Anywhere ne peut pas être configuré avec un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Facultatif : vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :
  
- Utilisez Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.
    
- Utilisez l' [Analyseur de connectivité à distance Microsoft](https://https://testconnectivity.microsoft.com/) pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.
    
- Dans Exchange Online PowerShell, exécutez les commandes suivantes :
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Définir des autorisations** Le compte d'utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange locale (également appelé administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous voulez migrer vers Office 365. Ce compte est utilisé lorsque vous vous connectez à votre système de messagerie en créant le point de terminaison de la migration (voir plus bas dans la procédure,[Étape 3 : Créez un point de terminaison de migration](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).
  
Pour migrer les boîtes aux lettres, l’administrateur doit disposer de l’un des jeux d’autorisations suivants :
  
- Être membre du groupe **Administrateurs du domaine** dans Active Directory au sein de l'organisation locale.
    
    ou
    
- Disposer de l'autorisation **Accès total** pour chaque boîte aux lettres locale et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur les comptes des utilisateurs locaux.
    
    ou
    
- Disposer de l'autorisation **Recevoir en tant que** sur la base de données de boîtes aux lettres locale qui contient les boîtes aux lettres utilisateur et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur le compte d'utilisateur local.
    
Pour des instructions sur la définition de ces autorisations, voir [Attribution d'autorisations pour la migration de boîtes aux lettres vers Exchange Online](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Désactiver la messagerie unifiée (MU)** Si la messagerie unifiée est activée pour les boîtes aux lettres locales que vous migrez, désactivez-la avant la migration. Réactivez-la ensuite pour les boîtes aux lettres une fois la migration terminée. Pour la procédure correspondante, voir[Désactivation d'une messagerie unifiée pour un utilisateur](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Utiliser la synchronisation d'annuaires pour créer de nouveaux utilisateurs dans Office 365** La synchronisation d'annuaires vous permet de créer tous les utilisateurs locaux de votre organisation Office 365.
  
Vous devez attribuer une licence aux utilisateurs créés. Vous disposez pour cela de 30 jours à compter de leur création. Pour la procédure d'ajout de licences, voir [Étape 8 : Exécutez les tâches post-migration](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Vous pouvez utiliser l'outil de synchronisation de Microsoft Azure Active Directory ou Microsoft Azure Active Directory Sync Services (AAD Sync) pour synchroniser et créer vos utilisateurs locaux dans Office 365. Une fois les boîtes aux lettres migrées dans Office 365, vous pouvez gérer les comptes d'utilisateurs dans votre organisation locale et ceux-ci sont synchronisés avec votre organisation Office 365. Pour plus d'informations, voir [Intégration d'annuaire](https://go.microsoft.com/fwlink/?LinkId=521788).
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration intermédiaire

Après avoir identifié les utilisateurs dont vous souhaitez migrer les boîtes aux lettres locales vers Office 365, vous devez utiliser un fichier de valeurs séparées par des virgules (CSV) pour créer un lot de migration. Chaque ligne du fichier CSV (utilisé par Office 365 pour effectuer la migration) contient des informations sur une boîte aux lettres locale. 
  
> [!NOTE]
> Il n'existe aucune limite au nombre de boîtes aux lettres que vous pouvez migrer vers Office 365 lors d'une migration intermédiaire. Le fichier CSV d'un lot de migration peut contenir au maximum 2 000 lignes. Pour migrer plus de 2 000 boîtes aux lettres, vous devez créer des fichiers CSV supplémentaires et les utiliser pour créer de nouveaux lots de migration. 
  
 **Attributs pris en charge**
  
Le fichier CSV destiné à une migration intermédiaire prend en charge les trois attributs suivants. Chaque ligne du fichier CSV correspond à une boîte aux lettres et doit contenir une valeur pour chacun des attributs ci-dessous.
  
|**Attribut**|**Description**|**Requis ?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Permet de définir l’adresse de messagerie SMTP principale, par exemple pilarp@contoso.com, pour les boîtes aux lettres locales.  <br/> Utilisez bien lʼadresse SMTP principale des boîtes aux lettres locales et non les identifiants utilisateur issus d'Office 365. Par exemple, si le nom de domaine local est contoso.com alors que le nom de domaine de messagerie Office 365 est service.contoso.com, vous devez utiliser le nom de domaine contoso.com pour les adresses de messagerie dans le fichier CSV.  <br/> |Requis  <br/> |
|Mot de passe  <br/> |Mot de passe à définir pour la nouvelle boîte aux lettres Office 365. Toutes les restrictions de mot de passe appliquées à votre organisation Office 365 s'appliquent également aux mots de passe inclus dans le fichier CSV.  <br/> |Facultatif  <br/> |
|ForceChangePassword  <br/> |Permet d'indiquer si les utilisateurs doivent modifier le mot de passe la première fois qu'ils se connectent à leur boîte aux lettres Office 365. Pour ce paramètre, utilisez la valeur **True** ou **False**. <br/> > [!NOTE]> Si vous avez implémenté une solution d'authentification unique (SSO) en déployant Active Directory Federation Services (AD FS) dans votre organisation locale, vous devez utiliser la valeur **False** pour l'attribut **ForceChangePassword**.          |Facultatif  <br/> |
   
 **Format de fichier CSV**
  
Voici un exemple de format pour le fichier CSV. Dans cet exemple, trois boîtes aux lettres locales sont migrées vers Office 365.
  
La première ligne, ou ligne d'en-tête, du fichier CSV répertorie les noms des attributs, ou champs, spécifiés dans les lignes qui suivent. Les noms d'attributs sont séparés par des virgules.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Chaque ligne sous la ligne d’en-tête représente un utilisateur et fournit les informations qui seront utilisées pour migrer la boîte aux lettres de l’utilisateur. Les valeurs d’attribut de chaque ligne doivent respecter l’ordre des noms d’attribut dans la ligne d’en-tête. 
  
Pour créer le fichier CSV, utilisez un éditeur de texte ou une application telle qu’Excel. Enregistrez le fichier au format .csv ou .txt.
  
> [!NOTE]
> Si le fichier CSV contient des caractères non ASCII ou des caractères spéciaux, enregistrez-le avec l’encodage UTF-8 ou un autre encodage Unicode. Selon l’application, l’enregistrement du fichier CSV avec l’encodage UTF-8 ou un autre encodage Unicode peut être facilité lorsque les paramètres régionaux système de l’ordinateur correspondent à la langue utilisée dans le fichier CSV. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Étape 3 : Créez un point de terminaison de migration
<a name="BK_Endpoint"> </a>

Pour que la migration fonctionne, Office 365 doit pouvoir se connecter au système de messagerie source et communiquer avec lui. Pour ce faire, Office 365 utilise un point de terminaison. Pour créer un point de terminaison de migration Outlook Anywhere à l'aide de PowerShell, afin d'effectuer une migration intermédiaire, commencez par vous [connecter à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Pour créer un point de terminaison de migration Outlook Anywhere appelé « StagedEndpoint » dans Exchange Online PowerShell, exécutez les commandes suivantes :
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.
  
#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « StagedEndpoint » :
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Étape 4 : Créez et démarrez un lot de migration intermédiaire
<a name="BK_Endpoint"> </a>

La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Cet exemple de code crée également un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'une seule lot de migration à basculement à la fois.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « StagedBatch1 » :
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Étape 5 : Convertissez des boîtes aux lettres locales en utilisateurs à extension messagerie
<a name="BK_Endpoint"> </a>

Une fois la migration d'un premier lot effectuée, vous devez permettre aux utilisateurs d'accéder à leur messagerie. Un utilisateur dont la boîte aux lettres a été migrée dispose de deux boîtes aux lettres : une en local et une autre dans Office 365. Les utilisateurs ayant une boîte aux lettres dans Office 365 ne reçoivent plus de messages dans leur boîte aux lettres locale. 
  
Toutes les migrations n'ayant pas encore été effectuées, vous ne pouvez pas encore rediriger l'ensemble des utilisateurs vers Office 365 pour qu'ils accèdent à leur messagerie électronique. Que faire alors pour les personnes qui disposent de deux boîtes aux lettres ? Eh bien vous pouvez convertir les boîtes aux lettres qui ont déjà été migrées en utilisateurs à extension messagerie. Cette opération vous permet de rediriger l'utilisateur pour qu'il puisse accéder à sa messagerie dans Office 365, et non plus en local. 
  
Une autre raison importante justifiant la conversion des boîtes aux lettres locales en utilisateurs à extension messagerie est que cette opération permet de conserver les adresses proxy des boîtes aux lettres Office 365 en les copiant vers les utilisateurs à extension messagerie. Cela vous permet de gérer des utilisateurs en nuage à partir de votre organisation locale à l'aide d'Active Directory. De plus, si vous décidez de mettre hors service votre organisation Exchange Server locale une fois toutes les boîtes aux lettres migrées vers Office 365, les adresses proxy que vous avez copiées vers les utilisateurs à extension messagerie sont conservées dans votre instance Active Directory locale.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Étape 6 : Supprimez un lot de migration intermédiaire
<a name="BK_Endpoint"> </a>

 Après avoir migré toutes les boîtes aux lettres d'un lot de migration et converti les boîtes aux lettres locales du lot en utilisateurs à extension messagerie, vous êtes prêt à supprimer un lot de migration intermédiaire. Vérifiez que le courrier électronique est transféré aux boîtes aux lettres Office 365 du lot de migration. Lorsque vous supprimez un lot de migration intermédiaire, le service de migration nettoie tous les enregistrements associés au lot de migration, puis supprime ce dernier.
  
Pour supprimer le lot de migration « StagedBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous.
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :
  
```powershell
Get-MigrationBatch StagedBatch1
```

La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.
  
Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Étape 7 : Attribuez des licences aux utilisateurs Office 365
<a name="BK_Endpoint"> </a>

Pour activer les comptes d'utilisateur Office 365 correspondant aux comptes migrés, vous devez leur attribuer des licences. Si vous n’attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour savoir comment attribuer une licence dans le Centre d'administration Microsoft 365, voir [Attribuer ou retirer des licences pour Office 365 pour les entreprises](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration
<a name="BK_Postmigration"> </a>

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres**Une fois toutes les boîtes aux lettres locales migrées vers Office 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Office 365 afin de permettre aux utilisateurs de se connecter aisément à leurs nouvelles boîtes aux lettres Office 365 avec des clients mobiles et Outlook. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui de votre organisation Office 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l'enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.
    
    Office 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients mobiles et Outlook. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :
    
  - **Alias :** autodiscover
    
  - **Cible :** autodiscover.outlook.com
    
    Pour plus d'informations, voir [Créer des enregistrements DNS pour Office 365 lors de la gestion de vos enregistrements DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Désactiver des serveurs Exchange locaux** Après avoir vérifié que tout le courrier est acheminé directement vers les boîtes aux lettres Office 365, si vous n'avez plus besoin de conserver votre organisation de messagerie locale ou que vous ne comptez pas implémenter de solution SSO, vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.
    
    Pour plus d’informations, voir les commandes suivantes :
    
  - [Modifier ou supprimer Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Procédure de suppression d'une organisation Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Procédure de désinstallation d'Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

