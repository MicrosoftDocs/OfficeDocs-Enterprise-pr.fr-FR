---
title: Afficher les licences et les services avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
description: Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licences, les services et les licences sont disponibles dans votre organisation Office 365.
ms.openlocfilehash: e4c4a0570cafd3d9cb775dd99c5f75da613715e3
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546535"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Afficher les licences et les services avec Office 365 PowerShell

**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des informations sur les plans de licences, les services et les licences sont disponibles dans votre organisation Office 365.
  
Chaque abonnement à Office 365 se compose des éléments suivants :

- **Plans de gestion des licences** Ce sont également appelés plans de licence ou plans Office 365. Plans de licence définissent les services Office 365 qui sont accessibles aux utilisateurs. Votre abonnement Office 365 peut contenir plusieurs plans de gestion des licences. Un plan de gestion des licences exemple serait Office 365 entreprise E3.
    
- **Services** Ils sont également appelés plans de service. Les services sont les produits Office 365, les fonctionnalités et les capacités qui sont disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Office Professionnel Plus. Les utilisateurs peuvent avoir plusieurs licences assignés à partir de différents plans de licence permettant d’accéder à différents services.
    
- **Licences** Chaque plan de licences contient le nombre de licences que vous avez acheté. Vous attribuez des licences aux utilisateurs afin qu’ils peuvent utiliser les services Office 365 qui sont définies par le plan de gestion des licences. Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences pour pouvoir se connecter à Office 365 et utiliser les services.
    
Vous pouvez utiliser Office 365 PowerShell pour afficher plus d’informations sur les plans de licence disponibles, les licences et les services dans votre organisation Office 365. Pour plus d’informations sur les produits, les fonctionnalités et les services qui sont disponibles dans les différents abonnements Office 365, voir [Options de Plan Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez Azure Active Directory PowerShell pour le module de graphique

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Pour afficher des informations récapitulatives concernant vos plans de gestion des licences en cours et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Les résultats contiennent les informations suivantes :
  
- **SkuPartNumber :** Afficher les plans de gestion de licences disponibles pour votre organisation > par exemple, `ENTERPRISEPACK` est le nom du système pour Office 365 entreprise E3.
    
- **Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **ConsumedUnits :** Nombre de licences que vous avez affectés aux utilisateurs d’un plan de gestion des licences spécifique.
    
Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans l’ensemble de vos modes de licence, d’abord afficher une liste de vos plans de licence.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Ensuite, stockez les informations de licence des plans dans une variable.

````
$licenses = Get-AzureADSubscribedSku
````

Ensuite, afficher les services dans un plan de licences spécifiques.

````
$licenses[<index>].ServicePlan
````

\<Index > est un entier qui spécifie le numéro de ligne de la licence de planification de l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` command, moins 1.

Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande s’agit-il :

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Puis la commande pour afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :

````
$licenses[2].ServicePlan
````

ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3 - 1) ou 2.

Pour une liste complète des plans de licence (également connu sous les noms de produits), leurs plans de service inclus et leurs noms conviviaux correspondants, voir [identificateurs de plan de service de gestion des licences et les noms de produits](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell

Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Vous trouverez un script PowerShell qui automatise les procédures décrites dans cette rubrique. Plus précisément, le script permet d’afficher et désactiver des services dans votre organisation Office 365, notamment balancement. Pour plus d’informations, voir [désactiver l’accès à balancement avec Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Pour afficher des informations récapitulatives concernant vos plans de gestion des licences en cours et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```
Get-MsolAccountSku
```

Les résultats contiennent les informations suivantes :
  
- **Éléments AccountSkuId :** Afficher les plans de gestion de licences disponibles pour votre organisation à l’aide de la syntaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ est la valeur que vous avez fournies lorsque vous inscrit dans Office 365 et êtes unique pour votre organisation. Le _<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur `litwareinc:ENTERPRISEPACK`, est le nom de la société `litwareinc`et le nom de plan de gestion des licences `ENTERPRISEPACK`, qui est le nom du système pour Office 365 entreprise E3.
    
- **ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **WarningUnits :** Nombre de licences d’un plan de gestion des licences que vous n’avez pas renouvelé, qui va expirer après la période de grâce de 30 jours.
    
- **ConsumedUnits :** Nombre de licences que vous avez affectés aux utilisateurs d’un plan de gestion des licences spécifique.
    
Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans l’ensemble de vos modes de licence, exécutez la commande suivante :
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Le tableau suivant indique les plans de service Office 365 et leurs noms conviviaux pour les services les plus courants. Votre liste des plans de service peut être différent. 
  
|**Plan de service**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professionnel Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Pour une liste complète des plans de licence (également connu sous les noms de produits), leurs plans de service inclus et leurs noms conviviaux correspondants, voir [identificateurs de plan de service de gestion des licences et les noms de produits](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Pour afficher plus d’informations sur les services Office 365 qui sont disponibles dans un plan de gestion des licences spécifique, utilisez la syntaxe suivante.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Cet exemple montre les services Office 365 qui sont disponibles dans le plan de gestion des licences litwareinc : enterprisepack (Office 365 entreprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Voir aussi


[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
