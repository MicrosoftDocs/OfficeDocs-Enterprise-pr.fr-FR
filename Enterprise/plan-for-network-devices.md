---
title: Planifier les périphériques réseau qui se connectent aux services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Résumé : décrit les considérations relatives à la capacité réseau, aux accélérateurs de réseau étendu et aux périphériques d’équilibrage de charge utilisés pour se connecter à Office 365.'
ms.openlocfilehash: 5015a146f92a32bd0200088517b6673ae00f8f64
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998633"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planifier les périphériques réseau qui se connectent aux services Office 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*
  
Certains matériels réseau peuvent avoir des limitations quant au nombre de sessions simultanées prises en charge. Pour les organisations qui possèdent plus de 2 000 utilisateurs, nous recommandons qu’ils surveillent leurs périphériques réseau pour s’assurer qu’ils sont capables de gérer le trafic de service 365 Office supplémentaire. Le logiciel de surveillance SNMP (simple Network Management Protocol) peut vous aider à effectuer cette opération.

||
|:-----|
| Cet article fait partie de la [planification réseau et du réglage des performances pour Office 365](https://aka.ms/tune).|

Les paramètres de proxy Internet sortants en local affectent également la connectivité aux services Office 365 pour vos applications clientes. Vous devez également configurer vos périphériques de proxy réseau pour autoriser les connexions pour les applications et les URL des services de Cloud Computing Microsoft. Chaque organisation est différente. Pour obtenir une idée de la façon dont Microsoft gère ce processus et de la quantité de bande passante que nous approvisionnez, [Lisez l’étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Les articles suivants de l’aide de Skype entreprise contiennent des informations supplémentaires sur les paramètres de Skype entreprise :
  
- [Dépannage des erreurs de connexion Skype entreprise Online pour les administrateurs](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Vous ne pouvez pas vous connecter à Skype entreprise, ou certaines fonctionnalités ne fonctionnent pas, car un pare-feu sur site bloque la connexion.](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Bien que la plupart de ces paramètres soient spécifiques à Skype entreprise, les conseils généraux sur la configuration du réseau sont utiles pour tous les services Office 365.
  
## <a name="determining-network-capacity"></a>Détermination de la capacité réseau

Chaque périphérique réseau qui existe sur une connexion a sa limite de capacité. Ces périphériques incluent les cartes réseau client et serveur, les routeurs, les commutateurs et les concentrateurs qui les interconnectent. Une capacité réseau adéquate signifie qu’aucun d’entre eux n’est saturé. La surveillance de l’activité réseau est essentielle pour garantir que les charges réelles sur tous les périphériques réseau sont inférieures à leur capacité maximale. La capacité réseau affecte les performances des périphériques proxy.
  
Dans la plupart des cas, la bande passante de connexion Internet définit la limite pour la quantité de trafic. Des performances médiocres pendant les heures de pointe du trafic sont probablement dues à une utilisation excessive de la liaison Internet. Cette situation s’applique également à un scénario de succursale, où les ordinateurs proxy de succursale sont connectés au périphérique proxy au siège de la succursale sur un lien de réseau étendu lent.
  
Pour tester la capacité du réseau, surveillez l’activité réseau sur l’interface réseau proxy. S’il s’agit de plus de 75% de la bande passante maximale de n’importe quelle interface réseau, envisagez d’augmenter la bande passante de l’infrastructure réseau qui est inadéquate. Vous pouvez également envisager d’utiliser des fonctionnalités avancées, telles que la compression HTTP.
  
## <a name="wan-accelerators"></a>Accélérateurs de réseau étendu

Si votre organisation utilise des appliances de proxy d’accélération WAN (large Area Network), vous pouvez rencontrer des problèmes lorsque vous accédez aux services Office 365. Vous devrez peut-être optimiser votre ou vos périphériques réseau pour vous assurer que vos utilisateurs bénéficient d’une expérience cohérente lors de l’accès à Office 365. Par exemple, les services Office 365 chiffrent du contenu Office 365 et l’en-tête TCP. Il se peut que votre appareil ne puisse pas gérer ce type de trafic.
  
Lisez notre déclaration de support concernant [l’utilisation du contrôleur d’optimisation WAN ou des appareils de trafic/inspection avec Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Dispositifs d’équilibrage de charge matériels et logiciels

Votre organisation doit utiliser un programme d’équilibrage de la charge matérielle (charge matérielle) ou une solution d’équilibrage de la charge réseau (NLB) pour distribuer les demandes à vos serveurs AD FS (Active Directory Federation Services) et/ou à vos serveurs hybrides Exchange. Les périphériques d’équilibrage de charge contrôlent le trafic réseau vers les serveurs locaux. Ces serveurs sont essentiels pour garantir la disponibilité de l’authentification unique et du déploiement hybride Exchange.
  
Nous fournissons une solution NLB basée sur des logiciels intégrée à Windows Server. Office 365 prend en charge cette solution pour mettre en œuvre l’équilibrage de charge.
  
## <a name="firewalls-and-proxies"></a>Pare-feu et proxys

Pour plus d’informations sur la configuration des pare-feu et des proxys pour se connecter à Office 365, consultez la rubrique [Managing office 365 Endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Evaluation Office 365 network connectivity](assessing-network-connectivity.md)et [Office 365 Endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) pour en savoir plus sur les appareils et la sélection de circuits.
  
## <a name="see-also"></a>Voir aussi

[Guides de configuration pour les services Office 365](setup-guides-for-office-365.md)

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
