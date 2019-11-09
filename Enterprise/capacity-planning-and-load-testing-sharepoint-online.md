---
title: Planification de la capacité et test de charge SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Cet article explique comment déployer sur SharePoint Online sans effectuer de tests de charge traditionnels, car il n’est pas autorisé.
ms.openlocfilehash: 13e71343aa5ec823003791d99e227fc835117b62
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077877"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planification de la capacité et test de charge SharePoint Online
Cet article explique comment déployer sur SharePoint Online sans test de charge classique, étant donné que le test de charge n’est pas autorisé sur SharePoint Online. SharePoint Online est un service Cloud et les capacités de chargement, l’intégrité et l’équilibre global de la charge dans le service sont gérées par Microsoft.
  
La meilleure approche pour garantir le succès du lancement de votre site est de suivre les principes, pratiques et recommandations de base qui sont mis en évidence dans le déploiement de la [planification du lancement de votre portail](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Vue d’ensemble de la planification de la capacité dans SharePoint Online 
L’un des principaux avantages de SharePoint Online par rapport à un déploiement sur site est l’élasticité du nuage, ainsi que les optimisations pour les utilisateurs dans les régions distribuées. Notre environnement à grande échelle étant configuré pour traiter des millions d’utilisateurs tous les jours, il est important de gérer la capacité efficacement en équilibrant et en étendant les batteries de serveurs.
  
Bien que la croissance soit souvent imprévisible pour un seul client dans une batterie de serveurs, la somme agrégée des demandes est prévisible dans le temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier une expansion future.
  
Afin d’utiliser efficacement la capacité et de faire face à une croissance inattendue, dans n’importe quelle batterie de serveurs, l’automatisation suit et surveille les différents éléments du service. Plusieurs mesures sont utilisées, avec l’une des principales charges de processeur, qui est utilisée comme signal pour les serveurs frontaux à l’adaptation. De plus, nous vous recommandons d’utiliser une [approche en phase/vague](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out), car les environnements SQL évoluent en fonction de la charge et de la croissance au fil du temps, et le suivi des phases et des vagues permet une distribution correcte de cette charge et de cette croissance. 

La capacité consiste à ajouter davantage de matériel en continu, mais elle concerne également la gestion et le contrôle de cette capacité afin de s’assurer qu’elle traite des demandes de chargement valides. Nous recommandons aux clients de suivre les recommandations pour s’assurer qu’ils bénéficient d’une expérience optimale. Cela signifie également que nous disposons de modèles et de contrôles de limitation en place pour garantir que nous n’autorisons pas le comportement « abusif » dans le service. Bien que tous les comportements « incorrects » ne soient pas intentionnels, nous devons nous assurer que nous limitons l’effet de ce comportement. Pour plus d’informations sur la limitation et sur la façon de l’éviter, consultez la rubrique [Comment éviter d’être limité](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Pourquoi ne puis-je pas charger SharePoint Online
Dans les environnements locaux, le test de charge permet de valider l’hypothèse d’envergure et de trouver le point de fin d’une batterie de serveurs ; en le saturant avec Load. 

Avec SharePoint Online, nous devons effectuer des opérations différemment, car l’évolution est relativement fluide et ajuste, limite et contrôle la charge, en fonction de certains heuristiques. Dans ce cas, nous devons protéger tous les clients de la même batterie de serveurs, afin de limiter automatiquement les tests de charge. Si, en revanche, vous tentez de charger le test, en dehors de la limitation, vous recevrez des résultats délimités et potentiellement trompeurs, car la batterie de serveurs que vous avez testée aujourd’hui aura probablement des changements d’envergure pendant la période de test ou dans les heures après le test, comme les actions d’échelle et d’équilibrage de batterie de serveurs sont effectuées sur une base continue.

Au lieu de tenter de charger SharePoint test en tant que service, il est préférable de suivre les pratiques recommandées et de suivre les conseils de [création, de lancement et de maintenance d’un portail sain](https://go.microsoft.com/fwlink/?linkid=2105838) .
