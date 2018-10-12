---
title: Fonctionnalités multi-localisés dans Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Développez votre présence d’Office 365 à plusieurs régions géographiques avec des capacités multi-localisés dans Exchange Online.
ms.openlocfilehash: aa83b5040cdc98a1c651388fa82d746b852c2313
ms.sourcegitcommit: 5cb4dbdd10ab399af414503cb518a9f530919ef5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "25498224"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Fonctionnalités multi-localisés dans Exchange Online

Fonctionnalités multi-localisés dans Office 365 activer un seul client de couvrir plusieurs emplacements géographiques (zones géographiques). Lorsque Multi-Geo est activée, les clients pouvant sélectionner l’emplacement du contenu des boîtes aux lettres Exchange Online (données au repos) par utilisateur.

Votre emplacement initiale du client (désigné comme « default » ou « centralisé ») est déterminée en fonction de votre adresse de facturation. Lorsque Multi-Geo est activé, vous pouvez placer des boîtes aux lettres dans les emplacements supplémentaires « satellites » par :

- Création d’une nouvelle boîte aux lettres Exchange Online directement dans un satellite.

- Déplacement d’une boîte aux lettres Exchange Online existant dans un satellite.

- Intégration d’une boîte aux lettres d’une organisation d’Exchange sur site directement dans un satellite.

Les zones géographiques suivantes sont disponibles pour une utilisation dans une configuration Multi-localisés :

- Asie-Pacifique

- Australie

- Canada

- Union européenne

- France

- Inde (actuellement uniquement disponible pour les clients avec des adresses de facturation en Inde)

- Japon

- Corée

- Royaume-Uni

- États-Unis

## <a name="prerequisite-configuration"></a>Configuration du logiciel requis
Avant de pouvoir commencer à l’aide de fonctionnalités Multi-localisés dans Exchange Online, Microsoft a besoin configurer votre client pour la prise en charge Multi-Geo Exchange Online. Ce processus de configuration unique est déclenché une fois que vous commandez que multi-Geo et les licences s’affichent-ils dans votre client. Ce processus de configuration unique adopter généralement moins de 30 jours. Ordre Multi-localisés, contactez votre représentant Microsoft. Pour plus d’informations, voir https://aka.ms/Multi-Geo.

Vous allez recevoir des notifications dans le [Centre de messages Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) lorsque votre configuration est terminée. Configuration est automatiquement déclenchée une fois vos licences Multi-Geo s’affichent-ils dans votre client.

## <a name="mailbox-placement-and-moves"></a>Déplacements et l’emplacement de la boîte aux lettres
Microsoft après les étapes de configuration Multi-localisés requis, Exchange Online respecte l’attribut **PreferredDataLocation** sur les objets utilisateur dans Azure AD.

Exchange Online synchronise la propriété **PreferredDataLocation** d’Azure Active Directory dans la propriété **MailboxRegion** dans le service d’annuaire Exchange Online. La valeur de **MailboxRegion** détermine le géographique où les boîtes aux lettres utilisateur et des boîtes aux lettres d’archive associé seront placées. Il n’est pas possible de configurer principales boîte aux lettres et archivage boîtes aux lettres un utilisateur pour se trouvent dans différentes zones géographiques. Geo qu’un seul peut être configuré par l’objet utilisateur.

- Lorsque **PreferredDataLocation** est configuré sur un utilisateur disposant d’une boîte aux lettres existante, la boîte aux lettres est de placer dans une file d’attente de déplacement et automatiquement déplacés vers le Geo spécifié. 

- Lorsque **PreferredDataLocation** est configuré sur un utilisateur sans une boîte aux lettres existante, la boîte aux lettres sera déployé dans le Geo spécifié. 

- Lorsque vous **PreferredDataLocation** sur un utilisateur n’est pas spécifié, la boîte aux lettres est placé dans la valeur par défaut localisés.

- Si le code **PreferredDataLocation** est incorrect (par exemple, un type de NAN au lieu du nom), la boîte aux lettres est placé dans la valeur par défaut localisés.

**Remarque**: fonctionnalités Multi-Geo et Skype pour les réunions en ligne Business régional hébergée par les deux permet de la propriété **PreferredDataLocation** sur les objets utilisateur localisent les services. Si vous configurez des valeurs **PreferredDataLocation** sur les objets utilisateur pour les réunions régional hébergées, la boîte aux lettres pour ces utilisateurs est automatiquement déplacée vers le Geo spécifié après que Multi-Geo est activée sur le client Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitations des fonctions pour Multi-localisés dans Exchange Online
1. Uniquement les boîtes aux lettres, les boîtes aux lettres de ressources (boîtes aux lettres de salles et équipements) et boîtes aux lettres partagées prennent en charge les fonctionnalités Multi-localisés. Boîtes aux lettres de dossier public et de groupes d’Office 365 demeurent dans Geo d’accueil du client.
 
2. Sécurité et conformité fonctionnalités (par exemple, l’audit et découverte électronique) qui sont disponibles dans le centre d’administration Exchange (CAE) ne sont pas disponibles dans les organisations Multi-localisés. Au lieu de cela, vous devez utiliser [Office 365 sécurité & centre de conformité](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.

3. Outlook pour Mac peut-être entraîner une perte temporaire de l’accès à leur dossier Archive en ligne pendant que vous déplacez leur boîte aux lettres à un nouveau localisés. Cette condition se produit lorsque le serveur principal de l’utilisateur archive les boîtes aux lettres se trouvent dans différentes zones géographiques, car les déplacements de boîtes aux lettres cross-Geo peuvent terminer à des moments différents.

4. Les utilisateurs ne peuvent pas partager des *dossiers de boîte aux lettres* entre les zones géographiques dans Outlook sur le web (anciennement appelé Outlook Web App ou OWA). Par exemple, un utilisateur dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé dans une boîte aux lettres qui se trouve aux États-Unis. Toutefois, Outlook sur les utilisateurs Web pouvez ouvrir les *autres boîtes aux lettres* dans différentes zones géographiques à l’aide d’une fenêtre de navigateur distincte comme décrit dans [Ouvrir la boîte aux lettres d’une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Remarque**: partage de dossiers de boîte aux lettres Cross-Geo est pris en charge dans Outlook sur Windows.

## <a name="administration"></a>Administration 
PowerShell distant est nécessaire pour afficher et configurer les propriétés liées à localisés dans votre environnement Office 365. Pour plus d’informations sur les différents modules PowerShell permettant de gérer Office 365, voir [Gérer Office 365 et Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- Vous devez le [Module Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version ultérieure d’en 1.x pour voir la propriété **PreferredDataLocation** sur les objets utilisateur. Les objets utilisateur synchronisés via DAS Connect dans DAS ne peut pas avoir à leur valeur **PreferredDataLocation** modifiée directement via PowerShell DAS. Les objets utilisateur en nuage uniquement peuvent être modifiés via PowerShell DAS. Pour vous connecter à Windows Azure AD PowerShell, voir [se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Pour vous connecter à Exchange Online PowerShell, voir [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Vous connecter directement à une région à l’aide d’Exchange Online PowerShell
En règle générale, Exchange Online PowerShell se connecte à la valeur par défaut localisés. Mais, vous pouvez également vous connecter directement à des zones géographiques non par défaut. En raison des améliorations des performances, nous vous recommandons d’une connexion directe au localisés par défaut lorsque vous gérez uniquement les utilisateurs de cette zone géographique.

Pour vous connecter à une région, le paramètre *ConnectionUri* est différent dans les instructions de connexion standard. Le reste des commandes et valeurs sont les mêmes. Les étapes sont les suivants :

1. Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante :
    
    ```
    $UserCredential = Get-Credential
    ```
   Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre bureau ou une école et mot de passe, puis cliquez sur **OK**.
    
2. Remplacez `<emailaddress>` avec l’adresse de messagerie de **toute** boîte aux lettres cible localisés et exécutez la commande suivante. Vos autorisations sur la boîte aux lettres et de la relation à vos informations d’identification à l’étape 1 ne sont pas un facteur ; l’adresse de messagerie simplement indique à Exchange Online où se connecter.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Par exemple, si olga@contoso.onmicrosoft.com est l’adresse de messagerie d’une boîte aux lettres valide dans le localisés que vous souhaitez vous connecter, exécutez la commande suivante :

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Exécutez la commande suivante :
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD Connect version requise
Connexion DAS version 1.1.524.0 ou version ultérieur est le seul moyen pour définir la propriété **PreferredDataLocation** sur les objets utilisateur qui sont synchronisés de sur site Active Directory. Les objets utilisateur synchronisés via DAS Connect dans DAS ne peut pas avoir à leur valeur **PreferredDataLocation** modifiée directement via PowerShell DAS. Les objets utilisateur en nuage uniquement peuvent être modifiés via PowerShell DAS. Pour des instructions détaillées, consultez la rubrique [synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Codes localisés
Codes de trois lettres vous permet de spécifier la localisés dans la propriété **PreferredDataLocation** . Le tableau suivant répertorie les codes pour les zones géographiques disponibles :

|Géo |Code |
|---------|---------|
|Asie/Pacifique |APC |
|Australie |AUS |
|Canada |CAN |
|Union européenne |EUR |
|France |FRA|
|Inde |IND |
|Japon |JPN |
|Corée |KOR |
|Royaume-Uni |GBR |
|États-Unis |NAM |

**Remarque**: les propriétés **PreferredDataLocation** et **MailboxRegion** sont des chaînes avec aucune vérification des erreurs. Si vous entrez une valeur non valide (par exemple, NAN), que la boîte aux lettres est placé dans la valeur par défaut localisés.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Afficher les zones géographiques disponibles qui sont configurées dans votre organisation Exchange Online
Pour afficher la liste des zones géographiques configurées dans votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

Le résultat de la commande ressemble à ceci :

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Afficher la valeur par défaut géographique de votre organisation Exchange Online
Pour afficher la localisés par défaut de votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

Le résultat de la commande ressemble à ceci :

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Rechercher l’emplacement géographique d’une boîte aux lettres
L’applet de commande **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés suivantes liées à localisés dans les boîtes aux lettres :

- **Base de données**: les 3 lettres du nom de base de données correspondent au code localisés, qui indique où se trouve actuellement la boîte aux lettres. Propriété doit être utilisée pour **ArchiveDatabase** de Online Archive boîtes aux lettres.

- **MailboxRegion**: Spécifie le code de géolocalisation qui a été défini par l’administrateur (synchronisée à partir de **PreferredDataLocation** dans Azure Active Directory).

- **MailboxRegionLastUpdateTime**: indique quand MailboxRegion a été modifiée (automatiquement ou manuellement).

Pour afficher les propriétés d’une boîte aux lettres, utilisez la syntaxe suivante :

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Par exemple, pour afficher les informations de localisés de la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Le résultat de la commande ressemble à ceci :

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Remarque :** Si le code localisés dans le nom de base de données ne correspond pas à la valeur de **MailboxRegion** , la boîte aux lettres sera automatiquement à placer dans une file d’attente de déplacement et déplacé vers le Geo spécifié par la valeur **MailboxRegion** (Exchange Online recherche une discordance entre ces valeurs de propriété).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Déplacer une boîte aux lettres en nuage uniquement existante à une région
Un utilisateur en nuage uniquement est un utilisateur pas opération au client via DAS Connect. Cet utilisateur a été créé directement dans Azure AD. Utilisez les applets de commande **Get-MsolUser** et **Set-MsolUser** dans le Module Azure AD pour Windows PowerShell pour afficher ou spécifier la zone géographique où seront stockés les boîtes aux lettres d’un utilisateur en nuage uniquement.

Pour afficher la valeur **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Par exemple, pour afficher la valeur **PreferredDataLocation** pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Le résultat de la commande ressemble à ceci :

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Pour modifier la valeur **PreferredDataLocation** pour un objet utilisateur en nuage uniquement, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Par exemple, pour définir la valeur **PreferredDataLocation** à l’Union européenne (EUR) localisés pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Remarques** :

- Comme mentionné précédemment vous ne pouvez pas utiliser cette procédure pour les objets utilisateur synchronisé de sur site Active Directory. Vous devez modifier la valeur **PreferredDataLocation** à l’aide de DAS se connecter. Pour plus d’informations, voir [synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- La durée nécessaire pour déplacer un mailboxfrom que son localisés en cours pour la nouvelle geo souhaitée dépend de plusieurs facteurs :
 
  - La taille et le type de boîte aux lettres.
 
  - Le nombre de boîtes aux lettres en cours de déplacement.
 
  - La disponibilité des ressources de déplacement.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Déplacement désactivé les boîtes aux lettres en conservation pour litige
Désactivé les boîtes aux lettres en conservation pour litige sont conservées pour la découverte électronique à des fins ne peuvent pas être déplacés en modifiant leur valeur **PreferredDataLocation** dans leur état désactivé. Pour déplacer une boîte aux lettres désactivée en attente pour litige :

1. Temporairement attribuer une licence à la boîte aux lettres.

2. Modifier la **PreferredDataLocation**.

3. Supprimer la licence de la boîte aux lettres après que qu’il a été déplacé vers la zone géographique sélectionnée à replacer dans un état désactivé.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Créer des nouvelles boîtes aux lettres en nuage dans une région 
Pour créer une nouvelle boîte aux lettres dans une zone géographique spécifique, vous devez effectuer une de ces étapes :

- Configurer la valeur **PreferredDataLocation** , comme décrit dans la précédente section *avant de* que la boîte aux lettres est créé dans Exchange Online. Par exemple, configurez la valeur de **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence. 

- Attribuer une licence en même temps que vous définissez la valeur **PreferredDataLocation** .

Pour créer un nouvel en nuage uniquement sous licence utilisateur (DAS se connectent pas synchronisé) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Cet exemple montre comment créer un nouveau compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :

- Nom d’utilisateur principal : ebrunner@contoso.onmicrosoft.com

- Prénom : Elizabeth

- Nom : Alain Durand

- Nom d’affichage Elizabeth Brunner

- Mot de passe : générée de manière aléatoire et affichées dans les résultats de la commande (parce que nous n’utilisons pas le paramètre de *mot de passe* )

- Licence : contoso:ENTERPRISEPREMIUM (E5)

- Emplacement : Australie (Australie)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Pour plus d’informations sur la création de nouveaux comptes d’utilisateur et de rechercher des valeurs LicenseAssignment dans Windows Azure AD PowerShell, voir [créer les comptes d’utilisateurs avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) et [Afficher les licences et les services Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Remarque :** Si vous utilisez Exchange Online PowerShell pour activer une boîte aux lettres et doivent être créées directement dans le localisés qui est spécifié dans **PreferredDataLocation**la boîte aux lettres, vous devez utiliser une cmdlet comme **Enable-Mailbox** ou **New-boîte aux lettres Exchange Online **directement sur le service en nuage. Si vous utilisez l’applet de commande **Enable-RemoteMailbox** locale Exchange, la boîte aux lettres sera créée dans la valeur par défaut localisés.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Intégré existant boîtes aux lettres locales dans une région
Vous pouvez utiliser les outils d’intégration standard et les processus pour migrer une boîte aux lettres d’une organisation d’Exchange local vers Exchange Online, y compris le [tableau de bord de Migration dans le CAE](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)et l’applet de commande [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) dans Exchange Online PowerShell.

La première étape consiste à vérifier qu'un objet utilisateur existe pour chaque boîte aux lettres onboarded, et vérifiez que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migreront les boîtes aux lettres directement à la Geo spécifié.

Ou bien, vous pouvez utiliser les étapes suivantes pour les boîtes aux lettres intégrées directement dans une région à l’aide de l’applet de commande [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) dans Exchange Online PowerShell.

1. Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres onboarded et que **PreferredDataLocation** est définie sur la valeur souhaitée dans Azure AD. La valeur de **PreferredDataLocation** sera synchronisée dans l’attribut **MailboxRegion** de l’objet utilisateur de messagerie correspondant dans Exchange Online.

2. Connectez-vous directement à la satellite spécifique localisés en suivant les instructions de connexion à partir de plus haut dans cette rubrique.

3. Dans Exchange Online PowerShell, stockent les informations d’identification d’administrateur local qui est utilisé pour effectuer une migration de boîtes aux lettres dans une variable en exécutant la commande suivante :

    ```
    $RC = Get-Credential
    ```

4. Dans Exchange Online PowerShell, créez un nouveau **New-MoveRequest** similaire à l’exemple suivant : 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Répétez l’étape 4 # pour chaque boîte aux lettres à migrer à partir d’Exchange en local au satellite géo vous êtes actuellement connecté.

6. Si vous avez besoin migrer des boîtes aux lettres supplémentaires à un autre satellite géo, répétez les étapes 2 à 4 pour chaque spécifique satellites localisés.

### <a name="multi-geo-reporting"></a>Création de rapports multi-localisés
**Rapports d’utilisation Multi-localisés** dans le centre d’administration Office 365 affiche le nombre d’utilisateurs par zone géographique. Le rapport affiche la distribution des utilisateurs pour le mois en cours et fournit des données d’historique pour les 6 derniers mois.
