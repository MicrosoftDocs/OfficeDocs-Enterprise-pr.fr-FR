---
title: Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires et les correctifs possibles dans le centre d’administration Microsoft 365.
ms.openlocfilehash: 344cc71d192e6a73826c66c8bcbf8569d10e45d8
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605706"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le centre d’administration Microsoft 365. Seules les erreurs d’objet utilisateur sont affichées. Pour afficher les erreurs avec PowerShell, consultez la rubrique [identifier les objets avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans le centre d’administration Microsoft 365

Pour afficher les erreurs dans le centre d’administration Microsoft 365 :
  
1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec un compte d’administrateur général. 
    
2. Sur la page d' **Accueil** , vous verrez la carte de **gestion des utilisateurs** . 
    
    ![Carte de gestion des utilisateurs dans le centre d’administration Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Sur la carte, sélectionnez **synchroniser les erreurs** sous **Azure ad Connect** pour afficher les erreurs sur la page **Erreurs de synchronisation d’annuaires** .   
    
    ![Exemple de page d’erreurs de synchronisation d’annuaires](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Choisissez l’une des erreurs pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la façon de résoudre le problème.

   ![Exemple de détails d’une erreur de synchronisation d’annuaires](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Après l’affichage, consultez la rubrique [résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.

