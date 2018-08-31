---
title: Prise en charge de la traduction d’adresses réseau (NAT) dans Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Résumé : Fournit des informations détaillées sur la manière d’estimer correctement le nombre de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT).'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540308"
---
# <a name="nat-support-with-office-365"></a>Prise en charge de la traduction d’adresses réseau (NAT) dans Office 365

 **Résumé :** Fournit des informations détaillées sur la manière d’estimer correctement le nombre de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT). 
  
Auparavant, conseils suggéré que le nombre maximal de clients Exchange que vous devez utiliser par adresse IP pour se connecter à Office 365 a environ 2 000 clients par port réseau.
  
## <a name="why-use-nat"></a>Pourquoi utiliser la traduction d’adresses réseau (NAT) ?

À l’aide de NAT, des milliers de personnes sur un réseau d’entreprise peuvent « partager » les quelques adresses IP publiquement routables.
  
La plupart des réseaux d’entreprise utilisent un espace d’adressage IP privé (RFC1918). Un espace d’adressage IP est alloué par l’organisme IANA (Internet Assigned Numbers Authority). Il est destiné uniquement aux réseaux qui n’effectuent pas de routage entrant ou sortant directement avec Internet.
  
Pour fournir l’accès à Internet pour les appareils dans un espace d’adressage IP privé, les organisations utilisent des technologies de passerelle telles que des pare-feu et des proxys qui fournissent la traduction d’adresses réseau (NAT) ou les services (PAT) traduction d’adresse port. Ces passerelles rendre le trafic interne appareils Internet (y compris Office 365) semblent provenir d’une ou plusieurs adresses IP publiquement routables. Chaque connexion sortante à partir d’un périphérique interne se traduit par un port TCP de sources différents sur l’adresse IP publique. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Pourquoi avez-vous besoin ouvrir autant de connexions à Office 365 en même temps ?

Outlook peut ouvrir huit connexions ou plus (dans les cas où des compléments, des calendriers partagés, des boîtes aux lettres, etc. sont présents). Le nombre maximal de ports disponibles étant de 64 000 sur un appareil NAT Windows, plus de 8 000 utilisateurs peuvent se trouver derrière une adresse IP avant que les ports soient saturés. Prenez note que, si des clients utilisent des appareils non compatibles avec le système d’exploitation Windows pour la NAT, le nombre total de ports disponibles dépend de l’appareil NAT ou du logiciel utilisés. Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000. La disponibilité des ports est également influencée par d’autres facteurs, tels que le fait que Windows réserve 4 000 ports pour son propre usage, ce qui réduit le nombre total de ports disponibles à 60 000. D’autres applications telles qu’Internet Explorer peuvent également se connecter au même moment, ce qui nécessite des ports supplémentaires.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcul du nombre maximal de périphériques pris en charge derrière une adresse IP publique avec Office 365

Pour déterminer le nombre maximal de périphériques derrière une adresse IP publique, vous devez analyser le trafic réseau pour déterminer la consommation de ports pointe par client. En outre, un facteur de pointe doit être utilisé pour l’utilisation du port (au moins 4). 
  
 **Utilisez la formule suivante pour calculer le nombre de périphériques pris en charge par adresse IP :**
  
Maximum pris en charge les périphériques derrière une adresse IP publique = (64 000 - ports réservés) / (pic de consommation de ports + facteur de pointe)
  
 **Par exemple, si les éléments suivants ont la valeur trus :**
  
- **Ports réservés :** 4 000 pour le système d’exploitation 
    
- **Pic de consommation de ports :** 6 par appareil 
    
- **Facteur de pointe :** 4 
    
Ensuite, la valeur maximale périphériques pris en charge derrière une adresse IP publique = (64 000-4 000) / (6 + 4) = 6 000
  
Avec la version d’Office 365 pack, inclus dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou de novembre 2011 pour Microsoft Outlook 2010 ou d’une mise à jour ultérieur, le nombre de connexions à partir d’Outlook (à la fois Office Outlook 2007 avec le Service d’hébergement Pack 2 et Outlook 2010) pour Exchange peut être aussi peu que 2. Vous devez prendre en compte les différents systèmes d’exploitation, comportements de l’utilisateur, et ainsi de suite pour déterminer le nombre maximum et minimum des ports qui nécessite votre réseau à l’utilisation maximale.
  
Si vous souhaitez prendre en charge plusieurs périphériques derrière une adresse IP publique, suivez la procédure présentée pour évaluer le nombre maximal de périphériques pouvant être pris en charge :
  
Surveiller le trafic réseau pour déterminer la consommation de ports pointe par client. Vous devez recueillir ces données :
  
- À partir de plusieurs emplacements
    
- À partir de plusieurs appareils
    
- À plusieurs moments différents
    
Pour calculer le nombre maximal d'utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement, utilisez la formule précédente.
  
Il existe différentes méthodes de distribution de charge du client sur des adresses IP publiques supplémentaires. Stratégies disponibles varient selon les fonctionnalités de la solution de passerelle d’entreprise. La solution la plus simple consiste à votre espace d’adressage utilisateur de segment et statiquement « affecter » un nombre d’adresses IP pour chaque passerelle. Une autre solution offrent de nombreux périphériques de passerelle est la possibilité d’utiliser un pool d’adresses IP. L’avantage du pool d’adresses est qu’il est beaucoup plus dynamique et moins susceptibles d’exiger l’ajustement que votre base d’utilisateurs augmente.
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

