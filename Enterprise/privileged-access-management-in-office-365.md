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
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="30438-103">Privilèges d’accès gestion dans Office 365</span><span class="sxs-lookup"><span data-stu-id="30438-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30438-104">Cette rubrique traite des instructions de déploiement et de configuration pour les fonctionnalités de la version bêta publique uniquement actuellement disponibles dans Office 365 E5 et références de conformité avancées.</span><span class="sxs-lookup"><span data-stu-id="30438-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="30438-p101">Un accès privilégié gestion permet de contrôle d’accès granulaire sur les tâches d’administration privilégié dans Office 365.  Il permet de protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administration privilégié existants avec accès permanent à des données sensibles ou l’accès aux paramètres de configuration critique. Après avoir activé la gestion de l’accès privilégié, les utilisateurs devront demander l’accès juste-à-temps pour effectuer des tâches avec des privilèges élevés et privilégiés via un flux de travail d’approbation qui est hautement et de temps. Ainsi, les utilisateurs juste suffisamment-accès pour effectuer la tâche en cours, sans risque d’exposition des données sensibles ou des paramètres de configuration critique. Activation de la gestion des accès privilégié dans Office 365 permettra à votre organisation de fonctionner avec des privilèges zéro permanent et fournir une couche de protection contre les vulnérabilités résultant en raison de cet accès administratif permanent.</span><span class="sxs-lookup"><span data-stu-id="30438-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="30438-110">Cette rubrique sera vous guidera activation et configuration de gestion de l’accès privilégié dans votre organisation Office 365 et servir d’un guide de référence pour la demande, l’approbation et la gestion de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="30438-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="30438-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="30438-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="30438-112">Fonctionnalité limitée</span><span class="sxs-lookup"><span data-stu-id="30438-112">Limited functionality</span></span>
<span data-ttu-id="30438-p102">Au cours de la version bêta publique, un accès privilégié des fonctionnalités de gestion sont uniquement disponibles via [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) dans Office 365. Traite les définitions de tâches au niveau de cmdlets de gestion Exchange de la gestion de privilèges d’accès. Dans Office 365 les versions ultérieures, accès privilégié seront disponible via le portail d’administration de fonctionnalités et couvrent d’autres services de charges de travail d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="30438-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="30438-116">Connexion à Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="30438-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="30438-117">Les étapes de configuration dans cette rubrique vous aidera à l’activation et à l’aide d’un accès privilégié dans Office 365 à l’aide d’Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30438-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="30438-118">Suivez les étapes [se connecter à Exchange Online PowerShell à l’aide de l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) pour se connecter à Exchange Online PowerShell avec vos informations d’identification Office 365 pour activer et configurer l’accès privilégié pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="30438-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="30438-p103">Il est inutile d’activer l’authentification multifacteur pour votre organisation Office 365 les étapes permettant d’activer l’accès privilégié lors de la connexion à Exchange Online PowerShell. Établir une connexion avec l’authentification multifacteur crée un jeton OAuth qui est utilisé par un accès privilégié pour signer vos demandes.</span><span class="sxs-lookup"><span data-stu-id="30438-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="30438-121">Activer et configurer la gestion des accès privilégié</span><span class="sxs-lookup"><span data-stu-id="30438-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="30438-122">Étape 1 : créer le groupe d’approbateur</span><span class="sxs-lookup"><span data-stu-id="30438-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="30438-p104">À partir du portail d’administration d’Office 365, sélectionnez **groupes** > **Ajouter un groupe**, puis créer un groupe de sécurité de messagerie pour les approbateurs d’accès par défaut privilégié. Lorsque vous avez terminé, sélectionnez **Ajouter** pour créer et enregistrer le groupe approbateur.</span><span class="sxs-lookup"><span data-stu-id="30438-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Privilèges d’accès écran approbateurs dans le portail d’administration d’Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="30438-p105">À ce stade, seuls les utilisateurs disposant d’un accès administratif sont autorisés à approuver les demandes à partir d’Office 365 privilégiée access. Dans les futures tout utilisateur qui fait partie du groupe des approbateurs sera en mesure d’approuver les demandes d’accès.</span><span class="sxs-lookup"><span data-stu-id="30438-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="30438-128">Étape 2 : activer l’accès privilégié dans Office 365</span><span class="sxs-lookup"><span data-stu-id="30438-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="30438-129">Accès privilégié doit être activé explicitement avec le groupe d’approbateur par défaut et y compris un ensemble de comptes système que vous souhaitez exclure le contrôle d’accès de gestion des accès privilégié.</span><span class="sxs-lookup"><span data-stu-id="30438-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="30438-130">Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’accès privilégié et à affecter à groupe de l’approbateur :</span><span class="sxs-lookup"><span data-stu-id="30438-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="30438-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="30438-132">Comptes système fonctionnalité sera disponible pour s’assurer de certains automatisations au sein de votre organisation peuvent travailler sans dépendance sur un accès privilégié, mais il est recommandé que ces exclusions exceptionnelles et ceux autorisés doivent être approuvés et audit régulièrement.</span><span class="sxs-lookup"><span data-stu-id="30438-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="30438-133">Étape 3 : créer une stratégie d’approbation</span><span class="sxs-lookup"><span data-stu-id="30438-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="30438-p106">Une stratégie d’approbation vous permet de définir les exigences spécifiques limitées à des tâches spécifiques. Les options de type approbation sont **automatique** ou **manuel**.</span><span class="sxs-lookup"><span data-stu-id="30438-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="30438-136">Exécutez la commande suivante dans Exchange Online PowerShell pour définir une stratégie d’approbation :</span><span class="sxs-lookup"><span data-stu-id="30438-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="30438-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="30438-138">À l’aide d’un accès privilégié dans votre organisation Office 365</span><span class="sxs-lookup"><span data-stu-id="30438-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="30438-139">Demande d’autorisation élévation pour exécuter des tâches</span><span class="sxs-lookup"><span data-stu-id="30438-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="30438-p107">Une fois activée, privilégié access nécessite approbations pour l’exécution de toute tâche qui dispose d’une stratégie d’approbation associé définie. Les utilisateurs qui ont besoin exécuter des tâches incluses dans l’une stratégie d’approbation doit demander et avoir approbation d’accès afin de disposer des autorisations nécessaires pour exécuter la tâche.</span><span class="sxs-lookup"><span data-stu-id="30438-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="30438-142">Exécutez la commande suivante dans Exchange Online PowerShell pour créer et soumettre une demande d’approbation au groupe de l’approbateur :</span><span class="sxs-lookup"><span data-stu-id="30438-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="30438-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="30438-144">Afficher l’état des demandes d’élévation</span><span class="sxs-lookup"><span data-stu-id="30438-144">View status of elevation requests</span></span>
<span data-ttu-id="30438-145">Après la création d’une demande d’approbation, état de la demande l’élévation peut être analysé à l’aide d’associé avec l’ID de demande.</span><span class="sxs-lookup"><span data-stu-id="30438-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="30438-146">Exécutez la commande suivante dans Exchange Online PowerShell pour afficher un état de la demande d’approbation pour un ID de demande spécifique :</span><span class="sxs-lookup"><span data-stu-id="30438-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="30438-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="30438-148">L’approbation d’une demande d’autorisation de l’élévation</span><span class="sxs-lookup"><span data-stu-id="30438-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="30438-149">Lors de la création d’une demande d’approbation, les membres du groupe pertinents approbateur reçoivent une notification par courrier électronique et peuvent approuver la requête associée à l’ID de demande.</span><span class="sxs-lookup"><span data-stu-id="30438-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="30438-150">Exécutez la commande suivante dans Exchange Online PowerShell pour approuver une demande d’autorisation élévation :</span><span class="sxs-lookup"><span data-stu-id="30438-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="30438-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="30438-152">Le refus d’une demande d’autorisation de l’élévation</span><span class="sxs-lookup"><span data-stu-id="30438-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="30438-153">Lors de la création d’une demande d’approbation, les membres du groupe pertinents approbateur peuvent refuser la demande associée à l’ID de demande.</span><span class="sxs-lookup"><span data-stu-id="30438-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="30438-154">Exécutez la commande suivante dans Exchange Online PowerShell pour refuser une demande d’autorisation élévation :</span><span class="sxs-lookup"><span data-stu-id="30438-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="30438-155">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="30438-156">Exécution de la tâche</span><span class="sxs-lookup"><span data-stu-id="30438-156">Running the task</span></span>
<span data-ttu-id="30438-p108">Une fois l’approbation est accordée, l’utilisateur peut exécuter la tâche souhaitée et accès privilégié seront autoriser et exécuter la tâche de la part des utilisateurs. L’approbation restera valide pour le demandé durée (durée par défaut est de 4 heures) pendant laquelle le demandeur peut exécuter la tâche prévue à plusieurs reprises. Toutes ces exécutions sont connectées et mises à disposition pour la sécurité et d’audit de conformité.</span><span class="sxs-lookup"><span data-stu-id="30438-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="30438-160">Désactiver l’accès privilégié dans Office 365</span><span class="sxs-lookup"><span data-stu-id="30438-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="30438-p109">Si nécessaire, vous pouvez désactiver la gestion des accès privilégié dans Office 365. Désactivation des privilèges access ne supprime pas des stratégies d’approbation associées ou des groupes de l’approbateur.</span><span class="sxs-lookup"><span data-stu-id="30438-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="30438-163">Exécutez la commande suivante dans Exchange Online Powershell pour désactiver l’accès privilégié :</span><span class="sxs-lookup"><span data-stu-id="30438-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="30438-164">Géré l’accès à Microsoft Graph dans Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="30438-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30438-165">Cette section couvre plus d’informations sur une fonctionnalité actuellement disponible uniquement dans l’aperçu.</span><span class="sxs-lookup"><span data-stu-id="30438-165">This section covers details about a feature currently available only in preview.</span></span>

<span data-ttu-id="30438-p110">Accès géré à Microsoft Graph dans Microsoft Azure est un service qui permet aux entreprises d’exercer un niveau granulaire de contrôle sur leurs données Office 365. Ce système permet aux développeurs d’applications créer des informations sur les données.</span><span class="sxs-lookup"><span data-stu-id="30438-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="30438-p111">Le système utilise Office 365 privilégié access pour déclarer un contrôle sur leurs données par le biais de son flux de travail approbation sur lesquelles porte l’accès aux données d’Office 365 avec supervision d’administration. Demandes de données sont lorsque les applications sont installées et nécessitent un accès aux données d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="30438-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="30438-170">Afficher les détails de demande</span><span class="sxs-lookup"><span data-stu-id="30438-170">View request details</span></span>
<span data-ttu-id="30438-171">Afficher les détails des demandes d’accès pour les données d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="30438-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="30438-172">Exécutez la commande suivante dans Exchange Online Powershell pour afficher les demandes de données :</span><span class="sxs-lookup"><span data-stu-id="30438-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="30438-173">Exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="30438-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="30438-174">Approuver les demandes d’accès aux données</span><span class="sxs-lookup"><span data-stu-id="30438-174">Approve data access requests</span></span>
<span data-ttu-id="30438-175">Toutes les demandes d’accès aux données peuvent être approuvées via les applets de commande d’approbation standard accès privilégié.</span><span class="sxs-lookup"><span data-stu-id="30438-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="30438-176">Exécutez la commande suivante dans Exchange Online Powershell pour approuver toutes les demandes de données demandeur spécifique :</span><span class="sxs-lookup"><span data-stu-id="30438-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="30438-177">Exemple :</span><span class="sxs-lookup"><span data-stu-id="30438-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="30438-178">Obtention d’aide et commentaires</span><span class="sxs-lookup"><span data-stu-id="30438-178">Getting help and providing feedback</span></span>
<span data-ttu-id="30438-p112">Nous reconnaissons qu’au cours de la version bêta publique, vous pouvez rencontrer un bogue occasionnellement ou ont des commentaires et des suggestions sur comment nous pouvons améliorer la gestion de l’accès privilégié. Nous envoyer vos commentaires et vous invitons à partager avec nous :</span><span class="sxs-lookup"><span data-stu-id="30438-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="30438-181">Publier vos commentaires suggestions ad dans le [Groupe de Yammer Preview Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="30438-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="30438-182">Vos rapports de bogues sous le chemin de la zone « Office 365 gestion privilégié d’accès » sur l' [Office Preview VSO](https://office-previews.visualstudio.com/previews)du fichier.</span><span class="sxs-lookup"><span data-stu-id="30438-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="30438-183">Questions fréquemment posées</span><span class="sxs-lookup"><span data-stu-id="30438-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="30438-184">Quelles versions clientes ai-je besoin pour utiliser un accès privilégié dans Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="30438-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="30438-185">Un accès privilégié gestion dans Office 365 n’est actuellement disponible pour les clients avec E5 et références de conformité avancées.</span><span class="sxs-lookup"><span data-stu-id="30438-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="30438-186">Lorsqu’un accès privilégié sera disponible pour des charges de travail Office 365 au-delà Exchange ?</span><span class="sxs-lookup"><span data-stu-id="30438-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="30438-p113">Nous prévoyons de proposer cette fonctionnalité dans les autres charges de travail Office 365 bientôt. Lorsque nous sommes prêts à partager une chronologie, il sera disponible par le biais de la feuille de route d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="30438-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="30438-189">Comment est-ce différent de gestion des identités privilégié Azure d’Active Directory ?</span><span class="sxs-lookup"><span data-stu-id="30438-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="30438-p114">Privilèges d’accès gestion dans Office 365 et [la gestion des identités Azure AD privilégié](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complément autres en fournissant un accès contrôle avec un accès à différentes étendues juste-à-temps. Elles permettent un ensemble robust de contrôles de protection de données.</span><span class="sxs-lookup"><span data-stu-id="30438-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="30438-p115">Un accès privilégié gestion dans Office 365 peut être définie et étendue au niveau de la tâche, tandis que la gestion des identités Azure AD privilégié s’applique au niveau du rôle avec la possibilité d’exécuter plusieurs tâches.  Gestion des identités privilégié Azure AD permet principalement la gestion des accès pour les rôles de AD et des groupes de rôles privilèges lors de la gestion des accès dans Office 365 est appliquée au niveau de la tâche.</span><span class="sxs-lookup"><span data-stu-id="30438-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="30438-194">**Gestion dans Office 365 de privilèges d’activation d’accès lorsque vous utilisez déjà la gestion des identités Azure AD privilégié :** Ajout de gestion de l’accès privilégié dans Office 365 peut fournir un niveau granulaire de protection et d’audit des fonctionnalités pour l’accès aux données d’Office 365 privilégié.</span><span class="sxs-lookup"><span data-stu-id="30438-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="30438-195">**Activation Azure AD privilégié déjà à l’aide de la gestion des identités privilégié gestion des accès dans Office 365 :**  Ajout de la gestion des identités Azure AD privilégié avec privilèges gestion des accès dans Office 365 peut étendre les privilèges d’accès aux données en dehors d’Office 365 principalement défini par rôle ou l’identité d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30438-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="30438-196">Je dois être un administrateur Global pour gérer l’accès privilégié dans Office 365</span><span class="sxs-lookup"><span data-stu-id="30438-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="30438-p116">Au cours de l’aperçu, vous devez disposer de privilèges d’administrateur Global pour être en mesure de gérer l’accès privilégié dans Office 365. Les utilisateurs qui sont inclus dans le groupe d’un approbateurs ne doivent être un administrateur Global pour examiner et approuver les demandes.</span><span class="sxs-lookup"><span data-stu-id="30438-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="30438-199">Quelle est la gestion des accès privilégié dans Office 365 liés à la zone de sécurité client ?</span><span class="sxs-lookup"><span data-stu-id="30438-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="30438-p117">[Zone de sécurité client](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) permet à un niveau de contrôle d’accès pour les organisations pour l’accès aux données par leur fournisseur de services, par exemple, Microsoft. Un accès privilégié gestion dans Office 365 permet de contrôle d’accès granulaire au sein d’une organisation pour toutes les tâches Office 365 privilégié.</span><span class="sxs-lookup"><span data-stu-id="30438-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>