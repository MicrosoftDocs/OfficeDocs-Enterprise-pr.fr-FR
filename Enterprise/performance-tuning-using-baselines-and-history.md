---
title: Optimisation des performances d’Office 365 à l’aide de lignes de référence et de l’historique des performances
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
description: Il existe quelques méthodes simples pour vérifier les performances de connexion entre Office 365 et votre entreprise qui vous permettra d’établir une base approximative de votre connectivité. Connaître l’historique des performances des connexions de vos ordinateurs client peut vous aider à détecter rapidement les problèmes émergents, à identifier et à prédire les problèmes.
ms.openlocfilehash: a399cb0057e9cc62e180fea8a6d7b9dbf1993a5f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069520"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Optimisation des performances d’Office 365 à l’aide de lignes de référence et de l’historique des performances

Il existe quelques méthodes simples pour vérifier les performances de connexion entre Office 365 et votre entreprise qui vous permettra d’établir une base approximative de votre connectivité. Connaître l’historique des performances des connexions de vos ordinateurs client peut vous aider à détecter rapidement les problèmes émergents, à identifier et à prédire les problèmes.
  
Si vous n’êtes pas utilisé pour traiter les problèmes de performances, cet article est conçu pour vous aider à prendre en compte certaines questions courantes, par exemple, comment savoir que le problème que vous rencontrez est un problème de performances et non un incident de service Office 365? Comment pouvez-vous planifier de bonnes performances? Comment pouvez-vous garder un œil sur les performances? Si votre équipe ou vos clients voient le ralentissement des performances lors de l’utilisation d’Office 365 et que vous vous posez des questions sur l’une de ces questions, lisez la suite.
  
> [!IMPORTANT]
> **Vous avez un problème de performances entre votre client et Office 365?** Suivez les étapes décrites dans le [plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Ce que vous devez savoir sur les performances d’Office 365

Office 365 se trouve à l’intérieur d’un réseau Microsoft dédié haute capacité, qui est régulièrement surveillé non seulement par Automation, mais par des personnes réelles. Une partie du rôle de la maintenance du nuage Office 365 est la création d’un réglage des performances et la rationalisation de l’emplacement où il est possible. Étant donné que les clients du nuage Office 365 doivent se connecter sur Internet, il existe un effort continu pour ajuster les performances dans les services Office 365. Les améliorations de performances ne s’arrêtent jamais dans le Cloud, et il existe un grand nombre d’expériences accumulées pour que le Cloud soit sain et rapide. Si vous êtes confronté à un problème de performances lié à la connexion de votre emplacement à Office 365, il est préférable de ne pas commencer par un cas de support technique et d’attendre. Au lieu de cela, vous devez commencer à étudier le problème à partir de «The Inside Out». En d’autres termes, démarrez votre réseau et travaillez dans Office 365. Avant d’ouvrir un cas avec la prise en charge d’Office 365, vous pouvez recueillir des données et prendre des mesures qui exploreront et pourront résoudre votre problème.
  
> [!IMPORTANT]
> Tenez compte de la planification de la capacité et des limites dans Office 365. Ces informations vous feront avancer de la courbe lors de la tentative de résolution d’un problème de performances. Voici un lien vers la [Description du service de plateforme Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Il s’agit d’un concentrateur central, et tous les services offerts par Office 365 disposent d’un lien qui permet d’accéder à leurs propres descriptions de service. Cela signifie que, si vous avez besoin de voir les limites standard pour SharePoint Online, par exemple, vous devez cliquer sur [Description du service SharePoint Online](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) et localiser sa [section limites de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkID=856113). 
  
Assurez-vous que vous êtes au fait de votre dépannage, sachant que les performances sont une mise à l’horizontale, il ne s’agit pas d’obtenir une valeur idéale et de la maintenir définitivement (si vous pensez qu’il s’agit ainsi, des tâches de bande passante exceptionnelles telles que l’embarquement d’un un grand nombre d’utilisateurs ou des migrations de données volumineuses seront très exigeants, c’est pourquoi nous allons planifier l’impact sur les performances. Vous pouvez et, si vous avez une idée approximative de vos objectifs de performances, mais que de nombreuses variables sont lues en matière de performances, par conséquent, les performances varient. Il s’agit de la nature des performances. 
  
La résolution des problèmes liés aux performances ne concerne pas la réunion de objectifs spécifiques ni la conservation de ces numéros indéfiniment, il s’agit de l’amélioration des activités existantes, étant donné toutes les variables. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>OK, à quoi ressemble un problème de performances?

Tout d’abord, vous devez vous assurer que ce que vous rencontrez est effectivement un problème de performances et non un incident de service. Un problème de performances est différent d’un incident de service dans Office 365. Voici comment les distinguer.
  
Si le service Office 365 rencontre des problèmes, il s’agit d’un incident de service. Des icônes rouges ou jaunes s’affichent sous **intégrité actuelle** dans le centre d’administration Office 365, vous pouvez également remarquer les performances de ralentissement sur les ordinateurs clients qui se connectent à Office 365. Par exemple, si l’intégrité actuelle signale une icône rouge et que vous voyez une **enquête** à côté d’Exchange, vous pouvez également recevoir des appels de personnes de votre organisation qui se plaignent que les boîtes aux lettres clientes qui utilisent Exchange Online ne fonctionnent pas correctement. Dans ce cas, il est raisonnable de supposer que vos performances Exchange Online sont devenues une victime de problèmes au sein du service. 
  
![Le tableau de bord d’intégrité Office 365 avec toutes les charges de travail qui affichent le vert, à l’exception d’Exchange, qui affiche le service restauré.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
À ce stade, l’administrateur Office 365 doit vérifier l' **intégrité actuelle** , puis afficher les **Détails et l’historique**, fréquemment, pour tenir à jour la maintenance que nous effectuons sur le système. Le tableau de bord d' **intégrité actuel** a été créé pour vous mettre à jour à propos des modifications apportées au service. Les notes et les explications écrites dans l’histoire de l’intégrité, administrateur et administrateur, sont là pour vous aider à évaluer votre impact et à vous tenir informé du travail en cours. 
  
![Image du tableau de bord d’intégrité Office 365 expliquant que le service Exchange Online a été restauré et pourquoi.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Un problème de performances n’est pas un incident de service, même si les incidents peuvent entraîner un ralentissement des performances. Un problème de performances se présente comme suit:
  
- Un problème de performances survient quelle que soit la fonctionnalité **actuelle** du centre d’administration Office 365 pour le service. 
    
-  Un comportement dont l’utilisation est relativement transparente prend beaucoup de temps ou ne se termine pas. 
    
- Vous pouvez également répliquer le problème ou, au moins, vous savez qu’il se produit si vous effectuez la bonne série d’étapes.
    
-  Si le problème est intermittent, il existe toujours un modèle, par exemple, si vous êtes conscient que par 10:00 AM, vous aurez des appels d’utilisateurs qui ne peuvent pas accéder de manière fiable à Office 365 et que les appels seront réparties en midi. 
    
Cela vous paraît probablement familier; peut-être trop familier. Une fois que vous avez déterminé qu’il s’agit d’un problème de performances, la question devient «que faire maintenant?». Le reste de cet article vous aide à déterminer exactement cela.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Procédure de définition et de test du problème de performances

Les problèmes de performances apparaissent souvent au fil du temps, c’est pourquoi il peut être difficile de définir le problème réel. Vous devez créer une bonne déclaration de problème et une bonne idée du contexte du problème, puis vous devez répéter les étapes de test pour remporter la journée. Dans le cas contraire, il se peut que vous perdiez votre propre faute. Pourquoi ? Voici quelques exemples d’instructions de problèmes qui ne fournissent pas suffisamment d’informations:
  
- Passer de ma boîte de réception à mon calendrier était une information que je ne savais pas et il s’agit maintenant d’un «café». Pouvez-vous le faire fonctionner comme s’il l’était?
    
- Le téléchargement de mes fichiers vers SharePoint Online prend un temps illimité. Pourquoi est-il lent pendant l’après-midi, mais à tout autre moment, c’est rapide? Est-il possible de se faire rapidement?
    
Les relevés des problèmes ci-dessus présentent plusieurs grands défis. Plus précisément, il existe de nombreuses ambiguïtés à prendre en compte. par exemple :
  
- Il n’est pas évident de savoir comment basculer entre la boîte de réception et le calendrier pour agir sur l’ordinateur portable.
    
- Lorsque l’utilisateur dit «ne peut pas être rapide», quel est le «rapide»?
    
- Quelle est la durée de «forevation»? Est-ce que plusieurs secondes ou quelques minutes, ou l’utilisateur peut aller déjeuner, est-il terminé dix minutes après que l’utilisateur a été renvoyé?
    
Tout ceci est sans que l’administrateur et l’utilitaire de résolution des problèmes ne soient conscients de nombreux détails des instructions problématiques comme celles-ci. Par exemple, lorsque le problème se produit; Que l’utilisateur travaille de chez vous et ne voit qu’une commutation lente pendant qu’il se trouve sur un réseau domestique; L’utilisateur doit exécuter plusieurs autres applications gourmandes en mémoire vive sur le client local, ou l’utilisateur exécute un ancien système d’exploitation ou n’a pas exécuté de mises à jour récentes.
  
Lorsque les utilisateurs signalent un problème de performances, il y a beaucoup d’informations à collecter. La collecte de ces informations fait partie d’un processus appelé portée du problème ou enquête. Vous trouverez ci-dessous une liste de portée de base que vous pouvez utiliser pour collecter des informations sur votre problème de performances. Cette liste n’est pas exhaustive, mais elle vous permet de commencer l’une des opérations suivantes: 
  
- Quelle est la date à laquelle le problème s’est produit et l’heure de la journée ou de la nuit?
    
- Quel type d’ordinateur client utilisez-vous et comment se connecte-t-il au réseau d’entreprise (VPN, filaire, sans fil)?
    
- Vous travailliez à distance ou êtes-vous au bureau?
    
- Avez-vous essayé les mêmes actions sur un autre ordinateur et observez-vous le même comportement?
    
- Passez en revue les étapes qui vous permettent d’écrire les actions que vous rencontrez.
    
- Dans quelle mesure les performances sont-elles lentes en secondes ou minutes?
    
- Où se trouve-t-il dans le monde?
    
Certaines de ces questions sont plus évidentes que d’autres. La plupart des utilisateurs comprendront un utilitaire de résolution des problèmes a besoin des étapes exactes pour reproduire le problème. Après tout, comment pouvez-vous enregistrer la cause du problème et comment savoir si le problème est résolu? Les choses sont moins évidentes comme «quelle date et quelle date avez-vous rencontré le problème?» et «où se trouve dans le monde?», informations qui peuvent être utilisées en tandem. En fonction de l’heure à laquelle l’utilisateur a travaillé, un certain nombre d’heures de différence peut signifier que la maintenance est déjà en cours sur des parties du réseau de votre entreprise. Si, par exemple, votre société a une implémentation hybride, comme une recherche SharePoint hybride, qui peut interroger des index de recherche dans SharePoint Online et une instance SharePoint Server 2013 locale, des mises à jour peuvent être en cours dans la batterie de serveurs locale. Si votre entreprise se trouve dans le Cloud, la maintenance du système peut inclure l’ajout ou la suppression de matériel réseau, le déploiement de mises à jour à l’échelle de l’entreprise ou la modification du DNS ou d’une autre infrastructure de base.
  
Lorsque vous dépannez un problème de performances, il s’agit d’un peu comme une scène de crime, vous devez être précis et attentif pour pouvoir tirer des conclusions de la preuve. Pour ce faire, vous devez obtenir une déclaration de problème en rassemblant des preuves. Il doit inclure le contexte de l’ordinateur, le contexte de l’utilisateur, lorsque le problème a commencé et les étapes exactes qui ont exposé le problème de performances. Cette déclaration de problème doit, et rester, la page la plus haute dans vos notes. En parcourant l’instruction posant problème une fois que vous avez travaillé sur la résolution, vous prenez les mesures nécessaires pour tester et vérifier si les actions que vous effectuez ont résolu le problème. Il est important de savoir à quel moment votre travail est fait.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Savez-vous dans quelle mesure les performances sont-elles utiles?

Si vous êtes Unlucky, personne ne sait. Personne n’avait des chiffres. Cela signifie que personne ne peut répondre à la question simple «combien de secondes ont été utilisées pour accéder à une boîte de réception dans Office 365?», ou «combien de temps a-t-elle été utilisée quand les cadres ont eu une réunion Lync Online?», qui est un scénario courant pour de nombreuses entreprises.
  
Ce qui manque ici est une ligne de base des performances.
  
Les configurations de référence vous fournissent un contexte pour les performances. Vous devez prendre une ligne de base de manière occasionnelle, en fonction des besoins de votre entreprise. Si vous êtes une grande entreprise, votre équipe des opérations peut déjà prendre des lignes de base pour votre environnement local. Par exemple, si vous patchez tous les serveurs Exchange le premier lundi du mois et tous vos serveurs SharePoint sur le troisième lundi, votre équipe des opérations dispose probablement d’une liste de tâches et de scénarios qu’elle exécute après la mise à jour corrective, afin de prouver que les fonctions critiques sont production. Par exemple, en ouvrant la boîte de réception, en cliquant sur Envoyer/recevoir, et en vous assurant que les dossiers sont mis à jour ou, dans SharePoint, en accédant à la page principale du site, en accédant à la page de recherche de contenu d’entreprise et en effectuant une recherche qui renvoie des résultats.
  
Si vos applications se trouvent dans Office 365, certaines des configurations de référence les plus fondamentales que vous pouvez prendre mesurent le temps (en millisecondes) à partir d’un ordinateur client au sein de votre réseau, à un point de sortie ou au point où vous quittez votre réseau et accédez à Office 365. Voici quelques bases utiles que vous pouvez examiner et enregistrer:
  
- Identifiez les appareils entre votre ordinateur client et votre point de sortie, par exemple, votre serveur proxy.
    
  - Vous devez être informé de vos appareils afin d’avoir un contexte (adresses IP, type de périphérique, et cetera) pour les problèmes de performances qui surviennent.
    
  - Les serveurs proxy sont des points de sortie communs, afin que vous puissiez consulter votre navigateur Web pour savoir quel serveur proxy il est configuré pour utiliser, le cas échéant.
    
  - Il existe des outils tiers qui peuvent découvrir et mapper votre réseau, mais le moyen le plus sûr de savoir que vos appareils est de demander à un membre de votre équipe réseau.
    
- Identifiez votre fournisseur de services Internet (ISP), notez ses informations de contact et demandez le nombre de circuits dont vous disposez.
    
- Au sein de votre entreprise, identifiez les ressources des appareils entre votre client et le point de sortie, ou identifiez un contact d’urgence pour discuter des problèmes de mise en réseau.
    
Voici quelques lignes de base que les tests simples avec les outils peuvent calculer pour vous:
  
- Temps écoulé entre votre ordinateur client et votre point de sortie en millisecondes
    
- Temps écoulé entre votre point de sortie vers Office 365 en millisecondes
    
- Emplacement dans le monde du serveur qui résout les URL pour Office 365 lorsque vous parcourez
    
- Vitesse de la résolution DNS de votre fournisseur de services en millisecondes, incohérences dans l’arrivée des paquets (gigue réseau), temps de téléchargement et de téléchargement en millisecondes.
    
Si vous n’êtes pas familiarisé avec la façon d’effectuer ces étapes, nous allons voir plus en détail dans cet article. 
  
## <a name="what-is-a-baseline"></a>Qu’est-ce qu’une ligne de base?

Vous saurez quand il s’agit de mauvais, mais si vous ne maîtrisez pas vos données de performances historiques, il n’est pas possible d’avoir un contexte indiquant le degré de mauvaise incorrect et, le cas échéant, le moment où il est devenu. Sans ligne de base, vous ne disposez pas de l’indication clé pour résoudre le puzzle: l’image sur la zone puzzle. Lors de la résolution des problèmes de performances, vous avez besoin d’un point de *comparaison* . Les lignes de base des performances simples ne sont pas difficiles à prendre. Votre équipe des opérations peut être chargée de la réalisation de ces tâches selon un calendrier. Par exemple, imaginons que votre connexion ressemble à ceci: 
  
![Graphique réseau de base illustrant le Cloud client, proxy et Office 365.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Cela signifie que vous avez vérifié avec votre équipe réseau et que vous avez quitté votre entreprise sur Internet par le biais d’un serveur proxy, et que ce proxy traite toutes les demandes envoyées par votre ordinateur client au Cloud. Dans ce cas, vous devez dessiner une version simplifiée de votre connexion qui répertorie tous les périphériques intermédiaires. À présent, insérez des outils que vous pouvez utiliser pour tester les performances entre le client, le point de sortie (où vous quittez votre réseau pour Internet) et le nuage Office 365.
  
![Réseau de base avec client, proxy et nuage, et suggestions d’outils PSPing, TraceTCP et suivis réseau.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Les options sont répertoriées comme **simples** et **avancées** en raison de la quantité de compétences dont vous avez besoin pour trouver les données de performances. Un suivi réseau prendra beaucoup de temps, par rapport à l’exécution d’outils en ligne de commande tels que PsPing et TraceTCP. Ces deux outils de ligne de commande ont été choisis car ils n’utilisent pas de paquets ICMP, qui seront bloqués par Office 365 et, car ils fournissent le temps en millisecondes nécessaire à la sortie de l’ordinateur client ou du serveur proxy (si vous avez accès) et arrivent sur Office 365. Chaque tronçon individuel d’un ordinateur à un autre se terminera par une valeur de temps, et c’est parfait pour les configurations de référence. Tout aussi important, ces outils de ligne de commande vous permettent d’ajouter un numéro de port à la commande, ce qui est utile, car Office 365 communique via le port 443, qui est le port utilisé par le protocole SSL et TLS (Transport Layer Security). Toutefois, d’autres outils tiers peuvent être des solutions plus efficaces pour votre situation. Microsoft ne prend pas en charge tous ces outils, donc si, pour une raison quelconque, vous ne pouvez pas utiliser PsPing et TraceTCP, passez à un suivi réseau avec un outil tel que Netmon. 
  
Vous pouvez prendre une ligne de base avant les heures d’ouverture, à nouveau pendant une utilisation intensive, puis à nouveau après les heures supplémentaires. Cela signifie que vous pouvez avoir une structure de dossiers ressemblant à ce qui suit à la fin:
  
![Graphique proposant un moyen d’organiser vos données de performances dans des dossiers.](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Vous devez également choisir une convention d’affectation de noms pour vos fichiers. Voici quelques exemples :
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Il existe de nombreuses façons de le faire, mais l’utilisation du format ** \<DateTime\>\<ce qui se passe dans le\> test** est un excellent point de départ. Une bonne diligence sera plus importante lorsque vous tenterez de résoudre des problèmes plus tard. Par la suite, vous pourrez dire «j’ai pris deux traces le 8 février, un a montré de bonnes performances et l’autre a montré un mauvais, donc nous pouvons les comparer». Cela est très utile pour la résolution des problèmes. 
  
Vous devez disposer d’un moyen organisé pour conserver vos planifications historiques. Dans cet exemple, les méthodes simples ont généré trois sorties de ligne de commande et les résultats ont été collectés en tant que captures d’écran, mais vous pouvez avoir des fichiers de capture réseau. Utilisez la méthode qui vous convient le mieux. Stockez vos planifications historiques et faites-y référence à des points où vous pouvez remarquer des modifications dans le comportement des services en ligne. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Pourquoi collecter les données de performances pendant un projet pilote?

Il n’y a pas de meilleur moment pour commencer à établir des lignes de base que lors d’un projet pilote du service Office 365. Votre bureau peut avoir des milliers d’utilisateurs, des centaines de milliers ou avoir cinq personnes, mais même avec un petit nombre d’utilisateurs, vous pouvez effectuer des tests pour mesurer les fluctuations des performances. Dans le cas d’une société de grande taille, un échantillon représentatif de plusieurs centaines d’utilisateurs pour l’installation d’Office 365 peut être projeté vers plusieurs milliers afin que vous sachiez où des problèmes peuvent survenir avant qu’ils ne se produisent.
  
Dans le cas d’une petite entreprise, lorsque l’accès à bord signifie que tous les utilisateurs accèdent au service en même temps et qu’il n’y a pas de pilote, conservez les mesures de performances de sorte que vous disposiez de données à afficher aux personnes susceptibles de dépanner une opération incorrecte. Par exemple, si vous remarquez que tout est soudain, vous pouvez vous déplacer dans le temps nécessaire pour charger un graphique de taille moyenne là où il s’est exécuté très rapidement.
  
## <a name="how-to-collect-baselines"></a>Procédure de collecte des configurations de référence

Pour tous les plans de dépannage, vous devez identifier ces éléments au minimum:
  
- L’ordinateur client que vous utilisez (le type d’ordinateur ou d’appareil, une adresse IP et les actions à l’origine du problème);
    
- Où se trouve l’ordinateur client dans le monde entier (par exemple, si cet utilisateur se trouve sur un réseau privé virtuel (VPN) sur le réseau, s’il travaille à distance ou sur l’intranet de l’entreprise)
    
- Le point de sortie que l’ordinateur client utilise à partir de votre réseau (le point auquel le trafic quitte votre entreprise pour un fournisseur de services Internet ou Internet).
    
 Vous pouvez découvrir la disposition de votre réseau à partir de l’administrateur réseau. Si vous êtes sur un petit réseau, jetez un œil aux appareils qui se connectent à Internet et appelez votre fournisseur de services Internet si vous avez des questions sur la mise en page. Créez un graphique de la mise en page finale pour votre référence. 
  
Cette section est divisée en des méthodes et des outils de ligne de commande simples, ainsi que des options d’outils avancées. Nous allons commencer par aborder des méthodes simples. Toutefois, si vous avez rencontré un problème de performances dès à présent, vous devez passer aux méthodes avancées et tester l’exemple de plan d’action de résolution des problèmes de performances.
  
### <a name="simple-methods"></a>Méthodes simples

L’objectif de ces méthodes simples est d’apprendre à prendre, à comprendre et à stocker correctement les lignes de base des performances simples au fil du temps, afin que vous soyez informé des performances d’Office 365. Voici le diagramme très simple, comme vous l’avez vu précédemment:
  
![Réseau de base avec client, proxy et nuage, et suggestions d’outils PSPing, TraceTCP et suivis réseau.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP est inclus dans cette capture d’écran, car il s’agit d’un outil utile pour afficher, en millisecondes, la durée de traitement d’une demande, ainsi que le nombre de tronçons réseau, ou les connexions d’un ordinateur à l’autre, que la demande doit atteindre pour atteindre une destination. TraceTCP peut également donner les noms des serveurs utilisés pendant les tronçons, ce qui peut être utile pour un utilitaire de résolution des problèmes de Microsoft Office 365 dans le support technique. > les commandes TraceTCP peuvent être très simples, telles que: `tracetcp.exe outlook.office365.com:443`_GT_ _GT_ n’oubliez pas d’inclure le numéro de port dans la commande! > [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html) est un téléchargement gratuit, mais s’appuie sur Wincap. Wincap est un outil qui est également utilisé et installé par Netmon. Nous utilisons également Netmon dans la section méthodes avancées. 
  
 Si vous avez plusieurs bureaux, vous devez également conserver un ensemble de données à partir d’un client dans chacun de ces emplacements. Cette latence de test mesure, qui, dans ce cas, est une valeur numérique qui décrit le temps écoulé entre un client envoyant une demande à Office 365 et Office 365 répondant à la demande. Le test provient de votre domaine sur un ordinateur client et recherche un aller-retour depuis votre réseau, jusqu’à un point de sortie, sur Internet vers Office 365, et inversement. 
  
Il existe plusieurs façons de traiter le point de sortie, dans ce cas, le serveur proxy. Vous pouvez effectuer un suivi de 1 à 2, puis de 2 à 3, puis ajouter les nombres en millisecondes pour obtenir un total final sur le serveur Edge de votre réseau. Sinon, vous pouvez configurer la connexion de sorte qu’elle contourne le proxy pour les adresses Office 365. Dans un réseau de plus grande taille avec un pare-feu, un proxy inverse ou une combinaison des deux, vous devrez peut-être faire des exceptions sur le serveur proxy qui permettra le trafic à transmettre pour un grand nombre d’URL. Pour obtenir la liste des points de terminaison utilisés par Office 365, voir [URL et plages d’adresses IP office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Si vous disposez d’un proxy d’authentification, commencez par tester les exceptions pour les éléments suivants:
  
- Ports 80 et 443
    
- TCP et HTTPs
    
- Connexions sortantes vers l’une de ces URL:
    
- \*. microsoftonline.com
    
- \*. microsoftonline-p.com
    
- \*. sharepoint.com
    
- \*. outlook.com
    
- \*. lync.com
    
- osub.microsoft.com
    
Tous les utilisateurs doivent être autorisés à accéder à ces adresses sans interférence ou authentification de proxy. Sur un réseau de petite taille, vous devez les ajouter à votre liste de contournement de proxy dans votre navigateur Web. 
  
Pour les ajouter à votre liste de contournement de proxy dans Internet Explorer, accédez à **Outils** \> **Internet options** \> **connexions** \> **réseau local paramètres** \> **avancés**. L’onglet avancé est également l’emplacement où se trouve le port de votre serveur proxy et de votre serveur proxy. Vous devrez peut-être cliquer sur la case à cocher **utiliser un serveur proxy pour votre réseau local**pour accéder au bouton **avancé** . Assurez-vous que l’option ne pas **utiliser de serveur proxy pour les adresses locales** est cochée. Une fois que vous avez cliqué sur **avancé**, vous verrez une zone de texte dans laquelle vous pouvez entrer des exceptions. Séparez les URL génériques mentionnées ci-dessus par des points-virgules, par exemple:
  
\*. microsoftonline.com; \*. SharePoint.com
  
Une fois que vous ignorez votre proxy, vous devriez pouvoir utiliser la commande ping ou PsPing directement sur une URL Office 365. L’étape suivante consiste à tester la commande ping **Outlook.office365.com**. Ou, si vous utilisez PsPing ou un autre outil qui vous permet de fournir un numéro de port à la commande, PsPing par rapport à **Portal.microsoftonline.com:443** pour voir la durée moyenne des boucles en millisecondes. 
  
Le temps d’aller-retour, ou RTT, est une valeur numérique qui mesure le temps nécessaire pour envoyer une requête HTTP à un serveur comme outlook.office365.com et obtenir une réponse indiquant que le serveur sait que vous l’avez fait. Vous verrez parfois l’abréviation RTT. Cette durée doit être relativement courte.
  
Pour effectuer ce test, vous devez utiliser [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) ou un autre outil qui n’utilise pas de paquets ICMP bloqués par Office 365. 
  
 **Utilisation de PsPing pour obtenir une boucle d’ensemble complète en millisecondes directement à partir d’une URL Office 365**
  
1. Exécutez une invite de commandes avec élévation de privilèges en procédant comme suit:
    
1. Cliquez sur **Démarrer**.
    
2. Dans la zone **lancer la recherche** , tapez cmd, puis appuyez sur Ctrl + Maj + Entrée.
    
3. Si la boîte de dialogue **Contrôle de compte d'utilisateur** apparaît, confirmez que l'action affichée est celle que vous souhaitez, puis cliquez sur **Continue**r.
    
2. Accédez au dossier dans lequel l’outil (dans le cas présent PsPing) est installé et testez ces URL Office 365:
    
  - psping portal.office.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![La commande PSPing passe à microsoft-my.sharepoint.com port 443.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Veillez à inclure le numéro de port 443. N’oubliez pas qu’Office 365 fonctionne sur un canal chiffré. Si vous PsPing sans le numéro de port, votre requête échouera. Une fois que vous avez interrogé votre courte liste, recherchez la durée moyenne en millisecondes (MS). C’est ce que vous voulez enregistrer!
  
![Graphique illustrant une illustration d’un client pour le proxy PSPing avec un temps d’aller-retour de 2,8 millisecondes.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Si vous n’êtes pas familiarisé avec la déviation du proxy et que vous préférez effectuer des opérations pas à pas, vous devez d’abord Rechercher le nom de votre serveur proxy. Dans Internet Explorer, accédez à **Outils** \> **Internet options** \> Internet **connexions** \> **paramètres** \> **avancés**. L’onglet **avancé** affiche votre serveur proxy. Exécutez une commande ping sur ce serveur proxy à partir d’une invite de commandes en effectuant cette tâche: 
  
 **Pour exécuter la commande ping sur le serveur proxy et obtenir une valeur d’aller-retour en millisecondes pour l’étape 1 à 2**
  
1. Exécutez une invite de commandes avec élévation de privilèges en procédant comme suit:
    
1. Cliquez sur **Démarrer**.
    
2. Dans la zone **lancer la recherche** , tapez cmd, puis appuyez sur Ctrl + Maj + Entrée.
    
3. Si la boîte de dialogue **Contrôle de compte d'utilisateur** apparaît, confirmez que l'action affichée est celle que vous souhaitez, puis cliquez sur **Continue**r.
    
2. Tapez ping \<le nom du serveur proxy utilisé par votre navigateur ou l’adresse IP du serveur\> proxy, puis appuyez sur entrée. Si vous avez PsPing, ou un autre outil, installé, vous pouvez choisir d’utiliser cet outil à la place. 
    
    Votre commande peut ressembler à l’un des exemples suivants: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy: 80
    
3. Lorsque le suivi cesse d’envoyer des paquets de test, vous obtiendrez un petit résumé qui répertorie une moyenne, en millisecondes, et c’est la valeur que vous avez suivie. Prenez une capture d’écran de l’invite et enregistrez-la à l’aide de votre convention d’affectation de noms. À ce stade, il peut également aider à renseigner le diagramme avec la valeur.
    
Vous avez peut-être suivi un suivi dès le matin, et votre client peut accéder au proxy (ou tout autre serveur de sortie sortant d’Internet) rapidement. Dans ce cas, vos numéros peuvent ressembler à ceci:
  
![Graphique illustrant le temps d’aller-retour entre un client et un proxy de 2,8 millisecondes.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Si votre ordinateur client est l’un des serveurs en cours d’accès au proxy (ou de sortie), vous pouvez exécuter l’étape suivante du test en vous connectant à distance à cet ordinateur, en exécutant l’invite de commandes sur PsPing à une URL Office 365 à partir de là. Si vous n’avez pas accès à cet ordinateur, vous pouvez contacter vos ressources réseau pour obtenir de l’aide sur la prochaine étape et obtenir des nombres exacts de cette façon. Si ce n’est pas possible, prenez un PsPing par rapport à l’URL d’Office 365 en question et comparez-le à l’PsPing ou au temps de ping par rapport à votre serveur proxy. 
  
Par exemple, si vous avez 51,84 millisecondes entre le client et l’URL Office 365 et que vous avez 2,8 millisecondes entre le client et le proxy (ou le point de sortie), vous disposez de 49,04 millisecondes de sortie vers Office 365. De même, si vous avez une PsPing de 12,25 millisecondes entre le client et le proxy pendant la journée, et 62,01 millisecondes entre le client et l’URL Office 365, votre valeur moyenne pour la sortie proxy vers l’URL Office 365 est de 49,76 millisecondes.
  
![Graphique supplémentaire illustrant la commande ping en millisecondes entre le client et le proxy à côté du client et Office 365, de sorte que les valeurs puissent être soustraites.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
En matière de résolution des problèmes, vous pouvez trouver un peu intéressant de conserver ces configurations de référence. Par exemple, si vous constatez que vous disposez généralement d’environ 40 à 59 millisecondes de latence du proxy ou de la sortie vers l’URL d’Office 365, et que la latence du client à proxy ou de sortie est de 3 à 7 millisecondes environ (en fonction de la quantité de trafic réseau que vous seein g pendant cette période de la journée) alors, vous saurez sûrement qu’un problème est problématique si vos trois derniers clients à proxy ou sortance de lignes de base indiquent une latence de 45 millisecondes.
  
### <a name="advanced-methods"></a>Méthodes avancées

Si vous souhaitez savoir ce qui se passe de vos demandes Internet auprès d’Office 365, vous devez vous familiariser avec les suivis réseau. Peu importe les outils que vous préférez pour ces traces, HTTPWatch, NetMon, analyseur de messages, Wireshark, Fiddler, l’outil de tableau de bord du développeur ou tout autre opération fera en sorte que cet outil puisse capturer et filtrer le trafic réseau. Dans cette section, il est préférable d’exécuter plusieurs de ces outils pour obtenir une image plus complète du problème. Lorsque vous effectuez des tests, certains de ces outils agissent également en tant que proxys à leur guise. Les outils utilisés dans l’article associé, [plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md), incluent [Netmon 3,4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)ou [Wireshark](https://www.wireshark.org/).
  
La prise en charge d’une ligne de base des performances est la partie simple de cette méthode, et la plupart des étapes sont les mêmes que pour résoudre un problème de performances. Les méthodes plus avancées de création de configurations de référence pour les performances nécessitent de prendre et de stocker des suivis réseau. La plupart des exemples de cet article utilisent SharePoint Online, mais vous devez développer une liste d’actions courantes sur les services Office 365 auxquels vous vous abonnez. Voici un exemple de ligne de base:
  
- Liste de référence pour SPO-* * étape 1: * * Naviguez jusqu’à la page d’accueil du site Web SPO et effectuez un suivi réseau. Enregistrez le suivi. 
    
- Liste de référence pour SPO- **étape 2:** recherchez un terme (par exemple, le nom de votre société) via la recherche de contenu d’entreprise et effectuez un suivi réseau. Enregistrez le suivi. 
    
- Liste de référence pour SPO- **étape 3:** télécharger un fichier volumineux dans une bibliothèque de documents SharePoint Online et effectuer un suivi réseau. Enregistrez le suivi. 
    
- Liste de référence pour SPO- **étape 4:** parcourir la page d’accueil du site Web OneDrive et effectuer un suivi réseau. Enregistrez le suivi. 
    
Cette liste doit inclure les actions courantes les plus importantes que les utilisateurs prennent sur SharePoint Online. Notez que la dernière étape, pour suivre la procédure de préparation de OneDrive entreprise, est une comparaison entre le chargement de la page d’accueil SharePoint Online (souvent personnalisée par les sociétés) et la page d’accueil de OneDrive entreprise, qui est rarement personnalisée. Il s’agit d’un test de base lorsqu’il s’agit d’un site SharePoint Online à chargement lent. Vous pouvez créer un enregistrement de cette différence dans vos tests.
  
Si vous êtes au milieu d’un problème de performances, la plupart des étapes sont les mêmes que lors de l’exécution d’une ligne de base. Les suivis réseau deviennent critiques, c’est ** pourquoi nous allons gérer le suivi des traces importantes. 
  
Pour résoudre un problème de performances ** , vous devez effectuer un suivi au moment où vous rencontrez le problème de performances. Vous devez disposer des outils appropriés pour collecter les journaux, et vous avez besoin d’un plan d’action, c’est-à-dire d’une liste des actions de résolution des problèmes à effectuer pour recueillir les meilleures informations que vous pouvez utiliser. La première chose à faire est d’enregistrer la date et l’heure du test afin que les fichiers puissent être enregistrés dans un dossier reflétant le calendrier. Ensuite, réduisez les étapes du problème. Voici les étapes exactes que vous allez utiliser pour les tests. N’oubliez pas les notions de base: si le problème concerne uniquement Outlook, veillez à noter que le problème se produit dans un seul service Office 365. Le rétrécissement de l’étendue de ce problème vous aidera à vous concentrer sur les éléments que vous pouvez résoudre. 
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

