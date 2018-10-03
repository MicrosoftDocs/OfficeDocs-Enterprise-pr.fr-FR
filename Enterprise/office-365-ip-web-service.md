---
title: Service web d’URL et d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Pour vous aider à mieux identifier et différencier le trafic réseau Office 365, un nouveau service web publie les points de terminaison Office 365, afin de vous permettre d’évaluer, de configurer et de rester informé plus facilement des modifications. Ce nouveau service web remplace les fichiers téléchargeables XML actuellement disponibles.
ms.openlocfilehash: 2b5763b9f8f08f2cc619331dac70743474a8515b
ms.sourcegitcommit: d67e73f6cdc1e8d220d90a239e23e218f24528d2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "24961823"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Service web d’URL et d’adresses IP Office 365**

Pour vous aider à mieux identifier et différencier le trafic réseau Office 365, un nouveau service web publie les points de terminaison Office 365, afin de vous permettre d’évaluer, de configurer et de rester informé plus facilement des modifications. Ce nouveau service web remplace les fichiers téléchargeables XML actuellement disponibles. La suppression du format XML est prévue pour le 2 octobre 2018.

En tant que client ou fournisseur de périphérique de périmètre réseau, vous pouvez vous fonder sur le service web basé sur REST pour les entrées FQDN et les adresse IP Office 365. Vous pouvez accéder aux données directement dans un navigateur web à l’aide de ces URL.

- Pour obtenir la dernière version des URL et plages d’adresses IP Office 365, utilisez [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Pour les données sur la page des URL et plages d’adresses IP Office 365 pour les pare-feux et les serveurs proxy, utilisez [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Pour obtenir les dernières modifications depuis la fin de juillet 2018, date de première mise à disposition du service web, utilisez [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

En tant que client, vous pouvez utiliser ce service web pour :

- mettre à jour vos scripts PowerShell et obtenir des données de point de terminaison Office 365 et modifier la mise en forme de vos périphériques réseau ;
- utiliser ces informations pour mettre à jour des fichiers PAC déployés sur des ordinateurs clients.

En tant que fournisseur de périphérique de périmètre réseau, vous pouvez utiliser ce service web pour :

- créer et tester le logiciel du périphérique pour télécharger la liste pour une configuration automatisée ;
- rechercher la version actuelle ;
- obtenir les modifications actuelles.

Pour plus d’informations, voir :

- [Annonce du billet de blog dans le Forum de la communauté technique Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Forum de la communauté technique Office 365 pour les questions sur l’utilisation des services web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**Paramètres communs**

Ces paramètres sont communs à toutes les méthodes de service web :

- **format = CSV | JSON** : paramètre de chaîne de requête. Par défaut, le format de données renvoyé est JSON. Incluez ce paramètre facultatif pour renvoyer les données au format de valeurs séparées par des virgules (CSV).
- **ClientRequestId** : paramètre de chaîne de requête. GUID obligatoire que vous générez pour l’association client. Vous devez générer un GUID pour chaque ordinateur qui appelle le service web. N’utilisez pas les GUID illustrés dans les exemples suivants, car ils peuvent être bloqués par le service web à l’avenir. Le format du GUID est _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, où x représente un nombre hexadécimal. Pour générer un GUID, utilisez la commande PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).

## <a name="version-web-method"></a>**Méthode web de version**

Microsoft met à jour les entrées FQDN et les adresses IP Office 365 à la fin de chaque mois et parfois hors cycle pour des exigences opérationnelles ou de prise en charge. Les données pour chaque instance publiée sont attribuées à un numéro de version. La méthode web de version vous permet de rechercher la dernière version pour chaque instance du service Office 365. Nous vous recommandons d’effectuer la recherche tous les jours, ou toutes les heures, au maximum. Les nouvelles versions sont prévues au début de chaque mois. Il peut arriver qu’en raison d’incidents du support technique, d’exigences de sécurité ou d’autres exigences opérationnelles, de nouvelles versions soient disponibles pendant le mois.

Il y a un paramètre pour la méthode web de version :

- **AllVersions = true** : paramètre de chaîne de requête. Par défaut, la version renvoyée est la dernière version. Incluez ce paramètre facultatif pour demander toutes les versions publiées.
- **Format = JSON** | **CSV** | **RSS** : outre les formats JSON et CSV, la méthode web de version prend également en charge RSS. Vous pouvez l’utiliser, ainsi que le paramètre allVersions = true pour demander un flux RSS qui peut être utilisé avec Outlook ou d’autres lecteurs RSS.
- **Instance** : paramètre d’itinéraire. Ce paramètre facultatif spécifie l’instance pour laquelle renvoyer la version. S’il est omis, toutes les instances sont renvoyées. Les instances valides sont : Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Le résultat de la méthode web de version peut être un enregistrement unique ou un tableau d’enregistrements. Les éléments de chaque enregistrement sont :

- instance : nom court de l’instance de service Office 365.
- latest : dernière version pour les points de terminaison de l’instance spécifiée.
- versions : liste de toutes les versions précédentes pour l’instance spécifiée. Cet élément est inclus uniquement si le paramètre AllVersions est true.

Vous pouvez utiliser Microsoft Flow pour recevoir des notifications par e-mail vous informant des modifications apportées aux adresses IP et aux URL. Consultez la rubrique relative à l’[utilisation de Microsoft Flow pour être informé par courrier électronique des modifications apportées aux URL et aux adresses IP d’Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).

### <a name="examples"></a>**Exemples :**

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

[!IMPORTANT]
Le GUID pour le paramètre ClientRequestID dans ces URI n’est qu’un exemple. Pour essayer les URI de service web, générez votre propre GUID. Les GUID illustrés dans ces exemples pourront être bloqués par le service web à l’avenir.

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
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>**Méthode web de points de terminaison**

La méthode web de points de terminaison renvoie tous les enregistrements pour les plages d’adresses IP et les URL qui composent le service Office 365. Les dernières données issues de la méthode web de points de terminaison web doivent être utilisées pour la configuration des périphériques réseau mais les données peuvent être mises en cache jusqu’à 30 jours après leur publication en raison du préavis fourni pour les ajouts. Les paramètres pour la méthode web de points de terminaison sont :

- **ServiceAreas** : paramètre de chaîne de requête. Liste de valeurs séparées par des virgules pour les zones de service. Les éléments valides sont : Common, Exchange, SharePoint, Skype. Étant donné que les éléments de la zone de service Common sont une condition préalable pour toutes les autres zones de service, le service web les inclura toujours. Si vous n’incluez pas ce paramètre, toutes les zones de service sont renvoyées.
- **TenantName** : paramètre de chaîne de requête. Votre nom du client Office 365. Le service web prend le nom que vous avez fourni et l’insère dans des parties des URL qui incluent le nom du client. Si vous ne fournissez pas le nom du client, ces parties d’URL ont le caractère générique (\*).
- **NoIPv6** : paramètre de chaîne de requête. Définissez cette option sur true pour exclure les adresses IPv6 du résultat, par exemple, si vous n’utilisez pas IPv6 dans votre réseau.
- **Instance** : paramètre d’itinéraire. Ce paramètre obligatoire spécifie l’instance pour laquelle renvoyer les points de terminaison. Les instances valides sont : Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

Le résultat de la méthode web de points de terminaison est un tableau d’enregistrements avec chaque enregistrement représentant un ensemble de points de terminaison. Les éléments pour chaque enregistrement sont :

- id : l’ID non modifiable de l’ensemble de points de terminaison.
- serviceArea : la zone de service dont il fait partie : Common, Exchange, SharePoint ou Skype.
- urls: URL pour l’ensemble de points de terminaison. Un tableau JSON des enregistrements DNS. Omis si vide.
- tcpPorts : ports TCP pour l’ensemble de points de terminaison. Tous les éléments de ports sont au format de liste de ports séparés par des virgules ou de plages de port séparées par un tiret (-). Les ports s’appliquent à toutes les adresses IP et toutes les URL dans cet ensemble de points de terminaison pour cette catégorie. Omis si vide.
- udpPorts : ports UDP pour les plages d’adresses IP dans cet ensemble de points de terminaison. Omis si vide.
- ips : plages d’adresses IP associées à cet ensemble de points de terminaison tel qu’associées aux ports TCP ou UDP répertoriés. Un tableau JSON des plages d’adresses IP. Omis si vide.
- category : catégorie de connectivité pour le jeu de points de terminaison. Les valeurs valides sont Optimize, Allow et Default. Si vous utilisez les données du point de terminaison pour rechercher la catégorie d’une adresse IP ou d’une URL, il est possible que votre requête puisse renvoyer plusieurs catégories. Voici quelques raisons pour lesquelles cela peut se produire. Dans ces cas, vous devez suivre les recommandations pour la catégorie ayant la priorité la plus élevée. Par exemple, si le point de terminaison s’affiche dans Optimize et Allow, vous devez suivre la configuration requise pour Optimize. Obligatoire. 
- expressRoute : True ou False si cet ensemble de points de terminaison est routé sur ExpressRoute.
- required : True si cet ensemble de points de terminaison est obligatoire pour disposer d’une connectivité et prendre en charge Office 365. False si cet ensemble de points de terminaison est facultatif.
- notes : pour les points de terminaison facultatifs, ce texte décrit les fonctionnalités Office 365 qui manqueront si les adresses IP ou les URL dans cet ensemble de points de terminaison ne sont pas accessibles sur la couche réseau. Omis si vide.

### <a name="examples"></a>Exemples :

Exemple 1 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet URI a obtenu tous les points de terminaison pour l’instance Worldwide d’Office 365 pour toutes les charges de travail. Exemple de résultat montrant un extrait du résultat :

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
...
```

Des ensembles de points de terminaison supplémentaires ne sont pas inclus dans cet exemple.

Exemple 2 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Cet exemple obtient des points de terminaison pour l’instance Worldwide d’Office 365 pour Exchange Online et les dépendances uniquement.

Le résultat pour l’exemple 2 ressemble à l’exemple 1 sauf que les résultats n’incluent pas les points de terminaison pour SharePoint Online ou Skype Entreprise Online.

## <a name="changes-web-method"></a>Méthode web de modifications

La méthode web de modifications renvoie les dernières mises à jour publiées. Il s’agit généralement des modifications apportées aux plages d’adresses IP et aux URL le mois précédent. Les modifications les plus importantes à traiter sont celles qui concernent l’ajout de nouvelles URL ou d’adresses IP. En effet, en cas d’échec d’ajout d’une adresse IP à une liste de contrôle d’accès de pare-feu ou d’une URL pointant vers une liste de contournement de serveur proxy, une panne pour les utilisateurs Office 365 utilisant ce périphérique réseau peut se produire. Malgré les exigences opérationnelles, les opérations d’_ajout_ sont ajoutées avec un préavis de 30 jours avant qu’une panne se produise.

Le paramètre de la méthode web de modifications est :

- **Version** : paramètre d’itinéraire URL obligatoire. La version que vous avez implémentée actuellement et dont vous souhaitez voir les modifications depuis cette version. Le format est _YYYYMMDDNN_.

Le résultat de la méthode web de modifications est un tableau d’enregistrements avec chaque enregistrement représentant une modification dans une version spécifique des points de terminaison. Les éléments pour chaque enregistrement sont :

- ID : ID non modifiable de l’enregistrement de la modification.
- endpointSetId : ID de l’enregistrement du point de terminaison qui est modifié. Obligatoire.
- disposition : modification, ajout ou suppression qui décrit l’effet de la modification sur l’enregistrement du point de terminaison. Obligatoire.
- version : version de l’ensemble de points de terminaison publié dans laquelle la modification a été introduite. Les numéros de version sont au format _YYYYMMDDNN_, où NN est un nombre naturel incrémenté si plusieurs versions doivent être publiées sur un seul jour.
- previous : sous-structure détaillant les valeurs précédentes des éléments modifiés sur l’ensemble de points de terminaison. Cela ne sera pas inclus pour les ensembles de points de terminaison nouvellement ajoutés. Inclut udpPorts, ExpressRoute, category, required, notes.
- current : sous-structure détaillant les valeurs mises à jour des éléments de modifications sur l’ensemble de points de terminaison. Inclut cpPorts, udpPorts, ExpressRoute, category, required, notes.
- add : sous-structure détaillant les éléments à ajouter aux collections d’ensembles de points de terminaison. Omis s’il n’y a aucun ajout.
  - effectiveDate : définit les données lorsque les ajouts seront disponibles dans le service.
  - ips : éléments à ajouter au tableau d’adresses IP.
  - urls : éléments à ajouter au tableau d’URL.
- remove : sous-structure détaillant les éléments à supprimer de l’ensemble de points de terminaison. Omis s’il n’y a aucune suppression.
  - ips : éléments à supprimer du tableau d’adresses IP.
  - urls : éléments à supprimer du tableau d’URL.

### <a name="examples"></a>**Exemples :**

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
...
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

## <a name="example-powershell-script"></a>**Exemple de script PowerShell**

Voici un script PowerShell que vous pouvez exécuter pour voir s’il y a des actions à exécuter pour les données mises à jour. Ce script vérifie le numéro de version pour les points de terminaison de l’instance Worldwide d’Office 365. Lorsqu’une modification a lieu, il télécharge les points de terminaison et les filtre en fonction de la catégorie &quot;Allow&quot; et &quot;Optimize&quot;. Il utilise aussi un ClientRequestId unique dans plusieurs appels et enregistre la dernière version trouvée dans un fichier temporaire. Vous devez appeler ce script une fois toutes les heures afin de rechercher une mise à jour de version.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
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
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**Exemple de script Python**

Voici un script Python testé avec Python 3.6.3 on Windows 10, que vous pouvez exécuter pour voir s’il y a des actions à exécuter pour les données mises à jour. Ce script vérifie le numéro de version pour les points de terminaison de l’instance Worldwide d’Office 365. Lorsqu’une modification a lieu, il télécharge les points de terminaison et les filtre en fonction de la catégorie _Allow_ et _Optimize_. Il utilise aussi un ClientRequestId unique dans plusieurs appels et enregistre la dernière version trouvée dans un fichier temporaire. Vous devez appeler ce script une fois toutes les heures afin de rechercher une mise à jour de version.

```python
import json
import os
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
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
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

## <a name="web-service-interface-versioning"></a>**Contrôle de version de l’interface du service web**

Des mises à jour des paramètres ou des résultats de ces méthodes de service web peuvent être requises à l’avenir. Une fois que la version de disponibilité générale de ces services web sera publiée, Microsoft s’efforcera de fournir un préavis des mises à jour matérielles au service web. Si Microsoft pense qu’une mise à jour nécessite des modifications des clients qui utilisent le service web, Microsoft conservera la version précédente (une version antérieure) du service web disponible pendant au moins douze (12) mois après la publication de la nouvelle version. Les clients qui n’effectuent pas de mise à niveau pendant ce délai ne pourront peut-être pas accéder au service web et à ses méthodes. Les clients doivent s’assurer que les clients du service web continuent à travailler sans erreur si les modifications suivantes sont apportées à la signature de l’interface du service web :

- Ajout d’un nouveau paramètre facultatif à une méthode web existant qui ne doit pas être fournie par des clients plus anciens et n’affecte pas le résultat qu’un client plus ancien reçoit.
- Ajout d’un attribut avec un nouveau nom dans l’un des éléments REST de réponse ou de colonnes supplémentaires au CSV de réponse.
- Ajout d’une nouvelle méthode web avec un nouveau nom qui n’est pas appelée par les clients plus anciens.

## <a name="related-topics"></a>Voir aussi
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)

[Connectivité réseau à Office 365](network-connectivity.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
