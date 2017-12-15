---
title: "Regroupement des données des rapports d'un client via Windows PowerShell pour les partenaires avec autorisation d'accès délégué"
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Regroupement des données des rapports d'un client via Windows PowerShell pour les partenaires avec autorisation d'accès délégué

 **Résumé :** Utiliser Windows PowerShell pour Office 365 pour récupérer des rapports sur tous les baux de client et d’agréger les données dans un emplacement unique.
  
Par défaut, Windows PowerShell pour Office 365 ne dispose pas d'une fonction intégrée de regroupement de données des rapports pour plusieurs locations de client. Toutefois, vous pouvez utiliser cet exemple de script Windows PowerShell pour Office 365 pour itérer l'opération dans toutes les locations de votre client afin de récupérer un rapport unique pour chacun de vos clients, puis regrouper les données des rapports à un emplacement unique. Vous obtenez ainsi un rapport unique pour tous les locataires de votre client. 
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients. Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations Administrer au nom de sur leslocations clientes. Ainsi, ils peuvent administrer les locations clientes et créer des rapports les concernant.
## <a name="before-you-begin"></a>Avant de commencer

Pour utiliser ce script, vous devez insérer vos valeurs particulières dans ces variables :
  
- **$UserName**: nom d'utilisateur d'administrateur de votre partenaire. Ces informations d'identification seront utilisées pour la connexion à toutes les locations de votre client.
    
- **$OutputFile**: fichier CSV dans lequel les données des rapports seront regroupées.
    
- **$ErrorFile**: fichier journal des erreurs.
    
- **$ScriptBlock**: cet exemple de script utilise **Get-MailboxActivityReport** et des paramètres (par exemple, les dates de début et de fin) pour que vous puissiez commencer. Si vous voulez d'autres rapports, remplacez le nom du rapport que vous voulez et les paramètres nécessaires pour **Get-MailboxActivityReport**.
    
- Ouvrez une session Remote Windows PowerShell pour Exchange Online à l'aide de la procédure décrite dans [Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Utilisez Windows PowerShell pour regrouper des rapports sur les locataires du client à un emplacement unique.

1. Copiez et collez ce script dans le bloc-notes.
    
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

2. Enregistrez le script sous le nom GetMailboxActivityReport.ps1 à un emplacement facile à trouver. Aux fins de l'exemple, le fichier est enregistré dans C:\\O365 Scripts. 
    
3. Exécutez le script dans Remote Windows PowerShell en suivant cette syntaxe.
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

Cet exemple de script place le rapport contenant les données regroupées dans le fichier ReportOutput.csv.
  
## <a name="see-also"></a>See also

#### 

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Service web de création de rapports Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de création de rapports dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

