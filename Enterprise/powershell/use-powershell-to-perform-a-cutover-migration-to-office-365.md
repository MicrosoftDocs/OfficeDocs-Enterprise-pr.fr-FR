---
title: "Utiliser PowerShell pour effectuer une migration à basculement vers Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "Résumé : Découvrez comment utiliser Windows PowerShell pour effectuer une migration à basculement vers Office 365."
ms.openlocfilehash: 8181d59f53464034a584724dcb53956976c917dd
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="f610d-103">Utiliser PowerShell pour effectuer une migration à basculement vers Office 365</span><span class="sxs-lookup"><span data-stu-id="f610d-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="f610d-104">**Résumé :** Découvrez comment utiliser Windows PowerShell pour effectuer une migration à basculement vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="f610d-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="f610d-p101">Vous pouvez migrer le contenu des boîtes aux lettres des utilisateurs vers Office 365 à partir d'un système de messagerie source en une seule fois à l'aide d'une migration à basculement. Cet article décrit les tâches correspondant à une migration de messagerie à basculement à l'aide d'Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f610d-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="f610d-p102">La rubrique [Ce que vous devez savoir sur une migration de messagerie à basculement vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688) vous permet d'obtenir une vue d'ensemble du processus de migration. Lorsque le contenu de cet article vous est familier, utilisez celui-ci pour commencer la migration de boîtes aux lettres d'un système à l'autre.</span><span class="sxs-lookup"><span data-stu-id="f610d-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f610d-p103">Vous pouvez également utiliser le Centre d'administration Exchange pour effectuer la migration à basculement. Voir [Effectuer une migration à basculement de la messagerie vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="f610d-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f610d-111">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="f610d-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="f610d-p104">Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d'informations sur les autres facteurs affectant la durée de migration des boîtes aux lettres vers Office 365, consultez la rubrique [Performances de migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="f610d-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="f610d-p105">Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="f610d-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="f610d-p106">Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="f610d-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="f610d-119">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="f610d-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="f610d-120">Étapes de migration</span><span class="sxs-lookup"><span data-stu-id="f610d-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="f610d-121">Étape 1 : Préparez une migration à basculement</span><span class="sxs-lookup"><span data-stu-id="f610d-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="f610d-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-122"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="f610d-p107">**Ajoutez votre organisation Exchange locale en tant que domaine accepté de votre organisation Office 365.** Le service de migration utilise l'adresse SMTP de vos boîtes aux lettres locales pour créer les identifiants d'utilisateurs Microsoft Online Services et les adresses de messagerie pour les nouvelles boîtes aux lettres Office 365. La migration échoue si votre domaine Exchange n'est pas un domaine accepté ou le domaine principal de votre organisation Office 365. Pour plus d'informations, consultez la rubrique[Vérifier votre domaine dans Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="f610d-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="f610d-p108">**Configurez Outlook Anywhere sur votre serveur Exchange local** Le service de migration de messagerie utilise RPC sur HTTP ou Outlook Anywhere pour se connecter à votre serveur Exchange local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange 2010, 2007 et 2003, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="f610d-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="f610d-130">Exchange 2010 : Activer Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="f610d-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="f610d-131">Exchange 2007 : Procédure d'activation d'Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="f610d-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="f610d-132">Exchange 2003 : Scénarios de déploiement RPC sur HTTP</span><span class="sxs-lookup"><span data-stu-id="f610d-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="f610d-133">Procédure de configuration d'Outlook Anywhere avec Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="f610d-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="f610d-p109">La configuration d'Outlook Anywhere doit être réalisée à l'aide d'un certificat émis par une autorité de certification (CA) approuvée. Il ne peut être configuré à l'aide d'un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="f610d-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="f610d-p110">**Vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f610d-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="f610d-139">Utilisez Microsoft Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="f610d-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="f610d-p111">Utilisez l'[analyseur de connectivité à distance Exchange](https://www.testexchangeconnectivity.com/) de Microsoft pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.</span><span class="sxs-lookup"><span data-stu-id="f610d-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="f610d-142">Dans Exchange Online PowerShell, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f610d-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="f610d-p112">**Attribuez à un compte d'utilisateur local les autorisations nécessaires pour accéder aux boîtes aux lettres de votre organisation Exchange.** Le compte d'utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange locale (également appeléadministrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous voulez migrer vers Office 365. Ce compte d'utilisateur permet de créer un point de terminaison de migration pour votre organisation locale.</span><span class="sxs-lookup"><span data-stu-id="f610d-p112">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.** The on-premises user account that you use to connect to your on-premises Exchange organization (also called themigration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="f610d-p113">La liste suivante montre les privilèges administratifs requis pour migrer des boîtes aux lettres à l'aide d'une migration à basculement. Trois options sont possibles.</span><span class="sxs-lookup"><span data-stu-id="f610d-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="f610d-148">L'administrateur de migration doit être membre du groupe **Administrateurs de domaine** dans Active Directory au sein de l'organisation locale.</span><span class="sxs-lookup"><span data-stu-id="f610d-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="f610d-149">Ou</span><span class="sxs-lookup"><span data-stu-id="f610d-149">Or</span></span>
    
  - <span data-ttu-id="f610d-150">L'administrateur de migration doit disposer de l'autorisation **FullAccess** pour chaque boîte aux lettres locale.</span><span class="sxs-lookup"><span data-stu-id="f610d-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="f610d-151">Ou</span><span class="sxs-lookup"><span data-stu-id="f610d-151">Or</span></span>
    
  - <span data-ttu-id="f610d-152">L'administrateur de migration doit disposer de l'autorisation **Receive As** pour la base de données de boîtes aux lettres locale stockant les boîtes aux lettres d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f610d-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="f610d-p114">**Désactivez la messagerie unifiée.** Si les boîtes aux lettres locales que vous migrez sont activées pour la messagerie unifiée, vous devez désactiver cette dernière avant de procéder à la migration. Une fois la migration terminée, vous pouvez activer la messagerie unifiée sur les boîtes aux lettres.</span><span class="sxs-lookup"><span data-stu-id="f610d-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="f610d-p115">**Groupes de sécurité et délégués** Le service de migration de messagerie électronique ne peut pas détecter si les groupes Active Directory sur site sont des groupes de sécurité ou non, il ne peut donc configurer aucun groupe migré en tant que groupe de sécurité dans Office 365. Si vous souhaitez disposer de groupes de sécurité dans votre client Office 365, vous devez d'abord configurer un groupe de sécurité à extension messagerie vide dans votre client Office 365 avant de commencer la migration à basculement. En outre, cette méthode de migration déplace uniquement les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie et les groupes à extension messagerie. Si un autre objet Active Directory, tel qu'un utilisateur n'ayant pas été migré vers Office 365, reçoit une attribution de gestionnaire ou de délégué pour un objet en cours de migration, il doit être supprimé de l'objet avant la migration.</span><span class="sxs-lookup"><span data-stu-id="f610d-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="f610d-160">Étape 2 : Créez un point de terminaison de migration</span><span class="sxs-lookup"><span data-stu-id="f610d-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="f610d-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-161"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="f610d-p116">Pour que la migration fonctionne, Office 365 doit pouvoir se connecter au système de messagerie source et communiquer avec lui. Pour ce faire, Office 365 utilise un point de terminaison. Pour créer un point de terminaison de migration Outlook Anywhere, afin d'effectuer une migration à basculement, commencez par vous [connecter à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="f610d-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="f610d-165">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="f610d-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="f610d-166">Dans Exchange Online PowerShell, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f610d-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="f610d-167">Cet exemple utilise la cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) pour obtenir et tester les paramètres de connexion au serveur Exchange local, puis utilise ces paramètres de connexion pour créer le point de terminaison de migration appelé « CutoverEndpoint ».</span><span class="sxs-lookup"><span data-stu-id="f610d-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="f610d-p117">La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.</span><span class="sxs-lookup"><span data-stu-id="f610d-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="f610d-170">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="f610d-170">Verify it worked</span></span>

<span data-ttu-id="f610d-171">Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « CutoverEndpoint » :</span><span class="sxs-lookup"><span data-stu-id="f610d-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="f610d-172">Étape 3 : Créez le lot de migration à basculement</span><span class="sxs-lookup"><span data-stu-id="f610d-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="f610d-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-173"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="f610d-p118">La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="f610d-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="f610d-p119">Cet exemple de code crée également un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'un seul lot de migration à basculement à la fois.</span><span class="sxs-lookup"><span data-stu-id="f610d-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="f610d-181">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="f610d-181">Verify it worked</span></span>

<span data-ttu-id="f610d-182">Pour vérifier que vous avez créé un lot de migration pour une migration à basculement, exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le nouveau lot de migration :</span><span class="sxs-lookup"><span data-stu-id="f610d-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="f610d-183">Étape 4 : Démarrez le lot de migration à basculement</span><span class="sxs-lookup"><span data-stu-id="f610d-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="f610d-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-184"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="f610d-p120">Pour lancer le lot de migration dans Exchange Online PowerShell, exécutez la commande suivante. Cela crée un lot de migration appelé « CutoverBatch ».</span><span class="sxs-lookup"><span data-stu-id="f610d-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="f610d-187">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="f610d-187">Verify it worked</span></span>

<span data-ttu-id="f610d-p121">Si le traitement d’un lot de migration a démarré, son état dans le tableau de bord de migration est Synchronisation. Pour vérifier que le traitement d’un lot de migration a commencé à l’aide d’Exchange Online PowerShell, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f610d-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="f610d-190">Étape 5 : Routez votre courrier électronique vers Office 365</span><span class="sxs-lookup"><span data-stu-id="f610d-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="f610d-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-191"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="f610d-p122">Les systèmes de messagerie utilisent un enregistrement DNS appelé enregistrement MX pour identifier l'emplacement de remise des messages électroniques. Pendant le processus de migration de la messagerie, votre enregistrement MX pointe vers votre système de messagerie source. Maintenant que la migration de messagerie vers Office 365 est terminée, vous devez faire pointer votre enregistrement MX vers Office 365. Cela permet de s'assurer que le message est remis à vos boîtes aux lettres Office 365. En déplaçant l'enregistrement MX, vous pouvez également désactiver votre ancien système de messagerie lorsque vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="f610d-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="f610d-p123">Pour plusieurs fournisseurs DNS, il existe des instructions spécifiques pour [modifier votre enregistrement MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Si votre fournisseur DNS n'est pas inclus, ou si vous souhaitez avoir une idée des instructions générales, vous avez également accès à des [instructions générales sur les enregistrements MX](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="f610d-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="f610d-p124">Il faut compter jusqu'à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l'enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : [Étape 6 : Supprimez le lot de migration à basculement](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="f610d-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="f610d-201">Étape 6 : Supprimez le lot de migration à basculement</span><span class="sxs-lookup"><span data-stu-id="f610d-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="f610d-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-202"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="f610d-p125">Après avoir modifié l'enregistrement MX et vérifié que tout le courrier est routé vers les boîtes aux lettres Office 365, informez les utilisateurs que leur courrier est envoyé vers Office 365. Après cela, vous pouvez supprimer le lot de migration à basculement. Avant de supprimer le lot de migration, vérifiez les points suivants.</span><span class="sxs-lookup"><span data-stu-id="f610d-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="f610d-p126">Tous les utilisateurs se servent des boîtes aux lettres Office 365. Une fois le lot supprimé, le courrier envoyé à des boîtes aux lettres sur le serveur Exchange local n'est plus copié dans les boîtes aux lettres Office 365 correspondantes.</span><span class="sxs-lookup"><span data-stu-id="f610d-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="f610d-p127">Les boîtes aux lettres Office 365 ont été synchronisées au moins une fois après que le courrier leur a été envoyé directement. Pour ce faire, assurez-vous que la valeur de la zone Heure de la dernière synchronisation pour le lot de migration est postérieure au début du routage direct du courrier vers les boîtes aux lettres Office 365.</span><span class="sxs-lookup"><span data-stu-id="f610d-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="f610d-210">Pour supprimer le lot de migration « CutoverBatch » dans Exchange Online PowerShell, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f610d-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="f610d-211">Section 7 : Attribuez des licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="f610d-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="f610d-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-212"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="f610d-p128">**Pour activer les comptes d'utilisateur Office 365 correspondant aux comptes migrés, vous devez leur attribuer des licences.** Si vous n'attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour savoir comment attribuer une licence dans le Centre d'administration Office 365, voir[Attribuer ou retirer des licences pour Office 365 pour les entreprises](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="f610d-p128">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.** If you don't assign a license, the mailbox is disabled when the grace period ends (30 days). To assign a license in the Office 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="f610d-216">Étape 8 : Exécutez les tâches post-migration</span><span class="sxs-lookup"><span data-stu-id="f610d-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="f610d-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="f610d-217"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="f610d-p129">**Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres**Une fois toutes les boîtes aux lettres locales migrées vers Office 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Office 365 afin de permettre aux utilisateurs de se connecter aisément à leurs nouvelles boîtes aux lettres Office 365 avec des clients mobiles et Outlook. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui de votre organisation Office 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l'enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f610d-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="f610d-222">Si vous conservez votre serveur Exchange, vous devez également vous assurer que l'enregistrement DNS CNAME de découverte automatique pointe vers Office 365 dans les DNS interne et externe après la migration afin que le client Outlook se connecte à la bonne boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="f610d-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="f610d-223">Dans Exchange 2007, Exchange 2010 et Exchange 2013, vous devez également définir  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` sur `Null`.</span><span class="sxs-lookup"><span data-stu-id="f610d-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="f610d-p130">Office 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients mobiles et Outlook. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f610d-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="f610d-226">**Alias :** autodiscover</span><span class="sxs-lookup"><span data-stu-id="f610d-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="f610d-227">**Cible :** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="f610d-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="f610d-228">Pour plus d'informations, voir [Créer des enregistrements DNS pour Office 365 lors de la gestion de vos enregistrements DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="f610d-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="f610d-p131">**Désactivez des serveurs Exchange locaux.** Après avoir vérifié que tout le courrier est acheminé directement vers les boîtes aux lettres Office 365, si vous n'avez plus besoin de conserver votre organisation de messagerie locale ou que vous ne comptez pas implémenter de solution d'authentification unique (SSO), vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="f610d-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="f610d-231">Pour plus d’informations, voir les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f610d-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="f610d-232">Modifier ou supprimer Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="f610d-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="f610d-233">Procédure de suppression d'une organisation Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="f610d-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="f610d-234">Procédure de désinstallation d'Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="f610d-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

