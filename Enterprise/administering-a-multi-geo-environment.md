---
title: Administration d’un environnement multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment administrer des services SharePoint et OneDrive dans un environnement multigéographique.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="4f94c-103">Administration d’un environnement multigéographique</span><span class="sxs-lookup"><span data-stu-id="4f94c-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="4f94c-104">Découvrez le fonctionnement des services OneDrive et SharePoint dans un environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="4f94c-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="4f94c-105">Expérience de l’administrateur OneDrive</span><span class="sxs-lookup"><span data-stu-id="4f94c-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="4f94c-p101">Dans le [Centre d’administration OneDrive](https://admin.onedrive.com), l’onglet **Emplacements géographiques** dans le volet de navigation gauche propose une carte où vous pouvez afficher et gérer vos emplacements géographiques. Utilisez cette page pour ajouter ou supprimer des emplacements géographiques pour votre client.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="4f94c-108">Taxonomie</span><span class="sxs-lookup"><span data-stu-id="4f94c-108">Taxonomy</span></span>

<span data-ttu-id="4f94c-p102">Nous prenons en charge une [taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unifiée pour gérer les métadonnées dans l’entreprise à différents emplacements géographiques ; les données de référence étant hébergées à l’emplacement central de votre entreprise. Nous vous recommandons de gérer votre taxonomie globale à partir de l’emplacement central et d’ajouter uniquement des termes spécifiques à la taxonomie de l’emplacement géographique satellite. Les termes de la taxonomie globale sont synchronisés sur les emplacements géographiques satellites.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="4f94c-112">Partage</span><span class="sxs-lookup"><span data-stu-id="4f94c-112">Sharing</span></span>

<span data-ttu-id="4f94c-p103">Les administrateurs peuvent définir et gérer les stratégies de partage pour chaque emplacement. Les sites OneDrive de chaque emplacement géographique respectent uniquement les paramètres de partage associés à un emplacement géographique précis. (Par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre emplacement central, mais pas pour votre emplacement satellite, et inversement.) Notez que les paramètres de partage ne vous permettent pas de configurer les limites de partage entre emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="4f94c-p104">Pour OneDrive Multi-Géo, vos paramètres de partage doivent être gérés à chaque emplacement géographique car ils ne sont pas synchronisés sur le client. Pour gérer les paramètres de partage, rendez-vous sur le [Centre d’administration OneDrive](https://admin.onedrive.com/?v=SharingSettings). Par défaut, le partage externe est activé pour Tout le monde, dans chaque emplacement satellite.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="4f94c-119">Application de profil utilisateur</span><span class="sxs-lookup"><span data-stu-id="4f94c-119">User Profile Application</span></span>

<span data-ttu-id="4f94c-p105">Il existe une [application de profil utilisateur](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) dans chaque emplacement géographique. Les informations de chaque profil utilisateur sont hébergées dans leur emplacement géographique et accessibles par l’administrateur de cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="4f94c-p106">Si vous avez des propriétés de profil personnalisées, nous vous recommandons d’utiliser le même schéma de profil dans toutes les zones géographiques et de remplir vos propriétés de profil personnalisées dans tous les emplacements géographiques ou dans les emplacements requis. Pour savoir comment remplir les données de profil utilisateur par programme, consultez l’[API de mise à jour en bloc de profil utilisateur](https://docs.microsoft.com/fr-FR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span><span class="sxs-lookup"><span data-stu-id="4f94c-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/fr-FR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="4f94c-124">BCS, service Banque d’informations sécurisé, applications</span><span class="sxs-lookup"><span data-stu-id="4f94c-124">BCS: Secure Store Service</span></span>

<span data-ttu-id="4f94c-125">BCS, le service Banque d’informations sécurisé et les applications ont des instances géographiques distinctes. Ainsi, l’administrateur SharePoint Online doit gérer et configurer ces services à partir de chaque instance géographique où ils doivent apparaître.</span><span class="sxs-lookup"><span data-stu-id="4f94c-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="4f94c-126">Centre de sécurité et conformité</span><span class="sxs-lookup"><span data-stu-id="4f94c-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="4f94c-127">Il existe un centre de conformité central pour le client multigéographique : [Centre de sécurité et conformité Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="4f94c-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="4f94c-128">Stratégies de protection contre la perte de données (DLP) et de protection des informations (IP)</span><span class="sxs-lookup"><span data-stu-id="4f94c-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="4f94c-p107">Vous pouvez définir vos stratégies DLP et IP pour OneDrive Entreprise dans le Centre de sécurité et conformité, en configurant l’étendue de vos stratégies selon vos besoins, pour tout le client ou pour certains utilisateurs. Par exemple, pour sélectionner une stratégie à appliquer à un utilisateur OneDrive dans un emplacement satellite, sélectionnez la stratégie et entrez l’URL OneDrive de l’utilisateur. Pour en savoir plus sur la création des stratégies DLP, consultez l’article [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="4f94c-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="4f94c-132">Les stratégies DLP sont synchronisées automatiquement en fonction de leurs conditions d’application à chaque emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="4f94c-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="4f94c-133">Dans l’interface utilisateur, il est impossible d’appliquer des stratégies de protection contre la perte de données et de protection des informations à tous les utilisateurs d’un emplacement géographique. À la place, sélectionnez les comptes OneDrive concernés par la stratégie ou appliquez la stratégie globalement à tous les comptes OneDrive.</span><span class="sxs-lookup"><span data-stu-id="4f94c-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="4f94c-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="4f94c-134">eDiscovery</span></span> 

<span data-ttu-id="4f94c-p108">Par défaut, un gestionnaire ou un administrateur eDiscovery d’un client multigéographique peut mettre en place un processus eDiscovery uniquement dans l’emplacement central de ce client. Pour pouvoir mettre en place un processus eDiscovery dans les emplacements satellites, il existe un nouveau paramètre Filtre de sécurité de conformité appelé « Région » dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="4f94c-137">L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre « Région » dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite.</span><span class="sxs-lookup"><span data-stu-id="4f94c-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="4f94c-p109">Quand un gestionnaire ou un administrateur eDiscovery est défini pour un emplacement particulier, ce gestionnaire ou cet administrateur peut uniquement effectuer des actions de recherche eDiscovery dans les sites SharePoint et OneDrive situés dans cet emplacement géographique. Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de la région spécifiée, aucun résultat n’est renvoyé. Par ailleurs, quand le gestionnaire ou l’administrateur eDiscovery d’une région déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Ainsi, les entreprises respectent les règles de conformité en interdisant l’exportation de contenu au-delà de frontières contrôlées.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="4f94c-142">Si un gestionnaire eDiscovery doit effectuer des recherches dans plusieurs régions SharePoint, un autre compte d’utilisateur doit être créé pour ce gestionnaire, lequel doit indiquer une autre région où sont situés les sites OneDrive ou SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4f94c-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="4f94c-143"><strong>Emplacements multigéographiques pris en charge</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="4f94c-144"><strong>Emplacement Blob Azure où les données eDiscovery pour SharePoint exportées seront stockées</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="4f94c-145"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-145"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-146">Centres de données situés aux États-Unis</span><span class="sxs-lookup"><span data-stu-id="4f94c-146">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4f94c-147"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-147"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-148">Centres de données situés en Europe</span><span class="sxs-lookup"><span data-stu-id="4f94c-148">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4f94c-149"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-149"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-150">Centres de données situés en Asie de l’Est ou du Sud-Est</span><span class="sxs-lookup"><span data-stu-id="4f94c-150">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4f94c-151"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-151"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-152">Centres de données situés aux États-Unis</span><span class="sxs-lookup"><span data-stu-id="4f94c-152">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4f94c-153"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-153"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-154">Centres de données situés en Asie de l’Est ou du Sud-Est</span><span class="sxs-lookup"><span data-stu-id="4f94c-154">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4f94c-155"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-155"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-156">Emplacement par défaut des données du client</span><span class="sxs-lookup"><span data-stu-id="4f94c-156">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4f94c-157"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-157"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-158">Centres de données situés en Europe</span><span class="sxs-lookup"><span data-stu-id="4f94c-158">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4f94c-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="4f94c-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="4f94c-160">Centres de données situés en Asie de l’Est ou du Sud-Est</span><span class="sxs-lookup"><span data-stu-id="4f94c-160">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="4f94c-161">Pour définir le filtre de sécurité de conformité pour une région :</span><span class="sxs-lookup"><span data-stu-id="4f94c-161">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="4f94c-162">Ouvrez Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f94c-162">Open Windows PowerShell.</span></span>

2.  <span data-ttu-id="4f94c-163">Entrez </span><span class="sxs-lookup"><span data-stu-id="4f94c-163">Enter</span></span>  
    <span data-ttu-id="4f94c-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="4f94c-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="4f94c-165">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="4f94c-165">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="4f94c-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="4f94c-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="4f94c-167">Par exemple : **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="4f94c-167">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="4f94c-168">Consultez l’article [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) pour en savoir plus sur la syntaxe et les paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="4f94c-168">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="4f94c-169">Recherche de journal d’audit</span><span class="sxs-lookup"><span data-stu-id="4f94c-169">Audit log search</span></span>

<span data-ttu-id="4f94c-p110">Un [journal d’audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unifié pour tous vos emplacements géographiques est disponible sur la page de recherche du journal d’audit Office 365. Vous pouvez voir toutes les entrées du journal d’audit de plusieurs emplacements géographiques. Par exemple, les activités des utilisateurs dans les régions NAM et EUR apparaissent dans un seul affichage et vous pouvez appliquer les filtres existants pour afficher les activités de certains utilisateurs uniquement.</span><span class="sxs-lookup"><span data-stu-id="4f94c-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
