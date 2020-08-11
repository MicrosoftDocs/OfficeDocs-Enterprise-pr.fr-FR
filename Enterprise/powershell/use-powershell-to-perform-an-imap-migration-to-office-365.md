---
title: Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: Découvrez comment utiliser PowerShell pour effectuer une migration IMAP (Internet Mail Access Protocol) vers Microsoft 365.
ms.openlocfilehash: 0254f35791ac83aed1afff293c98fcd654a27480
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606200"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a><span data-ttu-id="956f1-103">Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="956f1-103">Use PowerShell to perform an IMAP migration to Microsoft 365</span></span>

<span data-ttu-id="956f1-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="956f1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="956f1-p101">Dans le cadre du déploiement de Microsoft 365, vous pouvez choisir de migrer le contenu des boîtes aux lettres utilisateur à partir d’un service de messagerie IMAP (Internet Mail Access Protocol) vers Microsoft 365. Cet article vous guide tout au long des tâches relatives à la migration IMAP de courrier électronique à l’aide d’Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="956f1-p101">As part of the process of deploying Microsoft 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Microsoft 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="956f1-p102">Vous pouvez également utiliser le centre d’administration Exchange pour effectuer une migration IMAP. Voir [migrer vos boîtes aux lettres IMAP](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span><span class="sxs-lookup"><span data-stu-id="956f1-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="956f1-109">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="956f1-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="956f1-p103">Durée d’exécution estimée de cette tâche : 2-5 minutes pour créer un lot de migration. Une fois le lot de migration démarré, la durée de la migration varie en fonction du nombre de boîtes aux lettres du lot, de la taille de chaque boîte aux lettres et de la capacité réseau disponible. Pour plus d’informations sur les autres facteurs qui influent sur la durée de migration des boîtes aux lettres vers Microsoft 365, consultez la rubrique performance de la [migration](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="956f1-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="956f1-p104">Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="956f1-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="956f1-p105">Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="956f1-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="956f1-117">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="956f1-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="956f1-118">Les migrations IMAP font l'objet des restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="956f1-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="956f1-p106">Vous pouvez migrer uniquement des éléments figurant dans la boîte de réception ou d'autres dossiers de courrier d'un utilisateur. Vous ne pouvez pas migrer des contacts, des éléments du calendrier ou des tâches.</span><span class="sxs-lookup"><span data-stu-id="956f1-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="956f1-121">Vous ne pouvez pas migrer plus de 500 000 éléments d'une boîte aux lettres d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="956f1-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="956f1-122">Vous ne pouvez pas non plus migrer des messages d’une taille supérieure à 35 Mo.</span><span class="sxs-lookup"><span data-stu-id="956f1-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="956f1-123">Étapes de migration</span><span class="sxs-lookup"><span data-stu-id="956f1-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="956f1-124">Étape 1 : Préparez une migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="956f1-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-125"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="956f1-p107">**Si vous disposez d’un domaine pour votre organisation IMAP, ajoutez-le en tant que domaine accepté de votre organisation Microsoft 365.** Si vous souhaitez utiliser le même domaine que vous possédez déjà pour vos boîtes aux lettres Microsoft 365, vous devez d’abord l’ajouter en tant que domaine accepté à Microsoft 365. Une fois que vous l’avez ajouté, vous pouvez créer vos utilisateurs dans Microsoft 365. Pour plus d’informations, consultez[la rubrique Verify Your Domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="956f1-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Microsoft 365 organization.** If you want to use the same domain you already own for your Microsoft 365 mailboxes, you first have to add it as an accepted domain to Microsoft 365. After you have added it, you can create your users in Microsoft 365. For more information, see[Verify your domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="956f1-p108">**Ajoutez chaque utilisateur à Microsoft 365 afin qu’ils disposent d’une boîte aux lettres.** Pour obtenir des instructions, consultez la rubrique[Ajouter des utilisateurs à Microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span><span class="sxs-lookup"><span data-stu-id="956f1-p108">**Add each user to Microsoft 365 so that they have a mailbox.** For instructions, see[Add users to Microsoft 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="956f1-p109">**Obtenez le nom de domaine complet (FQDN) du serveur IMAP.** Lorsque vous créez un point de terminaison de migration IMAP, vous devez fournir le nom de domaine complet (FQDN) (également appelénom complet de l'ordinateur) du serveur IMAP à partir duquel vous allez migrer les données de boîte aux lettres. Utilisez un client IMAP ou la commande PING pour vérifier que vous pouvez utiliser le FQDN pour communiquer avec le serveur IMAP sur Internet.</span><span class="sxs-lookup"><span data-stu-id="956f1-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="956f1-p110">**Configurez le pare-feu pour autoriser les connexions IMAP.** Il se peut que vous deviez ouvrir des portes dans le pare-feu de l'organisation hébergeant le serveur IMAP afin que le trafic réseau en provenance du centre de données Microsoft durant la migration soit autorisé à pénétrer dans l'organisation hébergeant le serveur IMAP. Pour obtenir la liste des adresses IP utilisées par les centres de données Microsoft, consultez la rubrique relative aux[URL Exchange Online et plages d'adresses IP](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span><span class="sxs-lookup"><span data-stu-id="956f1-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="956f1-p111">**Attribuez les autorisations de compte administrateur pour accéder aux boîtes aux lettres de votre organisation**. Si vous utilisez des informations d'identification d'administrateur dans le fichier CSV, le compte utilisé doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales. Celles-ci sont déterminées par le serveur IMAP spécifique.</span><span class="sxs-lookup"><span data-stu-id="956f1-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="956f1-p112">**Pour utiliser les cmdlets Exchange Online PowerShell**, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, consultez la rubrique [Connexion à Exchange Online à l'aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="956f1-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="956f1-143">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="956f1-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="956f1-p113">**Vérifiez que vous pouvez vous connecter à votre serveur IMAP.** Pour tester les paramètres de connexion à votre serveur IMAP, exécutez la commande suivante dans Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="956f1-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="956f1-146">La valeur du paramètre **Port** utilisée est généralement 143 pour les connexions chiffrées ou TLS, et 993 pour les connexions SSL.</span><span class="sxs-lookup"><span data-stu-id="956f1-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="956f1-147">Étape 2 : Créez un fichier CSV pour un lot de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="956f1-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-148"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="956f1-p114">Identifiez le groupe d'utilisateurs dont vous voulez migrer les boîtes aux lettres dans un lot de migration IMAP. Chaque ligne du fichier CSV contient les informations nécessaires pour se connecter à une boîte aux lettres dans le système de messagerie IMAP.</span><span class="sxs-lookup"><span data-stu-id="956f1-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="956f1-151">Les attributs obligatoires pour chaque utilisateur sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="956f1-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="956f1-152">**EmailAddress** spécifie l’identifiant utilisateur pour la boîte aux lettres Microsoft 365 de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="956f1-152">**EmailAddress** specifies the user ID for the user's Microsoft 365 mailbox.</span></span>
    
- <span data-ttu-id="956f1-153">**UserName** spécifie le nom de connexion du compte à utiliser pour accéder à la boîte aux lettres sur le serveur IMAP.</span><span class="sxs-lookup"><span data-stu-id="956f1-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="956f1-154">**Password** spécifie le mot de passe du compte dans la colonne UserName **UserName**.</span><span class="sxs-lookup"><span data-stu-id="956f1-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="956f1-p115">Voici un exemple du format du fichier CSV. Dans cet exemple, trois boîtes aux lettres sont migrées :</span><span class="sxs-lookup"><span data-stu-id="956f1-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="956f1-157">Pour l'attribut **UserName**, en plus du nom d'utilisateur, vous pouvez utiliser les informations d'identification d'un compte disposant des autorisations nécessaires pour accéder à des boîtes aux lettres sur le serveur IMAP. Vous trouverez ci-dessous quelques-uns des formats spécifiques utilisés pour certains serveurs IMAP :</span><span class="sxs-lookup"><span data-stu-id="956f1-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="956f1-158">**Microsoft Exchange**</span><span class="sxs-lookup"><span data-stu-id="956f1-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="956f1-p116">Si vous migrez une messagerie à partir de l'implémentation IMAP pour Microsoft Exchange, utilisez le format **Domain/Admin_UserName/User_UserName** pour l'attribut **UserName** dans le fichier CSV. Supposons que vous migrez la messagerie à partir d'Exchange pour Terry Adams, Ann Beebe et Paul Cannon. Vous disposez d'un compte d'administrateur de messagerie dont le nom d'utilisateur est **mailadmin** et le mot de passe est **P@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :</span><span class="sxs-lookup"><span data-stu-id="956f1-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="956f1-163">**Dovecot**</span><span class="sxs-lookup"><span data-stu-id="956f1-163">**Dovecot:**</span></span>
  
<span data-ttu-id="956f1-p117">Pour les serveurs IMAP qui prennent en charge Simple Authentication and Security Layer (SASL), comme un serveur IMAP Dovecot, utilisez le format **User_UserName\*Admin_UserNam**, où l’astérisque (\*) est un caractère de séparation configurable. Supposons que vous migrez les mêmes boîtes aux lettres utilisateur à partir d’un serveur IMAP Dovecot à l’aide des informations d’identification d’administrateur **mailadmin** et **P@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :</span><span class="sxs-lookup"><span data-stu-id="956f1-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName\*Admin_UserName**, where the asterisk ( \* ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="956f1-167">**Mirapoint**</span><span class="sxs-lookup"><span data-stu-id="956f1-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="956f1-p118">Si vous migrez une messagerie à partir d'un serveur de messagerie Mirapoint, utilisez le format **#user@domain#Admin_UserName#** pour les informations d'identification d'administrateur. Pour migrer une messagerie à partir d'un serveur Mirapoint à l'aide des informations d'identification d'administrateur **mailadmin** et **P@ssw0rd**, votre fichier CSV ressemblerait à ceci :</span><span class="sxs-lookup"><span data-stu-id="956f1-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="956f1-170">**Courier IMAP :**</span><span class="sxs-lookup"><span data-stu-id="956f1-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="956f1-p119">Certains systèmes de courrier sources, comme Courier IMAP, ne prennent pas en charge l’utilisation des informations d’identification d’administrateur de boîte aux lettres pour migrer des boîtes aux lettres vers Microsoft 365. Au lieu de cela, vous pouvez configurer votre système de courrier source pour utiliser des dossiers partagés virtuels. À l’aide des dossiers partagés virtuels, vous pouvez utiliser les informations d’identification d’administrateur de boîtes aux lettres pour accéder aux boîtes aux lettres utilisateur sur le système de courrier source. Pour plus d’informations sur la configuration des dossiers partagés virtuels pour Courier IMAP, consultez la rubrique [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span><span class="sxs-lookup"><span data-stu-id="956f1-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Microsoft 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="956f1-p120">Pour migrer des boîtes aux lettres après avoir configuré des dossiers partagés virtuels sur votre système de messagerie source, vous devez inclure l'attribut facultatif **UserRoot** dans le fichier de migration. Cet attribut spécifie l'emplacement de la boîte aux lettres de chaque utilisateur dans la structure de dossiers partagés virtuels sur le système de messagerie source. Par exemple, le chemin d'accès de la boîte aux lettres de Terry est /users/terry.adams.</span><span class="sxs-lookup"><span data-stu-id="956f1-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="956f1-178">Voici un exemple de fichier CSV contenant l'attribut **UserRoot**:</span><span class="sxs-lookup"><span data-stu-id="956f1-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="956f1-179">Étape 3 : Créez un point de terminaison de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="956f1-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-180"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="956f1-p121">Pour migrer le courrier électronique correctement, Microsoft 365 doit se connecter au système de courrier source et communiquer avec lui. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Le point de terminaison de migration définit également le nombre de boîtes aux lettres à migrer simultanément et le nombre de boîtes aux lettres à synchroniser simultanément lors de la synchronisation incrémentielle, qui se produit une fois toutes les 24 heures. Pour créer un point de terminaison de migration pour la migration IMAP, [Connectez-vous d’abord à Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="956f1-p121">To migrate email successfully, Microsoft 365 needs to connect to and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="956f1-185">Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="956f1-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="956f1-186">Pour créer le point de terminaison de migration IMAP appelé « IMAPEndpoint » dans Exchange Online PowerShell, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="956f1-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="956f1-p122">Vous pouvez également ajouter des paramètres pour spécifier les migrations simultanées, les migrations incrémentielles simultanées et le port à utiliser. La commande Exchange Online PowerShell suivante crée un point de terminaison de migration IMAP appelé « IMAPEndpoint » qui prend en charge 50 migrations simultanées et jusqu'à 25 synchronisations incrémentielles simultanées. Il configure également le point de terminaison pour utiliser le port 143 pour le chiffrement TLS.</span><span class="sxs-lookup"><span data-stu-id="956f1-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="956f1-190">Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="956f1-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="956f1-191">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="956f1-191">Verify it worked</span></span>

<span data-ttu-id="956f1-192">Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPEndpoint » :</span><span class="sxs-lookup"><span data-stu-id="956f1-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="956f1-193">Étape 4 : Créez et démarrez un lot de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="956f1-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-194"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="956f1-p123">La cmdlet [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) permet de créer un lot pour une migration IMAP. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer son traitement par la suite à l'aide de la cmdlet [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440).</span><span class="sxs-lookup"><span data-stu-id="956f1-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="956f1-198">La commande Exchange Online PowerShell suivante démarre automatiquement le lot de migration appelé « IMAPBatch1 » à l’aide du point de terminaison IMAP appelé « IMAPEndpoint » :</span><span class="sxs-lookup"><span data-stu-id="956f1-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="956f1-199">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="956f1-199">Verify it worked</span></span>

<span data-ttu-id="956f1-200">Exécuter la cmdlet [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) pour afficher des informations sur le lot « IMAPBatch1 » :</span><span class="sxs-lookup"><span data-stu-id="956f1-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="956f1-201">Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="956f1-201">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a><span data-ttu-id="956f1-202">Étape 5 : acheminer votre courrier électronique vers Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="956f1-202">Step 5: Route your email to Microsoft 365</span></span>
<span data-ttu-id="956f1-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-203"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="956f1-p124">Les systèmes de courrier utilisent un enregistrement DNS appelé enregistrement MX pour déterminer l’emplacement de remise des courriers. Pendant le processus de migration du courrier, votre enregistrement MX pointait vers votre système de courrier source. Une fois la migration de la messagerie vers Microsoft 365 terminée, il est temps de faire pointer votre enregistrement MX sur Microsoft 365. Cela permet de s’assurer que le courrier électronique est remis à vos boîtes aux lettres Microsoft 365. En déplacant l’enregistrement MX, vous pouvez également désactiver votre ancien système de courrier lorsque vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Microsoft 365 is complete, it's time to point your MX record at Microsoft 365. This helps make sure that email is delivered to your Microsoft 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="956f1-p125">Pour de nombreux fournisseurs DNS, il existe des instructions spécifiques pour modifier votre enregistrement MX. Si votre fournisseur DNS n’est pas inclus ou si vous souhaitez obtenir un sens général, les [instructions générales de l’enregistrement MX](https://go.microsoft.com/fwlink/?LinkId=397449) sont également fournies.</span><span class="sxs-lookup"><span data-stu-id="956f1-p125">For many DNS providers, there are specific instructions to change your MX record. If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="956f1-p126">Il faut compter jusqu’à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l’enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : Étape 6 : Supprimez le lot de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="956f1-213">Étape 6 : Supprimez le lot de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="956f1-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="956f1-214"><a name="BK_Step6"> </a></span></span>

<span data-ttu-id="956f1-p127">Une fois que vous avez modifié l’enregistrement MX et vérifié que tous les messages sont acheminés vers les boîtes aux lettres Microsoft 365, informez-les aux utilisateurs que leur courrier va vers Microsoft 365. Après cela, vous pouvez supprimer le lot de migration IMAP. Vérifiez ce qui suit avant de supprimer le lot de migration.</span><span class="sxs-lookup"><span data-stu-id="956f1-p127">After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="956f1-p128">Tous les utilisateurs utilisent des boîtes aux lettres Microsoft 365. Après la suppression du lot, les messages envoyés à des boîtes aux lettres sur le serveur Exchange local ne sont pas copiés dans les boîtes aux lettres Microsoft 365 correspondantes.</span><span class="sxs-lookup"><span data-stu-id="956f1-p128">All users are using Microsoft 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Microsoft 365 mailboxes.</span></span>
    
- <span data-ttu-id="956f1-p129">Les boîtes aux lettres Microsoft 365 ont été synchronisées au moins une fois après leur envoi direct par le courrier. Pour ce faire, assurez-vous que la valeur de la zone heure de la dernière synchronisation du lot de migration est plus récente que celle de l’envoi de messages démarré directement aux boîtes aux lettres Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="956f1-p129">Microsoft 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Microsoft 365 mailboxes.</span></span>
    
<span data-ttu-id="956f1-222">Pour supprimer le lot de migration « IMAPBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="956f1-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="956f1-223">Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="956f1-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="956f1-224">Vérifier que l’opération a fonctionné</span><span class="sxs-lookup"><span data-stu-id="956f1-224">Verify it worked</span></span>

<span data-ttu-id="956f1-225">Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :</span><span class="sxs-lookup"><span data-stu-id="956f1-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="956f1-226">La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="956f1-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="956f1-227">Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="956f1-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="956f1-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="956f1-228">See also</span></span>

[<span data-ttu-id="956f1-229">Utilitaire de dépannage de migration IMAP</span><span class="sxs-lookup"><span data-stu-id="956f1-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

