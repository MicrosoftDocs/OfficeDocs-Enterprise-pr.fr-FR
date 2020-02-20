---
title: Utiliser l’outil de diagnostics de page pour SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/18/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: Utilisez l’outil Diagnostics de la page pour SharePoint pour analyser le portail moderne SharePoint Online et les pages de publication classiques par rapport à un ensemble prédéfini de critères de performances.
ms.openlocfilehash: 191db3db459f12a922c47844af72511cc9bf2544
ms.sourcegitcommit: 27172140051c31f5cd3f28ffb4282669d561549a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42155590"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Utilisation de l’outil Diagnostics de la page pour SharePoint

Cet article explique comment utiliser l' **outil Diagnostics de la page pour SharePoint** afin d’analyser les pages de site classiques et modernes SharePoint Online par rapport à un ensemble prédéfini de critères de performances.  

>[!TIP]
>**La version 2.0.2 de l’outil a été publiée**. Version **2.0.0** et versions ultérieures inclut la prise en charge des pages modernes en plus des pages de site classiques. Si vous n’êtes pas sûr de la version de l’outil que vous utilisez, vous pouvez sélectionner le lien **à propos** de ou les points de suspension (...) pour vérifier votre version. Toujours effectuer la mise à jour vers la dernière version lors de l’utilisation de l’outil.

L’outil Diagnostics de la page pour SharePoint est une extension de navigateur pour les nouveauxhttps://www.microsoft.com/edge) navigateurs Microsoft Edge (et de chrome qui analysent à la fois les pages de site de publication classiques et de portail modernes SharePoint Online). Cet outil fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

L’outil génère un rapport pour chaque page analysée affichant le mode d’exécution de la page par rapport à un ensemble prédéfini de règles et affiche des informations détaillées lorsque les résultats d’un test se situent hors de la valeur de la ligne de base. Les administrateurs et les concepteurs SharePoint Online peuvent utiliser l’outil pour résoudre les problèmes de performances et pour s’assurer que les nouvelles pages sont optimisées avant la publication.

L’outil de diagnostic de page est conçu pour analyser uniquement les pages de site SharePoint, pas les pages système telles que *AllItems. aspx* ou *SharePoint. aspx*. Si vous tentez d’exécuter l’outil sur une page système ou sur une autre page qui n’est pas un site, vous recevrez un message d’erreur indiquant que l’outil ne peut pas être exécuté pour ce type de page.

![Doit s’exécuter sur une page SharePoint](media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Il ne s’agit pas d’une erreur dans l’outil, car il n’y a pas de valeur dans les bibliothèques ou les pages système. Pour utiliser l’outil, accédez à une page de site SharePoint. Si cette erreur se produit sur une page SharePoint, vérifiez la page maître pour vous assurer que les métabalises SharePoint n’ont pas été supprimées.

Pour fournir des commentaires à propos de l’outil, sélectionnez les points de suspension dans le coin supérieur droit de l’outil, puis sélectionnez [Envoyer des commentaires](https://go.microsoft.com/fwlink/?linkid=874109).

![Envoyer des commentaires](media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Installer l’outil Diagnostics de la page pour SharePoint

La procédure d’installation de cette section fonctionne pour les navigateurs Chrome et Microsoft Edge.

> [!IMPORTANT]
> Microsoft ne lit pas les données ou le contenu de la page qui est analysé par l’outil Diagnostics de la page pour SharePoint, et nous ne capturent aucune information personnelle, ni aucun site Web, ni aucune information sur le téléchargement. Les seules informations identifiables enregistrées à Microsoft par l’outil sont le nom du client, le nombre de règles ayant échoué et la date et l’heure d’exécution de l’outil. Ces informations sont utilisées par Microsoft pour mieux comprendre les tendances d’utilisation des sites portail et de publication modernes ainsi que les problèmes de performances courants.

1. Installez l’outil Diagnostics de la page pour SharePoint pour **Microsoft Edge** [(extension Edge)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) ou **chrome** [(extension chrome)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi). Consultez la stratégie de confidentialité de l’utilisateur indiquée sur la page Description du Store. Lorsque vous ajoutez l’outil à votre navigateur, vous verrez l’avis d’autorisations suivant.

    ![Autorisations d’extension](media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Cette notification est en place car une page peut contenir du contenu provenant d’emplacements extérieurs à SharePoint, en fonction des composants WebPart et des personnalisations sur la page. Cela signifie que l’outil lira les demandes et les réponses lorsque le bouton Démarrer est activé et uniquement pour l’onglet SharePoint actif dans lequel l’outil est exécuté. Ces informations sont capturées localement par le navigateur Web et sont disponibles via le bouton **Exporter vers JSON** ou **Exporter vers** la bibliothèque de sites Web dans l’onglet _suivi du réseau_ de l’outil. **les informations ne sont ni envoyées ni capturées par Microsoft.** (L’outil respecte la politique de confidentialité de Microsoft accessible [ici](https://go.microsoft.com/fwlink/p/?linkid=857875).)

    L’autorisation _gérer vos téléchargements_ couvre l’utilisation de la fonctionnalité **exportation vers JSON** de l’outil. Suivez les instructions de confidentialité de votre entreprise avant de partager le fichier JSON en dehors de votre organisation, car les résultats contiennent des URL et peuvent être classés en tant que données personnelles (informations d’identification personnelle).
1. Si vous souhaitez utiliser l’outil dans incognito ou le mode InPrivate, suivez la procédure pour votre navigateur :
    1. Dans Microsoft Edge, accédez à **Extensions** ou tapez _Edge://extensions_ dans la barre d’URL et sélectionnez **Détails** pour l’extension. Dans les paramètres d’extension, activez la case à cocher **autoriser dans InPrivate**.
    1. Dans Chrome, accédez à **Extensions** ou tapez _chrome://extensions_ dans la barre d’URL et sélectionnez **Détails** pour l’extension. Dans les paramètres d’extension, sélectionnez le curseur pour **autoriser dans incognito**.
1. Accédez à la page du site SharePoint sur SharePoint Online que vous souhaitez consulter. Nous avons autorisé le chargement différé des éléments sur les pages ; par conséquent, l’outil ne s’arrêtera pas automatiquement (Ceci est par conception pour prendre en compte tous les scénarios de chargement de page). Pour arrêter la collection, sélectionnez **arrêter**. Assurez-vous que le chargement de la page est terminé avant d’arrêter la collecte de données ou que vous ne capturerez qu’une trace partielle.
1. Cliquez sur le bouton de la barre d’outils de l’extension ![Diagnostics de page pour le logo SharePoint](media/page-diagnostics-for-spo/pagediag-icon32.png) pour charger l’outil, le menu contextuel d’extension suivant s’affiche :

    ![Menu contextuel de l’outil Diagnostics de page](media/page-diagnostics-for-spo/pagediag-Landing.png)

Sélectionnez **Démarrer** pour commencer à collecter des données pour analyse.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Éléments que vous verrez dans l’outil Diagnostics de la page pour SharePoint

1. Cliquez sur les points de suspension (...) dans le coin supérieur droit de l’outil pour trouver les liens suivants :
   1. Le lien **ressources supplémentaires** fournit des instructions et des informations générales sur l’outil, y compris un lien vers cet article.
   1. Le lien **Envoyer des commentaires** fournit un lien vers les _sites SharePoint et_ le site d’utilisateur de collaboration.
   1. Le lien **à propos** inclut la version actuellement installée de l’outil, ainsi qu’un lien direct vers l’avertissement tiers de l’outil.  
1. L' **ID de corrélation, SPRequestDuration, SPIISLatency**, le **temps de chargement**de la page et les détails de l' **URL** sont des informations d’information et peuvent être utilisés à quelques fins.

    ![Détails des diagnostics de la page](media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationId** est un élément important lorsque vous travaillez avec le support Microsoft, car il lui permet de recueillir des données de diagnostic supplémentaires pour la page spécifique.
   - **SPRequestDuration** est le temps nécessaire pour que SharePoint traite la page. La navigation structurelle, les grandes images, de nombreux appels d’API, peuvent contribuer à des durées plus longues.
   - **SPIISLatency** est le temps en millisecondes nécessaire pour SharePoint Online commencer à charger la page. Cette valeur n’inclut pas le temps nécessaire à l’application Web pour répondre.
   - Le temps de chargement de la **page** est la durée totale enregistrée par la page entre le moment de la demande et le moment où la réponse a été reçue et affichée dans le navigateur. Cette valeur est affectée par divers facteurs, notamment la latence du réseau, les performances de l’ordinateur et le temps nécessaire pour que le navigateur charge la page.
   - L' **URL** de la page (Uniform Resource Locator) est l’adresse Web de la page active.

1. L’onglet [**tests de diagnostic**](#how-to-use-the-diagnostic-tests-tab) affiche les résultats de l’analyse en trois catégories ; **Aucune action requise**, **amélioration des opportunités** et **intervention requise**. Chaque résultat de test est représenté par un élément dans l’une de ces catégories, comme décrit dans le tableau suivant :

    |Catégorie  |Couleur  |Description  |
    |---------|---------|---------|
    |**Attention requise** |Rouge |Le résultat des tests se situe en dehors de la valeur de la ligne de base et affecte les performances de la page. Suivez les instructions de correction.|
    |**Opportunités d’amélioration** |Jaune |Le résultat des tests se situe en dehors de la valeur de base et peut contribuer aux problèmes de performances. Des critères spécifiques au test peuvent s’appliquer.|
    |**Aucune action n'est requise** |Vert |Le résultat des tests s’inscrit dans la valeur de base du test.|

    ![Diagnostics de page](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Un onglet [**suivi du réseau**](#how-to-use-the-network-trace-tab) fournit des détails sur les demandes et les réponses de création de page.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Utilisation de l’onglet tests de diagnostic

Lorsque vous analysez une page de portail moderne SharePoint ou une page de site de publication classique avec l’outil Diagnostics de la page pour SharePoint, les résultats sont analysés à l’aide de règles prédéfinies qui comparent les résultats par rapport aux valeurs de référence et s’affichent sous l’onglet **tests de diagnostic** . les règles de certains tests peuvent utiliser des valeurs de base différentes pour les sites de

Les résultats des tests qui apparaissent dans les catégories **opportunités d’amélioration** ou **attention requise** indiquent les domaines qui doivent être examinés par rapport aux pratiques recommandées et peuvent être sélectionnés pour afficher des informations supplémentaires sur le résultat. Les détails de chaque élément incluent un lien _en savoir plus_ , qui vous permet d’accéder directement aux conseils appropriés liés au test. Les résultats des tests qui apparaissent dans la catégorie **aucune action requise** indiquent la conformité avec la règle appropriée et n’affichent pas de détails supplémentaires lorsqu’ils sont sélectionnés.

Les informations de l’onglet tests de diagnostics ne vous indiquent pas comment concevoir des pages, mais ils mettent en surbrillance les facteurs susceptibles d’influer sur les performances des pages. La fonctionnalité de page et les personnalisations ont un impact inévitable sur les performances de la page et doivent être vérifiées pour permettre une correction potentielle ou une omission de la page si leur impact est substantiel.

Les résultats rouges ou jaunes peuvent également indiquer des composants WebPart qui actualisent les données trop fréquemment. Par exemple, les informations d’entreprise ne sont pas mises à jour tous les deux, mais les composants WebPart personnalisés sont souvent conçus pour extraire les dernières actualités toutes les secondes, au lieu d’implémenter des éléments de mise en cache qui pourraient améliorer l’expérience globale de l’utilisateur. N’oubliez pas que lorsque vous incluez des composants WebPart sur une page, il existe souvent des moyens simples de réduire leur impact sur les performances en évaluant la valeur de chaque paramètre disponible afin de s’assurer qu’il est correctement défini pour son objectif.

>[!NOTE]
>Les sites d’équipe classiques pour lesquels la fonctionnalité de publication n’est pas activée ne peuvent pas utiliser CDN. Lorsque vous exécutez l’outil sur ces sites, le test de CDN doit échouer et être ignoré, mais tous les autres tests sont applicables. Les fonctionnalités supplémentaires de la fonctionnalité de publication SharePoint pouvant augmenter le temps de chargement de la page, il ne doit pas être activé uniquement pour autoriser la fonctionnalité CDN.

>[!IMPORTANT]
>Les règles de test sont ajoutées et mises à jour régulièrement, reportez-vous à la dernière version de l’outil pour obtenir des détails sur les règles actuelles et des informations spécifiques incluses dans les résultats des tests. Vous pouvez vérifier la version en gérant vos extensions et l’extension indique si une mise à jour est disponible.

## <a name="how-to-use-the-network-trace-tab"></a>Utilisation de l’onglet suivi du réseau

L’onglet **suivi du réseau** fournit des informations détaillées sur les deux demandes de création de la page et les réponses reçues à partir de SharePoint.

1. **Recherchez les temps de chargement des éléments marqués en rouge**. Chaque requête et réponse est codée en couleurs pour indiquer son impact sur les performances globales de la page à l’aide des mesures de latence suivantes :
    - Vert : \< 500 m
    - Jaune : 500-1000MD
    - Rouge : \> 1000MD

    ![Suivi réseau](media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    Dans l’image illustrée ci-dessus, l’élément rouge est lié à la page par défaut. Elle s’affiche toujours en rouge, sauf si la \< page se charge dans les 1000MD (moins de 1 seconde).

2. **Temps de chargement des éléments de test**. Dans certains cas, il n’y aura pas d’indicateur d’heure ou de couleur, car les éléments ont déjà été mis en cache par le navigateur. Pour tester ce problème correctement, ouvrez la page, effacez le cache du navigateur, puis cliquez sur **Démarrer** , car cela entraînera un chargement de page « froid » et sera une véritable réflexion du chargement de page initial. Cela doit ensuite être comparé à la charge de page « chaude » car cela permettra également de déterminer les éléments mis en cache sur la page.

3. **Partagez des informations pertinentes avec d’autres personnes qui peuvent vous aider à identifier les problèmes**. Pour partager les détails ou les informations fournis dans l’outil avec vos développeurs ou une personne du support technique, cliquez sur **Exporter vers JSON** (comme illustré dans l’image ci-dessus). Cela vous permettra de télécharger les résultats, affichables avec une visionneuse de fichiers JSON.

    Si vous avez choisi d’utiliser la fonctionnalité aperçu *activer l’exportation vers* la version QAR, le type d’exportation s’affiche sous la forme **exportation vers**la version QAR.

    ![Suivi réseau](media/page-diagnostics-for-spo/pagediag-NetworkTraceHAR.PNG)

> [!IMPORTANT]
> Ces résultats contiennent des URL qui peuvent être classées en tant que données personnelles (informations d’identification personnelle). Veillez à suivre les instructions de votre organisation avant de distribuer ces informations.

## <a name="engaging-with-microsoft-support"></a>Engagement avec le support Microsoft

Nous avons inclus une **fonctionnalité de niveau de support Microsoft** qui doit être utilisée uniquement lorsque vous travaillez directement sur un cas de support. L’utilisation de cette fonctionnalité n’offre aucun avantage lorsque vous l’utilisez sans intervention de l’équipe de support et que la page peut s’exécuter beaucoup plus lentement. Il n’existe pas d’informations supplémentaires lors de l’utilisation de cette fonctionnalité dans l’outil, car les informations supplémentaires sont ajoutées à la journalisation dans le service.

Aucune modification n’est visible sauf si vous êtes informé que vous l’avez activé et que les performances de votre page seront considérablement dégradées de 2-3 fois la vitesse de fonctionnement et la vitesse d’activation. Il ne s’applique qu’à la page particulière et à la session active. Pour cette raison, elle doit être utilisée avec parcimonie et uniquement lorsque la prise en charge est activement engagée.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Pour activer la fonctionnalité niveau de support Microsoft

1. Ouvrez l’outil Diagnostics de la page pour SharePoint.
2. Sur votre clavier, appuyez sur **Alt-Maj-b**. Cette opération affiche la case à cocher **activer la journalisation** de l’assistance.
3. Activez la case à cocher, puis cliquez sur **Démarrer** pour recharger la page et générer une journalisation détaillée.

    ![Option de prise en charge activée](media/page-diagnostics-for-spo/pagediag-support.png)
  
    Notez le CorrelationID (affiché en haut de l’outil) et fournissez-le à votre représentant du support technique pour lui permettre de recueillir des informations supplémentaires sur la session de diagnostic.

## <a name="related-topics"></a>Voir aussi

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)
