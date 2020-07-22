---
title: Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Résumé : fournit des informations sur la façon de rapprocher le nombre correct de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT).'
ms.openlocfilehash: d1f6762fcb21e6c310c790f6b235e5a51db4b1f2
ms.sourcegitcommit: 35655e2b098e46822c14d98583cc47b87516a629
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "45201608"
---
# <a name="nat-support-with-office-365"></a>Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Auparavant, vous avez indiqué que le nombre maximal de clients Exchange à utiliser par adresse IP pour se connecter à Office 365 était environ 2 000 clients par port réseau.
  
## <a name="why-use-nat"></a>Pourquoi utiliser le protocole NAT ?

À l’aide de l’interface NAT, des milliers de personnes sur un réseau d’entreprise peuvent « partager » quelques adresses IP routables publiquement.
  
La plupart des réseaux d’entreprise utilisent l’espace d’adressage IP privé (RFC1918). L’espace d’adressage privé est alloué par l’IANA (Internet Assigned Numbers Authority) et destiné uniquement aux réseaux qui ne sont pas routés directement vers et depuis l’Internet global.
  
Pour fournir un accès Internet aux appareils sur un espace d’adressage IP privé, les organisations utilisent des technologies de passerelle telles que les pare-feu et les proxys qui fournissent des services de traduction d’adresses réseau (NAT) ou de traduction d’adresse de port (PAT). Ces passerelles rendent le trafic à partir d’appareils internes vers Internet (y compris Office 365) semblent provenir d’une ou de plusieurs adresses IP routables publiquement. Chaque connexion sortante à partir d’un périphérique interne se traduit par un port TCP source différent sur l’adresse IP publique. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Pourquoi avez-vous besoin d’un grand nombre de connexions ouvertes dans Office 365 ?

Outlook peut ouvrir au moins huit connexions (dans les situations où il y a des compléments, des calendriers partagés, des boîtes aux lettres, etc.). Étant donné qu’il y a un maximum de 64 000 ports disponibles sur un périphérique NAT basé sur Windows, il peut y avoir un maximum de 8 000 utilisateurs derrière une adresse IP pour que les ports soient épuisés. Notez que si les clients utilisent des appareils non-Windows pour la traduction d’adresses réseau (NAT), le total des ports disponibles dépend du périphérique ou du logiciel NAT utilisé. Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000. La disponibilité des ports est également affectée par d’autres facteurs tels que le fait que Windows limite les ports 4 000 pour sa propre utilisation, ce qui réduit le nombre total de ports disponibles à 60 000. Il peut y avoir d’autres applications, telles qu’Internet Explorer, qui peuvent se connecter en même temps, ce qui nécessite des ports supplémentaires.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcul du nombre maximal d’appareils pris en charge derrière une même adresse IP publique avec Office 365

Pour déterminer le nombre maximal d’appareils derrière une seule adresse IP publique, vous devez surveiller le trafic réseau afin de déterminer la consommation de ports maximale par client. De plus, un facteur de pic doit être utilisé pour l’utilisation des ports (4 minimum). 
  
 **Utilisez la formule suivante pour calculer le nombre de périphériques pris en charge par adresse IP :**
  
Nombre maximal d’appareils pris en charge derrière une même adresse IP publique = (64 000-Restricted ports)/(pic de consommation de ports + facteur de pic)
  
 **Par exemple, si les éléments suivants étaient vrais :**
  
- **Ports restreints :** 4 000 pour le système d’exploitation

- **Consommation de ports PIC :** 6 par appareil

- **Facteur de crête :** 4

Ensuite, le nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000-4000)/(6 + 4) = 6 000
  
Avec la version du pack d’hébergement Office 365, incluse dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou 2011 pour Microsoft Outlook 2010, ou une mise à jour ultérieure, le nombre de connexions à partir d’Outlook (Office Outlook 2007 avec Service Pack 2 et Outlook 2010) vers Exchange peut être de 2. Vous devez prendre en facteur les différents systèmes d’exploitation, comportements d’utilisateur, etc., pour déterminer le nombre minimal et maximal de ports requis par votre réseau au niveau maximal.
  
Si vous souhaitez prendre en charge un plus grand nombre d’appareils derrière une même adresse IP publique, suivez les étapes décrites pour évaluer le nombre maximal d’appareils pouvant être pris en charge :
  
Surveillez le trafic réseau pour déterminer la consommation de ports maximale par client. Vous devez collecter ces données :
  
- À partir de plusieurs emplacements
    
- À partir de plusieurs appareils
    
- À plusieurs reprises
    
Utilisez la formule précédente pour calculer le nombre maximal d’utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement.
  
Il existe différentes méthodes de répartition de la charge client sur des adresses IP publiques supplémentaires. Les stratégies disponibles dépendent des fonctionnalités de la solution de passerelle d’entreprise. La solution la plus simple consiste à segmenter votre espace d’adressage utilisateur et à « assigner » de façon statique des adresses IP à chaque passerelle. La possibilité d’utiliser un pool d’adresses IP constitue une autre alternative offerte par de nombreux périphériques de passerelle. L’avantage du pool d’adresses est qu’il est plus dynamique et moins susceptible de nécessiter des ajustements au fur et à mesure que votre base d’utilisateurs se développe.
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
