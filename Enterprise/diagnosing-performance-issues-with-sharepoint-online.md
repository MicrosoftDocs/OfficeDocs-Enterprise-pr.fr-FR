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
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="52db1-103">Diagnostic des problèmes de performances avec SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52db1-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="52db1-104">Cet article vous montre comment vous pouvez diagnostiquer les problèmes courants avec votre site SharePoint Online à l’aide des outils de développement Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="52db1-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="52db1-105">Il existe trois manières différentes pour identifier un problème de performances dû aux personnalisations sur une page d’un site SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="52db1-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="52db1-106">Le moniteur réseau de la barre d’outils F12</span><span class="sxs-lookup"><span data-stu-id="52db1-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="52db1-107">Comparaison à une page de référence non personnalisée</span><span class="sxs-lookup"><span data-stu-id="52db1-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="52db1-108">Les indicateurs de performances d’en-tête de réponse SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52db1-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="52db1-p101">Cette rubrique décrit comment utiliser chacune de ces méthodes pour diagnostiquer les problèmes de performances. Une fois que vous avez trouvé la cause du problème, vous pouvez toujours une solution à l’aide des articles sur l’amélioration des performances de SharePoint que vous trouverez sur http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="52db1-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="52db1-111">Utilisation de la barre d’outils F12 pour diagnostiquer les performances dans SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52db1-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="52db1-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52db1-112"></span></span>

<span data-ttu-id="52db1-p102">Dans cet article, nous utilisons Internet Explorer 11. Les versions des outils de développement F12 sur d’autres navigateurs ont des fonctionnalités similaires même si ceux-ci peuvent présenter de légères différences. Pour plus d’informations sur les outils de développement F12, voir :</span><span class="sxs-lookup"><span data-stu-id="52db1-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="52db1-116">Nouveautés dans les outils F12</span><span class="sxs-lookup"><span data-stu-id="52db1-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="52db1-117">L’utilisation des outils de développement F12</span><span class="sxs-lookup"><span data-stu-id="52db1-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="52db1-118">Pour faire apparaître les outils de développement, appuyez sur **F12**, puis cliquez sur l’icône Wi-Fi : 
</span><span class="sxs-lookup"><span data-stu-id="52db1-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Capture d’écran de l’icône Wi-Fi des outils de développement F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="52db1-p103">Sur l’onglet **Réseau**, appuyez sur le bouton de lecture vert pour charger une page. L’outil renvoie tous les fichiers que le navigateur demande afin d’obtenir la page que vous avez demandée. La capture d’écran suivante montre la liste.</span><span class="sxs-lookup"><span data-stu-id="52db1-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Capture d’écran de la liste de fichiers renvoyés avec une demande de page.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="52db1-124">Vous pouvez également afficher le temps de téléchargement des fichiers sur le côté droit, comme le montre cette capture d’écran.</span><span class="sxs-lookup"><span data-stu-id="52db1-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagramme montrant le temps nécessaire pour charger les pages demandées à partir de SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="52db1-p104">Vous obtenez ainsi une représentation visuelle de la durée de chargement du fichier. La ligne verte représente le moment auquel la page est prête à être affichée par le navigateur. Vous pouvez ainsi obtenir un aperçu rapide des différents fichiers susceptibles d’être à l’origine de la lenteur de chargement des pages sur votre site.

</span><span class="sxs-lookup"><span data-stu-id="52db1-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="52db1-129">Configuration d’une ligne de base non personnalisés pour SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52db1-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="52db1-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52db1-130"></span></span>

<span data-ttu-id="52db1-p105">La meilleure méthode pour déterminer les points faibles de performances de votre site consiste à configurer une collection de sites entièrement out-of-the-box dans SharePoint Online. De cette manière, vous pouvez comparer les différents aspects de votre site avec ce que vous obtenez sans personnalisation dans la page. La page d’accueil Business OneDrive est un bon exemple de collection de sites distincte qui n’est probablement pas avoir toutes les personnalisations.</span><span class="sxs-lookup"><span data-stu-id="52db1-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="52db1-134">Affichage des informations d’en-tête de réponse SharePoint</span><span class="sxs-lookup"><span data-stu-id="52db1-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="52db1-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52db1-135"></span></span>

<span data-ttu-id="52db1-p106">Dans SharePoint Online et SharePoint Server 2013, vous pouvez accéder aux informations qui sont renvoyées au navigateur dans l’en-tête de réponse pour chaque fichier. Pour diagnostiquer des problèmes de performances, les deux valeurs les plus utiles sont SPRequestDuration et X-SharePointHealthScore :</span><span class="sxs-lookup"><span data-stu-id="52db1-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="52db1-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="52db1-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="52db1-p107">Il s’agit de la durée de traitement de la demande sur le serveur. Cette valeur peut vous aider à déterminer si la demande est lourde et requiert beaucoup de ressources. Cette donnée est la meilleure information que vous pourrez obtenir sur la quantité de travail nécessaire au serveur pour fournir la page.</span><span class="sxs-lookup"><span data-stu-id="52db1-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="52db1-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="52db1-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="52db1-p108">Cela indique que l’utilisation du serveur, ou du processeur sur lequel s’exécute l’instance de SharePoint. Ce nombre compris entre 0 et 10, où 0 indique que le serveur est inactif et 10 indique le serveur est très occupé. Un score d’intégrité qui est toujours 9 ou 10 peut indiquer un problème de performances en cours avec le serveur. Toute autre valeur indique ce serveur fonctionne de la plage attendue.</span><span class="sxs-lookup"><span data-stu-id="52db1-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="52db1-147">**Affichage des informations d’en-tête de réponse SharePoint**</span><span class="sxs-lookup"><span data-stu-id="52db1-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="52db1-p109">Vérifiez que vous avez installés les outils F12. Pour plus d’informations sur le téléchargement et installation de ces outils, voir [Nouveautés d’outils F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="52db1-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="52db1-150">Dans les outils F12, sur l’onglet **Réseau**, appuyez sur le bouton lecture vert pour charger une page.</span><span class="sxs-lookup"><span data-stu-id="52db1-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="52db1-151">Cliquez sur l’un des fichiers .aspx renvoyés par l’outil, puis cliquez sur **DÉTAILS**.</span><span class="sxs-lookup"><span data-stu-id="52db1-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Affiche les détails de l’en-tête de réponse](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="52db1-153">Cliquez sur **En-têtes de réponse**.</span><span class="sxs-lookup"><span data-stu-id="52db1-153">Click **Response headers**.</span></span> 
    
    ![Diagramme présentant l’URL de l’en-tête de réponse](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="52db1-155">Quelle est la cause des problèmes de performances dans SharePoint Online ?</span><span class="sxs-lookup"><span data-stu-id="52db1-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="52db1-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="52db1-156"></span></span>

<span data-ttu-id="52db1-p110">L’article [options de Navigation de SharePoint Online](navigation-options-for-sharepoint-online.md) montre un exemple d’utilisation de la valeur SPRequestDuration pour déterminer que le volet de navigation structurelle complexe a été à l’origine de la page pour prendre beaucoup de temps à traiter sur le serveur. En optant pour une valeur pour un site de base (sans personnalisation), il est possible déterminer si un fichier donné prend beaucoup de temps à charger. L’exemple utilisé dans les [options de Navigation de SharePoint Online](navigation-options-for-sharepoint-online.md) est le fichier .aspx principale. Ce fichier contient la plupart du code qui s’exécute pour le chargement de la page ASP.NET. Selon le modèle de site que vous utilisez, il peut être start.aspx, home.aspx, default.aspx ou un autre nom si vous personnalisez la page d’accueil. Si ce numéro est considérablement plus élevé que votre site planifié, il est une bonne indication qu’il existe un élément complexe dans votre page, qui est à l’origine des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="52db1-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="52db1-p111">Une fois que vous avez identifié qu’il s’agit d’un problème propre à votre site, la méthode recommandée pour identifier l’origine de la médiocrité des performances consiste à éliminer toutes les causes possibles, telles que les personnalisations de page, et à les appliquer à nouveau au site une par une. Une fois que vous avez supprimé suffisamment de personnalisations et que la page présente de bonnes performances, vous pouvez les rajouter une par une.</span><span class="sxs-lookup"><span data-stu-id="52db1-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="52db1-p112">Par exemple, si vous disposez d’une navigation très complexe, essayez de modifier la navigation pour ne pas afficher les sous-sites, puis vérifiez dans les outils de développement pour déterminer si cette modification a eu un impact. Sinon, si vous disposez d’une grande quantité de regroupements de contenus, essayez de les supprimer de votre page et vérifiez si les performances s’améliorent. Si vous éliminez toutes les causes possibles, puis les rajoutez une à la fois, vous pouvez facilement identifier les fonctionnalités qui posent le plus problème, puis élaborer une solution. 
</span><span class="sxs-lookup"><span data-stu-id="52db1-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

