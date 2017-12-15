---
title: Abonnements, licences, les comptes et les locataires pour les offres en nuage de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: "Résumé : Comprendre les relations entre les organisations, les abonnements, licences, comptes d’utilisateurs et locataires sur les offres en nuage de Microsoft."
ms.openlocfilehash: 0c416efe1bfff6a3e6c979af165df8eb951b879c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, licences, les comptes et les locataires pour les offres en nuage de Microsoft

 **Résumé :** Comprendre les relations entre les organisations, les abonnements, licences, comptes d’utilisateurs et locataires sur les offres en nuage de Microsoft.
  
Microsoft fournit une hiérarchie des organisations, des abonnements, des licences et des comptes d’utilisateurs pour une utilisation cohérente de facturation et d’identités au sein de ses offres en nuage :
  
- Microsoft Office 365
    
    Consultez les [plans d’activités et de tarification](https://products.office.com/business/compare-office-365-for-business-plans) pour plus d’informations.
    
- Microsoft Azure
    
    Pour plus d’informations, consultez [tarification d’Azure](https://azure.microsoft.com/pricing/) .
    
- Microsoft Intune et de la mobilité d’entreprise + sécurité (EMS)
    
    Pour plus d’informations, consultez [Intune tarification](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) .
    
- Microsoft Dynamics 365
    
    Pour plus d’informations, consultez [tarification de Dynamics 365](https://dynamics.microsoft.com/) .
    
## <a name="elements-of-the-hierarchy"></a>Éléments de la hiérarchie

Voici les éléments de la hiérarchie :
  
### <a name="organization"></a>Organisation

Une organisation représente une entité commerciale qui utilise les offres de cloud Microsoft et qui est généralement identifiée par un nom de domaine DNS public, par exemple, contoso.com. L’organisation est un conteneur pour les abonnements.
  
### <a name="subscriptions"></a>Abonnements

Un abonnement est un accord avec Microsoft pour utiliser l’une ou plus de plateformes en nuage de Microsoft ou de services, pour lequel les frais accumuler sur soit une redevance de licence par utilisateur ou sur la consommation des ressources de nuage. Logiciel de Microsoft en tant que Service (SaaS)-offres en nuage de base (Office 365, Intune/EMS et Dynamics 365) frais par utilisateur licence. Plate-forme de Microsoft en tant que Service (PaaS) et Infrastructure en tant que Service (IaaS) cloud offres (Azure) frais en fonction de la consommation de ressources de cloud.
  
Vous pouvez également utiliser un abonnement d’évaluation, mais l’abonnement expire après une certaine période ou des frais de consommation spécifiques. Vous pouvez convertir un abonnement d’évaluation en abonnement payant.
  
Les organisations peuvent avoir plusieurs abonnements pour les offres en nuage de Microsoft. La figure 1 montre un exemple.
  
**Figure 1 : Exemple d’abonnements multiples pour une organisation**

![Un exemple d’organisation avec plusieurs abonnements pour les offres de cloud de Microsoft.](images/Subscriptions/Subscriptions_Fig1.png)

  
La Figure 1 présente une organisation unique avec plusieurs abonnements Office 365, un abonnement Intune, un abonnement Dynamics 365 et plusieurs abonnements Azure.
  
### <a name="licenses"></a>Licences

Pour les offres en nuage de Microsoft SaaS, une licence permet à un compte d’utilisateur spécifique utiliser les services du nuage offre. Vous sont facturés des frais mensuels fixes dans le cadre de votre abonnement. Les administrateurs attribuer des licences à des comptes d’utilisateurs individuels dans l’abonnement. Dans l’exemple de la Figure 2, la société Contoso a un abonnement à Office 365 entreprise E5 avec 100 licences, qui permet d’utiliser les services et les fonctionnalités d’entreprise E5 jusqu'à 100 comptes d’utilisateurs individuels.
  
**Figure 2 : Les licences dans les abonnements SaaS-basé pour une organisation**

![Exemple de plusieurs licences au sein des abonnements pour les offres de cloud SaaS de Microsoft.](images/Subscriptions/Subscriptions_Fig2.png)
  
Pour les services de cloud PaaS Azure, les licences logicielles sont intégrées dans la tarification du service.  
  
Pour les machines virtuelles IaaS Azure, des licences supplémentaires pour utiliser le logiciel ou une application installé(e) sur une image de machine virtuelle peuvent être exigées. Certaines images de machine virtuelle disposent de versions sous licence des logiciels installés et le coût est inclus dans le tarif par minute du serveur. Les images de machine virtuelle pour SQL Server 2014 et SQL Server 2016 en sont des exemples.  
  
Certaines images de machine virtuelle ont des versions d’évaluation des applications installées et ont besoin de licences logicielles supplémentaires pour une utilisation au-delà de la période d’évaluation. Par exemple, l’image de machine virtuelle de la version d’évaluation de SharePoint Server 2016 inclut une version d’évaluation de SharePoint Server 2016 préinstallée. Pour continuer à utiliser SharePoint Server 2016 après la date d’expiration de la version d’évaluation, vous devez acheter une licence SharePoint Server 2016 et des licences client auprès de Microsoft. Ces frais sont distincts de l’abonnement Azure et le tarif par minute relatif pour l’exécution de la machine virtuelle reste applicable.
  
### <a name="user-accounts"></a>Comptes d’utilisateur

Comptes d’utilisateurs pour toutes les offres de nuage de Microsoft sont stockés dans un locataire Azure Active Directory (AD), qui contient les comptes d’utilisateurs et de groupes. Un locataire AD Azure peut être synchronisé avec vos comptes Windows Server Active Directory existants à l’aide d’Azure AD de se connecter, un service Windows server. On parle alors de synchronisation d’annuaires (DirSync).
  
La Figure 3 illustre un exemple de plusieurs abonnements d’une organisation à l’aide d’un client Azure Active Directory commun qui contient les comptes de l’organisation.
  
**Figure 3 : Plusieurs abonnements d’une organisation qui utilisent le locataire AD Azure même**

![Un exemple d’organisation avec plusieurs abonnements utilisant tous le même client Azure AD.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>Clients

Pour les offres SaaS cloud, le client est l’emplacement régional qui héberge les serveurs fournissant des services de cloud. Par exemple, la société Contoso a choisi la région Europe pour héberger ses clients Office 365, EMS et Dynamics 365 pour les 15 000 travailleurs de son siège social à Paris.
  
Les services PaaS Azure et les charges de travail basées sur une machine virtuelle hébergés dans IaaS Azure peuvent avoir une location dans n’importe quel centre de données Azure dans le monde entier. Vous spécifiez le centre de données Azure, appelé emplacement, lorsque vous créez l’application ou le service PaaS Azure, ou l’élément d’une charge de travail IaaS.
  
Un client Azure Active Directory est une instance spécifique d’Azure AD contenant des comptes et des groupes. Les abonnements d’évaluation ou payants d’Office 365, Dynamics 365 ou Intune/EMS incluent un client Azure Active Directory gratuit. Ce client Azure Active Directory n’inclut pas les autres services Azure et n’est pas identique à un abonnement d’évaluation ou payant Azure.
  
### <a name="summary-of-the-hierarchy"></a>Résumé de la hiérarchie

Voici un récapitulatif rapide :
  
- Une organisation peut avoir plusieurs abonnements
    
  - Un abonnement peut avoir plusieurs licences
    
  - Des licences peuvent être affectées à des comptes d’utilisateur individuels
    
  - Les comptes d’utilisateur sont stockés dans un client Azure AD
    
Voici un exemple de relation des organisations, des abonnements, des licences et des comptes d’utilisateur :
  
- Une organisation identifiée par son nom de domaine public.
    
  - Un abonnement Office 365 Entreprise E3 avec licences utilisateur.
    
    Un abonnement Office 365 Entreprise E5 avec licences utilisateur.
    
    Un abonnement EMS avec licences utilisateur.
    
    Un abonnement Dynamics 365 avec licences utilisateur.
    
    Abonnements Azure multiples
    
  - Les comptes d’utilisateurs de l’organisation dans un client Azure AD commun.
    
Plusieurs abonnements à des offres de cloud Microsoft peuvent utiliser le même client Azure AD, qui agit comme un fournisseur d’identité commun. Un client Azure AD central qui contient les comptes synchronisés de votre Windows Server AD local fournit une identité IDaaS dans le cloud pour votre organisation. Cela est illustré dans la Figure 4.
  
**La figure 4 : Les comptes locaux synchronisés et IDaaS pour une organisation**

![Identité sous la forme d’un service (IaaS) IDaaS pour votre organisation.](images/Subscriptions/Subscriptions_Fig4.png)
  
La Figure 4 montre l’utilisation d’un client Azure AD commun par les offres cloud SaaS de Microsoft, les applications PaaS Azure et les machines virtuelles dans IaaS Azure qui utilisent les services de domaine Azure AD. Azure AD Connect synchronise la forêt Windows Server AD locale avec le client Azure AD.
  
Pour plus d’informations sur l’intégration des identités entre les offres en nuage de Microsoft, consultez [Identité de Cloud Microsoft pour Enterprise Architects](https://aka.ms/cloudarchidentity).
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Combiner les abonnements de plusieurs offres de cloud Microsoft

Le tableau suivant décrit la manière dont vous pouvez combiner plusieurs offres de cloud Microsoft en disposant déjà d’un abonnement pour un type d’offre de cloud (étiquettes actives vers le bas de la première colonne) et en ajoutant un abonnement pour une offre de cloud différente (à travers les colonnes).
  
||**Office 365**|**Azure**|**/EMS Intune**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |N/A  <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |Vous ajoutez un abonnement Intune /EMS à votre organisation à partir du portail Office 365.  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation à partir du portail Office 365.  <br/> |
|**Azure** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.   <br/> |N/A  <br/> |Vous ajoutez un abonnement Intune/EMS à votre organisation.  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation.  <br/> |
|**/EMS Intune** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.   <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |N/A  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation.  <br/> |
|**Dynamics 365** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.   <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |Vous ajoutez un abonnement Intune/EMS à votre organisation.  <br/> |N/A  <br/> |
   
Une solution simple pour ajouter des abonnements à votre organisation pour les services SaaS Microsoft consiste à utiliser le centre d’administration Office 365 :
  
1. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec votre compte d’administrateur global, puis cliquez sur **administration**.
    
2. À partir de navigation de gauche de la page d’accueil **Centre d’administration** , cliquez sur **facturation**, **services d’achat**.
    
3. Dans la page **services d’achat** , acheter vos nouveaux abonnements.
    
Le Centre d’administration Office 365 affecte l’organisation et le client Azure AD de votre abonnement à Office 365 aux nouveaux abonnements pour les offres de cloud SaaS.
  
Pour ajouter un abonnement Azure disposant de la même organisation et du même client Azure Active Directory que votre abonnement Office 365, procédez comme suit :
  
1. Connectez-vous au portail Azure ([https://portal.azure.com](https://portal.azure.com)) avec votre compte d’administrateur global de Office 365.
    
2. Dans la navigation de gauche, cliquez sur **abonnements**, puis cliquez sur **Ajouter**.
    
3. Sur la page **d’abonnement de l’ajouter** , sélectionnez une offre et terminer l’accord et les informations de paiement.
    
Si vous souhaitez accéder les clients AD Azure Office 365 de votre abonnement Azure acheté séparément les abonnements Azure et Office 365, reportez-vous aux instructions dans [associer un client Office 365 avec un abonnement Azure](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).
  
## <a name="see-also"></a>See Also

[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Solutions hybrides](hybrid-solutions.md)
  
[Abonnements, licences et comptes d'utilisateur de Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



