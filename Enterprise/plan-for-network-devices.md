---
title: Planifier les périphériques réseau qui se connectent aux services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Résumé : Décrit les éléments à prendre en compte pour la capacité réseau, les accélérateurs WAN et les périphériques d’équilibrage de charge qui sont utilisés pour se connecter à Office 365.'
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223066"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planifier les périphériques réseau qui se connectent aux services Office 365

 **Résumé** : Décrit les éléments à prendre en compte pour la capacité réseau, les accélérateurs WAN et les périphériques d’équilibrage de charge qui sont utilisés pour se connecter à Office 365.
  
Matériel réseau peut-être comporter des limites du nombre de sessions simultanées qui sont prises en charge. Pour les organisations ayant plus de 2 000 utilisateurs, nous vous recommandons de surveiller les leurs périphériques réseau pour vous assurer qu’ils sont capables de traiter le trafic du service Office 365 supplémentaire. SNMP Simple Network Management Protocol () logiciels de surveillance peuvent vous aider à effectuer cette opération.

||
|:-----|
| Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).|

Les paramètres de proxy Internet sortant également affectent la connectivité aux services Office 365 pour les applications clientes sur site. Vous devez également configurer vos périphériques de proxy réseau pour autoriser les connexions pour les applications et les URL de services de cloud Microsoft. Chaque organisation est différente. Pour avoir une idée de la façon dont Microsoft gère ce processus et la quantité de bande passante que nous provisionner, [Lisez l’étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Le Skype suivante pour les articles d’aide Business ont plus d’informations sur Skype pour les paramètres d’entreprise :
  
- [Résolution des problèmes de Skype pour Business erreurs de connexion (administrateurs)](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [Vous ne pouvez pas vous connecter à Skype pour les entreprises, ou certaines fonctionnalités ne fonctionnent pas, car un pare-feu local bloque la connexion](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Alors que la plupart de ces paramètres sont Skype pour spécifiques à l’entreprise, les instructions générales sur la configuration du réseau sont utile pour tous les services Office 365.
  
## <a name="determining-network-capacity"></a>Détermination de la capacité réseau

Chaque périphérique réseau existant sur une connexion présente une limite de capacité, notamment les cartes réseau de serveur et de client, les routeurs, les commutateurs et les concentrateurs qui les relient. Une capacité réseau adéquate signifie qu'aucun de ces périphériques réseau n'est saturé. Il est essentiel de contrôler l'activité réseau pour s'assurer que les charges réelles sur chaque périphérique réseau sont inférieures à leur capacité maximale. La capacité réseau a une incidence sur les performances des périphériques proxy.
  
Dans la plupart des cas, la bande passante Internet définit la limite pour la quantité de trafic. Faibles performances pendant les heures de pointe du trafic est probablement dû à une utilisation excessive de la liaison Internet. Cette situation s’applique également à un scénario de succursale, où les ordinateurs de serveur proxy branch office sont connectés au périphérique proxy aux sièges sociaux de la branche via une liaison lente de réseau étendu (WAN).
  
Pour tester la capacité du réseau, surveiller l’activité du réseau sur l’interface réseau de proxy. S’il est plus de 75 % de la bande passante maximale d’une interface réseau, envisagez d’augmenter la bande passante de l’infrastructure réseau qui est insuffisant. Ou bien, envisagez d’utiliser des fonctionnalités avancées, telles que la compression HTTP.
  
## <a name="wan-accelerators"></a>Accélérateurs de réseau étendu

Si votre organisation utilise des équipements de proxy de l’accélération de réseau (étendu WAN) étendu, vous pouvez rencontrer des problèmes lorsque vous accédez aux services Office 365. Vous devrez peut-être optimiser votre réseau ou les périphériques pour vous assurer que vos utilisateurs une expérience cohérente lorsque vous accédez à Office 365. Par exemple, les services Office 365 chiffrer certains contenus Office 365 et l’en-tête TCP. Votre appareil ne peut pas être en mesure de gérer ce type de trafic.
  
Lire notre déclaration de prise en charge sur [contrôleur d’optimisation WAN à l’aide de ou périphériques/Inspection du trafic avec Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Périphériques d'équilibrage de charge matérielle et logicielle

Pour répartir les demandes adressées à vos serveurs ADFS (Active Directory Federation Services) ou serveurs Exchange hybrides, votre organisation doit utiliser une solution d'équilibrage de la charge matérielle (HLP) ou d'équilibrage de la charge réseau (NLB). Les périphériques d'équilibrage de la charge contrôlent le trafic réseau vers les serveurs locaux. Ces serveurs sont essentiels pour garantir la disponibilité de l'authentification unique et du déploiement Exchange hybride.
  
Nous proposons une solution d’équilibrage de charge réseau basé sur logiciel intégrée à Windows Server. Office 365 prend en charge cette solution pour équilibrer la charge.
  
## <a name="firewalls-and-proxies"></a>Pare-feu et des proxys

Pour plus d’informations sur la configuration des pare-feu et des proxys pour se connecter à Office 365, lisez les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), la [connectivité réseau vers Office 365](network-connectivity.md)et [points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) pour en savoir plus sur les périphériques et sélection de circuits.
  
## <a name="see-also"></a>Voir aussi

[Conseillers de déploiement pour les services Office 365](deployment-advisors-for-office-365.md)
