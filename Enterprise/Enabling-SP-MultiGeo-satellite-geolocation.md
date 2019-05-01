---
title: Activation de SharePoint Multi-Geo dans votre emplacement géographique satellite
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Activation de SharePoint Multi-Geo dans votre emplacement satellite géographique.
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487868"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Activation de SharePoint Multi-Geo dans votre emplacement géographique satellite

Cet article est destiné aux administrateurs généraux ou SharePoint qui ont créé un emplacement satellite géo multiple **avant** les fonctionnalités SharePoint Multi-géo sont devenues généralement disponibles le 27 mars 2019 et n’ont pas activé SharePoint multi-Geo dans leurs emplacements. 

>[!Note]
>Si vous avez ajouté un nouvel emplacement géo **après le 27 mars**, vous n’avez pas besoin effectuer ces instructions car votre nouvel emplacement géo sera déjà activé pour OneDrive et SharePoint Multi-géo.

Ces instructions permettent d’activer SharePoint dans votre emplacement satellite, vos utilisateurs satellite géo multiple peuvent tirer parti des fonctionnalités OneDrive et SharePoint Multi-géo dans Office 365. 

>[!IMPORTANT]
>Veuillez noter qu’il s’agit d’une activation possible. Une fois que vous définissez le mode SharePoint Online, vous ne pouvez pas revenir vers votre client OneDrive uniquement en mode multiple géo sans une escalade avec une prise en charge. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Pour définir l’emplacement géo en mode SPO

Pour définir un emplacement géo en mode SPO, connectez-vous à l’emplacement géo que vous souhaitez définir en Mode SPO :

1.  Ouvrez votre outil SharePoint Online Management Shell 
2.  Se connecter-SPOService-URL « https://$tenantGeo-admin.sharepoint.com »- informations d’identification $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  Cette opération généralement prend environ une heure pendant que nous réalisons divers publications dans le service et de nouveau apposer un cachet à votre client. Après au moins 1 heure, veuillez effectuer une SPOMultiGeoExperience Get.  Vous verrez alors que cet emplacement géo est en mode SPO.</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Certains caches dans le service se mettent à jour toutes les 24 heures, il est donc possible que pendant une période de 24 heures, votre géo satellite peut, par intermittence, se comporter comme s’il s’agit en mode ODB. Cela n’entraîne pas de problème d’ordre technique. 
 
Pour plus d’informations concernant SharePoint Multi-géo, veuillez consulter [aka.ms/sharepointmultigeo](https://docs.microsoft.com/fr-FR/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)


