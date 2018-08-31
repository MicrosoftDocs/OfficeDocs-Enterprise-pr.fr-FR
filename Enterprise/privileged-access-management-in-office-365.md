---
title: Privilèges d’accès gestion dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Utilisez cette rubrique pour en savoir plus sur la fonctionnalité de gestion des accès privilégié dans Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915389"
---
# <a name="privileged-access-management-in-office-365"></a>Privilèges d’accès gestion dans Office 365

> [!IMPORTANT]
> Cette rubrique traite des instructions de déploiement et de configuration pour les fonctionnalités de la version bêta publique uniquement actuellement disponibles dans Office 365 E5 et références de conformité avancées.

Un accès privilégié gestion permet de contrôle d’accès granulaire sur les tâches d’administration privilégié dans Office 365.  Il permet de protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administration privilégié existants avec accès permanent à des données sensibles ou l’accès aux paramètres de configuration critique. Après avoir activé la gestion de l’accès privilégié, les utilisateurs devront demander l’accès juste-à-temps pour effectuer des tâches avec des privilèges élevés et privilégiés via un flux de travail d’approbation qui est hautement et de temps. Ainsi, les utilisateurs juste suffisamment-accès pour effectuer la tâche en cours, sans risque d’exposition des données sensibles ou des paramètres de configuration critique. Activation de la gestion des accès privilégié dans Office 365 permettra à votre organisation de fonctionner avec des privilèges zéro permanent et fournir une couche de protection contre les vulnérabilités résultant en raison de cet accès administratif permanent. 

Cette rubrique sera vous guidera activation et configuration de gestion de l’accès privilégié dans votre organisation Office 365 et servir d’un guide de référence pour la demande, l’approbation et la gestion de la fonctionnalité. 

## <a name="before-you-begin"></a>Avant de commencer

### <a name="limited-functionality"></a>Fonctionnalité limitée
Au cours de la version bêta publique, un accès privilégié des fonctionnalités de gestion sont uniquement disponibles via [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) dans Office 365. Traite les définitions de tâches au niveau de cmdlets de gestion Exchange de la gestion de privilèges d’accès. Dans Office 365 les versions ultérieures, accès privilégié seront disponible via le portail d’administration de fonctionnalités et couvrent d’autres services de charges de travail d’Office 365.

### <a name="connecting-to-exchange-online-powershell"></a>Connexion à Exchange Online PowerShell
Les étapes de configuration dans cette rubrique vous aidera à l’activation et à l’aide d’un accès privilégié dans Office 365 à l’aide d’Exchange Online PowerShell. 

Suivez les étapes [se connecter à Exchange Online PowerShell à l’aide de l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) pour se connecter à Exchange Online PowerShell avec vos informations d’identification Office 365 pour activer et configurer l’accès privilégié pour votre organisation.

> [!NOTE]
> Il est inutile d’activer l’authentification multifacteur pour votre organisation Office 365 les étapes permettant d’activer l’accès privilégié lors de la connexion à Exchange Online PowerShell. Établir une connexion avec l’authentification multifacteur crée un jeton OAuth qui est utilisé par un accès privilégié pour signer vos demandes.

## <a name="enable-and-configure-privileged-access-management"></a>Activer et configurer la gestion des accès privilégié

### <a name="step-1---create-an-approvers-group"></a>Étape 1 : créer le groupe d’approbateur
À partir du portail d’administration d’Office 365, sélectionnez **groupes** > **Ajouter un groupe**, puis créer un groupe de sécurité de messagerie pour les approbateurs d’accès par défaut privilégié. Lorsque vous avez terminé, sélectionnez **Ajouter** pour créer et enregistrer le groupe approbateur.

![Privilèges d’accès écran approbateurs dans le portail d’administration d’Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> À ce stade, seuls les utilisateurs disposant d’un accès administratif sont autorisés à approuver les demandes à partir d’Office 365 privilégiée access. Dans les futures tout utilisateur qui fait partie du groupe des approbateurs sera en mesure d’approuver les demandes d’accès.

### <a name="step-2---enable-privileged-access-in-office-365"></a>Étape 2 : activer l’accès privilégié dans Office 365
Accès privilégié doit être activé explicitement avec le groupe d’approbateur par défaut et y compris un ensemble de comptes système que vous souhaitez exclure le contrôle d’accès de gestion des accès privilégié. 

Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’accès privilégié et à affecter à groupe de l’approbateur :
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
Exemple :
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Comptes système fonctionnalité sera disponible pour s’assurer de certains automatisations au sein de votre organisation peuvent travailler sans dépendance sur un accès privilégié, mais il est recommandé que ces exclusions exceptionnelles et ceux autorisés doivent être approuvés et audit régulièrement.

### <a name="step-3---create-an-approval-policy"></a>Étape 3 : créer une stratégie d’approbation
Une stratégie d’approbation vous permet de définir les exigences spécifiques limitées à des tâches spécifiques. Les options de type approbation sont **automatique** ou **manuel**. 

Exécutez la commande suivante dans Exchange Online PowerShell pour définir une stratégie d’approbation :
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
Exemple :
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>À l’aide d’un accès privilégié dans votre organisation Office 365

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>Demande d’autorisation élévation pour exécuter des tâches
Une fois activée, privilégié access nécessite approbations pour l’exécution de toute tâche qui dispose d’une stratégie d’approbation associé définie. Les utilisateurs qui ont besoin exécuter des tâches incluses dans l’une stratégie d’approbation doit demander et avoir approbation d’accès afin de disposer des autorisations nécessaires pour exécuter la tâche.

Exécutez la commande suivante dans Exchange Online PowerShell pour créer et soumettre une demande d’approbation au groupe de l’approbateur :
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
Exemple :
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>Afficher l’état des demandes d’élévation
Après la création d’une demande d’approbation, état de la demande l’élévation peut être analysé à l’aide d’associé avec l’ID de demande.

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher un état de la demande d’approbation pour un ID de demande spécifique :
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
Exemple :
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>L’approbation d’une demande d’autorisation de l’élévation
Lors de la création d’une demande d’approbation, les membres du groupe pertinents approbateur reçoivent une notification par courrier électronique et peuvent approuver la requête associée à l’ID de demande. 

Exécutez la commande suivante dans Exchange Online PowerShell pour approuver une demande d’autorisation élévation :
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Exemple :
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>Le refus d’une demande d’autorisation de l’élévation
Lors de la création d’une demande d’approbation, les membres du groupe pertinents approbateur peuvent refuser la demande associée à l’ID de demande. 

Exécutez la commande suivante dans Exchange Online PowerShell pour refuser une demande d’autorisation élévation :
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
Exemple :
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>Exécution de la tâche
Une fois l’approbation est accordée, l’utilisateur peut exécuter la tâche souhaitée et accès privilégié seront autoriser et exécuter la tâche de la part des utilisateurs. L’approbation restera valide pour le demandé durée (durée par défaut est de 4 heures) pendant laquelle le demandeur peut exécuter la tâche prévue à plusieurs reprises. Toutes ces exécutions sont connectées et mises à disposition pour la sécurité et d’audit de conformité. 

### <a name="disable-privileged-access-in-office-365"></a>Désactiver l’accès privilégié dans Office 365
Si nécessaire, vous pouvez désactiver la gestion des accès privilégié dans Office 365. Désactivation des privilèges access ne supprime pas des stratégies d’approbation associées ou des groupes de l’approbateur.

Exécutez la commande suivante dans Exchange Online Powershell pour désactiver l’accès privilégié :

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>Géré l’accès à Microsoft Graph dans Microsoft Azure

> [!IMPORTANT]
> Cette section couvre plus d’informations sur une fonctionnalité actuellement disponible uniquement dans l’aperçu.

Accès géré à Microsoft Graph dans Microsoft Azure est un service qui permet aux entreprises d’exercer un niveau granulaire de contrôle sur leurs données Office 365. Ce système permet aux développeurs d’applications créer des informations sur les données. 

Le système utilise Office 365 privilégié access pour déclarer un contrôle sur leurs données par le biais de son flux de travail approbation sur lesquelles porte l’accès aux données d’Office 365 avec supervision d’administration. Demandes de données sont lorsque les applications sont installées et nécessitent un accès aux données d’Office 365.

### <a name="view-request-details"></a>Afficher les détails de demande
Afficher les détails des demandes d’accès pour les données d’Office 365.

Exécutez la commande suivante dans Exchange Online Powershell pour afficher les demandes de données :
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
Exemple de sortie :
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>Approuver les demandes d’accès aux données
Toutes les demandes d’accès aux données peuvent être approuvées via les applets de commande d’approbation standard accès privilégié.

Exécutez la commande suivante dans Exchange Online Powershell pour approuver toutes les demandes de données demandeur spécifique :

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Exemple :
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>Obtention d’aide et commentaires
Nous reconnaissons qu’au cours de la version bêta publique, vous pouvez rencontrer un bogue occasionnellement ou ont des commentaires et des suggestions sur comment nous pouvons améliorer la gestion de l’accès privilégié. Nous envoyer vos commentaires et vous invitons à partager avec nous :
- Publier vos commentaires suggestions ad dans le [Groupe de Yammer Preview Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).
- Vos rapports de bogues sous le chemin de la zone « Office 365 gestion privilégié d’accès » sur l' [Office Preview VSO](https://office-previews.visualstudio.com/previews)du fichier.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>Quelles versions clientes ai-je besoin pour utiliser un accès privilégié dans Office 365 ?
Un accès privilégié gestion dans Office 365 n’est actuellement disponible pour les clients avec E5 et références de conformité avancées.

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>Lorsqu’un accès privilégié sera disponible pour des charges de travail Office 365 au-delà Exchange ?
Nous prévoyons de proposer cette fonctionnalité dans les autres charges de travail Office 365 bientôt. Lorsque nous sommes prêts à partager une chronologie, il sera disponible par le biais de la feuille de route d’Office 365.

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>Comment est-ce différent de gestion des identités privilégié Azure d’Active Directory ?
Privilèges d’accès gestion dans Office 365 et [la gestion des identités Azure AD privilégié](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complément autres en fournissant un accès contrôle avec un accès à différentes étendues juste-à-temps. Elles permettent un ensemble robust de contrôles de protection de données.

Un accès privilégié gestion dans Office 365 peut être définie et étendue au niveau de la tâche, tandis que la gestion des identités Azure AD privilégié s’applique au niveau du rôle avec la possibilité d’exécuter plusieurs tâches.  Gestion des identités privilégié Azure AD permet principalement la gestion des accès pour les rôles de AD et des groupes de rôles privilèges lors de la gestion des accès dans Office 365 est appliquée au niveau de la tâche.

 - **Gestion dans Office 365 de privilèges d’activation d’accès lorsque vous utilisez déjà la gestion des identités Azure AD privilégié :** Ajout de gestion de l’accès privilégié dans Office 365 peut fournir un niveau granulaire de protection et d’audit des fonctionnalités pour l’accès aux données d’Office 365 privilégié.

- **Activation Azure AD privilégié déjà à l’aide de la gestion des identités privilégié gestion des accès dans Office 365 :**  Ajout de la gestion des identités Azure AD privilégié avec privilèges gestion des accès dans Office 365 peut étendre les privilèges d’accès aux données en dehors d’Office 365 principalement défini par rôle ou l’identité d’un utilisateur. 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Je dois être un administrateur Global pour gérer l’accès privilégié dans Office 365
Au cours de l’aperçu, vous devez disposer de privilèges d’administrateur Global pour être en mesure de gérer l’accès privilégié dans Office 365. Les utilisateurs qui sont inclus dans le groupe d’un approbateurs ne doivent être un administrateur Global pour examiner et approuver les demandes. 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>Quelle est la gestion des accès privilégié dans Office 365 liés à la zone de sécurité client ?
[Zone de sécurité client](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) permet à un niveau de contrôle d’accès pour les organisations pour l’accès aux données par leur fournisseur de services, par exemple, Microsoft. Un accès privilégié gestion dans Office 365 permet de contrôle d’accès granulaire au sein d’une organisation pour toutes les tâches Office 365 privilégié.