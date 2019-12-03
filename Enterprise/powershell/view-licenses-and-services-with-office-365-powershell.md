---
title: Afficher les licences et les services avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de gestion des licences, les services et les licences disponibles dans votre organisation Office 365.
ms.openlocfilehash: b8a0bb1845f3c0db5aa47cea0c2f6e5e580c804f
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655846"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Afficher les licences et les services avec Office 365 PowerShell

Chaque abonnement Office 365 se compose des éléments suivants :

- **Plans** de gestion des licences Il s’agit également de plans de licence ou de plans Office 365. Les plans de gestion des licences définissent les services Office 365 disponibles pour les utilisateurs. Votre abonnement Office 365 peut contenir plusieurs plans de gestion des licences. Un exemple de plan de gestion des licences serait Office 365 entreprise E3.
    
- **Services** Ces derniers sont également appelés plans de service. Les services sont les produits, les fonctionnalités et les fonctionnalités Office 365 qui sont disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Office professionnel plus. Des licences issues de différents plans de licence peuvent être attribuées à un même utilisateur, lui accordant l’accès à des services différents.
    
- **Licences** Chaque plan de gestion des licences contient le nombre de licences que vous avez achetées. Vous attribuez des licences aux utilisateurs afin qu’ils puissent utiliser les services Office 365 définis par le plan de gestion des licences. Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences afin qu’il puisse se connecter à Office 365 et utiliser les services.
    
Vous pouvez utiliser Office 365 PowerShell pour afficher des détails sur les plans de licence, les licences et les services disponibles dans votre organisation Office 365. Pour plus d’informations sur les produits, les fonctionnalités et les services disponibles dans les différents abonnements Office 365, reportez-vous à la rubrique [office 365 plan options](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Pour afficher des informations récapitulatives sur vos plans de gestion des licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Les résultats contiennent les informations suivantes :
  
- **SkuPartNumber :** Affiche les plans de gestion des licences disponibles pour votre organisation. Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 entreprise E3.
    
- **Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.
    
Pour afficher des détails sur les services Office 365 disponibles dans tous vos plans de licence, commencez par afficher la liste de vos plans de licence.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, stockez les informations des plans de licence dans une variable.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Ensuite, affichez les services dans un plan de licence spécifique.

```powershell
$licenses[<index>].ServicePlans
```

\<index> est un entier qui spécifie le numéro de ligne du plan de licence à partir de `Get-AzureADSubscribedSku | Select SkuPartNumber` l’affichage de la commande, moins 1.

Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande est le suivant :

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

La commande permettant d’afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3-1) ou 2.

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Office 365, y compris Sway. Pour plus d’informations, reportez-vous à la rubrique [désactiver l’accès à Sway avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Pour afficher des informations récapitulatives sur vos plans de gestion des licences actuels et sur les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Les résultats contiennent les informations suivantes :
  
- **AccountSkuId :** Affichez les plans de gestion des licences disponibles pour votre organisation `<CompanyName>:<LicensingPlan>`à l’aide de la syntaxe.  _<CompanyName>_ est la valeur que vous avez fournie lorsque vous vous êtes inscrit dans Office 365 et qui est unique pour votre organisation. La _<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur `litwareinc:ENTERPRISEPACK`, le nom `litwareinc`de la société et le nom `ENTERPRISEPACK`du plan de gestion des licences, qui est le nom du système pour Office 365 entreprise E3.
    
- **ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **WarningUnits :** Nombre de licences dans un plan de gestion des licences que vous n’avez pas renouvelé et qui expireront après la période de grâce de 30 jours.
    
- **ConsumedUnits :** Nombre de licences que vous avez affectées à des utilisateurs à partir d’un plan de gestion de licences spécifique.
    
Pour afficher les détails des services Office 365 disponibles dans tous vos plans de licence, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Le tableau suivant présente les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants. La liste de vos plans de services peut être différente. 
  
|**Plan de services**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (plan 2)  <br/> |
   
Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Pour afficher des détails sur les services Office 365 disponibles dans un plan de gestion de licences spécifique, utilisez la syntaxe suivante.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Cet exemple illustre les services Office 365 disponibles dans le plan de gestion des licences litwareinc : ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
