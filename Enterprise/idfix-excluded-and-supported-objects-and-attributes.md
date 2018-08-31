---
title: Attributs et objets d’IdFix pris en charge et exclus
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Répertorie les attributs qui sont pris en charge par l’outil IdFix et exclus.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540474"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Attributs et objets d’IdFix pris en charge et exclus
Il existe deux jeux de règles gérés par IdFix ; Multiclients et Dédié/ITAR. À ce stade, les deux jeux de règles excluent les mêmes objets, attributs et valeurs d'attributs de la recherche. Cela pourrait changer dans les prochaines versions.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusions d'erreurs Multiclients et Dédié utilisées par IdFix
Cette section répertorie les objets, attributs et valeurs IdFix exclut de la recherche dans le répertoire. L’astérisque (\*) est un caractère générique qui peut être remplacé par d’autres caractères.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objets, attributs et valeurs exclus lors d'une recherche IdFix

|**Exclusion**|**Exemple**|
|:-----|:-----|
|Admini\* |Administrateur |
|{CAS_\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Invité\* ||
|Connecteur HTTP\*  |HTTPConnector |
|krbtgt\* |MS-DS-KrbTgt-lien |
|IUSR_\* |IUSR_ *NomOrdinateur* |
|IWAM\*  |IWAM_ *NomOrdinateur* |
|MSOL\* |MSOL_AD_SYNC |
|compte Support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contient « \0ACNF : »|« \0ACNF : *GUID* » |
|L'objet contient l'attribut IsCriticalSystemObject |Consultez la rubrique [attribut isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Attributs et objets Multiclients et Dédié vérifiés par IdFix
Les attributs qui sont en cours pour les erreurs par IdFix sont décrits dans la section « Objet et attribut préparation Directory » dans les [attributs d’annuaire préparer pour la synchronisation avec Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

