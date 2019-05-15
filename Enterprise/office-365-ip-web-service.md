---
title: Service web d’URL et d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
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
ms.openlocfilehash: 35a34071a76e551cde8342566a912e4fd4d0100e
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "33976519"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="0bffb-104">Service web d’URL et d’adresses IP Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="0bffb-p102">Pour vous aider à mieux identifier et différencier le trafic réseau Office 365, un nouveau service web publie les points de terminaison Office 365, afin de vous permettre d’évaluer, de configurer et de rester informé plus facilement des modifications. Ce nouveau service web remplace les fichiers téléchargeables XML actuellement disponibles. La suppression du format XML est prévue pour le 2 octobre 2018.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="0bffb-p103">En tant que client ou fournisseur de périphérique de périmètre réseau, vous pouvez vous fonder sur le service web basé sur REST pour les entrées FQDN et les adresse IP Office 365. Vous pouvez accéder aux données directement dans un navigateur web à l’aide de ces URL.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="0bffb-110">Pour obtenir la dernière version des URL et plages d’adresses IP Office 365, utilisez [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0bffb-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="0bffb-111">Pour les données sur la page des URL et plages d’adresses IP Office 365 pour les pare-feux et les serveurs proxy, utilisez [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0bffb-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="0bffb-112">Pour obtenir les dernières modifications depuis la fin de juillet 2018, date de première mise à disposition du service web, utilisez [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="0bffb-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="0bffb-113">En tant que client, vous pouvez utiliser ce service web pour :</span><span class="sxs-lookup"><span data-stu-id="0bffb-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="0bffb-114">mettre à jour vos scripts PowerShell et obtenir des données de point de terminaison Office 365 et modifier la mise en forme de vos périphériques réseau ;</span><span class="sxs-lookup"><span data-stu-id="0bffb-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="0bffb-115">utiliser ces informations pour mettre à jour des fichiers PAC déployés sur des ordinateurs clients.</span><span class="sxs-lookup"><span data-stu-id="0bffb-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="0bffb-116">En tant que fournisseur de périphérique de périmètre réseau, vous pouvez utiliser ce service web pour :</span><span class="sxs-lookup"><span data-stu-id="0bffb-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="0bffb-117">créer et tester le logiciel du périphérique pour télécharger la liste pour une configuration automatisée ;</span><span class="sxs-lookup"><span data-stu-id="0bffb-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="0bffb-118">rechercher la version actuelle ;</span><span class="sxs-lookup"><span data-stu-id="0bffb-118">Check for the current version.</span></span>
- <span data-ttu-id="0bffb-119">obtenir les modifications actuelles.</span><span class="sxs-lookup"><span data-stu-id="0bffb-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="0bffb-120">Si vous utilisez Azure ExpressRoute pour vous connecter à Office 365, consultez [Azure ExpressRoute pour Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) pour vous familiariser avec les services Office 365 pris en charge sur Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="0bffb-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="0bffb-121">Consultez l’article [ URLs and plages d’adresse IP Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) pour identifier les requêtes réseau des applications Office 365 qui nécessitent une connectivité Internet.</span><span class="sxs-lookup"><span data-stu-id="0bffb-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="0bffb-122">Cette opération permet de mieux configurer vos périphériques de sécurité de périmètre.</span><span class="sxs-lookup"><span data-stu-id="0bffb-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="0bffb-123">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="0bffb-123">For additional information, see:</span></span>

- [<span data-ttu-id="0bffb-124">Annonce du billet de blog dans le Forum de la communauté technique Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="0bffb-125">Forum de la communauté technique Office 365 pour les questions sur l’utilisation des services web</span><span class="sxs-lookup"><span data-stu-id="0bffb-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="0bffb-126">Paramètres communs</span><span class="sxs-lookup"><span data-stu-id="0bffb-126">Common parameters</span></span>

<span data-ttu-id="0bffb-127">Ces paramètres sont communs à toutes les méthodes de service web :</span><span class="sxs-lookup"><span data-stu-id="0bffb-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="0bffb-128">**format = < JSON | CSV >** : par défaut, le format de données renvoyé est JSON.</span><span class="sxs-lookup"><span data-stu-id="0bffb-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="0bffb-129">Utilisez ce paramètre facultatif pour renvoyer les données au format de valeurs séparées par des virgules (CSV).</span><span class="sxs-lookup"><span data-stu-id="0bffb-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="0bffb-130">**ClientRequestId =\<guid >**: un GUID requis que vous générez pour association client.</span><span class="sxs-lookup"><span data-stu-id="0bffb-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="0bffb-131">Vous devez générer un GUID pour chaque ordinateur qui appelle le service web.</span><span class="sxs-lookup"><span data-stu-id="0bffb-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="0bffb-132">N’utilisez pas les GUID illustrés dans les exemples suivants, car ils peuvent être bloqués par le service web à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="0bffb-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="0bffb-133">Format GUID est _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, où x représente un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="0bffb-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="0bffb-134">Pour générer un GUID, utilisez la commande PowerShell [nouveau Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="0bffb-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="0bffb-135">Méthode web version </span><span class="sxs-lookup"><span data-stu-id="0bffb-135">Version web method</span></span>

<span data-ttu-id="0bffb-p107">Microsoft met à jour les entrées FQDN et les adresses IP Office 365 à la fin de chaque mois et parfois hors cycle pour des exigences opérationnelles ou de prise en charge. Les données pour chaque instance publiée sont attribuées à un numéro de version. La méthode web de version vous permet de rechercher la dernière version pour chaque instance du service Office 365. Nous vous recommandons d’effectuer la recherche tous les jours, ou toutes les heures, au maximum. Les nouvelles versions sont prévues au début de chaque mois. Il peut arriver qu’en raison d’incidents du support technique, d’exigences de sécurité ou d’autres exigences opérationnelles, de nouvelles versions soient disponibles pendant le mois.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="0bffb-142">Les paramètres pour la méthode web de version sont :</span><span class="sxs-lookup"><span data-stu-id="0bffb-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="0bffb-143">**AllVersions = < true | Faux >** : par défaut, la version renvoyée est la dernière version.</span><span class="sxs-lookup"><span data-stu-id="0bffb-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="0bffb-144">Inclure ce paramètre facultatif pour demander toutes les versions publiées depuis que le service web a été publié.</span><span class="sxs-lookup"><span data-stu-id="0bffb-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="0bffb-145">**Format = < JSON | CSV | RSS >** : outre les formats JSON et CSV, la méthode web version prend également en charge RSS.</span><span class="sxs-lookup"><span data-stu-id="0bffb-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="0bffb-146">Vous pouvez utiliser ce paramètre facultatif conjointement avec le paramètre _AllVersions = true_ pour demander un flux RSS qui peut être utilisé avec Outlook ou d’autres lecteurs de RSS.</span><span class="sxs-lookup"><span data-stu-id="0bffb-146">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="0bffb-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** : ce paramètre facultatif spécifie l’instance vers laquelle renvoyer la version.</span><span class="sxs-lookup"><span data-stu-id="0bffb-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="0bffb-148">Si cet argument est omis, toutes les instances sont renvoyées.</span><span class="sxs-lookup"><span data-stu-id="0bffb-148">If omitted, all instances are returned.</span></span> <span data-ttu-id="0bffb-149">Les instances valides sont : Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="0bffb-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="0bffb-p111">La méthode web de version n’est pas limitée en débit et ne renvoie jamais de codes de réponse HTTP 429. La réponse à la méthode web de version inclut un en-tête Cache-Control qui recommande la mise en cache des données pendant 1 heure. Le résultat de la méthode web de version peut être un enregistrement unique ou un tableau d’enregistrements. Les éléments de chaque enregistrement sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="0bffb-154">instance : nom court de l’instance de service Office 365.</span><span class="sxs-lookup"><span data-stu-id="0bffb-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="0bffb-155">latest : dernière version pour les points de terminaison de l’instance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0bffb-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="0bffb-p112">versions : liste de toutes les versions précédentes pour l’instance spécifiée. Cet élément est inclus uniquement si le paramètre AllVersions est true.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="0bffb-p113">Vous pouvez utiliser Microsoft Flow pour recevoir des notifications par e-mail vous informant des modifications apportées aux adresses IP et aux URL. Consultez la rubrique relative à l’[utilisation de Microsoft Flow pour être informé par courrier électronique des modifications apportées aux URL et aux adresses IP d’Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="0bffb-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="0bffb-160">Exemples :</span><span class="sxs-lookup"><span data-stu-id="0bffb-160">Examples:</span></span>

<span data-ttu-id="0bffb-161">Exemple 1 d’URI de requête : [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p114">Cet URI renvoie la dernière version de chaque instance du service Office 365. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="0bffb-p115">Le GUID pour le paramètre ClientRequestID dans ces URI n’est qu’un exemple. Pour essayer les URI de service web, générez votre propre GUID. Les GUID illustrés dans ces exemples pourront être bloqués par le service web à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="0bffb-167">Exemple 2 d’URI de requête : [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p116">Cet URI renvoie la dernière version de chaque instance du service Office 365 spécifiée. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="0bffb-170">Exemple 3 d’URI de requête : [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p117">Cet URI affiche le résultat au format CSV. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="0bffb-173">Exemple 4 d’URI de requête : [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p118">Cet URI affiche toutes les versions antérieures publiées pour l’instance du service Office 365 dans le monde. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="0bffb-176">Exemple 5 d’URI de flux RSS : [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="0bffb-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="0bffb-p119">Cet URI affiche un flux RSS des versions publiées qui incluent des liens vers la liste des modifications apportées à chaque version. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
```

## <a name="endpoints-web-method"></a><span data-ttu-id="0bffb-179">Points de terminaison méthode web</span><span class="sxs-lookup"><span data-stu-id="0bffb-179">Endpoints web method</span></span>

<span data-ttu-id="0bffb-180">Les points de terminaison de la méthode web renvoient tous les enregistrements pour les plages d’adresses IP et URL qui composent le service Office 365.</span><span class="sxs-lookup"><span data-stu-id="0bffb-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="0bffb-181">Tandis que les dernières données de la méthode de points de terminaison web doivent être utilisées pour la configuration des appareils réseau, les données peuvent mis en cache jusqu’à 30 jours après leur publication en raison de l’avis d’avance fourni pour les ajouts.</span><span class="sxs-lookup"><span data-stu-id="0bffb-181">While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions.</span></span> <span data-ttu-id="0bffb-182">Nous vous recommandons de rappeler uniquement les points de terminaison méthode web uniquement lorsque la méthode web version indique qu’une nouvelle version des données est disponible.</span><span class="sxs-lookup"><span data-stu-id="0bffb-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="0bffb-183">Les paramètres pour les points de terminaison de la méthode web sont :</span><span class="sxs-lookup"><span data-stu-id="0bffb-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="0bffb-184">**ServiceAreas = < courantes | Exchange | SharePoint | Skype >** : une liste de zones de service séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="0bffb-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="0bffb-185">Éléments valides sont _Common_, _Exchange_, _SharePoint_, et _Skype_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="0bffb-186">Étant donné que les éléments communs de zone de service sont une condition préalable pour toutes les autres zones de service, le service web les inclura toujours.</span><span class="sxs-lookup"><span data-stu-id="0bffb-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="0bffb-187">Si vous n’incluez pas ce paramètre, toutes les zones de service sont renvoyées.</span><span class="sxs-lookup"><span data-stu-id="0bffb-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="0bffb-188">**TenantName = < tenant_name >** : nom de votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="0bffb-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="0bffb-189">Le service web prend votre nom fourni et l’insère en plusieurs parties d’URL qui incluent le nom de client.</span><span class="sxs-lookup"><span data-stu-id="0bffb-189">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="0bffb-190">Si vous ne fournissez pas de nom de client, ces composants d’URL ont le caractère générique (\*).</span><span class="sxs-lookup"><span data-stu-id="0bffb-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="0bffb-191">**NoIPv6=<true | false>**  : définissez cette option sur true pour exclure les adresses IPv6 du résultat, par exemple, si vous n’utilisez pas IPv6 dans votre réseau.</span><span class="sxs-lookup"><span data-stu-id="0bffb-191">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="0bffb-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** : ce paramètre facultatif spécifie l’instance vers laquelle renvoyer les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bffb-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="0bffb-193">Les instances valides sont : _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-193">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="0bffb-194">Si vous appelez la méthode web endpoints un grand nombre de fois à partir de la même adresse IP du client, vous pouvez recevoir le code de réponse HTTP 429 (Trop de requêtes).</span><span class="sxs-lookup"><span data-stu-id="0bffb-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="0bffb-195">La plupart des utilisateurs ne verra jamais ceci.</span><span class="sxs-lookup"><span data-stu-id="0bffb-195">Most people will never see this.</span></span> <span data-ttu-id="0bffb-196">Si vous recevez ce code de réponse, patientez 1 heure avant de renouveler votre demande.</span><span class="sxs-lookup"><span data-stu-id="0bffb-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="0bffb-197">Rappelez uniquement la méthode web endpoints uniquement lorsque la méthode web indique qu’une nouvelle version est disponible.</span><span class="sxs-lookup"><span data-stu-id="0bffb-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="0bffb-p125">Le résultat de la méthode web de points de terminaison est un tableau d’enregistrements avec chaque enregistrement représentant un ensemble de points de terminaison. Les éléments pour chaque enregistrement sont :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="0bffb-200">id : l’ID non modifiable de l’ensemble de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bffb-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="0bffb-201">serviceArea : la zone de service dont il fait partie : Common, Exchange, SharePoint ou Skype.</span><span class="sxs-lookup"><span data-stu-id="0bffb-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="0bffb-p126">urls: URL pour l’ensemble de points de terminaison. Un tableau JSON des enregistrements DNS. Omis si vide.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="0bffb-p127">tcpPorts : ports TCP pour l’ensemble de points de terminaison. Tous les éléments de ports sont au format de liste de ports séparés par des virgules ou de plages de port séparées par un tiret (-). Les ports s’appliquent à toutes les adresses IP et toutes les URL dans cet ensemble de points de terminaison pour cette catégorie. Omis si vide.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="0bffb-p128">udpPorts : ports UDP pour les plages d’adresses IP dans cet ensemble de points de terminaison. Omis si vide.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="0bffb-p129">ips : plages d’adresses IP associées à cet ensemble de points de terminaison tel qu’associées aux ports TCP ou UDP répertoriés. Un tableau JSON des plages d’adresses IP. Omis si vide.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="0bffb-p130">category : catégorie de connectivité pour le jeu de points de terminaison. Les valeurs valides sont Optimize, Allow et Default. Si vous utilisez les données du point de terminaison pour rechercher la catégorie d’une adresse IP ou d’une URL, il est possible que votre requête puisse renvoyer plusieurs catégories. Voici quelques raisons pour lesquelles cela peut se produire. Dans ces cas, vous devez suivre les recommandations pour la catégorie ayant la priorité la plus élevée. Par exemple, si le point de terminaison s’affiche dans Optimize et Allow, vous devez suivre la configuration requise pour Optimize. Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="0bffb-221">expressRoute : True ou False si cet ensemble de points de terminaison est routé sur ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="0bffb-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="0bffb-p131">required : True si cet ensemble de points de terminaison est obligatoire pour disposer d’une connectivité et prendre en charge Office 365. False si cet ensemble de points de terminaison est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="0bffb-p132">notes : pour les points de terminaison facultatifs, ce texte décrit les fonctionnalités Office 365 qui manqueront si les adresses IP ou les URL dans cet ensemble de points de terminaison ne sont pas accessibles sur la couche réseau. Omis si vide.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="0bffb-226">Exemples :</span><span class="sxs-lookup"><span data-stu-id="0bffb-226">Examples:</span></span>

<span data-ttu-id="0bffb-227">Exemple 1 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p133">Cet URI a obtenu tous les points de terminaison pour l’instance Worldwide d’Office 365 pour toutes les charges de travail. Exemple de résultat montrant un extrait du résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="0bffb-230">Des ensembles de points de terminaison supplémentaires ne sont pas inclus dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="0bffb-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="0bffb-231">Exemple 2 d’URI de requête : [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-232">Cet exemple obtient des points de terminaison pour l’instance Worldwide d’Office 365 pour Exchange Online et les dépendances uniquement.</span><span class="sxs-lookup"><span data-stu-id="0bffb-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="0bffb-233">Le résultat pour l’exemple 2 ressemble à l’exemple 1 sauf que les résultats n’incluent pas les points de terminaison pour SharePoint Online ou Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="0bffb-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="0bffb-234">Méthode web de modifications</span><span class="sxs-lookup"><span data-stu-id="0bffb-234">Changes web method</span></span>

<span data-ttu-id="0bffb-p134">La méthode web de modifications renvoie les dernières mises à jour publiées. Il s’agit généralement des modifications apportées aux plages d’adresses IP et aux URL le mois précédent. Les modifications les plus importantes à traiter sont celles qui concernent l’ajout de nouvelles URL ou d’adresses IP. En effet, en cas d’échec d’ajout d’une adresse IP à une liste de contrôle d’accès de pare-feu ou d’une URL pointant vers une liste de contournement de serveur proxy, une panne pour les utilisateurs Office 365 utilisant ce périphérique réseau peut se produire. Malgré les exigences opérationnelles, les opérations d’_ajout_ sont ajoutées avec un préavis de 30 jours avant qu’une panne se produise.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="0bffb-239">Le paramètre requis pour la méthode web changes est le suivant :</span><span class="sxs-lookup"><span data-stu-id="0bffb-239">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="0bffb-240">**Version=\<YYYYMMDDNN>** - Paramètre d’itinéraire d’URL requis.</span><span class="sxs-lookup"><span data-stu-id="0bffb-240">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="0bffb-241">Cette valeur doit être la version que vous avez implémentée actuellement.</span><span class="sxs-lookup"><span data-stu-id="0bffb-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="0bffb-242">Le service web renvoie les modifications depuis cette version.</span><span class="sxs-lookup"><span data-stu-id="0bffb-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="0bffb-243">Le format est _JJNN/MM/AAAA_, où _NN_ est un nombre entier incrémenté si plusieurs versions doivent être publiées un même jour,  _00_ représentant la première mise à jour à la date concernée.</span><span class="sxs-lookup"><span data-stu-id="0bffb-243">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="0bffb-244">Le service web exige que le paramètre _version_ contienne exactement 10 chiffres.</span><span class="sxs-lookup"><span data-stu-id="0bffb-244">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="0bffb-245">La méthode web changes est limitée par le débit de la même manière que la méthode web endpoints.</span><span class="sxs-lookup"><span data-stu-id="0bffb-245">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="0bffb-246">Si vous recevez un code de réponse HTTP 429, attendez 1 heure avant de renouveler votre demande.</span><span class="sxs-lookup"><span data-stu-id="0bffb-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="0bffb-p137">Le résultat de la méthode web de modifications est un tableau d’enregistrements avec chaque enregistrement représentant une modification dans une version spécifique des points de terminaison. Les éléments pour chaque enregistrement sont :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="0bffb-249">ID : ID non modifiable de l’enregistrement de la modification.</span><span class="sxs-lookup"><span data-stu-id="0bffb-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="0bffb-250">endpointSetId : ID de l’enregistrement du point de terminaison qui est modifié.</span><span class="sxs-lookup"><span data-stu-id="0bffb-250">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="0bffb-251">disposition : modification, ajout ou suppression qui décrit l’effet de la modification sur l’enregistrement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bffb-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
- <span data-ttu-id="0bffb-p138">impact : toutes les modifications n’ont pas le même degré d’importance pour chaque environnement. Cet élément décrit l’impact attendu dans un environnement de périmètre réseau d’entreprise suite à cette modification. Cet attribut est inclus uniquement dans les enregistrements de modification de la version **2018112800** et ultérieure. Les options pour l’impact sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version **2018112800** and later. Options for the impact are:</span></span>
  - <span data-ttu-id="0bffb-p139">AddedIp : une adresse IP a été ajoutée à Office 365 et sera bientôt active sur le service. Cela représente une modification à apporter à un pare-feu ou un autre appareil de périmètre réseau de couche 3. Une indisponibilité peut se produire si vous ne l’ajoutez pas avant le début de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="0bffb-259">AddedUrl – Une URL a été ajoutée à Office 365 et sera bientôt disponible sur le service.</span><span class="sxs-lookup"><span data-stu-id="0bffb-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="0bffb-260">Il s’agit d’un changement que vous devez apporter à un serveur proxy ou à un périphérique réseau d’analyse d’URL.</span><span class="sxs-lookup"><span data-stu-id="0bffb-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="0bffb-261">Si vous ne l’ajoutez pas avant que nous commencions à l’utiliser, vous pourriez subir une panne.</span><span class="sxs-lookup"><span data-stu-id="0bffb-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="0bffb-p141">AddedIpAndUrl : une adresse IP et une URL ont été ajoutées. Cela représente une modification à apporter à un pare-feu de couche 3, un serveur proxy ou un périphérique d’analyse d’URL. Une indisponibilité peut se produire si vous ne l’ajoutez pas avant le début de son utilisation.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="0bffb-p142">RemovedIpOrUrl : au moins une adresse IP ou une URL a été supprimée d’Office 365. Vous devez supprimer les points de terminaison réseau de vos périphériques de périmètre, mais vous n’avez aucune date d'échéance.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="0bffb-p143">ChangedIsExpressRoute : l’attribut de support ExpressRoute a été modifié. Si vous utilisez ExpressRoute, vous devez agir en fonction de votre configuration.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="0bffb-p144">MovedIpOrUrl : nous avons déplacé une adresse IP ou une URL entre cet ensemble de points de terminaison et un autre emplacement. En général, aucune action n’est requise.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="0bffb-p145">RemovedDuplicateIpOrUrl : nous avons supprimé une adresse IP ou une URL en double, mais celle-ci est toujours publiée pour Office 365. En général, aucune action n’est requise.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="0bffb-273">OtherNonPriorityChanges : nous avons modifié un élément moins critique que toutes les autres options, comme un champ de note.</span><span class="sxs-lookup"><span data-stu-id="0bffb-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="0bffb-p146">version : version de l’ensemble de points de terminaison publié dans laquelle la modification a été introduite. Les numéros de version sont au format _YYYYMMDDNN_, où NN est un nombre naturel incrémenté si plusieurs versions doivent être publiées sur un seul jour.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="0bffb-276">previous : sous-structure détaillant les valeurs précédentes des éléments modifiés sur le point de terminaison défini.</span><span class="sxs-lookup"><span data-stu-id="0bffb-276">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="0bffb-277">Elle ne sera pas incluse pour les nouveaux ensembles de points de terminaison ajoutés.</span><span class="sxs-lookup"><span data-stu-id="0bffb-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="0bffb-278">Inclut _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ et _notes_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-278">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="0bffb-279">current : une sous-structure détaillant les valeurs mises à jour des éléments de modifications dans l’ensemble des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bffb-279">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="0bffb-280">Inclut _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ et _notes_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-280">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="0bffb-p149">add : sous-structure détaillant les éléments à ajouter aux collections d’ensembles de points de terminaison. Omis s’il n’y a aucun ajout.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="0bffb-283">effectiveDate : définit les données lorsque les ajouts seront disponibles dans le service.</span><span class="sxs-lookup"><span data-stu-id="0bffb-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="0bffb-284">ips : éléments à ajouter au tableau d’adresses _ips_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-284">ips - Items to be added to the _ips_ array.</span></span>
  - <span data-ttu-id="0bffb-285">urls : éléments à ajouter au tableau_urls_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-285">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="0bffb-286">remove : sous-structure détaillant les éléments à supprimer de l’ensemble de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bffb-286">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="0bffb-287">Omis si aucune suppression.</span><span class="sxs-lookup"><span data-stu-id="0bffb-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="0bffb-288">ips : éléments à supprimer du tableau d’adresses_ips_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-288">ips - Items to be removed from the _ips_ array.</span></span>
  - <span data-ttu-id="0bffb-289">urls : éléments à supprimer du tableau _urls_.</span><span class="sxs-lookup"><span data-stu-id="0bffb-289">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="0bffb-290">Exemples :</span><span class="sxs-lookup"><span data-stu-id="0bffb-290">Examples:</span></span>

<span data-ttu-id="0bffb-291">Exemple 1 d’URI de requête : [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p151">Toutes les modifications précédentes apportées à l’instance de service Worldwide d’Office 365 sont demandées. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="0bffb-294">Exemple 2 d’URI de requête : [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="0bffb-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="0bffb-p152">Les modifications apportées à l’instance Worldwide d’Office 365 depuis la version spécifiée sont demandées. Dans ce cas, la version spécifiée est la dernière. Exemple de résultat :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="0bffb-298">Exemple de Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="0bffb-298">Example PowerShell Script</span></span>

<span data-ttu-id="0bffb-299">Voici un script PowerShell que vous pouvez exécuter pour voir s’il y a des actions à suivre pour les données mises à jour.</span><span class="sxs-lookup"><span data-stu-id="0bffb-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="0bffb-300">Ce script vérifie le numéro de version pour les points de terminaison instance Office 365 dans le monde.</span><span class="sxs-lookup"><span data-stu-id="0bffb-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="0bffb-301">Lorsqu’il y a une modification, ce dernier télécharge les points de terminaison et les filtres pour les points de terminaison catégorie « Autoriser » et « Optimiser ».</span><span class="sxs-lookup"><span data-stu-id="0bffb-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="0bffb-302">Il utilise également une unique _ClientRequestId_ au sein de plusieurs appels et enregistre la dernière version trouvée dans un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="0bffb-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="0bffb-303">Vous devez appeler une fois par heure ce script pour rechercher une mise à jour de version.</span><span class="sxs-lookup"><span data-stu-id="0bffb-303">You should call this script once an hour to check for a version update.</span></span>

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
    $flatIp6s = $endpointSets | ForEach-Object {
    $endpointSet = $_
    $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
    # IPv6 strings have colons while IPv6 strings have dots
    $ip6s = $ips | Where-Object { $_ -like '*:*' }
    $ipCustomObjects = @()
    if ($endpointSet.category -in ("Optimize")) {
        $ipCustomObjects = $ip6s | ForEach-Object {
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
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a><span data-ttu-id="0bffb-304">Exemple de Script Python</span><span class="sxs-lookup"><span data-stu-id="0bffb-304">Example Python Script</span></span>

<span data-ttu-id="0bffb-p154">Voici un script Python testé avec Python 3.6.3 on Windows 10, que vous pouvez exécuter pour voir s’il y a des actions à exécuter pour les données mises à jour. Ce script vérifie le numéro de version pour les points de terminaison de l’instance Worldwide d’Office 365. Lorsqu’une modification a lieu, il télécharge les points de terminaison et les filtre en fonction de la catégorie _Allow_ et _Optimize_. Il utilise aussi un ClientRequestId unique dans plusieurs appels et enregistre la dernière version trouvée dans un fichier temporaire. Vous devez appeler ce script une fois toutes les heures afin de rechercher une mise à jour de version.</span><span class="sxs-lookup"><span data-stu-id="0bffb-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="0bffb-310">Contrôle de version interface de Service Web</span><span class="sxs-lookup"><span data-stu-id="0bffb-310">Web Service interface versioning</span></span>

<span data-ttu-id="0bffb-p155">Des mises à jour des paramètres ou des résultats de ces méthodes de service web peuvent être requises à l’avenir. Une fois que la version de disponibilité générale de ces services web sera publiée, Microsoft s’efforcera de fournir un préavis des mises à jour matérielles au service web. Si Microsoft pense qu’une mise à jour nécessite des modifications des clients qui utilisent le service web, Microsoft conservera la version précédente (une version antérieure) du service web disponible pendant au moins douze (12) mois après la publication de la nouvelle version. Les clients qui n’effectuent pas de mise à niveau pendant ce délai ne pourront peut-être pas accéder au service web et à ses méthodes. Les clients doivent s’assurer que les clients du service web continuent à travailler sans erreur si les modifications suivantes sont apportées à la signature de l’interface du service web :</span><span class="sxs-lookup"><span data-stu-id="0bffb-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="0bffb-316">Ajout d’un nouveau paramètre facultatif à une méthode web existant qui ne doit pas être fournie par des clients plus anciens et n’affecte pas le résultat qu’un client plus ancien reçoit.</span><span class="sxs-lookup"><span data-stu-id="0bffb-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="0bffb-317">Ajout d’un attribut avec un nouveau nom dans l’un des éléments REST de réponse ou de colonnes supplémentaires au CSV de réponse.</span><span class="sxs-lookup"><span data-stu-id="0bffb-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="0bffb-318">Ajout d’une nouvelle méthode web avec un nouveau nom qui n’est pas appelée par les clients plus anciens.</span><span class="sxs-lookup"><span data-stu-id="0bffb-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="0bffb-319">Module de fonctions de point de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="0bffb-320">Microsoft héberge un service REST pour obtenir l’URI la plus récente et la plus nouvelle pour les services Office 365.</span><span class="sxs-lookup"><span data-stu-id="0bffb-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="0bffb-321">Pour pouvoir utiliser l’URI comme une collection, vous pouvez utiliser ce module avec quelques applets de commande utiles.</span><span class="sxs-lookup"><span data-stu-id="0bffb-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="0bffb-322">Appeler le service REST</span><span class="sxs-lookup"><span data-stu-id="0bffb-322">Calling the REST service</span></span>

<span data-ttu-id="0bffb-323">Pour utiliser ce module, il suffit de copier le fichier du module [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) quelque part sur votre disque dur et importez-le directement avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="0bffb-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="0bffb-324">Après avoir importé le module, vous pourrez appeler le service REST.</span><span class="sxs-lookup"><span data-stu-id="0bffb-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="0bffb-325">Cela renverra l’URI en tant que collection que vous pouvez traiter maintenant directement dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bffb-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="0bffb-326">Vous devez entrer le nom de votre client Office 365, comme décrit dans la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0bffb-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a><span data-ttu-id="0bffb-327">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0bffb-327">Parameters</span></span>

- <span data-ttu-id="0bffb-328">**tenantName** : le nom de votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="0bffb-328">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="0bffb-329">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0bffb-329">This parameter is mandatory.</span></span>
- <span data-ttu-id="0bffb-330">**ForceLatest** : ce commutateur force l’API REST pour à toujours renvoyer la liste entière de la dernière URI.</span><span class="sxs-lookup"><span data-stu-id="0bffb-330">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="0bffb-331">**IPv6**: ce commutateur renverra également les adresses IPv6.</span><span class="sxs-lookup"><span data-stu-id="0bffb-331">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="0bffb-332">Par défaut uniquement IPv4 est renvoyé.</span><span class="sxs-lookup"><span data-stu-id="0bffb-332">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="0bffb-333">Exemples</span><span class="sxs-lookup"><span data-stu-id="0bffb-333">Examples</span></span>

<span data-ttu-id="0bffb-334">Retourne la liste complète de tous les URI, y compris les adresses IPv6</span><span class="sxs-lookup"><span data-stu-id="0bffb-334">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="0bffb-335">Renvoie uniquement les adresses IP pour Service Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0bffb-335">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="0bffb-336">Exporte un fichier PAC Proxy</span><span class="sxs-lookup"><span data-stu-id="0bffb-336">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="0bffb-337">Ce module permet de créer un fichier PAC Proxy.</span><span class="sxs-lookup"><span data-stu-id="0bffb-337">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="0bffb-338">Dans cet exemple vous obtenez tout d’abord les points de terminaison et filtrez le résultat pour sélectionner les URL.</span><span class="sxs-lookup"><span data-stu-id="0bffb-338">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="0bffb-339">Ces URL sont redirigées pour être exportées.</span><span class="sxs-lookup"><span data-stu-id="0bffb-339">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="0bffb-340">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="0bffb-340">Related Topics</span></span>
  
[<span data-ttu-id="0bffb-341">URL et plages d’adresses IP Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-341">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="0bffb-342">Points de terminaison Office 365 - FAQ</span><span class="sxs-lookup"><span data-stu-id="0bffb-342">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="0bffb-343">Principes de connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-343">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="0bffb-344">Paramétrage des performances et du réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-344">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="0bffb-345">Connectivité réseau à Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-345">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="0bffb-346">Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="0bffb-346">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="0bffb-347">Optimisation de votre réseau pour Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="0bffb-347">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="0bffb-348">Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances</span><span class="sxs-lookup"><span data-stu-id="0bffb-348">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="0bffb-349">Plan de résolution des problèmes de performances pour Office 365</span><span class="sxs-lookup"><span data-stu-id="0bffb-349">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
