---
title: Collaboration entre clients dans Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Découvrez le fonctionnement de la collaboration Office 365 entre les clients et les organisations.
ms.openlocfilehash: cedeab08cf6daf3817179bcf770eda6598361e67
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069670"
---
# <a name="office-365-inter-tenant-collaboration"></a>Collaboration entre clients dans Office 365

Cet article décrit plusieurs méthodes de collaboration entre deux clients Office 365. Elle est destinée aux administrateurs d’Office 365.
  
Supposons que deux organisations, Fabrikam et contoso, ont chacune un client Office 365 pour les entreprises et qu’elles souhaitent collaborer sur plusieurs projets; certains d’entre eux s’exécutent pendant une période limitée, dont certains sont en cours. Comment Fabrikam et contoso permettent-ils à leurs personnes et équipes de collaborer plus efficacement sur leurs différents clients Office 365 de manière sécurisée? Office 365, en association avec Azure Active Directory B2B collaboration, propose plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et contoso peuvent prendre en compte.
  
Les options de collaboration entre les clients Office 365 incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, les appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications. Utilisez les tableaux suivants pour sélectionner des solutions et en savoir plus.
  
## <a name="exchange-online-collaboration-options"></a>Options de collaboration Exchange Online

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Partager des calendriers avec une autre organisation Office 365  <br/> |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et de permettre aux utilisateurs de partager les planifications (informations de disponibilité) avec d’autres utilisateurs.  <br/> |[Partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relations d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Créer une relation d'organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modifier une relation d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Suppression d’une relation d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation  <br/> |Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs pour contrôler les personnes avec lesquelles elles peuvent être partagées, ainsi que le niveau d’accès accordé.  <br/> |[Stratégies de partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Créer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Appliquer une stratégie de partage à des boîtes aux lettres dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modifier, désactiver ou supprimer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurer des canaux de messagerie sécurisés et contrôler le flux de messagerie avec des organisations partenaires  <br/> |Les administrateurs créent des connecteurs pour appliquer la sécurité aux échanges de messages avec une organisation partenaire ou un fournisseur de services. Les connecteurs appliquent le chiffrement via le protocole TLS (Transport Layer Security) et autorisent les restrictions sur les noms de domaine ou les plages d’adresses IP à partir desquels vos partenaires envoient des messages.  <br/> |[Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie dans Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domaines distants dans Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurer un connecteur pour un flux de messagerie sécurisé avec une organisation partenaire](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Meilleures pratiques en matière de flux de messagerie pour Exchange Online et Office 365 (aperçu)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Options de collaboration SharePoint Online et OneDrive entreprise

|**Objectifs de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes  <br/> |Les administrateurs configurent le partage au niveau du client ou de la collection de sites pour le compte Microsoft authentifié, professionnel ou scolaire comptes authentifiés ou invités  <br/> |[Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Partage de domaines restreints dans Office 365 SharePoint Online et OneDrive entreprise](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Utiliser SharePoint Online comme solution extranet B2B (Business-to-Business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Suivi et contrôle du partage externe pour les utilisateurs finaux  <br/> |Propriétaires de fichiers OneDrive entreprise et utilisateurs finaux SharePoint Online configurer le partage de sites et de documents et établir des notifications pour le suivi du partage  <br/> |[Configurer les notifications pour le partage externe pour OneDrive entreprise](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Partager des fichiers ou dossiers SharePoint dans Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Options de collaboration Skype entreprise

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Skype entreprise Online-messagerie instantanée, appels et présence avec d’autres utilisateurs de Skype entreprise  <br/> |Les administrateurs peuvent permettre à leurs utilisateurs de Skype entreprise Online de se connecter à la messagerie instantanée, de passer des appels audio/vidéo et de voir la présence avec les utilisateurs d’un autre client Office 365.  <br/> |[Autoriser les utilisateurs à contacter des utilisateurs Skype Entreprise externes](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype entreprise Online-messagerie instantanée, appels et présence avec des utilisateurs Skype (particuliers)  <br/> |Les administrateurs peuvent permettre à leurs utilisateurs de Skype entreprise Online de se connecter à la messagerie instantanée, passer des appels et voir la présence avec des utilisateurs de Skype (consommateur).  <br/> |[Autoriser les utilisateurs Skype entreprise à ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Options de collaboration B2B Azure AD

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Collaboration B2B Azure AD-partage de contenu en ajoutant des utilisateurs externes à un groupe dans l’annuaire d’une organisation  <br/> |Un administrateur global d’un client Office 365 peut inviter des personnes dans un autre client Office 365 à rejoindre son annuaire, ajouter ces utilisateurs externes à un groupe et accorder l’accès à du contenu, tel que des sites et des bibliothèques SharePoint pour le groupe.  <br/> |[Qu’est-ce que Azure AD B2B collaboration preview?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Inter-entreprise B2B: nouvelles mises à jour collab](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Partage externe Office 365 et collaboration entre entreprises Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [API et personnalisation d’Azure Active Directory B2B](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD et Identity Show: Azure AD B2B collaboration (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Options de collaboration Office 365

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Groupes Office 365-messagerie, calendrier, OneNote et fichiers partagés à un emplacement central  <br/> |Les groupes sont pris en charge dans Business Essentials, Business Premium, éducation et les plans entreprise E1, E3 et E5. Les personnes d’un client Office 365 peuvent créer un groupe et inviter des personnes dans un autre client Office 365 en tant qu’utilisateurs invités. S’applique également à Dynamics CRM.  <br/> |[En savoir plus sur les groupes Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accès invité dans les groupes Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Déployer les groupes Office 365](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Options de collaboration Yammer

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Yammer-collaboration via un support social d’entreprise  <br/> |À moins que la possibilité de créer des groupes externes ne soit désactivée par un administrateur Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer par le biais de conversations, la possibilité d’utiliser des publications, de partager des fichiers et de converser en ligne.  <br/> |[Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Options de collaboration teams

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Collaborer dans teams avec des utilisateurs externes à l’Organisation  <br/> |Un administrateur général pour le client invité Office 365 doit activer la collaboration externe dans Teams. Les administrateurs globaux et les propriétaires d’équipe pourront désormais inviter quiconque disposant d’une adresse de messagerie à collaborer dans Teams.  <br/> Les administrateurs peuvent également gérer et modifier des invités déjà présents dans leur client.  <br/> |[Autoriser l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Activer ou désactiver l’accès invité dans teams](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Utiliser PowerShell pour contrôler l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Liste de vérification d’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Afficher les utilisateurs invités](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Modifier les informations de l’utilisateur invité](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Les propriétaires d’équipe peuvent inviter et gérer la collaboration des invités au sein de leurs équipes.  <br/> |Les propriétaires d’équipe disposent de contrôles supplémentaires sur ce que les invités peuvent faire au sein de leurs équipes.  <br/> |[Ajouter des invités](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Ajouter un invité à une équipe](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Gérer l’accès invité dans teams](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Afficher les utilisateurs d’une équipe ou d’un canal](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Les invités d’autres clients peuvent afficher le contenu dans teams et collaborer avec d’autres membres  <br/> |Aucun.  <br/> |[Expérience d’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Options de collaboration Power BI

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Power BI permet aux utilisateurs d’invités externes de consommer le contenu qui leur est partagé par le biais de liens. Cela permet aux utilisateurs de l’organisation de répartir le contenu de manière sécurisée entre les organisations.<br/> | L’administrateur Power BI peut contrôler si les utilisateurs peuvent inviter des utilisateurs externes à afficher le contenu au sein de l’organisation. <br/> |[Distribution de contenu Power BI à des utilisateurs d’invités externes avec Azure AD B2B](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Points à prendre en compte concernant la collaboration intersites Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage des comptes d’utilisateur, des licences, des abonnements et du stockage

Chaque organisation gère ses propres comptes d’utilisateur, identités, groupes de sécurité, abonnements, licences et stockage. Les utilisateurs utilisent les fonctionnalités de collaboration dans Office 365 avec des stratégies de partage et des paramètres de sécurité pour fournir un accès aux informations nécessaires tout en maintenant le contrôle des biens de l’entreprise.
  
- **Comptes d’utilisateur:** Les comptes ne peuvent pas être partagés et les comptes ne peuvent pas être dupliqués entre les clients ou les partitions dans les services d’annuaire Active Directory locaux. 
    
- **Abonnements de licences &amp; :** Dans Office 365, les licences des plans de gestion des licences (également appelés «SKU» ou «offres Office 365») permettent aux utilisateurs d’accéder aux services Office 365 définis pour ces plans. 
    
- **Stockage:** Dans les plans Office 365, les limites et limites logicielles pour SharePoint Online sont gérées séparément des limites de stockage des boîtes aux lettres. Les limites de stockage des boîtes aux lettres sont configurées et gérées à l’aide d’Exchange Online. Dans les deux cas, le stockage ne peut pas être partagé entre les locataires. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Puis-je partager des espaces de noms de domaine entre les clients Office 365?

Non. Les domaines personnel, tels que fabrikam.com ou tailspintoys.com, ne peuvent être associés qu’à un seul client à la fois. Chaque client doit disposer de son propre espace de noms; Les espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre les clients.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Qu’en est-il des composants hybrides et de la collaboration entre les clients Office 365?

Les composants hybrides locaux, tels qu’une organisation Exchange et Azure AD Connect, ne peuvent pas être répartis entre plusieurs clients.
  

