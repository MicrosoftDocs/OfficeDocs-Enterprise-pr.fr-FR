---
title: Installer et exécuter l'outil IdFix pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Comment installer et exécuter l’outil IdFix Office 365 pour nettoyer votre Active Directory avant de le synchroniser avec Office 365.
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067290"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installer et exécuter l'outil IdFix pour Office 365

IdFix identifie les erreurs telles que les doublons et les problèmes de mise en forme dans votre répertoire avant la synchronisation avec Office 365. 
  
Pour terminer cette tâche, vous devez être familiarisé avec les objets utilisateur, groupe et contact dans Active Directory.
  
Si vous ne pouvez pas effectuer cette tâche, il existe deux autres opérations que vous pouvez effectuer. Ces méthodes peuvent être plus faciles, mais elles peuvent également prendre plus de temps ou avoir d’autres inconvénients. Ces limites sont :
  
- **Exécutez la synchronisation d’annuaires sans exécuter IdFix.** Vous pouvez synchroniser votre annuaire sans exécuter l’outil IdFix, mais il n’est pas recommandé de le faire. La correction des erreurs avant la synchronisation nécessite moins de temps et permet souvent d’effectuer une transition plus fluide vers le nuage. 
- **Embaucher un consultant.** L’obtention d’une aide expert peut permettre à vos utilisateurs de fonctionner rapidement et de synchroniser votre annuaire. 
    
## <a name="what-you-need-to-run-idfix"></a>Ce dont vous avez besoin pour exécuter IdFix

Le moyen le plus simple d’obtenir IdFix et de l’exécuter est de l’installer sur un ordinateur qui est associé à votre domaine. Vous pouvez l’exécuter sur le contrôleur de domaine si vous le souhaitez, mais cela n’est pas nécessaire.
  
### <a name="idfix-hardware-requirements"></a>Configuration matérielle requise pour IdFix

L’ordinateur sur lequel vous installez IdFix doit répondre à la configuration matérielle minimale requise suivante:
  
- 4 Go de RAM
- 2 Go d’espace disque
    
### <a name="idfix-software-requirements"></a>Configuration logicielle requise pour IdFix

L’ordinateur sur lequel vous installez IdFix doit être joint au même domaine Active Directory que celui à partir duquel vous souhaitez synchroniser les utilisateurs avec Office 365. .NET Framework 4,0 doit également être installé sur l’ordinateur. 
  
Si vous exécutez Windows Server 2008 ou Windows Server 2012, .NET Framework est probablement déjà installé. Si ce n’est pas le cas, vous pouvez [Télécharger .net 4,0 à partir du centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou via Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Exigences en matière d’autorisations IdFix

Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture/écriture à l’annuaire.
  
Si vous n’êtes pas certain que votre compte d’utilisateur répond à ces exigences et que vous n’êtes pas sûr de savoir comment procéder, vous pouvez toujours installer et exécuter IdFix. Si votre compte d’utilisateur ne dispose pas des autorisations appropriées, IdFix affiche simplement une erreur lorsque vous tentez de l’exécuter.
  
## <a name="install-idfix"></a>Installer IdFix

Pour installer IdFix, téléchargez et décompressez **IdFix. exe**: 
  
1. Ouvrez une session sur l’ordinateur sur lequel vous souhaitez installer l’outil IdFix.
    
2. Accédez au site de téléchargement Microsoft pour l' [outil de correction d’erreur DirSync IdFix](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Choisissez **Download** (Télécharger).
    
4. Lorsque vous y êtes invité, choisissez **exécuter**.
    
5. Dans la boîte de dialogue **WinZip Self-Extractor** , dans la zone de texte **Unzip to Folder** (décompresser dans le dossier), tapez ou accédez à l’emplacement où vous souhaitez installer l’outil IdFix. Par défaut, IdFix est installé dans `C:\Deployment Tools\`. 
    
6. Sélectionnez **Unzip**.
    
## <a name="run-the-idfix-tool"></a>Exécuter l’outil IdFix

Une fois que vous avez installé IdFix, exécutez l’outil pour rechercher des problèmes dans votre répertoire:
  
1. À l’aide d’un compte disposant d’un accès en lecture/écriture à l’annuaire, ouvrez une session sur l’ordinateur sur lequel vous avez installé IdFix.
    
2. Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez installé IdFix. Si vous avez choisi le dossier par défaut lors de l' `C:\Deployment Tools\IdFix`installation, accédez à.
    
3. Double-cliquez sur **IdFix. exe**. 
    
    ![Choisissez le fichier IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Par défaut, IdFix utilise l’ensemble de règles mutualisée pour tester les entrées de votre répertoire. Il s’agit de l’ensemble de règles approprié pour la plupart des clients Office 365. Toutefois, si vous êtes un client Office 365 dédié ou ITAR (trafic international dans les réglementations sur les armes), vous pouvez configurer IdFix pour qu’il utilise le jeu de règles dédié à la place. Si vous n’êtes pas sûr de votre type de client, vous pouvez en toute sécurité ignorer cette étape. Pour définir le jeu de règles sur dédié, cliquez sur l’icône d’engrenage dans la barre de menus, puis choisissez **dédié**.
    
5. Sélectionnez **requête**.
    
    ![Sélectionnez requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Par défaut, IdFix recherche les erreurs dans le répertoire entier.
    
    En fonction de la taille de votre répertoire, l’exécution de la requête peut prendre un certain temps. Vous pouvez suivre la progression au bas de la fenêtre principale de l’outil. Si vous cliquez sur **Annuler**, vous devrez redémarrer depuis le début.
    
    ![Requête IdFix et nombre d’erreurs.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Une fois que IdFix a terminé la requête, vous pouvez continuer et synchroniser votre annuaire s’il n’y a pas d’erreurs. S’il existe des erreurs dans votre répertoire, il est recommandé de les résoudre avant de procéder à la synchronisation. Si vous souhaitez obtenir des informations plus spécifiques sur les types d’erreurs et des recommandations sur la meilleure façon de corriger chacune d’elles, consultez les liens à la fin de cette rubrique. 
    
    Bien qu’il ne soit pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons vivement de consulter au moins toutes les erreurs renvoyées par IdFix.
    
    Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil. 
    
8. Si vous acceptez le changement suggéré dans la colonne **mettre à jour** , dans la colonne **action** , sélectionnez les actions que doit effectuer IdFix pour implémenter la modification, puis cliquez sur **appliquer**. Lorsque vous cliquez sur **appliquer**, l’outil effectue les modifications dans l’annuaire.
    
    Il n’est pas nécessaire de cliquer sur **appliquer** après chaque mise à jour. Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **appliquer** et IdFix les modifiera en même temps. Vous pouvez trier les erreurs par type d’erreur en cliquant sur **erreur** en haut de la colonne qui répertorie les types d’erreur. 
    
    Une stratégie consiste à corriger toutes les erreurs du même type; par exemple, corrigez tous les doublons en premier, puis appliquez-les. Ensuite, corrigez les erreurs de format de caractère, et ainsi de suite. Chaque fois que vous appliquez les modifications, l’outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d’erreur. Le [Journal des transactions](idfix-transaction-log.md) est stocké dans le dossier dans lequel vous avez installé IdFix.  _C:\Deployment Tools\IdFix_ par défaut. 
    
    ![Correction des erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Une fois que toutes les modifications ont été apportées au répertoire, exécutez à nouveau IdFix pour vous assurer que les corrections que vous avez apportées n’ont pas introduit de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est recommandé de suivre le processus quelques fois avant de procéder à la synchronisation.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Je souhaite affiner ma recherche ou approfondir les erreurs, que puis-je faire avec IdFix?

Des informations plus détaillées sont disponibles dans les rubriques suivantes:
  
- [Préparez les attributs d’annuaire pour la synchronisation avec Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Une fois que vous avez installé l’outil, accédez à cette rubrique pour obtenir des instructions plus détaillées sur l’exécution de l’outil, les erreurs courantes que vous rencontrez, les corrections suggérées, les exemples et les meilleures pratiques à suivre lorsque vous avez un grand nombre d’erreurs. 
- [Reference: IdFix excluded and supported objects and attributes](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Référence : Journal des transactions IdFix d'Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Vidéo de formation

Pour plus d’informations, consultez la leçon [installer et utiliser l’outil IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), qui vous est proposée par LinkedIn Learning.
  

