---
title: Contrôles d’isolation Office 365
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
description: 'Résumé : explication des contrôles d’isolation dans Office 365.'
ms.openlocfilehash: 87317d753198b50ce360640c94f042adf27ed06e
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067367"
---
# <a name="office-365-isolation-controls"></a>Contrôles d’isolation Office 365 

Microsoft travaille en continu pour s’assurer que l’architecture mutualisée d’Office 365 prend en charge la sécurité au niveau de l’entreprise, la confidentialité, la confidentialité, l’intégrité, les [normes](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)locales, internationales et de disponibilité. L’échelle et l’étendue des services fournis par Microsoft rendent difficile et non rentable la gestion d’Office 365 avec une interaction humaine importante. Les services Office 365 sont fournis par le biais de plusieurs centres de données répartis dans le monde entier, chacun étant très automatisé avec peu d’opérations exigeant une touche humaine ou n’importe quel accès au contenu client. Notre équipe prend en charge ces services et centres de données à l’aide d’outils automatisés et d’accès à distance hautement sécurisé. Pour obtenir des informations détaillées sur la façon dont les services à grande échelle sont utilisés dans Office 365, voir [une présentation en arrière-plan de office 365 pour les professionnels de l’informatique](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202).

Office 365 est composé de plusieurs services qui fournissent des fonctionnalités métier importantes et contribuent à l’intégralité de l’expérience d’Office 365. Chacun de ces services est autonome et est conçu pour s’intégrer les uns avec les autres.

Office 365 est conçu selon les principes suivants :

 - ** [Architecture orientée service](https://msdn.microsoft.com/library/aa480021.aspx):** conception et développement de logiciels sous la forme de services interopérables fournissant une fonctionnalité métier bien définie.
 - **[Assurance de sécurité opérationnelle](http://www.microsoft.com/download/details.aspx?id=40872):** infrastructure qui comprend les connaissances acquises par le biais de différentes fonctionnalités propres à Microsoft, y compris le [cycle de vie de développement de sécurité](https://www.microsoft.com/sdl/default.aspx)Microsoft, la [sécurité Microsoft Response Center](https://technet.microsoft.com/library/dn440717.aspx)et sensibilisation approfondie du paysage des menaces Cybersecurity.

Les services Office 365 interagissent les uns avec les autres, mais sont conçus et implémentés de sorte qu’ils puissent être déployés et exploités en tant que services autonomes, indépendamment les uns des autres. Microsoft isole les responsabilités et domaines de responsabilité pour Office 365 afin de réduire les possibilités de modification non autorisée ou involontaire des ressources de l’organisation. Les équipes Office 365 disposent de rôles définis dans le cadre d’un mécanisme de contrôle d’accès basé sur un rôle complet.

## <a name="customer-content-isolation"></a>Isolation du contenu client

Tout le contenu client d’un client est isolé des autres clients et des opérations et des données système utilisées dans la gestion d’Office 365. Plusieurs formes de protection sont mises en œuvre partout dans Office 365 afin de réduire le risque de compromission d’un service ou d’une application Office 365. Plusieurs formes de protection empêchent également l’accès non autorisé aux informations des clients ou au système Office 365 lui-même.

Pour plus d’informations sur la façon dont Microsoft implémente l’isolation logique des données client dans Office 365, consultez la rubrique [isolation du client dans office 365](office-365-tenant-isolation-overview.md).
