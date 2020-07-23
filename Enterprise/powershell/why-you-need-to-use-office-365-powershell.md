---
title: Pourquoi utiliser PowerShell pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Résumé : Découvrez pourquoi vous devez utiliser PowerShell pour gérer Microsoft 365, dans certains cas plus efficacement et dans d’autres cas, par nécessité.'
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229860"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Pourquoi utiliser PowerShell pour Microsoft 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Avec le centre d’administration Microsoft 365, vous pouvez non seulement gérer vos licences et comptes d’utilisateur 365 Microsoft, mais également gérer vos services Microsoft 365 tels qu’Exchange Online, teams et SharePoint Online. Toutefois, vous pouvez également gérer ces éléments avec les commandes PowerShell, en tirant parti d’un environnement de langage de script et de ligne de commande pour la vitesse, l’automatisation et la capacité supplémentaire.
  
Dans cet article, nous allons vous montrer les façons dont vous pouvez utiliser PowerShell pour gérer Microsoft 365 :
  
- Révéler des informations supplémentaires que vous ne pouvez pas voir avec le centre d’administration Microsoft 365
    
- Configuration des fonctionnalités et des paramètres uniquement avec PowerShell
    
- Effectuer des opérations en bloc
    
- Filtrage des données
    
- Imprimer ou enregistrer des données
    
- Gérer dans les services
    
Avant de commencer, comprenez que PowerShell pour Microsoft 365 est un ensemble de modules pour Windows PowerShell, un environnement en ligne de commande pour les plateformes et les services Windows. Cet environnement crée un langage de l’interpréteur de commandes qui peut être étendu avec des modules supplémentaires et permet d’exécuter des commandes ou des scripts simples ou complexes. Par exemple, après avoir installé PowerShell pour les modules Microsoft 365 et vous être connecté à votre abonnement Microsoft 365, vous pouvez exécuter cette commande pour répertorier toutes les boîtes aux lettres utilisateur pour Microsoft Exchange Online :
  
```powershell
Get-Mailbox
```

Il est également facile d’obtenir la liste des boîtes aux lettres à l’aide du centre d’administration Microsoft 365, mais le nombre d’éléments dans toutes les listes de tous les sites de toutes les applications Web ne peut pas être facilement réalisé.
  
Veuillez noter que PowerShell pour Microsoft 365 est conçu pour enrichir et améliorer votre capacité à gérer Microsoft 365, et non pour remplacer le centre d’administration Microsoft 365. En tant qu’administrateur, vous devez être au moins familiarisé avec l’utilisation de PowerShell pour Microsoft 365, car il existe des procédures de configuration qui ne peuvent être réalisées qu’avec les commandes PowerShell pour Microsoft 365. Dans ces cas, vous devez savoir comment effectuer les opérations suivantes :
  
- Installez PowerShell pour les modules Microsoft 365 (opération faite une seule fois pour chaque ordinateur d’administrateur).
    
- Connectez-vous à votre abonnement Microsoft 365 (opération terminée une fois pour chaque session PowerShell).
    
- Recueillez les informations nécessaires pour exécuter les commandes PowerShell requises pour Microsoft 365.
    
- Exécutez correctement les commandes PowerShell pour Microsoft 365.
    
Une fois que vous avez acquis ces compétences de base, vous n'êtes plus obligé de répertorier vos utilisateurs de boîte aux lettres avec la commande **Get-Mailbox**, ni de comprendre comment créer une commande comme la précédente pour comptabiliser tous les éléments de toutes les listes de tous les sites pour toutes les applications web. Microsoft et la communauté des administrateurs peuvent vous aider, le cas échéant.
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>PowerShell pour Microsoft 365 peut révéler des informations supplémentaires que vous ne pouvez pas voir avec le centre d’administration Microsoft 365

Le centre d’administration Microsoft 365 affiche un grand nombre d’informations utiles, mais cela ne signifie pas qu’il affiche toutes les informations possibles stockées par Microsoft 365 sur les utilisateurs, les licences, les boîtes aux lettres et les sites. Voici un exemple pour **les utilisateurs et les groupes** dans le centre d’administration 365 de Microsoft :
  
![Exemple d’affichage des utilisateurs et des groupes dans le centre d’administration 365 de Microsoft.](media/o365-powershell-users-and-groups.png)
  
Dans de nombreux cas, cela permet d'afficher les informations que vous devez connaître. Toutefois, il peut arriver que vous ayez besoin de plus d'informations. Par exemple, les licences Microsoft 365 (et les fonctionnalités Microsoft 365 disponibles pour un utilisateur) dépendent en partie de l’emplacement géographique de cet utilisateur. Les stratégies et les fonctionnalités que vous pouvez étendre à un utilisateur qui vit aux États-Unis peuvent ne pas être les mêmes que celles que vous pouvez étendre à un utilisateur qui vit en Inde ou en Belgique. Vous pouvez utiliser le centre d’administration Microsoft 365 pour déterminer l’emplacement géographique d’un utilisateur en procédant comme suit :
  
1. Double-cliquez sur l'élément **Nom d'affichage** de l'utilisateur.
    
2. Dans le volet d'affichage des propriétés utilisateur, cliquez sur **détails**.
    
3. Dans l'affichage des détails, cliquez sur **détails supplémentaires**.
    
4. Faites défiler la liste vers le bas jusqu'à ce que vous voyiez l'en-tête **Pays ou région**:
    
     ![Exemple d’informations de région pour un utilisateur dans le centre d’administration Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. Écrivez le nom d'affichage et l'emplacement de l'utilisateur sur un morceau de papier, ou copiez-le et collez-le dans le Bloc-notes. 
    
Vous devez répéter cette procédure pour chaque utilisateur. Si les utilisateurs sont nombreux, cela peut être une tâche fastidieuse. Avec PowerShell pour Microsoft 365, vous pouvez afficher ces informations pour tous vos utilisateurs à l’aide de la commande suivante :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Voici un exemple d’affichage :
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs dans l’abonnement Microsoft 365 actuel ( **Get-AzureADUser** ), mais afficher uniquement le nom et l’emplacement de chaque utilisateur ( **Select DisplayName, UsageLocation** ).
  
Étant donné que PowerShell pour Microsoft 365 prend en charge une langue de l’interpréteur de commandes, vous pouvez manipuler les informations obtenues à partir de la commande **Get-AzureADUser** . Par exemple, vous voudrez peut-être trier ces utilisateurs en fonction de leur emplacement, en regroupant tous les utilisateurs brésiliens, tous les utilisateurs des États-Unis, etc. Voici la commande :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Voici un exemple d’affichage :
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais afficher uniquement le nom et l’emplacement de chaque utilisateur et les trier d’abord en fonction de leur emplacement, puis leur nom ( **Trier UsageLocation, DisplayName** ).
  
Vous pouvez également employer un filtrage supplémentaire. Par exemple, si vous voulez uniquement voir les informations relatives aux utilisateurs situés au Brésil, utilisez cette commande :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Voici un exemple d'affichage :
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel dont l’emplacement est le Brésil ( **où {$ \_ . UsageLocation-EQ "BR"}** ), puis affichez le nom et l’emplacement de chaque utilisateur.
  
 **Rapide remarque concernant les domaines plus volumineux**
  
Si vous avez un très grand domaine, disons avec des dizaines de milliers d'utilisateurs, l'exécution de certains des exemples que nous vous présentons dans cet article pourrait conduire à une « limitation de bande passante ». Cela signifie que, selon des éléments tels que la puissance de l'ordinateur et la bande passante réseau disponible, vous essayez d'effectuer un trop grand nombre d'actions à la fois. Pour cette raison, les organisations de plus grande taille peuvent souhaiter diviser certaines de ces commandes PowerShell pour Microsoft 365 en deux commandes. Par exemple, cette commande renvoie tous les comptes d'utilisateur et affiche le nom et l'emplacement pour chacun d'entre eux :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Cela fonctionne bien pour les petits domaines. Dans une grande organisation, en revanche, vous devrez peut-être diviser cette commande en deux : une commande pour stocker les informations de compte d'utilisateur dans une variable et une autre commande pour afficher les informations nécessaires. Voici un exemple :
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

L’interprétation de cet ensemble de commandes PowerShell est la suivante :
- Obtenez tous les utilisateurs dans l’abonnement Microsoft 365 actuel et stockez les informations dans une variable nommée $x ( **$x = Get-AzureADUser** ).
- Affiche le contenu de la variable $x, mais inclut uniquement le nom et l’emplacement de chaque utilisateur ( **$x | Select DisplayName, UsageLocation** ).
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 dispose de fonctionnalités que vous pouvez configurer uniquement avec PowerShell pour Microsoft 365

Le centre d’administration Microsoft 365 est destiné à fournir un accès aux tâches d’administration les plus courantes ou les plus pertinentes qui s’appliquent à la plupart des utilisateurs. En d’autres termes, le centre d’administration Microsoft 365 a été conçu afin que l’administrateur par défaut puisse utiliser l’outil pour effectuer les tâches de gestion les plus courantes. Par cette définition, cela signifie qu’il existe certaines tâches qui ne peuvent pas être exécutées à l’aide du centre d’administration Microsoft 365.
  
Par exemple, le Centre d'administration Skype Entreprise Online offre plusieurs options permettant de créer des invitations personnalisées aux réunions :
  
![Exemple d’affichage d’invitations personnalisées à une réunion dans le Centre d’administration de Skype Entreprise Online.](media/o365-powershell-meeting-invitation.png)
  
Avec ces paramètres, vous pouvez ajouter une touche de personnalisation et de professionnalisme aux invitations aux réunions. Cependant, les paramètres de configuration de réunion ne se résument pas à la simple création d'invitations personnalisées aux réunions. Par défaut, les réunions autorisent :
  
- les utilisateurs anonymes à obtenir une entrée automatique à chaque réunion ;
    
- les participants à enregistrer la réunion ;
    
- tous les utilisateurs de votre organisation à être désignés en tant que présentateurs lorsqu’ils rejoignent la réunion.
    
Ces paramètres ne sont pas disponibles à partir du Centre d'administration Skype Entreprise Online. Toutefois, vous pouvez les contrôler à partir de PowerShell pour Microsoft 365. Voici une commande qui désactive ces trois paramètres :
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Cette commande exige que vous installiez le [module Windows PowerShell pour Skype Entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366). 
  
> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : pour les paramètres des nouvelles réunions Skype entreprise Online ( **Set-CsMeetingConfiguration** ), Disable autorisant les utilisateurs anonymes à obtenir une entrée automatique des réunions ( **-AdmitAnonymousUsersByDefault $false** ), désactivez la possibilité pour les participants d’enregistrer des **réunions (** **-AllowConferenceRecording $false** ) et ne désignez pas tous les utilisateurs de votre organisation comme présentateurs
  
Si vous changez d’avis et souhaitez restaurer ces paramètres par défaut (tous les activer), exécutez la commande suivante :
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Il s'agit juste d'un exemple. Il en existe d’autres, c’est pourquoi vous devez être familiarisé avec l’exécution de PowerShell pour les commandes Microsoft 365 en tant qu’administrateur.
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a>PowerShell pour Microsoft 365 est idéal pour effectuer des opérations en bloc

Traditionnellement, les interfaces visuelles telles que le centre d’administration Microsoft 365 sont plus utiles lorsque vous avez une seule opération à effectuer. Par exemple, si vous avez besoin de désactiver un compte d’utilisateur, vous pouvez utiliser le centre d’administration Microsoft 365 pour localiser et désactiver rapidement une case à cocher. Cela peut être plus simple que d’effectuer une opération similaire dans PowerShell.
  
Toutefois, si vous devez modifier de nombreux éléments ou des éléments sélectionnés dans un grand nombre d’autres choses, le centre d’administration de Microsoft 365 peut ne pas être le meilleur moyen de votre temps. Par exemple, si vous deviez modifier le préfixe sur des milliers de numéros de téléphone ou si vous avez besoin de supprimer un utilisateur spécifique, Ken Myer, de tous vos sites SharePoint Online, comment pouvez-vous le faire dans le centre d’administration 365 de Microsoft ?
  
Pour ce dernier exemple, vous disposez de plusieurs centaines de sites SharePoint Online et vous ne savez même pas desquels Ken Meyer est membre. Cela signifie que vous devrez démarrer à partir du centre d’administration 365 de Microsoft, puis effectuer cette procédure pour chaque site :
  
1. Cliquez sur l' **URL** du site.
    
2. Dans la zone **Propriétés de la collection de sites**, cliquez sur le lien **Adresse du site web** pour accéder au site.
    
3. Sur le site, cliquez sur **Partager**.
    
4. Dans la boîte de dialogue **Partager**, cliquez sur le lien qui affiche tous les utilisateurs disposant d'autorisations sur le site :
    
     ![Exemple d’affichage des membres d’un site SharePoint Online dans le Centre d’administration SharePoint Online.](media/o365-powershell-view-permissions.png)
  
5. Dans la boîte de dialogue **Partagé avec**, cliquez sur **Avancé**.
    
6. Faites défiler vers le bas la liste des utilisateurs, recherchez et sélectionnez Ken Myer (en supposant qu'il dispose d'autorisations sur le site), puis cliquez sur **Supprimer les autorisations des utilisateurs**.
    
Réaliser la procédure pour plusieurs centaines de sites peut prendre un certain temps.
  
Vous pouvez également utiliser PowerShell pour Microsoft 365 et la commande suivante pour supprimer Ken Myer de tous vos sites :
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Cette commande exige que vous installiez le [module SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les sites SharePoint dans l’abonnement Microsoft 365 actuel ( **Get-SPOSite** ) et pour chaque site, supprimez Ken Meyer de la liste des utilisateurs qui peuvent y accéder ( **foreach {Remove-épouser-site $ \_ . URL-LoginName "kenmyer@litwareinc.com"}** ).
  
Étant donné que nous indiquons à Microsoft 365 de supprimer Ken Meyer de chaque site, y compris ceux auxquels il n’a pas accès, l’affichage de cette commande affiche des erreurs pour les sites dans lesquels il n’a pas accès. Nous pouvons utiliser une condition supplémentaire sur cette commande pour supprimer Ken Meyer uniquement des sites qui l'ont dans leur liste de connexion, mais les erreurs répertoriées ne nuisent pas aux sites eux-mêmes. L’exécution de cette commande peut prendre quelques minutes sur des centaines de sites, et non sur des heures de travail par le biais du centre d’administration Microsoft 365.
  
Voici un autre exemple d’opération en bloc. Utilisez cette commande pour ajouter Bonnie Kearney, une nouvelle administratrice SharePoint, à tous les sites de l’organisation :
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les sites SharePoint de l’abonnement Microsoft 365 actuel et pour chaque site, autoriser l’accès Kearney Bonnie en ajoutant son nom de connexion au groupe membres du site ( **foreach {Add-époux-site $ \_ . URL-LoginName "bkearney@litwareinc.com"-Group "members"}** ).
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell pour Microsoft 365 est idéal pour le filtrage des données

Le centre d’administration 365 de Microsoft offre plusieurs méthodes pour filtrer vos données afin de localiser rapidement et facilement un sous-ensemble ciblé d’informations. Par exemple, Exchange facilite le filtrage sur pratiquement toutes les propriétés de la boîte aux lettres d'un utilisateur. Par exemple, voici la liste des boîtes aux lettres de tous les utilisateurs qui habitent Bloomington :
  
![Exemple de recherche avancée dans le centre d’administration Microsoft 365 pour obtenir la liste des boîtes aux lettres de tous les utilisateurs vivant dans la ville de Bloomington.](media/o365-powershell-advanced-search.png)
  
Le Centre d'administration Exchange vous permet également de combiner des critères de filtre. Par exemple, vous pouvez trouver les boîtes aux lettres de toutes les personnes qui habitent à Bloomington et travaillent dans le service Finances. 
  
Toutefois, il existe des limites à ce que vous pouvez faire dans le Centre d'administration Exchange. Par exemple, vous souhaitez peut-être trouver les boîtes aux lettres des personnes qui habitent à Bloomington ou San Diego, ou les boîtes aux lettres de toutes les personnes qui n'habitent pas à Bloomington. 
  
Avec PowerShell pour Microsoft 365, vous pouvez obtenir la liste des boîtes aux lettres de toutes les personnes vivant dans les villes de Bloomington ou San Diego avec cette commande :
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Voici un exemple d’affichage :
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel disposant d’une boîte aux lettres dans les villes de San Diego ou Bloomington ( **où {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-et ($ \_ . City-EQ "San Diego"-ou $ \_ . City-EQ "Bloomington")}** ), puis affichez le nom et la ville de chacune d’entre elles ( **Sélectionnez DisplayName, City** ).
  
Pour répertorier toutes les boîtes aux lettres des personnes habitant n’importe où sauf à Bloomington, voici la commande :
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Voici un exemple d’affichage :
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel qui disposent d’une boîte aux lettres qui ne se trouve pas dans la ville de Bloomington ( **où {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-et $ \_ . Ville-ne "Bloomington"}** ), puis affiche le nom et la ville de chacun d’eux.
  
Vous pouvez également utiliser des caractères génériques dans vos filtres PowerShell pour faire correspondre une partie d’un nom. Par exemple, supposons que vous recherchiez un compte d'utilisateur et que vous vous rappeliez uniquement que son nom est Anderson, ou Henderson, ou bien Jorgenson.
  
Vous pouvez identifier cet utilisateur dans le centre d’administration 365 de Microsoft à l’aide de l’outil de recherche et en effectuant trois recherches différentes :
  
- Une sur  *Anderson* 
    
- Une sur  *Henderson* 
    
- Une sur  *Jorgenson* 
    
Étant donné que ces trois noms se terminent par « fils », vous pouvez indiquer à PowerShell d’afficher tous les utilisateurs dont le nom se termine par « fils ». Voici la commande :
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais utiliser un filtre qui répertorie uniquement les utilisateurs dont le nom de famille se termine par « fils » ( **-Filter « {LastName-like " \* fils »}»** ). \*Représente un ensemble de caractères, qui sont des lettres dans le cas du nom de famille de l’utilisateur.
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell pour Microsoft 365 facilite l’impression ou l’enregistrement des données

Le centre d’administration Microsoft 365 vous permet d’afficher des listes de données. Voici un exemple dans lequel le Centre d'administration Skype Entreprise Online affiche la liste des utilisateurs qui ont été activés pour Skype Entreprise Online :
  
![Exemple de liste d’utilisateurs ayant été activés pour Skype Entreprise Online, affichée dans le Centre d’administration de Skype Entreprise Online.](media/o365-powershell-lync-users.png)
  
Pour enregistrer ces informations dans un fichier, vous devez les copier-coller dans un document ou dans Excel. Dans les deux cas, la copie peut nécessiter une mise en forme supplémentaire. En outre, le centre d’administration Microsoft 365 ne permet pas d’imprimer directement la liste affichée.
  
Heureusement, vous pouvez utiliser PowerShell pour non seulement afficher la liste, mais l’enregistrer dans un fichier qui peut être facilement importé dans Excel. Voici un exemple de commande permettant d'enregistrer des données utilisateur Skype Entreprise Online dans un fichier au format CSV (valeurs séparées par des virgules), fichier qui peut être facilement importé sous forme de tableau dans une feuille de calcul Excel :
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Voici un exemple d’affichage :
  
![Exemple de table importée dans une feuille de calcul Excel pour des données Skype Entreprise Online qui ont été enregistrées dans un fichier de valeurs séparées par des virgules (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  L’interprétation de cette commande PowerShell est : obtenir tous les utilisateurs de Skype entreprise Online dans l’abonnement Microsoft 365 actuel ( **Get-CsOnlineUser** ), obtenir uniquement le nom d’utilisateur, l’UPN et l’emplacement ( **Select DisplayName, userPrincipalName, UsageLocation** ), puis enregistrer ces informations dans le fichier CSV nommé C : \\ logs \\SfBUsers.csv ( **Export-CSV-path "C : \\ logs \\SfBUsers.csv"-NoTypeInformation** ).
  
Vous pouvez également utiliser des options pour enregistrer cette liste sous forme de fichier XML ou de page HTML. En fait, avec les commandes PowerShell supplémentaires, vous pouvez l’enregistrer directement dans un fichier Excel, avec la mise en forme personnalisée de votre choix. 
  
Vous pouvez également envoyer la sortie d’une commande PowerShell qui affiche une liste directement sur l’imprimante par défaut dans Windows. Voici un exemple de commande :
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Le document imprimé aura l'apparence suivante :
  
![Exemple de document imprimé correspondant à la sortie d’une commande PowerShell indiquée directement sur l’imprimante par défaut dans Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de Skype entreprise Online dans l’abonnement Microsoft 365 actuel, obtenir uniquement le nom d’utilisateur, l’UPN et l’emplacement, puis envoyer ces informations à l’imprimante Windows par défaut ( **out-Printer** ).
  
Le document imprimé a la même mise en forme que l’affichage dans la fenêtre de commande PowerShell, mais une fois que vous avez créé une commande PowerShell pour répertorier ce dont vous avez besoin, ajoutez simplement **| Out-Printer** à la fin de la commande pour obtenir une copie matérielle.
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>PowerShell pour Microsoft 365 vous permet de gérer tous les produits serveur

Les différents composants qui composent Microsoft 365 sont conçus pour fonctionner ensemble. Par exemple, supposons que vous ajoutez un nouvel utilisateur à Microsoft 365 et, lorsque vous le faites, vous spécifiez des informations telles que le service et le numéro de téléphone de l’utilisateur. Ces informations seront disponibles si vous accédez aux informations de l’utilisateur à l’aide de l’un des services Microsoft 365 : Skype entreprise Online, Exchange ou SharePoint Online.
  
Toutefois, ceci concerne les informations communes qui couvrent une suite de produits. Les informations propres à un produit (par exemple, des informations sur la boîte aux lettres Exchange d'un utilisateur) ne sont généralement pas disponibles dans la suite. Par exemple, si vous voulez savoir si la boîte aux lettres d'un utilisateur est activée ou non, cette information est disponible uniquement dans le Centre d'administration Exchange. 
  
Supposons que vous souhaitiez établir un rapport qui présente les informations suivantes pour tous les utilisateurs :
  
- Nom complet de l'utilisateur
    
- Si l’utilisateur est titulaire d’une licence pour Microsoft 365
    
- Si la boîte aux lettres Exchange de l'utilisateur a été activée
    
- Si l'utilisateur est activé pour Skype Entreprise Online
    
Actuellement, vous ne pouvez pas utiliser le centre d’administration Microsoft 365 pour produire un tel rapport. Au lieu de cela, vous devrez créer un document distinct pour stocker les informations, comme une feuille de calcul Excel, et obtenir tous les noms d’utilisateur et les informations de licence à partir du centre d’administration 365 de Microsoft, obtenir des informations de boîte aux lettres à partir du centre d’administration Exchange, obtenir des informations Skype entreprise Online à partir du centre d’administration Skype entreprise Online, puis assembler
  
L’alternative consiste à utiliser un script PowerShell pour compiler ce rapport pour vous.
  
L'exemple de script suivant est plus complexe que les commandes que vous avez vues jusqu'à présent dans cet article. Toutefois, il illustre la possibilité d’utiliser PowerShell pour créer des affichages d’informations qui sont très difficiles à faire autrement. Voici le script qui peut compiler et afficher la liste nécessaire :
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Voici un exemple d’affichage :
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

L’interprétation de ce script PowerShell est la suivante :  

- Obtenez tous les utilisateurs dans l’abonnement Microsoft 365 actuel et stockez les informations dans une variable nommée $x ( **$x = Get-AzureADUser** ).
- Démarre une boucle qui s’exécute sur tous les utilisateurs dans la variable nommée $x ( **foreach ($i in $x)** ).  
- Définit une variable nommée $y et y stocke des informations sur la boîte aux lettres de l’utilisateur ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).
- Ajoute une nouvelle propriété dans les informations utilisateur nommée IsMailBoxEnabled et la définit sur la valeur de la propriété IsMailBoxEnabled de la boîte aux lettres de l’utilisateur ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).
- Définit une variable nommée $y et y stocke les informations Skype Entreprise Online de l’utilisateur ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).
- Ajoute une nouvelle propriété dans les informations utilisateur nommée EnabledForSfB et la définit sur la valeur de la propriété Enabled des informations Skype Entreprise Online ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).
- Affiche la liste des utilisateurs, mais indique uniquement leur nom, s’ils disposent d’une licence, et les deux nouvelles propriétés qui spécifient si leur boîte aux lettres est activée et si elles sont activées pour Skype Entreprise Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).
  
## <a name="see-also"></a>Voir aussi

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)
  
[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Utiliser Windows PowerShell pour créer des rapports dans Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)

