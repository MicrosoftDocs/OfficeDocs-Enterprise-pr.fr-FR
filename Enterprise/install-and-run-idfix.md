---
title: Télécharger et exécuter l’outil IdFix Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
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
description: Télécharger et exécuter l’outil IdFix Microsoft 365 pour vous aider à nettoyer vos services de domaine Active Directory (AD DS) avant de le synchroniser avec Microsoft 365.
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502659"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>Télécharger et exécuter l’outil IdFix Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

IdFix identifie les erreurs telles que les problèmes de doublons et de mise en forme dans votre domaine des services de domaine Active Directory (AD DS) avant la synchronisation avec Microsoft 365. 
  
Pour pouvoir exécuter cette tâche, vous devez savoir utiliser des objets utilisateur, groupe et contact dans AD DS.
  
Si vous ne parvenez pas à réaliser cette tâche, vous pouvez suivre d’autres procédures. Ces méthodes sont peut-être plus faciles, mais elles peuvent aussi prendre plus de temps ou présenter d’autres inconvénients. Ce sont :
  
- **Exécuter la synchronisation d'annuaires sans exécuter IdFix** 

  Vous pouvez synchroniser votre annuaire sans utiliser l’outil IdFix, mais nous ne le recommandons pas. Corriger les erreurs avant la synchronisation prend moins de temps et fournit souvent une transition plus facile vers le cloud. 

- **Faire appel à un consultant** 

  Obtenir de l’aide d’un expert peut permettre à vos utilisateurs d’être rapidement opérationnels et de synchroniser votre annuaire. 
    
## <a name="what-you-need-to-run-idfix"></a>Ce dont vous avez besoin pour exécuter IdFix

La façon la plus simple d’utiliser IdFix est de le télécharger sur un ordinateur joint à votre domaine AD DS. Vous pouvez l'exécuter sur le contrôleur de domaine mais ce n'est pas nécessaire.
  
### <a name="idfix-hardware-requirements"></a>Configuration matérielle requise pour IdFix

L’ordinateur sur lequel vous téléchargez IdFix doit respecter la configuration matérielle minimale requise suivante :
  
- 4 Go de RAM
- 2 Go d’espace disque dur
   
### <a name="idfix-software-requirements"></a>Configuration logicielle requise pour IdFix

L’ordinateur sur lequel vous téléchargez IdFix doit être joint au même domaine AD DS que celui à partir duquel vous voulez synchroniser les utilisateurs avec Microsoft 365. 

.NET Framework 4.0 doit également être installé sur l'ordinateur. Si vous exécutez Windows Server 2008 ou version ultérieure, le .NET Framework est probablement déjà installé. Sinon, vous pouvez [télécharger .NET 4.0 à partir du Centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou avec Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Conditions requises d'autorisations IdFix

Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture et en écriture au domaine AD DS.
  
Si vous n'êtes pas sûr que votre compte d'utilisateur répond à ces exigences, et si vous n'êtes pas sûr de la façon de le vérifier, vous pouvez télécharger et exécuter IdFix. Si votre compte d'utilisateur ne dispose pas des autorisations appropriées, IdFix affichera simplement une erreur lorsque vous essaierez de l'exécuter.
  
## <a name="download-and-extract-idfix"></a>Télécharger et extraire IdFix

Suivez ces instructions. 
  
1. Connectez-vous à l’ordinateur sur lequel vous voulez exécuter l’outil IdFix.
    
2. Accédez au [Outil de reconversion d’erreur IdFix DirSync](https://github.com/microsoft/idfix) site.
    
3. Cliquez sur **lancer** dans la section **lancement de ClickOnce** pour télécharger le fichier zip. Ouvrez le fichier zip.
    
4. Dans la fenêtre **IdFix**, sélectionnez **Extraire**, puis **Extraire toutes les**. Par défaut, IdFix est extrait pour `C:\Users\<your user name>\Documents\IdFix`. 
    
5. Sélectionnez **extraire**.

Votre procédure peut varier en fonction de votre version de Windows et de votre navigateur Internet.
    
## <a name="run-the-idfix-tool"></a>Exécution de l'outil IdFix

Une fois que vous avez téléchargé et extrait IdFix, exécutez-le pour rechercher les problèmes dans votre domaine AD DS.
  
1. À l’aide d’un compte qui dispose d’un accès en lecture/écriture à votre domaine AD DS, connectez-vous à l’ordinateur sur lequel vous avez téléchargé IdFix.
    
2. Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez extrait IdFix. Si vous avez choisi le dossier par défaut lors de l’extraction, accédez à `C:\Users\<your user name>\Documents\IdFix`. 
    
3. Double-cliquez sur **IdFix.exe**. 
  
4. Par défaut, IdFix utilise le jeu de règles multiclients pour tester les entrées dans votre annuaire. Il s’agit de l’entité de règle appropriée pour la plupart des clients Microsoft 365. Toutefois, si vous êtes un client Microsoft 365 dédié ou international en matière de réglementations sur les armements (ITAR)), vous pouvez configurer IdFix pour utiliser le groupe de règles dédié à la place. Si vous n'êtes pas sûr de votre type de client, vous pouvez ignorer cette étape en toute sécurité. Pour définir le jeu de règles sur Dédié, cliquez sur l’icône en forme d’engrenage dans la barre de menu, puis cliquez sur **Dédié**.
    
5. Cliquez sur **Requête**.
    
    ![Choisissez la requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Par défaut, IdFix recherche des erreurs dans l'intégralité de l'annuaire.
    
    En fonction de la taille de votre annuaire, l'exécution de la requête peut prendre du temps. Vous pouvez surveiller la progression au bas de la fenêtre principale de l'outil. Si vous cliquez sur **Annuler**, vous devez reprendre l'opération au début.
  
7. Une fois que IdFix a terminé la requête, vous pouvez synchroniser votre annuaire s’il n’y a pas d’erreur. S'il y a des erreurs dans votre annuaire, nous vous recommandons de les corriger avant de procéder à la synchronisation. Pour plus d’informations, voir [préparer les attributs d’annuaire pour la synchronisation avec ](prepare-directory-attributes-for-synch-with-idfix.md) Microsoft 365.
    
    Même s'il n'est pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons fortement de consulter au moins toutes les erreurs renvoyées par IdFix.
    
    Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil. 
    
8. Si vous êtes d’accord avec la modification recommandée dans la colonne **UPDATE**, sélectionnez l’action qu’IdFix doit effectuer dans la colonne **ACTION** pour appliquer le changement, puis cliquez sur **Appliquer**.  Lorsque vous cliquez sur **Apply**, l’outil apporte les modifications dans l’annuaire.
    
    Vous n'êtes pas obligé de cliquer sur **Appliquer** après chaque mise à jour. Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **Appliquer** et IdFix les modifie toutes simultanément. Vous pouvez les trier par type en cliquant sur **ERROR** (erreur) en haut de la colonne répertoriant les types d’erreurs. 
    
    Vous pouvez aussi corriger toutes les erreurs du même type ; par exemple, corrigez d'abord tous les doublons, puis appliquez les corrections. Corrigez ensuite les erreurs de format de caractère, et ainsi de suite. Chaque fois que vous appliquez les modifications, l'outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d'erreur. Le [journal des transactions](idfix-transaction-log.md) est stocké dans le dossier dans lequel vous avez extrait IdFix, _C:\Users\<your user name>\Documents\IdFix_ par défaut. 
    
    ![Correction d’erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Une fois que toutes vos modifications sont apportées à l'annuaire, exécutez IdFix à nouveau pour vous assurer que les corrections que vous avez effectuées n'ont pas introduit de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est conseillé de répéter cette procédure plusieurs fois avant la synchronisation.
    
## <a name="additional-resources-on-idfix"></a>Ressources supplémentaires sur IdFix 

- [Attributs et objets d’IdFix pris en charge et exclus](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Microsoft 365 journal des transactions IdFix](idfix-transaction-log.md)
    
