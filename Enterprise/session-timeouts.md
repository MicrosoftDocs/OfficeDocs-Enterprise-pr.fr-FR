---
title: Délais d’attente de session pour Office 365
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Délais d’attente de session sont utilisés pour équilibrer la sécurité et facilité d’accès dans les applications de client Office 365.
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540449"
---
# <a name="session-timeouts-for-office-365"></a>Délais d’attente de session pour Office 365

Durée de vie de session est une part importante de l’authentification pour Office 365 et un élément important dans l’équilibrage de la sécurité et le nombre de fois que les utilisateurs sont invités de leurs informations d’identification.
  
## <a name="session-times-for-office-365-services"></a>Durées de session pour les services Office 365

Lorsque les utilisateurs s’authentifient dans les applications mobiles ou les applications web Office 365, une session est établie. Pendant la durée de la session, les utilisateurs ne doivent s’authentifier à nouveau. Sessions peut expirer lorsque les utilisateurs sont inactives, lorsqu’ils ferment du navigateur ou un onglet, ou lorsque leur jeton d’authentification pour d’autres raisons telles que lorsque leur mot de passe réinitialisé arrive à expiration. Les services Office 365 ont des délais d’attente de session différent pour correspondre à l’utilisation classique de chaque service.
  
Le tableau suivant répertorie les durées de vie de session pour les services Office 365 :
  
|**Service Office 365**|**Délai d’expiration de session**|
|:-----|:-----|
|Centre d’administration Office 365  <br/> |Vous êtes invité à fournir des informations d’identification pour le centre d’administration toutes les 8 heures.  <br/> |
|SharePoint Online  <br/> |5 jours d’inactivité tant que les utilisateurs choisit **maintenir la connexion**. Si l’utilisateur accède à SharePoint Online à nouveau une fois au moins 24 heures se sont écoulées à partir de la connexion à précédente, la valeur de délai d’expiration est remises à 5 jours.<br/> |
|Outlook Web App  <br/> |6 heures.  <br/> Vous pouvez modifier cette valeur en utilisant le paramètre _ActivityBasedAuthenticationTimeoutInterval_ dans l’applet de commande [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Utilisé par les clients Office 2013 Windows avec l’authentification moderne est activée)  <br/> | Authentification moderne utilise des jetons d’accès et les jetons d’actualisation pour accorder l’accès utilisateur aux ressources Office 365 à l’aide d’Azure Active Directory. Un jeton d’accès est un jeton JSON Web fourni après une authentification réussie et valid pour 1 heure. Un jeton d’actualisation d’une durée de vie plu est également fourni. Expiration des jetons d’accès, les clients Office utilisent un jeton d’actualisation valide pour obtenir un jeton d’accès. Cet échange aboutit si l’authentification initiale de l’utilisateur est toujours valide.  <br/>  Jetons d’actualisation sont valides pendant 90 jours, et avec l’utilisation continue, ils peuvent être valides jusqu'à ce que révoqué.  <br/>  Actualiser les jetons peuvent invalidés par plusieurs événements tels que :  <br/>  Mot de passe de l’utilisateur a changé depuis le jeton d’actualisation a été émis.  <br/>  Un administrateur peut appliquer les stratégies d’accès conditionnel qui restreindre l’accès à la ressource que l’utilisateur tente d’accéder.  <br/> |
|SharePoint et OneDrive des applications mobiles pour Android, iOS et Windows 10  <br/> |La durée de vie par défaut pour le jeton d’accès est 1 heure. La durée d’inactivité maximale par défaut du jeton d’actualisation est 90 jours.<br/> [Pour plus d’informations sur les jetons et comment configurer la durée de vie des jetons](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Pour révoquer l’actualisation un jeton, vous pouvez réinitialiser le mot de passe Office 365  <br/> |
|Yammer avec connexion dans Office 365  <br/> |Durée de vie du navigateur. Si les utilisateurs fermez le navigateur et accéder Yammer dans une nouvelle fenêtre de navigateur, Yammer sera réauthentifier les avec Office 365. Si les utilisateurs utilisent des navigateurs tiers que les cookies de cache, il faudra pas réauthentifier lorsqu’ils rouvrez le navigateur.<br/> > [!NOTE]> Ceci est valide uniquement pour les réseaux à l’aide de connexion à Office 365 pour Yammer.           |
   

