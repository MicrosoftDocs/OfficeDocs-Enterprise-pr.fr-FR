---
title: Collaboration intersites Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Découvrez comment fonctionne la collaboration Microsoft 365 entre les clients et les organisations, ce qui permet à différentes organisations de collaborer en toute sécurité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e68df7c7b4d3574951957f576ffe7c896c0d13da
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606560"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Collaboration intersites Microsoft 365

Cet article décrit plusieurs méthodes de collaboration entre deux clients Microsoft 365. Elle est destinée aux administrateurs de Microsoft 365.
  
Supposons que deux organisations, Fabrikam et contoso, ont chacune un client Microsoft 365 pour les entreprises et qu’elles souhaitent collaborer sur plusieurs projets ; certains d’entre eux s’exécutent pendant une période limitée, dont certains sont en cours. Comment Fabrikam et contoso permettent-ils à leurs personnes et équipes de collaborer plus efficacement sur leurs différents clients Microsoft 365 de manière sécurisée ? Microsoft 365, en association avec Azure Active Directory B2B collaboration, propose plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et contoso peuvent prendre en compte.
  
Les options de collaboration inter-locataire de Microsoft 365 incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, les appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications. Utilisez les tableaux suivants pour sélectionner des solutions et en savoir plus.
  
## <a name="exchange-online-collaboration-options"></a>Options de collaboration Exchange Online

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Partager des calendriers avec une autre organisation Microsoft 365  <br/> |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et de permettre aux utilisateurs de partager les planifications (informations de disponibilité) avec d’autres utilisateurs.  <br/> |[Partage dans Exchange Online](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relations d’organisation dans Exchange Online](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) <br/> [Créer une relation d’organisation dans Exchange Online](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modifier une relation d’organisation dans Exchange Online](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) <br/> [Supprimer une relation d’organisation dans Exchange Online](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) <br/> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation  <br/> |Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs pour contrôler les personnes avec lesquelles elles peuvent être partagées, ainsi que le niveau d’accès accordé.  <br/> |[Stratégies de partage dans Exchange Online](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) <br/> [Créer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) <br/> [Appliquer une stratégie de partage à des boîtes aux lettres dans Exchange Online](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modifier, désactiver ou supprimer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurer des canaux de messagerie sécurisés et contrôler le flux de messagerie avec des organisations partenaires  <br/> |Les administrateurs créent des connecteurs pour appliquer la sécurité aux échanges de messages avec une organisation partenaire ou un fournisseur de services. Les connecteurs appliquent le chiffrement via le protocole TLS (Transport Layer Security) et autorisent les restrictions sur les noms de domaine ou les plages d’adresses IP à partir desquels vos partenaires envoient des messages.  <br/> |[Utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](https://technet.microsoft.com/library/mt163898.aspx) <br/> [Configurer le flux de messagerie à l’aide des connecteurs](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domaines distants dans Exchange Online](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurer un connecteur pour un flux de messagerie sécurisé avec une organisation partenaire](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) <br/> [Meilleures pratiques en matière de flux de messagerie pour Exchange Online (vue d’ensemble)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Options de collaboration SharePoint Online et OneDrive entreprise

|**Objectifs de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes  <br/> |Les administrateurs configurent le partage au niveau du client ou de la collection de sites pour le compte Microsoft authentifié, professionnel ou scolaire comptes authentifiés ou invités  <br/> |[Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Restreindre le partage de contenu SharePoint et OneDrive par domaine](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) <br/> [Utiliser SharePoint Online comme solution extranet B2B (Business-to-Business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Suivi et contrôle du partage externe pour les utilisateurs finaux  <br/> |Propriétaires de fichiers OneDrive entreprise et utilisateurs finaux SharePoint Online configurer le partage de sites et de documents et établir des notifications pour le suivi du partage  <br/> |[Configurer les notifications pour le partage externe pour OneDrive entreprise](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Partager des fichiers SharePoint ou des dossiers](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Options de collaboration Skype entreprise

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Skype entreprise Online-messagerie instantanée, appels et présence avec d’autres utilisateurs de Skype entreprise  <br/> |Les administrateurs peuvent permettre à leurs utilisateurs de Skype entreprise Online de se connecter à la messagerie instantanée, passer des appels audio/vidéo et voir la présence avec les utilisateurs d’un autre client Microsoft 365.  <br/> |[Autoriser les utilisateurs à contacter des utilisateurs Skype Entreprise externes](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype entreprise Online-messagerie instantanée, appels et présence avec des utilisateurs Skype (particuliers)  <br/> |Les administrateurs peuvent permettre à leurs utilisateurs de Skype entreprise Online de se connecter à la messagerie instantanée, passer des appels et voir la présence avec des utilisateurs de Skype (consommateur).  <br/> |[Autoriser les utilisateurs Skype Entreprise à ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Options de collaboration B2B Azure AD

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Collaboration B2B Azure AD-partage de contenu en ajoutant des utilisateurs externes à un groupe dans l’annuaire d’une organisation  <br/> |Un administrateur global pour un client Microsoft 365 peut inviter des personnes dans un autre client Microsoft 365 à rejoindre son annuaire, ajouter ces utilisateurs externes à un groupe et accorder l’accès à du contenu, tel que des sites et des bibliothèques SharePoint pour le groupe.  <br/> |[Qu’est-ce que Azure AD B2B collaboration preview ?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Inter-entreprise B2B : nouvelles mises à jour collab](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Partage externe et collaboration B2B Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [API et personnalisation d’Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD et Identity Show : Azure AD B2B collaboration (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="microsoft-365-collaboration-options"></a>Options de collaboration Microsoft 365

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Groupes Microsoft 365-messagerie, calendrier, OneNote et fichiers partagés à un emplacement central  <br/> |Les groupes sont pris en charge dans Business Essentials, Business Premium, éducation et les plans entreprise E1, E3 et E5. Les personnes d’un client Microsoft 365 peuvent créer un groupe et inviter des personnes dans un autre client Microsoft 365 en tant qu’utilisateurs invités. S’applique également à Dynamics CRM.  <br/> |[En savoir plus sur les groupes Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accès invité dans les groupes Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Déployer des groupes Microsoft 365](https://technet.microsoft.com/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Options de collaboration Yammer

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Yammer-collaboration via un support social d’entreprise  <br/> |À moins que la possibilité de créer des groupes externes ne soit désactivée par un administrateur Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer par le biais de conversations, la possibilité d’utiliser des publications, de partager des fichiers et de converser en ligne.  <br/> |[Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Options de collaboration teams

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Collaborer dans teams avec des utilisateurs externes à l’Organisation  <br/> |Un administrateur général pour le client invité de Microsoft 365 doit activer la collaboration externe dans Teams. Les administrateurs globaux et les propriétaires d’équipe pourront désormais inviter quiconque disposant d’une adresse de messagerie à collaborer dans Teams.  <br/> Les administrateurs peuvent également gérer et modifier des invités déjà présents dans leur client.  <br/> |[Autoriser l’accès invité](https://docs.microsoft.com/microsoftteams/teams-dependencies) <br/> [Activer ou désactiver l’accès invité dans teams](https://docs.microsoft.com/microsoftteams/set-up-guests) <br/> [Utiliser PowerShell pour contrôler l’accès invité](https://docs.microsoft.com/microsoftteams/guest-access-powershell) <br/> [Liste de vérification d’accès invité](https://docs.microsoft.com/microsoftteams/guest-access-checklist) <br/> [Afficher les utilisateurs invités](https://docs.microsoft.com/microsoftteams/view-guests) <br/> [Modifier les informations d’un utilisateur invité](https://docs.microsoft.com/microsoftteams/edit-guests-information) <br/> |
|Les propriétaires d’équipe peuvent inviter et gérer la collaboration des invités au sein de leurs équipes.  <br/> |Les propriétaires d’équipe disposent de contrôles supplémentaires sur ce que les invités peuvent faire au sein de leurs équipes.  <br/> |[Ajouter des invités](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Ajouter un invité à une équipe](https://docs.microsoft.com/microsoftteams/add-guests) <br/> [Gérer l’accès invité dans teams](https://docs.microsoft.com/microsoftteams/manage-guests) <br/> [Afficher les utilisateurs d’une équipe ou d’un canal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Les invités d’autres clients peuvent afficher le contenu dans teams et collaborer avec d’autres membres  <br/> |Aucun.  <br/> |[Expérience d’accès invité](https://docs.microsoft.com/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Options de collaboration Power BI

|**Objectif de partage**|**Action administrative**|**Informations sur les procédures**|
|:-----|:-----|:-----|
|Power BI permet aux utilisateurs d’invités externes de consommer le contenu qui leur est partagé par le biais de liens. Cela permet aux utilisateurs de l’organisation de répartir le contenu de manière sécurisée entre les organisations.<br/> | L’administrateur Power BI peut contrôler si les utilisateurs peuvent inviter des utilisateurs externes à afficher le contenu au sein de l’organisation. <br/> |[Distribution de contenu Power BI à des utilisateurs d’invités externes avec Azure AD B2B](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Points à prendre en compte concernant la collaboration intersites Microsoft 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage des comptes d’utilisateur, des licences, des abonnements et du stockage

Chaque organisation gère ses propres comptes d’utilisateur, identités, groupes de sécurité, abonnements, licences et stockage. Les utilisateurs utilisent les fonctionnalités de collaboration de Microsoft 365 avec les stratégies de partage et les paramètres de sécurité pour fournir un accès aux informations nécessaires tout en maintenant le contrôle des biens de l’entreprise.
  
- **Comptes d’utilisateur :** Les comptes ne peuvent pas être partagés et les comptes ne peuvent pas être dupliqués entre les clients ou les partitions dans les services d’annuaire Active Directory locaux. 
    
- ** &amp; Abonnements de licences :** dans Microsoft 365, les licences des plans de gestion des licences (également appelés sku ou Microsoft 365 plans) permettent aux utilisateurs d’accéder aux services Microsoft 365 définis pour ces plans. 
    
- **Stockage :** Dans les plans Microsoft 365, les limites et limites logicielles pour SharePoint Online sont gérées séparément des limites de stockage des boîtes aux lettres. Les limites de stockage des boîtes aux lettres sont configurées et gérées à l’aide d’Exchange Online. Dans les deux cas, le stockage ne peut pas être partagé entre les locataires. 
    
### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Puis-je partager des espaces de noms de domaine entre les clients Microsoft 365 ?

Non. Les domaines personnel, tels que fabrikam.com ou tailspintoys.com, ne peuvent être associés qu’à un seul client à la fois. Chaque client doit disposer de son propre espace de noms ; Les espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre les clients.
  
### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Qu’en est-il des composants hybrides et de la collaboration inter-clients Microsoft 365 ?

Les composants hybrides locaux, tels qu’une organisation Exchange et Azure AD Connect, ne peuvent pas être répartis entre plusieurs clients.
  

