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
# <a name="apply-labels-to-personal-data-in-office-365"></a>Application d’étiquettes à des données personnelles dans Office 365

 Consultez cette rubrique si vous utilisez des étiquettes Office dans le cadre de votre plan de protection RGPD. Les étiquettes peuvent être actuellement créées dans le Centre de sécurité et de conformité Office 365 et dans Azure Information Protection. À l’avenir, ces technologies convergeront vers une expérience unifiée d’étiquetage et de classification, vous donnant encore plus de possibilités.

Si vous utilisez des étiquettes pour la protection des données personnelles dans Office 365, Microsoft vous recommande de commencer par les étiquettes Office. Vous pouvez utiliser la gouvernance des données avancée pour appliquer automatiquement des étiquettes en fonction de types d’informations sensibles ou d’autres critères. Vous pouvez utiliser des étiquettes Office avec la protection contre la perte de données pour appliquer la protection. Vous pouvez également avoir recours à des étiquettes avec eDiscovery et la recherche de contenu. Vous serez bientôt en mesure d’employer des étiquettes et des types d’informations sensibles avec Cloud App Security pour surveiller les données personnelles qui se trouvent dans d’autres applications SaaS.

Les étiquettes Azure Information Protection sont actuellement recommandées pour l’application d’étiquettes à des fichiers en local ainsi que dans d’autres fournisseurs et services cloud. Elles sont également recommandées pour les fichiers dans Office 365 nécessitant le chiffrement Azure Rights Management (Azure RMS) pour la protection des données, tels que les fichiers contenant des secrets commerciaux.

À ce stade, il n’est pas recommandé d’avoir recours à Azure Information Protection afin d’appliquer le chiffrement Azure RMS à des fichiers dans Office 365 contenant des données soumises au RGPD. Les services Office 365 ne peuvent pas être actuellement lus dans des fichiers chiffrés via RMS. Par conséquent, le service ne peut pas trouver de données sensibles dans ces fichiers.

Les étiquettes Azure Information Protection peuvent être appliquées aux e-mails dans Exchange Online. Ces étiquettes sont compatibles avec la protection contre la perte de données Office 365. Grâce à la classification unifiée et au moteur de création d’étiquettes bientôt disponibles, vous serez en mesure d’utiliser les mêmes étiquettes pour les e-mails et les fichiers, y compris l’étiquetage et la protection automatiques des e-mails en transit.

![Étiquettes Office 365 et étiquettes Azure Information Protection](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

Dans cette illustration :

-   Utilisez les étiquettes Office 365 pour les données personnelles ou pour les fichiers contenant des données hautement réglementées et des secrets commerciaux dans SharePoint Online et OneDrive Entreprise.

-   Utilisez les étiquettes Azure Information Protection (AIP) pour les fichiers contenant des données hautement réglementées et des secrets commerciaux, les e-mails Exchange Online, les fichiers dans d’autres services SaaS, les fichiers dans des centres de données en local et les fichiers dans d’autres fournisseurs cloud.

-   Bientôt disponible : les deux types d’étiquettes vont converger vers une expérience unifiée de classification et d’étiquetage.

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a>Utilisation des étiquettes Office et des types d’informations sensibles au sein de Microsoft 365 pour la protection des informations

L’image suivante montre comment les étiquettes Office et les types d’informations sensibles peuvent être utilisés dans les stratégies d’étiquetage, les stratégies de protection contre la perte de données et les stratégies Cloud App Security.

![Étiquettes Office et types d’informations sensibles](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

Concernant l’accessibilité, le tableau suivant fournit les mêmes exemples dans l’illustration.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Éléments de classification</strong></th>
<th align="left"><strong>Stratégies d’étiquetage — 2 exemples</strong></th>
<th align="left"><strong>Stratégies de protection contre la perte de données — 2 exemples</strong></th>
<th align="left"><strong>Stratégies Cloud App Security pour toutes les applications SaaS — 1 exemple</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Étiquettes Office. Exemples : Personnel, Public, Données client, Données RH, Confidentiel, Hautement confidentiel</td>
<td align="left"><p>Appliquer automatiquement l’étiquette...</p>
<p>Données client</p>
<p>... aux documents qui correspondent aux types d’informations sensibles...</p>
<p>&lt;Liste des types d’informations sensibles disponibles&gt;</p></td>
<td align="left"><p>Appliquer cette protection...</p>
<p>&lt;définir la protection&gt;</p>
<p>... à des documents avec cette étiquette...</p>
<p>Données client</p></td>
<td align="left"><p>Avertir quand des fichiers avec les attributs suivants...</p>
<p>&lt;attribut PII prédéfini ou expression personnalisée&gt;</p>
<p>... dans des applications SaaS approuvées sont partagés en dehors de l’organisation</p></td>
</tr>
<tr class="even">
<td align="left">Types d’informations sensibles. Exemples : numéro national belge, numéro de carte de crédit, numéro de carte d’identité en Croatie, ID national en Finlande</td>
<td align="left"><p>Publiez ces étiquettes pour que les utilisateurs puissent les appliquer manuellement...</p>
<p>&lt;sélectionner des étiquettes&gt;</p>
<p>... à ces emplacements...</p>
<p>&lt;tous les emplacements ou choisir des emplacements spécifiques&gt;</p></td>
<td align="left"><p>Appliquer cette protection...</p>
<p>&lt;définir la protection&gt;</p>
<p>... aux documents qui correspondent à ces types d’informations sensibles&gt;</p></td>
<td align="left">Remarque : les attributs prochainement disponibles pour Cloud App Security incluent les types d’informations sensibles Office 365 ainsi que les étiquettes unifiées dans Office 365 et Azure Information Protection.</td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a>Hiérarchisation des stratégies d’étiquette à application automatique

Pour les données personnelles soumises au RGPD, Microsoft recommande l’application automatique des étiquettes à l’aide des types d’informations sensibles traités pour votre environnement. Il est important que les stratégies d’étiquettes à application automatique soient conçues correctement et testées pour s’assurer que le comportement attendu se produit.

L’ordre de création des stratégies d’application automatique et leur utilisation ou non par les utilisateurs ont une incidence sur le résultat. Par conséquent, il est important de planifier avec soin le déploiement. Voici ce que vous devez savoir.

### <a name="one-label-at-a-time"></a>Une seule étiquette à la fois

Vous pouvez uniquement attribuer une seule étiquette à un document.

### <a name="older-auto-apply-policies-win"></a>Priorité des anciennes stratégies d’application automatique

S’il existe plusieurs règles attribuant une étiquette à application automatique et si le contenu remplit les critères de plusieurs règles, l’étiquette de la règle la plus ancienne est attribuée. C’est pourquoi il est important de planifier les stratégies d’étiquette avec soin avant de les configurer. Si une organisation a besoin de modifier la priorité des stratégies d’étiquette, elle devra les supprimer et les recréer.

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a>Priorité des étiquettes appliquées manuellement par l’utilisateur sur les étiquettes appliquées automatiquement

Les étiquettes appliquées manuellement par l’utilisateur sont prioritaires sur les étiquettes appliquées automatiquement. Les stratégies d’application automatique ne peuvent pas remplacer une étiquette déjà appliquée par un utilisateur. Les utilisateurs peuvent remplacer les étiquettes qui sont appliquées automatiquement.

### <a name="auto-assigned-labels-can-be-updated"></a>Possibilité de mise à jour des étiquettes attribuées automatiquement

Les étiquettes attribuées automatiquement peuvent être mises à jour par de nouvelles stratégies d’étiquetage plus récentes ou par l’actualisation de stratégies existantes.

Assurez-vous que le plan d’implémentation des étiquettes inclut :

-   la priorisation de l’ordre dans lequel les stratégies d’application automatique sont créées ;

-   l’octroi de suffisamment de temps pour que les étiquettes soient automatiquement appliquées avant de les déployer pour que les utilisateurs puissent les appliquer manuellement. L’application des étiquettes à tout le contenu remplissant les conditions peut durer sept jours au maximum.

### <a name="example-priority-for-creating-the-auto-apply-policies"></a>Exemple de priorité permettant de créer des stratégies d’application automatique

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étiquettes</strong></th>
<th align="left"><strong>Ordre de priorité pour la création de stratégie d’application automatique</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Ressources humaines — Données des employés</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Données client</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Hautement confidentiel</td>
<td align="left">3</td>
</tr>
<tr class="even">
<td align="left">Ressources humaines — Données salariales</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Confidentiel</td>
<td align="left">5</td>
</tr>
<tr class="even">
<td align="left">Public</td>
<td align="left">6</td>
</tr>
<tr class="odd">
<td align="left">Personnelle</td>
<td align="left">Pas de stratégie d’application automatique</td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a>Création d’étiquettes et de stratégies d’étiquetage à application automatique

Créez des étiquettes et des stratégies dans le Centre de sécurité et de conformité.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étape</strong></th>
<th align="left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Accordez des autorisations aux membres de votre équipe de conformité.</p></td>
<td align="left"><p>Les membres de votre équipe de conformité qui créent des étiquettes ont besoin d’autorisations pour utiliser le Centre de sécurité &amp; de conformité. Accédez à des Autorisations dans le Centre de sécurité et de conformité et modifiez les membres du groupe Administrateur de conformité.</p>
<p>Reportez-vous à la rubrique <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Octroi de l’accès au Centre de sécurité &amp; de conformité Office 365 aux utilisateurs</a>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Créez des étiquettes d’Office.</p></td>
<td align="left">Accédez à Classifications dans le Centre de sécurité et de conformité, sélectionnez Étiquettes, puis créez des étiquettes pour votre environnement.</td>
</tr>
<tr class="odd">
<td align="left"><p>Créez des stratégies d’application automatique pour les étiquettes.</p></td>
<td align="left">Accédez à Classification dans le Centre de sécurité et de conformité, sélectionnez les stratégies d’étiquetage et créez les stratégies d’application automatique des étiquettes. Veillez à créer ces stratégies par ordre de priorité.</td>
</tr>
</tbody>
</table>

L’image suivante montre comment créer une étiquette à application automatique pour l’étiquette de données Client.

![Création et application d’étiquette pour des données client](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

Dans cette illustration :

-   L’étiquette « Données client » est créée.

-   Les types d’informations sensibles souhaitée pour le RGPD sont répertoriées : numéro national belge, numéro de carte de crédit, numéro de carte d’identité en Croatie, ID national en Finlande

-   La création d’une stratégie d’application automatique attribue l’étiquette « Données client » à tous les fichiers qui incluent un des types d’informations sensibles que vous ajoutez à la stratégie.
