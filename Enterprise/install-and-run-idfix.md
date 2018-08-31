---
title: Installation et exécution de l'outil IdFix d'Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Comment installer et exécuter l’outil Office 365 IdFix pour nettoyer votre annuaire active directory avant de le synchroniser avec Office 365.
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540345"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installation et exécution de l'outil IdFix d'Office 365

IdFix identifie les erreurs telles que des doublons et les problèmes de mise en forme dans votre annuaire avant la synchronisation avec Office 365. 
  
Pour terminer cette tâche avec succès, vous devez vous familiarisent avec l’utilisateur, groupe et les objets contacts dans Active Directory.
  
Si vous ne pouvez pas effectuer cette tâche, il existe deux autres choses que vous pouvez faire. Ces méthodes peuvent être plus faciles, mais ils peuvent également être plus longues ou autres inconvénients. Ils sont :
  
- **Exécuter la synchronisation d’annuaires sans exécuter IdFix.** Vous pouvez synchroniser votre annuaire sans exécuter l’outil IdFix, mais il n’est pas recommandé. Correction des erreurs avant la synchronisation prend moins de temps et fournit souvent une transition plus fluide vers le nuage. 
- **Faire appel à un consultant. ** Obtenir de l’aide d’un expert peut permettre à vos utilisateurs d’être rapidement opérationnels et de synchroniser votre annuaire. 
    
## <a name="what-you-need-to-run-idfix"></a>Ce dont vous avez besoin pour exécuter IdFix

Le plus simple à préparer IdFix et en cours d’exécution consiste à installer sur un ordinateur relié à votre domaine. Vous pouvez l’exécuter sur le contrôleur de domaine si vous le souhaitez, mais il n’est pas nécessaire.
  
### <a name="idfix-hardware-requirements"></a>Configuration matérielle requise pour IdFix

L’ordinateur sur lequel vous installez IdFix doit répondre aux exigences matérielles suivantes :
  
- 4 Go de RAM (minimum)
- 2 Go d'espace disque (minimum)
    
### <a name="idfix-software-requirements"></a>Configuration logicielle requise pour IdFix

L’ordinateur où vous installez IdFix doit doit être joint au même domaine Active Directory à partir de laquelle vous souhaitez synchroniser les utilisateurs vers Office 365. L’ordinateur doit également avoir installé .NET Framework 4.0. 
  
Si vous exécutez Windows Server 2008 ou Windows Server 2012, .NET Framework est probablement déjà installé. Si non, vous pouvez [télécharger .NET 4.0 à partir du centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou à l’aide de Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Conditions requises d'autorisations IdFix

Le compte d'utilisateur dont vous vous servez pour exécuter IdFix doit disposer de droits d'accès en lecture/écriture à l'annuaire.
  
Si vous n’êtes pas certain que votre compte d’utilisateur répond à ces exigences, et vous ne savez pas comment vérifier, vous pouvez installer et exécuter IdFix quand même. Si votre compte d’utilisateur ne possède pas les autorisations appropriées, IdFix affichera simplement une erreur lorsque vous essayez d’exécuter.
  
## <a name="install-idfix"></a>Installation d'IdFix

Pour installer IdFix, vous devez télécharger et décompresser le fichier **IdFix.exe**, comme décrit dans les étapes suivantes : 
  
1. Ouvrez une session sur l'ordinateur sur lequel vous souhaitez installer l'outil IdFix.
    
2. Accédez au site de téléchargement Microsoft pour l' [Outil de correction d’erreurs IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Choisissez **Download** (Télécharger).
    
4. Lorsque vous y êtes invité, cliquez sur **exécuter**.
    
5. Dans la boîte de dialogue **Auto-extracteur de fichier WinZip** , dans la zone **décompresser dans dossier** , tapez ou naviguez jusqu'à l’emplacement où vous souhaitez installer l’outil IdFix. Par défaut, IdFix est installé dans les outils de C:\Deployment\. 
    
6. Cliquez sur **décompresser**.
    
## <a name="run-the-idfix-tool"></a>Exécution de l'outil IdFix

Après l'installation d'IdFix, exécutez l'outil pour rechercher les problèmes dans votre annuaire :
  
1. Utilisez un compte disposant de droits d'accès en lecture/écriture à l'annuaire pour vous connecter à l'ordinateur sur lequel vous avez installé IdFix.
    
2. Dans l'Explorateur de fichiers, accédez à l'emplacement où vous avez installé IdFix.  Si vous avez choisi le dossier par défaut lors de l'installation, accédez à C:\Outils de déploiement\IdFix.
    
3. Double-cliquez sur **IdFix.exe**. 
    
    ![Choisissez le fichier IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Par défaut, IdFix utilise la règle multiclients à tester les entrées dans le répertoire. Il s’agit de la règle de droite définie pour la plupart des clients Office 365. Toutefois, si vous êtes un client ITAR (trafic International règlements armes) ou Office 365 dédiée, vous pouvez configurer IdFix pour utiliser la règle dédiée à la place. Si vous ne savez pas quel type de client vous êtes, vous pouvez ignorer cette étape. Pour définir l’ensemble de règles à dédié, cliquez sur l’icône représentant un engrenage dans la barre de menus, puis choisissez **dédié**.
    
5. Cliquez sur **requête**.
    
    ![Choisissez une requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Par défaut, IdFix recherche des erreurs dans l'intégralité de l'annuaire.
    
    Selon la taille de votre annuaire, exécution de la requête peut prendre du temps. Vous pouvez surveiller la progression au bas de la fenêtre principale de l’outil. Si vous cliquez sur **Annuler**, vous devrez redémarrer à partir du début.
    
    ![Nombre de requêtes et des erreurs IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Une fois qu'IdFix a terminé la requête, et s'il n'y a pas d'erreurs dans votre annuaire, vous pouvez continuer et synchroniser votre annuaire. S'il y a des erreurs dans votre annuaire, nous vous recommandons de les corriger avant de procéder à la synchronisation. Si vous souhaitez obtenir des informations plus précises sur les types d'erreurs et les recommandations sur la meilleure façon de résoudre chacune d'elles, consultez les liens à la fin de cette rubrique. 
    
    Même s'il n'est pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons fortement de consulter au moins toutes les erreurs renvoyées par IdFix.
    
    Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil. 
    
8. Si vous êtes d'accord avec la modification recommandée dans la colonne **UPDATE**, sélectionnez l'action qu'IdFix doit effectuer dans la colonne **ACTION** pour appliquer le changement, puis cliquez sur **Appliquer**. Lorsque vous cliquez sur **Appliquer**, l'outil effectue les modifications dans l'annuaire.
    
    Vous n’êtes pas obligé de cliquer sur **Appliquer** après chaque mise à jour. Au lieu de cela, vous pouvez résoudre plusieurs erreurs avant que vous cliquez sur **Appliquer** et IdFix les modifier en même temps. Vous pouvez trier les erreurs par type d’erreur en cliquant sur l' **erreur** en haut de la colonne qui répertorie les types d’erreurs. 
    
    Une stratégie consiste à corriger toutes les erreurs du même type ; par exemple, corrigez d’abord tous les doublons et les appliquer. Ensuite, corrigez les erreurs de format de caractère et ainsi de suite. Chaque fois que vous appliquez les modifications, l’outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d’erreur. Le [journal des transactions](idfix-transaction-log.md) est stocké dans le dossier que vous avez installé IdFix dans.  _C:\Deployment Tools\IdFix_ par défaut. 
    
    ![Correction des erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Après tout de vos modifications sont apportées à l’annuaire, exécuter IdFix à nouveau pour vous assurer que les correctifs que vous avez apportées n’a pas introduire de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est conseillé de suivre le processus de quelques heures avant la synchronisation.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Je veux affiner ma recherche ou analyser plus attentivement les erreurs, que puis-je faire avec IdFix ?

Des informations plus détaillées sont disponibles dans les rubriques suivantes :
  
- [Préparer les attributs de répertoire pour la synchronisation avec Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Après avoir installé l’outil, accéder à cette rubrique pour obtenir des instructions plus détaillées sur l’exécution de l’outil, erreurs courantes que vous rencontrerez suggérés correctifs, des exemples et des meilleures pratiques pour la procédure à suivre lorsque vous avez un grand nombre d’erreurs. 
- [Référence : IdFix et exclus pris en charge les attributs et objets](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Référence : Journal des transactions IdFix d'Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Formation vidéo

Pour plus d’informations, consultez la leçon, [installer et utiliser l’outil IDFix](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), proposée par apprentissage LinkedIn.
  

