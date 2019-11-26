---
title: Désactiver l’accès aux services lors de l’attribution des licences utilisateur
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/27/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Découvrez comment attribuer des licences à des comptes d’utilisateur et à désactiver des plans de service spécifiques en même temps à l’aide d’Office 365 PowerShell.
ms.openlocfilehash: 06b6de4ea6d96dd2c9510770042bd2a2f1260876
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257393"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Désactiver l’accès aux services lors de l’attribution des licences utilisateur

Les abonnements Office 365 sont fournis avec des plans de service pour des services individuels. Les administrateurs d'Office 365 ont souvent besoin de désactiver certains plans lors de l'attribution des licences aux utilisateurs. Avec les instructions fournies dans cet article, vous pouvez attribuer une licence Office 365 tout en désactivant des plans de service spécifiques à l'aide de PowerShell pour un ou plusieurs comptes d'utilisateur.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).

Ensuite, compilez une liste de services à activer. Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Pour le bloc de commande ci-dessous, renseignez le nom d’utilisateur principal du compte d’utilisateur, le numéro de référence SKU et la liste des plans de service pour activer et supprimer \< le texte explicatif, ainsi que les caractères et >. Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, exécutez la commande suivante pour afficher vos abonnements en cours :
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core ne prend pas en charge les applets de commande et le module Microsoft Azure Active Directory pour Windows PowerShell avec **MSOL** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Dans l'affichage de la commande  `Get-MsolAccountSku` :
  
- **AccountSkuId** est un abonnement pour votre organisation au format \<OrganizationName>:\<Subscription>. La valeur \<OrganizationName> est fournie lorsque vous vous inscrivez à Office 365 et elle est propre à votre organisation. La valeur \<Subscription> désigne un abonnement spécifique. Par exemple, pour litwareinc:ENTERPRISEPACK, le nom de l’organisation est litwareinc, et le nom de l’abonnement est ENTERPRISEPACK (Office 365 Entreprise E3).
    
- **ActiveUnits** représente le nombre de licences que vous avez achetées pour l'abonnement.
    
- **WarningUnits** représente le nombre de licences dans un abonnement que vous n'avez pas renouvelées et qui expireront après la période de grâce de 30 jours.
    
- **ConsumedUnits** représente le nombre de licences que vous avez affectées à des utilisateurs de l'abonnement.
    
Notez la valeur AccountSkuId pour votre abonnement Office 365 contenant les utilisateurs pour lesquels vous souhaitez obtenir une licence. En outre, assurez-vous qu'il y a suffisamment de licences à attribuer (soustraire **ConsumedUnits** de **ActiveUnits** ).
  
Ensuite, exécutez cette commande pour afficher les détails sur les plans de service Office 365 qui sont disponibles dans tous vos abonnements :
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

À partir de l’affichage de cette commande, déterminez les plans de service que vous souhaitez désactiver lorsque vous attribuez des licences aux utilisateurs.
  
Voici une liste partielle des plans de service et de leurs services Office 365 correspondants.

Le tableau suivant présente les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants. La liste de vos plans de services peut être différente. 
  
|**Plan de services**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (plan 2)  <br/> |
   
Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).
   
Maintenant que vous avez le paramètre AccountSkuId et les plans de service à désactiver, vous pouvez attribuer des licences pour un utilisateur ou plusieurs utilisateurs.
  
### <a name="for-a-single-user"></a>Pour un utilisateur unique

Pour un utilisateur unique, renseignez le nom d'utilisateur principal du compte d'utilisateur, le paramètre AccountSkuId et la liste des plans de service à désactiver, et supprimez le texte explicatif et les caractères \< et >. Ensuite, exécutez les commandes qui en résultent à l'invite de commande PowerShell.
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Voici un exemple de bloc de commande pour le compte nommé belindan@contoso.com, pour la licence contoso:ENTERPRISEPACK, et les plans de service à désactiver sont RMS_S_ENTERPRISE, SWAY, INTUNE_O365 et YAMMER_ENTERPRISE :
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a>Pour plusieurs utilisateurs

Pour effectuer cette tâche d'administration pour plusieurs utilisateurs, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs UserPrincipalName et UsageLocation. Voici un exemple :
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Ensuite, remplissez l’emplacement des fichiers CSV d’entrée et de sortie, l’ID de référence du compte et la liste des plans de service à désactiver, puis exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Ce bloc de commande PowerShell :
  
- affiche le nom d’utilisateur principal de chaque utilisateur ;
    
- attribue des licences personnalisées à chaque utilisateur ;
    
- crée un fichier CSV avec tous les utilisateurs qui ont été traités et affiche l’état de leur licence.
    
## <a name="see-also"></a>Voir aussi

[Désactiver l'accès aux services Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)
  
[Désactivation de l'accès à Sway avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)
  
[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)

