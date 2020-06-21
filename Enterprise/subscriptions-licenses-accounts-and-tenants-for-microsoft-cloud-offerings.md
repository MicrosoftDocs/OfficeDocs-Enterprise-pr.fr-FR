---
title: Abonnements, licences, comptes et clients des offres de cloud de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Résumé : Comprenez les relations des organisations, des abonnements, des licences, des comptes d’utilisateur et des clients au sein des offres de cloud de Microsoft.'
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735962"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, licences, comptes et clients des offres de cloud de Microsoft

 **Résumé :** Comprenez les relations des organisations, des abonnements, des licences, des comptes d’utilisateur et des clients au sein des offres de cloud de Microsoft.
  
Microsoft fournit une hiérarchie d’organisations, d’abonnements, de licences et de comptes d’utilisateur pour une utilisation cohérente des identités et de la facturation au sein de ses offres de cloud :
  
- Microsoft Office 365
- Microsoft Azure
- Microsoft Intune et Enterprise Mobility + Security (EMS)
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combine Office 365, EMS, et Windows 10 Entreprise en un seul abonnement et ensemble de services intégrés.

## <a name="elements-of-the-hierarchy"></a>Éléments de la hiérarchie

Voici les éléments de la hiérarchie :
  
### <a name="organization"></a>Organisation

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Abonnements

Un abonnement est un accord conclu avec Microsoft sur l’utilisation d’une ou de plusieurs plateformes ou services de cloud Microsoft, dont les frais applicables sont calculés sur la base de frais de licence par utilisateur ou selon la consommation des ressources de cloud. 

- Les offres de cloud Microsoft Software as a Service (SaaS) (Office 365, Intune/EMS et Dynamics 365) facturent des frais de licence par utilisateur. 
- Les offres de cloud Microsoft Platform as a Service (PaaS) et Infrastructure as a Service (IaaS) (Azure) facturent des frais en fonction de la consommation des ressources de cloud.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
Les organisations peuvent avoir plusieurs abonnements pour les offres de cloud Microsoft, comme illustré dans la Figure 1. La Figure 1 présente une organisation unique avec plusieurs abonnements Office 365, un abonnement Intune, un abonnement Dynamics 365 et plusieurs abonnements Azure.

**Figure 1 : Exemple de plusieurs abonnements pour une organisation**

![Un exemple d’organisation avec plusieurs abonnements pour les offres de cloud de Microsoft.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>Licences

Pour les offres de cloud SaaS de Microsoft, une licence permet à un compte d’utilisateur spécifique d’utiliser les services de l’offre de cloud. Vous payez un coût mensuel fixe dans le cadre de votre abonnement. Les administrateurs attribuent des licences à des comptes d’utilisateur individuels dans l’abonnement. Par exemple, dans la Figure 2, la société Contoso a un abonnement à Office 365 Entreprise E5 avec 100 licences, ce qui permet à un maximum de 100 comptes d’utilisateur individuels d’utiliser les services et fonctionnalités d’Entreprise E5 Office 365.
  
**Figure 2 : Licences liées aux abonnements SaaS d’une organisation**

![Exemple de plusieurs licences au sein des abonnements pour les offres de cloud SaaS de Microsoft.](media/Subscriptions/Subscriptions-Fig2.png)
  
Pour les services de cloud PaaS Azure, les licences logicielles sont intégrées dans la tarification du service.  
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>Comptes d’utilisateur

Les comptes d’utilisateur pour toutes les offres de cloud de Microsoft sont stockés dans un client Azure Active Directory (Azure AD) qui contient des comptes et groupes d’utilisateurs. Un client Azure AD peut être synchronisé avec vos comptes Active Directory Domain Services (AD DS) existants à l’aide d’Azure AD Connect, un service de serveur Windows. C’est ce que l’on appelle la synchronisation d’annuaires.
  
La Figure 3 illustre un exemple de plusieurs abonnements d’une organisation à l’aide d’un client Azure Active Directory commun qui contient les comptes de l’organisation.
  
**Figure 3 : Plusieurs abonnements d’une organisation qui utilisent le même client Azure AD**

![Un exemple d’organisation avec plusieurs abonnements utilisant tous le même client Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Clients

For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.
  
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
    
Plusieurs abonnements à des offres de cloud Microsoft peuvent utiliser le même client Azure AD, qui agit comme un fournisseur d’identité commun. Un client Azure AD central qui contient les comptes synchronisés de votre AD DS local fournit une identité IDaaS dans le cloud pour votre organisation. 
  
**Figure 4 : Comptes en local synchronisés et IDaaS pour une organisation**

![Identité sous la forme d’un service (IaaS) IDaaS pour votre organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
La Figure 4 montre l’utilisation d’un client Azure AD commun par les offres cloud SaaS de Microsoft, les applications PaaS Azure et les machines virtuelles dans IaaS Azure qui utilisent Azure Active Directory Domain Services. Azure AD Connect synchronise la forêt AD DS locale avec le client Azure AD.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Combiner les abonnements de plusieurs offres de cloud Microsoft

Le tableau suivant décrit la manière dont vous pouvez combiner plusieurs offres de cloud Microsoft en disposant déjà d’un abonnement pour un type d’offre de cloud (étiquettes actives vers le bas de la première colonne) et en ajoutant un abonnement pour une offre de cloud différente (à travers les colonnes).
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |N/A  <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |Vous ajoutez un abonnement Intune/EMS à votre organisation à partir du Centre d’administration Microsoft 365.  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation à partir du Centre d’administration Microsoft 365.  <br/> |
|**Azure** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.  <br/> |N/A  <br/> |Vous ajoutez un abonnement Intune/EMS à votre organisation.  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation.  <br/> |
|**Intune/EMS** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.  <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |N/A  <br/> |Vous ajoutez un abonnement Dynamics 365 à votre organisation.  <br/> |
|**Dynamics 365** <br/> |Vous ajoutez un abonnement Office 365 à votre organisation.  <br/> |Vous ajoutez un abonnement Azure à votre organisation à partir du portail Azure.  <br/> |Vous ajoutez un abonnement Intune/EMS à votre organisation.  <br/> |N/A  <br/> |
   
Une solution simple pour ajouter des abonnements à votre organisation pour les services SaaS Microsoft consiste à utiliser le centre d’administration :
  
1. Connectez-vous au Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) avec votre compte d’administrateur général.
    
2. À partir du volet de navigation gauche de la page d’accueil du **centre d’administration**, cliquez sur **Facturation**, puis **Acheter des services**.
    
3. Dans la page **Acheter des services**, achetez vos nouveaux abonnements.
    
Le centre d’administration affecte l’organisation et le client Azure AD de votre abonnement à Office 365 aux nouveaux abonnements pour les offres cloud SaaS.
  
Pour ajouter un abonnement Azure disposant de la même organisation et du même client Azure Active Directory que votre abonnement Office 365, procédez comme suit :
  
1. Connectez-vous au portail Azure ([https://portal.azure.com](https://portal.azure.com)) avec votre compte Administrateur général Office 365.
    
2. Dans le volet de navigation gauche, cliquez sur **Abonnements**, puis sur **Ajouter**.
    
3. Dans la page **Ajouter un abonnement**, sélectionnez une offre et complétez l’accord et les informations de paiement.
    
Si vous avez obtenu séparément des abonnements Azure et Office 365, et que vous souhaitez accéder au client Office 365 Azure AD à partir de votre abonnement Azure, reportez-vous aux instructions décrites de l’article [Ajouter un abonnement Azure à votre locataire Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Voir aussi

[Ressources relatives à l’architecture informatique Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Solutions hybrides](hybrid-solutions.md)

## <a name="next-step"></a>Étape suivante

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
