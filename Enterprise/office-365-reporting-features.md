---
title: Fonctionnalités de création de rapports Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-analytics
f1.keywords:
- NOCSH
description: Explication des fonctionnalités de création de rapports dans Office 365.
ms.openlocfilehash: 51ae09471b748b6e40af5a5b02b23f755908efff
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41842031"
---
# <a name="office-365-reporting-features"></a>Fonctionnalités de création de rapports Office 365 

## <a name="introduction"></a>Introduction

La fonctionnalité de rapports dans Office 365 fournit différents rapports d’audit pour Azure Active Directory (AD), Exchange Online, la gestion des périphériques, la vérification de surveillance et la protection contre la perte de données (DLP). Ces rapports sont différents et distincts des rapports d’activité Office 365.

## <a name="office-365-reports-dashboard"></a>Tableau de bord des rapports Office 365

Le tableau de bord rapports de la version d’évaluation du centre d’administration Microsoft 365 affiche les activités d’utilisation dans Office 365. Les administrateurs globaux d’Office 365, ou un administrateur Exchange Online, SharePoint Online ou Skype entreprise, peuvent obtenir un aperçu précis de l’utilisation de ce service. Par exemple, le nombre d’utilisateurs dans un service Office 365 particulier, le nombre d’utilisateurs ayant activé Office professionnel plus et la quantité de courrier circulant dans l’organisation. Les rapports sont disponibles pour les 7, 30, 90 et 180 derniers jours.

Les rapports suivants sont disponibles :

- [Rapport d’activité de courrier électronique](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--Email-activity-1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44)
- [Rapport sur les activations de Microsoft Office](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--Microsoft-Office-activations-87c24ae2-82e0-4d1e-be01-c3bcc3f18c60)
- [Rapport d’utilisation du site SharePoint Online](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--SharePoint-site-usage-4ecfb843-e5d5-464d-8bf6-7ed512a9b213)
- [Rapport d’utilisation de OneDrive entreprise](https://support.office.com/article/Office-365-Reports-in-the-Admin-Center-Preview--OneDrive-for-Business-usage-0de3b312-c4e8-4e4b-a02d-32b2f726a680)
- [Rapport d’activité Yammer](https://support.office.com/article/View-the-Yammer-Activity-report-in-the-Office-365-admin-center-preview-c7c9f938-5b8e-4d52-b1a2-c7c32cb2312a)
- [Rapport d’activité Skype entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/activity-report)
- [Rapport d’activité P2P Skype entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/peer-to-peer-activity-report)
- [Rapport d’organisateur de conférences Skype entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/conference-organizer-activity-report)
- [Rapport d’activité de participation à des conférences Skype entreprise](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/conference-participant-activity-report)

Pour plus d’informations, reportez-vous [à rapports d’activité dans le centre d’administration Microsoft 365](https://support.office.com/article/activity-reports-in-the-office-365-admin-center-0d6dfb17-8582-4172-a9a9-aed798150263).

## <a name="azure-active-directory-reports"></a>Rapports Azure Active Directory

Office 365 utilise Azure AD pour l’authentification et la gestion des identités. Les administrateurs d’Office 365 utilisent des rapports générés par Azure pour identifier une activité inhabituelle et un accès non autorisé à leurs données. Vous pouvez utiliser les rapports d’accès et d’utilisation dans Azure AD pour obtenir une visibilité sur l’intégrité et la sécurité de l’annuaire pour votre organisation. Grâce à ces informations, vous pouvez identifier et atténuer les risques de sécurité possibles.

Les rapports Azure AD peuvent être exportés vers Microsoft Excel et mis en corrélation avec d’autres données à partir d’Office 365. Par exemple, les résultats d’une recherche dans le journal d’audit peuvent fournir un aperçu des activités d’accès, d’authentification et de niveau application. Les rapports d’utilisation des ressources et des anomalies avancées sont disponibles avec Azure AD Premium. Ces rapports avancés contribuent à améliorer la sécurité et vous aident à répondre aux menaces potentielles en appliquant des analyses sur l’accès aux appareils et sur l’utilisation des applications. Pour plus d’informations, consultez la rubrique [création de rapports Azure Active Directory](https://docs.microsoft.com/azure/active-directory/reports-monitoring/overview-reports/).

## <a name="exchange-online-audit-reports"></a>Rapports d’audit Exchange Online

Les rapports d’audit Exchange Online incluent des détails sur l’accès aux boîtes aux lettres et les modifications apportées par les administrateurs à votre client Exchange Online. Avec l’audit des boîtes aux lettres, vous pouvez utiliser les tâches décrites dans le tableau suivant pour exécuter des rapports et exporter des journaux d’audit Exchange Online.

> [!NOTE]
> Vous devez activer l’enregistrement d’audit de boîte aux lettres pour chaque boîte aux lettres afin que les événements audités soient enregistrés dans le journal d’audit de cette boîte aux lettres. Si la journalisation d’audit des boîtes aux lettres n’est pas activée pour une boîte aux lettres, les événements de cette boîte aux lettres ne seront pas enregistrés dans le journal d’audit et n’apparaîtront pas dans les rapports d’audit Pour plus d’informations, consultez la rubrique [activer l’audit de boîte aux lettres](https://support.office.com/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918).

| Tâche | Description |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Exécuter un rapport d'accès aux boîtes aux lettres par des non-propriétaires](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report) | Affiche la liste des boîtes aux lettres auxquelles une personne autre que le propriétaire de la boîte aux lettres a accédé. Le rapport contient des informations sur la personne ayant accédé à la boîte aux lettres, les actions qu’elle a effectuées dans la boîte aux lettres et si les actions ont réussi. |
| [Exporter les journaux d’audit de boîte aux lettres](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs) | Les journaux d’audit de boîte aux lettres contiennent des informations sur l’accès et les actions dans une boîte aux lettres effectuée par un utilisateur autre que le propriétaire de la boîte aux lettres. Les administrateurs peuvent spécifier des boîtes aux lettres avec une plage de dates pour générer des rapports. Les journaux sont exportés au format XML, joints à un message, et envoyés à des utilisateurs spécifiques en fonction de l’administrateur. |
| [Exécuter un rapport de groupe de rôles d’administrateur](https://docs.microsoft.com/Office365/SecurityCompliance/eop/run-an-administrator-role-group-report-in-eop-eop) | Le groupe de rôles administrateur attribue des privilèges d’administration aux utilisateurs. Ces privilèges permettent aux utilisateurs d’effectuer des tâches d’administration telles que la réinitialisation des mots de passe, la création ou la modification de boîtes aux lettres et l’attribution de privilèges d’administrateur à d’autres utilisateurs. Le rapport de groupe de rôles d’administrateur affiche les modifications apportées aux groupes de rôles, y compris l’ajout ou la suppression de membres. |
| [Afficher le journal d’audit de l’administrateur](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log) | Le rapport du journal d’audit de l’administrateur répertorie toutes les fonctions de création, de mise à jour et de suppression effectuées par les administrateurs dans Exchange Online. Les entrées de journal fournissent des informations sur la cmdlet qui a été exécutée, les paramètres utilisés, l’utilisateur qui a exécuté la cmdlet et les objets affectés. |
| [Recherche et conservation du contenu de boîte aux lettres](https://docs.microsoft.com/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) | Fournit des détails sur les modifications apportées à la découverte électronique inaltérable ou aux paramètres de conservation inaltérable sur les boîtes aux lettres. |
| [Exporter le journal d’audit de l’administrateur](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes) | Le journal d’audit de l’administrateur enregistre des actions administratives spécifiques, telles que la création, la mise à jour et la suppression dans Exchange Online. Les résultats du journal sont exportés au format XML et les administrateurs peuvent choisir d’envoyer ce journal à un ensemble d’utilisateurs. |
| [Rapport de mise en attente pour litige par boîte aux lettres](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/per-mailbox-litigation-hold-report) | Fournit des détails sur les modifications apportées aux paramètres de conservation pour litige sur les boîtes aux lettres. |
| [Afficher et exporter le journal d’audit de l’administrateur externe](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-external-admin-audit-log) | Contient les détails des actions effectuées par les administrateurs externes. Les entrées fournissent des informations sur la cmdlet qui a été exécutée, les paramètres utilisés et les actions de création, de modification ou de suppression d’objets dans Exchange Online. |

## <a name="device-compliance-reports"></a>Rapports de conformité des appareils

Vous pouvez gérer et sécuriser les appareils mobiles connectés à votre organisation Office 365 à l’aide d’Office 365 Mobile Device Management (MDM). Les appareils mobiles utilisés pour accéder au courrier électronique, au calendrier, aux contacts et aux documents jouent un rôle important dans la façon de s’assurer que les employés peuvent travailler à tout moment et depuis n’importe quel endroit. Il est essentiel de protéger les informations de votre organisation. Vous utilisez Office 365 MDM pour définir les stratégies de sécurité des appareils et les règles d’accès. En cas de perte ou de vol, vous utilisez également Office 365 MDM pour réinitialiser les appareils mobiles.

Les rapports de conformité MDM fournissent une vue d’ensemble des stratégies configurées par une organisation pour sécuriser les appareils mobiles qui accèdent aux données Office 365. Le rapport autorise le filtrage des appareils par État de conformité, les violations signalées, les appareils bloqués et le nombre d’appareils effacés à la suite de stratégies de sécurité. Pour plus d'informations, voir [Overview of Mobile Device Management for Office 365](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a).

## <a name="data-loss-prevention"></a>Protection contre la perte de données

Les stratégies DLP aident à gérer la sécurité et le flux d’informations au sein d’une organisation. Vous pouvez configurer des stratégies pour bloquer l’accès au contenu, chiffrer les données ou informer les utilisateurs des violations de stratégie et de stratégie à l’aide des conseils de stratégie dans l’application DLP. Les rapports DLP fournissent un aperçu du nombre de correspondances de stratégie et de règle, de remplacements et de faux positifs.

Vous utilisez le centre d’administration Microsoft 365 pour afficher des informations sur le nombre de messages détectés par vos stratégies DLP. Les rapports DLP fournissent des informations sur les correspondances de stratégie et de règle pour les messages envoyés et reçus. Vous pouvez également afficher le nombre de correspondances, de remplacements et de faux positifs pour chaque stratégie au cours des 24 dernières heures à l’aide du centre d’administration Exchange. Si vous téléchargez un rapport Excel, vous pouvez afficher encore plus de détails, tels que la personne qui a envoyé le message, la date du jour et les correspondances de stratégie qui ont été déclenchées. Pour plus d’informations, consultez la rubrique [afficher les rapports sur les détections de stratégies DLP](https://technet.microsoft.com/library/jj889415(v=exchg.150).aspx).

## <a name="auditing-in-yammer-enterprise"></a>Audit dans Yammer Enterprise

Yammer Enterprise offre aux administrateurs la possibilité d’exporter les données d’activité de l’utilisateur à partir de leur réseau Yammer via l' [API d’exportation des données Yammer](https://support.office.com/article/export-data-from-yammer-enterprise-b303d8f3-007d-4ad4-81f8-54fb1ecfb3f2)ou manuellement via la page d’administration du réseau Yammer. La possibilité d’exporter des journaux est limitée aux administrateurs réseau dans Yammer. (Tous les administrateurs Office 365 globaux sont des administrateurs réseau Yammer).

Les données suivantes sont exportables :

| Filename | Description |
|----------------------------|-------------------------------------------------------------------------|
| Utilisateurs.csv | Tous les utilisateurs nouveaux, en attente et suspendus dans le réseau |
| Messages.csv | Tous les messages dans le réseau |
| Files. csv (métadonnées) | Les métadonnées telles que le nom de fichier, l’URL de l’API de fichier, l’ID de téléchargeur, le chargement à, etc. |
| Files. csv (fichiers d’origine) | Fichier zip des fichiers d’origine téléchargés par les utilisateurs dans Yammer |
| Topics.csv | Rubriques créées sur le réseau |
| Pages.csv | Pages (notes) créées par les utilisateurs dans le réseau |
| Admins.csv | Tous les administrateurs vérifiés sur le réseau |
| Networks.csv | Tous les réseaux externes Yammer |

Les données d’entreprise Yammer sont également disponibles par le biais des rapports d’activité Office 365. De plus, Yammer travaille activement sur l’exposition de la journalisation supplémentaire via l’API activité de gestion d’Office 365 et sur la capacité à se déconnecter des données à l’aide de Power BI. Pour plus d’informations sur ces fonctionnalités, reportez-vous à la feuille de [route Office](https://fasttrack.microsoft.com/roadmap?filters=yammer) .
