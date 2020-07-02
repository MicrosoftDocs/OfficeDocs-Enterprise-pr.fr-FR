---
title: Automatiser la collecte de fichiers pour eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Résumé : Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997975"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatiser la collecte de fichiers pour eDiscovery

All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel. 
  
eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.
  
Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.
  
## <a name="what-this-solution-does"></a>Descriptif de cette solution

This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery. 
  
> [!IMPORTANT]
> This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file. 
  
Le diagramme suivant vous guide à travers les étapes et les éléments de la solution.
  
![Vue d’ensemble de la solution de regroupement automatique de fichiers](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****Légende****||
|:-----|:-----|
|![légende magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Créez un objet de stratégie de groupe (GPO) et associez-le au script d’ouverture de session de collecte.  <br/> |
|![légende magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Configurez le filtre de sécurité de l’objet de stratégie de groupe pour appliquer l’objet de stratégie de groupe uniquement au groupe des dépositaires. <br/> |
|![légende magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Un dépositaire ouvre une session et l’objet de stratégie de groupe s’exécute, appelant le script d’ouverture de session de collecte  <br/> |
|![légende magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|Le script d’ouverture de session de collecte répertorie tous les lecteurs connectés localement à l’ordinateur des dépositaires, en cherchant les fichiers que vous souhaitez et en enregistrant leur emplacement.  <br/> |
|![légende magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|Le script d’ouverture de session de collecte copie les fichiers inventoriés sur un partage de fichiers caché sur le serveur intermédiaire.  <br/> |
|![légende magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (Option A) Exécutez manuellement le script d'importation PST pour importer les fichiers PST collectés dans Exchange Server 2013. <br/> |
|![légende magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Option B) À l’aide de l’outil et du processus d’importation de Microsoft 365, importez les fichiers PST collectés dans Exchange Online.  <br/> |
|![légende magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Déplacez tous les fichiers collectés vers un partage de fichiers Azure pour un stockage à long terme avec le runbook MoveToColdStorageSystem Center Orchestrator 2012 R2. <br/> |
|![légende magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexez les fichiers dans le partage des fichiers de stockage froid avec SharePoint 2013.  <br/> |
|![légende magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Effectuez eDiscovery sur le contenu dans l'espace de stockage froid et le Exchange Server 2013 sur site.  <br/> |
|![légende magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Effectuer eDiscovery sur le contenu de Microsoft 365.  <br/> |
   
## <a name="prerequisites"></a>Conditions préalables

The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.
  
### <a name="base-configuration"></a>Configuration de base

|**Élément**|**Lien**|
|:-----|:-----|
|Domaine Services de domaine Active Directory (AD DS)  <br/> ||
|Connectivité Internet à partir de votre réseau local  <br/> ||
|SQL Server 2012 pour prendre en charge SharePoint 2013 et System Center Orchestrator 2012 R2  <br/> |[Déploiement de System Center 2012 - Orchestrator](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| Sur site ou SharePoint 2013 basé sur Azure pour eDiscovery (requis pour l'option A) <br/> ||
|Serveur de partage de fichiers sur site pour le placement en zone de transit  <br/> ||
|Exchange Server 2013 sur site pour l'importation du PST de l'option A  <br/> |La mise à jour cumulative 5 (15.913.22) est disponible sur le site [Mise à jour cumulative 5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Déploiement de System Center 2012 - Orchestrator](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Microsoft 365 E3 avec Exchange Online et SharePoint Online (requis pour l’option B)  <br/> |Pour vous inscrire à un abonnement Microsoft 365 E3, consultez la rubrique [microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).  <br/> |
|Abonnement Azure avec un ordinateur virtuel  <br/> |Pour vous inscrire à Azure, voir la page d'[abonnement à Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Une connexion VPN entre votre réseau local et votre abonnement Azure  <br/> |Pour configurer un tunnel VPN entre votre abonnement Azure et votre réseau local, voir [Connecter un réseau local à Microsoft Azure Virtual Network](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery configuré pour effectuer une recherche dans SharePoint et Exchange Server 2013, et éventuellement Lync Server 2013  <br/> |Pour configurer la eDiscovery de cette façon, voir [Configurer eDiscovery dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) et[Guide de laboratoire de test : configurez eDiscovery pour un laboratoire de test de partages de fichiers Exchange, Lync, SharePoint et Windows ](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery dans Microsoft 365 pour SharePoint Online et Exchange Online  <br/> |Pour configurer la fonctionnalité eDiscovery dans Microsoft 365, voir [configurer un centre eDiscovery dans SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurer l’environnement

Maintenant que la configuration de base est en place, vous pouvez passer à la configuration de la solution elle-même. 
  
### <a name="staging-file-share"></a>Partage de fichiers intermédiaires

1. Dans le domaine local, créez un groupe de sécurité global nommé Custodians.
    
2. Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.
    
3. Définissez les autorisations de partage suivantes :
    
  - Dépositaires : Modifier, Lire
    
  - Administrateurs : Contrôle total
    
  - Sous-système approuvé Exchange : Modifier, Lire
    
4. Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:
    
  - **Type : Refuser**
    
  - **S'applique à : Ce dossier, les sous-dossiers et les fichiers**
    
5. Cliquez sur **Autorisations avancées** et sélectionnez ce qui suit :
    
  - **Lecture des attributs**
    
  - **Lecture des attributs étendus**
    
  - **Autorisations de lecture**
    
6. Testez l’accès au partage de fichiers Cases$ en effectuant les étapes suivantes :
    
1. Ajoutez un utilisateur au groupe des dépositaires.
    
2. Placez un fichier dans le dossier Cases$.
    
3. As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.
    
4. Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.
    
5. Try to open the file you previously placed in the share. This should fail.
    
### <a name="logon-script"></a>Script d’ouverture de session

1. Copiez et collez ce script Windows PowerShell dans le bloc-notes :
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Enregistrez le script ci-dessus sous CollectionScript.ps1 dans un emplacement facile à trouver, par exemple C:\\AFCScripts.
    
3. Use the Go To feature in Notepad. Make the following changes, as needed:
    
|**Ligne #**|**Ce que vous devez modifier**|**Obligatoire/facultatif**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. <br/> |Facultatif  <br/> |
|76 et 77  <br/> |Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. <br/> |Facultatif  <br/> |
|80  <br/> |La variable **$CaseRootLocation** doit être configurée pour votre partage des fichiers de collecte de serveurs intermédiaires. Par exemple **\\\\Staging\\Cases$** <br/> |Obligatoire  <br/> |
   
4. Placez le fichier CollectionScript.ps1 dans le partage des fichiers d’accès réseau sur un contrôleur de domaine. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Configuration de l’objet de stratégie de groupe pour le script d’ouverture de session et le groupe de dépositaires

1. Configurez un script d'ouverture de session pour le groupe de dépositaires en suivant les instructions de la section concernant la manière d'affecter des scripts d'ouverture de session utilisateur dans la rubrique relative à l'[utilisation des scripts de démarrage, d'arrêt, d'ouverture et de fermeture de session dans la stratégie de groupe](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Supprimez les utilisateurs authentifiés de **Filtrage de sécurité** et ajoutez le groupe des dépositaires.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>Importation du PST de l'option A, script pour Exchange Server 2013

1.  Copiez et collez le script Windows PowerShell suivant dans le bloc-notes :
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.
    
3. Utilisez la fonctionnalité Accédez à dans le bloc-notes et apportez les modifications suivantes, selon vos besoins :
    
|**Ligne #**|**Ce que vous devez modifier**|**Obligatoire/facultatif**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. <br/> |Facultatif  <br/> |
|17   <br/> |**$ConnectionUri** doit être configuré pour votre propre serveur. <br/> > [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.          |Requis  <br/> |
   
4. Vérifiez que le compte Sous-système approuvé Exchange dispose des autorisations de lecture, écriture et exécution sur le partage \\\\Staging\\Cases$.
    
5. Le script d’importation PST nécessite les deux paramètres d’entrée suivants :
    
  - **$SourcePath** L'emplacement des fichiers PST à importer, par exemple \\\\Staging\\Cases$.
    
  - **$MailboxAlias** L'alias de la boîte aux lettres cible qui recevra les éléments de messagerie importés.
    
6. Par exemple, si vous voulez importer tous les fichiers PST depuis le chemin \\\\Staging\Cases$ vers une boîte aux lettres avec l'alias eDiscoveryMailbox, vous devrez exécuter le script comme suit`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Importation des fichiers PST de l'option B, pour Exchange Online

-  Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Stockage froid

1. Créez un partage de fichiers sur la Ordinateur virtuel Azure où tous les fichiers collectés seront placés, par exemple \\\\AZFile1\\ContentColdStorage.
    
2. Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Si vous envisagez l'importation de fichiers PST à partir de \\\\AZFile1\\ContentColdStorage, accordez les autorisations de lecture, écriture et exécution du sous-système approuvé Exchange au partage.
    
### <a name="orchestrator"></a>Orchestrator

1. Téléchargez le [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) à partir du Centre de téléchargement Microsoft.
    
2. Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.
    
3. Dans la boîte **Emplacement du fichier**, saisissez le chemin d'accès et le nom du runbook que vous souhaitez importer ou cliquez sur les points de suspension ( **...**) pour rechercher le fichier à importer. 
    
4. Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.
    
5. Cliquez sur **Terminer**.
    
6. Modifiez le runbook **MoveFilesToColdStorage** comme suit :
    
1. **Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.
    
2. Activité **Supprimer le dossier**: définissez le **chemin d'accès** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\*, et sélectionnez **Supprimer tous les fichiers et sous-dossiers**. 
    
7. Déployer le runbook **MoveToColdStorage** en utilisant les procédures décrites dans l'article sur le[déploiement de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Recherche du stockage froid pour une instance SharePoint sur site

1. Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Utilisation de la solution

There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:
  
1. Gestion de l’appartenance des utilisateurs dans le groupe des dépositaires.
    
2. Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them
    
3. Gestion du processus d’importation PST.
    
4. Déplacement des fichiers de collecte vers l’emplacement de stockage froid.
    
Toutes les autres étapes ne sont pas propres à cette solution. Il s’agit de tâches d’administration standard que vous effectuez dans SharePoint 2013, Microsoft 365 et Azure. Il existe des aspects pour lesquels cette solution ne propose aucune recommandation et pour lesquels vous devrez utiliser votre meilleur jugement selon les besoins de votre société, tels que :
  
1. Suivi de vos cas eDiscovery et de la répartition des dépositaires en fonction des cas.
    
2. Contrôle de la répartition des ensembles de collecte de fichiers en fonction des cas eDiscovery.
    
3. Coordination du calendrier d’importation et des étapes de déplacement vers l’emplacement de stockage froid.
    
4. Gestion de l'espace de fichier utilisé dans Azure.
    
5. Gestion des boîtes aux lettres vers lesquelles les fichiers PST sont importés.
    
6. Sauvegarde et restauration de toutes les données locales.
    
### <a name="custodian-management"></a>Gestion de dépositaire

- To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Surveillance des fichiers collectés et examen des fichiers journaux

1. Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .
    
2. When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:
    
  - One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.
    
    > [!NOTE]
    > The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer. 
  
  - One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Importation des fichiers PST de l'option A pour Exchange Server 2013

1. Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.
    
3. Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Recherchez les erreurs dans la sortie.
    
5. Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Importation des fichiers PST de l'option B, pour Exchange Online

- Pour placer les fichiers PST collectés dans Exchange Online, suivez les procédures décrites dans la section importer des fichiers dans Microsoft 365 via le [chargement réseau](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).
    
### <a name="move-to-cold-storage"></a>Déplacement vers l’emplacement de stockage froid

1. Exécutez l’runbook **runbook movetocoldstorage** à l’aide des procédures décrites dans [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.
    
### <a name="ediscovery"></a>eDiscovery

1. Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Créez un cas eDiscovery dans SharePoint 2013 si vous avez utilisé l'option A pour l'importation d'un fichier PST ou créez un cas eDiscovery dans SharePoint Online si vous avez utilisé l'option B.
    

