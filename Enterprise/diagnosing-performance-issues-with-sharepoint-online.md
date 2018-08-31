---
title: Diagnostic des problèmes de performances avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: Cet article vous montre comment vous pouvez diagnostiquer les problèmes courants avec votre site SharePoint Online à l’aide des outils de développement Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540480"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnostic des problèmes de performances avec SharePoint Online

Cet article vous montre comment vous pouvez diagnostiquer les problèmes courants avec votre site SharePoint Online à l’aide des outils de développement Internet Explorer.
  
Il existe trois manières différentes pour identifier un problème de performances dû aux personnalisations sur une page d’un site SharePoint Online.
  
- Le moniteur réseau de la barre d’outils F12
    
- Comparaison à une page de référence non personnalisée
    
- Les indicateurs de performances d’en-tête de réponse SharePoint Online
    
Cette rubrique décrit comment utiliser chacune de ces méthodes pour diagnostiquer les problèmes de performances. Une fois que vous avez trouvé la cause du problème, vous pouvez toujours une solution à l’aide des articles sur l’amélioration des performances de SharePoint que vous trouverez sur http://aka.ms/tune.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Utilisation de la barre d’outils F12 pour diagnostiquer les performances dans SharePoint Online
<a name="F12ToolInfo"> </a>

Dans cet article, nous utilisons Internet Explorer 11. Les versions des outils de développement F12 sur d’autres navigateurs ont des fonctionnalités similaires même si ceux-ci peuvent présenter de légères différences. Pour plus d’informations sur les outils de développement F12, voir :
  
- [Nouveautés dans les outils F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [L’utilisation des outils de développement F12](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Pour faire apparaître les outils de développement, appuyez sur **F12**, puis cliquez sur l’icône Wi-Fi : 
 
  
![Capture d’écran de l’icône Wi-Fi des outils de développement F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Sur l’onglet **Réseau**, appuyez sur le bouton de lecture vert pour charger une page. L’outil renvoie tous les fichiers que le navigateur demande afin d’obtenir la page que vous avez demandée. La capture d’écran suivante montre la liste. 
  
![Capture d’écran de la liste de fichiers renvoyés avec une demande de page.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Vous pouvez également afficher le temps de téléchargement des fichiers sur le côté droit, comme le montre cette capture d’écran.
  
![Diagramme montrant le temps nécessaire pour charger les pages demandées à partir de SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Vous obtenez ainsi une représentation visuelle de la durée de chargement du fichier. La ligne verte représente le moment auquel la page est prête à être affichée par le navigateur. Vous pouvez ainsi obtenir un aperçu rapide des différents fichiers susceptibles d’être à l’origine de la lenteur de chargement des pages sur votre site.


  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configuration d’une ligne de base non personnalisés pour SharePoint Online
<a name="F12ToolInfo"> </a>

La meilleure méthode pour déterminer les points faibles de performances de votre site consiste à configurer une collection de sites entièrement out-of-the-box dans SharePoint Online. De cette manière, vous pouvez comparer les différents aspects de votre site avec ce que vous obtenez sans personnalisation dans la page. La page d’accueil Business OneDrive est un bon exemple de collection de sites distincte qui n’est probablement pas avoir toutes les personnalisations.
  
## <a name="viewing-sharepoint-response-header-information"></a>Affichage des informations d’en-tête de réponse SharePoint
<a name="F12ToolInfo"> </a>

Dans SharePoint Online et SharePoint Server 2013, vous pouvez accéder aux informations qui sont renvoyées au navigateur dans l’en-tête de réponse pour chaque fichier. Pour diagnostiquer des problèmes de performances, les deux valeurs les plus utiles sont SPRequestDuration et X-SharePointHealthScore :
  
- **SPRequestDuration**
    
    Il s’agit de la durée de traitement de la demande sur le serveur. Cette valeur peut vous aider à déterminer si la demande est lourde et requiert beaucoup de ressources. Cette donnée est la meilleure information que vous pourrez obtenir sur la quantité de travail nécessaire au serveur pour fournir la page.
    
- **X-SharePointHealthScore**
    
    Cela indique que l’utilisation du serveur, ou du processeur sur lequel s’exécute l’instance de SharePoint. Ce nombre compris entre 0 et 10, où 0 indique que le serveur est inactif et 10 indique le serveur est très occupé. Un score d’intégrité qui est toujours 9 ou 10 peut indiquer un problème de performances en cours avec le serveur. Toute autre valeur indique ce serveur fonctionne de la plage attendue.
    
 **Affichage des informations d’en-tête de réponse SharePoint**
  
1. Vérifiez que vous avez installés les outils F12. Pour plus d’informations sur le téléchargement et installation de ces outils, voir [Nouveautés d’outils F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. Dans les outils F12, sur l’onglet **Réseau**, appuyez sur le bouton lecture vert pour charger une page. 
    
3. Cliquez sur l’un des fichiers .aspx renvoyés par l’outil, puis cliquez sur **DÉTAILS**. 
    
    ![Affiche les détails de l’en-tête de réponse](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Cliquez sur **En-têtes de réponse**. 
    
    ![Diagramme présentant l’URL de l’en-tête de réponse](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Quelle est la cause des problèmes de performances dans SharePoint Online ?
<a name="F12ToolInfo"> </a>

L’article [options de Navigation de SharePoint Online](navigation-options-for-sharepoint-online.md) montre un exemple d’utilisation de la valeur SPRequestDuration pour déterminer que le volet de navigation structurelle complexe a été à l’origine de la page pour prendre beaucoup de temps à traiter sur le serveur. En optant pour une valeur pour un site de base (sans personnalisation), il est possible déterminer si un fichier donné prend beaucoup de temps à charger. L’exemple utilisé dans les [options de Navigation de SharePoint Online](navigation-options-for-sharepoint-online.md) est le fichier .aspx principale. Ce fichier contient la plupart du code qui s’exécute pour le chargement de la page ASP.NET. Selon le modèle de site que vous utilisez, il peut être start.aspx, home.aspx, default.aspx ou un autre nom si vous personnalisez la page d’accueil. Si ce numéro est considérablement plus élevé que votre site planifié, il est une bonne indication qu’il existe un élément complexe dans votre page, qui est à l’origine des problèmes de performances. 
  
Une fois que vous avez identifié qu’il s’agit d’un problème propre à votre site, la méthode recommandée pour identifier l’origine de la médiocrité des performances consiste à éliminer toutes les causes possibles, telles que les personnalisations de page, et à les appliquer à nouveau au site une par une. Une fois que vous avez supprimé suffisamment de personnalisations et que la page présente de bonnes performances, vous pouvez les rajouter une par une.
  
Par exemple, si vous disposez d’une navigation très complexe, essayez de modifier la navigation pour ne pas afficher les sous-sites, puis vérifiez dans les outils de développement pour déterminer si cette modification a eu un impact. Sinon, si vous disposez d’une grande quantité de regroupements de contenus, essayez de les supprimer de votre page et vérifiez si les performances s’améliorent. Si vous éliminez toutes les causes possibles, puis les rajoutez une à la fois, vous pouvez facilement identifier les fonctionnalités qui posent le plus problème, puis élaborer une solution. 

  

