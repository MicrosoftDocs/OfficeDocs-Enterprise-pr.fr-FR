---
title: Limites des ressources Microsoft 365
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
description: Dans cet article, vous trouverez des informations sur les limites des ressources pour les différentes applications de Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4d2e7987620891ddeac2c4fa08aaeb203f001f57
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606300"
---
# <a name="resource-limits"></a>Limites de ressources

Les limites des ressources sont appliquées à l’aide de quotas (limites) et de la limitation. Azure Active Directory (Azure AD) et les services individuels Microsoft 365 utilisent les deux. Les limites sont propres aux services et changent au fil du temps lorsque de nouvelles fonctionnalités sont ajoutées. Pour plus d’informations sur les limites actuelles pour les différents services, consultez les rubriques suivantes :

- [Limites et restrictions du service Azure AD](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [Limites d’Exchange Online](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Limites d’Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Limites et frontières des logiciels SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Limites de Skype entreprise](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [API REST Yammer et limites de débit](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Limites de taille de fichier dans Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

En plus de ces limites, plusieurs mécanismes de limitation sont utilisés dans Azure AD et Microsoft 365. La limitation au sein du service est particulièrement importante, étant donné que les ressources réseau dans les centres de données de Microsoft sont optimisées pour l’ensemble des clients qui utilisent les services. Les mécanismes de limitation sont les suivants :

- Azure AD et Microsoft 365 fonctionnalité de limitation au niveau de l’utilisateur, ce qui limite le nombre de transactions ou d’appels simultanés (par script ou code) qui peuvent être effectués par un seul utilisateur.
- Une stratégie de limitation PowerShell par défaut est attribuée à chaque client lors de la création du client. Ces paramètres affectent d’autres éléments, tels que le nombre maximal de sessions PowerShell simultanées pouvant être ouvertes par un administrateur unique.
- Chaque client Exchange Online a une stratégie de services Web Exchange (EWS) par défaut ajustée pour les opérations clientes EWS et la limitation qui s’applique à tous les clients Outlook.
