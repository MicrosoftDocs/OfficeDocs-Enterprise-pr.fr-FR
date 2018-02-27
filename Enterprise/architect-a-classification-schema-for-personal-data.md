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
# <a name="architect-a-classification-schema-for-personal-data"></a>Création d’un schéma de classification pour les données personnelles

Les articles précédents de cette série se concentrent sur l’utilisation des types d’informations sensibles pour identifier les données personnelles qui sont soumises au RGPD. Les types d’informations sensibles constituent une forme de classification qui pourrait vous suffire. Toutefois, de nombreuses organisations implémentent une stratégie de gouvernance des données plus large qui utilise des étiquettes. Utilisez cette rubrique pour déterminer si vous souhaitez implémenter des étiquettes également dans le cadre de votre plan RGPD. Si c’est le cas, cette rubrique fournit des conseils et des exemples.

Remarque : la définition d’un schéma de classification pour une organisation et la configuration des stratégies, étiquettes et conditions nécessitent une planification et une préparation rigoureuses. Il est important de savoir qu’il ne s’agit pas d’un processus informatisé. Vous devez collaborer avec votre équipe juridique et de conformité pour développer une classification appropriée et un schéma de création d’étiquettes pour les données de votre organisation.

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a>Utilisation ou non d’étiquettes en plus des types de données sensibles

Vous avez le choix entre deux approches de classification dans Office 365 pour les informations personnelles. L’une d’elles peut être utilisée pour la protection RGPD. Si vous décidez d’utiliser uniquement des types d’informations sensibles pour la classification, vous pouvez ignorer le reste de cette rubrique.

Choisissez l'une des options suivantes.

### <a name="option-1-use-only-office-365-sensitive-information-types"></a>Option 1 : utiliser des types d’informations sensibles Office 365 uniquement

-   Les types d’informations sensibles sont efficaces pour identifier et protéger les données personnelles soumises au RGPD et d’autres types de règlements.

-   Ils sont plus simples à utiliser si votre organisation n’a pas encore (ou n’envisage pas d’implémenter) de plan de gouvernance de données plus large qui utilise des étiquettes.

-   Ils fonctionnent avec des règles de protection contre la perte de données (à l’instar des étiquettes Office).

-   À l’avenir, ils fonctionneront avec Cloud App Security et vous pourrez détecter les informations sensibles dans d’autres applications SaaS.

### <a name="option-2-use-sensitive-information-types--office-labels"></a>Option 2 : utiliser des types d’informations sensibles + des étiquettes Office

-   Vous aurez besoin de types d’informations sensibles pour appliquer automatiquement des étiquettes à des données personnelles qui sont soumises au RGPD, donc ceci est une condition préalable.

-   L’utilisation d’étiquettes Office vous permet d’inclure des données personnelles qui sont soumises au RGPD dans un plan de gouvernance des données plus large pour votre organisation.

-   Plus tard, les étiquettes Office convergeront avec les étiquettes Azure Information Protection dans une classification unifiée et un moteur de création d’étiquettes.

## <a name="develop-a-label-schema-that-includes-personal-data"></a>Développement d’un schéma d’étiquettes qui comprend des données personnelles

Avant d’utiliser des fonctionnalités techniques pour appliquer des étiquettes et une protection, commencez par définir un schéma de classification à utiliser au sein de votre organisation. Il se peut que votre organisation ait déjà un schéma de classification, ce qui facilite l’ajout de données personnelles. Cette rubrique inclut un exemple de schéma de classification. Vous pouvez l’utiliser comme point de départ, le cas échéant.

### <a name="getting-started"></a>Prise en main

Commencez par décider du nombre et des noms des étiquettes à implémenter. Ne vous souciez pas de la technologie à utiliser ni de la façon dont les étiquettes seront appliquées. Appliquez ce schéma dans l’ensemble de votre organisation, y compris les données qui se trouvent en local et dans d’autres services cloud.

### <a name="recommendations"></a>Recommandations 

Lorsque vous concevez et implémentez des stratégies, étiquettes et conditions, vous pouvez suivre ces recommandations :

-   Utilisez le schéma de classification existant (le cas échéant) : de nombreuses organisations utilisent déjà la classification des données d’une certaine façon. Évaluez soigneusement le schéma d’étiquettes existant et, si possible, utilisez-le en l’état. L’utilisation d’étiquettes connues qui sont reconnaissables pour l’utilisateur final favorisa l’adoption.

-   Commencez par des étiquettes et des stratégies par défaut : toutes les solutions sont accompagnées d’un ensemble d’étiquettes et de stratégies prédéfinies. Évaluez-les soigneusement en fonction des exigences juridiques et professionnelles des organisations et envisagez de les utiliser plutôt que d’en créer d’autres.

-   Commencez avec un petit nombre : il n’y a presque aucune limite au nombre d’étiquettes pouvant être créées. Toutefois, un grand nombre d’étiquettes et d’étiquettes secondaires aura un impact négatif sur l’adoption. Trop de choix signifie souvent aucun choix.

-   Utilisez des scénarios et des cas d’utilisation : identifiez des cas d’utilisation courants au sein de l’organisation et utilisez des scénarios dérivés du RGPD pour vérifier si la configuration d’étiquette et de classification envisagée fonctionnera en pratique.

-   Posez-vous des questions à chaque demande d’une nouvelle étiquette, est-ce que chaque scénario ou cas d’utilisation nécessite vraiment une nouvelle étiquette ou pouvons-nous utiliser celles que l’on a déjà ? Le fait d’utiliser un nombre d’étiquettes restreint améliore l’adoption.

-   Utilisez des étiquettes secondaires pour des services clés : certains services auront des besoins spécifiques nécessitant des étiquettes spécifiques. Définissez ces étiquettes comme étiquettes secondaires d’une étiquette existante et envisagez d’utiliser des stratégies limitées qui sont affectées à des groupes d’utilisateurs plutôt que des stratégies globales.

-   Utilisez des stratégies limitées, c’est-à-dire des stratégies qui ciblent des sous-ensembles d’utilisateurs, pour éviter la « surcharge d’étiquettes ». Une stratégie limitée permet d’attribuer des étiquettes (secondaires) propres à un rôle ou à un service uniquement aux employés qui travaillent pour ce service spécifique.

-   Utiliser des noms d’étiquette explicites : il est recommandé de ne pas utiliser de jargon, de normes ni d’acronymes comme noms d’étiquette. Essayez d’utiliser des noms évocateurs pour l’utilisateur final afin d’améliorer l’adoption. Au lieu d’utiliser des étiquettes comme PII, PCI, HIPAA, LBI, MBI et HBI, utilisez des noms tels que Non professionnel, Public, Général, Confidentiel et Hautement confidentiel.

### <a name="example-classification-schema"></a>Exemple de schéma de classification

<table>
<thead>
<tr class="header">
<th align="left"><strong>Nom de l’étiquette</strong></th>
<th align="left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Personnel</td>
<td align="left">Données non métiers, pour une utilisation personnelle uniquement.</td>
</tr>
<tr class="even">
<td align="left">Public</td>
<td align="left">Données métiers qui sont spécifiquement préparées et approuvées pour une utilisation publique.</td>
</tr>
<tr class="odd">
<td align="left">Données client</td>
<td align="left">Données métiers qui contiennent des informations personnelles identifiables. Les numéros de carte de crédit, les numéros de compte bancaire et les numéros de sécurité sociale en sont des exemples.</td>
</tr>
<tr class="even">
<td align="left">Données RH</td>
<td align="left">Données de ressources humaines relatives aux employés de Contoso, telles que les données de salaire et de numéro d’employé.</td>
</tr>
<tr class="odd">
<td align="left">Confidentiel</td>
<td align="left">Données métiers sensibles qui peuvent porter atteinte à l’entreprise si elles sont partagées avec des personnes non autorisées. Les contrats, rapports de sécurité, résumés des prévisions et données des comptes commerciaux en sont des exemples.</td>
</tr>
<tr class="even">
<td align="left">Hautement confidentiel</td>
<td align="left">Données métiers très sensibles qui porteraient atteinte à l’entreprise si elles étaient partagées avec des personnes non autorisées. Les informations relatives aux employés et aux clients, mots de passe, code source et rapports financiers prédéfinis en sont des exemples.</td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a>Définition d’une taxonomie et de critères de recherche pour chaque étiquette

Après le développement d’un schéma de classification pour votre organisation, l’étape suivante consiste à développer la taxonomie et les critères de recherche pour rechercher ces données. Pour les données personnelles, vous avez déjà effectué cette tâche en identifiant les types d’informations sensibles et en personnalisant ou créant des types d’informations sensibles pour votre environnement.

Le tableau suivant fournit un exemple de schéma de taxonomie et des critères de recherche pour une organisation. Les étiquettes sont classées par niveau de confidentialité (de moins sensibles à plus sensibles) pour garantir que l’étiquette appropriée est attribuée aux données qui correspondent à plusieurs conditions d’étiquettes.

Remarque : l’exemple de configuration est fourni à des fins d’illustration uniquement et n’est pas destiné à servir de conseil ni de référence.

L’important est de garantir que le travail que vous effectuez pour classer les données personnelles pour la conformité au RGPD fonctionne bien avec les objectifs de l’ensemble de votre organisation.

### <a name="example-schema-taxonomy-and-search-criteria"></a>Exemple de schéma, taxonomie et critères de recherche

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étiquette</strong></th>
<th align="left"><strong>Taxonomie</strong></th>
<th align="left"><strong>Méthode</strong></th>
<th align="left"><strong>Syntaxe de recherche</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Personnel</td>
<td align="left">Documents étiquetés manuellement avec l’étiquette Personnel par l’utilisateur final.</td>
<td align="left">Manuel</td>
<td align="left">Documents étiquetés manuellement avec l’étiquette Personnel par l’utilisateur final.</td>
</tr>
<tr class="even">
<td align="left">Public</td>
<td align="left">Documents contenant l’expression ne respectant pas la casse Approuvé pour divulgation publique ##/### où # représente n’importe quel chiffre.</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Approuvé pour divulgation publique*</p>
<p>RegEx — (?i)(\bApprouvé pour divulgation publique \d{2}\/\d{4}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">Données client</td>
<td align="left">Types d’informations sensibles pour les données des citoyens européens.</td>
<td align="left">Types d’informations sensibles</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Ressources humaines — Données des employés</td>
<td align="left">Documents incluant l’ID d’employé respectant la casse au format CONTOSO-9##### où # représente n’importe quel chiffre.</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — CONTOSO-9*</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">Ressources humaines — Données salariales</td>
<td align="left">Documents qui incluent le mot-clé (ne respectant pas la casse) Contoso ET le mot-clé Salaire (ne respectant pas la casse) OU Rémunération</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso AND (Salaire OR Rémunération)</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="even">
<td align="left">Confidentiel</td>
<td align="left">Tous les documents contenant l’expression Contoso Confidentiel (ne respectant pas la casse).</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Confidentiel</p>
<p>RegEx — (?i)(\bContoso Confidentiel\b)</p></td>
</tr>
<tr class="odd">
<td align="left">Hautement confidentiel</td>
<td align="left">Documents incluant l’expression Contoso Secret (respectant la casse) ou Secret-C#### où # représente n’importe quel chiffre.</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Secret OR Secret-C*</p>
<p>RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</p></td>
</tr>
</tbody>
</table>
