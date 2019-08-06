---
title: Applications intégrées et Azure AD pour les administrateurs d’Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Découvrez comment les applications intégrées O365 sont enregistrées et administrées dans Azure AD
ms.openlocfilehash: c52b4beefaefd4a115c132c6f82e7f1d20564b46
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782524"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Applications intégrées et Azure AD pour les administrateurs d’Office 365

Il y a plus de gestion des applications intégrées que l’activation ou la désactivation [des applications intégrées](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Avec l’arrivée des API REST Office 365, les utilisateurs peuvent accorder aux applications l’accès à leurs données Office 365, telles que le courrier, les calendriers, les contacts, les utilisateurs, les groupes, les fichiers et les dossiers. Par défaut, les utilisateurs doivent accorder individuellement des autorisations à chaque application, mais cela n’est pas adapté si vous souhaitez autoriser une application au niveau de l’administrateur général et la déployer dans l’ensemble de votre organisation via le lanceur d’applications. Pour ce faire, vous devez enregistrer l’application dans Azure AD. Vous devez effectuer certaines étapes avant de pouvoir enregistrer une application dans Azure AD et des informations d’arrière-plan que vous devez savoir pour pouvoir gérer les applications dans votre organisation Office 365. Cet article vous dirige vers ces ressources.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Ressources Azure AD pour les administrateurs Office 365

Vous devez effectuer ces deux procédures pour pouvoir gérer vos applications Office 365 dans Azure AD.
  
|**Conditions préalables**|**Commentaires**|
|:-----|:-----|
|[Enregistrer votre abonnement Azure Active Directory gratuit](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Chaque abonnement payant à Office 365 est fourni avec un abonnement gratuit à Azure Active Directory. Vous pouvez utiliser Azure AD pour gérer vos applications et pour créer et gérer des comptes d’utilisateur et de groupe. Pour activer cet abonnement et accéder au portail de gestion Azure, vous devez suivre un processus d’enregistrement unique. Ensuite, vous pouvez accéder à Azure AD à partir du centre d’administration Microsoft 365.  <br/> |
|[Activation ou désactivation des applications intégrées](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Vous devez activer les applications intégrées pour que vos utilisateurs puissent autoriser les applications tierces à accéder à leurs informations Office 365 et à enregistrer des applications dans Azure AD. Par exemple, lorsqu’une personne utilise une application tierce, elle peut demander l’autorisation d’accéder à son calendrier et de modifier les fichiers qui se trouvent dans un dossier OneDrive entreprise.  <br/> |
   
La gestion des applications Office 365 nécessite que vous connaissez les applications dans Azure AD. Ces articles vous aident à vous fournir les informations d’arrière-plan dont vous avez besoin.
  
|**Article d’arrière-plan**|**Commentaires**|
|:-----|:-----|
|[Se conformer au lanceur d’applications Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous débutez avec le lanceur d’applications, vous pouvez vous en demander en quoi il s’agit et comment l’utiliser. Le lanceur d’applications est conçu pour vous aider à accéder à vos applications depuis n’importe où dans Office 365.  <br/> |
|[Ajout, mise à jour et suppression d'une application](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |Cette rubrique vous explique comment ajouter, mettre à jour ou supprimer une application dans Azure Active Directory. Vous en saurez plus sur les différents types d’applications qui peuvent être intégrées à Azure AD et sur la configuration de vos applications pour accéder à d’autres ressources, telles que les API Web, et bien plus encore.  <br/> |
|[Faire apparaître votre application dans le lanceur d’applications Office 365](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Le lanceur d’applications dans Office 365 qui permet aux utilisateurs de trouver et d’accéder plus facilement à leurs applications. Cet article décrit comment vous pouvez faire en sorte que vos applications apparaissent dans les lanceurs d’applications des utilisateurs et leur donner une expérience d’authentification unique (SSO) à l’aide de leurs informations d’identification Office 365.  <br/> |
|[Présentation de la plateforme des API Office 365](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Les API Office 365 vous permettent de fournir l’accès aux données Office 365 de votre client, y compris les éléments qui les intéressent le plus, leurs courriers, calendriers, contacts, utilisateurs et groupes, fichiers et dossiers. Dans cet article, il existe un diagramme qui illustre la relation entre les applications Office 365, Azure AD et les données auxquelles les applications ont accès.  <br/> |
|[Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Découvrez les applications intégrées à Azure Active Directory et comment enregistrer votre application, comprendre les concepts à l’origine d’une application inscrite et en savoir plus sur les instructions de personnalisation pour les applications mutualisées.  <br/> |
|[Didacticiels d’intégration Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |L’objectif de ces didacticiels est de vous montrer comment configurer Azure AD SSO pour les applications SaaS tierces.  <br/> |
|[Scénarios d’authentification pour Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant l’identité sous la forme d’un service, avec prise en charge des protocoles standard de l’industrie tels que OAuth 2,0 et OpenID Connect, ainsi que des bibliothèques Open source pour différentes plateformes pour vous aider à commencer à coder rapidement. Ce document vous aide à comprendre les différents scénarios pris en charge par Azure AD et vous montre comment commencer.  <br/> |
|[Accès aux applications](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permet une intégration facile à de nombreux logiciels populaires actuels en tant qu’applications de service (SaaS). Il fournit la gestion des identités et des accès, et fournit un panneau d’accès pour les utilisateurs, où ils peuvent découvrir l’accès aux applications dont ils disposent et où ils peuvent utiliser l’authentification unique pour accéder à leurs applications. Cet article fournit des liens vers les ressources associées qui vous permettent d’en savoir plus sur les améliorations de l’accès aux applications pour Azure AD et sur la façon de les aider.  <br/> |
|[Personnaliser votre expérience Office 365](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Vous pouvez accéder rapidement aux applications que vous utilisez quotidiennement en ajoutant ou en supprimant des applications dans le lanceur d’applications Office 365.  <br/> |
   

