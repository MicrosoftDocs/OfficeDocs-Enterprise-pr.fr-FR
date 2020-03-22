---
title: Confidentialité et conditions d’utilisation du réseau Office 365 (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Confidentialité et conditions d’utilisation du réseau Office 365 (aperçu)
ms.openlocfilehash: 9c47149ebef1e8b1614b26ad90fb60335783cfd0
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42891487"
---
# <a name="office-365-network-insights-privacy-and-terms-of-use-preview"></a>Confidentialité et conditions d’utilisation du réseau Office 365 (aperçu)

Le centre d’administration Microsoft 365 affiche maintenant des informations sur le **réseau et des recommandations**en matière de performances, qui sont des mesures de performances actives collectées à partir de votre client Office 365 et disponibles uniquement par les utilisateurs administratifs de votre client. La connectivité du réseau d’entreprise est conçue par emplacement de bureau via un emplacement réseau sortant vers Internet. La connectivité cliente d’Office 365 utilise cette route, puis sur Internet pour les serveurs Front Door de Microsoft service. L’identification des emplacements Office est essentielle pour pouvoir afficher ces informations sur le réseau.

## <a name="location-in-network-measurements"></a>Emplacement dans les mesures du réseau

L’administrateur d’une organisation peut choisir de l’emplacement à inclure dans les mesures du réseau utilisées par cette fonctionnalité. Cela permet la découverte automatique de la ville où se trouve chaque bureau. Les informations d’emplacement ne sont pas précises et sont obscurcies par le biais de la ville. Au moment où l’emplacement est capturé sur un appareil Windows, une icône **emplacement en cours** apparaît dans la barre d’outils et les administrateurs peuvent souhaiter en avertir les utilisateurs. Avec ce traitement, l’emplacement est traité comme l’emplacement du Bureau de l’organisation et non l’emplacement d’une personne ou d’un appareil. Les informations sur le réseau peuvent être affichées dans les villes des emplacements Office découverts. Si vous souhaitez obtenir une plus grande précision de recommandations, un administrateur peut entrer des adresses d’emplacement de bureau spécifiques et les informations sur le réseau seront regroupées à ceux-ci. Les emplacements Office ne peuvent pas être regroupés plus près de 300 mètres.

## <a name="location-in-the-microsoft-365-admin-center"></a>Emplacement dans le centre d’administration Microsoft 365

Dans le centre d’administration 365 de Microsoft, les contrôles de carte Bing sont utilisés pour indiquer où se trouvent les emplacements de bureau de l’organisation et pour afficher la topologie de périmètre réseau pour un emplacement de bureau sélectionné. Lorsqu’un administrateur ajoute des détails d’adresse spécifiques pour les emplacements Office, Bing Maps est également utilisé pour suggérer des adresses permettant de faciliter l’entrée des données.

## <a name="terms-of-use"></a>Conditions d’utilisation

Tout contenu fourni via Bing Maps, y compris les géocodes, ne peut être utilisé que dans le produit à partir duquel le contenu est fourni. L’utilisation par le client de la fonctionnalité services d’emplacement du centre d’administration M365, fournie par Bing Maps, est régie par les _conditions d’utilisation de l’utilisateur final cartes Bing_ disponibles sur le site <https://go.microsoft.com/?linkid=9710837> et la déclaration de confidentialité de _Microsoft_ disponible sur<https://go.microsoft.com/fwlink/?LinkID=248686.>

Cette fonctionnalité, fournie via Bing Maps, est également prise en charge par les **technologies ici**. Le mode d’exploitation des services de localisation fournis par les technologies est régi par les _conditions de service_ de <https://legal.here.com/en-gb/terms>nos technologies, disponibles sur le site.
