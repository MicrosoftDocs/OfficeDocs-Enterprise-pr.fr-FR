---
title: Service web d’URL et d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: L’adresse IP Office 365 et le service Web URL vous aident à mieux identifier et différencier le trafic réseau d’Office 365, ce qui vous permet d’évaluer, de configurer et de rester à jour avec les modifications.
ms.openlocfilehash: 7a1d882b6bc5e34e3d59cf4bade30a58a1c76d6f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843597"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Service web d’URL et d’adresses IP Office 365

L’adresse IP Office 365 et le service Web URL vous aident à mieux identifier et différencier le trafic réseau d’Office 365, ce qui vous permet d’évaluer, de configurer et de rester à jour avec les modifications. Ce service Web basé sur REST remplace les anciens fichiers XML téléchargés, qui ont été supprimés le 2 octobre 2018.

En tant que fournisseur de périphériques de périmètre réseau ou client, vous pouvez créer le service Web pour les entrées d’adresse IP et de nom de domaine complet Office 365. Vous pouvez accéder aux données directement dans un navigateur Web à l’aide des URL suivantes :

- Pour obtenir la dernière version des URL et plages d’adresses IP Office 365, utilisez [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Pour les données sur la page des URL et plages d’adresses IP Office 365 pour les pare-feux et les serveurs proxy, utilisez [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Pour obtenir les dernières modifications depuis juillet 2018, date de première mise à disposition du service web, utilisez [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

En tant que client, vous pouvez utiliser ce service web pour :

- mettre à jour vos scripts PowerShell et obtenir des données de point de terminaison Office 365 et modifier la mise en forme de vos périphériques réseau ;
- utiliser ces informations pour mettre à jour des fichiers PAC déployés sur des ordinateurs clients.

En tant que fournisseur de périphérique de périmètre réseau, vous pouvez utiliser ce service web pour :

- créer et tester le logiciel du périphérique pour télécharger la liste pour une configuration automatisée ;
- rechercher la version actuelle ;
- obtenir les modifications actuelles.

> [!NOTE]
> Si vous utilisez Azure ExpressRoute pour vous connecter à Office 365, consultez [Azure ExpressRoute pour Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) pour vous familiariser avec les services Office 365 pris en charge sur Azure ExpressRoute. Consultez l’article [ URLs and plages d’adresse IP Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) pour identifier les requêtes réseau des applications Office 365 qui nécessitent une connectivité Internet. Cette opération permet de mieux configurer vos périphériques de sécurité de périmètre.

Pour plus d’informations, voir :

- [Annonce du billet de blog dans le Forum de la communauté technique Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Forum de la communauté technique Office 365 pour les questions sur l’utilisation des services web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Paramètres communs

Ces paramètres sont communs à toutes les méthodes de service web :

- **format = < JSON | CSV >** : par défaut, le format de données renvoyé est JSON. Utilisez ce paramètre facultatif pour renvoyer les données au format de valeurs séparées par des virgules (CSV).
- **ClientRequestId =\<guid >**: un GUID requis que vous générez pour association client. Générer un GUID unique pour chaque ordinateur appelant le service Web (les scripts inclus sur cette page génèrent un GUID pour vous). N’utilisez pas les GUID illustrés dans les exemples suivants, car ils peuvent être bloqués par le service web à l’avenir. Format GUID est _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, où x représente un nombre hexadécimal.

  Pour générer un GUID, vous pouvez utiliser la commande PowerShell [New-GUID](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) ou utiliser un service en ligne tel que [générateur de GUID en ligne](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Méthode web version 

Microsoft met à jour les entrées d’adresse IP et de nom de domaine complet Office 365 à la fin de chaque mois. Les mises à jour hors bande sont parfois publiées en raison de problèmes de support, de mises à jour de sécurité ou d’autres exigences opérationnelles.

Un numéro de version est attribué aux données pour chaque instance publiée et la méthode Web version vous permet de rechercher la dernière version de chaque instance du service Office 365. Nous vous recommandons de ne pas vérifier la version plus d’une fois par heure.

Les paramètres pour la méthode web de version sont :

- **AllVersions = < true | Faux >** : par défaut, la version renvoyée est la dernière version. Inclure ce paramètre facultatif pour demander toutes les versions publiées depuis que le service web a été publié.
- **Format = < JSON | CSV | RSS >** : outre les formats JSON et CSV, la méthode web version prend également en charge RSS. Vous pouvez utiliser ce paramètre facultatif conjointement avec le paramètre _AllVersions = true_ pour demander un flux RSS qui peut être utilisé avec Outlook ou d’autres lecteurs de RSS.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** : ce paramètre facultatif spécifie l’instance vers laquelle renvoyer la version. Si cet argument est omis, toutes les instances sont renvoyées. Les instances valides sont : Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

La méthode Web version n’est pas limitée au taux et ne renvoie jamais de codes de réponse HTTP 429. La réponse à la méthode Web version inclut un en-tête de contrôle du cache qui recommande la mise en cache des données pendant 1 heure. Le résultat de la méthode web de version peut être un enregistrement unique ou un tableau d’enregistrements. Les éléments de chaque enregistrement sont :

- instance : nom court de l’instance de service Office 365.
- dernière : dernière version pour les points de terminaison de l’instance spécifiée.
- versions : liste de toutes les versions précédentes pour l’instance spécifiée. Cet élément est inclus uniquement si le paramètre _AllVersions_ est true.

### <a name="examples"></a>Exemples :

Exemple 1 d’URI de requête : [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URI renvoie la dernière version de chaque instance du service Office 365. Exemple de résultat :

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> Le GUID pour le paramètre ClientRequestID dans ces URI n’est qu’un exemple. Pour essayer les URI de service web, générez votre propre GUID. Les GUID illustrés dans ces exemples pourront être bloqués par le service web à l’avenir.

Exemple 2 d’URI de requête : [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URI renvoie la dernière version de chaque instance du service Office 365 spécifiée. Exemple de résultat :

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Exemple 3 d’URI de requête : [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URI affiche le résultat au format CSV. Exemple de résultat :

```csv
instance,latest
Worldwide,2018063000
```

Exemple 4 d’URI de requête : [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URI affiche toutes les versions antérieures publiées pour l’instance du service Office 365 dans le monde. Exemple de résultat :

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Exemple 5 d’URI de flux RSS : [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Cet URI affiche un flux RSS des versions publiées qui incluent des liens vers la liste des modifications apportées à chaque version. Exemple de résultat :

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Points de terminaison méthode web

Les points de terminaison de la méthode web renvoient tous les enregistrements pour les plages d’adresses IP et URL qui composent le service Office 365. Les données les plus récentes des points de terminaison de la méthode Web doivent toujours être utilisées pour la configuration des périphériques réseau. Microsoft fournit une notification préalable 30 jours avant la publication de nouveaux ajouts afin de vous laisser le temps de mettre à jour les listes de contrôle d’accès et les listes de contournement du serveur proxy. Nous vous recommandons de rappeler uniquement les points de terminaison méthode web uniquement lorsque la méthode web version indique qu’une nouvelle version des données est disponible.

Les paramètres pour les points de terminaison de la méthode web sont :

- **ServiceAreas=<Common | Exchange | SharePoint | Skype >** : une liste de zones de service séparée par des virgules. Éléments valides sont _Common_, _Exchange_, _SharePoint_, et _Skype_. Étant donné que les éléments_Common_ de zone de service sont une condition préalable pour toutes les autres zones de service, le service web les inclura toujours. Si vous n’incluez pas ce paramètre, toutes les zones de service sont renvoyées.
- **TenantName=<tenant_name>** : nom de votre client Office 365. Le service web prend votre nom fourni et l’insère en plusieurs parties d’URL qui incluent le nom de client. Si vous ne fournissez pas de nom de client, ces composants d’URL ont le caractère générique (\*).
- **NoIPv6=<true | false>**  : définissez cette option sur _true_ pour exclure les adresses IPv6 du résultat, par exemple, si vous n’utilisez pas IPv6 dans votre réseau.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** : ce paramètre facultatif spécifie l’instance vers laquelle renvoyer les points de terminaison. Les instances valides sont : _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.

Si vous appelez la méthode web points de terminaison un trop grand nombre de fois à partir de la même adresse IP du client, vous pouvez recevoir le code de réponse HTTP _429 (Trop de requêtes)_. Si vous recevez ce code de réponse, patientez 1 heure avant de renouveler votre demande, ou générez un nouveau GUID pour la demande. Nous recommandons de ne rappeler la méthode web points de terminaison uniquement lorsque la méthode web indique qu’une nouvelle version est disponible.

Le résultat de la méthode web de points de terminaison est un tableau d’enregistrements avec chaque enregistrement représentant un ensemble de points de terminaison spécifique. Les éléments pour chaque enregistrement sont :

- id : l’ID non modifiable de l’ensemble de points de terminaison.
- serviceArea : la zone de service dont il fait partie : _Common_, _Exchange_, _SharePoint_, ou _Skype_.
- URL : URL pour l’entité de point de terminaison. Tableau JSON d’enregistrements DNS. Omis si vide.
- tcpPorts — ports TCP pour l’entité de point de terminaison. Tous les éléments port sont mis en forme en tant que liste de ports séparés par des virgules ou plages de ports séparés par un tiret (-). Les ports s’appliquent à toutes les adresses IP et toutes les URL du point de terminaison défini pour une catégorie donnée. Omis si vide.
- udpPorts : ports UDP pour les plages d’adresses IP dans cet ensemble de points de terminaison.  Omis si vide.
- ips : plages d’adresses IP associées à cet ensemble de points de terminaison tel qu’associées aux ports TCP ou UDP répertoriés. Un tableau JSON des plages d’adresses IP.  Omis si vide.
- Catégorie : catégorie de connectivité pour l’entité de point de terminaison. Les valeurs valides sont : _Optimiser_, _Autoriser_, and _Défaut_. Si vous recherchez la sortie de la méthode Web de points de terminaison pour la catégorie d’une adresse IP ou d’une URL spécifique, il est possible que votre requête renvoie plusieurs catégories. Dans ce cas, suivez la recommandation pour la catégorie de priorité la plus élevée. Par exemple, si le point de terminaison apparaît dans les deux options _optimiser_ et _autoriser_, vous devez respecter les conditions requises pour _optimiser_. Obligatoire.
- expressRoute : _True_ si cet ensemble de points de terminaison est routé sur ExpressRoute, _False_ si ce n’est pas le cas.
- required : _True_ si cet ensemble de points de terminaison est obligatoire pour disposer d’une connectivité et prendre en charge Office 365.  _False_ si cet ensemble de points de terminaison est facultatif.
- notes : pour les points de terminaison facultatifs, ce texte décrit les fonctionnalités Office 365 qui seront indisponibles si les adresses IP ou les URL dans cet ensemble de points de terminaison ne sont pas accessibles sur la couche réseau. Omis si vide.

### <a name="examples"></a>Exemples :

Exemple 1 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URL a obtenu tous les points de terminaison pour l’instance Worldwide d’Office 365 pour toutes les charges de travail.  Exemple de résultat montrant un extrait du résultat :

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Notez que le résultat complet de la requête dans cet exemple contient d’autres jeux de points de terminaison.

Exemple 2 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet exemple obtient des points de terminaison pour l’instance Worldwide d’Office 365 pour Exchange Online et les dépendances uniquement.

Le résultat pour l’exemple 2 ressemble à l’exemple 1 sauf que les résultats n’incluent pas les points de terminaison pour SharePoint Online ou Skype Entreprise Online.

## <a name="changes-web-method"></a>Méthode web de modifications

La méthode Web modifications renvoie les mises à jour les plus récentes qui ont été publiées, généralement les modifications apportées au mois précédent en plages d’adresses IP et URL.

Les modifications les plus critiques apportées aux données de points de terminaison sont les nouvelles URL et les adresses IP. L’échec de l’ajout d’une adresse IP à une liste de contrôle d’accès de pare-feu ou d’une URL à une liste de contournement de serveur proxy peut provoquer une panne pour les utilisateurs d’Office 365 derrière ce périphérique réseau. Nonobstant les impératifs opérationnels, les nouveaux points de terminaison sont publiés sur le service Web 30 jours avant la date à laquelle les points de terminaison sont configurés pour vous laisser le temps de mettre à jour les listes de contrôle d’accès et les listes de contournement du serveur proxy.

Le paramètre requis pour la méthode web changes est le suivant :

- **Version=\<YYYYMMDDNN>** - Paramètre d’itinéraire d’URL requis. Cette valeur est la version que vous avez implémentée actuellement. Le service web renvoie les modifications depuis cette version. Le format est _JJNN/MM/AAAA_, où _NN_ est un nombre entier incrémenté si plusieurs versions doivent être publiées un même jour,  _00_ représentant la première mise à jour à la date concernée. Le service web exige que le paramètre _version_ contienne exactement 10 chiffres.

La méthode web changes est limitée par le débit de la même manière que la méthode web endpoints. Si vous recevez ce code de réponse 429, patientez 1 heure avant de renouveler votre demande, ou générez un nouveau GUID pour la demande.

Le résultat de la méthode web modifications est un tableau d’enregistrements avec chaque enregistrement représentant une modification d’une version de points de terminaison spécifique. Les éléments pour chaque enregistrement sont :

- ID : ID non modifiable de l’enregistrement de la modification.
- endpointSetId : ID de l’enregistrement du point de terminaison qui est modifié.
- disposition : décrit les modifications apportées à l’enregistrement de point de terminaison. Les valeurs sont _modifier_, _ajouter_, or _supprimer_.
- impact : toutes les modifications ne sont pas aussi importantes pour tous les environnements. Cet élément décrit l’impact attendu sur l’environnement du périmètre d’un réseau d’entreprise en raison de cette modification. Cet élément est inclus uniquement dans les enregistrements de modification de la version **2018112800** et les versions ultérieures. Les options d’impact sont les suivantes : — AddedIp – une adresse IP a été ajoutée à Office 365 et sera bientôt disponible sur le service. Il s’agit d’un changement que vous devez apporter à un pare-feu ou à un autre périphérique de périmètre réseau couche 3. Si vous ne l’ajoutez pas avant que nous commencions à l’utiliser, vous pourriez subir une panne.
  – AddedUrl – Une URL a été ajoutée à Office 365 et sera bientôt disponible sur le service. Il s’agit d’un changement que vous devez apporter à un serveur proxy ou à un périphérique réseau d’analyse d’URL. Si vous ne l’ajoutez pas avant que nous commencions à l’utiliser, vous pourriez subir une panne.
  — AddedIpAndUrl — une adresse IP et une URL ont été ajoutées. Il s’agit d’un changement que vous devez apporter à un périphérique de périmètre réseau couche 3, un serveur proxy ou à un périphérique réseau d’analyse d’URL. Si vous ne l’ajoutez pas avant que nous commencions à l’utiliser, vous pourriez subir une panne.
  — RemovedIpOrUrl – au moins une adresse IP ou une URL a été supprimée d’Office 365. Supprimez les points de terminaison réseau de vos périphériques de périmètre, mais il n’y a aucune échéance pour le faire.
  — ChangedIsExpressRoute – l’attribut support ExpressRoute a été modifié. Si vous utilisez ExpressRoute, vous devrez peut-être agir en fonction de votre configuration.
  —MovedIpOrUrl — nous avons déplacé une adresse IP ou une URL entre cet ensemble de points de terminaison et un autre emplacement.  En général, aucune action n’est requise.
  — RemovedDuplicateIpOrUrl – nous avons supprimé une adresse IP ou une URL en double, mais celle-ci est toujours publiée pour Office 365.  En général, aucune action n’est requise.
  — OtherNonPriorityChanges – nous avons modifié un élément moins critique que toutes les autres options, comme un champ de note.
- version : version de l’entité de point de terminaison publiée dans laquelle la modification a été introduite. Le format des numéros de version est _JJNN/MM/AAAA_, où _NN_ est un nombre entier incrémenté si plusieurs versions doivent être publiées un même jour.
- previous : sous-structure détaillant les valeurs précédentes des éléments modifiés sur le point de terminaison défini. Elle ne sera pas incluse pour les nouveaux ensembles de points de terminaison ajoutés. Inclut _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ et _notes_.
- current : une sous-structure détaillant les valeurs mises à jour des éléments de modifications dans l’ensemble des points de terminaison. Inclut _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ et _notes_.
- add : sous-structure détaillant les éléments à ajouter aux collections d’ensembles de points de terminaison.  Omis s’il n’y a aucun ajout.
  — effectiveDate — définit les données lorsque les ajouts seront disponibles dans le service.
  — ips — éléments à ajouter au tableau d’adresses _ips_.
  — urls — éléments à ajouter au tableau_urls_.
- remove : sous-structure détaillant les éléments à supprimer de l’ensemble de points de terminaison. Omis si aucune suppression.
  — ips — éléments à supprimer du tableau d’adresses_ips_.
  — urls — éléments à supprimer du tableau_urls_.

### <a name="examples"></a>Exemples :

Exemple 1 d’URI de requête : [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Toutes les modifications précédentes apportées à l’instance de service Worldwide d’Office 365 sont demandées. Exemple de résultat :

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Exemple 2 d’URI de requête : [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Les modifications apportées à l’instance Worldwide d’Office 365 depuis la version spécifiée sont demandées. Dans ce cas, la version spécifiée est la dernière. Exemple de résultat :

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Exemple de Script PowerShell

Vous pouvez exécuter un script PowerShell pour voir s’il y a des actions à suivre pour les données mises à jour. Vous pouvez exécuter ce script sous la forme d’une tâche planifiée pour rechercher une mise à jour de la version. Pour éviter une charge excessive sur le service Web, essayez de ne pas exécuter le script plus d’une fois par heure.

Ce script effectue les opérations suivantes :

- Vérifie le numéro de version des points de terminaison d’instance dans le monde Office 365 en appelant l’API REST du service Web.
- Recherche un fichier de version actuelle sur _$Env:TEMP\O365_endpoints_latestversion.txt_. Le chemin d’accès de la variable globale **$Env:TEMP**est généralement _C:\Users\\<username\>\AppData\Local\Temp_.
- S’il s’agit de la première fois que le script est exécuté, le script renvoie la version actuelle et toutes les adresses IP et URL actuelles, écrit la version des points de terminaison dans le fichier _$Env:TEMP\O365_endpoints_latestversion.txt_ et les points de terminaison la sortie des données vers le fichier _$Env:TEMP\O365_endpoints_data.txt_. Vous pouvez modifier le chemin d’accès et/ou le nom du fichier de sortie en modifiant les lignes suivantes :

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- À chaque exécution suivante du script, si la version de service Web la plus récente est identique à la version figurant dans le fichier _O365_endpoints_latestversion.txt_, le script se ferme sans apporter de modifications.
- Lorsque la dernière version du service Web est plus récente que la version du fichier _O365_endpoints_latestversion.txt_, le script renvoie les points de terminaison et les filtres pour les points de terminaison catégories **autoriser** et **optimiser**, met à jour la version figurant dans le fichier _O365_endpoints_latestversion.txt_ et écrit les données mises à jour dans le fichier_O365_endpoints_data.txt_. 

Le script génère une _ClientRequestId_ unique pour l’ordinateur sur lequel il est exécuté et réutilise cet ID dans plusieurs appels. Cet ID est stocké dans le fichier_O365_endpoints_latestversion.txt_.

### <a name="to-run-the-powershell-script"></a>Exécution du script PowerShell

1. Copiez le script et enregistrez-le sur votre disque dur local ou sur l’emplacement de votre script sous_Get-O365WebServiceUpdates.ps1_.
1. Exécutez le script dans votre éditeur de script favori, tel que le code ISE ou VS PowerShell, ou à partir d’une console PowerShell à l’aide de la commande suivante :

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    Il n’existe aucun paramètre à transmettre au script.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>Exemple de Script Python

Voici un script Python testé avec Python 3.6.3 on Windows 10, que vous pouvez exécuter pour voir s’il y a des actions à exécuter pour les données mises à jour. Ce script vérifie le numéro de version pour les points de terminaison de l’instance Worldwide d’Office 365. Lorsqu’une modification a lieu, il télécharge les points de terminaison et les filtre en fonction de la catégorie _Allow_ et _Optimize_. Il utilise aussi un ClientRequestId unique dans plusieurs appels et enregistre la dernière version trouvée dans un fichier temporaire. Vous devez appeler ce script une fois toutes les heures afin de rechercher une mise à jour de version.

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Contrôle de version interface de Service Web

Des mises à jour des paramètres ou des résultats pour ces méthodes de service Web peuvent être nécessaires à l’avenir. Une fois la version de disponibilité générale de ces services Web publiée, Microsoft fera des efforts raisonnables pour fournir à l’avance les mises à jour de matériel du service Web. Lorsque Microsoft pense qu’une mise à jour nécessite des modifications pour les clients utilisant le service Web, Microsoft conserve la version précédente (une version avant) du service Web disponible au moins 12 mois après la publication de la nouvelle version. Les clients qui n’effectuent pas de mise à niveau pendant ce temps peuvent être incapables d’accéder au service Web et à ses méthodes. Les clients doivent s’assurer que les clients du service Web continuent de fonctionner sans erreur si les modifications suivantes sont apportées à la signature de l’interface de service Web :

- Ajout d’un nouveau paramètre facultatif à une méthode web existant qui ne doit pas être fournie par des clients plus anciens et n’affecte pas le résultat qu’un client plus ancien reçoit.
- Ajout d’un attribut avec un nouveau nom dans l’un des éléments REST de réponse ou de colonnes supplémentaires au CSV de réponse.
- Ajout d’une nouvelle méthode web avec un nouveau nom qui n’est pas appelée par les clients plus anciens.

## <a name="update-notifications"></a>Notifications de mise à jour

Vous pouvez utiliser plusieurs méthodes pour recevoir des notifications par courrier électronique lorsque des modifications apportées aux adresses IP et aux URL sont publiées sur le service Web.

- Pour utiliser une solution de flux Microsoft, voir [utiliser Microsoft Flow pour recevoir un courrier électronique pour les modifications apportées aux adresses IP et URL d’Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- Pour déployer une application de logique Azure à l’aide d’un modèle ARM, voir [notification de mise à jour d’Office 365 (v 1.1)](https://aka.ms/ipurlws-updates-template).
- Pour écrire votre propre script de notification à l’aide de PowerShell, voir [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Exporte un fichier PAC Proxy

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) est un script PowerShell qui lit les derniers points de terminaison réseau à partir de l’adresse IP et du service Web d’URL Office 365 et crée un exemple de fichier PAC. Pour plus d’informations sur l’utilisation de Get-PacFile, voir [utiliser un fichier PAC pour le routage direct du trafic Office 365 vital](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>Rubriques connexes
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
