---
title: RGPD pour SharePoint Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment satisfaire aux exigences du RGPD dans un environnement SharePoint Server local.
ms.openlocfilehash: 81ee339748923af835f88f73f5cf891d01212a17
ms.sourcegitcommit: 53a57b0617b5bb22beea766e515873d14b3a4783
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "19186616"
---
# <a name="gdpr-for-sharepoint-server"></a>RGPD pour SharePoint Server

Dans le cadre de la protection des informations personnelles, nous vous recommandons d’effectuer les tâches suivantes :

-   Classer vos données à l’aide d’Azure Information Protection.

-   Exécuter SharePoint Server dans une configuration avec des privilèges minimaux. Pour plus d’informations, reportez-vous à l’article relatif à la [planification d’une administration avec des privilèges minimaux dans SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) et à l’article [Sécurité pour SharePoint Server](https://docs.microsoft.com/fr-FR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).

-   [Activer le chiffrement BitLocker sur vos serveurs](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).

## <a name="user-generated-content"></a>Contenu généré par l’utilisateur

Voici l’approche à adopter concernant le contenu généré par l’utilisateur dans les bibliothèques et les sites SharePoint Server :

-   Attribuez des étiquettes aux données sensibles à l’aide d’Azure Information Protection.

-   Récupérez les données sensibles à l’aide des fonctions de [recherche SharePoint Server](https://docs.microsoft.com/SharePoint/search/search) et [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server).

Voici la procédure recommandée à suivre concernant les partages de fichiers, ainsi que les bibliothèques et les sites SharePoint :

1.  **Installez et configurez le scanneur Azure Information Protection.**

    -   Déterminez les types de données sensibles à utiliser.

    -   Spécifiez les sites SharePoint à utiliser.

2.  **Effectuez un cycle de détection.**

    -   Exécutez le scanneur en mode de détection et validez les résultats.

    -   Si nécessaire, optimisez les conditions et les types d’informations sensibles.

    -   Évaluez l’incidence que peut avoir l’application automatique d’étiquettes.

3.  **Exécutez le scanneur Azure Information Protection pour appliquer des étiquettes aux documents correspondants**.

4.  **Pour une meilleure protection :**

    a. configurez des règles de protection contre la perte de données Exchange pour protéger les documents avec l’étiquette souhaitée.

    b. veillez à déterminer des autorisations pour limiter les personnes pouvant accéder aux fichiers.

    c. pour SharePoint, utilisez la protection IRM pour les bibliothèques.

5.  **Pour la surveillance, intégrez un outil SIEM aux journaux Windows Server.**

    a. Pour rechercher des données personnelles pour les demandes d’objet de données, utilisez le Centre de recherche ou eDiscovery.

Lorsque vous appliquez des étiquettes à des données sensibles, veillez à utiliser des étiquettes qui ne sont pas configurées avec un système de protection. La protection inclut le chiffrement, qui empêche les services de détecter les données sensibles dans les fichiers.

Pour plus d’informations sur l’utilisation du scanneur Azure Information Protection pour la recherche et l’étiquetage des données personnelles, reportez-vous au [Kit de détection de données du RGPD Microsoft à l’adresse](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners)).

Pour plus d’informations sur la configuration du scanneur pour diverses conditions et sur l’utilisation des types d’informations sensibles Office 365 dans le cadre de la protection contre la perte de données, reportez-vous à l’article [Comment configurer des conditions pour la classification automatique et recommandée pour Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Notez que les nouveaux types d’informations sensibles Office 365 ne pourront pas immédiatement être utilisés avec le scanneur et que les types d’informations sensibles personnalisés ne peuvent pas être utilisés avec le scanneur.

## <a name="removing-personal-information-from-office-files"></a>Suppression d’informations personnelles à partir de fichiers Office

La suppression d’informations personnelles (par exemple, des métadonnées ou des commentaires dans un document Word) à partir de fichiers Office stockés dans une bibliothèque de documents SharePoint doit être effectuée manuellement. Procédez comme suit :

1.  Téléchargez une copie du document à partir de SharePoint Server sur votre disque local.

2.  Supprimez le document de la bibliothèque de documents SharePoint.

3.  Suivez la procédure indiquée dans l’article [Supprimer des données masquées et des informations personnelles en inspectant des documents](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).

4.  Téléchargez de nouveau le document vers la bibliothèque de documents SharePoint.

## <a name="telemetry-and-log-files"></a>Télémétrie et fichiers journaux

### <a name="uls-logs"></a>Journaux ULS

Les journaux du service ULS (Unified Logging Service) et les journaux d’utilisation dans SharePoint Server permettent d’effectuer le suivi de différentes fonctions système et peuvent contenir des informations sur l’utilisateur. Les journaux ULS et les journaux d’utilisation sont des fichiers texte et peuvent être recherchés à l’aide d’un large éventail d’outils. La [cmdlet PowerShell Merge-SPLogFile](https://docs.microsoft.com/fr-FR/powershell/module/sharepoint-server/merge-splogfile) fournit un moyen de renvoyer des enregistrements à partir des journaux ULS sur plusieurs serveurs dans une batterie de serveurs.

Pensez à définir les stratégies de rétention des journaux sur la valeur minimale nécessaire selon vos besoins. Pour plus d’informations sur la configuration de la journalisation dans SharePoint Server, reportez-vous à l’article [Configurer la journalisation des diagnostics dans SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).

Notez que certains événements système sont également enregistrés pour le journal des événements Windows.

### <a name="usage-database"></a>Base de données d’utilisation

La base de données d’utilisation de SharePoint Server (nom par défaut : WSS_Logging) contient un sous-ensemble des informations figurant dans les journaux ULS. La durée maximale de rétention des données dans cette base de données est de 30 jours. Nous vous recommandons de la configurer sur la durée la plus courte possible en fonction de vos besoins. Pour plus d’informations, reportez-vous à l’article [Configurer la journalisation des diagnostics dans SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).

## <a name="personal-information-and-search"></a>Informations personnelles et recherche

Les enregistrements d’utilisation et l’historique des requêtes de recherche contiennent des références à des noms d’utilisateur.

### <a name="query-history-and-favorite-queries"></a>Historique de requêtes et requêtes favorites

Dans SharePoint Server 2013 et SharePoint Server 2016, les historiques de requête et les requêtes marquées comme favorites expirent automatiquement au bout de 365 jours. Si un utilisateur quitte votre organisation, vous pouvez supprimer les références à son nom d’utilisateur à partir de l’historique de requêtes en suivant la procédure ci-dessous.

Les requêtes SQL suivantes s’appliquent à SharePoint 2013 et à SharePoint 2016, et permettent d’effectuer les actions suivantes :

-   Exporter l’historique de requêtes et les requêtes favorites d’un utilisateur

-   Supprimer les références à des noms d’utilisateur dans l’historique de requêtes

#### <a name="export-a-users-queries-since-a-specific-date"></a>Exporter les requêtes d’un utilisateur depuis une date spécifique 

La procédure suivante permet d’exporter des requêtes à partir des tables de journaux de requêtes Link Store effectuées par @UserName depuis @StartTime.

```sql
[In dbo].[LinkStore_<ID>]:
CREATE PROCEDURE proc_MSS_GetQueryTermsForUser 
( 
    @UserName nvarchar(256), 
    @StartTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT searchTime, queryString 
    FROM 
        dbo.MSSQLogPageImpressionQuery 
    WITH 
        (NOLOCK) 
    WHERE 
        userName = @UserName AND 
        searchTime > @StartTime 
END 
GO 
```

#### <a name="export-a-users-queries-from-the-past-100-days"></a>Exporter les requêtes d’un utilisateur émises au cours des 100 derniers jours

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a>Exporter les requêtes favorites d’un utilisateur

Suivez la procédure ci-dessous pour exporter les requêtes favorites d’un utilisateur à partir des tables de résultats personnels de la base de données d’administration de recherche, effectuées par @UserName, depuis <DateTime>.

```sql
In [dbo].[Search_<ID>]:
CREATE PROCEDURE proc_MSS_GetPersonalFavoriteQueries 
( 
    @UserName nvarchar(256), 
    @SearchTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT max(queries.SearchTime) as SearchTime, 
           max(queries.querystring) as queryString, 
           max(url.url) as URL 
    FROM MSSQLogOwner owners WITH(NOLOCK) 
    JOIN MSSQLogPersonalResults results WITH(NOLOCK) on owners.OwnerId = results.OwnerId 
    JOIN MSSQLogUrl url WITH(NOLOCK) on results.ClickedUrlId = url.urlId 
    JOIN MSSQLogPersonalQueries queries WITH(NOLOCK) on results.OwnerId = queries.OwnerId 
    WHERE queries.SearchTime > @SearchTime 
        AND queries.UserName = @UserName 
        GROUP BY queries.QueryString,url.url 
END 
GO 
```

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a>Exporter les requêtes favorites d’un utilisateur émises au cours des 100 derniers jours 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a>Supprimer les références aux noms d’utilisateur qui datent de plus de X jours

Procédez comme indiqué ci-dessous pour supprimer les références à *tous* les noms d’utilisateur qui datent de plus de @Days à partir des tables de journaux de requêtes Link Store. La procédure supprime uniquement les références antérieures jusqu’à l’heure du dernier nettoyage @LastCleanupTime.

```sql
In [dbo].[LinksStore_<ID>]:  
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a>Supprimer les références à un nom d’utilisateur spécifique qui date de plus de X jours

Procédez comme indiqué ci-dessous pour supprimer les références à un nom d’utilisateur *spécifique* des tables de journaux de requêtes Link Store, où les références datent de plus de @Days. La procédure supprime uniquement les références antérieures jusqu’à l’heure du dernier nettoyage @LastCleanupTime.

```sql
In [dbo].[LinksStore_<ID>]:
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @UserName nvarchar(256),
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a>Supprimer les références à tous les noms d’utilisateur dans l’historique de requêtes entre une date spécifique et jusqu’aux 30 derniers jours

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a>Supprimer les enregistrements d’utilisation

SharePoint Server 2013 et SharePoint Server 2016 suppriment automatiquement les enregistrements d’utilisation au bout de 3 ans. Vous pouvez supprimer manuellement ces enregistrements à l’aide de la procédure ci-dessous :

Pour supprimer tous les enregistrements d’utilisation associés à des documents supprimés, procédez comme suit : 

1.  Assurez-vous que la dernière mise à jour de SharePoint est installée. 

2.  Démarrez SharePoint Management Shell.

3.  Arrêtez et effacez l’analyse de l’utilisation : 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  Attendez que l’analyse recommence (cela peut prendre jusqu’à 24 heures). 

5.  Lors de la prochaine exécution de l’analyse, tous les enregistrements seront vidés de la base de données de création de rapports d’analyse. Ce vidage complet peut prendre du temps pour une base de données volumineuse avec de nombreuses entrées.

6.  Attendez 10 jours. L’analyse s’exécute tous les jours. Les enregistrements associés à des documents supprimés sont supprimés au bout de la dixième exécution. Cette dernière peut prendre plus de temps que les autres, si les enregistrements à supprimer sont nombreux. 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a>Informations personnelles et recherche dans SharePoint Server 2010

#### <a name="fast-search-server-2010-for-sharepoint"></a>FAST Search Server 2010 for SharePoint 

En plus de stocker des fichiers dans l’index, le module complémentaire FAST Search Server 2010 stocke également les fichiers au format intermédiaire FixML. Les fichiers FiXML sont régulièrement compactés, par défaut entre 3 h 00 et 5 h 00 toutes les nuits. Le compactage élimine automatiquement les fichiers supprimés des fichiers FiXML. Pour que les informations appartenant à des utilisateurs ou des documents supprimés soient supprimées au bon moment, veillez à ce que le compactage soit toujours activé.

### <a name="hybrid-search"></a>Recherche hybride 

Les actions recommandées pour les solutions de recherche hybride sont les mêmes que pour la recherche dans SharePoint Server ou SharePoint Online. Il existe deux solutions de recherche hybride :

**Solution de recherche hybride dans le cloud :** avec la solution cloud de recherche hybride pour SharePoint, vous indexez l’ensemble de votre contenu analysé, y compris le contenu local, dans votre index de recherche dans Office 365. Lorsque les utilisateurs exécutent une requête dans votre index de recherche Office 365, ils reçoivent les résultats de recherche du contenu local et du contenu Office 365. Lorsque des documents sont supprimés de l’environnement SharePoint Server, ils sont également supprimés de l’index de recherche dans Office 365. [Découvrez la solution de recherche hybride sur le cloud](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) et [comment les bases de données et composants de recherche interagissent dans la fonction de recherche hybride dans le cloud](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) pour mieux comprendre l’incidence du RGPD sur l’environnement hybride.

**Solution de recherche fédérée hybride :** grâce à la solution de recherche fédérée hybride, vous utilisez votre index à la fois dans SharePoint Server et dans Office 365. Les services de recherche de SharePoint Server et de SharePoint Online peuvent exécuter une requête dans l’index de recherche dans l’autre environnement et renvoyer des résultats fédérés. Lorsque les utilisateurs effectuent une recherche à partir d’un centre de recherche, les résultats sont extraits de votre index de recherche dans SharePoint Server et dans Office 365. [Découvrez la solution de recherche fédérée hybride](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) pour mieux comprendre l’incident du RGPD sur l’environnement hybride.

## <a name="on-prem-to-cloud-migrations"></a>Migrations depuis votre ordinateur local vers le cloud

Lors de la migration des données de SharePoint Server vers SharePoint Online, il se peut que des données existent en double aux deux emplacements pendant un certain temps. Si certaines données doivent être supprimées en cours de la migration, nous vous recommandons d’effectuer dans un premier temps la migration, puis de supprimer les données aux deux emplacements. Vous pouvez exécuter une requête de données pour exportation à partir d’un emplacement ou de l’autre.

## <a name="user-profile-data"></a>Données des profils utilisateur

Le service de profil utilisateur permet d’importer des données de profil provenant de diverses sources externes. Les requêtes et les mises à jour liées à ces données de profil utilisateur doivent être gérées dans les systèmes dans lesquels les données sont administrées. Si vous effectuez des mises à jour sur le système externe, veillez à synchroniser à nouveau les profils utilisateur dans SharePoint Server.

Suivez la procédure de base pour supprimer les informations personnelles d’un utilisateur de son profil utilisateur SharePoint Server :

1.  Supprimez les informations utilisateur sur tout système externe alimentant le profil utilisateur SharePoint Server. Si vous utilisez la synchronisation d’annuaires, l’utilisateur doit être supprimé de l’environnement Active Directory local.

2.  Exécutez une [synchronisation des profils](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) sur SharePoint Server.

3.  Supprimez le profil de SharePoint Server. Une fois cette opération terminée, SharePoint Server supprime entièrement le profil de la base de données de profil utilisateur dans les 30 jours. Le site personnel et la page de profil de l’utilisateur sont supprimés.

Après la suppression d’un profil utilisateur, certaines informations limitées (par exemple, l’ID utilisateur) peuvent toujours être enregistrées dans les collections de sites que l’utilisateur a consultées. Si vous choisissez de supprimer ces données dans une collection de sites donnée, cette opération peut être effectuée à l’aide du modèle CSOM. Vous trouverez un exemple de script ci-dessous :

```powershell
$username = "<admin@company.sharepoint.com>"
$password = "password"
$url = "<https://site.sharepoint.com>"
$securePassword = ConvertTo-SecureString $Password -AsPlainText -Force

# the path here may need to change if you used e.g. C:Lib.
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.dll"
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.Runtime.dll"

# connect/authenticate to SharePoint Online and get ClientContext object.
$clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($username, $securePassword)
$clientContext.Credentials = $credentials
if (!$clientContext.ServerObjectIsNull.Value)
{
    Write-Host "Connected to SharePoint Online site: '$Url'" -ForegroundColor Green
}

# Get user
$user = $clientContext.Web.SiteUsers.GetByLoginName("i:0#.f|membership|user@company.sharepoint.com")

# Redact user
$user.Email = "Redacted"
$user.Title = "Redacted"
$user.Update()
$clientContext.Load($user)
$clientContext.ExecuteQuery()

# Get users
$users = $clientContext.Web.SiteUsers

# Remove user from site
$users.RemoveById($user.Id)
$clientContext.Load($users)
$clientContext.ExecuteQuery()
```