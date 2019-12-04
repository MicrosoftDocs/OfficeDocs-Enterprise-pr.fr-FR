---
title: Attributs et objets d'IdFix pris en charge et exclus
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Répertorie les attributs qui sont exclus et pris en charge par l’outil IdFix.
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813924"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Attributs et objets d'IdFix pris en charge et exclus

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Il existe deux ensembles de règles gérées par IdFix ; Mutualisée et dédiée/ITAR. Pour l’instant, les deux ensembles de règles excluent les mêmes objets, attributs et valeurs d’attribut de la recherche. Cela peut changer dans les versions ultérieures.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusions d’erreurs dédiées et mutualisées utilisées par IdFix
Cette section répertorie les objets, attributs et valeurs que IdFix exclut de sa recherche dans l’annuaire. L’astérisque (\*) est un caractère générique qui peut être remplacé par d’autres caractères.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objets, attributs et valeurs exclus pendant une recherche IdFix

|**Exclusion**|**Exemple**|
|:-----|:-----|
|Choix\* |Administrateur |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|iusr_\* |iusr_ *MachineName* |
|connaît\*  |IWAM_ *MachineName* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contient « \0ACNF : »|« \0ACNF : *GUID* » |
|L’objet contient l’attribut IsCriticalSystemObject |Voir [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Objets et attributs dédiés à plusieurs clients et contrôlés par IdFix
Les attributs vérifiés pour les erreurs par IdFix sont décrits dans la section « Préparation des attributs et des objets d’annuaire » de [Prepare Directory attributes for Synchronization with Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

