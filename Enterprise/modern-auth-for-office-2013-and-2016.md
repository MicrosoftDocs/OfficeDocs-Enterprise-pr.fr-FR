---
title: Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Découvrez comment les fonctionnalités d’authentification moderne Microsoft 365 fonctionnent différemment pour les applications clientes Office 2013 et 2016.
ms.openlocfilehash: 20a6f495ac7e8bd6b2a918ca05b9edd074c7d61c
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606910"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Fonctionnement de l’authentification moderne pour Office 2013, Office 2016 et les applications clientes Office 2019

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lisez cet article pour découvrir comment les applications clientes Office 2013, Office 2016 et Office 2019 utilisent des fonctionnalités d’authentification modernes basées sur la configuration de l’authentification sur le client Microsoft 365 pour Exchange Online, SharePoint Online et Skype entreprise online.

> [!NOTE]
> Les applications clientes héritées, telles que Office 2010 et Office pour Mac 2011, ne prennent pas en charge l’authentification moderne et ne peuvent être utilisées qu’avec l’authentification de base.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Disponibilité de l’authentification moderne pour les services Microsoft 365

Pour les services Microsoft 365, l’État par défaut de l’authentification moderne est :
  
- Activé **par défaut pour Exchange** online. Consultez la rubrique [activer ou désactiver l’authentification moderne dans Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) pour la désactiver ou la désactiver. 
    
- Activé **par** défaut pour SharePoint Online. 
    
- Activé **par** défaut pour Skype entreprise online. Consultez la rubrique [Enable Skype for Business Online for moderne Authentication pour l' ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)activer ou le désactiver.

> [!NOTE]
> Pour les locataires créés **avant** le 1er août 2017, l’authentification moderne est **désactivée ** par défaut pour Exchange Online et Skype Entreprise Online.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportement de connexion des applications clientes Office

Les applications clientes Office 2013 prennent en charge l’authentification héritée par défaut. Legacy signifie qu’ils prennent en charge l’Assistant de connexion Microsoft Online ou l’authentification de base. Pour que ces clients utilisent les fonctionnalités d’authentification modernes, le client Windows doit disposer de clés de Registre définies. Pour obtenir des instructions, consultez la rubrique [activer l’authentification moderne pour Office 2013 sur les appareils Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Pour activer l'authentification moderne pour les appareils exécutant Windows (par exemple les ordinateurs portables et tablettes) et sur lesquels Microsoft Office 2013 est installé, vous devez définir les clés de Registre suivantes. Les clés doivent être définies sur chaque appareil pour lequel vous voulez activer l'authentification moderne :
  
|**Clé de Registre**|**Type**|**Valeur** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |0,1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |0,1 |
  
Découvrez [comment utiliser l’authentification moderne (Adal) avec Skype entreprise](https://go.microsoft.com/fwlink/p/?LinkId=785431) pour en savoir plus sur son fonctionnement avec Skype entreprise. 
  
Les clients Office 2016 et Office 2019 prennent en charge l’authentification moderne par défaut et aucune action n’est nécessaire pour que le client utilise ces nouveaux flux. Toutefois, une action explicite est nécessaire pour utiliser l’authentification héritée.
  
Cliquez sur les liens ci-dessous pour voir comment Office 2013, Office 2016 et Office 2019 Client Authentication fonctionne avec les services Microsoft 365 selon que l’authentification moderne est activée ou non.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype Entreprise Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Le tableau suivant décrit le comportement d’authentification pour Office 2013, Office 2016 et les applications clientes Office 2019 lorsqu’ils se connectent à Exchange Online avec ou sans authentification moderne.
  
|Version de l’application cliente Office * * * *|Clé de registre présente ? * * * *|Authentification moderne activée ? * * * *|Comportement d’authentification avec l’authentification moderne activée pour le client (par défaut) * * * *|Comportement d’authentification avec l’authentification moderne désactivée pour le client * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nbre <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur Outlook 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne dans le client Outlook.<br/> |
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2016  <br/> |Nbre <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne dans le client Outlook.<br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est alors utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Le tableau suivant décrit le comportement d’authentification pour Office 2013, Office 2016 et les applications clientes Office 2019 lorsqu’ils se connectent à SharePoint Online avec ou sans authentification moderne.
  
|Version de l’application cliente Office * * * *|Clé de registre présente ? * * * *|Authentification moderne activée ? * * * *|Comportement d’authentification avec l’authentification moderne activée pour le client (par défaut) * * * *|Comportement d’authentification avec l’authentification moderne désactivée pour le client * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype Entreprise Online
<a name="BK_SFBO"> </a>

Le tableau suivant décrit le comportement d’authentification pour Office 2013, Office 2016 et les applications clientes Office 2019 lorsqu’ils se connectent à Skype entreprise Online avec ou sans authentification moderne.
  
|Version de l’application cliente Office * * * *|Clé de registre présente ? * * * *|Authentification moderne activée ? * * * *|Comportement d’authentification avec l’authentification moderne activée pour le client * * * *|Comportement d’authentification avec l’authentification moderne désactivé pour le client (par défaut) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype entreprise Online ne sont pas activés.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
   
## <a name="see-also"></a>Voir aussi

[Activer l’Authentification moderne pour Office 2013 sur les appareils Windows](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication)

[Authentification multifacteur pour Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365)

[Se connecter à Microsoft 365 avec l’authentification multifacteur](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
