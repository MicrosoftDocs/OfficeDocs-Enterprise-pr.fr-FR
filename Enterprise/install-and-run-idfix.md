---
title: Télécharger et exécuter l’outil IdFix Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Comment télécharger et exécuter l’outil IdFix Office 365 pour nettoyer vos services de domaine Active Directory (AD DS) avant de le synchroniser avec Office 365.
ms.openlocfilehash: d816abe8e93830832077c614e496576d42890d50
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068776"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a>Télécharger et exécuter l’outil IdFix Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

IdFix identifie les erreurs telles que les doublons et les problèmes de mise en forme dans votre domaine des services de domaine Active Directory (AD DS) avant la synchronisation avec Office 365. 
  
Pour terminer cette tâche, vous devez être familiarisé avec les objets utilisateur, groupe et contact dans AD DS.
  
Si vous ne pouvez pas effectuer cette tâche, il existe deux autres opérations que vous pouvez effectuer. Ces méthodes peuvent être plus faciles, mais elles peuvent également prendre plus de temps ou avoir d’autres inconvénients. Ce sont :
  
- **Exécuter la synchronisation d’annuaires sans exécuter IdFix** 

  Vous pouvez synchroniser votre annuaire sans utiliser l’outil IdFix, mais il n’est pas recommandé de le faire. La correction des erreurs avant la synchronisation nécessite moins de temps et permet souvent d’effectuer une transition plus fluide vers le nuage. 

- **Embaucher un consultant** 

  L’obtention d’une aide expert peut permettre à vos utilisateurs de fonctionner rapidement et de synchroniser votre annuaire. 
    
## <a name="what-you-need-to-run-idfix"></a>Ce dont vous avez besoin pour exécuter IdFix

Le moyen le plus simple d’obtenir et d’exécuter IdFix est de le télécharger sur un ordinateur qui est joint à votre domaine AD DS. Vous pouvez l’exécuter sur le contrôleur de domaine si vous le souhaitez, mais cela n’est pas nécessaire.
  
### <a name="idfix-hardware-requirements"></a>Configuration matérielle requise pour IdFix

L’ordinateur sur lequel vous téléchargez IdFix doit satisfaire à la configuration matérielle minimale requise suivante :
  
- 4 Go de RAM
- 2 Go d’espace disque
   
### <a name="idfix-software-requirements"></a>Configuration logicielle requise pour IdFix

L’ordinateur sur lequel vous téléchargez IdFix doit être joint au même domaine AD DS que celui à partir duquel vous voulez synchroniser les utilisateurs avec Office 365. 

.NET Framework 4,0 doit également être installé sur l’ordinateur. Si vous exécutez Windows Server 2008 ou une version ultérieure, .NET Framework est probablement déjà installé. Si ce n’est pas le cas, vous pouvez [Télécharger .net 4,0 à partir du centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou de Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Exigences en matière d’autorisations IdFix

Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture et en écriture au domaine AD DS.
  
Si vous n’êtes pas certain que votre compte d’utilisateur répond à ces exigences et que vous n’êtes pas sûr de savoir comment procéder, vous pouvez toujours télécharger et exécuter IdFix. Si votre compte d’utilisateur ne dispose pas des autorisations appropriées, IdFix affiche simplement une erreur lorsque vous tentez de l’exécuter.
  
## <a name="download-and-extract-idfix"></a>Télécharger et extraire IdFix

Suivez ces instructions. 
  
1. Connectez-vous à l’ordinateur sur lequel vous souhaitez exécuter l’outil IdFix.
    
2. Accédez au site [outil de correction d’erreurs DirSync IdFix](https://github.com/microsoft/idfix) .
    
3. Cliquez sur **lancer** dans la section de **lancement ClickOnce** pour télécharger le fichier zip. Ouvrez le fichier zip.
    
4. Dans la fenêtre **IdFix** , sélectionnez **extraire**, puis **extraire tout**. Par défaut, IdFix est extrait `C:\Users\<your user name>\Documents\IdFix`. 
    
5. Sélectionnez **extraire**.

Vos étapes peuvent varier en fonction de votre version de Windows et de votre navigateur Internet.
    
## <a name="run-the-idfix-tool"></a>Exécuter l’outil IdFix

Une fois que vous avez téléchargé et extrait IdFix, exécutez-le pour rechercher des problèmes dans votre domaine AD DS.
  
1. À l’aide d’un compte disposant d’un accès en lecture/écriture à votre domaine AD DS, connectez-vous à l’ordinateur sur lequel vous avez téléchargé IdFix.
    
2. Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez extrait IdFix. Si vous avez choisi le dossier par défaut pendant l’extraction `C:\Users\<your user name>\Documents\IdFix`, accédez à. 
    
3. Double-cliquez sur **IdFix. exe**. 
  
4. Par défaut, IdFix utilise l’ensemble de règles mutualisée pour tester les entrées de votre répertoire. Il s’agit de l’ensemble de règles approprié pour la plupart des clients Office 365. Toutefois, si vous êtes un client Office 365 dédié ou international dans le cadre des réglementations relatives aux armes (ITAR)), vous pouvez configurer IdFix pour qu’il utilise plutôt le jeu de règles dédié. Si vous n’êtes pas sûr de votre type de client, vous pouvez en toute sécurité ignorer cette étape. Pour définir le jeu de règles sur dédié, cliquez sur l’icône d’engrenage dans la barre de menus, puis choisissez **dédié**.
    
5. Sélectionnez **requête**.
    
    ![Sélectionnez requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Par défaut, IdFix recherche les erreurs dans le répertoire entier.
    
    En fonction de la taille de votre répertoire, l’exécution de la requête peut prendre un certain temps. Vous pouvez suivre la progression au bas de la fenêtre principale de l’outil. Si vous cliquez sur **Annuler**, vous devrez redémarrer depuis le début.
  
7. Une fois que IdFix a terminé la requête, vous pouvez synchroniser votre répertoire s’il n’y a pas d’erreurs. S’il existe des erreurs dans votre répertoire, il est recommandé de les résoudre avant de procéder à la synchronisation. Pour plus d’informations, consultez la rubrique [Prepare Directory attributes for Synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) .
    
    Bien qu’il ne soit pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons vivement de consulter au moins toutes les erreurs renvoyées par IdFix.
    
    Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil. 
    
8. Si vous acceptez le changement suggéré dans la colonne **mettre à jour** , dans la colonne **action** , sélectionnez les actions que doit effectuer IdFix pour implémenter la modification, puis cliquez sur **appliquer**. Lorsque vous cliquez sur **appliquer**, l’outil effectue les modifications dans l’annuaire.
    
    Il n’est pas nécessaire de cliquer sur **appliquer** après chaque mise à jour. Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **appliquer** et IdFix les modifiera en même temps. Vous pouvez trier les erreurs par type d’erreur en cliquant sur **erreur** en haut de la colonne qui répertorie les types d’erreur. 
    
    Une stratégie consiste à corriger toutes les erreurs du même type ; par exemple, corrigez tous les doublons en premier, puis appliquez-les. Ensuite, corrigez les erreurs de format de caractère, et ainsi de suite. Chaque fois que vous appliquez les modifications, l’outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d’erreur. Le [Journal des transactions](idfix-transaction-log.md) est stocké dans le dossier où vous avez extrait IdFix, qui est _C:\Users\<votre nom d’utilisateur> \documents\idfix_ par défaut. 
    
    ![Correction des erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Une fois que toutes les modifications ont été apportées au répertoire, exécutez à nouveau IdFix pour vous assurer que les corrections que vous avez apportées n’ont pas introduit de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est recommandé de suivre le processus quelques fois avant de procéder à la synchronisation.
    
## <a name="additional-resources-on-idfix"></a>Ressources supplémentaires sur IdFix 

- [Attributs et objets d’IdFix pris en charge et exclus](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Office 365 IdFix journal des transactions](idfix-transaction-log.md)
    
## <a name="video-training"></a>Vidéo de formation

Pour plus d’informations, consultez la leçon [installer et utiliser l’outil IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), qui vous est proposée par LinkedIn Learning.
  

