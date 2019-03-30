---
title: Automatiser la collecte de fichiers pour eDiscovery
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Résumé : Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.'
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001607"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatiser la collecte de fichiers pour eDiscovery

 **Résumé :** Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.
  
Toutes les sociétés peuvent être confrontées à des poursuites judiciaires ou à d'autres types d'action en justice. Bien que les départements juridiques tentent de réduire l'exposition, la résolution de litiges fait partie de la vie des entreprises. Lorsqu'une entreprise est confrontée à une action légale, il est de son devoir, via le processus de découverte légale, de fournir tout document pertinent requis par le tribunal et la partie adverse. 
  
La découverte électronique est le processus par lequel les entreprises inventorient, recherchent, conservent, filtrent et rendent disponibles les documents pertinents existant sous forme électronique. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, et Exchange Online peuvent contenir de grandes quantités de documents. Selon la version, ces produits peuvent prendre en charge eDiscovery et la conservation inaltérable (Lync via Exchange Server), ce qui facilite le travail d'indexation, d'identification, de conservation et de filtrage du contenu le plus pertinent pour une affaire donnée.
  
Une grande quantité de documents est également stockée sur les ordinateurs locaux des utilisateurs (dépositaires), et non dans un emplacement centralisé. Il est ainsi pratiquement impossible d'effectuer des recherches dans SharePoint 2013. Or, si la recherche y est impossible, vous ne pouvez pas inclure l'instance dans eDiscovery. Cette solution vous montre comment utiliser les scripts d'ouverture de session, System Center Orchestrator 2012 R2 et Windows PowerShell pour que Exchange Server automatise l'identification et la collecte des documents à partir des ordinateurs des utilisateurs.
  
## <a name="what-this-solution-does"></a>Descriptif de cette solution

Cette solution utilise un groupe de sécurité global, une stratégie de groupe et un script Windows PowerShell pour localiser, inventorier et recueillir du contenu et les fichiers du magasin personnel (PST) Outlook à partir d'ordinateurs locaux des utilisateurs vers un partage de fichiers caché. À partir de là, les fichiers PST peuvent être importés dans Exchange Server 2013 ou Exchange Online. Tous les fichiers sont ensuite déplacés à l'aide d'un runbook System Center Orchestrator 2012 R2 vers un autre partage de fichier dans Microsoft Azure pour un stockage à long terme et d'une indexation par SharePoint 2013. Vous utilisez ensuite les centres eDiscovery dans votre déploiement SharePoint 2013 sur site ou dans SharePoint Online comme vous le feriez régulièrement pour effectuer une eDiscovery. 
  
> [!IMPORTANT]
> Cette solution utilise robocopy pour copier des fichiers à partir d'ordinateurs de dépositaires vers un partage de fichiers centralisé. Étant donné que robocopy ne copie pas les fichiers qui sont ouverts ou verrouillés, tous les fichiers, y compris les fichiers PST, ouverts par le dépositaire ne seront pas collectés. Vous devrez les collecter manuellement. Cette solution vous fournit une liste qui identifie de manière explicite les fichiers impossibles à copier et le chemin d'accès complet à chaque fichier. 
  
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
|![légende magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Option B) À l'aide de l'outil et du processus d'importation de Office 365, importez les fichiers PST collectés dans Exchange Online.  <br/> |
|![légende magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Déplacez tous les fichiers collectés vers un partage de fichiers Azure pour un stockage à long terme avec le runbook MoveToColdStorageSystem Center Orchestrator 2012 R2. <br/> |
|![légende magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexez les fichiers dans le partage des fichiers de stockage froid avec SharePoint 2013.  <br/> |
|![légende magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Effectuez eDiscovery sur le contenu dans l'espace de stockage froid et le Exchange Server 2013 sur site.  <br/> |
|![légende magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Effectuez eDiscovery sur le contenu dans Office 365.  <br/> |
   
## <a name="prerequisites"></a>Conditions préalables

La configuration de cette solution nécessite plusieurs éléments, dont la plupart sont probablement en place et configurés si vous envisagez eDiscovery. Pour les éléments que vous n'avez pas ou ceux qui requièrent une configuration spécifique, nous allons vous fournir les liens, d'après lesquels vous devez élaborer votre configuration de base. La configuration de base doit être en place avant de configurer la solution elle-même.
  
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
|Office 365 (Plan E3) avec Exchange Online et SharePoint Online (requis pour l'option B)  <br/> |Pour souscrire à un abonnement E3 Office 365, voir la page relative à l'[abonnement Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Abonnement Azure avec un ordinateur virtuel  <br/> |Pour vous inscrire à Azure, voir la page d'[abonnement à Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Une connexion VPN entre votre réseau local et votre abonnement Azure  <br/> |Pour configurer un tunnel VPN entre votre abonnement Azure et votre réseau local, voir [Connecter un réseau local à Microsoft Azure Virtual Network](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery configuré pour effectuer une recherche dans SharePoint et Exchange Server 2013, et éventuellement Lync Server 2013  <br/> |Pour configurer la eDiscovery de cette façon, voir [Configurer eDiscovery dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) et[Guide de laboratoire de test : configurez eDiscovery pour un laboratoire de test de partages de fichiers Exchange, Lync, SharePoint et Windows ](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery dans Office 365 pour SharePoint Online et Exchange Online  <br/> |Pour configurer la eDiscovery dans Office 365, voir [Configurer un centre eDiscovery dans SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628)  <br/> |
   
## <a name="configure-the-environment"></a>Configurer l’environnement

Maintenant que la configuration de base est en place, vous pouvez passer à la configuration de la solution elle-même. 
  
### <a name="staging-file-share"></a>Partage de fichiers intermédiaires

1. Dans le domaine local, créez un groupe de sécurité global nommé Custodians.
    
2. Créez un partage de fichiers cachés pour les fichiers qui sont collectés à partir d'ordinateurs de dépositaires. Il doit s'agir d'un serveur local. Par exemple, sur un serveur appelé Staging, créez un partage de fichiers appelé Cases$. Le **$** est requis pour en faire un partage caché.
    
3. Définissez les autorisations de partage suivantes :
    
  - Dépositaires : Modifier, Lire
    
  - Administrateurs : Contrôle total
    
  - Sous-système approuvé Exchange : Modifier, Lire
    
4. Ouvrez l'onglet **Sécurité**, ajoutez le groupe des dépositaires, puis cliquez sur **Avancé**. Définissez les autorisations suivantes pour le groupe des dépositaires :
    
  - **Type : Refuser**
    
  - **S'applique à : Ce dossier, les sous-dossiers et les fichiers**
    
5. Cliquez sur **Autorisations avancées** et sélectionnez ce qui suit :
    
  - **Lecture des attributs**
    
  - **Lecture des attributs étendus**
    
  - **Autorisations de lecture**
    
6. Testez l’accès au partage de fichiers Cases$ en effectuant les étapes suivantes :
    
1. Ajoutez un utilisateur au groupe des dépositaires.
    
2. Placez un fichier dans le dossier Cases$.
    
3. En tant qu'utilisateur, accédez au serveur intermédiaire, par exemple accédez au partage \\\\Staging pour voir quels partages sont disponibles. Vous ne devriez pas voir le partage **Cases$** répertorié.
    
4. Saisissez manuellement le chemin d’accès complet au partage Cases$ dans Explorer. Cela devrait ouvrir le partage Cases$.
    
5. Essayez d’ouvrir le fichier que vous avez placé dans le partage. Vous ne devriez pas y parvenir
    
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
    
3. Utilisez la fonctionnalité Accédez à dans le bloc-notes. Apportez les modifications suivantes, selon vos besoins :
    
|**Ligne #**|**Ce que vous devez modifier**|**Obligatoire/facultatif**|
|:-----|:-----|:-----|
|71  <br/> |Variable **$FileTypes**. Inclure toutes les extensions de type de fichier que vous souhaitez que le script inventorie et collecte dans la variable du tableau<br/> |Facultatif  <br/> |
|76 et 77  <br/> |Modifier la conception de la variable **$CaseNo** en fonction de vos besoins. Le script capture la date et heure actuelles et y ajoute le nom d'utilisateur.<br/> |Facultatif  <br/> |
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. Enregistrez le script en tant que PSTImportScript.ps1 dans un emplacement facile à trouver. Par exemple et pour une grande facilité d'utilisation, créez un dossier sur votre serveur intermédiaire appelé \\\\Staging\\AFCScripts et enregistrez le script ici.
    
3. Utilisez la fonctionnalité Accédez à dans le bloc-notes et apportez les modifications suivantes, selon vos besoins :
    
|**Ligne #**|**Ce que vous devez modifier**|**Obligatoire/facultatif**|
|:-----|:-----|:-----|
|an  <br/> |**$FolderIdentifier** marque les dossiers de boîte aux lettres vers lesquels les fichiers PST sont importés. Modifier si nécessaire.<br/> |Facultatif  <br/> |
|cm  <br/> |**$ConnectionUri** doit être configuré pour votre propre serveur. <br/> > [!IMPORTANT]> Vérifiez que votre **$ConnectionUri** pointe vers un emplacement http://, et non pas https://. Cela ne fonctionnera pas avec https://          |Requis  <br/> |
   
4. Vérifiez que le compte Sous-système approuvé Exchange dispose des autorisations de lecture, écriture et exécution sur le partage \\\\Staging\\Cases$.
    
5. Le script d’importation PST nécessite les deux paramètres d’entrée suivants :
    
  - **$SourcePath** L'emplacement des fichiers PST à importer, par exemple \\\\Staging\\Cases$.
    
  - **$MailboxAlias** L'alias de la boîte aux lettres cible qui recevra les éléments de messagerie importés.
    
6. Par exemple, si vous voulez importer tous les fichiers PST depuis le chemin \\\\Staging\Cases$ vers une boîte aux lettres avec l'alias eDiscoveryMailbox, vous devrez exécuter le script comme suit`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Importation des fichiers PST de l'option B, pour Exchange Online

-  Créez la structure de la boîte aux lettres pour y placer les fichiers PST importés. Pour plus d'informations sur la création d'une boîte aux lettres utilisateur dans Exchange Online, voir[Création de boîtes aux lettres utilisateur dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Stockage froid

1. Créez un partage de fichiers sur la Ordinateur virtuel Azure où tous les fichiers collectés seront placés, par exemple \\\\AZFile1\\ContentColdStorage.
    
2. Accordez au moins les autorisations de lecture du partage et de tous les sous-dossiers et fichiers au compte d'accès au contenu par défaut. Pour plus d'informations sur la configuration de la recherche SharePoint 2013, voir [Créer et configurer une application de service de recherche dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940)
    
3. Si vous envisagez l'importation de fichiers PST à partir de \\\\AZFile1\\ContentColdStorage, accordez les autorisations de lecture, écriture et exécution du sous-système approuvé Exchange au partage.
    
### <a name="orchestrator"></a>Orchestrator

1. Téléchargez le [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) à partir du Centre de téléchargement Microsoft.
    
2. Ouvrez le **Runbook Designer**, dans le panneau **Connexions**, cliquez sur le dossier dans lequel vous souhaitez importer le runbook. Cliquez sur le menu **Actions**, puis cliquez sur **Importer**. La boîte de dialogue **Importer** s'affiche.
    
3. Dans la boîte **Emplacement du fichier**, saisissez le chemin d'accès et le nom du runbook que vous souhaitez importer ou cliquez sur les points de suspension ( **...**) pour rechercher le fichier à importer. 
    
4. Sélectionnez **Importer le runbook** et **Importer les données chiffrées d'Orchestrator**. Effacez **Compteurs**, **Planifications**, **Variables**, **Groupes d'ordinateurs**, **Importer les configurations globales**, et **Remplacer les configurations globales existantes**.
    
5. Cliquez sur **Terminer**.
    
6. Modifiez le runbook **MoveFilesToColdStorage** comme suit :
    
1. Activité **Déplacer le fichier**: définissez le chemin d'accès du **fichier source** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$. Définissez le **dossier de destination** sur l'emplacement de partage des fichiers de stockage froid dans Azure, par exemple \\\\AZFile1\\ContentColdStorage. Sélectionnez **Créer un fichier avec un nom unique**.
    
2. Activité **Supprimer le dossier**: définissez le **chemin d'accès** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\*, et sélectionnez **Supprimer tous les fichiers et sous-dossiers**. 
    
7. Déployer le runbook **MoveToColdStorage** en utilisant les procédures décrites dans l'article sur le[déploiement de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Recherche du stockage froid pour une instance SharePoint sur site

1. Créez une nouvelle source de contenu dans votre batterie de serveurs SharePoint 2013 pour le partage du stockage froid dans Azure, par exemple \\\\AZFile1\\ContentColdStorage. Pour plus d'informations sur la gestion des sources de contenu, voir [Ajouter, modifier ou supprimer une source de contenu dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).
    
2. Démarrez une analyse complète. Pour plus d'informations, voir [Démarrer, suspendre, reprendre ou arrêter une analyse dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Utilisation de la solution

Il existe cinq étapes principales concernant l'utilisation de cette solution, en supposant que vous ne souhaitez pas ingérer les fichiers PST dans Exchange Server 2013 et Exchange Online. Cette section vous fournit les procédures pour tous les cas. Votre interaction principale avec la solution aura lieu en effectuant les actions suivantes :
  
1. Gestion de l’appartenance des utilisateurs dans le groupe des dépositaires.
    
2. Erreurs
    
3. Gestion du processus d’importation PST.
    
4. Déplacement des fichiers de collecte vers l’emplacement de stockage froid.
    
Toutes les autres étapes ne sont pas propres à cette solution. Ce sont des tâches administratives standard que vous effectuez dans SharePoint 2013, Office 365 et Azure. Il existe des aspects pour lesquels cette solution ne propose aucune recommandation et pour lesquels vous devrez utiliser votre meilleur jugement selon les besoins de votre société, tels que :
  
1. Suivi de vos cas eDiscovery et de la répartition des dépositaires en fonction des cas.
    
2. Contrôle de la répartition des ensembles de collecte de fichiers en fonction des cas eDiscovery.
    
3. Coordination du calendrier d’importation et des étapes de déplacement vers l’emplacement de stockage froid.
    
4. Gestion de l'espace de fichier utilisé dans Azure.
    
5. Gestion des boîtes aux lettres vers lesquelles les fichiers PST sont importés.
    
6. Sauvegarde et restauration de toutes les données locales.
    
### <a name="custodian-management"></a>Gestion de dépositaire

- Pour démarrer le processus de collecte automatique des fichiers pour un utilisateur individuel, ajoutez-les au groupe des dépositaires. La prochaine fois que l'utilisateur se connecte, le script d'ouverture de session affecté au groupe des dépositaires via la stratégie de groupe s'exécutera. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Surveillance des fichiers collectés et examen des fichiers journaux

1. Observez le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\* pour le dossier de collecte à partir de l'utilisateur. Le nom du dossier sera formaté comme suit :  *aaaaMMjjHHmm_NomUtilisateur*  .
    
2. Lorsque la collecte est terminée, ouvrez le dossier de collecte et accédez au dossier _Log. Les éléments suivants s'affichent dans le dossier _Log :
    
  - Un seul fichier XML pour chaque lecteur local sur l'ordinateur des utilisateurs, par exemple **A.xml**, **C.xml**. Ces fichiers contiennent les lecteurs d'inventaire d'après lesquels ils sont nommés et ils sont utilisés pour l'opération robocopy.
    
    > [!NOTE]
    > Le script de collecte crée uniquement une entrée dans le fichier d'inventaire pour les types de fichiers que vous avez définis dans le script lui-même. Il ne crée pas une entrée d'inventaire pour chaque fichier sur l'ordinateur des utilisateurs. 
  
  - Un seul fichier journal nommé FileCopyErrors.log est exécuté pour chaque collecte. Ce fichier contient une liste des fichiers que robocopy n'a pas pu copier sur le partage de collecte de fichiers, par exemple, \\\\Staging\\cases$\\*. Vous devrez l'examiner et décider des mesures à adopter pour ces fichiers manquants. En règle générale, vous devez les rassembler manuellement si vous souhaitez les conserver ou vous pouvez décider qu'ils ne sont pas nécessaires et qu'ils peuvent donc être omis de la collecte.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Importation des fichiers PST de l'option A pour Exchange Server 2013

1. Ouvrez une session sur le serveur qui héberge le partage des fichiers de collecte, par exemple **Staging** et ouvrez Windows PowerShell. Pour plus d'informations sur le démarrage de Windows PowerShell, voir l'article relatif au[démarrage de Windows PowerShell sous Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Définissez la stratégie d'exécution sur Illimitée. Saisissez  `Set-ExecutionPolicy Unrestricted -Scope Process` dans Windows PowerShell et appuyez sur Entrée.
    
3. Exécutez le fichier PSTImportScript.ps1 et indiquez les paramètres **$SourcePath** et **$MailboxAlias**. Pour plus d'informations sur l'exécution des scripts Windows PowerShell, voir[Prise en charge des scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Recherchez les erreurs dans la sortie.
    
5. Avant d'essayer d'importer un fichier PST portant le même nom dans la même boîte aux lettres, vous devez supprimer la demande d'importation de boîte aux lettres. Pour ce faire, exécutez la commande suivante :  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Vous serez invité à supprimer chaque demande individuelle de la file d'attente. Répondez selon vos besoins.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Importation des fichiers PST de l'option B, pour Exchange Online

- Pour placer les fichiers PST collectés dans Exchange Online, suivez les procédures décrites dans la section concernant l'importation de fichiers vers Office 365 via le chargement réseau dans la rubrique relative au [service d'importation Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Déplacement vers l’emplacement de stockage froid

1. Exécutez le runbook **MoveToColdStorage** à l'aide des procédures décrites dans la rubrique relative à l'[exécution de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Observez le partage de fichiers Azure que vous utilisez pour le stockage à long terme, par exemple \\\\AZFile1\\ContentColdStorage et le partage des fichiers de collecte sur site, par exemple \\\\Staging\\cases$. Vous devriez voir les fichiers et dossiers apparaître dans le partage des fichiers de stockage froid et disparaître du partage des fichiers de collecte.
    
### <a name="ediscovery"></a>eDiscovery

1. Autorisez l'analyse complète du partage des fichiers de stockage froid à s'exécuter en tant que planification ou lancez une analyse. Pour plus d'informations sur le démarrage d'analyses complètes ou incrémentielles, voir [Démarrer, suspendre, reprendre ou arrêter une analyse dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Créez un cas eDiscovery dans SharePoint 2013 si vous avez utilisé l'option A pour l'importation d'un fichier PST ou créez un cas eDiscovery dans SharePoint Online si vous avez utilisé l'option B.
    

