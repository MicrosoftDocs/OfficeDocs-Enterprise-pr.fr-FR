---
title: Collaboration inter-client dans Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Découvrez le fonctionne d’Office 365 collaboration entre les clients et les organisations.
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540389"
---
# <a name="office-365-inter-tenant-collaboration"></a>Collaboration inter-client dans Office 365

Cet article décrit plusieurs façons de collaborer entre deux clients Office 365. Elle est destinée aux administrateurs d’Office 365.
  
Supposons que deux organisations, Fabrikam et Contoso, chacun ont un Office 365 pour les clients d’entreprise et qu’ils souhaitent travailler ensemble sur plusieurs projets ; certains d'entre eux s’exécutent pendant une durée limitée et certains d'entre eux sont en cours. Comment Fabrikam et Contoso permettent les personnes et les équipes à collaborer plus efficacement entre les différents clients Office 365 de manière sécurisée ? Office 365, conjointement avec la collaboration d’Azure Active Directory B2B, fournit plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et Contoso peuvent prendre en compte.
  
À l’aide d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, à l’aide de la messagerie instantanée sont les options de collaboration entre client Office 365, appels audio/vidéo pour une communication et sécuriser l’accès aux ressources et des applications. Utilisez les tableaux suivants pour sélectionner les solutions et en savoir plus.
  
## <a name="exchange-online-collaboration-options"></a>Options de collaboration Exchange Online

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Partager des calendriers avec une autre organisation Office 365  <br/> |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et pour permettre aux utilisateurs de partager les planifications (informations disponible/occupé) avec d’autres personnes  <br/> |[Partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relations d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Créer une relation d'organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modifier et relation d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Supprimer une relation d’organisation dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation  <br/> |Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs à contrôler qui peut être partagée avec et le niveau d’accès accordé  <br/> |[Partage de stratégies dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Créer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Appliquer une stratégie de partage aux boîtes aux lettres dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modifier, désactiver ou supprimer une stratégie de partage dans Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurer des canaux de messagerie sécurisée et contrôler le flux de messagerie avec des organisations partenaires  <br/> |Administrateurs de créer des connecteurs pour appliquer la sécurité à l’échange de messages de messagerie avec une organisation partenaire ou un fournisseur de services. Les connecteurs d’appliquent le chiffrement via le protocole TLS (TLS) ainsi que d’autoriser des restrictions sur les noms de domaine ou vos partenaires envoyer un message électronique à partir de plages d’adresses IP.  <br/> |[Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie dans Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domaines distants dans Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurer le connecteur pour le flux de messagerie sécurisée avec une organisation partenaire](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Meilleures pratiques en matière de flux de messagerie pour Exchange Online et Office 365 (aperçu)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online et OneDrive pour les options de collaboration d’entreprise

|**Partage des objectifs**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes  <br/> |Administrateurs de configurer le client de partage ou de niveau collection de sites pour le compte Microsoft authentifiés, bureau ou une école compte comptes authentifiés ou invités  <br/> |
  [Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Domaines restreints partage dans Office 365, SharePoint Online et OneDrive entreprise](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Utilisez SharePoint Online en tant qu’une solution extranet d’entreprise-entreprise (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Suivi et contrôle le partage externe pour les utilisateurs finaux  <br/> |OneDrive pour les propriétaires de fichiers d’entreprise et les utilisateurs finaux SharePoint Online configurer des sites et partage de documents et établir des notifications pour effectuer le suivi de partage  <br/> |[Configurer les notifications d’un partage externe de OneDrive entreprise](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Partager des fichiers ou dossiers SharePoint dans Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype pour les options de collaboration d’entreprise

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Skype pour Business Online - appels, messagerie instantanée et présence avec les autres Skype pour les utilisateurs professionnels  <br/> |Les administrateurs peuvent activer leur Skype pour les utilisateurs professionnels en ligne à la messagerie instantanée, émettre des appels audio/vidéo et présence avec des utilisateurs dans un autre client Office 365.  <br/> |[Permettre aux utilisateurs de contacts Skype externe pour les utilisateurs professionnels](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype pour Business Online - messagerie instantanée, les appels et la présence avec les utilisateurs Skype (consommateur)  <br/> |Les administrateurs peuvent activer leur Skype pour les utilisateurs professionnels en ligne à la messagerie instantanée, émettre des appels et présence avec les utilisateurs Skype (consommateur).  <br/> |[Permettre Skype pour les utilisateurs d’ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Options AD B2B Collaboration Azure

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Azure AD B2B collaboration - partage en ajoutant des utilisateurs externes à un groupe dans le répertoire d’une organisation de contenu  <br/> |Un administrateur global pour un client Office 365 peut inviter des personnes dans une autre organisation cliente Office 365 pour participer à leur répertoire, ajoutez les utilisateurs externes à un groupe et accorder l’accès au contenu, tels que des sites SharePoint et des bibliothèques pour le groupe.  <br/> |[Nouveautés d’aperçu de collaboration Azure AD B2B ?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B : Nouvelles mises à jour facilitent la collaboration entre-business](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Partage externe Office 365 et Azure Active Directory B2B collaboration](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B collaboration API et la personnalisation](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD et afficher des identités : Collaboration Azure AD B2B (commerciaux](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Options de collaboration Office 365

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Groupes d’Office 365 - courrier, calendrier, OneNote et les fichiers partagés dans un emplacement central  <br/> |Les groupes sont pris en charge dans Business Essentials, entreprise Premium, éducation et les plans d’entreprise E1, E3 et E5. Personnes dans une organisation cliente Office 365 peut créer un groupe et inviter des personnes dans une autre organisation cliente Office 365 comme des utilisateurs invités. S’applique également à Dynamics CRM.  <br/> |[En savoir plus sur les groupes d’Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Accès invité dans Office 365 groupes](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Déploiement des groupes d’Office 365](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Options de collaboration Yammer

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Yammer - Collaboration via un support social d’entreprise  <br/> |Sauf si la possibilité de créer des groupes externes est désactivée par un administrateur de Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer par le biais de conversations, la possibilité de like et suivez les billets, partager des fichiers et conversation en ligne.  <br/> |[Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Options de collaboration des équipes

|**Objectif de partage**|**Action d’administration**|**Informations d’ordre général**|
|:-----|:-----|:-----|
|Collaborer en équipe avec des utilisateurs externes à l’organisation  <br/> |Un administrateur global pour le client Office 365 invitation doit activer la collaboration externe dans les équipes. Les propriétaires de l’équipe et les administrateurs globaux pourront désormais inviter quiconque avec une adresse de messagerie pour la collaboration en équipe.  <br/> Administrateurs peuvent également gérer et modifier les invités déjà présentes dans leur client.  <br/> |[Autoriser l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Activer ou désactiver les accès invité dans les équipes](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Utiliser PowerShell pour contrôler l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Liste de vérification de l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Afficher les utilisateurs d’invité](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Modifier les informations utilisateur invité](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Les propriétaires de l’équipe peuvent inviter et gérer comment invités collaborent au sein de leurs équipes.  <br/> |Les propriétaires de l’équipe ont des contrôles supplémentaires sur ce que les invités peuvent faire dans leurs équipes.  <br/> |[Ajouter des invités](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Ajouter un invité à une équipe](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Gérer l’accès invité dans les équipes](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Voir qui est d’une équipe ou dans un canal d’échange](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Invités à partir d’autres clients peuvent afficher le contenu dans les équipes et collaborer avec les autres membres  <br/> |Aucun.  <br/> |[L’expérience de l’accès invité](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Points à connaître à propos de la collaboration entre locataires de Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage de stockage, les licences, les abonnements et les comptes d’utilisateurs

Chaque organisation gère ses propres comptes d’utilisateurs, des identités, groupes de sécurité, abonnements, licences et de stockage. Personnes utilisent les fonctionnalités de collaboration dans Office 365 avec partage de stratégies et paramètres de sécurité pour fournir l’accès aux informations nécessaires tout en conservant le contrôle de ressources d’entreprise.
  
- **Les comptes d’utilisateurs :** Comptes ne peuvent pas être partagés et comptes ne peut pas être dupliquées entre les clients ou les partitions dans les Services de répertoire Active Directory local. 
    
- **Licences &amp; abonnements :** Dans Office 365, les licences de plans de gestion des licences (également appelées références ou Office 365 plans) donner aux utilisateurs l’accès aux services qui sont définies pour les plans Office 365. 
    
- **Stockage :** Dans les plans Office 365 et frontières logicielles pour SharePoint Online sont gérés séparément à partir des limites de stockage de boîtes aux lettres. Limites de stockage de boîtes aux lettres sont définies et gérées à l’aide en ligne Exchange. Dans les deux scénarios de stockage ne peuvent pas être partagé entre les clients. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Pouvons nous partager des espaces de noms de domaine entre les clients Office 365 ?

Non. Redirection domaines, tels que fabrikam.com ou tailspintoys.com, seulement pouvant être associés et utilisées avec un client à l’heure. Chaque client doit avoir son propre espace de noms ; Espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre des clients.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Qu’advient-il des composants hybride et de collaboration de cliente entre Office 365 ?

Composants hybrides locaux, tels que d’une organisation Exchange et de la connexion Azure AD ne peut pas être réparties entre plusieurs clients.
  

