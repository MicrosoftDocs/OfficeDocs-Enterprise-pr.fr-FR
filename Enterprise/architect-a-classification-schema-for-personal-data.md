---
title: "Création d’un schéma de classification pour les données personnelles"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- GDPR
- Strat_O365_Enterprise
ms.assetid: 
description: "Déterminez si votre organisation implémentera des étiquettes dans le cadre de votre plan RGPD."
ms.openlocfilehash: ee3c01cd4fd99fcc62bbde445eeb3018bb05f586
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="architect-a-classification-schema-for-personal-data"></a><span data-ttu-id="c3d19-103">Création d’un schéma de classification pour les données personnelles</span><span class="sxs-lookup"><span data-stu-id="c3d19-103">Architect a classification schema for personal data</span></span>

<span data-ttu-id="c3d19-p101">Les articles précédents de cette série se concentrent sur l’utilisation des types d’informations sensibles pour identifier les données personnelles qui sont soumises au RGPD. Les types d’informations sensibles constituent une forme de classification qui pourrait vous suffire. Toutefois, de nombreuses organisations implémentent une stratégie de gouvernance des données plus large qui utilise des étiquettes. Utilisez cette rubrique pour déterminer si vous souhaitez implémenter des étiquettes également dans le cadre de votre plan RGPD. Si c’est le cas, cette rubrique fournit des conseils et des exemples.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p101">Previous articles in this series focus on using sensitive information types to identify personal data that is subject to GDPR. Sensitive information types are a form of classification. This might be all the classification you need. However, many organizations implement a broader data governance strategy using labels. Use this topic to decide if you also want to implement labels as part of your GDPR plan. If you do, this topic provides some guidance and examples.</span></span>

<span data-ttu-id="c3d19-p102">Remarque : la définition d’un schéma de classification pour une organisation et la configuration des stratégies, étiquettes et conditions nécessitent une planification et une préparation rigoureuses. Il est important de savoir qu’il ne s’agit pas d’un processus informatisé. Vous devez collaborer avec votre équipe juridique et de conformité pour développer une classification appropriée et un schéma de création d’étiquettes pour les données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p102">Note: Defining a classification schema for an organization and configuring policies, labels, and conditions requires careful planning and preparation. It is important to realize that this is not an IT driven process. Be sure to work with your legal and compliance team to develop an appropriate classification and labeling schema for your organization’s data.</span></span>

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a><span data-ttu-id="c3d19-113">Utilisation ou non d’étiquettes en plus des types de données sensibles</span><span class="sxs-lookup"><span data-stu-id="c3d19-113">Decide if you are using labels in addition to sensitive data types</span></span>

<span data-ttu-id="c3d19-p103">Vous avez le choix entre deux approches de classification dans Office 365 pour les informations personnelles. L’une d’elles peut être utilisée pour la protection RGPD. Si vous décidez d’utiliser uniquement des types d’informations sensibles pour la classification, vous pouvez ignorer le reste de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p103">You can take one of two approaches for classification in Office 365 for personal information. Either of these can be used for GDPR protection. If decide to use only sensitive information types for classification, you can skip the rest of this topic.</span></span>

<span data-ttu-id="c3d19-117">Choisissez l'une des options suivantes.</span><span class="sxs-lookup"><span data-stu-id="c3d19-117">Choose one of the following options</span></span>

### <a name="option-1-use-only-office-365-sensitive-information-types"></a><span data-ttu-id="c3d19-118">Option 1 : utiliser des types d’informations sensibles Office 365 uniquement</span><span class="sxs-lookup"><span data-stu-id="c3d19-118">Option 1: Use only Office 365 sensitive information types</span></span>

-   <span data-ttu-id="c3d19-119">Les types d’informations sensibles sont efficaces pour identifier et protéger les données personnelles soumises au RGPD et d’autres types de règlements.</span><span class="sxs-lookup"><span data-stu-id="c3d19-119">Sensitive information types work well to identify and protect personal data subject to GDPR and other types of regulations.</span></span>

-   <span data-ttu-id="c3d19-120">Ils sont plus simples à utiliser si votre organisation n’a pas encore (ou n’envisage pas d’implémenter) de plan de gouvernance de données plus large qui utilise des étiquettes.</span><span class="sxs-lookup"><span data-stu-id="c3d19-120">These are simpler to use if your organization doesn’t already have or plan to implement a broader data governance plan using labels.</span></span>

-   <span data-ttu-id="c3d19-121">Ils fonctionnent avec des règles de protection contre la perte de données (à l’instar des étiquettes Office).</span><span class="sxs-lookup"><span data-stu-id="c3d19-121">These work with DLP rules (so do Office labels).</span></span>

-   <span data-ttu-id="c3d19-122">À l’avenir, ils fonctionneront avec Cloud App Security et vous pourrez détecter les informations sensibles dans d’autres applications SaaS.</span><span class="sxs-lookup"><span data-stu-id="c3d19-122">In the future these will work with Cloud App Security so you can detect sensitive information in other SaaS apps.</span></span>

### <a name="option-2-use-sensitive-information-types--office-labels"></a><span data-ttu-id="c3d19-123">Option 2 : utiliser des types d’informations sensibles + des étiquettes Office</span><span class="sxs-lookup"><span data-stu-id="c3d19-123">Option 2: Use sensitive information types + Office labels</span></span>

-   <span data-ttu-id="c3d19-124">Vous aurez besoin de types d’informations sensibles pour appliquer automatiquement des étiquettes à des données personnelles qui sont soumises au RGPD, donc ceci est une condition préalable.</span><span class="sxs-lookup"><span data-stu-id="c3d19-124">You’ll need sensitive information types to automatically apply labels to personal data that is subject to GDPR, so these are a prerequisite.</span></span>

-   <span data-ttu-id="c3d19-125">L’utilisation d’étiquettes Office vous permet d’inclure des données personnelles qui sont soumises au RGPD dans un plan de gouvernance des données plus large pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="c3d19-125">Using Office labels allows you to include personal data that is subject to GDPR into a broader data governance plan for your organization.</span></span>

-   <span data-ttu-id="c3d19-126">Plus tard, les étiquettes Office convergeront avec les étiquettes Azure Information Protection dans une classification unifiée et un moteur de création d’étiquettes.</span><span class="sxs-lookup"><span data-stu-id="c3d19-126">Later, Office labels will converge with Azure Information Protection labels into a unified classification and labeling engine.</span></span>

## <a name="develop-a-label-schema-that-includes-personal-data"></a><span data-ttu-id="c3d19-127">Développement d’un schéma d’étiquettes qui comprend des données personnelles</span><span class="sxs-lookup"><span data-stu-id="c3d19-127">Develop a label schema that includes personal data</span></span>

<span data-ttu-id="c3d19-p104">Avant d’utiliser des fonctionnalités techniques pour appliquer des étiquettes et une protection, commencez par définir un schéma de classification à utiliser au sein de votre organisation. Il se peut que votre organisation ait déjà un schéma de classification, ce qui facilite l’ajout de données personnelles. Cette rubrique inclut un exemple de schéma de classification. Vous pouvez l’utiliser comme point de départ, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p104">Before using technical capabilities to apply labels and protection, first work across your organization to define a classification schema. Your organization might already have a classification schema, which makes it easier to add personal data. This topic includes an example classification schema. You can use this as a starting point, if needed.</span></span>

### <a name="getting-started"></a><span data-ttu-id="c3d19-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c3d19-132">Getting started</span></span>

<span data-ttu-id="c3d19-p105">Commencez par décider du nombre et des noms des étiquettes à implémenter. Ne vous souciez pas de la technologie à utiliser ni de la façon dont les étiquettes seront appliquées. Appliquez ce schéma dans l’ensemble de votre organisation, y compris les données qui se trouvent en local et dans d’autres services cloud.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p105">Begin by deciding on the number and names of labels to implement. Do this activity without worrying about which technology to use and how labels will be applied. Apply this schema universally throughout your organization, including data that resides on premises and in other cloud services.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c3d19-136">Recommandations</span><span class="sxs-lookup"><span data-stu-id="c3d19-136">Recommendations</span></span> 

<span data-ttu-id="c3d19-137">Lorsque vous concevez et implémentez des stratégies, étiquettes et conditions, vous pouvez suivre ces recommandations :</span><span class="sxs-lookup"><span data-stu-id="c3d19-137">When designing and implementing policies, labels and conditions, consider following these recommendations:</span></span>

-   <span data-ttu-id="c3d19-p106">Utilisez le schéma de classification existant (le cas échéant) : de nombreuses organisations utilisent déjà la classification des données d’une certaine façon. Évaluez soigneusement le schéma d’étiquettes existant et, si possible, utilisez-le en l’état. L’utilisation d’étiquettes connues qui sont reconnaissables pour l’utilisateur final favorisa l’adoption.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p106">Use existing classification schema (if any) — Many organizations already are using data classification in some form. Carefully evaluate the existing label schema and if possible use it as is. Using familiar labels that are recognizable to the end-user will drive adoption.</span></span>

-   <span data-ttu-id="c3d19-p107">Commencez par des étiquettes et des stratégies par défaut : toutes les solutions sont accompagnées d’un ensemble d’étiquettes et de stratégies prédéfinies. Évaluez-les soigneusement en fonction des exigences juridiques et professionnelles des organisations et envisagez de les utiliser plutôt que d’en créer d’autres.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p107">Start with default policies and labels — All solutions come with a set of predefined policies and labels. Carefully evaluate these against the organizations legal and business requirements and consider using them instead of creating new ones.</span></span>

-   <span data-ttu-id="c3d19-p108">Commencez avec un petit nombre : il n’y a presque aucune limite au nombre d’étiquettes pouvant être créées. Toutefois, un grand nombre d’étiquettes et d’étiquettes secondaires aura un impact négatif sur l’adoption. Trop de choix signifie souvent aucun choix.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p108">Start small — There is virtually no limit to the number of labels that can be created. However, large numbers of labels and sub-labels will negatively impact the adoption. Too many choices often means no choice at all.</span></span>

-   <span data-ttu-id="c3d19-146">Utilisez des scénarios et des cas d’utilisation : identifiez des cas d’utilisation courants au sein de l’organisation et utilisez des scénarios dérivés du RGPD pour vérifier si la configuration d’étiquette et de classification envisagée fonctionnera en pratique.</span><span class="sxs-lookup"><span data-stu-id="c3d19-146">Use scenarios and use cases — Identify common use cases within the organization and use scenarios derived from the GDPR to verify if the envisioned label and classification configuration will work in practice.</span></span>

-   <span data-ttu-id="c3d19-p109">Posez-vous des questions à chaque demande d’une nouvelle étiquette, est-ce que chaque scénario ou cas d’utilisation nécessite vraiment une nouvelle étiquette ou pouvons-nous utiliser celles que l’on a déjà ? Le fait d’utiliser un nombre d’étiquettes restreint améliore l’adoption.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p109">Question every request for a new label, does every scenario or use case really need a new label or can we use what we already have? Keeping the number of labels to a minimum improves adoption.</span></span>

-   <span data-ttu-id="c3d19-p110">Utilisez des étiquettes secondaires pour des services clés : certains services auront des besoins spécifiques nécessitant des étiquettes spécifiques. Définissez ces étiquettes comme étiquettes secondaires d’une étiquette existante et envisagez d’utiliser des stratégies limitées qui sont affectées à des groupes d’utilisateurs plutôt que des stratégies globales.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p110">Use sub-labels for key departments, some departments will have specific needs that require specific labels. Define these labels as sub-labels to an existing label and consider using scoped policies that are assigned to user groups instead of globally.</span></span>

-   <span data-ttu-id="c3d19-p111">Utilisez des stratégies limitées, c’est-à-dire des stratégies qui ciblent des sous-ensembles d’utilisateurs, pour éviter la « surcharge d’étiquettes ». Une stratégie limitée permet d’attribuer des étiquettes (secondaires) propres à un rôle ou à un service uniquement aux employés qui travaillent pour ce service spécifique.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p111">Consider scoped policies, polices targeted at subsets of users will prevent "label overload". A scoped policy enables assigning role or department specific (sub-)labels to just employees that work for that specific department.</span></span>

-   <span data-ttu-id="c3d19-p112">Utiliser des noms d’étiquette explicites : il est recommandé de ne pas utiliser de jargon, de normes ni d’acronymes comme noms d’étiquette. Essayez d’utiliser des noms évocateurs pour l’utilisateur final afin d’améliorer l’adoption. Au lieu d’utiliser des étiquettes comme PII, PCI, HIPAA, LBI, MBI et HBI, utilisez des noms tels que Non professionnel, Public, Général, Confidentiel et Hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p112">Use meaningful label names, it is recommended not to use jargon, standards or acronyms as label names. Try to use names that resonate with the end user to improve adoption. Instead of using labels like PII, PCI, HIPAA, LBI, MBI and HBI consider names like Non-Business, Public, General, Confidential and Highly Confidential.</span></span>

### <a name="example-classification-schema"></a><span data-ttu-id="c3d19-156">Exemple de schéma de classification</span><span class="sxs-lookup"><span data-stu-id="c3d19-156">Example classification schema</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c3d19-157"><strong>Nom de l’étiquette</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-157"><strong>Label name</strong></span></span></th>
<th align="left"><span data-ttu-id="c3d19-158"><strong>Description</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-158"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-159">Personnel</span><span class="sxs-lookup"><span data-stu-id="c3d19-159">Personal</span></span></td>
<td align="left"><span data-ttu-id="c3d19-160">Données non métiers, pour une utilisation personnelle uniquement.</span><span class="sxs-lookup"><span data-stu-id="c3d19-160">Non-business data, for personal use only.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-161">Public</span><span class="sxs-lookup"><span data-stu-id="c3d19-161">Public</span></span></td>
<td align="left"><span data-ttu-id="c3d19-162">Données métiers qui sont spécifiquement préparées et approuvées pour une utilisation publique.</span><span class="sxs-lookup"><span data-stu-id="c3d19-162">Business data that is specifically prepared and approved for public consumption.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-163">Données client</span><span class="sxs-lookup"><span data-stu-id="c3d19-163">Customer data</span></span></td>
<td align="left"><span data-ttu-id="c3d19-p113">Données métiers qui contiennent des informations personnelles identifiables. Les numéros de carte de crédit, les numéros de compte bancaire et les numéros de sécurité sociale en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p113">Business data that contains personal identifiable information. Examples are credit card numbers, bank account numbers, and social security numbers.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-166">Données RH</span><span class="sxs-lookup"><span data-stu-id="c3d19-166">HR data</span></span></td>
<td align="left"><span data-ttu-id="c3d19-167">Données de ressources humaines relatives aux employés de Contoso, telles que les données de salaire et de numéro d’employé.</span><span class="sxs-lookup"><span data-stu-id="c3d19-167">Human Resource data about Contoso employees, such as employee number and salary data.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-168">Confidentiel</span><span class="sxs-lookup"><span data-stu-id="c3d19-168">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="c3d19-p114">Données métiers sensibles qui peuvent porter atteinte à l’entreprise si elles sont partagées avec des personnes non autorisées. Les contrats, rapports de sécurité, résumés des prévisions et données des comptes commerciaux en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p114">Sensitive business data that could cause damage to the business if shared with unauthorized people. Examples include contracts, security reports, forecast summaries, and sales account data.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-171">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="c3d19-171">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="c3d19-p115">Données métiers très sensibles qui porteraient atteinte à l’entreprise si elles étaient partagées avec des personnes non autorisées. Les informations relatives aux employés et aux clients, mots de passe, code source et rapports financiers prédéfinis en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p115">Very sensitive business data that would cause damage to the business if it was shared with unauthorized people. Examples include employee and customer information, passwords, source code, and pre-announced financial reports.</span></span></td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a><span data-ttu-id="c3d19-174">Définition d’une taxonomie et de critères de recherche pour chaque étiquette</span><span class="sxs-lookup"><span data-stu-id="c3d19-174">Define a taxonomy and search criteria for each label</span></span>

<span data-ttu-id="c3d19-p116">Après le développement d’un schéma de classification pour votre organisation, l’étape suivante consiste à développer la taxonomie et les critères de recherche pour rechercher ces données. Pour les données personnelles, vous avez déjà effectué cette tâche en identifiant les types d’informations sensibles et en personnalisant ou créant des types d’informations sensibles pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p116">After developing a classification schema for your organization, the next step is to develop the taxonomy and search criteria for finding this data. For personal data, you’ve already completed this work by identifying sensitive information types and also by customizing or creating new sensitive information types for your environment.</span></span>

<span data-ttu-id="c3d19-p117">Le tableau suivant fournit un exemple de schéma de taxonomie et des critères de recherche pour une organisation. Les étiquettes sont classées par niveau de confidentialité (de moins sensibles à plus sensibles) pour garantir que l’étiquette appropriée est attribuée aux données qui correspondent à plusieurs conditions d’étiquettes.</span><span class="sxs-lookup"><span data-stu-id="c3d19-p117">The following table provides an example schema, taxonomy, and search criteria for an organization. The labels are ordered by sensitivity level from least sensitive to most sensitive to ensure that data that matches multiple label conditions is assigned the appropriate label.</span></span>

<span data-ttu-id="c3d19-179">Remarque : l’exemple de configuration est fourni à des fins d’illustration uniquement et n’est pas destiné à servir de conseil ni de référence.</span><span class="sxs-lookup"><span data-stu-id="c3d19-179">Note: The configuration example is provided for illustration only and is not intended as deployment guidance or reference.</span></span>

<span data-ttu-id="c3d19-180">L’important est de garantir que le travail que vous effectuez pour classer les données personnelles pour la conformité au RGPD fonctionne bien avec les objectifs de l’ensemble de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="c3d19-180">The important takeaway is to ensure that the work you invest to classify personal data for GDPR compliance fits together with the objectives for your entire organization.</span></span>

### <a name="example-schema-taxonomy-and-search-criteria"></a><span data-ttu-id="c3d19-181">Exemple de schéma, taxonomie et critères de recherche</span><span class="sxs-lookup"><span data-stu-id="c3d19-181">Example schema, taxonomy, and search criteria</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c3d19-182"><strong>Étiquette</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-182"><strong>label</strong></span></span></th>
<th align="left"><span data-ttu-id="c3d19-183"><strong>Taxonomie</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-183"><strong>Taxonomy</strong></span></span></th>
<th align="left"><span data-ttu-id="c3d19-184"><strong>Méthode</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-184"><strong>method</strong></span></span></th>
<th align="left"><span data-ttu-id="c3d19-185"><strong>Syntaxe de recherche</strong></span><span class="sxs-lookup"><span data-stu-id="c3d19-185"><strong>Search syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-186">Personnel</span><span class="sxs-lookup"><span data-stu-id="c3d19-186">Personal</span></span></td>
<td align="left"><span data-ttu-id="c3d19-187">Documents étiquetés manuellement avec l’étiquette Personnel par l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="c3d19-187">Documents manually labelled personal by the end user.</span></span></td>
<td align="left"><span data-ttu-id="c3d19-188">Manuel</span><span class="sxs-lookup"><span data-stu-id="c3d19-188">Manual</span></span></td>
<td align="left"><span data-ttu-id="c3d19-189">Documents étiquetés manuellement avec l’étiquette Personnel par l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="c3d19-189">Documents manually labelled personal by the end user.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-190">Public</span><span class="sxs-lookup"><span data-stu-id="c3d19-190">Public</span></span></td>
<td align="left"><span data-ttu-id="c3d19-191">Documents contenant l’expression ne respectant pas la casse Approuvé pour divulgation publique ##/### où # représente n’importe quel chiffre.</span><span class="sxs-lookup"><span data-stu-id="c3d19-191">Documents containing the case insensitive phrase Approved for Public Release ##/#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="c3d19-192">KQL</span><span class="sxs-lookup"><span data-stu-id="c3d19-192">KQL</span></span></p>
<p><span data-ttu-id="c3d19-193">RegEx</span><span class="sxs-lookup"><span data-stu-id="c3d19-193">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="c3d19-194">KQL — Approuvé pour divulgation publique\*</span><span class="sxs-lookup"><span data-stu-id="c3d19-194">KQL — Approved for Public Release\*</span></span></p>
<p><span data-ttu-id="c3d19-195">RegEx — (?i)(\bApprouvé pour divulgation publique \d{2}\/\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="c3d19-195">RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-196">Données client</span><span class="sxs-lookup"><span data-stu-id="c3d19-196">Customer data</span></span></td>
<td align="left"><span data-ttu-id="c3d19-197">Types d’informations sensibles pour les données des citoyens européens.</span><span class="sxs-lookup"><span data-stu-id="c3d19-197">Sensitive information types for EU citizen data.</span></span></td>
<td align="left"><span data-ttu-id="c3d19-198">Types d’informations sensibles</span><span class="sxs-lookup"><span data-stu-id="c3d19-198">Sensitive information types</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-199">Ressources humaines — Données des employés</span><span class="sxs-lookup"><span data-stu-id="c3d19-199">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="c3d19-200">Documents incluant l’ID d’employé respectant la casse au format CONTOSO-9##### où # représente n’importe quel chiffre.</span><span class="sxs-lookup"><span data-stu-id="c3d19-200">Documents that include the case sensitive employee id in the format CONTOSO-9##### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="c3d19-201">KQL</span><span class="sxs-lookup"><span data-stu-id="c3d19-201">KQL</span></span></p>
<p><span data-ttu-id="c3d19-202">RegEx</span><span class="sxs-lookup"><span data-stu-id="c3d19-202">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="c3d19-203">KQL — CONTOSO-9\*</span><span class="sxs-lookup"><span data-stu-id="c3d19-203">KQL — CONTOSO-9\*</span></span></p>
<p><span data-ttu-id="c3d19-204">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="c3d19-204">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-205">Ressources humaines — Données salariales</span><span class="sxs-lookup"><span data-stu-id="c3d19-205">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="c3d19-206">Documents qui incluent le mot-clé (ne respectant pas la casse) Contoso ET le mot-clé Salaire (ne respectant pas la casse) OU Rémunération</span><span class="sxs-lookup"><span data-stu-id="c3d19-206">Documents that include the keyword (not case sensitive) Contoso AND either keyword (not case sensitive) Salary OR Compensation</span></span></td>
<td align="left"><p><span data-ttu-id="c3d19-207">KQL</span><span class="sxs-lookup"><span data-stu-id="c3d19-207">KQL</span></span></p>
<p><span data-ttu-id="c3d19-208">RegEx</span><span class="sxs-lookup"><span data-stu-id="c3d19-208">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="c3d19-209">KQL — Contoso AND (Salaire OR Rémunération)</span><span class="sxs-lookup"><span data-stu-id="c3d19-209">KQL — Contoso AND (Salary OR Compensation)</span></span></p>
<p><span data-ttu-id="c3d19-210">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="c3d19-210">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c3d19-211">Confidentiel</span><span class="sxs-lookup"><span data-stu-id="c3d19-211">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="c3d19-212">Tous les documents contenant l’expression Contoso Confidentiel (ne respectant pas la casse).</span><span class="sxs-lookup"><span data-stu-id="c3d19-212">Documents containing the phrase (not case sensitive) Contoso Confidential.</span></span></td>
<td align="left"><p><span data-ttu-id="c3d19-213">KQL</span><span class="sxs-lookup"><span data-stu-id="c3d19-213">KQL</span></span></p>
<p><span data-ttu-id="c3d19-214">RegEx</span><span class="sxs-lookup"><span data-stu-id="c3d19-214">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="c3d19-215">KQL — Contoso Confidentiel</span><span class="sxs-lookup"><span data-stu-id="c3d19-215">KQL — Contoso Confidential</span></span></p>
<p><span data-ttu-id="c3d19-216">RegEx — (?i)(\bContoso Confidentiel\b)</span><span class="sxs-lookup"><span data-stu-id="c3d19-216">RegEx — (?i)(\bContoso Confidential\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c3d19-217">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="c3d19-217">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="c3d19-218">Documents incluant l’expression Contoso Secret (respectant la casse) ou Secret-C#### où # représente n’importe quel chiffre.</span><span class="sxs-lookup"><span data-stu-id="c3d19-218">Documents that include either pharase (case sensitive) Contoso Secret or Secret-C#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="c3d19-219">KQL</span><span class="sxs-lookup"><span data-stu-id="c3d19-219">KQL</span></span></p>
<p><span data-ttu-id="c3d19-220">RegEx</span><span class="sxs-lookup"><span data-stu-id="c3d19-220">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="c3d19-221">KQL — Contoso Secret OR Secret-C\*</span><span class="sxs-lookup"><span data-stu-id="c3d19-221">KQL — Contoso Secret OR Secret-C\*</span></span></p>
<p><span data-ttu-id="c3d19-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="c3d19-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span></span></p></td>
</tr>
</tbody>
</table>
