---
title: "Application d’étiquettes à des données personnelles dans Office 365"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "Découvrez comment utiliser des étiquettes Office dans le cadre de votre plan de protection RGPD."
ms.openlocfilehash: be09afa8efa19d48d6bed2ad818adbcaf2aafcda
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="a11ed-103">Application d’étiquettes à des données personnelles dans Office 365</span><span class="sxs-lookup"><span data-stu-id="a11ed-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="a11ed-p101">Consultez cette rubrique si vous utilisez des étiquettes Office dans le cadre de votre plan de protection RGPD. Les étiquettes peuvent être actuellement créées dans le Centre de sécurité et de conformité Office 365 et dans Azure Information Protection. À l’avenir, ces technologies convergeront vers une expérience unifiée d’étiquetage et de classification, vous donnant encore plus de possibilités.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="a11ed-p102">Si vous utilisez des étiquettes pour la protection des données personnelles dans Office 365, Microsoft vous recommande de commencer par les étiquettes Office. Vous pouvez utiliser la gouvernance des données avancée pour appliquer automatiquement des étiquettes en fonction de types d’informations sensibles ou d’autres critères. Vous pouvez utiliser des étiquettes Office avec la protection contre la perte de données pour appliquer la protection. Vous pouvez également avoir recours à des étiquettes avec eDiscovery et la recherche de contenu. Vous serez bientôt en mesure d’employer des étiquettes et des types d’informations sensibles avec Cloud App Security pour surveiller les données personnelles qui se trouvent dans d’autres applications SaaS.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="a11ed-p103">Les étiquettes Azure Information Protection sont actuellement recommandées pour l’application d’étiquettes à des fichiers en local ainsi que dans d’autres fournisseurs et services cloud. Elles sont également recommandées pour les fichiers dans Office 365 nécessitant le chiffrement Azure Rights Management (Azure RMS) pour la protection des données, tels que les fichiers contenant des secrets commerciaux.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="a11ed-p104">À ce stade, il n’est pas recommandé d’avoir recours à Azure Information Protection afin d’appliquer le chiffrement Azure RMS à des fichiers dans Office 365 contenant des données soumises au RGPD. Les services Office 365 ne peuvent pas être actuellement lus dans des fichiers chiffrés via RMS. Par conséquent, le service ne peut pas trouver de données sensibles dans ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="a11ed-p105">Les étiquettes Azure Information Protection peuvent être appliquées aux e-mails dans Exchange Online. Ces étiquettes sont compatibles avec la protection contre la perte de données Office 365. Grâce à la classification unifiée et au moteur de création d’étiquettes bientôt disponibles, vous serez en mesure d’utiliser les mêmes étiquettes pour les e-mails et les fichiers, y compris l’étiquetage et la protection automatiques des e-mails en transit.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Étiquettes Office 365 et étiquettes Azure Information Protection](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="a11ed-120">Dans cette illustration :</span><span class="sxs-lookup"><span data-stu-id="a11ed-120">In the illustration:</span></span>

-   <span data-ttu-id="a11ed-121">Utilisez les étiquettes Office 365 pour les données personnelles ou pour les fichiers contenant des données hautement réglementées et des secrets commerciaux dans SharePoint Online et OneDrive Entreprise.</span><span class="sxs-lookup"><span data-stu-id="a11ed-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="a11ed-122">Utilisez les étiquettes Azure Information Protection (AIP) pour les fichiers contenant des données hautement réglementées et des secrets commerciaux, les e-mails Exchange Online, les fichiers dans d’autres services SaaS, les fichiers dans des centres de données en local et les fichiers dans d’autres fournisseurs cloud.</span><span class="sxs-lookup"><span data-stu-id="a11ed-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="a11ed-123">Bientôt disponible : les deux types d’étiquettes vont converger vers une expérience unifiée de classification et d’étiquetage.</span><span class="sxs-lookup"><span data-stu-id="a11ed-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="a11ed-124">Utilisation des étiquettes Office et des types d’informations sensibles au sein de Microsoft 365 pour la protection des informations</span><span class="sxs-lookup"><span data-stu-id="a11ed-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="a11ed-125">L’image suivante montre comment les étiquettes Office et les types d’informations sensibles peuvent être utilisés dans les stratégies d’étiquetage, les stratégies de protection contre la perte de données et les stratégies Cloud App Security.</span><span class="sxs-lookup"><span data-stu-id="a11ed-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Étiquettes Office et types d’informations sensibles](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="a11ed-127">Concernant l’accessibilité, le tableau suivant fournit les mêmes exemples dans l’illustration.</span><span class="sxs-lookup"><span data-stu-id="a11ed-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a11ed-128"><strong>Éléments de classification</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="a11ed-129"><strong>Stratégies d’étiquetage — 2 exemples</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="a11ed-130"><strong>Stratégies de protection contre la perte de données — 2 exemples</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="a11ed-131"><strong>Stratégies Cloud App Security pour toutes les applications SaaS — 1 exemple</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a11ed-p106">Étiquettes Office. Exemples : Personnel, Public, Données client, Données RH, Confidentiel, Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="a11ed-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="a11ed-p107">Appliquer automatiquement l’étiquette...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="a11ed-137">Données client</span><span class="sxs-lookup"><span data-stu-id="a11ed-137">Customer data</span></span></p>
<p><span data-ttu-id="a11ed-p108">... aux documents qui correspondent aux types d’informations sensibles...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="a11ed-144">&lt;Liste des types d’informations sensibles disponibles&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="a11ed-p109">Appliquer cette protection...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="a11ed-148">&lt;définir la protection&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="a11ed-p110">... à des documents avec cette étiquette...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="a11ed-155">Données client</span><span class="sxs-lookup"><span data-stu-id="a11ed-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="a11ed-p111">Avertir quand des fichiers avec les attributs suivants...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="a11ed-159">&lt;attribut PII prédéfini ou expression personnalisée&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="a11ed-p112">... dans des applications SaaS approuvées sont partagés en dehors de l’organisation</span><span class="sxs-lookup"><span data-stu-id="a11ed-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a11ed-p113">Types d’informations sensibles. Exemples : numéro national belge, numéro de carte de crédit, numéro de carte d’identité en Croatie, ID national en Finlande</span><span class="sxs-lookup"><span data-stu-id="a11ed-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="a11ed-p114">Publiez ces étiquettes pour que les utilisateurs puissent les appliquer manuellement...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="a11ed-169">&lt;sélectionner des étiquettes&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="a11ed-p115">... à ces emplacements...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="a11ed-176">&lt;tous les emplacements ou choisir des emplacements spécifiques&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="a11ed-p116">Appliquer cette protection...</span><span class="sxs-lookup"><span data-stu-id="a11ed-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="a11ed-180">&lt;définir la protection&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="a11ed-p117">... aux documents qui correspondent à ces types d’informations sensibles&gt;</span><span class="sxs-lookup"><span data-stu-id="a11ed-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="a11ed-185">Remarque : les attributs prochainement disponibles pour Cloud App Security incluent les types d’informations sensibles Office 365 ainsi que les étiquettes unifiées dans Office 365 et Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="a11ed-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="a11ed-186">Hiérarchisation des stratégies d’étiquette à application automatique</span><span class="sxs-lookup"><span data-stu-id="a11ed-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="a11ed-p118">Pour les données personnelles soumises au RGPD, Microsoft recommande l’application automatique des étiquettes à l’aide des types d’informations sensibles traités pour votre environnement. Il est important que les stratégies d’étiquettes à application automatique soient conçues correctement et testées pour s’assurer que le comportement attendu se produit.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="a11ed-p119">L’ordre de création des stratégies d’application automatique et leur utilisation ou non par les utilisateurs ont une incidence sur le résultat. Par conséquent, il est important de planifier avec soin le déploiement. Voici ce que vous devez savoir.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="a11ed-191">Une seule étiquette à la fois</span><span class="sxs-lookup"><span data-stu-id="a11ed-191">One participant at a time (serial)</span></span>

<span data-ttu-id="a11ed-192">Vous pouvez uniquement attribuer une seule étiquette à un document.</span><span class="sxs-lookup"><span data-stu-id="a11ed-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="a11ed-193">Priorité des anciennes stratégies d’application automatique</span><span class="sxs-lookup"><span data-stu-id="a11ed-193">Older auto-apply policies win</span></span>

<span data-ttu-id="a11ed-p120">S’il existe plusieurs règles attribuant une étiquette à application automatique et si le contenu remplit les critères de plusieurs règles, l’étiquette de la règle la plus ancienne est attribuée. C’est pourquoi il est important de planifier les stratégies d’étiquette avec soin avant de les configurer. Si une organisation a besoin de modifier la priorité des stratégies d’étiquette, elle devra les supprimer et les recréer.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="a11ed-197">Priorité des étiquettes appliquées manuellement par l’utilisateur sur les étiquettes appliquées automatiquement</span><span class="sxs-lookup"><span data-stu-id="a11ed-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="a11ed-p121">Les étiquettes appliquées manuellement par l’utilisateur sont prioritaires sur les étiquettes appliquées automatiquement. Les stratégies d’application automatique ne peuvent pas remplacer une étiquette déjà appliquée par un utilisateur. Les utilisateurs peuvent remplacer les étiquettes qui sont appliquées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="a11ed-201">Possibilité de mise à jour des étiquettes attribuées automatiquement</span><span class="sxs-lookup"><span data-stu-id="a11ed-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="a11ed-202">Les étiquettes attribuées automatiquement peuvent être mises à jour par de nouvelles stratégies d’étiquetage plus récentes ou par l’actualisation de stratégies existantes.</span><span class="sxs-lookup"><span data-stu-id="a11ed-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="a11ed-203">Assurez-vous que le plan d’implémentation des étiquettes inclut :</span><span class="sxs-lookup"><span data-stu-id="a11ed-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="a11ed-204">la priorisation de l’ordre dans lequel les stratégies d’application automatique sont créées ;</span><span class="sxs-lookup"><span data-stu-id="a11ed-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="a11ed-p122">l’octroi de suffisamment de temps pour que les étiquettes soient automatiquement appliquées avant de les déployer pour que les utilisateurs puissent les appliquer manuellement. L’application des étiquettes à tout le contenu remplissant les conditions peut durer sept jours au maximum.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="a11ed-207">Exemple de priorité permettant de créer des stratégies d’application automatique</span><span class="sxs-lookup"><span data-stu-id="a11ed-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a11ed-208"><strong>Étiquettes</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="a11ed-209"><strong>Ordre de priorité pour la création de stratégie d’application automatique</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a11ed-210">Ressources humaines — Données des employés</span><span class="sxs-lookup"><span data-stu-id="a11ed-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="a11ed-211">1</span><span class="sxs-lookup"><span data-stu-id="a11ed-211">1.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a11ed-212">Données client</span><span class="sxs-lookup"><span data-stu-id="a11ed-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="a11ed-213">2</span><span class="sxs-lookup"><span data-stu-id="a11ed-213">2.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a11ed-214">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="a11ed-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="a11ed-215">3</span><span class="sxs-lookup"><span data-stu-id="a11ed-215">3.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a11ed-216">Ressources humaines — Données salariales</span><span class="sxs-lookup"><span data-stu-id="a11ed-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="a11ed-217">4</span><span class="sxs-lookup"><span data-stu-id="a11ed-217">4.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a11ed-218">Confidentiel</span><span class="sxs-lookup"><span data-stu-id="a11ed-218">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="a11ed-219">5</span><span class="sxs-lookup"><span data-stu-id="a11ed-219">5.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a11ed-220">Public</span><span class="sxs-lookup"><span data-stu-id="a11ed-220">Public</span></span></td>
<td align="left"><span data-ttu-id="a11ed-221">6</span><span class="sxs-lookup"><span data-stu-id="a11ed-221">6.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a11ed-222">Personnelle</span><span class="sxs-lookup"><span data-stu-id="a11ed-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="a11ed-223">Pas de stratégie d’application automatique</span><span class="sxs-lookup"><span data-stu-id="a11ed-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="a11ed-224">Création d’étiquettes et de stratégies d’étiquetage à application automatique</span><span class="sxs-lookup"><span data-stu-id="a11ed-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="a11ed-225">Créez des étiquettes et des stratégies dans le Centre de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="a11ed-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a11ed-226"><strong>Étape</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="a11ed-227"><strong>Description</strong></span><span class="sxs-lookup"><span data-stu-id="a11ed-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="a11ed-228">Accordez des autorisations aux membres de votre équipe de conformité.</span><span class="sxs-lookup"><span data-stu-id="a11ed-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="a11ed-p123">Les membres de votre équipe de conformité qui créent des étiquettes ont besoin d’autorisations pour utiliser le Centre de sécurité &amp; de conformité. Accédez à des Autorisations dans le Centre de sécurité et de conformité et modifiez les membres du groupe Administrateur de conformité.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="a11ed-231">Reportez-vous à la rubrique <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Octroi de l’accès au Centre de sécurité &amp; de conformité Office 365 aux utilisateurs</a>.</span><span class="sxs-lookup"><span data-stu-id="a11ed-231">Give users access to the Office 365 Security & Compliance Center</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="a11ed-232">Créez des étiquettes d’Office.</span><span class="sxs-lookup"><span data-stu-id="a11ed-232">Phase 3: Create Office 365 labels</span></span></p></td>
<td align="left"><span data-ttu-id="a11ed-233">Accédez à Classifications dans le Centre de sécurité et de conformité, sélectionnez Étiquettes, puis créez des étiquettes pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a11ed-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="a11ed-234">Créez des stratégies d’application automatique pour les étiquettes.</span><span class="sxs-lookup"><span data-stu-id="a11ed-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="a11ed-p124">Accédez à Classification dans le Centre de sécurité et de conformité, sélectionnez les stratégies d’étiquetage et créez les stratégies d’application automatique des étiquettes. Veillez à créer ces stratégies par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="a11ed-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a11ed-237">L’image suivante montre comment créer une étiquette à application automatique pour l’étiquette de données Client.</span><span class="sxs-lookup"><span data-stu-id="a11ed-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![Création et application d’étiquette pour des données client](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="a11ed-239">Dans cette illustration :</span><span class="sxs-lookup"><span data-stu-id="a11ed-239">In the illustration:</span></span>

-   <span data-ttu-id="a11ed-240">L’étiquette « Données client » est créée.</span><span class="sxs-lookup"><span data-stu-id="a11ed-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="a11ed-241">Les types d’informations sensibles souhaitée pour le RGPD sont répertoriées : numéro national belge, numéro de carte de crédit, numéro de carte d’identité en Croatie, ID national en Finlande</span><span class="sxs-lookup"><span data-stu-id="a11ed-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="a11ed-242">La création d’une stratégie d’application automatique attribue l’étiquette « Données client » à tous les fichiers qui incluent un des types d’informations sensibles que vous ajoutez à la stratégie.</span><span class="sxs-lookup"><span data-stu-id="a11ed-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
