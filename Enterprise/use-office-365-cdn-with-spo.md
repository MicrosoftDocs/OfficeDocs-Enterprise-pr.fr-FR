---
title: Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Décrit l’utilisation du réseau de distribution de contenu (CDN) d’Office 365 pour accélérer la remise de vos ressources SharePoint Online à tous vos utilisateurs, où qu’ils soient ou dans lesquels ils accèdent à votre contenu.
ms.openlocfilehash: de8c02b44405260aa7379ab0a881ba72f73c7a6b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070630"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online

Vous pouvez utiliser le réseau de distribution de contenu Office 365 intégré pour héberger des ressources statiques afin d’améliorer les performances de vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Par ailleurs, le CDN Office 365 utilise le [protocole http/2](https://en.wikipedia.org/wiki/HTTP/2) pour une compression améliorée et un traitement en pipeline http. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger sur le réseau de distribution de contenu Office 365, vous pouvez ajouter des origines **publiques**, **privées** ou les deux. Voir [choisir si chaque origine doit être publique ou privée](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) pour plus d’informations sur la différence entre les origines publiques et privées.

![Diagramme conceptuel de CDN Office 365] (media/O365-CDN/o365-cdn-flow-transparent.svg "Diagramme conceptuel de CDN Office 365")

Si vous êtes déjà familiarisé avec la façon dont CDN fonctionne, vous devez uniquement effectuer quelques étapes pour activer le CDN Office 365 pour votre client. Cette rubrique décrit la procédure. Pour plus d’informations sur la prise en main de l’hébergement de vos composants statiques, consultez la rubrique.

> [!TIP]
> Il existe d’autres CDN hébergés par Microsoft qui peuvent être utilisés avec Office 365 pour des scénarios d’utilisation spécialisés, mais qui ne sont pas abordés dans cette rubrique, car ils ne font pas partie de l’étendue du CDN Office 365. Pour plus d’informations, consultez la rubrique [autres Microsoft CDN](content-delivery-networks.md#other-microsoft-cdns).

 **La tête revient à la [planification réseau et au réglage des performances pour Office 365](https://aka.ms/tune).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Vue d’ensemble de l’utilisation du CDN Office 365 dans SharePoint Online

Pour configurer le CDN Office 365 pour votre organisation, procédez comme suit:

- [Planifier le déploiement du CDN Office 365](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - [Déterminez les composants statiques que vous souhaitez héberger sur le CDN](use-office-365-cdn-with-spo.md#CDNAssets).
  - [Déterminez l’emplacement où vous souhaitez stocker vos biens](use-office-365-cdn-with-spo.md#CDNStoreAssets). Cet emplacement peut être un site, une bibliothèque ou un dossier SharePoint et est appelé « _origine_».
  - [Indiquez si chaque origine doit être publique ou privée](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Vous pouvez ajouter plusieurs origines des types publics et privés.

- Installer et configurer le CDN à l’aide de PowerShell ou de l’interface de ligne de commande SharePoint Online

  - [Installer et configurer le CDN à l’aide de SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [Installer et configurer le CDN à l’aide de l’interface CLI Office 365](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  Lorsque vous effectuez cette étape, vous disposez des éléments suivants:

  - Activation du CDN pour votre organisation.
  - Ajout de vos origines, identifiant chaque origine comme étant public ou privé.

Une fois que vous avez terminé l’installation, vous pouvez [gérer le CDN Office 365](use-office-365-cdn-with-spo.md#CDNManage) au fil du temps en procédant comme suit:
  
- Ajout, mise à jour et suppression de ressources
- Ajout et suppression d’origines
- Configuration des stratégies de CDN
- Si nécessaire, désactivation du CDN

Enfin, reportez-vous [à la rubrique utilisation de vos ressources CDN](use-office-365-cdn-with-spo.md#using-your-cdn-assets) pour en savoir plus sur l’accès à vos ressources de CDN à partir d’origines publiques et privées.

Pour obtenir des conseils sur la résolution des problèmes courants, consultez [la rubrique Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planifier le déploiement du CDN Office 365

Avant de déployer le CDN Office 365 pour votre client 365 Office, vous devez prendre en compte les facteurs suivants dans le cadre de votre processus de planification.

  - [Déterminer les ressources statiques que vous souhaitez héberger sur le CDN](use-office-365-cdn-with-spo.md#CDNAssets)
  - [Déterminer où vous souhaitez stocker vos ressources](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [Choisir si chaque origine doit être publique ou privée](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Déterminer les ressources statiques que vous souhaitez héberger sur le CDN
<a name="CDNAssets"> </a>

En règle générale, les CDN sont plus efficaces pour héberger des _composants statiques_ou des ressources qui ne changent pas très souvent. En règle générale, il est recommandé d’identifier les fichiers qui répondent à une partie ou l’ensemble de ces conditions:

- Fichiers statiques incorporés dans une page (par exemple les scripts et les images) qui peuvent avoir un impact significatif sur le chargement des pages
- Fichiers volumineux comme les fichiers exécutables et les fichiers d’installation
- Fichiers multimédias de diffusion en continu
- Bibliothèques de ressources qui prennent en charge le code côté client

Par exemple, les petits fichiers qui sont fréquemment demandés comme les images de site et les scripts peuvent considérablement améliorer les performances de rendu de site et réduire de façon incrémentielle la charge sur vos sites SharePoint Online lorsque vous les ajoutez à une origine de CDN. Des fichiers plus volumineux, tels que des fichiers exécutables ou des fichiers vidéo, peuvent être téléchargés ou diffusés à partir du CDN, ce qui offre un impact positif sur les performances et une réduction ultérieure de la charge sur votre site SharePoint Online, même s’ils ne sont pas utilisés aussi souvent.

L’amélioration des performances en fonction des fichiers dépend de nombreux facteurs, notamment de la proximité du client par le point de terminaison CDN le plus proche, des conditions passagères sur le réseau local, etc. De nombreux fichiers statiques sont relativement petits et peuvent être téléchargés à partir d’Office 365 en moins d’une seconde. Toutefois, une page Web peut contenir un grand nombre de fichiers incorporés avec un temps de téléchargement cumulé de plusieurs secondes. Le traitement de ces fichiers à partir du CDN peut considérablement réduire le temps de chargement global de la page. Voir [Quels sont les gains de performances fournis par un CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) pour obtenir un exemple.

### <a name="determine-where-you-want-to-store-your-assets"></a>Déterminer où vous souhaitez stocker vos ressources
<a name="CDNStoreAssets"> </a>

Le CDN extrait vos biens à partir d’un emplacement appelé _origine_. Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL. Vous disposez d’une grande souplesse lorsque vous spécifiez des origines pour votre organisation. Par exemple, vous pouvez spécifier plusieurs origines ou une seule origine pour placer toutes vos ressources de CDN. Vous pouvez choisir d’avoir à la fois des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux.

Vous pouvez créer un nouveau conteneur pour vos origines, comme des dossiers ou des bibliothèques de documents, et ajouter des fichiers que vous souhaitez mettre à disposition à partir du CDN. Cette approche est intéressante si vous disposez d’un ensemble spécifique de ressources que vous souhaitez mettre à disposition du CDN et que vous souhaitez limiter l’ensemble des ressources CDN uniquement aux fichiers du conteneur.

Vous pouvez également configurer une collection de sites, un site, une bibliothèque ou un dossier existant en tant qu’origine, ce qui rendra tous les composants éligibles dans le conteneur disponible à partir du CDN. Avant d’ajouter un conteneur existant en tant qu’origine, il est important de vous assurer que vous connaissez bien son contenu et ses autorisations afin de ne pas exposer par inadvertance les ressources à l’accès anonyme ou aux utilisateurs non autorisés.

Vous pouvez définir des _stratégies de CDN_ pour exclure le contenu de vos origines du CDN. Les stratégies de CDN excluent les ressources dans les origines publiques ou privées par attributs tels que le _type de fichier_ et la _Classification de site_, et sont appliquées à toutes les origines de l’CdnType (privées ou publiques) que vous spécifiez dans la stratégie. Par exemple, si vous ajoutez une origine privée composée d’un site qui contient plusieurs sous-sites, vous pouvez définir une stratégie pour exclure les sites marqués **** comme confidentiels de sorte que le contenu des sites avec cette classification appliquée ne sera pas pris en charge par le CDN. La stratégie s’applique au contenu de _toutes les_ origines privées que vous avez ajoutées au CDN.
  
Gardez à l’esprit que plus le nombre d’origines est élevé, plus l’impact sur le service CDN est important pour traiter les demandes. Nous vous recommandons de limiter le nombre d’origines autant que possible.
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Choisir si chaque origine doit être publique ou privée
<a name="CDNOriginChoosePublicPrivate"> </a>

Lorsque vous identifiez une origine, vous spécifiez si elle doit être _publique_ ou _privée_. L’accès aux biens CDN dans les origines publiques est anonyme et le contenu CDN des origines privées est sécurisé par des jetons générés dynamiquement pour renforcer la sécurité. Quelle que soit l’option que vous choisissez, Microsoft effectue tout le lourd de levage lorsqu’il s’agit de l’administration du CDN lui-même. Vous pouvez également modifier votre avis ultérieurement, une fois que vous avez configuré le CDN et identifié vos origines.

Les options publiques et privées offrent des gains de performances similaires, mais chacune a des avantages et des attributs uniques.

Les origines **publiques** au sein du CDN Office 365 sont accessibles de manière anonyme, et les ressources hébergées sont accessibles par quiconque dispose de l’URL de la ressource. Comme l’accès au contenu des origines publiques est anonyme, vous ne devez l’utiliser que pour mettre en cache du contenu générique non sensible, comme des scripts, des icônes, des images et des fichiers javascript.

Les origines **privées** du réseau de distribution de contenu Office 365 fournissent un accès privé au contenu des utilisateurs, comme les bibliothèques de documents, les sites et les ressources multimédias (telles que les vidéos) SharePoint Online. L’accès au contenu des origines privées est sécurisé par des jetons générés de manière dynamique afin de permettre uniquement aux utilisateurs disposant d’autorisations sur la bibliothèque de documents ou l’emplacement de stockage d’origine. Les origines privées dans le CDN Office 365 ne peuvent être utilisées que pour le contenu SharePoint Online, et vous pouvez uniquement accéder aux ressources dans des origines privées via la redirection à partir de votre client SharePoint Online.

Pour plus d’informations sur l’accès CDN aux biens dans une origine privée, consultez la rubrique [utilisation des biens dans des origines privées](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attributs et avantages de l’hébergement des biens dans des origines publiques
  
- Les ressources exposées dans une origine publique sont accessibles par tout le monde de manière anonyme.
    > [!IMPORTANT]
    > Vous ne devez jamais placer de ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation dans une origine publique.
- Si vous supprimez une ressource d’une origine publique, celle-ci reste disponible pendant un maximum de 30 jours à partir du cache. Cependant, nous rendons les liens vers la ressource dans le CDN non valides dans les 15 minutes.
- Lorsque vous hébergez des feuilles de style (fichiers CSS) depuis une origine publique, vous pouvez utiliser les URI et les chemins d’accès relatifs dans le code. Cela signifie que vous pouvez faire référence à l’emplacement d’images d’arrière-plan et d’autres objets de manière relative, par rapport à l’emplacement de la ressource qui les appelle.
- Même si vous pouvez coder en dur l’URL d’une origine publique, cette méthode n’est pas recommandée. En effet, si l’accès au CDN devient indisponible, l’URL ne renverra pas automatiquement à votre organisation dans SharePoint Online, ce qui pourrait générer des liens défectueux et d’autres erreurs.
- Les types de fichier par défaut inclus pour les origines publiques sont les suivants : .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf et .woff. Vous pouvez spécifier des types de fichier supplémentaires.
- Vous pouvez configurer une stratégie pour exclure les ressources identifiées par les classifications de site que vous spécifiez. Par exemple, vous pouvez choisir d’exclure toutes les ressources marquées comme « confidentiel » ou « accès réservé », même s’il s’agit d’un type de fichier autorisé et qu’elles ont une origine publique.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attributs et avantages de l’hébergement des biens dans des origines privées

- Les origines privées ne peuvent être utilisées que pour les ressources SharePoint Online.
- Les utilisateurs peuvent accéder aux biens à partir d’une origine privée uniquement s’ils disposent des autorisations nécessaires pour accéder au conteneur. Vous êtes protégé contre l’accès anonyme à ces ressources.
- Les biens dans des origines privées doivent être référencés à partir du client SharePoint Online. L’accès direct aux ressources CDN privées ne fonctionne pas.
- Si vous supprimez un bien de l’origine privée, il se peut que la ressource continue à être disponible pendant une heure au maximum à partir du cache; Toutefois, nous allons invalider les liens vers la ressource dans le CDN dans un délai de 15 minutes après la suppression de l’élément.
- Les types de fichier par défaut inclus pour les origines privées sont les suivants : .gif, .ico, .jpeg, .jpg, .js et .png. Vous pouvez spécifier des types de fichier supplémentaires.
- Tout comme avec les origines publiques, vous pouvez configurer une stratégie pour exclure les ressources identifiées par des classifications de site que vous spécifiez même si vous utilisez des caractères génériques pour inclure toutes les ressources dans un dossier ou une bibliothèque de documents.

Pour plus d’informations sur les raisons d’utiliser le CDN Office 365, les concepts généraux du CDN et d’autres CDN Microsoft que vous pouvez utiliser avec votre client Office 365, consultez la rubrique [Content Delivery Networks](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Origines par défaut du CDN

Sauf indication contraire, Office 365 configure certaines origines par défaut lorsque vous activez le CDN Office 365. Si vous choisissez initialement de ne pas les mettre en service, vous pouvez ajouter ces origines une fois l’installation terminée. À moins que vous ne compreniez les conséquences de l’omission de la configuration des origines par défaut et que vous avez une raison particulière de le faire, vous devez les autoriser à être créées lorsque vous activez le CDN.
  
Origines du CDN privé par défaut:
  
- \*/userphoto.aspx
- \*/siteassets

Origines par défaut du CDN public:
  
- \*/masterpage
- \*Bibliothèque/style
- \*/clientsideassets

> [!NOTE]
> _clientsideassets_ est une origine publique par défaut qui a été ajoutée au service de CDN Office 365 en décembre 2017. Cette origine doit être présente afin que les solutions SharePoint Framework du CDN fonctionnent. Si vous avez activé le CDN Office 365 avant le 2017 décembre, ou si vous avez ignoré le programme d’installation des origines par défaut lorsque vous avez activé le CDN, vous pouvez ajouter manuellement cette origine. Pour plus d’informations, consultez la rubrique [mon composant WebPart côté client ou la solution SharePoint Framework ne fonctionne pas](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Installer et configurer le CDN Office 365 à l’aide de SharePoint Online Management Shell
<a name="CDNSetupinPShell"> </a>

Les procédures décrites dans cette section vous obligent à utiliser SharePoint Online Management Shell pour se connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Procédez comme suit pour installer et configurer le CDN afin d’héberger vos ressources dans SharePoint Online à l’aide de SharePoint Online Management Shell.
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Permettre à votre organisation d’utiliser le CDN Office 365

Avant de modifier les paramètres de CDN de client, vous devez récupérer l’état actuel de la configuration de CDN privé dans votre client Office 365. Connectez-vous à votre client à l’aide de SharePoint Online Management Shell:

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

À présent, utilisez la cmdlet **Get-SPOTenantCdnEnabled** pour récupérer les paramètres d’État CDN à partir du client:

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

L’état du CDN pour le CdnType spécifié s’affiche à l’écran.

Utilisez l’applet de commande **Set-SPOTenantCdnEnabled** pour permettre à votre organisation d’utiliser le CDN Office 365. Vous pouvez permettre à votre organisation d’utiliser des origines publiques, des origines privées ou les deux à la fois. Vous pouvez également configurer le CDN de sorte qu’il ignore le paramétrage des origines par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines plus tard, comme décrit dans cette rubrique.
  
Dans Windows PowerShell pour SharePoint Online:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées, tapez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées, mais de ne pas configurer les origines par défaut, tapez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Consultez la rubrique [origines du CDN par défaut](use-office-365-cdn-with-spo.md#default-cdn-origins) pour obtenir des informations sur les origines qui sont configurées par défaut lorsque vous activez le CDN Office 365, ainsi que l’impact potentiel de l’omission de la configuration des origines par défaut.

Pour permettre à votre organisation d’utiliser des origines publiques, tapez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privées, tapez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette cmdlet, consultez la rubrique [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Modifier la liste des types de fichiers à inclure dans le CDN Office 365 (facultatif)
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de la cmdlet **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez ajouter d’autres types de fichiers à la liste, utilisez d’abord la cmdlet pour savoir quels types de fichiers sont déjà autorisés et les inclure dans la liste en même temps que les nouveaux.
  
La cmdlet **Set-SPOTenantCdnPolicy** permet de définir des types de fichiers statiques qui peuvent être hébergés par des origines publiques et privées dans le CDN. Par défaut, les types d’éléments communs sont autorisés, par exemple. CSS,. gif,. jpg et. js.

Dans Windows PowerShell pour SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Par exemple, pour permettre au CDN d’héberger des fichiers. CSS et. png, entrez la commande suivante:

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Pour voir les types de fichiers actuellement autorisés par le CDN, utilisez la cmdlet **Get-SPOTenantCdnPolicies** :

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Modifier la liste des classifications de sites que vous souhaitez exclure du CDN Office 365 (facultatif)
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Lorsque vous excluez les classifications de site à l’aide de la cmdlet **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez exclure des classifications de site supplémentaires, utilisez d’abord la cmdlet pour savoir quelles classifications sont déjà exclues, puis ajoutez-les en même temps que les nouvelles classifications.

Utilisez la cmdlet **Set-SPOTenantCdnPolicy** pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

Dans Windows PowerShell pour SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Pour voir les classifications de site actuellement restreintes, utilisez la cmdlet **Get-SPOTenantCdnPolicies** :

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Les propriétés qui seront renvoyées sont _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ et _ExcludeIfNoScriptDisabled_.

La propriété _IncludeFileExtensions_ contient la liste des extensions de fichiers qui seront fournies à partir du CDN.

> [!NOTE]
> Les extensions de fichier par défaut sont différentes entre public et Private.

La propriété _ExcludeRestrictedSiteClassifications_ contient les classifications de site que vous souhaitez exclure du CDN. Par exemple, vous pouvez exclure des sites marqués **** comme confidentiels de sorte que le contenu de sites avec cette classification appliquée ne sera pas pris en charge par le CDN.

La propriété _ExcludeIfNoScriptDisabled_ exclut le contenu du CDN en fonction des paramètres d’attribut _NoScript_ au niveau du site. Par défaut, l’attribut _NoScript_ est défini sur **activé** pour les sites _modernes_ et **désactivé** pour les sites _classiques_ . Cela dépend de vos paramètres de client.

Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="add-an-origin-for-your-assets"></a>Ajouter une origine pour vos biens
<a name="Office365CDNforSPOOrigin"> </a>

Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.
  
> [!IMPORTANT]
> Vous ne devez jamais placer de ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation dans une origine publique.

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

La valeur _path_ est le chemin d’accès relatif à la bibliothèque ou au dossier qui contient les composants. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Les origines prennent en charge les caractères génériques ajoutés à l’URL. Cela vous permet de créer des origines qui s’étendent sur plusieurs sites. Par exemple, pour inclure toutes les ressources dans le dossier MasterPages pour tous vos sites en tant qu’origine publique dans le CDN, tapez la commande suivante:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- Le modificateur de caractère**/** générique * peut uniquement être utilisé au début du chemin d’accès et correspondra à tous les segments d’URL sous l’URL spécifiée.
- Le chemin d’accès peut pointer vers une bibliothèque de documents, un dossier ou un site. Par exemple, le chemin d’accès _*/site1_ correspondra à toutes les bibliothèques de documents sous le site.

Vous pouvez ajouter une origine avec un chemin d’accès relatif spécifique. Vous ne pouvez pas ajouter d’origine à l’aide du chemin d’accès complet.

Cet exemple ajoute une origine privée de la bibliothèque éléments sur un site spécifique:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Cet exemple ajoute une origine privée du dossier _dossier1_ dans la bibliothèque de sites de la collection de sites:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

> [!NOTE]
> Dans les origines privées, les biens partagés à partir d’une origine doivent avoir une version majeure publiée pour pouvoir être accessibles à partir du CDN.
  
Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de l’expérience. Cela peut prendre jusqu’à 15 minutes.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple: configurer une origine publique pour vos pages maîtres et pour votre bibliothèque de styles pour SharePoint Online
<a name="ExamplePublicOrigin"> </a>

Normalement, ces origines sont définies par défaut lorsque vous activez le CDN Office 365. Toutefois, si vous souhaitez les activer manuellement, procédez comme suit.
  
- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir la bibliothèque de styles comme origine publique.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir les pages maîtres comme une origine publique.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de l’expérience. Cela peut prendre jusqu’à 15 minutes.

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple: configurer une origine privée pour vos ressources de site, pages de site et images de publication pour SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier des éléments de site comme origine privée.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier des pages de site comme origine privée.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier Publishing images comme origine privée.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de l’expérience. Cela peut prendre jusqu’à 15 minutes.

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple: configurer une origine privée pour une collection de sites pour SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

La cmdlet **Add-SPOTenantCdnOrigin** permet de définir une collection de sites en tant qu’origine privée. Par exemple :

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de l’expérience. Il se peut que vous rencontriez un message de _configuration en attente_ qui est attendu lorsque le client SharePoint Online se connecte au service CDN. Cela peut prendre jusqu’à 15 minutes.

### <a name="manage-the-office-365-cdn"></a>Gérer le CDN Office 365
<a name="CDNManage"> </a>

Une fois que vous avez configuré le CDN, vous pouvez modifier votre configuration lors de la mise à jour du contenu ou à mesure que vos besoins changent, comme décrit dans cette section.
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Ajouter, mettre à jour ou supprimer des ressources du CDN Office 365
<a name="Office365CDNforSPOaddremoveasset"> </a>

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources, ainsi que mettre à jour ou supprimer des biens existants chaque fois que vous le souhaitez. Modifiez simplement les ressources dans le dossier ou la bibliothèque SharePoint que vous avez identifiée comme origine. Si vous ajoutez une nouvelle ressource, elle est immédiatement disponible via le CDN. Toutefois, si vous mettez à jour l’élément, la propagation de la nouvelle copie peut prendre jusqu’à 15 minutes et devenir disponible dans le CDN.
  
Si vous avez besoin de récupérer l’emplacement de l’origine, vous pouvez utiliser la cmdlet **Get-SPOTenantCdnOrigins** . Pour plus d’informations sur l’utilisation de cette cmdlet, consultez la rubrique [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Supprimer une origine du CDN Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Vous pouvez supprimer l’accès à un dossier ou à une bibliothèque SharePoint que vous avez identifiée comme origine. Pour ce faire, utilisez la cmdlet **Remove-SPOTenantCdnOrigin** .

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Pour plus d’informations sur l’utilisation de cette cmdlet, consultez la rubrique [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modifier une origine dans le CDN Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Vous ne pouvez pas modifier une origine que vous avez créée. Au lieu de cela, supprimez l’origine, puis ajoutez-en une nouvelle. Pour plus d’informations, reportez-vous [à la rubrique pour supprimer une origine du CDN Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) et [Ajouter une origine pour vos biens](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
#### <a name="disable-the-office-365-cdn"></a>Désactiver le CDN Office 365
<a name="Office365CDNforSPODisable"> </a>

La cmdlet **Set-SPOTenantCdnEnabled** permet de désactiver le CDN pour votre organisation. Si vous avez à la fois les origines publique et privée activées pour le CDN, vous devez exécuter l’applet de commande deux fois, comme illustré dans les exemples suivants.
  
Pour désactiver l’utilisation des origines publiques dans le CDN, entrez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans le CDN, entrez la commande suivante:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette cmdlet, consultez la rubrique [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Installation et configuration du CDN Office 365 à l’aide de la CLI Office 365
<a name="CDNSetupinCLI"> </a>

Les procédures décrites dans cette section nécessitent l’installation de l' [interface CLI Office 365](https://aka.ms/o365cli). Ensuite, connectez-vous à votre client SharePoint Online à l’aide de la commande [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/).

Suivez ces étapes pour installer et configurer le CDN afin d’héberger vos ressources dans SharePoint Online à l’aide de l’interface de ligne de commande Office 365.

### <a name="enable-the-office-365-cdn"></a>Activer le CDN Office 365

Vous pouvez gérer l’état du CDN Office 365 dans votre client à l’aide de la commande [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).

Pour activer le CDN public Office 365 dans votre client exécutez la commande suivante :

```sh
spo cdn set --type Public --enabled true
```

Pour activer le CDN Office 365 SharePoint, exécutez:

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Affichage de l’état actuel du CDN Office 365

Pour vérifier si le type particulier de CDN Office 365 est activé ou désactivé, utilisez la commande [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .

Pour vérifier si le CDN public Office 365 est activé, exécutez la commande suivante :

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Afficher les origines du CDN Office 365

Pour afficher les origines actuellement configurées du CDN public Office 365, exécutez la commande suivante :

```sh
spo cdn origin list --type Public
```

Consultez la rubrique [origines du CDN par défaut](use-office-365-cdn-with-spo.md#default-cdn-origins) pour obtenir des informations sur les origines qui sont configurées par défaut lorsque vous activez le CDN Office 365.

### <a name="add-an-office-365-cdn-origin"></a>Ajouter une origine de CDN Office 365

> [!IMPORTANT]
> Vous ne devez jamais placer de ressources sensibles à votre organisation dans une bibliothèque de documents SharePoint configurée comme une origine publique.

Utilisez la commande [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) pour définir une origine de CDN. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

Où `path` est le chemin d’accès relatif au dossier qui contient les biens. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs.

Pour inclure toutes les ressources de la **Galerie de pages maîtres** de tous les sites en tant qu’origine publique, exécutez:

```sh
spo cdn origin add --type Public --origin */masterpage
```

Pour configurer une origine privée pour une collection de sites spécifique, exécutez la commande suivante :

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Après l’ajout d’une origine de CDN, un délai de 15 minutes maximum peut être nécessaire avant que vous ne puissiez récupérer des fichiers par le biais du service de CDN. Vous pouvez vérifier si l’origine spécifique a déjà été activée à l’aide la commande [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).

### <a name="remove-an-office-365-cdn-origin"></a>Supprimer une origine de CDN Office 365

Utilisez la commande [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) pour supprimer une origine de CDN pour le type de CDN spécifié.

Pour supprimer une origine publique de la configuration du CDN, exécutez:

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> La suppression d’une origine de CDN n’affecte pas les fichiers stockés dans une bibliothèque de documents correspondant à cette origine. Si ces ressources ont été référencées à l’aide de leur URL SharePoint, SharePoint revient automatiquement à l’URL d’origine pointant vers la bibliothèque de documents. Toutefois, si des ressources ont été référencées à l’aide d’une URL de CDN public, la suppression de l’origine rompt le lien et vous devez les modifier manuellement.

### <a name="modify-an-office-365-cdn-origin"></a>Modifier une origine de CDN Office 365

Il n’est pas possible de modifier une origine de CDN existante. Vous devez plutôt supprimer l’origine de CDN définie précédemment à l’aide de la commande `spo cdn origin remove` et en ajouter une nouvelle à l’aide de la commande `spo cdn origin add`.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Modifier les types de fichiers à inclure dans le CDN Office 365

Par défaut, les types de fichier suivants sont inclus dans le CDN : _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf et .woff_. Si vous devez inclure des types de fichier supplémentaires dans le CDN, vous pouvez modifier la configuration du CDN à l’aide de la commande [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Lorsque vous modifiez la liste des types de fichier, vous remplacez la liste actuellement définie. Pour inclure des types de fichier supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) afin de vérifier les types de fichier qui sont actuellement configurés.

Pour ajouter le type de fichier _JSON_ à la liste par défaut des types de fichiers inclus dans le CDN public, exécutez:

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Modification de la liste des classifications de site que vous souhaitez exclure du CDN Office 365

Utilisez la commande [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

> [!NOTE]
> Lorsque vous modifiez la liste des classifications de site exclues, vous remplacez la liste actuellement définie. Pour exclure des classifications supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) afin de vérifier les classifications qui sont actuellement configurées.

Pour exclure les sites classés comme _IEA_ du CDN public, exécutez

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Désactiver le CDN Office 365

Pour désactiver le CDN Office 365, utilisez la commande `spo cdn set`, par exemple :

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a>Utilisation de vos ressources CDN

À présent que vous avez activé le CDN et les origines et les stratégies configurées, vous pouvez commencer à utiliser vos ressources CDN.

Cette section vous aidera à comprendre comment utiliser les URL du CDN dans vos pages et votre contenu SharePoint afin que SharePoint redirige les demandes d’actifs dans les origines publiques et privées vers le CDN.

- [Mise à jour des liens vers les éléments CDN](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [Utilisation des biens dans des origines publiques](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [Utilisation des biens dans les origines privées](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

Pour plus d’informations sur l’utilisation du CDN pour l’hébergement de composants WebPart côté client, consultez la rubrique [héberger votre composant WebPart côté client à partir d’Office 365 CDN (Hello World quatrième partie)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

### <a name="updating-links-to-cdn-assets"></a>Mise à jour des liens vers les éléments CDN

Pour utiliser des biens que vous avez ajoutés à une origine, il vous suffit de mettre à jour les liens vers le fichier d’origine avec le chemin d’accès au fichier dans l’origine.

- Modifier la page ou le contenu qui contient des liens vers des ressources que vous avez ajoutées à une origine. Vous pouvez également utiliser l’une des méthodes suivantes pour rechercher et remplacer des liens dans une collection de sites ou de sites si vous souhaitez mettre à jour le lien vers un élément donné partout où il apparaît.
- Pour chaque lien vers un élément dans une origine, remplacez le chemin d’accès par le chemin d’accès au fichier dans l’origine du CDN. Vous pouvez utiliser des chemins d’accès relatifs.
- Enregistrez la page ou le contenu.

Par exemple, considérez l’image _/site/SiteAssets/images/image.png_, que vous avez copiée dans le dossier de la bibliothèque de documents _/site/CDN_origins/public/_. Pour utiliser l’élément CDN, remplacez le chemin d’accès d’origine de l’emplacement du fichier image par le chemin d’accès à l’origine pour créer la nouvelle URL _/site/CDN_origins/public/image.png_.

Si vous souhaitez utiliser l’URL complète de l’élément au lieu d’un chemin d’accès relatif, construisez le lien comme suit:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> En règle générale, vous ne devez pas coder les URL directement dans les ressources du CDN. Toutefois, vous pouvez créer manuellement des URL pour des biens dans des origines publiques si nécessaire. Pour plus d’informations, consultez la rubrique relative [aux URL de CDN en dur pour les biens publics](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).

Pour en savoir plus sur la façon de vérifier que les biens sont pris en charge par le CDN, voir [Comment puis-je vérifier que les biens sont pris en charge par le CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) dans la section [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .

### <a name="using-assets-in-public-origins"></a>Utilisation des biens dans des origines publiques

La **fonctionnalité de publication** de SharePoint Online réécrit automatiquement les URL des biens stockés dans des origines publiques vers leurs équivalents CDN afin que les biens soient pris en charge par le service CDN au lieu de SharePoint.

Si votre origine se trouve dans un site où la fonctionnalité de publication est activée et que les ressources que vous souhaitez décharger vers le CDN se trouvent dans l’une des catégories suivantes, SharePoint réécrit automatiquement les URL des biens de l’origine, à condition que l’actif n’ait pas été exclu par un CDN.  renvoi.

Voici un aperçu des liens qui sont réécrits automatiquement par la fonctionnalité de publication SharePoint :

- URL IMG/LINK/CSS dans les réponses HTML de pages de publications classiques
  - Cela comprend les images ajoutées par des auteurs dans le contenu HTML d’une page.
- URL d’images de composants WebPart de diaporamas de bibliothèque d’images
- Champs d’image dans les résultats d’API REST SPList (RenderListDataAsStream)
  - Utiliser la nouvelle propriété _ImageFieldsToTryRewriteToCdnUrls_ pour fournir une liste de champs séparés par des virgules
  - Prend en charge les champs de lien hypertexte et PublishingImage
- Rendus d’image SharePoint

Le diagramme suivant illustre le flux de travail lorsque SharePoint reçoit une demande pour une page contenant des biens provenant d’une origine publique.

![Diagramme de flux de travail: récupération des composants de CDN Office 365 à partir d’une origine publique] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "Flux de travail: extraction des ressources CDN Office 365 d’une origine publique")

> [!TIP]
> Si vous souhaitez désactiver la réécriture automatique pour des URL spécifiques sur une page, vous pouvez extraire la page et ajouter le paramètre de chaîne de requête **?NoAutoReWrites = true** à la fin de chaque lien que vous souhaitez désactiver.

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>URL de CDN en dur pour les ressources publiques

Si la fonctionnalité de _publication_ n’est pas activée pour une origine publique ou si l’élément n’est pas l’un des types de liens pris en charge par la fonctionnalité de réécriture automatique du service CDN, vous pouvez créer manuellement des URL vers l’emplacement du CDN des biens et utiliser ces URL dans votre contenu.

> [!NOTE]
> Vous ne pouvez pas coder en dur les URL de CDN vers des biens dans une origine privée car le jeton d’accès requis qui forme la dernière section de l’URL est généré au moment de la demande de la ressource.

Pour les ressources de CDN public, le format de l’URL se présente comme suit:

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Remplacez **TenantHostName** par le nom de votre client. Exemple :

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>Utilisation des biens dans les origines privées

Aucune configuration supplémentaire n’est requise pour utiliser des biens dans des origines privées. SharePoint Online réécrit automatiquement des URL pour des biens dans des origines privées, de sorte que les demandes de ces ressources seront toujours traitées à partir du CDN. Vous ne pouvez pas créer manuellement des URL vers des éléments CDN dans des origines privées car ces URL contiennent des jetons qui doivent être générés automatiquement par SharePoint Online au moment de la demande de la ressource.

L’accès aux biens dans des origines privées est protégé par des jetons générés de manière dynamique en fonction des autorisations des utilisateurs pour l’origine, avec les limitations décrites dans les sections suivantes. Les utilisateurs doivent disposer au moins d’un accès **en lecture** à l’origine du CDN pour afficher le contenu.

Le diagramme suivant illustre le flux de travail lorsque SharePoint reçoit une demande pour une page contenant des ressources provenant d’une origine privée.

![Diagramme de flux de travail: récupération des composants de CDN Office 365 à partir d’une origine privée] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "Flux de travail: extraction des composants CDN Office 365 d’une origine privée")

#### <a name="token-based-authorization-in-private-origins"></a>Autorisation basée sur des jetons dans les origines privées

L’accès aux biens dans les origines privées dans le CDN Office 365 est accordé par des jetons générés par SharePoint Online. Les utilisateurs qui ont déjà l’autorisation d’accéder au dossier ou à la bibliothèque désigné par l’origine reçoivent automatiquement des jetons qui permettent à l’utilisateur d’accéder au fichier en fonction de son niveau d’autorisation. Ces jetons d’accès sont valides entre 30 et 90 minutes après leur génération afin d’empêcher les attaques par relecture de jetons.

Une fois que le jeton d’accès est généré, SharePoint Online renvoie un URI personnalisé vers le client contenant deux paramètres d’autorisation _manger_ (jeton d’autorisation Edge) et _avoine_ (jeton d’autorisation d’origine). La structure de chaque jeton est _<'expiration temps de Format'>__<'secure signature'>_. Par exemple :

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Toute personne en possession du jeton peut accéder à la ressource dans le CDN. Toutefois, les URL contenant ces jetons d’accès sont partagées uniquement via HTTPs, de sorte que, sauf si l’URL est explicitement partagée par un utilisateur final avant l’expiration du jeton, ce dernier n’est pas accessible aux utilisateurs non autorisés.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Les autorisations au niveau des éléments ne sont pas prises en charge pour les biens dans les origines privées

Il est important de noter que SharePoint Online ne prend pas en charge les autorisations au niveau des éléments dans les origines privées. Par exemple, pour un fichier se trouvant à `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, les utilisateurs ont un accès effectif au fichier en fonction des conditions suivantes:

|Utilisateur  |Autorisations  |Accès effectif  |
|---------|---------|---------|
|Utilisateur 1     |A accès à dossier1         |Peut accéder à image1. jpg à partir du CDN         |
|Utilisateur 2     |N’a pas accès à dossier1         |Impossible d’accéder à image1. jpg à partir du CDN         |
|Utilisateur 3     |N’a pas accès à Dossier1, mais dispose d’une autorisation explicite pour accéder à image1. jpg dans SharePoint Online         |Peut accéder à la ressource image1. jpg directement à partir de SharePoint Online, mais pas à partir du CDN         |
|Utilisateur 4     |A accès à Dossier1, mais l’accès à image1. jpg a été explicitement refusé dans SharePoint Online         |Impossible d’accéder au bien à partir de SharePoint Online, mais peut accéder à l’élément à partir du CDN malgré le fait que l’accès au fichier est refusé dans SharePoint Online         |

## <a name="troubleshooting-the-office-365-cdn"></a>Dépannage du CDN Office 365
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Comment puis-je vérifier que les biens sont pris en charge par le CDN?
<a name="CDNConfirm"> </a>

Une fois que vous avez ajouté des liens vers des ressources CDN à une page, vous pouvez confirmer que l’élément est pris en charge par le CDN en accédant à la page, en cliquant avec le bouton droit sur l’image une fois qu’elle a affiché et vérifié l’URL de l’image.

Vous pouvez également utiliser les outils de développement de votre navigateur pour afficher l’URL de chaque ressource sur une page ou utiliser un outil de suivi réseau tiers.

> [!NOTE]
> Si vous utilisez un outil réseau tel que Fiddler pour tester vos biens en dehors du rendu de l’élément à partir d’une page SharePoint, vous devez ajouter manuellement l’en `https://yourdomain.sharepoint.com`-tête de renvoi «Referrer:» à la requête get où l’URL est l’URL racine de votre client SharePoint Online.

Vous ne pouvez pas tester les URL du CDN directement dans un navigateur Web, car vous devez disposer d’un référent provenant de SharePoint Online. Toutefois, si vous ajoutez l’URL de la ressource CDN à une page SharePoint, puis ouvrez la page dans un navigateur, vous verrez l’élément CDN s’afficher sur la page.

Pour plus d’informations sur l’utilisation des outils de développement dans le navigateur Microsoft Edge, consultez la rubrique [outils de développement Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Pourquoi les biens d’une nouvelle origine ne sont-ils pas disponibles?
Les biens dans de nouvelles origines ne seront pas immédiatement disponibles à l’utilisation, car le temps nécessaire pour que l’inscription se propage via le CDN et que les biens soient chargés du stockage de l’origine vers le CDN. Le temps nécessaire pour que les biens soient disponibles dans le CDN dépend du nombre de ressources et de tailles de fichiers.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mon composant WebPart côté client ou la solution SharePoint Framework ne fonctionne pas

Lorsque vous activez le CDN Office 365 pour les origines publiques, le service CDN crée automatiquement ces origines par défaut:

- */MASTERPAGE
- * BIBLIOTHÈQUE/STYLE
- */CLIENTSIDEASSETS

Si l’origine */clientsideassets est manquante, les solutions de l’infrastructure SharePoint échouent et aucun message d’avertissement ou d’erreur n’est généré. Cette origine peut être manquante, car le CDN a été activé avec le paramètre _-NoDefaultOrigins_ défini sur **$true**ou parce que l’origine a été supprimée manuellement.

Vous pouvez vérifier si l’origine */CLIENTSIDEASSETS est présente à l’aide de la commande PowerShell suivante:

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Ou vous pouvez consulter la CLI Office 365:

``` powershell
spo cdn origin list
```

Pour ajouter l’origine dans PowerShell:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Pour ajouter l’origine dans l’interface CLI Office 365:

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Quels modules PowerShell et shells CLI dois-je utiliser avec le CDN Office 365?

Vous pouvez choisir de travailler avec le CDN Office 365 à l’aide du module PowerShell de **SharePoint Online Management Shell** ou de l’interface de ligne de **commande Office 365**.

- [Prise en main de SharePoint Online Management Shell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [Installation d’Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Voir aussi

[Réseaux de distribution de contenu](https://aka.ms/o365cdns)

[Planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune)

