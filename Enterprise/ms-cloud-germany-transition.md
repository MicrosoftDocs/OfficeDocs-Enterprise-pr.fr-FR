---
title: Migration de Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) vers les services Office 365 dans les nouvelles régions de centre de données allemandes
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
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
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Récapitulatif : comprendre la migration de Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) vers les services Office 365 dans les nouvelles régions de centre de données allemandes.'
ms.openlocfilehash: d8b02d149083095793ef2038c8df3d9b62e7cba8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844875"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Migration de Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) vers les services Office 365 dans les nouvelles régions de centre de données allemandes


>[!Note]
>Cet article s’applique uniquement aux clients Microsoft Cloud Allemagne/Deutschland éligibles.
>

## <a name="cloud-service-offerings-in-germany"></a>Offres de service Cloud en Allemagne

En août 2018, nous avons annoncé notre volonté d’offrir la suite Microsoft Cloud (Azure, Office 365, Dynamics 365 et Power Platform), des nouvelles régions Cloud en Allemagne pour améliorer la transformation numérique de nos clients. En août 2019, nous avons annoncé que nous sommes désormais en train d’ouvrir les nouvelles régions dans le Cloud en Allemagne. Nous avons annoncé la disponibilité d’Azure en août et Office 365 est devenu disponible en décembre.  Dynamics 365 et Power Platform sont anticipés pour devenir disponibles au cours du premier trimestre de 2020.  

Les nouvelles régions sont conçues pour répondre aux besoins changeants des clients allemands avec la plus grande flexibilité, les derniers services cloud intelligents et la connectivité complète à notre réseau cloud mondial, ainsi que la résidence des données client en Allemagne.

## <a name="moving-to-the-new-german-regions"></a>Transition vers les nouvelles régions allemandes

Les clients Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) existants peuvent désormais migrer leurs clients Office 365, Dynamics 365 Customer engagement et Power Platform BI.  La première étape consiste à [opter pour une migration dirigée par Microsoft](https://aka.ms/office365germanymoveoptin) vers nos nouvelles régions de centre de données allemandes.

Pour les organisations qui choisissent d’adopter l’approche dirigée par Microsoft, les migrations doivent se produire en 2020. Suite à la migration, les données client principales et les abonnements sont transférés vers les nouvelles régions allemandes. 

Les services suivants seront migrés dans le cadre de l’approche dirigée par Microsoft :

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive Entreprise
- Skype Entreprise Online

Pendant la migration de Microsoft Cloud Allemagne vers le centre de données allemand, les clients Skype Entreprise Online existants seront transférés vers Microsoft Teams. Voir [Prise en main de votre mise à niveau de Microsoft Teams](https://aka.ms/SkypeToTeams-Home) pour plus d’informations.

- Groupes Office 365
- Dynamics 365/Power Platform

Les conditions préalables et l’impact de la migration sur ces services sont décrits dans l’article [Dynamics 365 for Customer Engagement](https://aka.ms/D365ceOptIn).

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Comment préparer la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes

La première étape consiste à avertir Microsoft pour avoir votre autorisation de migrer votre abonnement et vos données de Microsoft Cloud Allemagne/Deutschland vers les services Office 365 dans les nouvelles régions de centre de données allemandes.  Pour obtenir des instructions, voir [processus de connexion](ms-cloud-germany-migration-opt-in.md).

- Tous les clients migrants doivent vérifier la connectivité aux [URL et adresses IP Office 365](urls-and-ip-address-ranges.md) du monde entier, lesquelles incluent les nouvelles régions de centre de données allemandes.
- Consultez la description du service de plateforme Office 365 pour comprendre les fonctionnalités et services qui seront mis à la disposition de votre organisation suite à l’achèvement pour la région allemande. 
- La migration entraîne la transition des abonnements payants.  Nous ne pouvons pas déplacer les abonnements d’évaluation.

Les migrations de client sont exécutées en tant qu’opérations de service back-end avec une interaction minimale requise du client.  Toutes les tâches supplémentaires dirigées par le client et l’état de la migration globale sont notifiés via le Centre de messages pendant le processus de migration.  Par exemple, les tâches peuvent inclure des mises à jour DNS gérées par les clients ou une reconfiguration de la configuration hybride pour les clients hybrides Exchange.

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Expérience client pendant la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes

Les migrations client ont été conçues pour avoir un impact minime sur les clients finaux et les administrateurs.  Toutefois, il existe des facteurs à prendre en compte pour chaque charge de travail.  

### <a name="azure-active-directory"></a>Azure Active Directory

Les abonnements Office/Dynamics de Microsoft Cloud Allemagne sont transférés vers la région allemande avec la mutation d’Azure Active Directory (Azure AD). L’organisation est alors mise à jour pour prendre en compte les nouveaux abonnements au service international. Pendant le court processus de transfert d’abonnement, les modifications apportées aux abonnements sont bloquées.

### <a name="exchange-online"></a>Exchange Online

Les clients hybrides Exchange Online doivent réexécuter l’Assistant Configuration hybride pour mettre à jour la configuration locale de Microsoft Cloud Allemagne avant la transition, et réexécuter l’Assistant Configuration hybride lors du nettoyage sur le service international. D’autres mises à jour de DNS peuvent être requises pour les clients disposant de domaines personnalisés.

Les boîtes aux lettres sont déplacées au cours d’un processus back-end, les utilisateurs au sein de votre organisation peuvent se trouver dans Microsoft Cloud Allemagne ou une région allemande pendant la transition et font partie de la même organisation Exchange (GAL)

### <a name="exchange-online-protection"></a>Exchange Online Protection

Les fonctionnalités d’Exchange Online Protection back-end sont copiées vers la nouvelle région d’Allemagne

### <a name="sharepoint-online"></a>SharePoint Online

Une fois la migration de SharePoint Online vers la région allemande terminée, les index de données sont recréés. Les fonctionnalités dépendantes des index de recherche peuvent être affectées lorsque la réindexation est terminée.

Les URL sharepoint.de existantes sont conservées pour les organisations transférées.

### <a name="onedrive-for-business"></a>OneDrive Entreprise

Une fois la migration de OneDrive Entreprise vers la région allemande terminée, les index de données sont recréés. Les fonctionnalités dépendantes des index de recherche peuvent être affectées lorsque la réindexation est terminée.

### <a name="skype-for-business-online"></a>Skype Entreprise Online

Les clients Skype Entreprise Online existants sont transférés vers Microsoft Teams. Pour plus d’informations, voir [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home).


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>Différences clés entre Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) et les services Office 365 dans les nouvelles régions de centre de données allemandes


|| Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) | Services Office 365 dans les nouvelles régions de centre de données allemandes |
|:-------|:-----|:-----|
| Services Microsoft 365 disponibles pour un abonnement avec un seul client Office 365 | 15 services (voir REF) | 29 services (voir REF) |
| Nouvelles fonctionnalités | Aucune nouvelle fonctionnalité n’est disponible. | De nouvelles fonctionnalités sont disponibles en cohérence avec les services Office 365 globaux. |
| Administrateur de données | Oui | Non |
| Collaboration entre clients Office 365 du monde entier | Non | Oui |
| Résidence des données client | Les données client sont stockées uniquement dans les centres de données allemands. | Microsoft stockera les données client suivantes exclusivement en Allemagne : contenu de la boîte aux lettres Exchange Online (corps des e-mails, entrées de calendrier et contenu des pièces jointes aux e-mails), contenu du site SharePoint Online et fichiers stockés dans ce site, fichiers téléchargés dans OneDrive Entreprise. |
| Conditions applicables | [Conditions d’utilisation d’Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) avec [supplément](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Conditions d’utilisation d’Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="is-migration-required"></a>La migration est-elle obligatoire ?

Microsoft offre la migration des clients Office 365 de Microsoft Cloud Allemagne vers les services Office 365 dans les nouvelles régions de centre de données allemandes sans frais supplémentaires.  Bien qu’il soit vivement recommandé d’opter pour la migration vers les nouvelles régions de centre de données allemandes, nous continuerons à fournir les mises à jour de sécurité nécessaires à la région Microsoft Cloud Allemagne.  

Les services Office 365 dans les nouvelles régions de centre de données allemandes offrent des avantages supplémentaires :

- Ils offrent des tarifs compétitifs pour [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer engagement](https://dynamics.microsoft.com/pricing/)et [Power BI](https://powerbi.microsoft.com/pricing/). 
- Ils sont connectés au réseau mondial Microsoft, offrant des centaines de sites de réseau Edge, d’emplacements d’homologation et de points de sortie pour offrir une expérience utilisateur puissante n’importe où dans le monde. 
- Ils vous aident à répondre aux exigences de résidence des données client en Allemagne. 
- Ils fournissent notre offre globale de cloud complète, y compris la dernière version de nos services et les nouvelles fonctionnalités, dont Microsoft Teams et Multi-Géo dans Office 365. Ils permettent de comparer les produits par région pour [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://products.office.com/fr-FR/where-is-your-data-located) et [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).
- Ils offrent toutes les fonctionnalités, une sécurité de qualité professionnelle et des fonctionnalités complètes pour aider les clients à respecter les exigences de conformité et de réglementation. 
- Ils sont accessibles via les contrats de services en ligne existants.

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>Quelle est la disponibilité du service entre les différentes offres de service Cloud d’Office 365 ?

Les 15 services suivants sont disponibles dans l’offre de service Cloud Microsoft Cloud Allemagne (Microsoft Cloud Deutschland).  Nous n’ajoutons pas de nouveaux services à Microsoft Cloud Allemagne.

1. Exchange Online
2. Customer Lockbox (Exchange Online)
3. Groupes (groupes modernes)
4. Profil Delve
5. Exchange Online Protection
6. Protection avancée contre les menaces (ATP)
7. Advanced eDiscovery
8. Gouvernance des données avancée
9. SharePoint Online
10. Customer Lockbox (SharePoint Online)
11. OneDrive Entreprise
12. Skype Entreprise
13. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
14. Office 365 Pro Plus
15. Outlook Mobile

Nous avons actuellement 29 services dans le cadre des services Office 365 dans les nouvelles régions de centres de données allemands.  De nouvelles fonctionnalités et de nouveaux services sont régulièrement disponibles avec les services Office 365 globaux.

1. Exchange Online
2. Customer Lockbox (Exchange Online)
3. Groupes (groupes modernes)
4. Profil Delve
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Protection avancée contre les menaces (ATP)
9. Advanced eDiscovery
10. Gestion de la sécurité avancée
11. Gestion des droits relatifs à l’information
12. Gouvernance des données avancée
13. SharePoint Online
14. Customer Lockbox (SharePoint Online)
15. OneDrive Entreprise
16. Microsoft Stream
17. Skype Entreprise (effectuera la transition vers Microsoft Teams pendant la migration)
18. PBX cloud
19. Conférence sur réseau téléphonique commuté
20. Appel sur réseau téléphonique commuté
21. Microsoft Teams
22. Rapports d’administration/rapports d’utilisation
23. Word Online, Excel Online, PowerPoint, OneNote et Visio Online
24. Planificateur
25. Sway
26. Office 365 Pro Plus
27. Outlook Mobile
28. EMS E3 (Azure Active Directory Premium P1 + Intune + Service Gestion des droits)
29. Yammer Online

### <a name="when-will-migration-happen"></a>Quand la migration aura-t-elle lieu ?

#### <a name="azure"></a>Azure 

Vous pouvez commencer à [migrer](https://docs.microsoft.com/azure/germany/germany-migration-main) vos ressources Azure vers une autre région aujourd’hui. Si vous utilisez Azure avec Office 365, Dynamics 365 et/ou Power BI, procédez comme suit.

#### <a name="office-365"></a>Office 365

[Optez](https://aka.ms/office365germanymoveoptin) pour la migration dirigée par Microsoft aujourd’hui. Lorsque nous serons prêts à démarrer votre migration, nous vous informerons via le [Centre de messages](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) dans le Centre d’administration Microsoft 365.

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 et Power BI

Optez pour la migration dirigée par Microsoft pour [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) et [Power BI aujourd’hui](https://aka.ms/pbioptin). Lorsque nous serons prêts à démarrer votre migration, nous vous informerons via le [centre de messages](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) dans le Centre d’administration Microsoft 365.

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>Le prix changera-t-il pour les services Office que j’utilise ?

Oui, les prix dans les régions de cloud global de Microsoft (y compris les nouvelles régions de centre de données) sont généralement moins élevés.

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>Comment obtenir de l’aide de la part de Microsoft pour effectuer la migration vers une nouvelle région ou répondre à des questions de support ?

Si vous avez des questions, vous pouvez nous contacter comme suit ou via votre partenaire :

- Pour Azure, vous pouvez envoyer de [nouvelles demandes de support](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) dans le portail Azure.
- Pour Office 365, vous pouvez envoyer des questions à l’aide de l’outil « Besoin d’aide ? » lien du [Centre d’administration Microsoft 365](https://portal.office.de/).
- Les clients de Dynamics 365 Customer Engagement et Power BI qui disposent également d’Office 365 peuvent envoyer des questions à l’aide de l’outil « Besoin d’aide ? » lien du [Centre d’administration Microsoft 365](https://portal.office.de/). Les options de support de Dynamics 365 Customer Engagement se trouvent [ici](https://docs.microsoft.com/dynamics365/get-started/support/). Les options de support de Power BI se trouvent [ici](https://powerbi.microsoft.com/support/).

## <a name="more-information"></a>Plus d’informations

- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](https://aka.ms/office365germanymoveoptin)
- [Informations sur le programme de migration Dynamics 365](https://aka.ms/D365ceOptIn)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [URL et plages d’adresses IP Office 365](https://aka.ms/o365endpoints)
- [Assistant de configuration hybride d’Office 365](https://aka.ms/HybridWizard)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
