---
title: Utiliser l’outil de diagnostics de page pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Utilisez l’outil Diagnostics de la page pour SharePoint pour analyser vos pages classiques par rapport aux meilleures pratiques recommandées pour SharePoint Online.
ms.openlocfilehash: a188b5dbe52a92cd536ef7145534288345b74c22
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069510"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utiliser l’outil de diagnostics de page pour SharePoint Online

Cet article explique comment utiliser l’outil de diagnostic de page pour analyser vos pages et pages de publication classiques sur des sites d’équipe classiques, par rapport à un sous-ensemble de pratiques recommandées dans **SharePoint Online**. 
  
Les sites d’équipe pour lesquels la publication n’est pas activée ne peuvent pas utiliser CDN, mais toutes les règles restantes sont applicables. La publication ajoute une charge supplémentaire: n’activez pas la publication uniquement pour obtenir la fonctionnalité CDN car elle aura un impact négatif sur les temps de chargement des pages.

**Veuillez noter que v 1.05 a été publié afin de mettre à jour votre extension si elle est déjà installée**. Si vous ne savez pas quelle version vous avez, cliquez sur le lien «à propos de» pour la vérifier.
  
> [!IMPORTANT]
> L’outil Diagnostics de page ne s’exécute pas sur les bibliothèques de documents ou les pages système, car l’outil est conçu pour examiner les pages de site SharePoint. Une page *AllItems. aspx* est une page système. Si vous tentez d’exécuter l’outil sur une page système, vous obtiendrez un message indiquant «cette application doit être exécutée que sur des pages SharePoint.» <br/> ![Doit s’exécuter sur une page SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Il ne s’agit pas d’une erreur dans l’outil, car il n’y a pas de valeur dans les bibliothèques ou les pages système. Pour utiliser l’outil, accédez à une page SharePoint non-système. Si cela se produit sur une page SharePoint, vérifiez le MasterPage car nous avons vu que les clients ont consulté les balises meta SharePoint, puis la page n’est plus une page SharePoint. Si vous souhaitez envoyer des commentaires à propos de l’outil, cliquez sur l’onglet à propos de et suivez le [lien donner des commentaires](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installer l’outil de diagnostic de la page

> [!IMPORTANT]
> Microsoft ne lit pas les données ou sites Web que vous visitez, et nous ne recueillons aucune information personnelle, ni de site Web, ni de téléchargement d’informations avec cet outil. Les seules informations consignées par l’outil sont le nom du client, le nombre de règles et l’option indiquant si l’option de journalisation de la prise en charge a été utilisée lors de l’exécution de l’outil. Ces informations sont destinées à Microsoft pour analyser les défis rencontrés par nos clients et pour s’assurer que la fonctionnalité de journalisation du support n’est pas utilisée à des fins d’utilisation.

1. À l’aide d’un navigateur Chrome, ouvrez le [lien vers l’outil](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) directement ou ouvrez la recherche dans le [navigateur Chrome Webstore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) et installez l’extension du navigateur. Consultez la stratégie de confidentialité de l’utilisateur indiquée sur la page Description du Store. Lorsque vous ajoutez l’outil à votre navigateur, vous verrez l’avis d’autorisations suivant.<br/>![Autorisations du magasin chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Cette notification est en place car une page peut contenir du contenu provenant d’emplacements extérieurs à SharePoint, en fonction des composants WebPart et des personnalisations de la page. Cela signifie que l’outil lira les demandes et les réponses lorsque le bouton Démarrer est activé et uniquement pour l’onglet SharePoint actif dans lequel l’outil est exécuté. Ces informations sont capturées localement par le navigateur Web et sont disponibles via le lien exporter vers JSON de l’outil. **Les informations ne sont ni envoyées ni capturées par Microsoft.** (L’outil respecte la politique de confidentialité de Microsoft accessible [ici](https://go.microsoft.com/fwlink/p/?linkid=857875).)<br/><br/>La fonctionnalité «exporter vers JSON» de l’outil explique également pourquoi l’autorisation «gérer vos téléchargements» est nécessaire. Suivez les instructions de confidentialité de votre entreprise avant de partager le fichier JSON en dehors de votre organisation, car les résultats contiennent des URL et peuvent être classés en tant que données personnelles (informations d’identification personnelle).
    
2. (Cette option est facultative) Si vous souhaitez utiliser l’outil en mode Incognito chrome, accédez à l’extension et cliquez sur **autoriser dans incognito**.
    
3. Accédez à la page de publication SharePoint classique sur SharePoint Online que vous souhaitez consulter. Nous avons autorisé le chargement différé des éléments sur les pages; par conséquent, l' **outil ne s’arrêtera pas automatiquement**. Si vous souhaitez arrêter la collection, vous pouvez cliquer sur **arrêter**. (Cette méthode est conçue pour répondre à tous les scénarios de chargement de pages.) Avant de cliquer sur **arrêter**, assurez-vous que les données de suivi réseau sont complètes. Dans le cas contraire, vous aurez un suivi partiel. En outre, l’outil est une extension de navigateur et l’ouverture de plusieurs onglets ou fenêtres n’autorise qu’une seule instance active de l’outil à être exécutée à la fois. Il s’agit d’une limitation des extensions dans le navigateur. 
  
4. Cliquez sur le logo de l’extension. ![Diagnostics de page pour le logo SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) pour charger l’outil, le menu contextuel d’extension suivant s’affiche:<br/> ![Menu contextuel de l’outil Diagnostics de page](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Les opérations de démarrage et d’arrêt suivent le concept de base de lorsque vous cliquez sur Démarrer la page se recharge et la collecte commence.

Pour en savoir plus sur les informations fournies dans l’outil, consultez les sections suivantes.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Ce que vous verrez dans l’outil de diagnostics de page
    
1. Le lien **à propos** fournit des instructions générales et des détails relatifs à l’outil, y compris un lien vers cet article. Il inclut également un lien direct vers les recommandations de performances de SharePoint, une notification tierce et une option pour fournir des commentaires sur l’outil. 
    
2. L' **ID de corrélation, SPRequestDuration, SPIISLatency**, le **temps de chargement**de la page et les détails de l' **URL** sont des informations d’information et peuvent être utilisés à quelques fins. 
    
  - **CorrelationId** est un élément important lorsque vous travaillez avec les équipes de support technique Microsoft, car cela leur permet d’extraire des données de diagnostic supplémentaires. 
    
  - **SPRequestDuration** est le temps du serveur utilisé pour traiter la page. Si ce délai est long, cela ne signifie pas nécessairement que le serveur était exécuté de façon incorrecte, mais qu’il peut également refléter le nombre d’appels et de charge envoyés par la page au serveur (par exemple, la navigation structurelle, les grandes images, un grand nombre d’appels d’API, tout en contribuant à des temps de serveur plus longs). . 
    
  - **SPIISLatency** est le temps en millisecondes qui s’est écoulé sur le serveur Web frontal lorsqu’il reçoit la demande de chargement de la page. Il s’agit d’un indicateur de latence pour démarrer le traitement de la page et n’inclut pas le temps nécessaire à l’application Web pour répondre. 
    
  - Le temps de chargement de la **page** est le temps enregistré par la page entre le moment de la demande et le moment où la réponse a été reçue et lue par le navigateur. Tout temps supplémentaire est affecté par les performances de l’ordinateur et le temps nécessaire au chargement du navigateur. 
    
  - L' **URL** (Uniform Resource Locator) est l’adresse Web de la page active. 
    
3. L' [onglet **diagnostic** ](#how-to-use-the-diagnostic-tab) répertorie les règles et, si elles sont marquées par une croix ![](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)rouge, si des problèmes sont identifiés sur la page.<br/>Chaque règle dispose de son propre lien «plus d’informations» sur lequel vous cliquez si un élément est rouge. Cela vous permettra de suivre les détails de cette règle et de résoudre le problème.<br/>![Diagnostics rouge-règle ouverte](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Un [onglet **suivi du réseau** ](#how-to-use-the-network-trace-tab) fournit des détails sur les demandes et les réponses de création de page.

## <a name="how-to-use-the-diagnostic-tab"></a>Utilisation de l’onglet Diagnostics

1. **Vérifier l’exécution en tant qu’utilisateur standard**  La vérification des performances de page ne doit pas être effectuée lorsque vous êtes connecté en tant que compte de service, administrateur ou administrateur de collection de sites, ou tout compte avec des privilèges élevés. Des scripts et fonctionnalités supplémentaires sont chargés spécifiquement pour ces types de comptes, de sorte que les résultats ne seront pas une représentation véritable des performances des pages.
    
2. **Vérifier les demandes vers SharePoint**  La quantité de données et de demandes adressées au serveur doit être limitée car une page surchargée présente des performances médiocres. Cette vérification vérifie le nombre de demandes adressées à SharePoint et indique quand les demandes dépassent 6 demandes. La plupart des demandes doivent être mises en cache et par conséquent pas appelées pour chaque chargement de page. Le cache doit être configuré et utilisé pendant au moins 15 minutes pour réduire le nombre d’appels vers une page par chaque utilisateur. Il s’agit d’un problème courant et, dans la plupart des cas, les données ne changent que tous les jours, mais la page vérifie et extrait les données chaque fois pour chaque page, ce qui est souvent inutile.
    
3. **Vérifier à l’aide de CDN**  Les réseaux de distribution de contenu (CDN) ont été fournis par Microsoft et ceux qui sont mentionnés ici sont les réseaux de distribution de contenu SharePoint Online. Plusieurs types sont disponibles, ainsi que différents services de CDN tels que SharePoint CDN, puis CDN dans Azure. [Utilisez les instructions suivantes](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Vérifier les tailles d’image volumineuses**  Les images doivent être optimisées pour le Web en utilisant des types de Web plus efficaces comme PNG. Les rendus d’image doivent également être utilisés et disponibles directement dans SharePoint. Les images/rendus d’image dont la taille est supérieure à 100Ko sont mis en surbrillance comme non optimisés pour le Web. [Utilisez les conseils suivants pour optimiser les images](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Vérifier la navigation structurelle**  La navigation structurelle a été conçue à l’origine pour une utilisation dans SharePoint sur site où le cache d’objets pouvait être utilisé. La navigation structurelle n’est pas recommandée pour une utilisation dans SharePoint Online et doit être remplacée par la navigation gérée ou un fournisseur personnalisé. [Utilisez les conseils suivants pour optimiser la navigation.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Vérifier le composant WebPart CBQ** (CBQ-contenu par composant WebPart de requête)  Le composant WebPart contenu par requête génère une charge SQL élevée lorsqu’il parcourt tous les éléments de la requête pour chaque charge de page, pour chaque utilisateur. Contrairement à une installation locale, il n’existe pas de cache disponible pour limiter le nombre de requêtes nécessaires au remplissage de ce composant WebPart. Comme ce CBQ s’exécute lentement et influe sur les performances globales de la page, c’est pourquoi il ne doit pas être utilisé. Utilisez le composant WebPart recherche de contenu (composant WebPart recherche) pour remplacer le composant WebPart de requête de contenu. [Utilisez les instructions suivantes relatives au composant WebPart recherche de contenu](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Utilisation de l’onglet suivi du réseau
    
L’onglet **suivi du réseau** fournit des informations détaillées sur les demandes de création de la page, ainsi que sur les réponses reçues. 

1. **Recherchez les temps de chargement des éléments marqués en rouge**. Les performances de chaque demande et réponse sont codées par couleur, en fonction de leur impact sur les performances globales de la page, comme suit:
- Vert: \< 500 m
- Jaune: 500-1000MD
- Rouge: \> 1000MD
<br/>![Suivi réseau](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> Dans l’image illustrée ci-dessus, l’élément rouge est lié à la page par défaut. Elle s’affiche toujours en rouge, sauf si la \< page se charge dans les 1000MD (moins de 1 seconde).

2. **Temps de chargement des éléments de test**. Dans certains cas, il n’y aura pas d’indicateur d’heure ou de couleur, car les éléments ont déjà été mis en cache par le navigateur. Pour tester ce problème correctement, ouvrez la page, effacez le cache du navigateur, puis cliquez sur **Démarrer** , car cela entraînera un chargement de page «froid» et sera une véritable réflexion du chargement de page initial. Cela doit ensuite être comparé à la charge de page «chaude» car cela permettra également de déterminer les éléments mis en cache sur la page. 
    
3. **Partagez des informations pertinentes avec d’autres personnes qui peuvent vous aider à identifier les problèmes**. Pour partager les détails ou les informations fournis dans l’outil avec vos développeurs ou une personne du support technique, cliquez sur **Exporter vers JSON** (comme illustré dans l’image ci-dessus). Cela vous permettra de télécharger les résultats, affichables avec une visionneuse de fichiers JSON.

> [!IMPORTANT]
> Ces résultats contiennent des URL qui peuvent être classées en tant que données personnelles (informations d’identification personnelle). Veillez à suivre les instructions de votre organisation avant de distribuer ces informations. 

## <a name="engaging-with-microsoft-support"></a>Engagement avec le support Microsoft
   
Nous avons inclus une **fonctionnalité de niveau de support Microsoft** qui doit être utilisée uniquement lorsque vous travaillez directement sur un cas de support technique. L’utilisation de cette fonctionnalité ne vous permettra pas si elle est utilisée sans notre équipe de support technique. Cela fera en sorte que la page s’exécute beaucoup plus lentement et que l’utilisation continue de la fonctionnalité peut être considérée comme une «mauvaise utilisation» du service. Il n’existe pas d’informations supplémentaires lors de l’utilisation de cette fonctionnalité dans l’outil, car les informations supplémentaires sont ajoutées à la journalisation dans le service. 

Aucune modification n’est visible sauf si vous êtes informé que vous l’avez activé et que les performances de votre page seront considérablement dégradées de 2-3 fois la vitesse de fonctionnement, tandis que l’option est activée. Il ne s’applique qu’à la page particulière et à la session active. Pour cette raison, vous devez l’utiliser avec parcimonie et uniquement lorsque vous participez activement à notre équipe de support technique.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Pour activer la fonctionnalité niveau de support Microsoft

1. Ouvrez l’outil Diagnostics de la page.
2. Sur votre clavier, appuyez sur ALT-MAJ-B. Cette opération permet d’afficher la journalisation du **niveau de prise en charge**. 
3. Activez la case à cocher, puis cliquez sur **Démarrer** pour recharger la page et générer une journalisation détaillée pour la prise en charge de l’analyse.<br/>![Option de prise en charge activée](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un élément important pour cette opération est l’CorrelationID, car l’équipe de support technique utilisera ce numéro pour extraire les informations nécessaires. Veuillez copier le CorrelationID (en haut de l’outil de diagnostics de page) et fournissez-lui la prise en charge car ils ne peuvent pas effectuer le travail requis sans l’ID complet.
    
## <a name="related-topics"></a>Sujets associés

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)
