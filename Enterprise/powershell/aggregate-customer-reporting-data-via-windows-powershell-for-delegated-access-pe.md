---
title: "Regroupement des données des rapports d’un client via Windows PowerShell pour les partenaires avec autorisation d’accès délégué"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "Résumé : Utiliser Windows PowerShell pour Office 365 pour récupérer des rapports sur toutes les locations de client et regrouper les données à un emplacement unique."
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="699d9-103">Regroupement des données des rapports d’un client via Windows PowerShell pour les partenaires avec autorisation d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="699d9-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="699d9-104">**Résumé :** Utilisez Windows PowerShell pour Office 365 pour récupérer des rapports sur toutes les locations de client et regrouper les données à un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="699d9-104">Summary: Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="699d9-p101">Par défaut, Windows PowerShell pour Office 365 ne dispose pas d'une fonction intégrée de regroupement de données des rapports pour plusieurs locations de client. Toutefois, vous pouvez utiliser cet exemple de script Windows PowerShell pour Office 365 pour itérer l'opération dans toutes les locations de votre client afin de récupérer un rapport unique pour chacun de vos clients, puis regrouper les données des rapports à un emplacement unique. Vous obtenez ainsi un rapport unique pour tous les locataires de votre client.</span><span class="sxs-lookup"><span data-stu-id="699d9-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="699d9-p102">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients. Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations Administrer au nom de sur leslocations clientes. Ainsi, ils peuvent administrer les locations clientes et créer des rapports les concernant.</span><span class="sxs-lookup"><span data-stu-id="699d9-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="699d9-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="699d9-112">Before you begin</span></span>

<span data-ttu-id="699d9-113">Pour utiliser ce script, vous devez insérer vos valeurs particulières dans ces variables :</span><span class="sxs-lookup"><span data-stu-id="699d9-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="699d9-p103">**$UserName**: nom d'utilisateur d'administrateur de votre partenaire. Ces informations d'identification seront utilisées pour la connexion à toutes les locations de votre client.</span><span class="sxs-lookup"><span data-stu-id="699d9-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="699d9-116">**$OutputFile**: fichier CSV dans lequel les données des rapports seront regroupées.</span><span class="sxs-lookup"><span data-stu-id="699d9-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="699d9-117">**$ErrorFile**: fichier journal des erreurs.</span><span class="sxs-lookup"><span data-stu-id="699d9-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="699d9-p104">**$ScriptBlock**: cet exemple de script utilise **Get-MailboxActivityReport** et des paramètres (par exemple, les dates de début et de fin) pour que vous puissiez commencer. Si vous voulez d'autres rapports, remplacez le nom du rapport que vous voulez et les paramètres nécessaires pour **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="699d9-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="699d9-120">Ouvrez une session Remote Windows PowerShell pour Exchange Online à l'aide de la procédure décrite dans [Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="699d9-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="699d9-121">Utilisez Windows PowerShell pour regrouper des rapports sur les locataires du client à un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="699d9-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="699d9-122">Copiez et collez ce script dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="699d9-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="699d9-p105">Enregistrez le script sous le nom GetMailboxActivityReport.ps1 à un emplacement facile à trouver. Aux fins de l'exemple, le fichier est enregistré dans C:\\O365 Scripts.</span><span class="sxs-lookup"><span data-stu-id="699d9-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="699d9-125">Exécutez le script dans Remote Windows PowerShell en suivant cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="699d9-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="699d9-126">Cet exemple de script place le rapport contenant les données regroupées dans le fichier ReportOutput.csv.</span><span class="sxs-lookup"><span data-stu-id="699d9-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="699d9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="699d9-127">See also</span></span>

#### 

[<span data-ttu-id="699d9-128">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="699d9-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="699d9-129">Service web de création de rapports Office 365</span><span class="sxs-lookup"><span data-stu-id="699d9-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="699d9-130">Cmdlets de création de rapports dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="699d9-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

