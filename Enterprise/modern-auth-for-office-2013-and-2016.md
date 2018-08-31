---
title: Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016
ms.author: sirkkuw
author: Sirkkuw
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
description: Découvrez comment Office 365 moderne fonctionne l’authentification différemment pour Office 2013 et les applications clientes de 2016.
ms.openlocfilehash: a9b6e2dabec9fb59f5fd7f60508dcbc6fe840cfb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540490"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016

Lisez cet article pour découvrir comment Office 2013 et les applications clientes Office 2016 utilisent les fonctionnalités d’authentification moderne en fonction de la configuration d’authentification sur le client Office 365 pour Exchange Online, SharePoint Online et Skype pour Business Online.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilité de l’authentification pour les services Office 365 moderne

Pour les services Office 365, l’état par défaut d’authentification moderne est :
  
- **Activé pour Exchange Online par défaut.** Consultez la rubrique [Activer ou désactiver l’authentification moderne dans Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) pour l’activer ou désactiver. 
    
- **Activé pour SharePoint Online par défaut.** 
    
- **Activé pour Skype pour Business Online par défaut.** Consultez la rubrique [Activer les Skype pour Business Online pour l’authentification moderne ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)pour l’activer ou désactiver.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportement de connexion des applications de client Office

Les applications client Office 2013 prend en charge l’authentification héritée par défaut. Hérité signifie qu’elles prennent en charge soit connexion dans Microsoft Online Compagnon ou base d’authentification. Afin que ces clients à utiliser les fonctionnalités d’authentification moderne, les fenêtres client a ont les clés de Registre à définir. Pour plus d’informations, voir [Activer l’authentification moderne pour Office 2013 sur les périphériques Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Lisez [comment utiliser l’authentification moderne (ADAL) avec Skype pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=785431) pour découvrir comment il fonctionne avec Skype pour les entreprises. 
  
Clients Office 2016 prennent en charge l’authentification moderne par défaut, et aucune action n’est nécessaire pour le client à utiliser ces nouveaux flux. Toutefois, une action explicite est nécessaire pour utiliser l’authentification héritée.
  
Cliquez sur les liens ci-dessous pour voir comment l’authentification du client Office 2013 et Office 2016 fonctionne avec les services Office 365 en fonction de l’authentification moderne est activée ou non.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype Entreprise Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

Le tableau suivant décrit le comportement de l’authentification pour les applications clientes Office 2013 ou 2016 Office lorsqu’ils se connectent à Exchange Online avec ou sans authentification moderne.
  
|Version d’application client Office ***|Clé de Registre présent ? ***|L’authentification sur moderne ? ***|Comportement de l’authentification avec l’authentification moderne activé pour le client (par défaut) ***|Comportement de l’authentification avec l’authentification moderne désactivée pour le client ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

Le tableau suivant décrit le comportement de l’authentification pour les applications clientes Office 2013 ou 2016 Office lorsqu’ils se connectent à SharePoint Online avec ou sans authentification moderne.
  
|Version d’application client Office ***|Clé de Registre présent ? ***|L’authentification sur moderne ? ***|Comportement de l’authentification avec l’authentification moderne activé pour le client (par défaut) ***|Comportement de l’authentification avec l’authentification moderne désactivée pour le client ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne.  <br/> |Échec de connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne.  <br/> |Échec de connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne.  <br/> |Échec de connexion.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype Entreprise Online
<a name="BK_SFBO"> </a>

Le tableau suivant décrit le comportement de l’authentification pour Office 2013 et les applications clientes Office 2016 lorsqu’ils se connectent à Skype pour Business Online avec ou sans authentification moderne.
  
|Version d’application client Office ***|Clé de Registre présent ? ***|L’authentification sur moderne ? ***|Comportement de l’authentification avec l’authentification moderne activé pour le client ***|Comportement de l’authentification avec l’authentification moderne désactivée pour le client (par défaut) ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, Assistant de connexion Microsoft Online est utilisée. Serveur refuse l’authentification moderne lorsque Skype pour les clients professionnels en ligne ne sont pas activés.  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, Assistant de connexion Microsoft Online est utilisée. Serveur refuse l’authentification moderne lorsque Skype pour les clients professionnels en ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, Assistant de connexion Microsoft Online est utilisée. Serveur refuse l’authentification moderne lorsque Skype pour les clients professionnels en ligne ne sont pas activés.  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, Assistant de connexion Microsoft Online est utilisée. Serveur refuse l’authentification moderne lorsque Skype pour les clients professionnels en ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, Assistant de connexion Microsoft Online est utilisée. Serveur refuse l’authentification moderne lorsque Skype pour les clients professionnels en ligne ne sont pas activés.  <br/> |Microsoft Online Assistant de connexion uniquement.  <br/> |
   
## <a name="see-also"></a>Voir aussi

[À l’aide de l’authentification moderne Office 365 avec les clients Office](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)

