---
title: QuickStart sur le réseau de distribution de contenu (CDN) Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: QuickStart sur le réseau de distribution de contenu (CDN) Office 365
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561920"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>QuickStart sur le réseau de distribution de contenu (CDN) Office 365

Vous pouvez utiliser le **réseau de distribution de contenu (CDN) Office 365** intégré pour héberger les ressources statiques (images, JavaScript, feuilles de style, fichiers WOFF) afin d’améliorer les performances de vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Par ailleurs, le CDN Office 365 utilise le protocole HTTP/2 pour une compression améliorée et un traitement en pipeline HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour obtenir des conseils plus détaillés [, consultez la rubrique utiliser le réseau de distribution de contenu (CDN) Office 365 avec SharePoint Online](use-office-365-cdn-with-spo.md).

>[!NOTE]
>Le CDN Office 365 est uniquement disponible pour les clients dans le Cloud de production (dans le monde entier). Les clients des nuages des États-Unis, de Chine et d’Allemagne ne prennent actuellement pas en charge le CDN Office 365.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Utiliser l’outil Diagnostics de la page pour SharePoint pour identifier les éléments qui ne sont pas dans le CDN

Vous pouvez utiliser l’extension **des diagnostics de page pour SharePoint Tool** Browser pour répertorier facilement les ressources de vos pages SharePoint Online pouvant être ajoutées à une origine de CDN.

L' **outil Diagnostics de la page pour SharePoint** est une extension de navigateur pour les nouveaux https://www.microsoft.com/edge) navigateurs Microsoft Edge (et de chrome qui analysent à la fois les pages de site de publication classiques et de portail modernes SharePoint Online). L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](https://aka.ms/perftool).

Lorsque vous exécutez l’outil Diagnostics de la page pour SharePoint sur une page SharePoint Online, vous pouvez cliquer sur l’onglet **tests de diagnostic** pour afficher la liste des composants qui ne sont pas hébergés par le CDN. Ces ressources seront répertoriées sous le **contrôle de réseau de distribution de contenu (CDN)** de titre, comme illustré dans la capture d’écran ci-dessous.

![Diagnostics de page](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>L’Outil Diagnostic de page fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

## <a name="cdn-overview"></a>Vue d’ensemble du CDN

Le CDN Office 365 est conçu pour optimiser les performances pour les utilisateurs en distribuant des objets fréquemment utilisés comme des images et des fichiers JavaScript sur un réseau mondial à haut débit, ce qui réduit le temps de chargement des pages et l’accès aux objets hébergés aussi près que possible de l’utilisateur. Le CDN extrait vos biens à partir d’un emplacement appelé _origine_. Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL.

Le CDN Office 365 est séparé en deux types de base :

- Le **CDN public** est conçu pour être utilisé pour js (JavaScript), CSS (feuilles de style), fichier de police Web (WOFF, WOFF2) et images non propriétaires comme les logos de l’entreprise.
- Le **CDN privé** est conçu pour être utilisé pour les images (png, jpg, JPEG, etc.).

Vous pouvez choisir d’avoir à la fois des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux. Les options publiques et privées offrent des gains de performances similaires, mais chacune a des avantages et des attributs uniques. Pour plus d’informations sur les origines de CDN public et privé, voir [choisir si chaque origine doit être publique ou privée](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Procédure d’activation du CDN public et privé avec la configuration par défaut
Avant de modifier les paramètres de CDN du client, vous devez vérifier qu’il répond aux stratégies de conformité, de sécurité et de confidentialité de votre organisation.

Pour plus d’informations sur les paramètres de configuration, ou si vous avez déjà activé le CDN et que vous souhaitez ajouter des emplacements supplémentaires (origines), consultez la section [set up and Configure the Office 365 CDN à l’aide de SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) .

Connectez-vous à votre client à l’aide de SharePoint Online Management Shell :

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées avec la configuration par défaut, tapez la commande suivante :

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

La sortie de ces applets de commande doit ressembler à ce qui suit :

![Sortie de Set-SPOTenantCdnEnabled](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Voir aussi

[Utiliser l’outil de diagnostics de page pour SharePoint Online](https://aka.ms/perftool)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-office-365-cdn-with-spo.md)

[Réseaux de distribution de contenu](https://aka.ms/o365cdns)

[Planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune)

[Série de performances SharePoint-série de vidéos pour le CDN Office 365](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
