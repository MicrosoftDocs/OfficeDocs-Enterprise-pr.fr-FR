---
title: Utiliser PowerShell pour effectuer une migration intermédiaire vers Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Résumé : Découvrez comment utiliser Windows PowerShell pour effectuer une migration intermédiaire vers Office 365.'
ms.openlocfilehash: d60145c7dd25fc7cf6be51a891b8fae8e67ccc2b
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747530"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="84cfa-103">Utiliser PowerShell pour effectuer une migration intermédiaire vers Office 365</span><span class="sxs-lookup"><span data-stu-id="84cfa-103">Use PowerShell to perform a staged migration to Office 365</span></span>

<span data-ttu-id="84cfa-104">Vous pouvez migrer progressivement le contenu des boîtes aux lettres des utilisateurs vers Office 365 à partir d'un système de messagerie source à l'aide d'une migration intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="84cfa-104">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="84cfa-p101">Cet article décrit les tâches nécessaires pour effectuer une migration de messagerie intermédiaire à l'aide d'Exchange Online PowerShell. La rubrique [Ce que vous devez savoir sur une migration de messagerie intermédiaire vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487) présente le processus de migration. Une fois familiarisé avec son contenu, reportez-vous au présent article pour migrer des boîtes aux lettres d'un système de messagerie vers un autre.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="84cfa-p102">Vous pouvez également utiliser le Centre d'administration Exchange pour effectuer la migration intermédiaire. Voir [Effectuer une migration intermédiaire de la messagerie vers Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="84cfa-110">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="84cfa-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="84cfa-p103">Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d'informations sur les autres facteurs affectant la durée de migration des boîtes aux lettres vers Office 365, consultez la rubrique [Performances de migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="84cfa-p104">Des autorisations doivent vous être attribuées que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="84cfa-p105">Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="84cfa-118">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="84cfa-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="84cfa-119">Étapes de migration</span><span class="sxs-lookup"><span data-stu-id="84cfa-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="84cfa-120">Étape 1 : Préparez une migration intermédiaire</span><span class="sxs-lookup"><span data-stu-id="84cfa-120">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="84cfa-121">Avant de migrer les boîtes aux lettres vers Office 365 en utilisant une migration intermédiaire, vous devez apporter certaines modifications à votre environnement Exchange.</span><span class="sxs-lookup"><span data-stu-id="84cfa-121">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="84cfa-p106">**Configurer Outlook Anywhere sur votre Exchange Server local** Le service de migration de la messagerie utilise Outlook Anywhere (également appelé RPC sur HTTP) pour se connecter à votre Exchange Server local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange Server 2007 et Exchange 2003, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="84cfa-124">Exchange 2007 : Procédure d'activation d'Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="84cfa-124">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="84cfa-125">Procédure de configuration d'Outlook Anywhere avec Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="84cfa-125">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="84cfa-p107">Vous devez utiliser un certificat émis par une autorité de certification (AC) approuvée pour votre configuration Outlook Anywhere. Outlook Anywhere ne peut pas être configuré avec un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="84cfa-129">**Facultatif : vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-129">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="84cfa-130">Utilisez Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-130">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="84cfa-p108">Utilisez l'[analyseur de connectivité à distance Exchange](https://www.testexchangeconnectivity.com/) de Microsoft pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p108">Use the [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="84cfa-133">Dans Exchange Online PowerShell, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-133">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="84cfa-p109">**Définir des autorisations** Le compte d'utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange locale (également appelé administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous voulez migrer vers Office 365. Ce compte est utilisé lorsque vous vous connectez à votre système de messagerie en créant le point de terminaison de la migration (voir plus bas dans la procédure,[Étape 3 : Créez un point de terminaison de migration](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="84cfa-136">Pour migrer les boîtes aux lettres, l’administrateur doit disposer de l’un des jeux d’autorisations suivants :</span><span class="sxs-lookup"><span data-stu-id="84cfa-136">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="84cfa-137">Être membre du groupe **Administrateurs du domaine** dans Active Directory au sein de l'organisation locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-137">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="84cfa-138">ou</span><span class="sxs-lookup"><span data-stu-id="84cfa-138">or</span></span>
    
- <span data-ttu-id="84cfa-139">Disposer de l'autorisation **Accès total** pour chaque boîte aux lettres locale et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur les comptes des utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="84cfa-139">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="84cfa-140">ou</span><span class="sxs-lookup"><span data-stu-id="84cfa-140">or</span></span>
    
- <span data-ttu-id="84cfa-141">Disposer de l'autorisation **Recevoir en tant que** sur la base de données de boîtes aux lettres locale qui contient les boîtes aux lettres utilisateur et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur le compte d'utilisateur local.</span><span class="sxs-lookup"><span data-stu-id="84cfa-141">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="84cfa-142">Pour des instructions sur la définition de ces autorisations, voir [Attribution d'autorisations pour la migration de boîtes aux lettres vers Exchange Online](https://go.microsoft.com/fwlink/?LinkId=521656).</span><span class="sxs-lookup"><span data-stu-id="84cfa-142">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="84cfa-p110">**Désactiver la messagerie unifiée (MU)** Si la messagerie unifiée est activée pour les boîtes aux lettres locales que vous migrez, désactivez-la avant la migration. Réactivez-la ensuite pour les boîtes aux lettres une fois la migration terminée. Pour la procédure correspondante, voir[Désactivation d'une messagerie unifiée pour un utilisateur](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="84cfa-p111">**Utiliser la synchronisation d'annuaires pour créer de nouveaux utilisateurs dans Office 365** La synchronisation d'annuaires vous permet de créer tous les utilisateurs locaux de votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p111">**Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="84cfa-p112">Vous devez attribuer une licence aux utilisateurs créés. Vous disposez pour cela de 30 jours à compter de leur création. Pour la procédure d'ajout de licences, voir [Étape 8 : Exécutez les tâches post-migration](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="84cfa-p113">Vous pouvez utiliser l'outil de synchronisation de Microsoft Azure Active Directory ou Microsoft Azure Active Directory Sync Services (AAD Sync) pour synchroniser et créer vos utilisateurs locaux dans Office 365. Une fois les boîtes aux lettres migrées dans Office 365, vous pouvez gérer les comptes d'utilisateurs dans votre organisation locale et ceux-ci sont synchronisés avec votre organisation Office 365. Pour plus d'informations, voir [Intégration d'annuaire](https://go.microsoft.com/fwlink/?LinkId=521788).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p113">You can use either the Microsoft Azure Active Directory Synchronization Tool or the Microsoft Azure Active Directory Sync Services (AAD Sync) to synchronize and create your on-premises users in Office 365. After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="84cfa-154">Étape 2 : Créez un fichier CSV pour un lot de migration intermédiaire</span><span class="sxs-lookup"><span data-stu-id="84cfa-154">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="84cfa-p114">Après avoir identifié les utilisateurs dont vous souhaitez migrer les boîtes aux lettres locales vers Office 365, vous devez utiliser un fichier de valeurs séparées par des virgules (CSV) pour créer un lot de migration. Chaque ligne du fichier CSV (utilisé par Office 365 pour effectuer la migration) contient des informations sur une boîte aux lettres locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p114">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="84cfa-p115">Il n'existe aucune limite au nombre de boîtes aux lettres que vous pouvez migrer vers Office 365 lors d'une migration intermédiaire. Le fichier CSV d'un lot de migration peut contenir au maximum 2 000 lignes. Pour migrer plus de 2 000 boîtes aux lettres, vous devez créer des fichiers CSV supplémentaires et les utiliser pour créer de nouveaux lots de migration.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p115">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="84cfa-160">**Attributs pris en charge**</span><span class="sxs-lookup"><span data-stu-id="84cfa-160">**Supported attributes**</span></span>
  
<span data-ttu-id="84cfa-p116">Le fichier CSV destiné à une migration intermédiaire prend en charge les trois attributs suivants. Chaque ligne du fichier CSV correspond à une boîte aux lettres et doit contenir une valeur pour chacun des attributs ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="84cfa-163">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="84cfa-163">**Attribute**</span></span>|<span data-ttu-id="84cfa-164">**Description**</span><span class="sxs-lookup"><span data-stu-id="84cfa-164">**Description**</span></span>|<span data-ttu-id="84cfa-165">**Requis ?**</span><span class="sxs-lookup"><span data-stu-id="84cfa-165">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="84cfa-166">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="84cfa-166">EmailAddress</span></span>  <br/> |<span data-ttu-id="84cfa-167">Permet de définir l’adresse de messagerie SMTP principale, par exemple pilarp@contoso.com, pour les boîtes aux lettres locales.</span><span class="sxs-lookup"><span data-stu-id="84cfa-167">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="84cfa-p117">Utilisez bien lʼadresse SMTP principale des boîtes aux lettres locales et non les identifiants utilisateur issus d'Office 365. Par exemple, si le nom de domaine local est contoso.com alors que le nom de domaine de messagerie Office 365 est service.contoso.com, vous devez utiliser le nom de domaine contoso.com pour les adresses de messagerie dans le fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="84cfa-170">Requis</span><span class="sxs-lookup"><span data-stu-id="84cfa-170">Required</span></span>  <br/> |
|<span data-ttu-id="84cfa-171">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="84cfa-171">Password</span></span>  <br/> |<span data-ttu-id="84cfa-p118">Mot de passe à définir pour la nouvelle boîte aux lettres Office 365. Toutes les restrictions de mot de passe appliquées à votre organisation Office 365 s'appliquent également aux mots de passe inclus dans le fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p118">The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="84cfa-174">Facultatif</span><span class="sxs-lookup"><span data-stu-id="84cfa-174">Optional</span></span>  <br/> |
|<span data-ttu-id="84cfa-175">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="84cfa-175">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="84cfa-p119">Permet d'indiquer si les utilisateurs doivent modifier le mot de passe la première fois qu'ils se connectent à leur boîte aux lettres Office 365. Pour ce paramètre, utilisez la valeur **True** ou **False**. </span><span class="sxs-lookup"><span data-stu-id="84cfa-p119">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="84cfa-178">> [!NOTE]> Si vous avez implémenté une solution d'authentification unique (SSO) en déployant Active Directory Federation Services (AD FS) dans votre organisation locale, vous devez utiliser la valeur **False** pour l'attribut **ForceChangePassword**.</span><span class="sxs-lookup"><span data-stu-id="84cfa-178">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="84cfa-179">Facultatif</span><span class="sxs-lookup"><span data-stu-id="84cfa-179">Optional</span></span>  <br/> |
   
 <span data-ttu-id="84cfa-180">**Format de fichier CSV**</span><span class="sxs-lookup"><span data-stu-id="84cfa-180">**CSV file format**</span></span>
  
<span data-ttu-id="84cfa-p120">Voici un exemple de format pour le fichier CSV. Dans cet exemple, trois boîtes aux lettres locales sont migrées vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="84cfa-p121">La première ligne, ou ligne d'en-tête, du fichier CSV répertorie les noms des attributs, ou champs, spécifiés dans les lignes qui suivent. Les noms d'attributs sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="84cfa-p122">Chaque ligne sous la ligne d’en-tête représente un utilisateur et fournit les informations qui seront utilisées pour migrer la boîte aux lettres de l’utilisateur. Les valeurs d’attribut de chaque ligne doivent respecter l’ordre des noms d’attribut dans la ligne d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="84cfa-p123">Pour créer le fichier CSV, utilisez un éditeur de texte ou une application telle qu’Excel. Enregistrez le fichier au format .csv ou .txt.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="84cfa-p124">Si le fichier CSV contient des caractères non ASCII ou des caractères spéciaux, enregistrez-le avec l’encodage UTF-8 ou un autre encodage Unicode. Selon l’application, l’enregistrement du fichier CSV avec l’encodage UTF-8 ou un autre encodage Unicode peut être facilité lorsque les paramètres régionaux système de l’ordinateur correspondent à la langue utilisée dans le fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="84cfa-191">Étape 3 : Créez un point de terminaison de migration</span><span class="sxs-lookup"><span data-stu-id="84cfa-191">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="84cfa-192"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-192"></span></span>

<span data-ttu-id="84cfa-p125">Pour que la migration fonctionne, Office 365 doit pouvoir se connecter au système de messagerie source et communiquer avec lui. Pour ce faire, Office 365 utilise un point de terminaison. Pour créer un point de terminaison de migration Outlook Anywhere à l'aide de PowerShell, afin d'effectuer une migration intermédiaire, commencez par vous [connecter à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="84cfa-p125">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="84cfa-196">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="84cfa-196">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="84cfa-197">Pour créer un point de terminaison de migration Outlook Anywhere appelé « StagedEndpoint » dans Exchange Online PowerShell, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-197">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="84cfa-198">Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="84cfa-198">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="84cfa-p126">La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="84cfa-201">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="84cfa-201">Verify it worked</span></span>

<span data-ttu-id="84cfa-202">Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « StagedEndpoint » :</span><span class="sxs-lookup"><span data-stu-id="84cfa-202">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="84cfa-203">Étape 4 : Créez et démarrez un lot de migration intermédiaire</span><span class="sxs-lookup"><span data-stu-id="84cfa-203">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="84cfa-204"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-204"></span></span>

<span data-ttu-id="84cfa-p127">La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="84cfa-p128">Cet exemple de code crée également un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'une seule lot de migration à basculement à la fois.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="84cfa-212">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="84cfa-212">Verify it worked</span></span>

<span data-ttu-id="84cfa-213">Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « StagedBatch1 » :</span><span class="sxs-lookup"><span data-stu-id="84cfa-213">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="84cfa-214">Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="84cfa-214">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="84cfa-215">Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="84cfa-215">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="84cfa-216">Étape 5 : Convertissez des boîtes aux lettres locales en utilisateurs à extension messagerie</span><span class="sxs-lookup"><span data-stu-id="84cfa-216">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="84cfa-217"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-217"></span></span>

<span data-ttu-id="84cfa-p129">Une fois la migration d'un premier lot effectuée, vous devez permettre aux utilisateurs d'accéder à leur messagerie. Un utilisateur dont la boîte aux lettres a été migrée dispose de deux boîtes aux lettres : une en local et une autre dans Office 365. Les utilisateurs ayant une boîte aux lettres dans Office 365 ne reçoivent plus de messages dans leur boîte aux lettres locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="84cfa-p130">Toutes les migrations n'ayant pas encore été effectuées, vous ne pouvez pas encore rediriger l'ensemble des utilisateurs vers Office 365 pour qu'ils accèdent à leur messagerie électronique. Que faire alors pour les personnes qui disposent de deux boîtes aux lettres ? Eh bien vous pouvez convertir les boîtes aux lettres qui ont déjà été migrées en utilisateurs à extension messagerie. Cette opération vous permet de rediriger l'utilisateur pour qu'il puisse accéder à sa messagerie dans Office 365, et non plus en local.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="84cfa-p131">Une autre raison importante justifiant la conversion des boîtes aux lettres locales en utilisateurs à extension messagerie est que cette opération permet de conserver les adresses proxy des boîtes aux lettres Office 365 en les copiant vers les utilisateurs à extension messagerie. Cela vous permet de gérer des utilisateurs en nuage à partir de votre organisation locale à l'aide d'Active Directory. De plus, si vous décidez de mettre hors service votre organisation Exchange Server locale une fois toutes les boîtes aux lettres migrées vers Office 365, les adresses proxy que vous avez copiées vers les utilisateurs à extension messagerie sont conservées dans votre instance Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
  
<span data-ttu-id="84cfa-228">Pour obtenir plus d’informations et télécharger des scripts que vous pouvez exécuter pour convertir des boîtes aux lettres en utilisateurs à extension messagerie, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-228">For more information, and to download scripts that you can run to convert mailboxes to mail-enabled users, see the following:</span></span>
  
- [<span data-ttu-id="84cfa-229">Convertir des boîtes aux lettres Exchange 2007 en utilisateurs à extension messagerie</span><span class="sxs-lookup"><span data-stu-id="84cfa-229">Convert Exchange 2007 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [<span data-ttu-id="84cfa-230">Convertir des boîtes aux lettres Exchange 2003 en utilisateurs à extension messagerie</span><span class="sxs-lookup"><span data-stu-id="84cfa-230">Convert Exchange 2003 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="84cfa-231">Étape 6 : Supprimez un lot de migration intermédiaire</span><span class="sxs-lookup"><span data-stu-id="84cfa-231">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="84cfa-232"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-232"></span></span>

 <span data-ttu-id="84cfa-p132">Après avoir migré toutes les boîtes aux lettres d'un lot de migration et converti les boîtes aux lettres locales du lot en utilisateurs à extension messagerie, vous êtes prêt à supprimer un lot de migration intermédiaire. Vérifiez que le courrier électronique est transféré aux boîtes aux lettres Office 365 du lot de migration. Lorsque vous supprimez un lot de migration intermédiaire, le service de migration nettoie tous les enregistrements associés au lot de migration, puis supprime ce dernier.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p132">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="84cfa-236">Pour supprimer le lot de migration « StagedBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="84cfa-236">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="84cfa-237">Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="84cfa-237">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="84cfa-238">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="84cfa-238">Verify it worked</span></span>

<span data-ttu-id="84cfa-239">Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :</span><span class="sxs-lookup"><span data-stu-id="84cfa-239">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="84cfa-240">La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="84cfa-240">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="84cfa-241">Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="84cfa-241">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="84cfa-242">Étape 7 : Attribuez des licences aux utilisateurs Office 365</span><span class="sxs-lookup"><span data-stu-id="84cfa-242">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="84cfa-243"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-243"></span></span>

<span data-ttu-id="84cfa-244">Pour activer les comptes d'utilisateur Office 365 correspondant aux comptes migrés, vous devez leur attribuer des licences.</span><span class="sxs-lookup"><span data-stu-id="84cfa-244">Activate Office 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="84cfa-245">Si vous n’attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours).</span><span class="sxs-lookup"><span data-stu-id="84cfa-245">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="84cfa-246">Pour savoir comment attribuer une licence dans le Centre d'administration Microsoft 365, voir [Attribuer ou retirer des licences pour Office 365 pour les entreprises](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="84cfa-246">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="84cfa-247">Étape 8 : Exécutez les tâches post-migration</span><span class="sxs-lookup"><span data-stu-id="84cfa-247">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="84cfa-248"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="84cfa-248"></span></span>

- <span data-ttu-id="84cfa-p134">**Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres**Une fois toutes les boîtes aux lettres locales migrées vers Office 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Office 365 afin de permettre aux utilisateurs de se connecter aisément à leurs nouvelles boîtes aux lettres Office 365 avec des clients mobiles et Outlook. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui de votre organisation Office 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l'enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p134">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="84cfa-p135">Office 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients mobiles et Outlook. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-p135">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="84cfa-255">**Alias :** autodiscover</span><span class="sxs-lookup"><span data-stu-id="84cfa-255">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="84cfa-256">**Cible :** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="84cfa-256">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="84cfa-257">Pour plus d'informations, voir [Créer des enregistrements DNS pour Office 365 lors de la gestion de vos enregistrements DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="84cfa-257">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="84cfa-p136">**Désactiver des serveurs Exchange locaux** Après avoir vérifié que tout le courrier est acheminé directement vers les boîtes aux lettres Office 365, si vous n'avez plus besoin de conserver votre organisation de messagerie locale ou que vous ne comptez pas implémenter de solution SSO, vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="84cfa-p136">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="84cfa-260">Pour plus d’informations, voir les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="84cfa-260">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="84cfa-261">Modifier ou supprimer Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="84cfa-261">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="84cfa-262">Procédure de suppression d'une organisation Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="84cfa-262">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="84cfa-263">Procédure de désinstallation d'Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="84cfa-263">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

