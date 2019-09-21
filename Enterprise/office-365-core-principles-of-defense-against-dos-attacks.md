---
title: Principes de base de la protection Office 365 contre les attaques par déni de service
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Utilisation des principes de base de l’absorption, de la détection et de l’atténuation dans sa défense contre les attaques par déni de service (DoS).
ms.openlocfilehash: abfb0efda679930c22d9ce87709aded9a2880f06
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067398"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a>Principes fondamentaux de défense contre les attaques par déni de service

Les trois principes fondamentaux de la défense contre les attaques DoS sur le réseau sont l’absorption, la détection et l’atténuation. L’absorption se produit avant la détection et la détection a lieu avant l’atténuation. L’absorption est la meilleure défense contre une attaque DoS. Si l’attaque ne peut pas être détectée, elle ne peut pas être atténuée. Toutefois, si même la plus petite attaque de refus de service ne peut pas être absorbée, les services ne seront pas en mesure de survivre suffisamment longtemps pour que l’attaque soit détectée.

La plupart des organisations n’ont pas la possibilité économique d’acheter une capacité excessive pour absorber les attaques par déni de service, car cela nécessite un investissement considérable en matière de technologies et de compétences techniques. Cela met en évidence l’un des avantages en matière de sécurité liés à l’utilisation des services de Cloud Computing Microsoft. La grande ampleur des services Microsoft offre une protection réseau puissante aux clients du nuage de façon rentable. Mais même à grande échelle, il doit y avoir un équilibre entre l’absorption, la détection et l’atténuation. Pour connaître cet équilibre, Microsoft étudie les taux de croissance des attaques pour estimer le volume de Microsoft à absorber.

La détection est un jeu de chat et de souris. Vous devez constamment Rechercher de nouvelles méthodes d’attaque et essayer de contrecarrer vos systèmes. Detect-> mitigation-> détecter > minimisation, etc., est un État perpétuel, permanent, qui continue indéfiniment.

## <a name="defending-against-dos-attacks"></a>Défense contre les attaques DoS

Pour être en mesure de vous défendre contre une attaque DoS, la détection précoce est essentielle. En détectant une attaque avant que le système ne soit submergé, les défenseurs peuvent exécuter un plan de réponse.

La formule suivante permet de se rapprocher du temps nécessaire à l’impact d’une attaque DoS :

   **Capacité maximale (en octets/s)/taux de croissance (en octets/s) = temps d’impact (en octets/s)**

Si le délai de détection a lieu après l’impact, il est probable que l’attaque de refus de service se produise. Si le délai de détection a lieu avant l’impact, les services attaqués doivent rester en ligne et accessibles si des stratégies de minimisation sont utilisées. Ainsi, il y a deux choses à faire pour vous défendre contre les attaques de refus de déni de compte :

- Augmentation de la capacité pour augmenter le plafond de la capacité maximale (qui, à son tour, offre plus de temps pour détecter une attaque); des
- Réduisez le temps de détection.

Une augmentation de la capacité a un impact fiscal direct. Microsoft recommande aux clients de développer au moins une capacité d’absorption de base pour s’assurer qu’ils peuvent survivre à un certain niveau d’attaques DoS. La capacité d’absorption réelle varie selon le client et le client, car chaque client a ses propres seuils d’exposition, de risque et de dépenses financières. Pour des raisons économiques, les investissements en matière de recherche et de temps pour réduire le temps de détection sont généralement la défense la plus économique.
