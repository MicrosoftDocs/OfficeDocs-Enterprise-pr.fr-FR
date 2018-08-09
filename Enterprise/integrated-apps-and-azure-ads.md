---
title: Applications intégrées et Azure AD pour les administrateurs Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Découvrez comment O365 intégrés applications sont enregistrés et administré dans Azure AD
ms.openlocfilehash: 666bfca5c2621d25f13dff7c5753c5ef47591b68
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213112"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Applications intégrées et Azure AD pour les administrateurs Office 365

Il est plus à la gestion des applications intégrées à seulement [Applications intégrée activer ou désactiver](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Avec l’arrivée de l’API REST d’Office 365, les utilisateurs peuvent accorder l’accès des applications à leurs données Office 365, tels que la messagerie, calendriers, contacts, les utilisateurs, groupes, fichiers et dossiers. Par défaut, les utilisateurs ont besoin accorder des autorisations pour chaque application individuellement, mais il ne l’échelle également si vous souhaitez autoriser une application une fois au niveau de l’administrateur global et le déployer dans toute l’organisation par le biais de lancement de l’application. Pour ce faire, vous devez inscrire l’application dans Azure AD. Il existe quelques étapes à suivre avant que vous pouvez enregistrer une application dans Azure AD et des informations de base à connaître qui peuvent vous aider à gérer les applications dans votre organisation Office 365. Cet article vous à ces ressources.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Ressources AD Azure pour les administrateurs Office 365

Vous devez effectuer ces deux procédures avant de pouvoir gérer vos applications Office 365 dans Azure AD.
  
|**Conditions préalables**|**Commentaires**|
|:-----|:-----|
|[Enregistrer votre abonnement Azure Active Directory gratuit](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Chaque abonnement payant à Office 365 est fourni avec un abonnement gratuit à Azure Active Directory. Vous pouvez utiliser Azure AD pour gérer vos applications et à créer et gérer des comptes d’utilisateur et groupe. Pour activer cet abonnement et accéder au portail de gestion Azure, vous devez effectuer un processus d’enregistrement unique. Ensuite, vous pouvez atteindre Azure AD à partir du centre d’administration Office 365.  <br/> |
|[Activation ou désactivation des applications intégrée](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Vous devez activer les applications intégrée pour vos utilisateurs à autoriser les applications de tiers à accéder à leurs informations Office 365 et pour vous inscrire des applications dans Azure AD. Par exemple, lorsqu’une personne utilise une application tierce, cette application peut demander à autorisation pour accéder à leur calendrier et de modifier des fichiers qui se trouvent dans un dossier de Business OneDrive.  <br/> |
   
La gestion des applications Office 365, vous devez avoir connaissance des applications dans Azure AD. Ces articles aident à vous donner l’arrière-plan que vous avez besoin.
  
|**Article en arrière-plan**|**Commentaires**|
|:-----|:-----|
|[Respecter le lancement d’application Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous ne connaissez pas le lancement d’application, vous vous demandez peut-être qu’il est et comment l’utiliser. Le lancement d’application est conçu pour vous aider à atteindre vos applications à partir de n’importe où dans Office 365.  <br/> |
|[Ajout, modification et suppression d’une Application](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |Cette rubrique montre comment ajouter, mettre à jour ou supprimer une application dans Azure Active Directory. Vous allez découvrir les différents types d’applications qui peuvent être intégrées avec Azure AD et comment configurer vos applications pour accéder aux autres ressources telles que les API de web et bien plus encore.  <br/> |
|[Les applications apparaissent dans le lancement d’application Office 365](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Lancement de l’application dans Office 365 qui facilite pour les utilisateurs à trouver et accéder à leurs applications. Cet article décrit les façons de vous en tant que développeur vos applications à afficher dans les lanceurs application des utilisateurs et leur donner une expérience d’authentification unique (SSO) à l’aide de leurs informations d’identification d’Office 365.  <br/> |
|[Présentation de la plateforme Office 365 API](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Les API d’Office 365 vous permet de fournir l’accès aux données d’Office 365 de votre client, y compris les éléments qui les intéressent plus — leur messagerie, calendriers, contacts, les utilisateurs et groupes, fichiers et dossiers. Il existe un diagramme bonne dans cet article qui illustre la relation entre les applications Office 365, Azure AD, et les données qui accèdent aux applications.  <br/> |
|[Intégration d’Applications dans Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | Découvrez les applications qui sont intégrées dans Azure Active Directory et comment enregistrer votre application, comprendre les concepts d’une application enregistrée et découvrez les instructions de personnalisation pour plusieurs applications de client.  <br/> |
|[Didacticiels de l’intégration Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |L’objectif de ces didacticiels consiste à vous montrer comment configurer l’authentification unique de Azure AD pour les applications SaaS tiers.  <br/> |
|[Scénarios d’authentification pour Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant l’identité en tant que service, avec prise en charge des protocoles standard tels que OAuth 2.0 et se connecter OpenID, ainsi que d’ouvrir des bibliothèques de sources pour les différentes plateformes pour vous aider à commencer rapidement à coder. Ce document vous aide à comprendre les différents scénarios Azure AD prend en charge et vous montre comment commencer.  <br/> |
|[Accès aux applications](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD permet l’intégration facile à de nombreuses répandus aujourd'hui comme une application de service (SaaS) ; Il fournit la gestion des identités et l’accès et il fournit un panneau d’accès pour les utilisateurs où ils peuvent découvrir les accès application et ils peuvent utiliser l’authentification unique pour accéder à leurs applications. Cet article fournit des liens vers les ressources connexes qui vous permettent d’en savoir plus sur les améliorations d’application access pour Azure AD et comment vous pouvez contribuer à leur.  <br/> |
|[Ajouter ou supprimer des mosaïques sur le lancement d’application Office 365](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |Vous pouvez obtenir un accès rapide pour les applications que vous utilisez tous les jours en ajoutant ou supprimant des applications dans le lancement d’application Office 365.  <br/> |
   

