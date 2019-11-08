---
title: Limites des ressources Office 365
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
description: 'Résumé : informations sur les limites de ressources pour les différentes applications dans Office 365.'
ms.openlocfilehash: 7ccbf2bdfe359dd44a0b03dcf6e2aed8d5daedbe
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035484"
---
# <a name="resource-limits"></a>Limites de ressources

Les limites des ressources sont appliquées à l’aide de quotas (limites) et de la limitation. Azure Active Directory et les services Office 365 individuels utilisent les deux. Les limites sont propres aux services et changent au fil du temps lorsque de nouvelles fonctionnalités sont ajoutées. Pour plus d’informations sur les limites actuelles pour les différents services, consultez les rubriques suivantes :

- [Limites et restrictions du service Azure Active Directory](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Limites d’Exchange Online](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Limites d’Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Limites et frontières des logiciels SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Limites de Skype entreprise](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [API REST Yammer et limites de débit](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Limites de taille de fichier dans Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

En plus de ces limites, plusieurs mécanismes de limitation sont utilisés dans Azure Active Directory et Office 365. La limitation au sein du service est particulièrement importante, étant donné que les ressources réseau dans les centres de données de Microsoft sont optimisées pour l’ensemble des clients qui utilisent les services. Les mécanismes de limitation sont les suivants :

- Azure Active Directory et Office 365 fonctionnalité de limitation au niveau de l’utilisateur, ce qui limite le nombre de transactions ou d’appels simultanés (par script ou code) qui peuvent être exécutés par un seul utilisateur.
- Une stratégie de limitation PowerShell par défaut est attribuée à chaque client lors de la création du client. Ces paramètres affectent d’autres éléments, tels que le nombre maximal de sessions PowerShell simultanées pouvant être ouvertes par un administrateur unique.
- Chaque client Exchange Online a une stratégie de services Web Exchange (EWS) par défaut ajustée pour les opérations clientes EWS et la limitation qui s’applique à tous les clients Outlook.
