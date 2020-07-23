---
title: Utiliser PowerShell pour effectuer une migration IMAP vers Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 'Résumé : Découvrez comment utiliser Windows PowerShell pour effectuer une migration IMAP vers Microsoft 365.'
ms.openlocfilehash: fa53fd1829121bb697277805e4f07d25ec2179b9
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229770"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Utiliser PowerShell pour effectuer une migration IMAP vers Microsoft 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Dans le cadre du déploiement de Microsoft 365, vous pouvez choisir de migrer le contenu des boîtes aux lettres utilisateur à partir d’un service de messagerie IMAP (Internet Mail Access Protocol) vers Microsoft 365. Cet article vous guide tout au long des tâches relatives à la migration IMAP de courrier électronique à l’aide d’Exchange Online PowerShell. 
  
> [!NOTE]
> Vous pouvez également utiliser le centre d’administration Exchange pour effectuer une migration IMAP. Voir [migrer vos boîtes aux lettres IMAP](https://go.microsoft.com/fwlink/p/?LinkId=536685). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d’exécution estimée de cette tâche : 2-5 minutes pour créer un lot de migration. Une fois le lot de migration démarré, la durée de la migration varie en fonction du nombre de boîtes aux lettres du lot, de la taille de chaque boîte aux lettres et de la capacité réseau disponible. Pour plus d’informations sur les autres facteurs qui influent sur la durée de migration des boîtes aux lettres vers Microsoft 365, consultez la rubrique performance de la [migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Les migrations IMAP font l'objet des restrictions suivantes :
  
- Vous pouvez migrer uniquement des éléments figurant dans la boîte de réception ou d'autres dossiers de courrier d'un utilisateur. Vous ne pouvez pas migrer des contacts, des éléments du calendrier ou des tâches.
    
- Vous ne pouvez pas migrer plus de 500 000 éléments d'une boîte aux lettres d'utilisateur.
    
- Vous ne pouvez pas non plus migrer des messages d’une taille supérieure à 35 Mo.
    
## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-an-imap-migration"></a>Étape 1 : Préparez une migration IMAP
<a name="BK_Step1"> </a>

- **Si vous disposez d’un domaine pour votre organisation IMAP, ajoutez-le en tant que domaine accepté de votre organisation Microsoft 365.** Si vous souhaitez utiliser le même domaine que vous possédez déjà pour vos boîtes aux lettres Microsoft 365, vous devez d’abord l’ajouter en tant que domaine accepté à Microsoft 365. Une fois que vous l’avez ajouté, vous pouvez créer vos utilisateurs dans Microsoft 365. Pour plus d’informations, consultez[la rubrique Verify Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Ajoutez chaque utilisateur à Microsoft 365 afin qu’ils disposent d’une boîte aux lettres.** Pour obtenir des instructions, consultez la rubrique[Ajouter des utilisateurs à Microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=535065).
    
- **Obtenez le nom de domaine complet (FQDN) du serveur IMAP.** Lorsque vous créez un point de terminaison de migration IMAP, vous devez fournir le nom de domaine complet (FQDN) (également appelénom complet de l'ordinateur) du serveur IMAP à partir duquel vous allez migrer les données de boîte aux lettres. Utilisez un client IMAP ou la commande PING pour vérifier que vous pouvez utiliser le FQDN pour communiquer avec le serveur IMAP sur Internet.
    
- **Configurez le pare-feu pour autoriser les connexions IMAP.** Il se peut que vous deviez ouvrir des portes dans le pare-feu de l'organisation hébergeant le serveur IMAP afin que le trafic réseau en provenance du centre de données Microsoft durant la migration soit autorisé à pénétrer dans l'organisation hébergeant le serveur IMAP. Pour obtenir la liste des adresses IP utilisées par les centres de données Microsoft, consultez la rubrique relative aux[URL Exchange Online et plages d'adresses IP](https://go.microsoft.com/fwlink/p/?LinkId=535066).
    
- **Attribuez les autorisations de compte administrateur pour accéder aux boîtes aux lettres de votre organisation**. Si vous utilisez des informations d'identification d'administrateur dans le fichier CSV, le compte utilisé doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales. Celles-ci sont déterminées par le serveur IMAP spécifique. 
    
- **Pour utiliser les cmdlets Exchange Online PowerShell**, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, consultez la rubrique [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
    
    Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
    
- **Vérifiez que vous pouvez vous connecter à votre serveur IMAP.** Pour tester les paramètres de connexion à votre serveur IMAP, exécutez la commande suivante dans Exchange Online PowerShell.
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    La valeur du paramètre **Port** utilisée est généralement 143 pour les connexions chiffrées ou TLS, et 993 pour les connexions SSL.
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration IMAP
<a name="BK_Step2"> </a>

Identifiez le groupe d'utilisateurs dont vous voulez migrer les boîtes aux lettres dans un lot de migration IMAP. Chaque ligne du fichier CSV contient les informations nécessaires pour se connecter à une boîte aux lettres dans le système de messagerie IMAP.
  
Les attributs obligatoires pour chaque utilisateur sont les suivants : 
  
- **EmailAddress** spécifie l’identifiant utilisateur pour la boîte aux lettres Microsoft 365 de l’utilisateur.
    
- **UserName** spécifie le nom de connexion du compte à utiliser pour accéder à la boîte aux lettres sur le serveur IMAP.
    
- **Password** spécifie le mot de passe du compte dans la colonne UserName **UserName**.
    
Voici un exemple du format du fichier CSV. Dans cet exemple, trois boîtes aux lettres sont migrées :
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

Pour l'attribut **UserName**, en plus du nom d'utilisateur, vous pouvez utiliser les informations d'identification d'un compte disposant des autorisations nécessaires pour accéder à des boîtes aux lettres sur le serveur IMAP. Vous trouverez ci-dessous quelques-uns des formats spécifiques utilisés pour certains serveurs IMAP :
  
 **Microsoft Exchange**
  
Si vous migrez une messagerie à partir de l'implémentation IMAP pour Microsoft Exchange, utilisez le format **Domain/Admin_UserName/User_UserName** pour l'attribut **UserName** dans le fichier CSV. Supposons que vous migrez la messagerie à partir d'Exchange pour Terry Adams, Ann Beebe et Paul Cannon. Vous disposez d'un compte d'administrateur de messagerie dont le nom d'utilisateur est **mailadmin** et le mot de passe est **P@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot**
  
Pour les serveurs IMAP qui prennent en charge Simple Authentication and Security Layer (SASL), comme un serveur IMAP Dovecot, utilisez le format **User_UserName*Admin_UserNam**, où l’astérisque (*) est un caractère de séparation configurable. Supposons que vous migrez les mêmes boîtes aux lettres utilisateur à partir d’un serveur IMAP Dovecot à l’aide des informations d’identification d’administrateur **mailadmin** et **P@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint**
  
Si vous migrez une messagerie à partir d'un serveur de messagerie Mirapoint, utilisez le format **#user@domain#Admin_UserName#** pour les informations d'identification d'administrateur. Pour migrer une messagerie à partir d'un serveur Mirapoint à l'aide des informations d'identification d'administrateur **mailadmin** et **P@ssw0rd**, votre fichier CSV ressemblerait à ceci :
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP :**
  
Certains systèmes de courrier sources, comme Courier IMAP, ne prennent pas en charge l’utilisation des informations d’identification d’administrateur de boîte aux lettres pour migrer des boîtes aux lettres vers Microsoft 365. Au lieu de cela, vous pouvez configurer votre système de courrier source pour utiliser des dossiers partagés virtuels. À l’aide des dossiers partagés virtuels, vous pouvez utiliser les informations d’identification d’administrateur de boîtes aux lettres pour accéder aux boîtes aux lettres utilisateur sur le système de courrier source. Pour plus d’informations sur la configuration des dossiers partagés virtuels pour Courier IMAP, consultez la rubrique [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).
  
Pour migrer des boîtes aux lettres après avoir configuré des dossiers partagés virtuels sur votre système de messagerie source, vous devez inclure l'attribut facultatif **UserRoot** dans le fichier de migration. Cet attribut spécifie l'emplacement de la boîte aux lettres de chaque utilisateur dans la structure de dossiers partagés virtuels sur le système de messagerie source. Par exemple, le chemin d'accès de la boîte aux lettres de Terry est /users/terry.adams.
  
Voici un exemple de fichier CSV contenant l'attribut **UserRoot**:
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Étape 3 : Créez un point de terminaison de migration IMAP
<a name="BK_Step3"> </a>

Pour migrer le courrier électronique correctement, Microsoft 365 doit se connecter au système de courrier source et communiquer avec lui. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Le point de terminaison de migration définit également le nombre de boîtes aux lettres à migrer simultanément et le nombre de boîtes aux lettres à synchroniser simultanément lors de la synchronisation incrémentielle, qui se produit une fois toutes les 24 heures. Pour créer un point de terminaison de migration pour la migration IMAP, [Connectez-vous d’abord à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Pour créer le point de terminaison de migration IMAP appelé « IMAPEndpoint » dans Exchange Online PowerShell, exécutez la commande suivante :
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Vous pouvez également ajouter des paramètres pour spécifier les migrations simultanées, les migrations incrémentielles simultanées et le port à utiliser. La commande Exchange Online PowerShell suivante crée un point de terminaison de migration IMAP appelé « IMAPEndpoint » qui prend en charge 50 migrations simultanées et jusqu'à 25 synchronisations incrémentielles simultanées. Il configure également le point de terminaison pour utiliser le port 143 pour le chiffrement TLS.
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPEndpoint » :
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Étape 4 : Créez et démarrez un lot de migration IMAP
<a name="BK_Step4"> </a>

La cmdlet [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) permet de créer un lot pour une migration IMAP. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer son traitement par la suite à l'aide de la cmdlet [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440).
  
La commande Exchange Online PowerShell suivante démarre automatiquement le lot de migration appelé « IMAPBatch1 » à l’aide du point de terminaison IMAP appelé « IMAPEndpoint » :
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécuter la cmdlet [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) pour afficher des informations sur le lot « IMAPBatch1 » :
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Étape 5 : acheminer votre courrier électronique vers Microsoft 365
<a name="BK_Step5"> </a>

Les systèmes de courrier utilisent un enregistrement DNS appelé enregistrement MX pour déterminer l’emplacement de remise des courriers. Pendant le processus de migration du courrier, votre enregistrement MX pointait vers votre système de courrier source. Une fois la migration de la messagerie vers Microsoft 365 terminée, il est temps de faire pointer votre enregistrement MX sur Microsoft 365. Cela permet de s’assurer que le courrier électronique est remis à vos boîtes aux lettres Microsoft 365. En déplacant l’enregistrement MX, vous pouvez également désactiver votre ancien système de courrier lorsque vous êtes prêt. 
  
Pour de nombreux fournisseurs DNS, il existe des instructions spécifiques pour modifier votre enregistrement MX. Si votre fournisseur DNS n’est pas inclus ou si vous souhaitez obtenir un sens général, les [instructions générales de l’enregistrement MX](https://go.microsoft.com/fwlink/?LinkId=397449) sont également fournies.
  
Il faut compter jusqu’à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l’enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : Étape 6 : Supprimez le lot de migration IMAP 
  
### <a name="step-6-delete-imap-migration-batch"></a>Étape 6 : Supprimez le lot de migration IMAP
<a name="BK_Step6"> </a>

Une fois que vous avez modifié l’enregistrement MX et vérifié que tous les messages sont acheminés vers les boîtes aux lettres Microsoft 365, informez-les aux utilisateurs que leur courrier va vers Microsoft 365. Après cela, vous pouvez supprimer le lot de migration IMAP. Vérifiez ce qui suit avant de supprimer le lot de migration.
  
- Tous les utilisateurs utilisent des boîtes aux lettres Microsoft 365. Après la suppression du lot, les messages envoyés à des boîtes aux lettres sur le serveur Exchange local ne sont pas copiés dans les boîtes aux lettres Microsoft 365 correspondantes.
    
- Les boîtes aux lettres Microsoft 365 ont été synchronisées au moins une fois après leur envoi direct par le courrier. Pour ce faire, assurez-vous que la valeur de la zone heure de la dernière synchronisation du lot de migration est plus récente que celle de l’envoi de messages démarré directement aux boîtes aux lettres Microsoft 365.
    
Pour supprimer le lot de migration « IMAPBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous :
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.
  
Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
## <a name="see-also"></a>Voir aussi

[Utilitaire de dépannage de migration IMAP](https://go.microsoft.com/fwlink/p/?LinkId=536482)

