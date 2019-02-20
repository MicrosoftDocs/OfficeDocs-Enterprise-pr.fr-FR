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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Répertorie les attributs qui sont exclus et pris en charge par l'outil IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085083"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Attributs et objets d’IdFix pris en charge et exclus
Il existe deux jeux de règles gérés par IdFix ; Multiclients et Dédié/ITAR. À ce stade, les deux jeux de règles excluent les mêmes objets, attributs et valeurs d'attributs de la recherche. Cela pourrait changer dans les prochaines versions.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusions d'erreurs Multiclients et Dédié utilisées par IdFix
Cette section répertorie les objets, attributs et valeurs que IdFix exclut de sa recherche dans l'annuaire. L'astérisque (\*) est un caractère générique qui peut être remplacé par d'autres caractères.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objets, attributs et valeurs exclus lors d'une recherche IdFix

|**Exclusion**|**Exemple**|
|:-----|:-----|
|Choix\* |Administrateur |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Invité\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|IUSR\* |IUSR _ *nomordinateur* |
|connaît\*  |IWAM _ *nomordinateur* |
|MSOL\* |MSOL_AD_SYNC |
|prend\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contient «\0ACNF:»|«\0ACNF: *GUID* » |
|L'objet contient l'attribut IsCriticalSystemObject |Voir [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Attributs et objets Multiclients et Dédié vérifiés par IdFix
Les attributs vérifiés pour les erreurs par IdFix sont décrits dans la section «Préparation des attributs et des objets d'annuaire» de [Prepare Directory attributes for Synchronization with Office 365 à l'aide de l'outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

