---
title: Recherche et localisation des données personnelles
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: ''
description: Découvrez comment rechercher et localiser des données personnelles dans Office 365.
ms.openlocfilehash: 8f1a293377570233e4d3ef01da9c56345768828c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914909"
---
# <a name="search-for-and-find-personal-data"></a>Recherche et localisation des données personnelles

Les données personnelles sont définies à très grande échelle dans le cadre du RGPD comme les données associées à une personne naturelle identifiée ou identifiable qui est résidente de l’Union européenne (UE).

Article 4 - Définitions

> Les « données personnelles » correspondent aux informations relatives à une personne naturelle identifiée ou identifiable (« la personne concernée ») ; une personne naturelle identifiable est une personne qui peut être identifiée, directement ou indirectement, notamment par référence à un identificateur par exemple, un nom, un numéro d’identification, des données de localisation, un identificateur en ligne, ou un ou plusieurs facteurs spécifiques de l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne naturelle ;

Cet article explique comment rechercher des données personnelles stockées dans SharePoint Online et OneDrive Entreprise (qui inclut les sites de tous les groupes Office 365 et Microsoft Teams).

La recherche de données personnelles soumises au RGPD repose sur l’utilisation de types d’informations sensibles dans Office 365. Ceux-ci définissent comment le processus automatisé reconnaît des types d’informations spécifiques tels que les numéros de sécurité sociale et les numéros de carte de crédit. Pour l’instant, ils ne permettent pas de rechercher des données dans les boîtes aux lettres Exchange au repos. Toutefois, les types d’informations sensibles peuvent être utilisés avec des stratégies de protection contre la perte de données pour rechercher des données personnelles dans le courrier en transit.

Par conséquent, même si vous ne pouvez pas utiliser actuellement la recherche de contenu pour rechercher des données personnelles au repos dans les boîtes aux lettres Exchange Online, vous pouvez utiliser les types d’informations sensibles que vous gérez pour le RGPD pour rechercher et protéger des informations personnelles lors de leur envoi par courrier électronique.

## <a name="use-content-search-to-find-personal-data"></a>Utilisation de la recherche de contenu pour rechercher des données personnelles

Microsoft recommande d’utiliser une approche en trois étapes pour rechercher des données personnelles dans Office 365. Le reste de cette rubrique fournit des instructions pour chacune de ces étapes.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étape</strong></th>
<th align="left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1. Recherche des types d’informations sensibles</p></td>
<td align="left"><p>Commencez par utiliser des types d’informations sensibles pour rechercher des données personnelles. Créez une requête de recherche de contenu pour chaque type d’informations sensibles. Exécutez la requête et analysez les résultats.</p>
Si nécessaire, ajoutez des paramètres à la requête afin de réduire les faux positifs : <li>Plage de nombre</li>
    <li>Plage de confiance</li>
    <li>Autres propriétés ou opérateurs pour des requêtes plus complexes</li>
<p>Si nécessaire, modifiez un type d’informations sensibles pour améliorer la précision pour votre organisation :</p>
<p><li>Ajustez le niveau de confiance directement dans le fichier XML.</li></p>
<p><li>Ajoutez des mots-clés.</li></p>
<p><li>Ajustez les exigences de proximité pour les mots-clés.</li></p></td>
</tr>
<tr class="even">
<td align="left"><p>2. Utilisation du langage de requête de mot-clé (KQL) pour rechercher des données personnelles supplémentaires dans votre environnement</p></td>
<td align="left"><p>Pour rechercher des données qui ne sont pas incluses dans des types d’informations sensibles, utilisez le langage de requête de mot-clé KQL pour développer des requêtes personnalisées.</p>
<p>Testez les résultats de ces recherches et ajustez la chaîne de requête KQL jusqu'à ce que vous obteniez le résultat attendu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3. Création de types d’informations sensibles personnalisés à l’aide de requêtes KQL</p></td>
<td align="left">Après avoir optimisé des requêtes KQL pour rechercher des données cibles, créez des types d’informations sensibles personnalisés à l’aide de ces requêtes. Vous pouvez ensuite utiliser ces types d’informations sensibles personnalisés avec la recherche de contenu, dans les stratégies DLP et d’autres outils, ainsi que dans d’autres requêtes KQL.</td>
</tr>
</tbody>
</table>

Prochainement : vous pourrez créer et modifier des types d’informations sensibles dans une nouvelle interface utilisateur dans le Centre de sécurité et de conformité. Vous pouvez voir les résultats correspondants de façon dynamique et optimiser les types d’informations sensibles pour répondre à vos besoins.

## <a name="search-for-sensitive-information-types-using-content-search"></a>Recherche des types d’informations sensibles à l’aide de la recherche de contenu

Commencez la recherche de données personnelles en utilisant les types d’informations sensibles inclus dans Office 365. Ils sont répertoriés dans le Centre de sécurité et de conformité sous Classification.

Cette rubrique inclut la liste des types d’informations sensibles actuels qui s’appliquent aux citoyens de l’Union européenne. Utilisez-les comme point de départ. Vérifiez fréquemment le Centre de sécurité et de conformité pour savoir s’il existe de nouveaux ajouts relatifs à la conformité au RGPD.

Consultez également l’article relatif à la [liste des types d’informations sensibles et à ce qu’ils recherchent](https://support.office.com/fr-FR/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).

Les types d’informations sensibles définissent la façon dont le processus automatisé reconnaît des types d’informations spécifiques tels que les numéros de compte bancaire, de sécurité sociale et de carte de crédit. Les types d’informations sensibles sont également appelés conditions. Un type d’informations sensibles est défini par un modèle qui peut être identifié par une fonction ou une expression régulière. En outre, des preuves corroborantes comme les mots-clés et les sommes de contrôle peuvent être utilisées pour identifier un type d’informations sensibles. La proximité et le niveau de confiance sont également utilisés dans le processus d’évaluation.

Pour l’instant, les types d’informations sensibles ne permettent pas de rechercher des données au repos dans les boîtes aux lettres.

### <a name="using-content-search-with-sensitive-information-types"></a>Utilisation de la recherche de contenu avec des types d’informations sensibles

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étape</strong></th>
<th align="left"><strong>Plus d’informations</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p>Accédez à Recherche de contenu dans le Centre de sécurité et de conformité</p></td>
<td align="left"><p>Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Recherches &amp; enquêtes** &gt; **Recherche de contenu**.</p>
<p>Reportez-vous à la rubrique <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Exécuter une recherche de contenu dans le Centre de sécurité et de conformité Office 365</a>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Création d’un élément de recherche pour chaque type d’informations sensibles</p></td>
<td align="left"><p>Utilisez la syntaxe suivante :</p>
<blockquote>
<p>SensitiveType:”&lt;type&gt;”</p>
</blockquote>
<p>Par exemple :</p>
<blockquote>
<p>SensitiveType:&quot;Numéro de passeport français&quot;</p>
</blockquote>
<p>Étendue de la recherche Scope dans SharePoint (inclut OneDrive Entreprise). Vérifiez que la syntaxe est exacte et qu’il n’y a pas d’espaces supplémentaires ni de fautes de frappe.</p>
<p>Reportez-vous à la rubrique relative à la <a href="https://support.office.com/fr-FR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">création d’une requête pour rechercher des données sensibles stockées sur des sites</a>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Analyse des résultats pour chaque recherche</p></td>
<td align="left"><p>Recherchez ces types de problèmes pour déterminer si la précision de la requête est un objectif :</p>
<p><li>De nombreux faux positifs</li></p>
<p><li>Instances de données connues manquantes</li></p>
<p>Reportez-vous à la rubrique relative à l’<a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">exportation des résultats de la recherche de contenu du Centre de sécurité et de conformité Office 365</a>.</p>
<p>Remarque : si vous utilisez Mozilla Firefox ou Chrome, il se peut que vous deviez d’abord télécharger des rapports avec Internet Explorer ou Edge pour installer le complément requis.</p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a>Types d’informations sensibles pour les données des citoyens européens

Commencez par ces types d’informations sensibles. De nombreux autres types d’informations sensibles seront disponibles prochainement pour les données personnelles dans les pays de l’UE.

> Numéro national belge
>
> Numéro de carte de crédit
>
> Numéro de carte d’identité croate
>
> Numéro d’identification personnelle croate (OIB)
>
> Numéro de carte d’identité nationale tchèque
>
> Numéro d’identification personnelle danois
>
> Numéro de carte de crédit de l'U.E.
>
> Numéro d'identification national finlandais
>
> Numéro de passeport finlandais
>
> Numéro de permis de conduire français
>
> Carte nationale d'identité (CNI) française
>
> Numéro de passeport français
>
> Numéro de sécurité sociale (INSEE) français
>
> Numéro de permis de conduire allemand
>
> Numéro de carte d’identité allemand
>
> Numéro de passeport allemand
>
> Carte d’identité nationale grecque
>
> Numéro de compte international (IBAN)
>
> Adresse IP
>
> Numéro personnel pour le service public irlandais (PPS)
>
> Numéro de permis de conduire italien
>
> Numéro de service des citoyens hollandais (BSN)
>
> Numéro d’identité norvégien
>
> Carte d'identité polonaise
>
> Numéro d'identification national polonais (PESEL)
>
> Numéro de passeport polonais
>
> Numéro de carte de citoyen portugais
>
> Numéro de sécurité sociale (N° S.S.) espagnol
>
> ID national suédois
>
> Numéro de passeport suédois
>
> Numéro de permis de conduire britannique
>
> Numéro de liste électorale du Royaume-Uni
>
> Numéro du service de santé national (NHS) du Royaume-Uni
>
> Numéro d'assurance national (NINO) du Royaume-Uni
>
> Numéro de passeport des États-Unis/du Royaume-Uni

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a>Ajout de paramètres à une requête de type d’informations sensibles pour affiner les résultats

Vous pouvez ajouter ces paramètres à une requête de type d’informations sensibles :

-   Plage de nombre : définit le nombre d'occurrences des informations sensibles qu'un document doit contenir avant qu'il ne soit inclus dans les résultats de la requête.

-   Plage de confiance : niveau de confiance auquel le type d'informations sensibles détecté correspond réellement (par exemple, 85 (85 %)).

Syntaxe :

-   SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”

Exemples :

-   SensitiveType:“Numéro de carte de crédit|5” (renvoie uniquement les documents qui contiennent exactement cinq numéros de carte de crédit)

-   SensitiveType:“Numéro de carte de crédit|\*|85..” (la plage de confiance est de 85 % ou supérieure)

Remarque : “SensitiveType” est sensible à la casse, mais le reste de la requête ne l’est pas.

Vous pouvez également utiliser des propriétés et des opérateurs pour illustrer la façon dont vous pouvez affiner vos requêtes. Pour plus d’informations et des exemples, reportez-vous à la rubrique relative à la [création d’une requête pour rechercher des données sensibles stockées sur des sites](https://support.office.com/fr-FR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).
