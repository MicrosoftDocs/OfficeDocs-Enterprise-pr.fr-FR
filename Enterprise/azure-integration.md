---
title: Intégration d’Azure à Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Votre abonnement Office 365 inclut un abonnement à Azure AD. Intégrez Office 365 avec Azure AD si vous voulez une synchronisation de mot de passe ou une authentification unique avec votre environnement local.
ms.openlocfilehash: 44231420ee92c37f14874d6fb0f9e926d8d4369d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745787"
---
# <a name="azure-integration-with-office-365"></a>Intégration d’Azure à Office 365

*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 entreprise.*

Office 365 utilise Azure Active Directory (Azure AD) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement Office 365 inclut un abonnement gratuit à Azure AD afin que vous puissiez intégrer Office 365 à Azure AD si vous souhaitez synchroniser les mots de passe ou configurer l’authentification unique avec votre environnement local. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.
  
Azure offre également d’autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser vos abonnements Office 365.
  
Vous pouvez utiliser les conseillers de déploiement Azure AD pour une expérience de configuration et d’installation guidée (vous devez être connecté à Office 365) :

 - [Conseiller Azure AD Connect](https://aka.ms/aadconnectpwsync)
 - [Conseiller de déploiement AD FS](https://aka.ms/adfsguidance)
 - [Guide de configuration d’Azure AD Premium](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Gestion des identités Azure AD et Office 365

Si vous disposez d’un abonnement payant à Office 365, vous disposez également d’un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d’utilisateurs et de groupes. Pour activer cet abonnement, vous devez effectuer une inscription unique. Par la suite, vous pouvez accéder à Azure AD à partir de votre portail d’administration Office 365. 

Pour obtenir des instructions, consultez [la rubrique utiliser votre abonnement Azure ad gratuit](https://go.microsoft.com/fwlink/p/?LinkId=617127). Suivez les instructions pour enregistrer l’abonnement Azure AD gratuit fourni avec votre abonnement à Office 365. N’accédez pas directement à azure.microsoft.com pour vous inscrire ou vous obtiendrez une version d’évaluation ou un abonnement payant à Microsoft Azure qui est distinct de votre version gratuite pour Office 365. 
  
Avec l’abonnement gratuit, vous pouvez synchroniser avec des annuaires locaux, configurer l’authentification unique et effectuer une synchronisation avec de nombreux logiciels en tant qu’applications de service, telles que Salesforce, DropBox et bien d’autres encore.
  
Si vous souhaitez améliorer la fonctionnalité des services de domaine Active Directory (AD DS), la synchronisation bidirectionnelle et d’autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit vers un abonnement Premium payant. Pour plus d’informations, reportez-vous à [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).
  
Pour plus d’informations sur Office 365 et Azure AD, consultez la rubrique [Understanding Office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Étendez les capacités de votre client Office 365

|**Fonctionnalité**|**Description**|
|:-----|:-----|
|Applications intégrées  <br/> |Vous pouvez accorder à des applications individuelles l’accès à vos données Office 365, par exemple des courriers, des calendriers, des contacts, des utilisateurs, des groupes, des fichiers et des dossiers. Vous pouvez également autoriser ces applications au niveau de l’administrateur général et les rendre accessibles à votre entreprise entière en enregistrant les applications dans Azure AD. Pour plus d’informations, consultez la rubrique [applications intégrées et Azure AD pour les administrateurs d’Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  <br/> Voir aussi l' [authentification unique pour les applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Les applications Power sont des applications ciblées pour les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que les listes SharePoint et les autres applications de données. Pour plus d’informations, reportez-vous à [la page créer un PowerApp pour une liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et les [PowerApp](https://powerapps.microsoft.com/) .  <br/> |
   
Pour plus d’informations, consultez la rubrique [applications intégrées et Azure AD pour les administrateurs d’Office 365](integrated-apps-and-azure-ads.md) , ainsi que la [Galerie d’applications Azure ad et l’authentification unique](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
