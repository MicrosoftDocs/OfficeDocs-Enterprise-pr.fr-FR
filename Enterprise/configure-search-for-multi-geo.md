---
title: Configurer la recherche de OneDrive pour l’entreprise Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur la façon de configurer la recherche dans un environnement multi-geo.
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>Configurer la recherche de OneDrive pour l’entreprise Multi-Geo

Dans un environnement Multi-Geo SharePoint Online (OFS), une organisation peut avoir un locataire d’Office 365, mais stocker leur contenu SharePoint dans plusieurs régions géographiques - un emplacement central et un ou plusieurs par satellite géo emplacements.

Chaque emplacement géographique a son propre index de recherche et le centre de recherche. Lorsqu’un utilisateur recherche, la requête est serveur pour tous les index, et les résultats renvoyés sont fusionnées.

Par exemple, un utilisateur dans un emplacement géographique peut rechercher du contenu stocké dans un autre emplacement géographique ou de contenu sur un site SharePoint qui est limité à un emplacement géographique différent. Si l’utilisateur a accès à ce contenu, recherche affiche le résultat.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Qui recherche les clients dans un environnement Multi-Geo ?

Ces clients peuvent renvoyer des résultats à partir de tous les emplacements de la zone géographique :

-   OneDrive for Business

-   Delve

-   La page d’accueil SharePoint

-   Le centre de recherche

-   Applications de recherche personnalisées qui utilisent l’API de recherche de SharePoint

### <a name="onedrive-for-business"></a>OneDrive for Business

Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans OneDrive obtenir des résultats de tous les emplacements de la zone géographique.

### <a name="delve"></a>Delve

Dès que l’environnement Multi-Geo a été configuré, les utilisateurs qui recherche dans Delve obtenir des résultats de tous les emplacements de la zone géographique.

Le flux Delve et la Fiche profil uniquement affichent les aperçus des fichiers qui sont stockés dans l’emplacement **central** . Pour les fichiers qui sont stockés dans des emplacements satellite géo, l’icône du type de fichier est affiché.

### <a name="the-sharepoint-home-page"></a>La page d’accueil SharePoint

Dès que l’environnement Multi-Geo a été configuré, les utilisateurs verront news, sites récents et suivis à partir de plusieurs emplacements geo sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche sur la page d’accueil SharePoint, ils obtiendrez des résultats fusionnés à partir de plusieurs emplacements de la zone géographique.

### <a name="the-search-center"></a>Le centre de recherche

Après le Multi-Geo environnement a été configuré, chaque centre de recherche continue d’afficher uniquement les résultats à partir de leur propre emplacement géographique. Administrateurs doivent [Modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir des résultats à partir de tous les emplacements de la zone géographique. Par la suite, les utilisateurs qui recherche dans le centre de recherche affiche des résultats de tous les emplacements de la zone géographique.

### <a name="custom-search-applications"></a>Applications de recherche personnalisées

Comme d’habitude, les applications de recherche personnalisées interagissent avec les index de recherche à l’aide de l’API de reste de recherche SharePoint existant. Pour obtenir des résultats à partir d’emplacements de geo tout ou partie, l’application doit [appeler l’API et inclure les nouveaux paramètres de requête Multi-Geo](#_Get_custom_search) dans la demande. Cela déclenche un ventilateur de la requête à tous les emplacements de la zone géographique.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Quelle est la différence sur la recherche dans un environnement Multi-Geo ?

Vous pouvez être familiarisé avec certaines fonctions de recherche fonctionnent différemment dans un environnement Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Fonctionnalité</strong></th>
<th align="left"><strong>Comment cela fonctionne-t-il</strong></th>
<th align="left"><strong>Solution de contournement</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Résultats de la promotion</td>
<td align="left">Vous pouvez créer des règles de requête avec les résultats promus à différents niveaux : pour le locataire ensemble, pour une collection de sites ou pour un site. Dans un environnement Multi-Geo, définir des résultats promues au niveau des <strong>clients</strong> si vous souhaitez promouvoir les résultats pour les centres de recherche dans <strong>tous les</strong> emplacements de la zone géographique. Si vous <strong>seulement</strong> souhaitez promouvoir les résultats dans le centre de recherche qui se trouve dans l’emplacement géographique de la collection de sites ou un site, définir les résultats au niveau du <strong>site</strong> ou de <strong>collection de sites</strong> .</td>
<td align="left">Si vous n’avez pas besoin des résultats différents promues par emplacement géographique, par exemple des règles différentes pour les déplacements, nous vous recommandons de définir promu les résultats au niveau du client.</td>
</tr>
<tr class="even">
<td align="left">Raffineurs de recherche</td>
<td align="left">La recherche renvoie les raffineurs de tous les emplacements géographique d’un client et puis les agrège. L’agrégation est un maximum d’efforts, ce qui signifie que le nombre de raffineur ne peut pas précis à 100 %. La plupart des scénarios piloté par recherche, cette précision est suffisante.</td>
<td align="left">Pour les applications pilotées par recherche dépendant de l’exhaustivité de raffineur, interroger chaque emplacement géographique indépendamment sans utiliser Multi-Geo Fanout.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Recherche de multi-Geo ne prend pas en charge la dynamique la création de compartiments pour les raffineurs numériques.</td>
<td align="left">Utilisez le <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre de « Discretize »</a> pour les raffineurs numériques.</td>
</tr>
<tr class="even">
<td align="left">ID de document</td>
<td align="left">Si vous développez une application pilotée par recherche qui dépend des numéros de document, notez que les numéros de document dans un environnement Multi-Geo ne sont pas uniques dans tous les magasins de géo, ils sont uniques par les emplacement géographique.</td>
<td align="left">Nous avons ajouté une colonne qui identifie l’emplacement géographique. Utilisez cette colonne pour atteindre l’unicité. Cette colonne est nommée « GeoLocationSource ».</td>
</tr>
<tr class="odd">
<td align="left">Nombre de résultats</td>
<td align="left">La page de résultats affiche les résultats combinés à partir de l’emplacement géographique, mais il n’est pas possible de la page au-delà de 500 résultats.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Ce qui n’est pas pris en charge pour les recherches dans un environnement Multi-Geo ?

Certaines des fonctionnalités de recherche, vous pouvez être familiarisé avec, ne sont pas pris en charge dans un environnement Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Fonctionnalité de recherche</strong></th>
<th align="left"><strong>Remarque</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Authentification d’application uniquement</td>
<td align="left">App uniquement l’authentification (accès privilégié à partir des services) n’est pas pris en charge dans la recherche de Multi-Geo.</td>
</tr>
<tr class="even">
<td align="left">Utilisateurs invités</td>
<td align="left">Les utilisateurs invités obtiennent uniquement des résultats à partir de l’emplacement géographique qui ils recherchent à partir de.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Fonctionnement de recherche de fait dans un environnement Multi-Geo ?

**Tous les** clients recherche utilisent les API de reste de recherche SharePoint existante pour interagir avec les index de recherche.
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. Un client recherche appelle le point de terminaison de recherche reste avec la propriété de requête EnableMultiGeoSearch = true.
2. La requête est envoyée à tous les emplacements de geo dans le locataire.
3. Résultats de la recherche à partir de chaque emplacement géographique sont fusionnées et classés.
4. Le client obtient des résultats de la recherche unifiée.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notez que nous ne pas fusionner les résultats de recherche jusqu'à ce que nous avons reçu les résultats à partir de tous les emplacements de la zone géographique. Cela signifie que les recherches Multi-Geo ont latence supplémentaire par rapport aux recherches dans un environnement avec geo qu’un seul emplacement.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Obtenir un centre de recherche pour afficher les résultats de tous les emplacements de la zone géographique

Chaque centre de recherche possède plusieurs secteurs, et vous devez définir individuellement chaque vertical.

1.  Assurez-vous que vous effectuez ces étapes avec un compte qui dispose des autorisations nécessaires pour modifier la page de résultats de la recherche et le composant WebPart résultats de recherche.

2.  Accédez à la page de résultats de la recherche (voir la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de recherche des pages de résultats)

3.  Sélectionnez vertical pour définir, cliquez sur icône engrenage de **paramètres** dans l’angle supérieur droit, puis cliquez sur **Modifier la Page**. La page de résultats de recherche s’ouvre en mode édition.

     ![](media/configure-search-for-multi-geo_image2.png)
1.  Dans le composant WebPart résultats de recherche, déplacez le pointeur vers le haut, à droite du composant WebPart, cliquez sur la flèche et puis cliquez sur **Modifier des composants WebPart** dans le menu. Le volet d’outils composant WebPart résultats de la recherche s’affiche sous le ruban dans la partie supérieure droite de la page.![](media/configure-search-for-multi-geo_image3.png)

1.  Dans le volet d’outils composant WebPart, dans la section **paramètres** , sous **paramètres de contrôle des résultats**, sélectionnez **Multi-Geo afficher les résultats** pour obtenir le composant WebPart résultats de recherche pour afficher les résultats de tous les emplacements de la zone géographique.

2.  Cliquez sur **OK** pour enregistrer vos modifications et fermer le volet d’outils composant WebPart.

3.  Vérifiez vos modifications dans le composant WebPart résultats de la recherche en cliquant sur **Archiver** dans l’onglet de Page du menu principal.

4.  Publier les modifications en utilisant le lien fourni dans la note en haut de la page.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Obtenir les applications de recherche personnalisées pour afficher les résultats de tout ou partie des emplacements geo

Applications de recherche personnalisées obtenir des résultats à partir d’emplacements de geo tous ou certains, en spécifiant des paramètres de la requête avec la demande de l’API REST de recherche SharePoint. Selon les paramètres de requête, la requête est serveur à tous les emplacements de la zone géographique ou à certains emplacements de la zone géographique. Par exemple, si vous avez besoin uniquement d’interroger un sous-ensemble des emplacements geo pour rechercher des informations pertinentes, vous pouvez contrôler le facteur pyramidal de sortie uniquement ces. Si la demande réussit, l’API REST de recherche SharePoint renvoie des données de réponse.

### <a name="query-parameters"></a>Paramètres de la requête

EnableMultiGeoSearch - il s’agit d’une valeur de type Boolean qui spécifie si la requête doit être serveur pour les index des autres emplacements géographique du locataire Multi-Geo. Affectez-lui la valeur **true** pour déployer la requête ; **false** pour ne ventilateur pas la requête. La valeur par défaut est **false**. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique. Si vous utilisez le paramètre dans un environnement qui n’est pas de Multi-Geo, le paramètre est ignoré.

TypeClient - il s’agit d’une chaîne. Entrez un nom de client unique pour chaque application de recherche. Si vous n’incluez pas ce paramètre, la requête n’est **pas** serveur vers d’autres emplacements de la zone géographique.

MultiGeoSearchConfiguration - il s’agit d’une liste facultative de la zone géographique des emplacements dans le Multi-Geo client pour déployer la requête à lorsque **EnableMultiGeoSearch** a la **valeur true**. Si vous ne spécifiez ce paramètre, ou laissez le champ vide, la requête est serveur à tous les emplacements de la zone géographique. Pour chaque emplacement géographique, entrez les éléments suivants, au format JSON :

<table>
<thead>
<tr class="header">
<th align="left">Élément</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">L’emplacement géographique, par exemple NAM.</td>
</tr>
<tr class="even">
<td align="left">Point de terminaison</td>
<td align="left">Le point de terminaison pour se connecter à, par exemple.https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">Le GUID de la source de résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Si vous omettez de DataLocation ou point de terminaison, ou si une DataLocation est en double, la demande échoue. [Vous pouvez obtenir des informations sur le point de terminaison des emplacements de géographique d’un client à l’aide de Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Données de réponse

MultiGeoSearchStatus – il s’agit d’une propriété qui retourne de l’API de recherche de SharePoint en réponse à une demande. La valeur de la propriété est une chaîne et renvoie les informations suivantes sur les résultats qui renvoie de l’API de recherche de SharePoint :

<table>
<thead>
<tr class="header">
<th align="left">Valeur</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Complet</td>
<td align="left">Complet à partir de <strong>tous les</strong> résultats de l’emplacement géographique.</td>
</tr>
<tr class="even">
<td align="left">Partielle</td>
<td align="left">Résultats partiels à partir d’un ou plusieurs emplacements de la zone géographique. Les résultats sont incomplets en raison d’une erreur temporaire.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Exécuter une requête via le service REST

Avec une demande GET, vous spécifiez les paramètres de requête dans l’URL. Avec une demande POST, vous transmettez les paramètres de requête dans le corps dans le format de Notation JSON (JavaScript Object).

#### <a name="request-headers"></a>En-têtes de demande

<table>
<thead>
<tr class="header">
<th align="left">Nom</th>
<th align="left">Valeur</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">application/json ; odata = verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Exemple de demande GET qui est serveur à **tous les** emplacements de la zone géographique

https:// \<clients\>/\_api/recherche/query?querytext = « sharepoint » & propriétés = 'EnableMultiGeoSearch:true' & TypeClient =' Mes\_client\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Exemple de demande GET pouvoir déployer vers **certains** emplacements geo

https:// <tenant>/_api/search/query?querytext = 'site' & TypeClient = 'my_client_id' & propriétés ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration : [{DataLocation\:« NAM »\,point de terminaison\:« https\: contosoNAM.sharepoint.com »\,SourceId\:« B81EAB55-3140-4312-B0F4-9459D1B4FFEE »}\,{DataLocation\:« Peut »\,point de terminaison\:« https\://contosoCAN.sharepoint-df.com »}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Exemple de requête POST qui est serveur à **tous les** emplacements de la zone géographique

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Exemple de requête POST qui est serveur à **certains** emplacements geo


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a>Requête à l’aide de CSOM

Voici un exemple de requête CSOM qui est serveur à **tous les** emplacements de la zone géographique :

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

