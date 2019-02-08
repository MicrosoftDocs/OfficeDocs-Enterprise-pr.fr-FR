---
title: Utiliser le réseau de distribution de contenu Office 365 avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Décrit l’utilisation intégrés Content Delivery Network d’Office 365 (CDN) pour accélérer la remise de vos ressources SharePoint Online pour tous vos utilisateurs quel que soit l’où ils se trouvent ou comment ils accèdent à votre contenu.
ms.openlocfilehash: fd118e8df404961e1c35c6297a788397f810d1a2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "29547112"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Utiliser le réseau de distribution de contenu Office 365 avec SharePoint Online

Vous pouvez héberger des biens statiques dans le réseau de distribution de contenu (CDN) Office 365 pour améliorer les performances de vos pages SharePoint Online. Ressources statiques sont des fichiers qui ne changent pas très souvent, comme les images, vidéo et audio, des feuilles de style, les polices et fichiers JavaScript. Le CDN fonctionne comme un proxy de mise en cache distribué géographiquement, en mettant en cache les biens statiques rapprocher pour les navigateurs les demandant. 
  
Si vous êtes déjà familiarisé avec la façon dont les CDN, vous devez uniquement effectuer quelques étapes pour la configurer. Cette rubrique décrit comment. Lecture pour plus d’informations sur le CDN 365 Office et la mise en route qui héberge vos ressources statiques.
  
 **Tête de retour à la [planification du réseau et réglage des performances pour Office 365](https://aka.ms/tune).**
  
## <a name="office-365-cdn-basics"></a>Notions de base sur Office 365 CDN

Le CDN 365 Office est inclus dans le cadre de votre abonnement SharePoint Online. Vous n’êtes pas obligé de payer supplémentaire. Office 365 fournit la prise en charge pour les deux privé et accès public et vous permet aux biens statique hôte dans plusieurs emplacements ou origines. Le CDN 365 Office n’est pas le même que le CDN Azure. Si vous avez besoin de plus d’informations sur les raisons d’utiliser un CDN ou sur les concepts généraux relatifs CDN, voir [réseaux de distribution de contenu](content-delivery-networks.md).
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>Comment le CDN permet d’accéder aux utilisateurs finaux

Accès privé aux biens statiques dans le CDN 365 Office est affecté par les jetons générés par SharePoint Online. Les utilisateurs qui ont déjà l’autorisation d’accéder au dossier ou bibliothèque désigné par l’origine seront accordées automatiquement jetons. SharePoint Online ne prend pas en charge autorisations au niveau de l’élément pour du CDN.
  
Par exemple, pour un fichier situé dans le `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, étant donné les éléments suivants :
  
- L’utilisateur 1 dispose d’un accès pour folder1 et image1.jpg
    
- L’utilisateur 2 n’a pas accès aux dossiers folder1
    
- Utilisateur 3 n’a pas accès aux dossiers folder1 mais est l’autorisation explicite d’accéder à image1.jpg via SharePoint Online
    
- Utilisateur 4 a accès aux dossiers folder1 mais a été explicitement refusé l’accès à image1.jpg
    
Puis les conditions suivantes sont remplies :
  
- L’utilisateur 1 et 4 de l’utilisateur sera en mesure d’accéder aux image1.jpg par le biais du CDN.
    
- L’utilisateur 2 et 3 de l’utilisateur ne sera pas en mesure d’accéder aux image1.jpg par le biais du CDN.
    
    Toutefois, utilisateur 3 peut toujours accéder les biens image1.jpg via SharePoint Online, pendant que l’utilisateur 4 ne peut pas accéder à la ressource via SharePoint Online.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Vue d’ensemble de l’utilisation du CDN 365 Office

Pour configurer le CDN 365 Office, vous suivez ces étapes de base :
  
- Planifier un déploiement CDN :
    
  - Connaître les ressources statiques vous souhaitez héberger sur le CDN 365 Office. Pour plus d’informations sur la façon d’apporter ces choix, reportez-vous aux [réseaux de distribution de contenu](content-delivery-networks.md).
    
  - [Déterminer où vous souhaitez stocker vos actifs](use-office-365-cdn-with-spo.md#CDNStoreAssets). Cet emplacement est un dossier ou une bibliothèque SharePoint et est appelé une origine.
    
  - Déterminer si les éléments doivent être rendues publiques ou confidentiel. Vous faire lorsque vous [Choisissez si chaque origine doit être publiques ou privées](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Si vous le souhaitez, vous pouvez avoir plusieurs origines dans laquelle certaines sont publics, et certaines sont privés.
    
- [Définir installation et configuration du CDN 365 Office à l’aide de SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Lorsque vous avez terminé cette étape, vous devez :
    
  - Extension du CDN pour votre organisation.
    
  - Ajouté votre origines. Vous identifier chaque origine comme public ou private.
    
Une fois terminé le programme d’installation, [Gérer les CDN 365 Office](use-office-365-cdn-with-spo.md#CDNManage) au fil du temps par : 
  
- Ajout, mise à jour et suppression d’actifs
    
- Ajout et suppression d’origine
    
- Configuration des stratégies CDN
    
- Si nécessaire, la désactivation du CDN 365 Office
    
## <a name="determine-where-you-want-to-store-your-assets"></a>Déterminer où vous souhaitez stocker vos ressources

Le CDN extrait vos ressources à partir d’un emplacement de l’origine. Pour Office 365, une origine est une bibliothèque SharePoint ou un dossier accessible par une URL. Vous avez une grande souplesse lorsque vous spécifiez origines pour votre organisation. Par exemple, vous pouvez spécifier plusieurs origines, ou, une seule origine où vous souhaitez placer tous vos actifs CDN. Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations seront choisir d’implémenter une combinaison des deux.
  
Si vous définissez des centaines d’origines, il sera probablement avoir un impact négatif sur le temps que nécessaire pour traiter les demandes. Il est recommandé que si vous avez plus de 100 origines vous souhaitez concevoir de nouveau votre architecture.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>Choisissez si chaque origine doit être publiques ou privées

Lorsque vous identifiez une origine, vous spécifiez s’il doit être rendu public ou privé. Quel que soit l’option que vous choisissez, Microsoft fait l’essentiel pour vous lorsqu’il s’agit de l’administration du CDN proprement dit. En outre, vous pouvez modifier votre avis ultérieurement, une fois que vous avez configuré le CDN et identifié votre origines.
  
Options publiques et privées améliorent les performances, mais chacun présente des avantages et des attributs uniques.
  
 **Attributs et les avantages de l’hébergement des biens dans une origine publique**
  
- Biens exposées dans une origine public sont accessibles par tout le monde accès anonyme.
    
    > [!IMPORTANT]
    > Si vous identifiez une origine publique dans votre CDN, vous devez placer jamais les ressources qui sont considérés comme critiques pour votre organisation dans une origine public ou une bibliothèque SharePoint Online. 
  
- Si vous supprimez un bien à partir d’une origine publique, bien peut continuer à être disponible pendant 30 jours à partir du cache ; Toutefois, nous affectera des liens vers les biens dans le CDN après 15 minutes.
    
- Lorsque vous hébergez les feuilles de style (fichiers CSS) dans une origine publique, vous pouvez utiliser les URI et les chemins d’accès relatifs dans le code. Cela signifie que vous pouvez faire référence à l’emplacement des images d’arrière-plan et d’autres objets par rapport à l’emplacement de l’immobilisation qui l’appelle.
    
- Alors que vous pouvez coder les URL d’une origine public, cela est déconseillé. La raison en est que si l’accès du CDN devient indisponible, l’URL ne résout pas automatiquement à votre organisation dans SharePoint Online et liens rompus et les autres erreurs pouvant entraîner.
    
- Les types de fichiers par défaut qui sont inclus pour origines publics sont .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf et .woff. Vous pouvez spécifier les types de fichiers supplémentaires.
    
- Si vous le souhaitez, vous pouvez configurer une stratégie pour exclure les éléments qui ont été identifiés par des classifications de site que vous spécifiez. Par exemple, vous pouvez choisir d’exclure tous les actifs qui sont marqués comme étant « confidentiel » ou « restreint » même si elles sont un type de fichier autorisés et se trouvent dans une origine publique.
    
 **Attributs et les avantages de l’hébergement des biens dans une origine privée**
  
- Les utilisateurs accèdent uniquement les ressources à partir d’une origine privée si elles sont autorisés à le faire. L’accès anonyme à ces actifs est bloquée.
    
- Si vous supprimez un bien à l’origine privée, bien peut continuer à être disponible pour jusqu'à une heure à partir du cache ; Toutefois, nous affectera des liens vers les biens dans le CDN après 15 minutes.
    
- Les types de fichiers par défaut qui sont inclus pour origines privées sont .ico, .gif, .jpeg, .jpg, .js et .png. Vous pouvez spécifier les types de fichiers supplémentaires.
    
- À l’instar des origines publics, vous pouvez configurer une stratégie pour exclure les éléments qui ont été identifiés par des classifications de site que vous spécifiez la même si vous utilisez des caractères génériques pour inclure tous les éléments dans un dossier ou une bibliothèque de Site.
    
## <a name="default-office-365-cdn-origins"></a>Origines d’Office 365 CDN par défaut

Sauf indication contraire, Office 365 organise des origines par défaut pour vous lorsque vous activez le CDN 365 Office. Si vous les excluez à l’origine, vous pouvez ajouter ces origines après avoir terminé le programme d’installation.
  
Origines privées par défaut :
  
- \*/userphoto.aspx
    
- \*/siteassets
    
Origines publics par défaut :
  
- \*/MasterPage
    
- \*bibliothèque /style

> [!NOTE]
> Clientsideassets est une origine public par défaut qui a été ajoutée dans déc de 2017 afin que, si vous avez un CDN public avant cette date, vous ne consultez l’entrée ajoutée automatiquement, mais si vous avez créé par la suite, vous constaterez que cette modification automatiquement. Si vous souhaitez lire un exemple d’utilisation de cette origine CDN, voir : [hôte votre composant WebPart côté client à partir d’Office 365 CDN (Hello World partie 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Installer et configurer le CDN 365 Office à l’aide de SharePoint Online Management Shell

Les procédures décrites dans cette rubrique nécessitent que vous permet de vous connecter à SharePoint Online SharePoint Online Management Shell. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Effectuez ces étapes pour installer et configurer le CDN 365 Office pour héberger vos ressources statiques dans SharePoint Online.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Pour activer votre organisation d’utiliser le CDN 365 Office

Utilisez l’applet de commande **Set-SPOTenantCdnEnabled** pour permettre à votre organisation d’utiliser le CDN 365 Office. Vous pouvez activer votre organisation d’utiliser des origines publics, origines privés ou les deux avec du CDN. Vous pouvez également configurer le CDN 365 Office pour ignorer l’installation d’origine par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique. 
  
Dans Windows Powershell pour SharePoint Online :
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées avec du CDN, tapez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées avec du CDN mais ignorer la configuration d’origine de la valeur par défaut, tapez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Pour permettre à votre organisation d’utiliser des origines publics avec du CDN, tapez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privés avec du CDN, tapez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette applet de commande, voir [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(Facultatif) Pour modifier la liste des types de fichiers à inclure dans le CDN 365 Office
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez ajouter d’autres types de fichiers à la liste, utilisez l’applet de commande tout d’abord pour découvrir les types de fichiers sont déjà autorisés et les incluent dans la liste, ainsi que les nouvelles. 
  
Utilisez l’applet de commande **Set-SPOTenantCdnPolicy** pour définir les types de fichiers statiques qui peuvent être hébergées par origines publiques et privées dans du CDN. Par défaut, les types de biens courants sont autorisées, pour .js, .gif, .jpg et .css exemple. 
  
Dans Windows PowerShell pour SharePoint Online :
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Pour voir quels types de fichiers actuellement autorisés par le CDN, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(Facultatif) Pour modifier la liste des classifications de site que vous souhaitez exclure à partir du CDN de 365 Office
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Lorsque vous excluez des classifications de sites à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez exclure des classifications de sites supplémentaires, utilisez la cmdlet tout d’abord, à savoir quelles classifications sont déjà exclues et puis ajoutez-les ainsi que les nouvelles. 
  
Utilisez l’applet de commande **Set-SPOTenantCdnPolicy** pour exclure des classifications de sites que vous ne souhaitez pas rendre disponible sur le CDN. Par défaut, aucune classification de site n’est exclues. 
  
Dans Windows PowerShell pour SharePoint Online :
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Pour voir quelles classifications de site sont actuellement restreintes, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="to-add-an-origin-for-your-assets"></a>Pour ajouter une origine pour vos ressources
<a name="Office365CDNforSPOOrigin"> </a>

Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL qui pointe vers une bibliothèque SharePoint ou un dossier qui contient les ressources que vous souhaitez être hébergée par le CDN. 
  
> [!IMPORTANT]
> Si vous identifiez une origine publique dans votre CDN, vous devez placer jamais les ressources qui sont considérés comme critiques pour votre organisation dans l’origine public ou une bibliothèque SharePoint Online. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

Où chemin d’accès est le chemin d’accès au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Par exemple, pour inclure tous les actifs dans le dossier masterpages pour tous vos sites en tant qu’une origine public au sein du CDN, tapez la commande suivante :
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple : Configuration d’une origine publique pour vos pages maîtres et de votre bibliothèque de style pour SharePoint Online
<a name="ExamplePublicOrigin"> </a>

En règle générale, ces origines sont configurés pour vous par défaut lorsque vous activez origines publics pour le CDN 365 Office. Toutefois, si vous souhaitez les activer manuellement, procédez comme suit.
  
- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’une origine public au sein du CDN 365 Office. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir les pages maîtres comme une origine public au sein du CDN 365 Office. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple : Configuration d’une origine privée pour vos éléments de site, pages de site et des images de publications de SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier de ressources de site comme une origine privée au sein du CDN 365 Office. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier de pages de site comme une origine privée au sein du CDN 365 Office. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier images de publication comme une origine privée au sein du CDN 365 Office. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple : Configuration d’une origine privée pour une collection de sites pour SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une collection de sites comme une origine privée au sein du CDN 365 Office. Par exemple, 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.
  
## <a name="manage-the-office-365-cdn"></a>Gérer le Office 365 CDN
<a name="CDNManage"> </a>

Une fois que vous avez configuré le CDN, vous pouvez modifier votre configuration que vous mettez à jour le contenu ou selon vos besoins, comme décrit dans cette section.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>Pour ajouter, mettre à jour ou supprimer des ressources à partir du CDN de 365 Office
<a name="Office365CDNforSPOaddremoveasset"> </a>

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des ressources existantes chaque fois que vous le souhaitez. Simplement, apportez vos modifications pour les biens dans le dossier ou la bibliothèque SharePoint que vous avez identifié comme origine. Si vous ajoutez une nouvelle immobilisation, il est immédiatement disponible par le biais du CDN. Toutefois, si vous mettez à jour l’immobilisation, il prendra jusqu'à 15 minutes pour la nouvelle copie de propagation et deviennent disponibles dans le CDN.
  
Si vous avez besoin récupérer l’emplacement de l’origine, vous pouvez utiliser l’applet de commande **Get-SPOTenantCdnOrigins** . Pour plus d’informations sur l’utilisation de cette applet de commande, voir [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Pour supprimer une origine à partir du CDN de 365 Office
<a name="Office365CDNforSPORemoveOrigin"> </a>

Si vous le souhaitez, vous pouvez supprimer l’accès à un dossier ou une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez l’applet de commande **Remove-SPOTenantCdnOrigin** . Pour plus d’informations sur l’utilisation de cette applet de commande, voir [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Pour modifier une origine dans le CDN 365 Office
<a name="Office365CDNforSPORemoveOrigin"> </a>

Vous ne pouvez pas modifier une origine que vous avez créé. Au lieu de cela, supprimez l’origine, puis ajoutez un nouveau. Pour plus d’informations, consultez [pour supprimer une origine à partir du CDN de 365 Office](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) et [Ajouter une origine pour vos ressources](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
### <a name="to-disable-the-office-365-cdn"></a>Pour désactiver le CDN 365 Office
<a name="Office365CDNforSPODisable"> </a>

Utilisez l’applet de commande **Set-SPOTenantCdnEnabled** pour désactiver le CDN pour votre organisation. Si vous avez deux origines publiques et privées activés pour le CDN, vous devez exécuter l’applet de commande à deux reprises comme indiqué dans les exemples suivants. 
  
Pour désactiver l’utilisation d’origines publics dans du CDN, dans Windows Powershell pour SharePoint Online, entrez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans du CDN, entrez la commande suivante :
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette applet de commande, voir [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Résolution des problèmes de votre configuration Office 365 CDN
<a name="CDNManage"> </a>

Le point de terminaison pas immédiatement sera disponible pour une utilisation, comme le temps requis pour l’inscription d’être propagées par le biais du CDN. Configuration prend 15 minutes.
  

