---
title: Délais d’expiration de la session pour Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Les délais d’expiration des sessions sont utilisés pour équilibrer la sécurité et faciliter l’accès dans les applications clientes Microsoft 365.
ms.openlocfilehash: d439d36a3a67914658098e757b916dcf110b1df4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998156"
---
# <a name="session-timeouts-for-microsoft-365"></a>Délais d’expiration de la session pour Microsoft 365

La durée de vie des sessions est un élément important de l’authentification pour Microsoft 365 et constitue un élément important dans l’équilibrage de la sécurité et le nombre de fois que les utilisateurs sont invités à entrer leurs informations d’identification.
  
## <a name="session-times-for-microsoft-365-services"></a>Temps de session pour les services Microsoft 365

Lorsque les utilisateurs s’authentifient dans l’une des applications Web ou des applications mobiles Microsoft 365, une session est établie. Pendant la durée de la session, les utilisateurs n’ont pas besoin de s’authentifier à nouveau. Les sessions peuvent expirer lorsque les utilisateurs sont inactifs, lorsqu’ils ferment le navigateur ou l’onglet, ou lorsque leur jeton d’authentification expire pour d’autres raisons, comme lorsque leur mot de passe a été réinitialisé. Les services Microsoft 365 ont des délais d’attente de session différents qui correspondent à l’utilisation classique de chaque service.
  
Le tableau suivant répertorie les durées de vie des sessions pour les services Microsoft 365 :
  
|**Service Microsoft 365**|**Délai d’expiration de session**|
|:-----|:-----|
|Centre d’administration Microsoft 365  <br/> |Vous êtes invité à fournir des informations d’identification pour le centre d’administration toutes les 8 heures.  <br/> |
|SharePoint Online  <br/> |5 jours d’inactivité tant que l’utilisateur choisit **maintenir la connexion**. Si l’utilisateur accède à nouveau à SharePoint Online après 24 heures ou plus, la valeur de délai d’expiration est réinitialisée à 5 jours.  <br/> |
|Outlook Web App  <br/> |6 heures.  <br/> Vous pouvez modifier cette valeur à l’aide du paramètre _ActivityBasedAuthenticationTimeoutInterval_ de la cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Utilisé par les clients Windows 2013 avec l’authentification moderne activée)  <br/> | L’authentification moderne utilise des jetons d’accès et actualise les jetons pour accorder aux utilisateurs l’accès aux ressources Microsoft 365 à l’aide d’Azure Active Directory. Un jeton d’accès est un jeton Web JSON fourni après une authentification réussie pendant 1 heure. Un jeton d’actualisation avec une durée de vie plus longue est également fourni. Lorsque les jetons d’accès expirent, les clients Office utilisent un jeton d’actualisation valide pour obtenir un nouveau jeton d’accès. Cet échange réussit si l’authentification initiale de l’utilisateur est toujours valide.  <br/>  Les jetons d’actualisation sont valides pendant 90 jours, et avec une utilisation continue, ils peuvent être valides jusqu’à leur révocation.  <br/>  Les jetons d’actualisation peuvent être invalidés par plusieurs événements, tels que :  <br/>  Le mot de passe de l’utilisateur a été modifié depuis l’émission du jeton d’actualisation.  <br/>  Un administrateur peut appliquer des stratégies d’accès conditionnel qui restreignent l’accès à la ressource à laquelle l’utilisateur tente d’accéder.  <br/> |
|Applications mobiles SharePoint et OneDrive pour Android, iOS et Windows 10  <br/> |La durée de vie par défaut du jeton d’accès est de 1 heure. Le temps d’inactivité maximal par défaut du jeton d’actualisation est de 90 jours.  <br/> [En savoir plus sur les jetons et sur la configuration de la durée de vie des jetons](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Pour révoquer le jeton d’actualisation, vous pouvez réinitialiser le mot de passe Microsoft 365 de l’utilisateur.  <br/> |
|Yammer avec connexion Microsoft 365  <br/> |Durée de vie du navigateur. Si les utilisateurs ferment le navigateur et accèdent à Yammer dans un nouveau navigateur, Yammer les authentifie de nouveau à l’aide de Microsoft 365. Si les utilisateurs utilisent des navigateurs tiers qui cachent les cookies, ils n’ont peut-être pas besoin de s’authentifier à nouveau lors de la réouverture du navigateur.  <br/> > [!NOTE]> ceci n’est valide que pour les réseaux utilisant la connexion Microsoft 365 pour Yammer.           |
   

