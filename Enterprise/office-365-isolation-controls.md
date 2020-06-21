---
title: Contrôles d’isolation Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: 'Résumé : Expliquez les contrôles d’isolation au sein de Microsoft 365.'
ms.openlocfilehash: da26bb6a41c97a16865bfdd5bdf6aada2069f7fe
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774909"
---
# <a name="microsoft-365-isolation-controls"></a>Contrôles d’isolation Microsoft 365 

Microsoft travaille en continu pour s’assurer que l’architecture mutualisée de Microsoft 365 prend en charge la sécurité au niveau de l’entreprise, la confidentialité, la confidentialité, l’intégrité, les [normes](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)locales, internationales et de disponibilité. L’échelle et l’étendue des services fournis par Microsoft rendent difficile et non économique la gestion de Microsoft 365 avec une interaction humaine importante. Les services Microsoft 365 sont fournis par le biais de plusieurs centres de données répartis dans le monde entier, chacun étant très automatisé avec peu d’opérations exigeant une touche humaine ou n’importe quel accès au contenu client. Notre équipe prend en charge ces services et centres de données à l’aide d’outils automatisés et d’accès à distance hautement sécurisé. 

Microsoft 365 est composé de plusieurs services qui fournissent des fonctionnalités métier importantes et contribuent à l’expérience complète de Microsoft 365. Chacun de ces services est autonome et est conçu pour s’intégrer les uns avec les autres.

Microsoft 365 est conçu selon les principes suivants :

 - ** [Architecture orientée service](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** conception et développement de logiciels sous la forme de services interopérables fournissant une fonctionnalité métier bien définie.
 - **[Assurance de sécurité opérationnelle](https://www.microsoft.com/download/details.aspx?id=40872):** infrastructure qui comprend les connaissances acquises par le biais de différentes fonctionnalités propres à Microsoft, y compris le [cycle de vie de développement](https://www.microsoft.com/sdl/default.aspx)de la sécurité Microsoft, le centre de réponse à la [sécurité Microsoft](https://technet.microsoft.com/library/dn440717.aspx)et une connaissance approfondie du paysage des menaces Cybersecurity.

Les services Microsoft 365 interagissent les uns avec les autres, mais ils sont conçus et mis en œuvre de sorte qu’ils puissent être déployés et exploités en tant que services autonomes, indépendamment les uns des autres. Microsoft isole les responsabilités et domaines de responsabilité pour Microsoft 365 afin de réduire les possibilités de modification non autorisée ou involontaire des ressources de l’organisation. Microsoft 365 teams ont des rôles définis dans le cadre d’un mécanisme de contrôle d’accès basé sur un rôle complet.

## <a name="customer-content-isolation"></a>Isolation du contenu client

Tout le contenu client d’un client est isolé des autres clients et des opérations et des données système utilisées dans la gestion de Microsoft 365. Plusieurs formes de protection sont mises en œuvre tout au long de Microsoft 365 afin de réduire le risque de compromission d’un service ou d’une application Microsoft 365. Plusieurs formes de protection empêchent également l’accès non autorisé aux informations des clients ou du système Microsoft 365 lui-même.

Pour plus d’informations sur la façon dont Microsoft implémente l’isolation logique des données client dans Microsoft 365, voir [isolation des clients dans microsoft 365](office-365-tenant-isolation-overview.md).
