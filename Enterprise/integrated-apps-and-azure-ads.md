---
title: Applications intégrées et Azure AD pour les administrateurs Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Découvrez comment les applications intégrées O365 sont enregistrées et administrées dans Azure AD
ms.openlocfilehash: 0cb3ac73230e0ddce62366af9019a12ea2b04d09
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998089"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Applications intégrées et Azure AD pour les administrateurs Microsoft 365

Il y a plus de gestion des applications intégrées que l’activation ou la désactivation [des applications intégrées](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Avec l’arrivée des API REST Microsoft 365, les utilisateurs peuvent accorder aux applications l’accès à leurs données Microsoft 365, telles que le courrier, les calendriers, les contacts, les utilisateurs, les groupes, les fichiers et les dossiers. Par défaut, les utilisateurs doivent accorder individuellement des autorisations à chaque application, mais cela n’est pas adapté si vous souhaitez autoriser une application au niveau de l’administrateur général et la déployer dans l’ensemble de votre organisation via le lanceur d’applications. Pour ce faire, vous devez enregistrer l’application dans Azure AD. Vous devez effectuer certaines étapes avant de pouvoir enregistrer une application dans Azure AD, ainsi que des informations d’arrière-plan que vous devez savoir, qui peuvent vous aider à gérer les applications dans votre organisation Microsoft 365. Cet article vous dirige vers ces ressources.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Ressources Azure AD pour les administrateurs de Microsoft 365

Vous devez effectuer ces deux procédures pour pouvoir gérer vos applications Microsoft 365 dans Azure AD.
  
|**Conditions préalables**|**Comments**|
|:-----|:-----|
|[Utiliser votre abonnement Azure Active Directory gratuit](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure Active Directory (Azure AD). Vous pouvez utiliser Azure AD pour gérer vos applications et pour créer et gérer des comptes d’utilisateur et de groupe. Pour utiliser Azure AD, accédez au portail Azure et connectez-vous à l’aide de votre compte Microsoft 365.  <br/> |
|[Activation ou désactivation des applications intégrées](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Vous devez activer les applications intégrées pour que vos utilisateurs puissent autoriser les applications tierces à accéder à leurs informations Microsoft 365 et à enregistrer des applications dans Azure AD. Par exemple, lorsqu’une personne utilise une application tierce, elle peut demander l’autorisation d’accéder à son calendrier et de modifier les fichiers qui se trouvent dans un dossier OneDrive entreprise.  <br/> |
   
La gestion des applications Microsoft 365 nécessite que vous connaissez les applications dans Azure AD. Ces articles vous aident à vous fournir les informations d’arrière-plan dont vous avez besoin.
  
|**Article d’arrière-plan**|**Comments**|
|:-----|:-----|
|[Rencontrez le lanceur d’applications Microsoft 365](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous débutez avec le lanceur d’applications, vous pouvez vous en demander en quoi il s’agit et comment l’utiliser. Le lanceur d’applications est conçu pour vous aider à accéder à vos applications de n’importe où dans Microsoft 365.  <br/> |
|[Vue d’ensemble des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Les API 365 de Microsoft vous permettent de fournir un accès à vos données Microsoft 365, notamment les éléments qui les intéressent le plus, leurs courriers, calendriers, contacts, utilisateurs et groupes, fichiers et dossiers. Dans cet article, il existe un diagramme qui illustre la relation entre les applications Microsoft 365, Azure AD et les données auxquelles les applications ont accès.  <br/> |
|[Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Découvrez les applications intégrées à Azure AD et comment enregistrer votre application, comprendre les concepts sous-jacents d’une application inscrite et en savoir plus sur les instructions de personnalisation pour les applications multi-locataires.  <br/> |
|[Ajouter des vignettes personnalisées au lanceur d’applications](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |Le lanceur d’applications de Microsoft 365 permet aux utilisateurs de trouver plus facilement les applications et d’y accéder. Cet article décrit comment vous pouvez faire en sorte que vos applications apparaissent dans les lanceurs d’applications des utilisateurs et leur donner une expérience d’authentification unique (SSO) à l’aide de leurs informations d’identification Microsoft 365.  <br/> |
|[Didacticiels d’intégration Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |L’objectif de ces didacticiels est de vous montrer comment configurer Azure AD SSO pour les applications SaaS tierces.  <br/> |
|[Scénarios d’authentification pour Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant l’identité sous la forme d’un service, avec prise en charge des protocoles standard de l’industrie tels que OAuth 2,0 et OpenID Connect, ainsi que des bibliothèques Open source pour différentes plateformes pour vous aider à commencer à coder rapidement. Ce document vous aide à comprendre les différents scénarios pris en charge par Azure AD et vous montre comment commencer.  <br/> |
|[Accès aux applications](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permet une intégration facile à de nombreux logiciels populaires actuels en tant qu’applications de service (SaaS). Il fournit la gestion des identités et des accès, et fournit un panneau d’accès pour les utilisateurs, où ils peuvent découvrir l’accès aux applications dont ils disposent et où ils peuvent utiliser l’authentification unique pour accéder à leurs applications. Cet article fournit des liens vers les ressources associées qui vous permettent d’en savoir plus sur les améliorations de l’accès aux applications pour Azure AD et sur la façon de les aider.  <br/> |
|[Personnaliser votre expérience Office 365](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Vous pouvez accéder rapidement aux applications que vous utilisez quotidiennement en ajoutant ou en supprimant des applications dans le lanceur d’applications Microsoft 365.  <br/> |
   

