---
title: "Sécuriser les sites d’équipe SharePoint Online pour les ressources sensibles et hautement confidentielles"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Résumé : Découvrez comment Contoso a mis en œuvre des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, afin de permettre une collaboration simple, mais sécurisée, entre ses centres de recherche et ses cadres."
ms.openlocfilehash: 1574babb54bfcb3fd74fb8ce4f31c364bb96b14a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="7392c-103">Sécuriser les sites d’équipe SharePoint Online pour les ressources sensibles et hautement confidentielles</span><span class="sxs-lookup"><span data-stu-id="7392c-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="7392c-104">**Résumé :** Découvrez comment Contoso a mis en œuvre des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, afin de permettre une collaboration simple, mais sécurisée, entre ses centres de recherche et ses cadres.</span><span class="sxs-lookup"><span data-stu-id="7392c-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers..</span></span>
  
<span data-ttu-id="7392c-p101">Les cadres supérieurs de Contoso souhaitent utiliser Office 365 et stocker leurs fichiers dans un emplacement unique à des fins de collaboration, quel que soit l'endroit où ils sont susceptibles de se trouver. De même, les services de recherche de Contoso, qui comptent des départements à Paris, Moscou, New York, Beijing (Pékin) et Bengaluru (Bangalore), aimeraient faire passer leurs ressources numériques en local sur le cloud afin d'en faciliter l'accès et de permettre une collaboration plus ouverte entre les équipes.</span><span class="sxs-lookup"><span data-stu-id="7392c-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="7392c-p102">Toutefois, dans les deux cas, l'accès à ces ressources doit être limité au sous-ensemble de personnes qui sont autorisées à les visualiser ou à les modifier, avec des autorisations permanentes pour le site géré par le service informatique. En outre, même si certaines ressources sont distribuées intentionnellement ou non, elles doivent être chiffrées et dotées d'autorisations pour empêcher les personnes qui ne disposent pas d'un accès de visualiser ou de modifier leur contenu.</span><span class="sxs-lookup"><span data-stu-id="7392c-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="7392c-109">Les administrateurs de la sécurité et de SharePoint au sein du service informatique de Contoso ont décidé d'utiliser des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, comme illustré dans la figure 1.</span><span class="sxs-lookup"><span data-stu-id="7392c-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="7392c-110">**Figure 1 : Comparaison des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles**</span><span class="sxs-lookup"><span data-stu-id="7392c-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Sites d’équipe SharePoint Online hautement confidentiels et avec protection des données sensibles](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="7392c-112">Contoso a créé des sites d’équipe SharePoint Online sécurisés pour ses cadres et ses équipes de recherche de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="7392c-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="7392c-113">Création d'un site d'équipe SharePoint Online sensible pour les **cadres**</span><span class="sxs-lookup"><span data-stu-id="7392c-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="7392c-114">Le nouveau site d’équipe utilise des groupes Azure Active Directory (AD) existants pour les cadres en tant que membres avec le niveau d’autorisation Modifier SharePoint et un petit ensemble de comptes d’administrateur SharePoint en tant que propriétaires avec le niveau d’autorisation Contrôle total.</span><span class="sxs-lookup"><span data-stu-id="7392c-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="7392c-115">Migration des fichiers des cadres</span><span class="sxs-lookup"><span data-stu-id="7392c-115">Migrate executives files</span></span>
    
    <span data-ttu-id="7392c-116">Les fichiers et dossiers des cadres existants en local sont déplacés vers le nouveau site d’équipe SharePoint Online pour les cadres.</span><span class="sxs-lookup"><span data-stu-id="7392c-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="7392c-117">Création d'un site d'équipe SharePoint Online hautement confidentiel pour la **recherche**</span><span class="sxs-lookup"><span data-stu-id="7392c-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="7392c-p103">Le nouveau site d'équipe utilise des groupes d'équipe de recherche Azure AD existants en tant que membres avec le niveau d'autorisation Modifier et un petit ensemble de comptes d'administrateur SharePoint en tant que propriétaires avec le niveau d'autorisation Contrôle total. Une étiquette AIP est affectée aux fichiers de recherche, ce qui permet de s'assurer qu'ils sont chiffrés et que seuls les membres d'un groupe de recherche peuvent les ouvrir.</span><span class="sxs-lookup"><span data-stu-id="7392c-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="7392c-120">Migration des fichiers de recherche</span><span class="sxs-lookup"><span data-stu-id="7392c-120">Migrate research files</span></span>
    
    <span data-ttu-id="7392c-121">Les fichiers et dossiers de recherche existants en local sont déplacés vers le nouveau site d’équipe SharePoint Online pour la recherche.</span><span class="sxs-lookup"><span data-stu-id="7392c-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="7392c-p104">Le résultat consiste en deux sites de collaboration dont l'accès est étroitement contrôlé par les administrateurs de la sécurité et de SharePoint. Pour les fichiers dotés de l'étiquette AIP Hautement confidentiel, même s'ils sont distribués en dehors du site d'équipe pour la recherche, ils sont chiffrés et ne peuvent être ouverts que par un membre d'une équipe de recherche.</span><span class="sxs-lookup"><span data-stu-id="7392c-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="7392c-124">Pour plus d'informations, consultez l'article [Sécuriser des sites et des fichiers SharePoint Online]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)).</span><span class="sxs-lookup"><span data-stu-id="7392c-124">For more information, see [Secure SharePoint Online sites and files]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)).</span></span>
  
 <span data-ttu-id="7392c-125">Pour effectuer cette configuration à des fins de démonstration, de preuve de concept ou de développement/test, consultez l'article [Sécuriser des sites SharePoint Online dans un environnement de développement et de test]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)).</span><span class="sxs-lookup"><span data-stu-id="7392c-125">To set this up for demonstration, proof-of-concept, or dev/test, see[Secure SharePoint Online sites in a dev/test environment]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7392c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7392c-126">See Also</span></span>

[<span data-ttu-id="7392c-127">Scénarios d'entreprise pour la société Contoso</span><span class="sxs-lookup"><span data-stu-id="7392c-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="7392c-128">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="7392c-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="7392c-129">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="7392c-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="7392c-130">[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))</span><span class="sxs-lookup"><span data-stu-id="7392c-130">[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))</span></span>
  
<span data-ttu-id="7392c-131">[Feuille de route de Microsoft Enterprise Cloud : Ressources pour les décideurs informatiques]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="7392c-131">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>




