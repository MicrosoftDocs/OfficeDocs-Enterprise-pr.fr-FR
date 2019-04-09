---
title: Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment administrer le paramètre d’Exchange Online avec Microsoft PowerShell.
ms.openlocfilehash: 5e1108c946ab1d9588ad5d1d41f21799e8254257
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933980"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique

Remote PowerShell est nécessaire pour afficher et configurer les propriétés multigéographiques dans votre environnement Office 365. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

Pour voir la propriété **PreferredDataLocation** sur les objets utilisateur, vous devez disposer du [module PowerShell Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version v1.x ultérieure. La valeur **PreferredDataLocation** des objets utilisateur synchronisés via AAD Connect dans AAD ne peut pas être modifiée directement via AAD PowerShell. Les objets utilisateur cloud uniquement peuvent être modifiés via AAD PowerShell. Pour vous connecter à Azure AD PowerShell, voir [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Se connecter directement à un emplacement géographique à l’aide d’Exchange Online PowerShell
En règle générale, Exchange Online PowerShell se connecte à l’emplacement central. Vous pouvez cependant aussi vous connecter directement à des emplacements satellites. En raison des améliorations apportées aux performances, nous vous recommandons de vous connecter directement à l’emplacement satellite lorsque vous gérez uniquement des utilisateurs situés dans cet emplacement géographique.

Le paramètre *ConnectionUri* utilisé pour la connexion à un emplacement géographique spécifique diffère des instructions de connexion ordinaires. Les autres commandes et valeurs sont identiques. Voici comment procéder :

1. Sur votre ordinateur local, ouvrez Windows PowerShell, puis exécutez la commande suivante :
    
    ```
    $UserCredential = Get-Credential
    ```
   Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez vos nom d’utilisateur et mot de passe, puis cliquez sur **OK**.
    
2. Remplacez `<emailaddress>` par l’adresse e-mail d’une boîte aux lettres **quelconque** dans l’emplacement géographique cible, puis exécutez la commande suivante. Vos autorisations sur la boîte aux lettres et la relation à vos informations d’identification décrites à l’étape 1 ne constituent pas un facteur. L’adresse e-mail indique simplement à Exchange Online où se connecter.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Par exemple, si olga@contoso.onmicrosoft.com est l’adresse e-mail d’une boîte aux lettres valide dans la zone géographique à laquelle vous voulez vous connecter, exécutez la commande suivante :

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Exécutez la commande suivante :
    
    ```
    Import-PSSession $Session
    ```


## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Affichage des emplacements géographiques disponibles configurés dans votre organisation Exchange Online
Pour afficher la liste des emplacements géographiques configurés dans Office 365 multigéographique, exécutez la commande suivante dans Exchange Online PowerShell :

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-location-for-your-exchange-online-organization"></a>Afficher l’emplacement central de votre organisation Exchange Online
Pour afficher l’emplacement central de votre locataire, exécutez la commande suivante dans Exchange Online PowerShell :

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Recherche de l’emplacement géographique d’une boîte aux lettres
La cmdlet **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés multigéographiques associées suivantes sur les boîtes aux lettres :

- **Database** : les 3 premières lettres du nom de base de données correspondent au géocode indiquant où la boîte aux lettres se trouve actuellement. Pour les boîtes aux lettres d’archivage en ligne, il convient d’utiliser la propriété **ArchiveDatabase**.

- **MailboxRegion** : spécifie le code de géolocalisation défini par l’administrateur (synchronisé à partir de **PreferredDataLocation** dans Azure AD).

- **MailboxRegionLastUpdateTime** : indique quand la propriété MailboxRegion a été mise à jour (automatiquement ou manuellement) pour la dernière fois.

Pour afficher ces propriétés pour une boîte aux lettres, utilisez la syntaxe suivante :

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Par exemple, pour voir les informations géographiques de la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Le résultat de la commande ressemble à ceci :

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Remarque :** si le code de géolocalisation dans le nom de la base de données ne correspond pas à la valeur **MailboxRegion**, la boîte aux lettres est automatiquement placée dans une file d’attente de déplacement, et déplacée vers l’emplacement géographique spécifié par la valeur **MailboxRegion** (Exchange Online recherche une discordance entre ces valeurs de propriété).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Déplacer une boîte aux lettres cloud uniquement vers un emplacement géographique spécifique
Un utilisateur cloud uniquement est un utilisateur qui n’est pas synchronisé avec le locataire via AAD Connect. Cet utilisateur a été créé directement dans Azure AD. Pour afficher ou spécifier la zone géographique dans laquelle sera stockée la boîte aux lettres d’un utilisateur cloud uniquement, utilisez les cmdlets **Get-MsolUser** et **Set-MsolUser** dans le module Azure AD pour Windows PowerShell.

Pour voir la valeur **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Azure AD PowerShell :

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Par exemple, pour voir la valeur **PreferredDataLocation** pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Pour modifier la valeur **PreferredDataLocation** d’un objet utilisateur cloud uniquement, utilisez la syntaxe suivante dans Azure AD PowerShell :

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Par exemple, pour définir la valeur **PreferredDataLocation** sur la zone géographique Union européenne (EUR) pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Remarques** :

- Comme mentionné précédemment, vous ne pouvez pas utiliser cette procédure pour des objets utilisateur synchronisés à partir du service Active Directory local. Vous devez modifier la valeur **PreferredDataLocation** dans Active Directory et la synchroniser à l’aide d’AAD Connect. Pour plus d’informations, voir [Synchronisation Azure Active Directory Connect : Configurer un emplacement de données par défaut pour les ressources Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Le temps nécessaire pour déplacer une boîte aux lettres vers un nouvel emplacement géographique dépend de plusieurs facteurs :
 
  - la taille et le type de boîte aux lettres ;
 
  - le nombre total de boîtes aux lettres déplacées ;
 
  - la disponibilité des ressources nécessaires pour le déplacement.

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Déplacer des boîtes aux lettres désactivées pour cause de Conservation pour litige
Il est possible de déplacer des boîtes aux lettres désactivées pour cause de Conservation pour litige à des fins de découverte électronique (eDiscovery) en modifiant leur valeur **PreferredDataLocation**. Pour déplacer une boîte aux lettres désactivée pour cause de Conservation pour litige :

1. Attribuez temporairement une licence à la boîte aux lettres.

2. Modifiez la valeur **PreferredDataLocation**.

3. Une fois la boîte aux lettres déplacée vers l’emplacement géographique choisi, supprimez sa licence afin de la remettre à l’état désactivé.

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Créer des boîtes aux lettres cloud dans un emplacement géographique spécifique
Pour créer une boîte aux lettres dans un emplacement géographique spécifique, vous devez effectuez l’une des opérations suivantes :

- Configurer la valeur **PreferredDataLocation** de la manière décrite dans la section précédente *avant* de créer la boîte aux lettres dans Exchange Online ; par exemple, définir la valeur **PreferredDataLocation** sur un utilisateur avant l’attribution d’une licence. 

- Attribuer une licence lors de la définition de la valeur **PreferredDataLocation**.

Pour créer un utilisateur titulaire d’une licence d’utilisation cloud uniquement (non synchronisé avec AAD Connect) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Azure AD PowerShell :

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Cet exemple montre comment créer un compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :

- Nom d’utilisateur principal : ebrunner@contoso.onmicrosoft.com

- Prénom : Elizabeth

- Nom : Brunner

- Nom d’affichage Elizabeth Brunner

- Mot de passe : généré de façon aléatoire et affiché dans les résultats de la commande (étant donné que nous n’utilisons pas le paramètre *Password*)

- Licence : contoso:ENTERPRISEPREMIUM (E5)

- Emplacement : Australie (AUS)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Pour plus d’informations sur la création de comptes d’utilisateur et la recherche de valeurs LicenseAssignment dans Azure AD PowerShell, voir [Création de comptes d’utilisateurs avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) et [Afficher les licences et les services avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Remarque :** si vous utilisez Exchange Online PowerShell pour activer une boîte aux lettres et avez besoin que la boîte aux lettres soit créée directement dans la zone géographique spécifiée dans **PreferredDataLocation**, vous devez utiliser une cmdlet Exchange Online telle que **Enable-Mailbox** ou **New-Mailbox** directement sur le service cloud. Si vous utilisez la cmdlet Exchange locale **RemoteMailbox activer**, la boîte aux lettres est créée dans l’emplacement central.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Intégrer des boîtes aux lettres locales existant dans un emplacement géographique spécifique
Vous pouvez vous servir des outils et processus d’intégration standard pour migrer une boîte aux lettres d’une organisation Exchange locale vers Exchange Online. Ces outils sont le [Tableau de bord de migration dans le Centre d’administration Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) et la cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) dans Exchange Online PowerShell.

La première étape consiste à vérifier qu’un objet utilisateur existe pour chaque boîte aux lettres à intégrer, et que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement vers la zone géographique spécifiée.

Ou bien, pour intégrer les boîtes aux lettres directement dans un emplacement géographique à l’aide de la cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) dans Exchange Online PowerShell, vous pouvez également procéder comme suit.

1. Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres intégrée et que la valeur **PreferredDataLocation** est correctement définie dans Azure AD. La valeur **PreferredDataLocation** est synchronisée avec l’attribut **MailboxRegion** de l’objet utilisateur de courrier correspondant dans Exchange Online.

2. Connectez-vous directement à la zone géographique satellite spécifique en suivant les instructions de connexion figurant plus haut dans cette rubrique.

3. Dans Exchange Online PowerShell, stockez les informations d’identification d’administrateur locales utilisées pour effectuer une migration de boîte aux lettres dans une variable en exécutant la commande suivante :

    ```
    $RC = Get-Credential
    ```

4. Dans Exchange Online PowerShell, créez une cmdlet **New-MoveRequest** similaire à l’exemple suivant : 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Répétez l’étape 4 pour chaque boîte aux lettres à migrer d’Exchange sur site vers l’emplacement satellite auquel vous êtes actuellement connecté.

6. Si vous devez migrer des boîtes aux lettres supplémentaires vers un autre emplacement satellite, répétez les étapes 2 à 4 pour chaque emplacement satellite.

## <a name="multi-geo-reporting"></a>Génération de rapports multigéographiques
Les **rapports d’utilisation multigéographique** dans le Centre d’administration Microsoft 365 affichent le nombre d’utilisateurs par emplacement géographique. Le rapport présente la répartition des utilisateurs pour le mois en cours et les données historiques des 6 derniers mois.

## <a name="see-also"></a>Voir aussi

[Gestion d’Office 365 et d’Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)