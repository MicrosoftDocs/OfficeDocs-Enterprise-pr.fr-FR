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
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540356"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="1ac64-103">Utiliser le réseau de distribution de contenu Office 365 avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1ac64-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="1ac64-p101">Vous pouvez héberger des biens statiques dans le réseau de distribution de contenu (CDN) Office 365 pour améliorer les performances de vos pages SharePoint Online. Ressources statiques sont des fichiers qui ne changent pas très souvent, comme les images, vidéo et audio, des feuilles de style, les polices et fichiers JavaScript. Le CDN fonctionne comme un proxy de mise en cache distribué géographiquement, en mettant en cache les biens statiques rapprocher pour les navigateurs les demandant.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="1ac64-p102">Si vous êtes déjà familiarisé avec la façon dont les CDN, vous devez uniquement effectuer quelques étapes pour la configurer. Cette rubrique décrit comment. Lecture pour plus d’informations sur le CDN 365 Office et la mise en route qui héberge vos ressources statiques.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="1ac64-110">**Tête de retour à la [planification du réseau et réglage des performances pour Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="1ac64-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="1ac64-111">Notions de base sur Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="1ac64-111">Office 365 CDN basics</span></span>

<span data-ttu-id="1ac64-p103">Le CDN 365 Office est inclus dans le cadre de votre abonnement SharePoint Online. Vous n’êtes pas obligé de payer supplémentaire. Office 365 fournit la prise en charge pour les deux privé et accès public et vous permet aux biens statique hôte dans plusieurs emplacements ou origines. Le CDN 365 Office n’est pas le même que le CDN Azure. Si vous avez besoin de plus d’informations sur les raisons d’utiliser un CDN ou sur les concepts généraux relatifs CDN, voir [réseaux de distribution de contenu](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="1ac64-117">Comment le CDN permet d’accéder aux utilisateurs finaux</span><span class="sxs-lookup"><span data-stu-id="1ac64-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="1ac64-p104">Accès privé aux biens statiques dans le CDN 365 Office est affecté par les jetons générés par SharePoint Online. Les utilisateurs qui ont déjà l’autorisation d’accéder au dossier ou bibliothèque désigné par l’origine seront accordées automatiquement jetons. SharePoint Online ne prend pas en charge autorisations au niveau de l’élément pour du CDN.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="1ac64-121">Par exemple, pour un fichier situé dans le `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, étant donné les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1ac64-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="1ac64-122">L’utilisateur 1 dispose d’un accès pour folder1 et image1.jpg</span><span class="sxs-lookup"><span data-stu-id="1ac64-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="1ac64-123">L’utilisateur 2 n’a pas accès aux dossiers folder1</span><span class="sxs-lookup"><span data-stu-id="1ac64-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="1ac64-124">Utilisateur 3 n’a pas accès aux dossiers folder1 mais est l’autorisation explicite d’accéder à image1.jpg via SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1ac64-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="1ac64-125">Utilisateur 4 a accès aux dossiers folder1 mais a été explicitement refusé l’accès à image1.jpg</span><span class="sxs-lookup"><span data-stu-id="1ac64-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="1ac64-126">Puis les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="1ac64-126">Then the following are true:</span></span>
  
- <span data-ttu-id="1ac64-127">L’utilisateur 1 et 4 de l’utilisateur sera en mesure d’accéder aux image1.jpg par le biais du CDN.</span><span class="sxs-lookup"><span data-stu-id="1ac64-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="1ac64-128">L’utilisateur 2 et 3 de l’utilisateur ne sera pas en mesure d’accéder aux image1.jpg par le biais du CDN.</span><span class="sxs-lookup"><span data-stu-id="1ac64-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="1ac64-129">Toutefois, utilisateur 3 peut toujours accéder les biens image1.jpg via SharePoint Online, pendant que l’utilisateur 4 ne peut pas accéder à la ressource via SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1ac64-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="1ac64-130">Vue d’ensemble de l’utilisation du CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="1ac64-131">Pour configurer le CDN 365 Office, vous suivez ces étapes de base :</span><span class="sxs-lookup"><span data-stu-id="1ac64-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="1ac64-132">Planifier un déploiement CDN :</span><span class="sxs-lookup"><span data-stu-id="1ac64-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="1ac64-p105">Connaître les ressources statiques vous souhaitez héberger sur le CDN 365 Office. Pour plus d’informations sur la façon d’apporter ces choix, reportez-vous aux [réseaux de distribution de contenu](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="1ac64-p106">[Déterminer où vous souhaitez stocker vos actifs](use-office-365-cdn-with-spo.md#CDNStoreAssets). Cet emplacement est un dossier ou une bibliothèque SharePoint et est appelé une origine.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="1ac64-p107">Déterminer si les éléments doivent être rendues publiques ou confidentiel. Vous faire lorsque vous [Choisissez si chaque origine doit être publiques ou privées](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Si vous le souhaitez, vous pouvez avoir plusieurs origines dans laquelle certaines sont publics, et certaines sont privés.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="1ac64-p108">[Définir installation et configuration du CDN 365 Office à l’aide de SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Lorsque vous avez terminé cette étape, vous devez :</span><span class="sxs-lookup"><span data-stu-id="1ac64-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="1ac64-142">Extension du CDN pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="1ac64-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="1ac64-p109">Ajouté votre origines. Vous identifier chaque origine comme public ou private.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="1ac64-145">Une fois terminé le programme d’installation, [Gérer les CDN 365 Office](use-office-365-cdn-with-spo.md#CDNManage) au fil du temps par :</span><span class="sxs-lookup"><span data-stu-id="1ac64-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="1ac64-146">Ajout, mise à jour et suppression d’actifs</span><span class="sxs-lookup"><span data-stu-id="1ac64-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="1ac64-147">Ajout et suppression d’origine</span><span class="sxs-lookup"><span data-stu-id="1ac64-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="1ac64-148">Configuration des stratégies CDN</span><span class="sxs-lookup"><span data-stu-id="1ac64-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="1ac64-149">Si nécessaire, la désactivation du CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="1ac64-150">Déterminer où vous souhaitez stocker vos ressources</span><span class="sxs-lookup"><span data-stu-id="1ac64-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="1ac64-p110">Le CDN extrait vos ressources à partir d’un emplacement de l’origine. Pour Office 365, une origine est une bibliothèque SharePoint ou un dossier accessible par une URL. Vous avez une grande souplesse lorsque vous spécifiez origines pour votre organisation. Par exemple, vous pouvez spécifier plusieurs origines, ou, une seule origine où vous souhaitez placer tous vos actifs CDN. Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations seront choisir d’implémenter une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="1ac64-p111">Si vous définissez des centaines d’origines, il sera probablement avoir un impact négatif sur le temps que nécessaire pour traiter les demandes. Il est recommandé que si vous avez plus de 100 origines vous souhaitez concevoir de nouveau votre architecture.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="1ac64-159">Choisissez si chaque origine doit être publiques ou privées</span><span class="sxs-lookup"><span data-stu-id="1ac64-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="1ac64-p112">Lorsque vous identifiez une origine, vous spécifiez s’il doit être rendu public ou privé. Quel que soit l’option que vous choisissez, Microsoft fait l’essentiel pour vous lorsqu’il s’agit de l’administration du CDN proprement dit. En outre, vous pouvez modifier votre avis ultérieurement, une fois que vous avez configuré le CDN et identifié votre origines.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="1ac64-163">Options publiques et privées améliorent les performances, mais chacun présente des avantages et des attributs uniques.</span><span class="sxs-lookup"><span data-stu-id="1ac64-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="1ac64-164">**Attributs et les avantages de l’hébergement des biens dans une origine publique**</span><span class="sxs-lookup"><span data-stu-id="1ac64-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="1ac64-165">Biens exposées dans une origine public sont accessibles par tout le monde accès anonyme.</span><span class="sxs-lookup"><span data-stu-id="1ac64-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="1ac64-166">Si vous identifiez une origine publique dans votre CDN, vous devez placer jamais les ressources qui sont considérés comme critiques pour votre organisation dans une origine public ou une bibliothèque SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1ac64-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="1ac64-167">Si vous supprimez un bien à partir d’une origine publique, bien peut continuer à être disponible pendant 30 jours à partir du cache ; Toutefois, nous affectera des liens vers les biens dans le CDN après 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="1ac64-p113">Lorsque vous hébergez les feuilles de style (fichiers CSS) dans une origine publique, vous pouvez utiliser les URI et les chemins d’accès relatifs dans le code. Cela signifie que vous pouvez faire référence à l’emplacement des images d’arrière-plan et d’autres objets par rapport à l’emplacement de l’immobilisation qui l’appelle.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="1ac64-p114">Alors que vous pouvez coder les URL d’une origine public, cela est déconseillé. La raison en est que si l’accès du CDN devient indisponible, l’URL ne résout pas automatiquement à votre organisation dans SharePoint Online et liens rompus et les autres erreurs pouvant entraîner.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="1ac64-p115">Les types de fichiers par défaut qui sont inclus pour origines publics sont .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf et .woff. Vous pouvez spécifier les types de fichiers supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="1ac64-p116">Si vous le souhaitez, vous pouvez configurer une stratégie pour exclure les éléments qui ont été identifiés par des classifications de site que vous spécifiez. Par exemple, vous pouvez choisir d’exclure tous les actifs qui sont marqués comme étant « confidentiel » ou « restreint » même si elles sont un type de fichier autorisés et se trouvent dans une origine publique.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="1ac64-176">**Attributs et les avantages de l’hébergement des biens dans une origine privée**</span><span class="sxs-lookup"><span data-stu-id="1ac64-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="1ac64-p117">Les utilisateurs accèdent uniquement les ressources à partir d’une origine privée si elles sont autorisés à le faire. L’accès anonyme à ces actifs est bloquée.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="1ac64-179">Si vous supprimez un bien à l’origine privée, bien peut continuer à être disponible pour jusqu'à une heure à partir du cache ; Toutefois, nous affectera des liens vers les biens dans le CDN après 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="1ac64-p118">Les types de fichiers par défaut qui sont inclus pour origines privées sont .ico, .gif, .jpeg, .jpg, .js et .png. Vous pouvez spécifier les types de fichiers supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="1ac64-182">À l’instar des origines publics, vous pouvez configurer une stratégie pour exclure les éléments qui ont été identifiés par des classifications de site que vous spécifiez la même si vous utilisez des caractères génériques pour inclure tous les éléments dans un dossier ou une bibliothèque de Site.</span><span class="sxs-lookup"><span data-stu-id="1ac64-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="1ac64-183">Origines d’Office 365 CDN par défaut</span><span class="sxs-lookup"><span data-stu-id="1ac64-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="1ac64-p119">Sauf indication contraire, Office 365 organise des origines par défaut pour vous lorsque vous activez le CDN 365 Office. Si vous les excluez à l’origine, vous pouvez ajouter ces origines après avoir terminé le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="1ac64-186">Origines privées par défaut :</span><span class="sxs-lookup"><span data-stu-id="1ac64-186">Default private origins:</span></span>
  
- <span data-ttu-id="1ac64-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="1ac64-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="1ac64-188">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="1ac64-188">\*/siteassets</span></span>
    
<span data-ttu-id="1ac64-189">Origines publics par défaut :</span><span class="sxs-lookup"><span data-stu-id="1ac64-189">Default public origins:</span></span>
  
- <span data-ttu-id="1ac64-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="1ac64-190">\*/masterpage</span></span>
    
- <span data-ttu-id="1ac64-191">\*bibliothèque /style</span><span class="sxs-lookup"><span data-stu-id="1ac64-191">\*/style library</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="1ac64-192">Installer et configurer le CDN 365 Office à l’aide de SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="1ac64-192">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="1ac64-p120">Les procédures décrites dans cette rubrique nécessitent que vous permet de vous connecter à SharePoint Online SharePoint Online Management Shell. Pour plus d’informations, voir [se connecter à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p120">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="1ac64-195">Effectuez ces étapes pour installer et configurer le CDN 365 Office pour héberger vos ressources statiques dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1ac64-195">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="1ac64-196">Pour activer votre organisation d’utiliser le CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-196">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="1ac64-p121">Utilisez l’applet de commande **Set-SPOTenantCdnEnabled** pour permettre à votre organisation d’utiliser le CDN 365 Office. Vous pouvez activer votre organisation d’utiliser des origines publics, origines privés ou les deux avec du CDN. Vous pouvez également configurer le CDN 365 Office pour ignorer l’installation d’origine par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p121">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="1ac64-201">Dans Windows Powershell pour SharePoint Online :</span><span class="sxs-lookup"><span data-stu-id="1ac64-201">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="1ac64-202">Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées avec du CDN, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-202">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="1ac64-203">Pour permettre à votre organisation d’utiliser des origines publiques et privées avec du CDN mais ignorer la configuration d’origine de la valeur par défaut, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-203">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="1ac64-204">Pour permettre à votre organisation d’utiliser des origines publics avec du CDN, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-204">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="1ac64-205">Pour permettre à votre organisation d’utiliser des origines privés avec du CDN, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-205">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="1ac64-206">Pour plus d’informations sur cette applet de commande, voir [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-206">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="1ac64-207">(Facultatif) Pour modifier la liste des types de fichiers à inclure dans le CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-207">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-208"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-208"></span></span>

> [!TIP]
> <span data-ttu-id="1ac64-p122">Lorsque vous définissez des types de fichiers à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez ajouter d’autres types de fichiers à la liste, utilisez l’applet de commande tout d’abord pour découvrir les types de fichiers sont déjà autorisés et les incluent dans la liste, ainsi que les nouvelles.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p122">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="1ac64-p123">Utilisez l’applet de commande **Set-SPOTenantCdnPolicy** pour définir les types de fichiers statiques qui peuvent être hébergées par origines publiques et privées dans du CDN. Par défaut, les types de biens courants sont autorisées, pour .js, .gif, .jpg et .css exemple.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p123">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="1ac64-213">Dans Windows PowerShell pour SharePoint Online :</span><span class="sxs-lookup"><span data-stu-id="1ac64-213">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="1ac64-214">Pour voir quels types de fichiers actuellement autorisés par le CDN, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="1ac64-214">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="1ac64-215">Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-215">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="1ac64-216">(Facultatif) Pour modifier la liste des classifications de site que vous souhaitez exclure à partir du CDN de 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-216">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-217"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-217"></span></span>

> [!TIP]
> <span data-ttu-id="1ac64-p124">Lorsque vous excluez des classifications de sites à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez exclure des classifications de sites supplémentaires, utilisez la cmdlet tout d’abord, à savoir quelles classifications sont déjà exclues et puis ajoutez-les ainsi que les nouvelles.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p124">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="1ac64-p125">Utilisez l’applet de commande **Set-SPOTenantCdnPolicy** pour exclure des classifications de sites que vous ne souhaitez pas rendre disponible sur le CDN. Par défaut, aucune classification de site n’est exclues.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p125">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="1ac64-222">Dans Windows PowerShell pour SharePoint Online :</span><span class="sxs-lookup"><span data-stu-id="1ac64-222">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="1ac64-223">Pour voir quelles classifications de site sont actuellement restreintes, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="1ac64-223">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="1ac64-224">Pour plus d’informations sur ces applets de commande, voir [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) et [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-224">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="1ac64-225">Pour ajouter une origine pour vos ressources</span><span class="sxs-lookup"><span data-stu-id="1ac64-225">To add an origin for your assets</span></span>
<span data-ttu-id="1ac64-226"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-226"></span></span>

<span data-ttu-id="1ac64-p126">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL qui pointe vers une bibliothèque SharePoint ou un dossier qui contient les ressources que vous souhaitez être hébergée par le CDN.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p126">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="1ac64-230">Si vous identifiez une origine publique dans votre CDN, vous devez placer jamais les ressources qui sont considérés comme critiques pour votre organisation dans l’origine public ou une bibliothèque SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1ac64-230">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="1ac64-p127">Où chemin d’accès est le chemin d’accès au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Par exemple, pour inclure tous les actifs dans le dossier masterpages pour tous vos sites en tant qu’une origine public au sein du CDN, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-p127">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="1ac64-234">Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-234">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="1ac64-p128">Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p128">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="1ac64-237">Exemple : Configuration d’une origine publique pour vos pages maîtres et de votre bibliothèque de style pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1ac64-237">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="1ac64-238"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-238"></span></span>

<span data-ttu-id="1ac64-p129">En règle générale, ces origines sont configurés pour vous par défaut lorsque vous activez origines publics pour le CDN 365 Office. Toutefois, si vous souhaitez les activer manuellement, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p129">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="1ac64-241">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’une origine public au sein du CDN 365 Office.</span><span class="sxs-lookup"><span data-stu-id="1ac64-241">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="1ac64-242">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir les pages maîtres comme une origine public au sein du CDN 365 Office.</span><span class="sxs-lookup"><span data-stu-id="1ac64-242">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="1ac64-243">Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-243">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="1ac64-p130">Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p130">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="1ac64-246">Exemple : Configuration d’une origine privée pour vos éléments de site, pages de site et des images de publications de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1ac64-246">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="1ac64-247"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-247"></span></span>

- <span data-ttu-id="1ac64-248">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier de ressources de site comme une origine privée au sein du CDN 365 Office.</span><span class="sxs-lookup"><span data-stu-id="1ac64-248">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="1ac64-249">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier de pages de site comme une origine privée au sein du CDN 365 Office.</span><span class="sxs-lookup"><span data-stu-id="1ac64-249">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="1ac64-250">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier images de publication comme une origine privée au sein du CDN 365 Office.</span><span class="sxs-lookup"><span data-stu-id="1ac64-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="1ac64-251">Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-251">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="1ac64-p131">Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="1ac64-254">Exemple : Configuration d’une origine privée pour une collection de sites pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1ac64-254">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="1ac64-255"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-255"></span></span>

<span data-ttu-id="1ac64-p132">Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une collection de sites comme une origine privée au sein du CDN 365 Office. Par exemple,</span><span class="sxs-lookup"><span data-stu-id="1ac64-p132">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="1ac64-258">Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-258">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="1ac64-p133">Une fois que vous avez exécuté la commande, le système synchronise la configuration sur le centre de données. Il prend 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p133">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="1ac64-261">Gérer le Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="1ac64-261">Manage the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-262"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-262"></span></span>

<span data-ttu-id="1ac64-263">Une fois que vous avez configuré le CDN, vous pouvez modifier votre configuration que vous mettez à jour le contenu ou selon vos besoins, comme décrit dans cette section.</span><span class="sxs-lookup"><span data-stu-id="1ac64-263">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="1ac64-264">Pour ajouter, mettre à jour ou supprimer des ressources à partir du CDN de 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-264">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-265"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-265"></span></span>

<span data-ttu-id="1ac64-p134">Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des ressources existantes chaque fois que vous le souhaitez. Simplement, apportez vos modifications pour les biens dans le dossier ou la bibliothèque SharePoint que vous avez identifié comme origine. Si vous ajoutez une nouvelle immobilisation, il est immédiatement disponible par le biais du CDN. Toutefois, si vous mettez à jour l’immobilisation, il prendra jusqu'à 15 minutes pour la nouvelle copie de propagation et deviennent disponibles dans le CDN.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p134">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="1ac64-p135">Si vous avez besoin récupérer l’emplacement de l’origine, vous pouvez utiliser l’applet de commande **Get-SPOTenantCdnOrigins** . Pour plus d’informations sur l’utilisation de cette applet de commande, voir [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p135">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="1ac64-272">Pour supprimer une origine à partir du CDN de 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-272">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-273"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-273"></span></span>

<span data-ttu-id="1ac64-p136">Si vous le souhaitez, vous pouvez supprimer l’accès à un dossier ou une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez l’applet de commande **Remove-SPOTenantCdnOrigin** . Pour plus d’informations sur l’utilisation de cette applet de commande, voir [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p136">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="1ac64-277">Pour modifier une origine dans le CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-277">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-278"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-278"></span></span>

<span data-ttu-id="1ac64-p137">Vous ne pouvez pas modifier une origine que vous avez créé. Au lieu de cela, supprimez l’origine, puis ajoutez un nouveau. Pour plus d’informations, consultez [pour supprimer une origine à partir du CDN de 365 Office](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) et [Ajouter une origine pour vos ressources](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="1ac64-p137">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="1ac64-282">Pour désactiver le CDN 365 Office</span><span class="sxs-lookup"><span data-stu-id="1ac64-282">To disable the Office 365 CDN</span></span>
<span data-ttu-id="1ac64-283"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-283"></span></span>

<span data-ttu-id="1ac64-p138">Utilisez l’applet de commande **Set-SPOTenantCdnEnabled** pour désactiver le CDN pour votre organisation. Si vous avez deux origines publiques et privées activés pour le CDN, vous devez exécuter l’applet de commande à deux reprises comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p138">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="1ac64-286">Pour désactiver l’utilisation d’origines publics dans du CDN, dans Windows Powershell pour SharePoint Online, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-286">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="1ac64-287">Pour désactiver l’utilisation des origines privées dans du CDN, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac64-287">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="1ac64-288">Pour plus d’informations sur cette applet de commande, voir [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="1ac64-288">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="1ac64-289">Résolution des problèmes de votre configuration Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="1ac64-289">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="1ac64-290"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="1ac64-290"></span></span>

<span data-ttu-id="1ac64-p139">Le point de terminaison pas immédiatement sera disponible pour une utilisation, comme le temps requis pour l’inscription d’être propagées par le biais du CDN. Configuration prend 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="1ac64-p139">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

