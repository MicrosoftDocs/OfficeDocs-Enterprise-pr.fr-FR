---
title: Administration d’un environnement multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur l’administration des services SharePoint et OneDrive dans un environnement multi-geo.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="349d2-103">Administration d’un environnement multi-geo</span><span class="sxs-lookup"><span data-stu-id="349d2-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="349d2-104">Voici comment les services OneDrive et SharePoint fonctionnent dans un environnement multi-geo.</span><span class="sxs-lookup"><span data-stu-id="349d2-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="349d2-105">Expérience de l’administrateur de OneDrive</span><span class="sxs-lookup"><span data-stu-id="349d2-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="349d2-p101">Le [Centre admin de OneDrive](https://admin.onedrive.com) a un onglet **emplacements de la zone géographique** dans la navigation gauche quelles fonctionnalités un géo-emplacements mappent dans lequel vous pouvez afficher et gérer les emplacements de votre zone géographique. Utilisez cette page pour ajouter ou supprimer des emplacements geo pour vos clients.</span><span class="sxs-lookup"><span data-stu-id="349d2-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="349d2-108">Taxonomie</span><span class="sxs-lookup"><span data-stu-id="349d2-108">Taxonomy</span></span>

<span data-ttu-id="349d2-p102">Nous prend en charge une [taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) de unifiée de métadonnées d’entreprise géré dans tous les magasins de géo, avec le maître hébergé dans l’emplacement central pour votre société. Nous vous conseillons gérez votre taxonomie globale à partir de l’emplacement central et ajoutez uniquement les termes spécifiques à l’emplacement à la taxonomie de l’emplacement géographique satellite. Termes de taxonomie globale seront synchronisées dans les emplacements de geo satellite.</span><span class="sxs-lookup"><span data-stu-id="349d2-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="349d2-112">Partage</span><span class="sxs-lookup"><span data-stu-id="349d2-112">Sharing</span></span>

<span data-ttu-id="349d2-p103">Les administrateurs peuvent définir et gérer les stratégies de partage pour chacun de leurs magasins. Les sites de OneDrive dans chaque emplacement géographique honorera seulement les correspondant geo partage des paramètres spécifiques. Par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre site central, mais pas pour vos satellites emplacement et inversement. Pour OneDrive Multi-Geo, vous devez gérer vos paramètres de partage à chaque emplacement géographique comme elles ne sont pas synchronisées sur les clients.</span><span class="sxs-lookup"><span data-stu-id="349d2-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="349d2-p104">Pour gérer le partage visite la page du [Centre d’administration OneDrive paramètres de partage](https://admin.onedrive.com/?v=SharingSettings) . Par défaut le partage externe est activé avec n’importe qui dans chaque emplacement de satellite.</span><span class="sxs-lookup"><span data-stu-id="349d2-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="349d2-119">Application de profil utilisateur</span><span class="sxs-lookup"><span data-stu-id="349d2-119">User Profile Application</span></span>

<span data-ttu-id="349d2-p105">Il existe une [application de profil utilisateur](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) dans chaque emplacement géographique. Les informations de profil de chaque utilisateur sont hébergées dans leur emplacement géographique et est disponible à l’administrateur de cet emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="349d2-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="349d2-122">Si vous avez des propriétés de profil personnalisé, nous vous recommandons d’utiliser le même schéma de profil dans le monde entier et de remplir les propriétés de votre profil personnalisé dans tous les emplacements de la zone géographique ou lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="349d2-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="349d2-123">Applications BCS, banque d’informations sécurisé,</span><span class="sxs-lookup"><span data-stu-id="349d2-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="349d2-124">BCS, banque d’informations sécurisée et applications possèdent des instances de geo distinct, donc l’administrateur SharePoint Online doit gérer et configurer ces services à partir de chaque instance géographique où ils le souhaitent être présents.</span><span class="sxs-lookup"><span data-stu-id="349d2-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="349d2-125">Centre Admin de mise en conformité et de sécurité</span><span class="sxs-lookup"><span data-stu-id="349d2-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="349d2-126">Il existe un centre de conformité centralisé pour le locataire Multi-Geo : [Office 365 sécurité & centre de conformité](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="349d2-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="349d2-127">Information Protection (IP) Prevention (DLP) stratégie DLP</span><span class="sxs-lookup"><span data-stu-id="349d2-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="349d2-p106">Vous pouvez définir votre DLP IP stratégies de OneDrive pour l’entreprise dans le centre de sécurité et de conformité, portée des stratégies en fonction des besoins au locataire entier ou pour les utilisateurs concernés. Par exemple : Si vous souhaitez sélectionner une stratégie pour un utilisateur de OneDrive dans un emplacement de satellite, sélectionnez cette option pour appliquer la stratégie à un OneDrive spécifique et entrez les url de l’OneDrive. Pour obtenir des instructions générales lors de la création de stratégies DLP, consultez [vue d’ensemble des stratégies de prévention de perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .</span><span class="sxs-lookup"><span data-stu-id="349d2-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="349d2-131">Les stratégies DLP sont synchronisés automatiquement en fonction de leur applicabilité dans chaque emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="349d2-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="349d2-132">Mise en œuvre de stratégies de prevention de perte de données et de Protection des informations à tous les utilisateurs dans un emplacement géographique n’est pas une option disponible dans l’interface utilisateur, à la place vous devez sélectionner les comptes de OneDrive applicables pour la stratégie ou appliquer globalement à tous les comptes de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="349d2-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="349d2-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="349d2-133">eDiscovery</span></span> 

<span data-ttu-id="349d2-p107">Par défaut, une e-Discovery Manager ou l’administrateur d’un client multi-geo sera en mesure de conduire eDiscovery uniquement dans l’emplacement central de ce client. Pour prendre en charge la possibilité de mener l’e-Discovery pour les emplacements de satellite, un nouveau paramètre de filtre de sécurité de la conformité, appelé « Region » est disponible via PowerShell.</span><span class="sxs-lookup"><span data-stu-id="349d2-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="349d2-136">L’administrateur Office 365 doit affecter des autorisations de gestionnaire d’e-Discovery pour permettre à d’autres utilisateurs à effectuer des e-Discovery et de lui attribuer un paramètre « Région » dans leur filtre de sécurité de la conformité applicables pour spécifier la région de conduite d’e-Discovery comme satellite emplacement, sinon qu'aucun eDiscovery ne se fera pour l’emplacement de satellite.</span><span class="sxs-lookup"><span data-stu-id="349d2-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="349d2-p108">Lorsque le rôle de responsable ou l’administrateur d’e-Discovery est défini pour un emplacement particulier-geo, l’e-Discovery Manager ou administrateur uniquement pourront effectuer des actions de recherche d’e-Discovery contre les sites SharePoint et les sites de OneDrive que qui se trouve à cet emplacement géo. Si un administrateur ou un gestionnaire eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de la région déterminée, aucun résultats ne seront renvoyés. En outre, lorsque l’e-Discovery responsable ou administrateur pour une région déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Cela aide les entreprises à respecter les réglementations en ne permettant ne pas de contenu à exporter au-delà des frontières contrôlés.</span><span class="sxs-lookup"><span data-stu-id="349d2-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="349d2-141">S’il est nécessaire pour une e-Discovery Manager pour effectuer une recherche dans plusieurs régions de SharePoint, un autre compte d’utilisateur devez être créé pour l’e-Discovery Manager qui spécifie la zone secondaire où se trouvent les sites OneDrive ou SharePoint.</span><span class="sxs-lookup"><span data-stu-id="349d2-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="349d2-142"><strong>Prise en charge de multi-Geo Geo emplacements</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="349d2-143"><strong>e-Discovery pour les données exportées de SharePoint sera dans cet emplacement de données Blob d’Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="349d2-144"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-145">Les centres de données américains</span><span class="sxs-lookup"><span data-stu-id="349d2-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="349d2-146"><strong>EUROS</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-147">Les centres de données en Europe</span><span class="sxs-lookup"><span data-stu-id="349d2-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="349d2-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-149">Sud-est ou des centres de données d’Asie orientale</span><span class="sxs-lookup"><span data-stu-id="349d2-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="349d2-150"><strong>POUVEZ</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-151">Les centres de données américains</span><span class="sxs-lookup"><span data-stu-id="349d2-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="349d2-152"><strong>AUSTRALIE</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-153">Sud-est ou des centres de données d’Asie orientale</span><span class="sxs-lookup"><span data-stu-id="349d2-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="349d2-154"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-155">Emplacement de données par défaut du locataire</span><span class="sxs-lookup"><span data-stu-id="349d2-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="349d2-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-157">Les centres de données en Europe</span><span class="sxs-lookup"><span data-stu-id="349d2-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="349d2-158"><strong>JPN</strong></span><span class="sxs-lookup"><span data-stu-id="349d2-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="349d2-159">Sud-est ou des centres de données d’Asie orientale</span><span class="sxs-lookup"><span data-stu-id="349d2-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="349d2-160">Pour définir le filtre de sécurité de la conformité d’une région :</span><span class="sxs-lookup"><span data-stu-id="349d2-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="349d2-161">Ouvrir Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="349d2-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="349d2-162">Entrez </span><span class="sxs-lookup"><span data-stu-id="349d2-162">Enter</span></span>  
    <span data-ttu-id="349d2-163">$s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred des informations d’identification-authentification base - AllowRedirection - SessionOption (nouveau-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="349d2-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="349d2-164">$un = Import-PSSession $s - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="349d2-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="349d2-165">**Nouvelle-ComplianceSecurityFilter** **-Action** Tous les EnterTheNameYouWantToAssign de **NomFiltre -** **-région** EnterTheRegionParameter **-utilisateurs** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="349d2-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="349d2-166">Par exemple : **ComplianceSecurityFilter-nouvelle-Action** tous les **NomFiltre -** NAMEDISCOVERYMANAGERS **-région** NAM **-utilisateurs** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="349d2-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="349d2-167">Consultez l’article de la [Nouvelle-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) pour la syntaxe et les paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="349d2-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="349d2-168">Recherche de journal d’audit</span><span class="sxs-lookup"><span data-stu-id="349d2-168">Audit log search</span></span>

<span data-ttu-id="349d2-p109">Un unifiée [journal d’Audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) pour tous les emplacements de votre zone géographique est disponible à partir de la page de recherche de journal d’audit Office 365. Vous pouvez voir toutes les entrées de journal d’audit de sur des zones géographiques, par exemple, euros & nom géographique activités de l’utilisateur seront affiche dans une vue hiérarchique et vous pouvez ensuite appliquer des filtres existants pour voir les activités spécifiques de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="349d2-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
