---
title: "Personnalisation ou création d’un type d’informations sensibles"
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
description: "Découvrez comment modifier ou créer des types d’informations sensibles Office 365 pour le RGPD."
ms.openlocfilehash: 58bfce19d75a66fe36d3e61ec0b05bcca6913b85
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a>Personnalisation ou création d’un type d’informations sensibles

Cet article fournit trois exemples qui décrivent comment modifier ou créer de nouveaux types d’informations sensibles Office 365 pour le RGPD.

-   Modification d’un type d’informations sensibles existant : Numéro de carte de crédit de l'U.E.

-   Création d’un type d’informations sensibles : adresse e-mail

-   Création d’un type d’informations sensibles avec un exemple de fichier XML : numéro de client Contoso

Voir également :

-   [Créer un type d’informations sensibles personnalisé](https://support.office.com/fr-FR/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   Rubrique relative à la [personnalisation d’un type d’informations sensibles intégré](https://support.office.com/fr-FR/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a>Modification d’un type d’informations sensibles pour améliorer la précision

Si vous utilisez la recherche de contenu pour rechercher des données personnelles à l’aide des types d’informations sensibles et que vous n’obtenez pas les résultats attendus ou que la requête renvoie un trop grand nombre de faux positifs, vous pouvez modifier le type d’informations sensibles en fonction de votre environnement.

La meilleure pratique lorsque vous créez ou personnalisez un type d’informations sensibles consiste à créer un type d’informations sensibles sur la base d’un type existant et à lui attribuer un nom et des identificateurs uniques. Par exemple, si vous souhaitez ajuster les paramètres du type d’informations sensibles « Numéro de carte de crédit de l'U.E. », vous pouvez nommer votre copie de cette règle « Carte de crédit de l’U.E. améliorée » pour la distinguer de l’originale.

Dans votre nouveau type d’informations sensibles, il suffit de modifier les valeurs à modifier pour améliorer sa précision. Ensuite, chargez votre nouveau type d’informations sensibles et créez une règle DLP (ou modifiez-en une existante) pour utiliser le nouveau type d’informations sensibles que vous venez d’ajouter. La modification de la précision de types d’informations sensibles peut nécessiter des essais et des erreurs. Par conséquent, conservez une copie du type d’origine pour l’utiliser éventuellement à l’avenir.

Pour personnaliser un type d’informations sensibles :

1.  Exportez le Package de règles Microsoft existant des types d’informations sensibles intégrés dans Office 365.

2.  Renommez ce fichier XML et ouvrez-le dans votre éditeur XML préféré.

3.  Isolez le type d’informations sensibles et supprimez tous les autres.

4.  Utilisez PowerShell pour générer deux nouveaux GUID pour le type d’informations sensibles que vous modifiez.

5.  Modifiez l’ID et d’autres éléments de base pour que le type d’informations sensibles soit unique (remplacez également les deux GUID par les deux nouveaux que vous avez générés).

6.  Affinez les exigences de correspondance pour améliorer la précision.

    1.  Modifications de la proximité : modifiez la proximité du motif de caractère pour développer ou réduire la fenêtre dans laquelle les mots-clés doivent être recherchés autour du type d’informations sensibles.

    2.  Modifications du mot-clé : ajoutez des mots clés à l’un des éléments \<Keyword\> afin de fournir à notre type d’informations sensibles un élément de preuve corroborante plus spécifique à rechercher pour signaler une correspondance sur cette règle. Vous pouvez aussi supprimer des mots-clés qui sont à l’origine de faux positifs.

    3.  Modifications de confiance : modifiez la confiance avec laquelle le type d’informations sensibles doit correspondre aux critères spécifiés dans sa définition avant qu’une correspondance soit signalée et déclarée.

7.  Chargez le nouveau type d'informations sensibles.

8.  Analysez de nouveau votre contenu pour identifier les informations sensibles. Reportez-vous à la rubrique [Demander manuellement l’analyse et la réindexation d’un site](https://support.office.com/fr-FR/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E).

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a>Exemple : modification du type d’informations sensibles « Numéro de carte de crédit de l'U.E. »

Lorsque vous améliorez la précision des règles DLP dans un système, vous devez effectuer des tests sur un ensemble de données exemple et éventuellement des réglages précis à l’aide de tests et modifications répétitifs. Cet exemple décrit des modifications du type d’informations sensibles « Numéro de carte de crédit de l'U.E. » pour améliorer sa précision.

Lorsque vous recherchez un numéro de carte de crédit de l'U.E., la définition de ce numéro est strictement définie comme 16 chiffres utilisant un modèle complexe et soumis à la validation d’une somme de contrôle. Nous ne pouvons pas modifier ce modèle en raison de la définition de chaîne de ce type d’informations sensibles. Toutefois, nous pouvons effectuer les ajustements suivants pour améliorer la précision avec laquelle la DLP Office 365 recherche ce type d’informations sensibles dans Office 365.

### <a name="proximity-modification"></a>Modification de la proximité

Nous allons réduire la fenêtre en modifiant la valeur patternProximity dans notre élément \<Entity\> de 300 à 150 caractères. Cela signifie que notre preuve corroborante, ou nos mots-clés doivent être plus proches de notre type d’informations sensibles pour signaler une correspondance sur cette règle.

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

### <a name="keyword-modifications"></a>Modifications des mots-clés

Certains mots-clés peuvent entraîner des faux positifs. Par conséquent, vous pouvez supprimer des mots-clés. Voici les mots-clés pour cet exemple :

\<Keyword id="Keyword\_card\_terms\_dict"\>

\<Group\>

\<Term\>corporate card\</Term\>

\<Term\>organization card\</Term\>

\<Term\>acct nbr\</Term\>

\<Term\>acct num\</Term\>

\<Term\>acct no\</Term\>

…

\</Group\>

\</Keyword\>

### <a name="confidence-modifications"></a>Modifications de la confiance

Si vous supprimez des mots-clés de la définition, vous voudrez généralement ajuster le niveau de confiance que vous avez concernant le fait que ce type d’informations sensibles a été trouvé en diminuant cette valeur. Le niveau par défaut pour le type de numéro de carte de crédit de l'U.E. est 85.

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

…

\</Pattern\>

\</Entity\>

## <a name="create-a-new-custom-sensitive-information-type"></a>Création d’un type d’informations sensibles personnalisé

Pour créer un type d’informations sensibles personnalisé, commencez par utiliser la recherche de contenu pour :

-   Optimiser une requête KQL

-   Voir les mots-clés les plus utiles

Utilisez ces résultats pour créer un type d’informations sensibles. Ensuite, optimisez le nouveau type d’informations sensibles pour votre environnement.

Remarque : de nombreux nouveaux types d’informations sensibles seront bientôt disponibles pour les données personnelles dans les pays de l’UE. Si vous avez besoin de créer de nouveaux types d’informations sensibles, commencez par cibler des données qui sont personnalisées pour votre environnement.

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a>Étape 1 : utilisez des requêtes KQL et des mots-clés pour rechercher des données supplémentaires dans votre environnement

Il se peut que vous deviez créer des requêtes afin d’obtenir des données personnelles qui sont soumises au RGPD. La recherche de contenu utilise le langage de requête de mot-clé (KQL) pour rechercher des données. Les données les plus sensibles ne peuvent pas être correctement détectées à l’aide de KQL seul sans types d’informations sensibles. Par conséquent, l’objectif consiste à tester et optimiser des chaînes KQL à l’aide de la recherche de contenu, puis à les utiliser pour créer et affiner de nouveaux types d’informations sensibles dans lesquels vous pouvez obtenir une précision encore plus grande.

Utilisez ces ressources pour formuler et optimiser des requêtes à l’aide de KQL :

-   [Référence de syntaxe de langage de requête de mot-clé (KQL) (DMC)](https://docs.microsoft.com/fr-FR/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [Exécuter une recherche de contenu dans le Centre de sécurité et de conformité Office 365](https://support.office.com/fr-FR/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

La recherche de contenu fournit une autre ressource pour vous aider à développer des requêtes KQL appropriées et des types d’informations sensibles : les mots-clés. Pourquoi utiliser la liste de mots-clés ? Vous pouvez obtenir des statistiques indiquant le nombre d’éléments qui correspondent à chaque mot-clé. Cela peut vous aider à identifier rapidement les mots-clés les plus (et les moins) efficaces. Pour plus d’informations sur les statistiques de recherche, reportez-vous à la rubrique relative à l’[affichage des statistiques de mots-clés pour les résultats de la recherche de contenu](https://support.office.com/fr-FR/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04).

Les mots-clés sur chaque ligne sont connectés par l’opérateur OR dans la requête de recherche qui est créée. Vous pouvez également utiliser une expression de mots-clés (entre parenthèses) dans une ligne.

Pour plus d’informations, reportez-vous à la rubrique [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](https://support.office.com/fr-FR/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3).

### <a name="exampleusing-content-search-to-identify-email-addresses"></a>Exemple : utilisation de la recherche de contenu pour identifier des adresses e-mail

Les adresses e-mail sont considérées comme des informations sensibles liées à des personnes. Voici un exemple simple qui décrit comment la recherche de contenu peut être utile.

Le langage KQL et les mots-clés ne peuvent pas être utilisés conjointement. Utilisez ces outils séparément pour affiner votre requête et identifier des mots-clés qui peuvent être utiles dans les types d’informations sensibles.

### <a name="kql-query"></a>Requête KQL

(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)

Remarques :

-   Vous pouvez utiliser NEAR et ONEAR pour les recherches de proximité.

-   Malheureusement, le langage KQL ne prend pas en charge les requêtes avec la classe Regex (ex : IdRef="Regex\_email\_address")

### <a name="keywords"></a>Mots clés

Entrez chaque mot-clé sur une ligne distincte. Exemple de mots-clés :

-   adresse électronique

-   messagerie

-   contact

-   expéditeur

-   destinataire

-   cc

-   bcc

Dans cet exemple, vous pouvez voir que les mots-clés ne sont pas nécessaires et produisent un grand nombre de résultats faux positifs.

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a>Étape 2 : créez un type d’informations sensibles personnalisé

Après avoir utilisé des requêtes KQL et des mots-clés pour identifier des informations sensibles, utilisez-les pour créer des types d’informations sensibles personnalisés. Dans de nombreux cas, vous aurez besoin de la sophistication des types d’informations sensibles pour atteindre le niveau de précision adéquat. Vous pouvez ensuite utiliser ces types d’informations sensibles personnalisés avec la recherche de contenu dans les stratégies DLP et d’autres outils, ainsi que dans d’autres requêtes KQL.

La meilleure pratique consiste à créer un type d’informations sensibles basé sur un type existant. Utilisez la même procédure décrite plus haut dans cet article.

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a>Exemple : création d’un type d’informations sensibles pour les adresses e-mail 

Nous allons poursuivre avec l’adresse e-mail car il s’agit d’un exemple simple. Le tableau suivant indique les modifications recommandées pour un nouveau type d’informations sensibles de messagerie.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étape</strong></th>
<th align="left"><strong>Modification </strong></th>
<th align="left"><strong>Exemple de syntaxe XML</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Définissez la propriété IdRef
<p>Dans l’élément &lt;Entity&gt;, modifiez l’élément &lt;IdMatch&gt; afin que sa propriété idRef est une valeur unique. Cette valeur pointera vers un élément qui définit notre expression régulière pour qu’elle recherche des adresses e-mail.</p></td>
<td align="left">IdRef=&quot;Regex_email_address&quot;</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><p>Attribut de proximité</p>
<p>Nous allons commencer par une valeur patternProximity dans notre élément &lt;Entity&gt; de 300.</p></td>
<td align="left">patternsProximity=&quot;300&quot;</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><p>Niveau de confiance</p>
<p>Définissez la propriété recommendedConfidence sur une valeur qui représentera la probabilité de trouver une correspondance précise. Vous devrez probablement effectuer des tests avec un ensemble de données représentatif pour obtenir un résultat précis. Comme paramètre initial, définissez cette valeur sur 75.</p></td>
<td align="left"><p>recommendedConfidence=&quot;75&quot;&gt;</p>
<p>Le code XML obtenu pour ces trois premiers éléments combinés ressemble à ceci :</p>
<p>&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</p>
<p>&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</p>
<p>&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</p>
<p>&lt;Any minMatches=&quot;1&quot;&gt;</p>
<p>&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</p>
<p>&lt;/Any&gt;</p>
<p>&lt;/Pattern&gt;</p>
<p>&lt;/Entity&gt;</p></td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left"><p>Élément Regex</p>
<p>Ajoutez un nouvel élément &lt;Regex&gt; immédiatement en dessous de l’élément &lt;Entity&gt; qui définit l’expression régulière utilisée pour identifier les adresses e-mail.</p></td>
<td align="left">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left"><p>Mots-clés</p>
<p>Ajoutez un nouvel élément &lt;Keyword&gt; sous l’élément &lt;Regex&gt; qui définit la liste des mots-clés liés à des adresses e-mail. Vérifiez que la valeur id pour l’élément &lt;Keyword&gt; correspond à la valeur &lt;Match idRef&gt; dans l’élément &lt;Entity&gt;&lt;Pattern&gt;. Vous pouvez continuer à ajouter vos propres mots-clés, si nécessaire.</p>
<p>Il n’est probablement pas nécessaire d’inclure des mots-clés dans un type d’informations sensibles de messagerie. Ceux-ci sont fournis en guise d’exemple.</p></td>
<td align="left"><p>&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</p>
<p>&lt;Group&gt;</p>
<p>&lt;Term&gt;email&lt;/Term&gt;</p>
<p>&lt;Term&gt;email address&lt;/Term&gt;</p>
<p>&lt;Term&gt;contact&lt;/Term&gt;</p>
<p>&lt;/Group&gt;</p>
<p>&lt;/Keyword&gt;</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left"><p>Élément LocalizedStrings</p>
<p>Dans l’élément &lt;LocalizedStrings&gt;&lt;Resource&gt;, vérifiez que vous avez un nom unique qui identifie votre type d’informations sensibles.</p></td>
<td align="left"><p>&lt;LocalizedStrings&gt;</p>
<p>&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</p>
<p>&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</p>
<p>&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</p>
<p>&lt;/Resource&gt;</p>
<p>&lt;/LocalizedStrings&gt;</p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a>Création d’un type d’informations sensibles avec un exemple de fichier XML et PowerShell : numéro de client Contoso

Contoso utilise un numéro de client Contoso (CCN) pour identifier chaque client dans sa base de données clients. Un CCN est constitué de la taxonomie suivante :

-   Deux chiffres qui représentent l’année de création de l’enregistrement. Contoso a été fondée en 2002 ; par conséquent, la valeur la plus précoce serait 02.

-   Trois chiffres qui représentent l’agence partenaire qui a créé l’enregistrement. La plage des valeurs possibles pour les agences se situe entre 000 et 999.

-   Un caractère alpha qui représente la ligne de l’entreprise. Les valeurs possibles sont les caractères de a à z et doivent respecter la casse.

-   Un numéro de série à quatre chiffres. La plage des valeurs de numéro de série possible est comprise entre 0000 et 9999.

Exemples de CCN :

> 15080P9562
>
> 14040O1119
>
> 15020J8317
>
> 14050E2330
>
> 16050E2166
>
> 17040O1118

Contoso fait toujours référence aux clients en utilisant un CCN dans la correspondance interne, la correspondance externe, les documents, etc. Il souhaite créer un type d’informations sensibles personnalisé pour détecter l’utilisation d’un CCN dans Office 365 pour appliquer la protection à l’utilisation de ce formulaire de données personnelles.

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a>Création d’un type d’informations sensibles pour un numéro de client Contoso

<table>
<thead>
<tr class="header">
<th align="left"><strong>Étape</strong></th>
<th align="left"><strong>Action </strong></th>
<th align="left"><strong>Résultat</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contoso utilise PowerShell et la recherche de contenu pour rechercher des documents qui correspondent à un exemple de jeu de CCN.</td>
<td align="left">

<p>#Se connecter au Centre de sécurité et de conformité Office 365</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#Créer et lancer une recherche pour un exemple de données</p>
<p>$searchName = &quot;Sample Customer Information Search&quot;</p>
<p>$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</p>
<p>New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</p>
<p>Start-ComplianceSearch -Identity $searchName</p>
</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Contoso analyse les résultats. Chaque fois que le CCN a été utilisé, une date au format européen mis en forme a été utilisée et l’un de ces mots-clés a été utilisé également dans une proximité de 300 caractères.</td>
<td align="left">customer number, customer no, customer #, customer#, Contoso customer</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Contoso a développé le modèle d’expression régulière (RegEx) suivant afin d’identifier son CCN.</td>
<td align="left">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">Contoso a développé le modèle d’expression régulière (RegEx) suivant pour identifier les dates européennes aux formats utilisés par ses différentes filiales.</td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left">Contoso utilise PowerShell pour générer trois GUID uniques.</td>
<td align="left"><p>#Générer un GUID unique pour RulePack Id, Publisher Id et Entity Id</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left">Contoso définit les paramètres suivants pour sa règle de type d’élément sensible.</td>
<td align="left"><p>Nom : Numéro de client Contoso (CCN)</p>
<p>Description : Numéro de client Contoso (CCN) qui recherche des mots-clés supplémentaires et une date au format européen</p></td>
</tr>
<tr class="odd">
<td align="left">7</td>
<td align="left">Contoso crée un fichier XML pour un nouveau type d’informations sensibles pour détecter un numéro de client Contoso (CCN) et l’enregistre dans un système de fichiers local C:\Scripts\ContosoCCN.xml avec codage UTF-8.</td>
<td align="left">Reportez-vous au fichier XML sous ce tableau.</td>
</tr>
<tr class="even">
<td align="left">8</td>
<td align="left">Contoso crée le type d’informations sensibles personnalisé avec le PowerShell suivant.</td>
<td align="left"><p>#Se connecter au Centre de sécurité et de conformité Office 365</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#Créer un type d’informations sensibles</p>
<p>New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a>Exemple de fichier XML pour le nouveau type d’informations sensibles (étape 7)
```xml
\<?xml version="1.0" encoding="utf-8"?\>

\<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"\>

\<RulePack id="130ae63b-a91e-4a12-9e02-a90e36a83d7f"\>

\<Version major="1" minor="0" build="0" revision="0" /\>

\<Publisher id="47148982-defd-42a1-890a-7b9472099f1f" /\>

\<Details defaultLangCode="en"\>

\<LocalizedDetails langcode="en"\>

\<PublisherName\>Contoso Ltd.\</PublisherName\>

\<Name\>Contoso Rule Package\</Name\>

\<Description\>Defines Contoso's custom set of classification rules\</Description\>

\</LocalizedDetails\>

\</Details\>

\</RulePack\>

\<Rules\>

\<!-- Contoso Customer Number (CCN) --\>

\<Entity id="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b" patternsProximity="300" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

\<IdMatch idRef="Regex\_contoso\_ccn" /\>

\<Match idRef="Keyword\_contoso\_ccn" /\>

\<Match idRef="Regex\_eu\_date" /\>

\</Pattern\>

\</Entity\>

\<Regex id="Regex\_contoso\_ccn"\>[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}\</Regex\>

\<Keyword id="Keyword\_contoso\_ccn"\>

\<Group matchStyle="word"\>

\<Term caseSensitive="false"\>customer number\</Term\>

\<Term caseSensitive="false"\>customer no\</Term\>

\<Term caseSensitive="false"\>customer \#\</Term\>

\<Term caseSensitive="false"\>customer\#\</Term\>

\<Term caseSensitive="false"\>Contoso customer\</Term\>

\</Group\>

\</Keyword\>

\<Regex id="Regex\_eu\_date"\> (0?[1-9]|[12][0-9]|3[0-1])[\\/-](0?[1-9]|1[0-2]|j\\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?‌ |feb(ruary|ruari|rero|braio|ruar|br)?|f\\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\\x00e4rz|maart‌|apr(ile|il)?|abr(il)?|avril‌ |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?‌ |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\\x00e9c(embre)?)[ \\/-](19|20)?[0-9]{2}\</Regex\>

\<LocalizedStrings\>

\<Resource idRef="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b"\>

\<Name default="true" langcode="en-us"\>Contoso Customer Number (CCN)\</Name\>

\<Description default="true" langcode="en-us"\>Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date\</Description\>

\</Resource\>

\</LocalizedStrings\>

\</Rules\>

\</RulePackage\>
```
