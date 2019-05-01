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
description: Cet article explique comment vous pouvez diagnostiquer les problèmes courants liés à votre site SharePoint Online à l'aide des outils de développement Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492260"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnostic des problèmes de performances avec SharePoint Online

Cet article explique comment vous pouvez diagnostiquer les problèmes courants liés à votre site SharePoint Online à l'aide des outils de développement Internet Explorer.
  
Il existe trois méthodes différentes pour identifier une page sur un site SharePoint Online présentant un problème de performances avec les personnalisations.
  
- Moniteur réseau de la barre d'outils F12
    
- Comparaison avec une planification non personnalisée
    
- Mesures d'en-tête de réponse SharePoint Online
    
Cette rubrique décrit l'utilisation de chacune de ces méthodes pour diagnostiquer les problèmes de performances. Une fois que vous avez trouvé la cause du problème, vous pouvez travailler vers une solution à l'aide des articles sur l'amélioration des performances SharePoint que vous http://aka.ms/tunepouvez trouver sur.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Utilisation de la barre d'outils F12 pour diagnostiquer les performances dans SharePoint Online
<a name="F12ToolInfo"> </a>

Dans cet article, nous utilisons Internet Explorer 11. Les versions des outils de développement F12 sur d'autres navigateurs ont des fonctionnalités similaires, mais elles peuvent sembler légèrement différentes. Pour plus d'informations sur les outils de développement F12, voir:
  
- [Nouveautés dans les outils F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Utilisation des outils de développement F12](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Pour afficher les outils de développement, appuyez sur la **touche F12** , puis cliquez sur l'icône Wi-Fi: 
  
![Capture d’écran de l’icône Wi-Fi des outils de développement F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Dans l'onglet **réseau** , appuyez sur le bouton de lecture vert pour charger une page. L'outil renvoie tous les fichiers demandés par le navigateur pour obtenir la page que vous avez demandée. La capture d'écran suivante montre une liste de ce type. 
  
![Capture d’écran de la liste de fichiers renvoyés avec une demande de page.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Vous pouvez également consulter les temps de téléchargement des fichiers sur le côté droit, comme indiqué dans cette capture d'écran.
  
![Diagramme montrant le temps nécessaire pour charger les pages demandées à partir de SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Cela vous donne une représentation visuelle de la durée de chargement du fichier. La ligne verte représente le moment où la page est prête à être affichée par le navigateur. Cela peut vous donner un aperçu rapide des différents fichiers susceptibles de provoquer des charges de pages lentes sur votre site.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configuration d'une planification initiale non personnalisée pour SharePoint Online
<a name="F12ToolInfo"> </a>

La meilleure façon de déterminer les points faibles de performances de votre site consiste à configurer une collection de sites entièrement complète dans SharePoint Online. De cette façon, vous pouvez comparer tous les différents aspects de votre site à ce que vous obtiendriez sans personnalisation sur la page. La page d'accueil de OneDrive entreprise est un exemple d'une collection de sites distincte qui n'a probablement aucune personnalisation.
  
## <a name="viewing-sharepoint-response-header-information"></a>Affichage des informations d'en-tête de réponse SharePoint
<a name="F12ToolInfo"> </a>

Dans SharePoint Online et SharePoint Server 2013, vous pouvez accéder aux informations qui sont renvoyées au navigateur dans l'en-tête de la réponse pour chaque fichier. Les deux valeurs les plus utiles pour diagnostiquer les problèmes de performances sont SPRequestDuration et X-SharePointHealthScore:
  
- **SPRequestDuration**
    
    Il s'agit de la durée de traitement de la demande sur le serveur à traiter. Cela peut vous aider à déterminer si la demande est très lourde et gourmande en ressources. Il s'agit de la meilleure compréhension de la somme de travail que le serveur effectue pour traiter la page.
    
- **X-SharePointHealthScore**
    
    Cela indique l'utilisation du serveur, ou processeur, sur lequel votre instance SharePoint est exécutée. Ce nombre est compris entre 0 et 10, où 0 indique que le serveur est inactif et 10 indique que le serveur est très occupé. Un HealthScore qui est régulièrement 9 ou 10 peut indiquer un problème de performances en cours sur le serveur. Tout autre nombre indique que le serveur fonctionne dans la plage attendue.
    
 **Pour afficher les informations d'en-tête de réponse SharePoint**
  
1. Assurez-vous que les outils F12 sont installés. Pour plus d'informations sur le téléchargement et l'installation de ces outils, voir [what's New in F12 Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. Dans les outils F12, sous l'onglet **réseau** , appuyez sur le bouton de lecture vert pour charger une page. 
    
3. Cliquez sur l'un des fichiers. aspx renvoyés par l'outil, puis cliquez sur **Détails**. 
    
    ![Affiche les détails de l’en-tête de réponse](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Cliquez sur **en-têtes de réponse**. 
    
    ![Diagramme présentant l’URL de l’en-tête de réponse](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Qu'est-ce qui provoque des problèmes de performances dans SharePoint Online?
<a name="F12ToolInfo"> </a>

L'article [options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md) illustre un exemple d'utilisation de la valeur SPRequestDuration pour déterminer que la navigation structurelle compliquée entraînait un long traitement de la page sur le serveur. En prenant une valeur pour un site de base (sans personnalisation), il est possible de déterminer si le chargement d'un fichier donné prend beaucoup de temps. L'exemple utilisé dans les [options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md) est le fichier principal. aspx. Ce fichier contient la plupart des codes ASP.NET qui s'exécutent pour votre chargement de page. Selon le modèle de site que vous utilisez, il peut s'agir de Start. aspx, Home. aspx, default. aspx ou d'un autre nom si vous personnalisez la page d'accueil. Si ce nombre est considérablement supérieur à votre site de référence, c'est qu'il y a un problème complexe dans votre page, ce qui entraîne des problèmes de performances. 
  
Une fois que vous avez identifié un problème spécifique à votre site, la méthode recommandée pour déterminer ce qui provoque des performances médiocres est d'éliminer toutes les causes possibles, comme les personnalisations de page, et de les rajouter au site un par un. Une fois que vous avez supprimé suffisamment de personnalisations de la page, vous pouvez ajouter des personnalisations spécifiques une par une.
  
Par exemple, si vous avez une navigation très complexe, essayez de modifier la navigation de manière à ne pas afficher les sous-sites, puis vérifiez les outils de développement pour voir si cela fait une différence. Ou si vous avez un grand nombre de reprises de contenu, essayez de les supprimer de votre page et voyez si cela améliore les choses. Si vous supprimez toutes les causes possibles et les rajoutant une par une, vous pouvez facilement identifier les fonctionnalités qui constituent le plus grand problème, puis travailler vers une solution.
  

