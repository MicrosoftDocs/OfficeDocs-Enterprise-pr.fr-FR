---
title: Capacités multi-Geo dans Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Développez votre présence sur Office 365 dans plusieurs régions géographiques avec des capacités multi-geo dans Exchange en ligne.
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Capacités multi-Geo dans Exchange Online

Les fonctionnalités de multi-Geo dans Office 365 permettent un mono-utilisateur à couvrir plusieurs emplacements géographiques (zones géographiques). Lorsque Multi-Geo est activée, les clients peuvent sélectionner l’emplacement du contenu de boîte aux lettres Exchange Online (données au repos) sur une base par utilisateur.

Votre emplacement de clients initial (appelée « par défaut » ou « endroit ») est déterminé en fonction de votre adresse de facturation. Lorsque Multi-Geo est activé, vous pouvez placer des boîtes aux lettres dans les emplacements supplémentaires « satellite » par :

- Création d’une nouvelle boîte aux lettres Exchange Online directement dans un satellite.

- Déplacement d’une boîte aux lettres Exchange Online existant dans un satellite.

- Intégration d’une boîte aux lettres d’une organisation d’Exchange local directement dans un satellite.

Les zones géographiques suivantes sont disponibles pour utilisation dans une configuration Multi-Geo :

- Asie-Pacifique

- Australie

- Canada

- Union européenne

- Inde (actuellement uniquement disponible pour les clients avec des adresses de facturation en Inde)

- Japon

- Corée

- Royaume-Uni

- États-Unis

## <a name="prerequisite-configuration"></a>Configuration du logiciel requis
Avant de commencer à l’aide de fonctions de Multi-Geo dans Exchange en ligne, Microsoft a besoin configurer vos clients Exchange Online pour la prise en charge Multi-Geo. Ce processus de configuration unique est déclenché lorsque vous commandez des licences Multi-Geo et devez prennent généralement moins de 30 jours pour terminer.

Vous recevrez des notifications dans le [Centre de messages d’Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) lorsque votre configuration a démarré et est terminée. Configuration est automatiquement déclenchée lorsque vous achetez des licences Multi-Geo.

## <a name="mailbox-placement-and-moves"></a>Se déplace et le positionnement de la boîte aux lettres
Microsoft après les étapes de configuration Multi-Geo requis, Exchange Online respecte l’attribut **PreferredDataLocation** sur les objets utilisateur dans Active Directory Azure.

En ligne Exchange synchronise la propriété **PreferredDataLocation** à partir d’AD Azure dans la propriété **MailboxRegion** dans le service d’annuaire Exchange en ligne. La valeur de **MailboxRegion** détermine le géographique où seront placés les boîtes aux lettres et boîtes aux lettres d’archive associé. Il n’est pas possible de configurer boîte aux lettres et archivage boîtes aux lettres principales un utilisateur pour résident dans des zones géographiques différentes. Seul Geo peut être configuré par un objet utilisateur.

- Lorsque **PreferredDataLocation** est configuré pour un utilisateur avec une boîte aux lettres existante, la boîte aux lettres sera automatiquement déplacé vers la région spécifiée. 

- Lorsque **PreferredDataLocation** est configuré pour un utilisateur sans une boîte aux lettres existante, la boîte aux lettres sera déployé dans la région spécifiée. 

- Si aucun Geo n’est spécifié, la boîte aux lettres sera placé dans la zone géographique de la valeur par défaut.

**Remarque**: les capacités Multi-Geo et Skype pour des réunions en ligne Business régional hébergé à la fois utilisent la propriété **PreferredDataLocation** sur les objets utilisateur pour localiser les services. Si vous configurez les valeurs de **PreferredDataLocation** sur les objets de l’utilisateur pour les réunions régional hébergées, la boîte aux lettres et OneDrive pour les utilisateurs automatiquement va à la zone géographique spécifiée après que Multi-Geo est activé sur le client Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitations de fonctionnalités pour Multi-Geo dans Exchange Online
1. Uniquement les boîtes aux lettres de l’utilisateur, boîtes aux lettres de ressource (salle et équipement de boîtes aux lettres) et les boîtes aux lettres partagées prennent en charge les fonctionnalités de Multi-Geo. Vous pouvez uniquement placer des boîtes aux lettres des dossiers publics et les groupes d’Office 365 dans géographique d’origine du client.
 
2. Respect de la réglementation de sécurité et de fonctionnalités (par exemple, l’audit et e-Discovery) qui sont disponibles dans le centre d’administration Exchange (FAC) ne sont pas disponibles dans les organisations de Multi-Geo. Au lieu de cela, vous devez utiliser la [sécurité de Microsoft Office 365 et de centre de conformité](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.

3. Outlook pour les utilisateurs de Mac peut rencontrer une perte temporaire de l’accès à leur dossier d’archivage en ligne pendant que vous déplacez sa boîte aux lettres à un nouveau Geo. Cette situation se produit lorsque le l’utilisateur primaire et boîtes aux lettres d’archive dans géographiques différents, car le déplacement de boîtes aux lettres cross-Geo peut se terminer à des moments différents.

4. Les utilisateurs ne peuvent pas partager des *dossiers de boîtes aux lettres* entre les zones géographiques dans Outlook sur le web (anciennement Outlook Web App ou OWA). Par exemple, un utilisateur dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé dans une boîte aux lettres se trouvant aux États-Unis. Toutefois, Outlook sur les utilisateurs du web peut ouvrir les *autres boîtes aux lettres* dans des zones géographiques différentes en utilisant une fenêtre distincte du navigateur, comme décrit dans [Ouvrir boîte aux lettres d’une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Remarque**: le partage des dossiers de boîte aux lettres de Cross-Geo est pris en charge dans Outlook sous Windows.

5. Actuellement, la délégation de calendrier cross-Geo n’est pas pris en charge dans Outlook sur le web. Délégation de calendrier Cross-Geo est pris en charge dans Outlook sous Windows.

## <a name="administration"></a>Administration 
PowerShell distant est nécessaire pour afficher et configurer les propriétés relatives à la zone géographique dans votre environnement Office 365. Pour plus d’informations sur les différents modules PowerShell permettant de gérer Office 365, voir [Gestion d’Office 365 et Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- Vous devez la v1.1.166.0 de [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) ou en version ultérieurement à 1.x pour voir la propriété **PreferredDataLocation** sur les objets utilisateur. Pour vous connecter à Azure AD PowerShell, voir [se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Pour vous connecter à Exchange Online PowerShell, voir [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Se connecter directement à une région à l’aide d’Exchange Online PowerShell
En règle générale, Exchange Online PowerShell se connecte par défaut Geo. Toutefois, vous pouvez également vous connecter directement à des zones géographiques de celle par défaut. En raison des améliorations de performances, nous vous recommandons de connexion directe à la Geo non défini par défaut lorsque vous gérez uniquement les utilisateurs de cette zone géographique.

Pour vous connecter à une zone géographique spécifique, le paramètre *ConnectionUri* est différent dans les instructions de connexion régulières. Le reste des commandes et des valeurs sont les mêmes. Les étapes sont les suivantes :

1. Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante :
    
    ```
    $UserCredential = Get-Credential
    ```
   Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail ou le compte de l’établissement et le mot de passe, puis cliquez sur **OK**.
    
2. Remplacer `<emailaddress>` avec l’adresse de messagerie de **toutes** les boîtes aux lettres dans la cible géographique et exécutez la commande suivante. Vos autorisations sur la boîte aux lettres et de la relation avec vos informations d’identification à l’étape 1 ne sont pas un facteur ; l’adresse de messagerie indique simplement Exchange en ligne permettant de se connecter.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Par exemple, si olga@contoso.onmicrosoft.com est l’adresse de messagerie d’une boîte aux lettres valide dans le géographique que vous voulez vous connecter, exécutez la commande suivante :

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Exécutez la commande suivante :
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Exigences de version Azure Connect de la publicité
Connecter des DAS version 1.1.524.0 ou version ultérieure est la seule méthode prise en charge pour la définition de la propriété **PreferredDataLocation** sur les objets utilisateur sont synchronisés sur les sites Active Directory. Pour obtenir des instructions détaillées, reportez-vous à la section [la synchronisation Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Codes de zone géographique
Codes à trois lettres vous permet de spécifier la zone géographique dans la propriété **PreferredDataLocation** . Le tableau suivant répertorie les codes pour les zones géographiques disponibles :

|Géo |Code |
|---------|---------|
|Asie/Pacifique |APC |
|Australie |AUSTRALIE |
|Canada |POUVEZ |
|Union européenne |EUROS |
|Inde |IND |
|Japon |JPN |
|Corée |KOR |
|Royaume-Uni |GBR |
|États-Unis |NAM |

**Remarque**: les propriétés **PreferredDataLocation** et **MailboxRegion** sont des chaînes avec aucune vérification des erreurs. Si vous entrez une valeur non valide (par exemple, NAN), que la boîte aux lettres est placé dans la zone géographique de la valeur par défaut.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Permet d’afficher les zones géographiques disponibles qui sont configurées dans votre organisation Exchange en ligne
Pour afficher la liste des géographiques configurées dans votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

Le résultat de la commande ressemble à ceci :

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a>Trouver l’emplacement géographique d’une boîte aux lettres
L’applet de commande **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés de géo-associées suivantes sur les boîtes aux lettres :

- **Base de données**: les 3 premières lettres du nom de la base de données correspondent au code géographique, qui vous indique où se trouve actuellement la boîte aux lettres.

- **MailboxRegion**: Spécifie le code géographique qui a été défini par l’administrateur (synchronisé dans Azure annonce à partir de **PreferredDataLocation** ).

- **MailboxRegionLastUpdateTime**: indique lorsque MailboxRegion a été mises à jour (manuellement ou automatiquement).

Pour afficher les propriétés d’une boîte aux lettres, utilisez la syntaxe suivante :

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Par exemple, pour afficher les informations Geo pour la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Le résultat de la commande ressemble à ceci :

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> Si le code géographique dans le nom de la base de données ne correspond pas à la valeur de **MailboxRegion** , la boîte aux lettres sera automatiquement déplacé vers le Geo spécifié par la valeur de **MailboxRegion** (Exchange Online recherche une incompatibilité entre ces valeurs de propriété).

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a>Déplacer une boîte aux lettres du nuage existante à une zone géographique spécifique
Utilisez les applets de commande **Get-MsolUser** et **MsolUser de l’ensemble** du Module AD Azure pour Windows PowerShell pour afficher ou spécifier la zone géographique où seront stockées les boîtes aux lettres de l’utilisateur.

Pour afficher la valeur de **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Azure AD PowerShell :

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Par exemple, pour afficher la valeur de **PreferredDataLocation** pour la michelle@contoso.onmicrosoft.com utilisateur, exécutez la commande suivante :

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Le résultat de la commande ressemble à ceci :

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Pour modifier la valeur de **PreferredDataLocation** pour un objet utilisateur nuage uniquement, utilisez la syntaxe suivante dans Azure AD PowerShell :

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Par exemple, pour définir la valeur de **PreferredDataLocation** à l’Union européenne (en euros) pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Notes**:

- Comme mentionné précédemment pour les objets utilisateur synchronisé sur site Active Directory, vous ne pouvez pas utiliser cette procédure. Vous devez modifier la valeur **PreferredDataLocation** à l’aide de la connexion des DAS. Pour plus d’informations, consultez [sync d’Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Le temps nécessaire pour déplacer une boîte aux lettres dépend de plusieurs facteurs :
 
  - La taille et le type de boîte aux lettres.
 
  - Le nombre de boîtes aux lettres en cours de déplacement.
 
  - La disponibilité des ressources de la déplacer.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Boîtes aux lettres de transfert désactivé sur Litigation Hold
Désactivé les boîtes aux lettres sur Litigation Hold et qui sont conservés pour e-Discovery à des fins ne peut pas être déplacés en modifiant leur valeur **PreferredDataLocation** dans leur état désactivé. Pour déplacer une boîte aux lettres désactivée sur gel :

1. Temporairement attribuer une licence à la boîte aux lettres.

2. Modifier la **PreferredDataLocation**.

3. Supprimer la licence de la boîte aux lettres après que qu’il a été déplacé vers la zone géographique sélectionnée à replacer dans un état désactivé.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Créer des nouvelles boîtes aux lettres du nuage dans une zone géographique spécifique 
Pour créer une nouvelle boîte aux lettres dans une zone géographique spécifique, vous devez effectuer une des opérations suivantes :

- Configurer la valeur **PreferredDataLocation** , comme décrit dans la section *avant de* la boîte aux lettres est créé dans Exchange en ligne (par exemple, en configurant la valeur **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence). 

- Attribuer une licence en même temps que vous définissez la valeur **PreferredDataLocation** .

Pour créer un nuage uniquement sous licence utilisateur (DAS se connecte pas synchronisé) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Azure AD PowerShell :

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Cet exemple montre comment créer un nouveau compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :

- Nom principal d’utilisateur : ebrunner@contoso.onmicrosoft.com

- Prénom : Elizabeth

- Nom : Brunner

- Nom d’affichage Elizabeth Brunner

- Mot de passe : générée de manière aléatoire et apparaissent dans les résultats de la commande (dans la mesure où nous n’utilisons pas le paramètre de *mot de passe* )

- Licence : contoso:ENTERPRISEPREMIUM (E5)

3-emplacement : Australie (Australie)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Pour plus d’informations sur la création de comptes d’utilisateur et la recherche des valeurs de LicenseAssignment dans Azure AD PowerShell, consultez [créer les comptes d’utilisateurs avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) et [Afficher les licences et les services avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> [!NOTE]
> Si vous utilisez Exchange PowerShell pour activer une boîte aux lettres et ont besoin de la boîte aux lettres doit être créé directement dans la zone géographique qui est spécifié dans **PreferredDataLocation**, vous devez utiliser Exchange Online une applet de commande **Enable-Mailbox** ou **New-Mailbox** directement sur le service en nuage. Si vous utilisez l’applet de commande **Enable-RemoteMailbox** sur site Exchange, la boîte aux lettres sera créé dans la région par défaut.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Existante intégrée sur site boîtes aux lettres dans une zone géographique spécifique
Vous pouvez utiliser les outils d’intégration standard et processus pour migrer une boîte aux lettres d’une organisation d’Exchange en local vers Exchange Online, y compris le [tableau de bord de Migration dans l’estimation à l’achèvement](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)et l’applet de commande [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) dans Exchange en ligne PowerShell.

La première étape consiste à vérifier qu'un objet utilisateur existe pour chaque boîte aux lettres onboarded, et vérifiez que la valeur correcte de la **PreferredDataLocation** est configurée dans Active Directory Azure. Les outils d’intégration respecteront la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement à la zone géographique spécifié.

Ou bien, vous pouvez utiliser les étapes suivantes pour les boîtes aux lettres intégrés directement dans une région à l’aide de l’applet de commande [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) dans PowerShell en ligne d’Exchange.

1. Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres soit onboarded et que **PreferredDataLocation** est définie sur la valeur souhaitée dans Azure AD. La valeur de **PreferredDataLocation** est synchronisée avec l’attribut **MailboxRegion** de l’objet utilisateur de messagerie correspondant dans Exchange en ligne.

2. Se connecter directement à la spécifique satellite géo utilisant les instructions de connexion à partir de plus haut dans cette rubrique.

3. Dans Exchange Online PowerShell, stocker les informations d’identification d’administrateur local qui est utilisé pour effectuer une migration de boîtes aux lettres dans une variable en exécutant la commande suivante :

    ```
    $RC = Get-Credential
    ```

4. Dans Exchange Online PowerShell, créez un nouveau **New-MoveRequest** similaire à l’exemple suivant : 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Répétez l’étape #4 pour chaque boîte aux lettres que vous avez besoin pour migrer d’Exchange local vers le satellite géo, vous êtes actuellement connecté à.

6. Si vous avez besoin migrer des boîtes aux lettres supplémentaires vers un autre satellite géo, répétez les étapes 2 à 4 pour chaque spécifique satellite géo.

### <a name="multi-geo-reporting"></a>Création de rapports multi-Geo
**Rapports d’utilisation Multi-Geo** dans le centre d’administration Office 365 affiche le nombre d’utilisateurs par zone géographique. Le rapport affiche la distribution des utilisateurs pour le mois en cours et fournit des données historiques pour les 6 derniers mois.
 
