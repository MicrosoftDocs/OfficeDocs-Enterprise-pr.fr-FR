---
title: Plan de résolution des problèmes de performances pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: Avez-vous besoin de connaître les étapes à suivre pour identifier et résoudre les problèmes de retard, de blocage et de ralentissement des performances entre SharePoint Online, OneDrive entreprise, Exchange Online ou Skype entreprise Online, et votre ordinateur client ? Avant d’appeler la prise en charge, cet article peut vous aider à résoudre les problèmes de performances d’Office 365 et même à résoudre certains problèmes les plus courants.
ms.openlocfilehash: 1740e73c298578b4a13e254081ae62b795aed0ab
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814622"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan de résolution des problèmes de performances pour Office 365

Avez-vous besoin de connaître les étapes à suivre pour identifier et résoudre les problèmes de retard, de blocage et de ralentissement des performances entre SharePoint Online, OneDrive entreprise, Exchange Online ou Skype entreprise Online, et votre ordinateur client ? Avant d’appeler la prise en charge, cet article peut vous aider à résoudre les problèmes de performances d’Office 365 et même à résoudre certains problèmes les plus courants.
  
Cet article est en fait un exemple de plan d’action que vous pouvez utiliser pour capturer des données importantes sur votre problème de performances à mesure qu’il se produit. Certains des principaux problèmes sont également inclus dans cet article.

Si vous ne connaissez pas les performances du réseau et que vous souhaitez faire un plan à long terme pour surveiller les performances entre vos ordinateurs clients et Office 365, jetez un œil à [office 365 Performance Tuning and Troubleshooting-admin and IT Pro](performance-tuning-using-baselines-and-history.md).
  
## <a name="sample-performance-troubleshooting-action-plan"></a>Exemple de plan d’action de résolution des problèmes de performances

Ce plan d’action contient deux parties ; une phase de préparation et une phase de journalisation. Si vous avez un problème de performances dès à présent, et que vous devez effectuer une collecte de données, vous pouvez commencer à utiliser ce plan immédiatement.
  
### <a name="prepare-the-client-computer"></a>Préparer l’ordinateur client
  
- Recherchez un ordinateur client qui peut reproduire le problème de performances. Cet ordinateur sera utilisé au cours de la résolution des problèmes.
- Notez les étapes qui provoquent le problème de performances afin que vous soyez prêt à tester.
- Installez les outils permettant de collecter et d’enregistrer des informations :
  - Installez [Netmon 3,4](https://www.microsoft.com/download/details.aspx?id=4865) (ou utilisez un outil de suivi réseau équivalent).
  - Installez l’édition de base gratuite de [HTTPWatch](https://www.httpwatch.com/download/) (ou utilisez un outil de suivi réseau équivalent).
  - Utilisez un enregistreur d’écran ou exécutez l’enregistreur d’actions (V.Q.P.R.D.. exe) fourni avec Windows Vista et les versions ultérieures, afin de conserver un enregistrement des étapes que vous effectuez pendant les tests.

### <a name="log-the-performance-issue"></a>Consigner le problème de performances
  
- Fermez tous les navigateurs Internet superflus.
- Démarrez l’enregistreur d’actions ou un autre enregistreur d’écran.
- Démarrez votre capture Netmon (ou l’outil de suivi réseau).
- Effacez votre cache DNS sur l’ordinateur client à partir de la ligne de commande en tapant ipconfig/flushdns.
- Démarrez une nouvelle session de navigateur et activez HTTPWatch.
- Facultatif : Si vous testez Exchange Online, exécutez l’analyseur de performances du client Exchange à partir de la console d’administration Office 365.
- Reproduisez les étapes exactes à l’origine du problème de performances.
- Arrêtez votre Netmon ou le suivi de l’autre outil.
- Sur la ligne de commande, exécutez un itinéraire de suivi vers votre abonnement Office 365 en tapant la commande suivante, puis en appuyant sur entrée :

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Arrêtez l’enregistreur d’actions et enregistrez la vidéo. Veillez à inclure la date et l’heure de la capture et indiquez si les performances sont bonnes ou mauvaises.
- Enregistrez les fichiers de suivi. N’oubliez pas d’inclure la date et l’heure de la capture et s’il s’agit d’une bonne ou d’une mauvaise performance.

Si vous n’êtes pas familiarisé avec l’exécution des outils mentionnés dans cet article, ne vous inquiétez pas, car nous fournissons les étapes suivantes. Si vous avez l’habitude d’effectuer ce type de capture de réseau, vous pouvez passer à la [procédure de collecte de configurations de référence](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), qui décrit le filtrage et la lecture des journaux.
  
### <a name="flush-the-dns-cache-first"></a>Videz d’abord le cache DNS

Pourquoi ? En vidant le cache DNS, vous commencez vos tests avec une ardoise propre. En effaçant le cache, vous redéfinissez le contenu de la résolution DNS sur les entrées les plus à jour. N’oubliez pas qu’un vidage ne supprime pas les entrées de fichier hosts. Si vous utilisez largement des entrées de fichier hôte, vous devez copier ces entrées dans un fichier dans un autre répertoire, puis vider le fichier hôte.
  
#### <a name="flush-your-dns-resolver-cache"></a>Videz le cache de résolution DNS
  
1. Ouvrez l’invite de commandes ( **Démarrez** \> **exécuter** \> **cmd** ou la **touche** \> Windows **cmd**).
2. Tapez la commande suivante, puis appuyez sur Entrée :

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Moniteur

L’outil de surveillance réseau de Microsoft ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analyse les paquets, c’est-à-dire le trafic, qui transitent entre les ordinateurs sur les réseaux. L’utilisation de Netmon pour suivre le trafic avec Office 365 vous permet de capturer, d’afficher et de lire des en-têtes de paquets, d’identifier les périphériques impliqués, de vérifier les paramètres importants sur le matériel réseau, de rechercher les paquets ignorés et de suivre le flux de trafic entre les ordinateurs de votre entreprise. réseau et Office 365. Étant donné que le corps réel du trafic est chiffré, c’est-à-dire, qu’il a (transite sur le port 443 via SSL/TLS, vous ne pouvez pas lire les fichiers envoyés. Au lieu de cela, vous obtenez un suivi non filtré du chemin emprunté par le paquet pour vous aider à identifier le comportement du problème.
  
Veillez à ne pas appliquer de filtre pour le moment. Au lieu de cela, exécutez les étapes et montrez le problème avant d’arrêter le suivi et d’enregistrer.
  
Une fois que vous avez installé Netmon 3,4, ouvrez l’outil et procédez comme suit :
  
### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Effectuer un suivi Netmon et reproduire le problème
  
1. Lancez Netmon 3,4.
La page de **démarrage** comporte trois volets : **captures récentes**, **sélection des réseaux**et **mise en route avec le moniteur réseau Microsoft 3,4. Notification**. Le panneau sélectionner les réseaux vous donnera également une liste des réseaux par défaut à partir desquels vous pouvez effectuer des captures. Assurez-vous que les cartes réseau sont sélectionnées ici.

2. Cliquez sur **nouvelle capture** en haut de la page de **démarrage** . Cette méthode ajoute un nouvel onglet en regard de l’onglet page de **démarrage** appelé **capture 1**.
![Interface utilisateur de Netmon avec les nouveaux boutons de capture, de démarrage et d’arrêt mis en surbrillance.](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Pour effectuer une capture simple, cliquez sur **Démarrer** dans la barre d’outils.

4. Reproduisez les étapes qui présentent un problème de performances.

5. Cliquez sur **arrêter** \> le **fichier** \> **Enregistrer sous**. N’oubliez pas d’indiquer la date et l’heure avec le fuseau horaire et de mentionner s’il présente des performances médiocres ou bonnes.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) est facturé et une édition gratuite. La version gratuite de Basic Edition couvre tout ce dont vous avez besoin pour ce test. HTTPWatch analyse le trafic réseau et le temps de chargement de la page directement à partir de votre fenêtre de navigateur. HTTPWatch est un plug-in d’Internet Explorer qui décrit graphiquement les performances. L’analyse peut être enregistrée et visualisée dans HTTPWatch Studio.
  
> [!NOTE]
> Si vous utilisez un autre navigateur, tel que Firefox, Google Chrome, ou si vous ne pouvez pas installer HTTPWatch dans Internet Explorer, ouvrez une nouvelle fenêtre de navigateur et appuyez sur la touche F12 de votre clavier. Le menu contextuel de l’outil de développement doit apparaître en bas de votre navigateur. Si vous utilisez Opera, appuyez sur CTRL + MAJ + I pour l’inspecteur Web, puis cliquez sur l’onglet **réseau** et effectuez les tests présentés ci-dessous. Les informations seront légèrement différentes, mais les temps de chargement resteront affichés en millisecondes. > HTTPWatch est également très utile pour les problèmes liés aux temps de chargement des pages SharePoint Online.
  
### <a name="run-httpwatch-and-reproduce-the-issue"></a>Exécuter HTTPWatch et reproduire le problème
  
HTTPWatch est un plug-in de navigateur, donc l’exposition de l’outil dans le navigateur est légèrement différente pour chaque version d’Internet Explorer. En règle générale, vous pouvez trouver HTTPWatch sous la barre de commandes dans le navigateur Internet Explorer. Si vous ne voyez pas le plug-in HTTPWatch dans la fenêtre de votre navigateur, vérifiez la version de votre navigateur en cliquant sur **aide** \> **sur**ou dans les versions ultérieures d’Internet Explorer, cliquez sur le symbole de l’engrenage et **sur Internet Explorer**. Pour ouvrir la barre de **commandes** , cliquez avec le bouton droit sur la barre de menus dans Internet Explorer, puis cliquez sur **barre de commandes**.

Dans le passé, HTTPWatch a été associé à la fois aux commandes et aux volets d’exploration, par conséquent, une fois que vous avez installé, si vous ne voyez pas immédiatement l’icône (même après le redémarrage **), puis**les barres d’outils de l’icône. N’oubliez pas que les barres d’outils peuvent être personnalisées et qu’il est possible d’y ajouter des options.

![Barre d’outils de commandes d’Internet Explorer avec l’icône HTTPWatch affichée.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
1. Lancez HTTPWatch dans une fenêtre de navigateur Internet Explorer. Il apparaîtra ancré au navigateur au bas de cette fenêtre. Cliquez sur **Enregistrer**.

2. Reproduisez les étapes exactes du problème de performances. Cliquez sur le bouton **arrêter** dans HTTPWatch.

3. **Enregistrer** le HTTPWatch ou **Envoyer par courrier électronique**. N’oubliez pas de nommer le fichier afin qu’il comprenne des informations de date et d’heure, ainsi qu’une indication de la présence d’une démonstration de bonne ou mauvaise qualité.

![HTTPWatch affichant l’onglet Réseau pour le chargement de la page d’accueil Office 365.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Cette capture d’écran provient de la version professionnelle de HTTPWatch. Vous pouvez ouvrir des traces prises dans la version de base sur un ordinateur avec une version professionnel et y accéder. Des informations supplémentaires peuvent être disponibles à partir du suivi via cette méthode.

## <a name="problem-steps-recorder"></a>Enregistreur d’actions d’un problème

L’enregistreur d’actions utilisateur, ou V.Q.P.R.D.. exe, vous permet d’enregistrer les problèmes au fur et à mesure qu’ils se produisent. Il s’agit d’un outil très utile et très simple à exécuter.
  
### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Exécuter l’enregistreur d’étapes du problème (V.Q.P.R.D.. exe) pour enregistrer votre travail
  
1. Utilisez **Démarrer** \> **exécuter** \> type **v.q.p.r.d.. exe** \> **OK**, ou cliquez sur le type de **clé** \> Windows **v.q.p.r.d.. exe** \> , puis appuyez sur entrée.

2. Lorsque la fenêtre Small V.Q.P.R.D.. exe s’affiche, cliquez sur **Démarrer l’enregistrement** et reproduisez les étapes qui reproduisent le problème de performances. Vous pouvez ajouter des commentaires en fonction de vos besoins en cliquant sur **Ajouter des commentaires**.

3. Cliquez sur **arrêter l’enregistrement** lorsque vous avez terminé les étapes. Si le problème de performances est un rendu de page, attendez que la page s’affiche avant d’arrêter l’enregistrement.

4. Cliquez sur **Enregistrer**.

![Capture d’écran de l’enregistreur d’actions ou du fichier V.Q.P.R.D.. exe.](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
La date et l’heure sont enregistrées. Cela lie vos V.Q.P.R.D. à votre suivi Netmon et HTTPWatch dans le temps, et vous aide à résoudre les problèmes de précision. La date et l’heure de l’enregistrement du V.Q.P.R.D. peuvent indiquer qu’une minute s’est écoulée entre la connexion et la consultation de l’URL et le rendu partiel du site d’administration, par exemple.
  
## <a name="read-your-traces"></a>Lire vos traces

Il n’est pas possible d’apprendre tout sur le dépannage du réseau et des performances que quelqu’un a besoin de connaître via un article. Obtenir des performances optimales prend de l’expérience et connaît le fonctionnement de votre réseau et se comporte généralement. Toutefois, il est possible d’arrondir une liste des principaux problèmes et de montrer comment les outils peuvent vous aider à éliminer les problèmes les plus courants.
  
Si vous souhaitez prendre des compétences en lisant des traces réseau pour vos sites Office 365, il n’y a pas de meilleur enseignant que la création régulière de traces de charge de page et l’expérience de lecture. Par exemple, lorsque vous avez une chance, chargez un service Office 365 et suivez le processus. Filtrez le suivi pour le trafic DNS ou recherchez le nom du service que vous avez parcouru dans le FrameData. Analysez le suivi pour obtenir une idée des étapes qui se produisent lors du chargement du service. Cela vous permettra de découvrir ce à quoi ressemblent le chargement normal des pages, et dans le cas d’une résolution des problèmes, en particulier en ce qui concerne les performances, la comparaison de bons et de mauvais suivis peut vous enseigner beaucoup.
  
Netmon utilise Microsoft IntelliSense dans le champ filtre d’affichage. IntelliSense, ou la saisie semi-automatique du code, est cette astuce où vous tapez un point et toutes les options disponibles sont affichées dans une zone de sélection déroulante. Si, par exemple, vous vous inquiétez de la mise à l’échelle de la fenêtre TCP, vous pouvez rechercher un filtre `.protocol.tcp.window < 100`(tel que) par cette méthode.
  
![Capture d’écran de Netmon montrant que le champ filtre d’affichage utilise IntelliSense.](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Les traces Netmon peuvent contenir un grand nombre de trafic. Si vous n’êtes pas expérimenté en les lisant, il est probable que vous ouvriez le suivi la première fois. La première chose à faire est de séparer le signal du bruit de fond dans le suivi. Vous avez testé sur Office 365, et c’est le trafic que vous souhaitez voir. Si vous êtes utilisé pour naviguer dans les traces, il se peut que vous n’ayez pas besoin de cette liste.
  
Le trafic entre votre client et Office 365 transite via TLS, ce qui signifie que le corps du trafic est chiffré et illisible dans un suivi Netmon générique. Votre analyse des performances n’a pas besoin de savoir quels sont les détails des informations contenues dans le paquet. Toutefois, il est très intéressé par les en-têtes de paquets et les informations qu’ils contiennent.
  
### <a name="tips-to-get-a-good-trace"></a>Conseils pour obtenir un suivi approprié
  
- Sachez que la valeur de l’adresse IPv4 ou IPv6 de votre ordinateur client. Vous pouvez obtenir ce message à partir de l’invite de commandes en tapant **ipconfig** , puis en appuyant sur entrée. La connaissance de cette adresse vous permettra de savoir en un clin d’œil si le trafic dans le suivi implique directement votre ordinateur client. S’il existe un proxy connu, exécutez la commande ping et obtenez également son adresse IP.

- Videz le cache de résolution DNS et, si possible, fermez tous les navigateurs à l’exception de celui dans lequel vous exécutez vos tests. Si vous ne parvenez pas à effectuer cette opération, par exemple, si la prise en charge utilise un outil basé sur un navigateur pour afficher le Bureau de votre ordinateur client, préparez-vous à filtrer votre suivi.

- Dans un suivi occupé, localisez le service Office 365 que vous utilisez. Si vous n’avez jamais vu votre trafic auparavant, il s’agit d’une étape utile pour séparer le problème de performances d’un autre bruit réseau. Il existe plusieurs façons de le faire. Directement avant votre test, vous pouvez utiliser _ping_ ou _PsPing_ par rapport à l’URL du service spécifique`ping outlook.office365.com` ( `psping -4 microsoft-my.sharepoint.com:443`ou, par exemple). Vous pouvez également trouver facilement ce ping ou PsPing dans un suivi Netmon (par son nom de processus). Cela vous permettra de commencer à rechercher.

Si vous utilisez uniquement le suivi Netmon au moment du problème, c’est également possible. Pour vous orienter, utilisez un filtre comme `ContainsBin(FrameData, ASCII, "office")` ou `ContainsBin(FrameData, ASCII, "outlook")`. Vous pouvez enregistrer votre numéro de trame à partir du fichier de suivi. Vous pouvez également faire défiler le volet de _synthèse des cadres_ vers la droite et rechercher la colonne ID de conversation. Il existe un numéro indiqué pour l’ID de cette conversation spécifique que vous pouvez également enregistrer et regarder dans isolation ultérieurement. N’oubliez pas de supprimer ce filtre avant d’appliquer d’autres filtres.

> [!TIP]
> Netmon comporte un grand nombre de filtres intégrés utiles. Essayez le bouton **charger le filtre** en haut du volet filtre d' _affichage_ .
  
![Recherchez votre adresse IP à l’aide de PSPing sur la ligne de commande sur l’ordinateur client.](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Trace Netmon à partir du client affichant la même commande PSPing via le filtre TCP. Flags. syn = = 1.](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
Familiarisez-vous avec votre trafic et découvrez comment trouver les informations dont vous avez besoin. Par exemple, Apprenez à déterminer quel paquet de la trace a la première référence au service Office 365 que vous utilisez (par exemple, « Outlook »).

En prenant Office 365 Outlook Online comme exemple, le trafic commence comme ceci :
  
- Requête DNS standard et réponse DNS pour outlook.office365.com avec QueryIDs correspondant. Il est important de noter le décalage de temps pour ce tour, ainsi que l’endroit où le DNS global d’Office 365 envoie la demande de résolution de noms. Idéalement, autant que possible, au lieu de traverser le monde entier.

- Une requête HTTP GET dont le rapport d’État A été déplacé définitivement (301)

- Le trafic RWS, y compris les demandes de connexion à RWS, et connecte les réponses. (Winsock distant effectue une connexion pour vous.)

- Une conversation TCP SYN et TCP SYN/ACK. De nombreuses valeurs de cette conversation influent sur les performances.

- Une série de TLS : le trafic TLS où se déroule la négociation TLS et les conversations de certificat TLS. (Souvenez-vous que les données sont chiffrées via SSL/TLS.)

Toutes les parties du trafic sont importantes et connectées, mais les petites parties du suivi contiennent des informations particulièrement importantes en matière de résolution des problèmes de performances, c’est pourquoi nous allons nous concentrer sur ces domaines. En outre, étant donné que nous avons terminé le dépannage des performances Office 365 chez Microsoft pour compiler une liste des dix problèmes courants, nous nous concentrerons sur ces problèmes et sur l’utilisation des outils que nous devons mettre en avant.
  
Si vous n’avez pas installé tous les éléments prêts, la matrice ci-dessous utilise plusieurs outils. Dans la mesure du possible. Des liens sont fournis aux points d’installation. La liste inclut des outils de suivi réseau courants, tels que [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) et [Wireshark](https://www.wireshark.org/), mais vous pouvez utiliser n’importe quel outil de suivi auquel vous êtes habitué et dans lequel vous êtes habitué à filtrer le trafic réseau. Lorsque vous testez, rappelez-vous des éléments suivants :
  
- *Fermez vos navigateurs et testez avec un seul navigateur en cours d’exécution* -cela réduira le trafic global que vous capturez. Il effectue une trace moins chargée.
- *Videz votre cache de résolution DNS sur l’ordinateur client* : vous obtiendrez une place vierge lorsque vous commencerez à effectuer votre capture, pour un suivi plus clair.

## <a name="common-issues"></a>Problèmes courants

Certains problèmes courants que vous pouvez rencontrer et comment les trouver dans votre suivi réseau.

### <a name="tcp-windows-scaling"></a>Mise à l’échelle TCP Windows

Trouvé dans le SYN-SYN/ACK. Le matériel hérité ou âgé ne peut pas tirer parti de la mise à l’échelle Windows TCP.  Sans paramètres de mise à l’échelle Windows TCP appropriés, la mémoire tampon de 16 bits par défaut dans les en-têtes TCP est exprimée en millisecondes.  Le trafic ne peut pas continuer à envoyer jusqu’à ce que le client reçoive un accusé de réception indiquant que les données d’origine ont été reçues, provoquant des retards.

#### <a name="tools"></a>Outils

- Moniteur
- Wireshark

#### <a name="what-to-look-for"></a>Éléments à rechercher

Recherchez le trafic SYN-SYN/ACK dans votre suivi réseau.  Dans NetMon, utilisez un filtre comme `tcp.flags.syn == 1`. Ce filtre est le même dans Wireshark.  

![Filtre dans Netmon ou Wireshark pour les paquets SYN pour les deux outils : TCP. Flags. syn = = 1.](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Notez que, pour chaque SYN, il existe un numéro de port source (SrcPort) qui est mis en correspondance dans le port de destination (DstPort) de l’accusé de réception associé (SYN/ACK).

Pour afficher la valeur de mise à l’échelle Windows utilisée par votre connexion réseau, développez d’abord le SYN, puis le SYN/ACK associé.  

![Graphique montrant comment faire correspondre SrcPort à DstPort dans un suivi, pour obtenir le delta de temps.](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>Paramètres de durée d’inactivité TCP

Traditionnellement, la plupart des réseaux de périmètre sont configurés pour les connexions temporaires, ce qui signifie que les connexions inactives sont généralement terminées. Les sessions TCP inactives peuvent se terminer par des proxys et des pare-feu dont la taille est supérieure à 100 à 300 secondes. Cela pose problème pour Outlook Online, car il crée et utilise des connexions à long terme, qu’ils soient inactifs ou non.  

Lorsque les connexions sont terminées par des périphériques proxy ou pare-feu, le client n’est pas informé et une tentative d’utilisation d’Outlook Online signifie qu’un ordinateur client essaiera, de manière répétée, de rétablir la connexion avant d’en créer une nouvelle. Le produit, les invites ou le ralentissement des performances lors du chargement de la page peuvent apparaître.

#### <a name="tools"></a>Outils

- Moniteur
- Wireshark

#### <a name="what-to-look-for"></a>Éléments à rechercher

Dans NetMon, examinez le champ décalage temporel d’un aller-retour. Un aller-retour est le temps écoulé entre le client envoyant une demande au serveur et la réception d’une réponse. Vérifiez le client et le point de sortie (par exemple, Client--\> proxy) ou le client vers Office 365 (client--\> Office 365). Vous pouvez le voir dans la plupart des types de paquets.

Par exemple, le filtre de Netmon peut ressembler `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`ou, dans Wireshark, `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.  

> [!TIP]
> Vous ne saurez pas si l’adresse IP de votre suivi appartient à votre serveur DNS ? Essayez de le trouver sur la ligne de commande. Cliquez sur **Démarrer** \> **,** \> puis tapez **cmd**ou appuyez sur la **touche** \> Windows et tapez **cmd**. À l’invite, tapez `nslookup <the IP address from the network trace>`. Pour tester, utilisez nslookup sur l’adresse IP de votre propre ordinateur. > pour afficher la liste des plages d’adresses IP de Microsoft, consultez la rubrique [Office 365 URL and IP address Ranges](https://technet.microsoft.com/library/hh373144.aspx).

S’il y a un problème, attendez que des décalages longs apparaissent, dans ce cas (Outlook Online), en particulier dans TLS : les paquets TLS qui montrent le passage des données d’application (par exemple, dans NetMon, vous pouvez trouver des `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`paquets de données d’application via). Vous devriez voir une progression progressive dans le temps pendant la session. Si vous constatez des délais longs lors de l’actualisation de votre Outlook Online, cela peut être dû à l’envoi d’un niveau élevé de réinitialisations.

### <a name="latencyround-trip-time"></a>Durée de la latence/boucle

La latence est une mesure qui peut modifier un lot en fonction de nombreuses variables, telles que la mise à niveau des appareils d’antériorité, l’ajout d’un grand nombre d’utilisateurs à un réseau et le pourcentage de bande passante globale consommée par d’autres tâches sur une connexion réseau.

Il existe des calculatrices de bande passante pour Office 365 disponible à partir de cette page [planification et optimisation des performances pour office 365](network-planning-and-performance.md) .  

Vous avez besoin de mesurer la vitesse de votre connexion ou la bande passante de votre connexion ISP ? Essayez ce site (ou des sites similaires) : [site officiel speedtest](https://www.speedtest.net/), ou interrogez votre moteur de recherche favori pour le test de la **Vitesse**de l’expression.

#### <a name="tools"></a>Outils

- Interroge
- PsPing
- Moniteur
- Wireshark

#### <a name="what-to-look-for"></a>Éléments à rechercher

Pour suivre la latence dans un suivi, vous pouvez avoir enregistré l’adresse IP de l’ordinateur client et l’adresse IP du serveur DNS dans Office 365. Ceci est destiné à faciliter le filtrage du suivi. Si vous vous connectez via un proxy, vous aurez besoin de l’adresse IP de votre ordinateur client, de l’adresse IP proxy/sortie et de l’adresse IP DNS de l’Office 365 pour faciliter le travail.  

Une requête ping envoyée à outlook.office365.com vous indique le nom du centre de donneur qui reçoit la demande, même si la commande ping ne *peut* pas se connecter pour envoyer la marque de paquets ICMP consécutifs. Si vous utilisez PsPing (outil gratuit pour le téléchargement) et que vous souhaitez utiliser le port (443), et peut-être utiliser IPv4 (-4), vous obtiendrez un temps d’aller-retour moyen pour les paquets envoyés. Cela fonctionnera pour les autres URL dans les services Office 365, comme `psping -4 yourSite.sharepoint.com:443`. En fait, vous pouvez spécifier un nombre de commandes ping pour obtenir un échantillon plus large pour votre moyenne, essayer une `psping -4 -n 20 yourSite-my.sharepoint.com:443`autre solution.  

> [!NOTE]
> PsPing n’envoie pas de paquets ICMP. Il envoie une commande ping avec des paquets TCP sur un port spécifique, de sorte que vous pouvez utiliser l’un de ceux que vous connaissez comme étant ouverts. Dans Office 365, qui utilise SSL/TLS, essayez d’attacher le port : 443 à votre PsPing.

![Capture d’écran illustrant un test de résolution des problèmes de outlook.office365.com et PSPing avec le 443, qui fait de même, mais signalent également un temps RTT moyen de 6,5 ms.](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Si vous avez chargé la page Office 365 à faible exécution lors d’une trace réseau, vous devez filtrer un Netmon ou un `DNS`suivi Wireshark pour. Il s’agit de l’une des adresses IP que nous recherchons.  

Voici les étapes à suivre pour filtrer votre Netmon afin d’obtenir l’adresse IP (et jetez un œil à la latence DNS). Cet exemple utilise outlook.office365.com, mais peut également utiliser l’URL d’un client SharePoint Online (hithere.sharepoint.com par exemple).  

1. Exécutez une commande `ping outlook.office365.com` ping sur l’URL et, dans les résultats, enregistrez le nom et l’adresse IP du serveur DNS auquel la demande Ping a été envoyée.
2. Suivi réseau l’ouverture de la page, ou l’exécution de l’action qui vous donne le problème de performances, ou si vous voyez une latence élevée sur le ping, lui-même, suivi du réseau.
3. Ouvrez le suivi dans Netmon et filtre pour DNS (ce filtre fonctionne également dans Wireshark, mais il est sensible à `-- dns`la casse). Étant donné que vous connaissiez le nom du serveur DNS de votre ping, vous pouvez également filtrer plus rapidement dans Netmon comme `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`suit :, qui se présente comme suit dans Wireshark DNS et frame contient « namnorthwest ».<br/>Ouvrez le paquet de réponse, puis, dans la fenêtre **Détails de trame** NetMon, cliquez sur **DNS** pour développer plus d’informations. Dans les informations DNS, vous trouverez l’adresse IP du serveur DNS vers lequel la demande est passée dans Office 365. Vous aurez besoin de cette adresse IP pour l’étape suivante (l’outil PsPing). Supprimez le filtre, cliquez avec le bouton droit sur la réponse DNS dans Netmon (**Résumé** \> des trames **Rechercher** \> **DNS**) pour afficher la requête DNS et la réponse côte à côte.
4. Dans NetMon, Notez également la colonne décalage horaire entre la demande DNS et la réponse. Dans l’étape suivante, l’outil de [PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx) facile à installer et à utiliser est très utile, car ICMP est souvent bloqué sur les pare-feu, et dans la mesure où PsPing suit de manière élégante la latence en millisecondes. PsPing termine une connexion TCP à une adresse et un port (dans notre cas, ouvrez le port 443).
5. Installez PsPing.
6. Ouvrez une invite de commandes ( \> Start \> Run type cmd ou Windows Key \> type cmd) et modifiez Directory dans le répertoire où vous avez installé PsPing pour exécuter la commande PsPing. Dans mes exemples, j’ai créé un dossier « perf » à la racine de C. Vous pouvez effectuer la même opération pour un accès rapide.
7. Tapez la commande pour effectuer votre PsPing par rapport à l’adresse IP du serveur DNS Office 365 à partir de votre trace Netmon précédente, y compris le numéro de port `psping -n 20 132.245.24.82:445`, comme. Vous obtiendrez ainsi un échantillon de 20 pings et la latence moyenne lors de l’arrêt d’PsPing.

Si vous accédez à Office 365 via un serveur proxy, les étapes sont légèrement différentes. Vous devez d’abord PsPing sur votre serveur proxy pour obtenir une valeur de latence moyenne en millisecondes pour proxy/sortie et retour, puis exécutez PsPing sur le proxy ou sur un ordinateur disposant d’une connexion Internet directe pour obtenir la valeur manquante (celle à Office 365 et inversement).  

Si vous choisissez d’exécuter PsPing à partir du proxy, vous aurez deux millisecondes : ordinateur client à proxy ou point de sortie, et serveur proxy vers Office 365. Et vous avez fini ! Enregistrez les valeurs, quand même.  

Si vous exécutez PsPing sur un autre ordinateur client disposant d’une connexion directe à Internet, c’est-à-dire sans proxy, vous aurez deux millisecondes : ordinateur client à proxy ou point de sortie, et ordinateur client vers Office 365. Dans ce cas, soustrayez la valeur de l’ordinateur client au serveur proxy ou de sortie de la valeur de l’ordinateur client vers Office 365, et vous aurez les chiffres RTT de votre ordinateur client vers le serveur proxy ou vers le point de sortie, ainsi qu’entre Proxy Server ou sortie pointer vers offi ce 365.

Toutefois, si vous trouvez un ordinateur client dans l’emplacement concerné directement connecté ou si vous contournez le proxy, vous pouvez choisir de voir si le problème se reproduit et de le tester par la suite.

Latence, comme dans un suivi NetMon, ces millisecondes supplémentaires peuvent être additionnées s’il y en a suffisamment dans une session donnée.  

![Latence générale dans Netmon, avec la colonne Délai par défaut Netmon ajoutée au Résumé de la trame.](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Votre adresse IP peut être différente de celle indiquée ici, par exemple, votre commande ping peut renvoyer une valeur similaire à 157.56.0.0/16 ou à une plage similaire. Pour obtenir la liste des plages utilisées par Office 365, consultez les [URL et les plages d’adresses IP office 365](https://technet.microsoft.com/library/hh373144.aspx).

N’oubliez pas de développer tous les nœuds (il y a un bouton en haut de la page) si vous souhaitez effectuer une recherche, par exemple, 132,245.

### <a name="proxy-authentication"></a>Authentification par proxy

Ceci s’applique uniquement si vous passez par un serveur proxy. Si ce n’est pas le cas, vous pouvez ignorer ces étapes. Lorsque le travail fonctionne correctement, l’authentification proxy doit être effectuée en millisecondes, de manière cohérente. Vous ne devriez pas voir les performances incorrectes intermittentes pendant les périodes d’utilisation maximale (par exemple).  

Si l’authentification proxy est activée, chaque fois que vous créez une nouvelle connexion TCP à Office 365 pour obtenir des informations, vous devez passer par un processus d’authentification en arrière-plan. Ainsi, par exemple, lors du passage de calendrier à courrier dans Outlook Online, vous vous authentifiez. Dans SharePoint Online, si une page affiche des médias ou des données à partir de plusieurs sites ou emplacements, vous vous authentifiez pour chaque connexion TCP requise pour le rendu des données.  

Dans Outlook Online, il se peut que vous rencontriez des temps de chargement lents à chaque fois que vous basculez entre le calendrier et votre boîte aux lettres, ou chargez lentement la page dans SharePoint Online. Toutefois, il existe d’autres symptômes non répertoriés ici.

L’authentification proxy est un paramètre de votre serveur proxy de sortie. Si elle provoque un problème de performances avec Office 365, vous devez consulter votre équipe réseau.  

#### <a name="tools"></a>Outils

- Moniteur
- Wireshark

#### <a name="what-to-look-for"></a>Éléments à rechercher

L’authentification par proxy a lieu chaque fois qu’une nouvelle session TCP doit être lancée, généralement pour demander des fichiers ou des informations à partir du serveur, ou pour fournir des informations. Par exemple, vous pouvez voir l’authentification proxy pour les requêtes HTTP GET ou HTTP POST. Si vous souhaitez voir les cadres dans lesquels vous authentifiez les demandes dans votre suivi, ajoutez la colonne « Résumé NTLMSSP » à netmon et filtrez `.property.NTLMSSPSummary`. Pour connaître la durée de l’authentification, ajoutez la colonne Delta du temps.

Pour ajouter une colonne à netmon :

1. Cliquez avec le bouton droit sur une colonne telle que **Description**.
2. Cliquez sur **choisir des colonnes**.
3. Recherchez le _Résumé NTLMSSP_ et le _delta de temps_ dans la liste, puis cliquez sur **Ajouter**.
4. Déplacez les nouvelles colonnes en place avant ou après la colonne _Description_ afin de pouvoir les lire côte à côte.
5. Cliquez sur **OK**.

Même si vous n’ajoutez pas la colonne, le filtre Netmon fonctionnera. Toutefois, votre dépannage est beaucoup plus facile si vous pouvez voir l’étape de l’authentification dans laquelle vous vous trouvez.

Lorsque vous recherchez des instances de l’authentification proxy, veillez à étudier toutes les trames pour lesquelles il existe une stimulation NTLM, ou un message d’authentification est présent. Si nécessaire, cliquez avec le bouton droit sur l’élément de trafic spécifique \> et recherchez TCP conversations. Gardez à l’esprit les valeurs Delta Time de ces conversations.

![Suivi Netmon montrant l’authentification proxy, filtré par conversation.](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Un délai de quatre secondes dans l’authentification proxy, comme indiqué dans Wireshark. Le **delta du temps à partir de la colonne image affichée précédente** a été effectué en cliquant avec le bouton droit sur le champ du même nom dans les détails du cadre et en sélectionnant Ajouter en tant que colonne.  <br/> ![Dans Wireshark, la colonne « temps Delta de l’image affichée précédente » peut être effectuée en cliquant avec le bouton droit sur le champ du même nom dans les détails du cadre et en sélectionnant Ajouter en tant que colonne.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>Performances DNS

La résolution de noms fonctionne de manière optimale et la plus rapide quand elle se trouve à proximité du pays du client.

Si la résolution de noms DNS a lieu à l’étranger, elle peut ajouter des secondes au chargement de la page. Idéalement, la résolution de noms se produit sous 100 millisecondes. Si ce n’est pas le cas, vous devez procéder à une nouvelle enquête.

> [!TIP]
> Vous ne savez pas comment fonctionne la connectivité client dans Office 365 ? Consultez [ici](https://technet.microsoft.com/library/dn741250.aspx)le document de référence de connectivité client.

#### <a name="tools"></a>Outils

- Moniteur
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Éléments à rechercher

L’analyse des performances DNS est généralement un autre travail pour un suivi réseau. Toutefois, PsPing est également utile dans le cas d’une cause possible.

Le trafic DNS est basé sur les requêtes TCP et UDP, et les réponses sont clairement signalées par un ID permettant de faire correspondre une demande spécifique à sa réponse spécifique. Vous verrez le trafic DNS lorsque, par exemple, SharePoint Online utilise un nom de réseau ou une URL sur une page Web. En règle générale, la majeure partie de ce trafic, sauf lors du transfert de zones, s’exécute via UDP.

Dans Netmon et Wireshark, le filtre le plus élémentaire qui vous permettra d’examiner le trafic DNS est simplement `dns`. Veillez à utiliser les minuscules lorsque vous spécifiez le filtre. N’oubliez pas de vider votre cache de résolution DNS avant de commencer à reproduire le problème sur votre ordinateur client. Par exemple, si vous avez une charge de pages SharePoint Online lente pour la page d’accueil, fermez tous les navigateurs, ouvrez un nouveau navigateur, démarrez le suivi, videz le cache de résolution DNS et accédez à votre site SharePoint Online. Une fois la page entière résolue, vous devez arrêter et enregistrer la trace.

![Un filtre de base pour DNS dans Netmon est DNS.](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Vous souhaitez consulter le décalage temporel ici. Et il peut être utile d’ajouter la colonne **Delta Time** à netmon en procédant comme suit :

1. Cliquez avec le bouton droit sur une colonne telle que **Description**.
2. Cliquez sur **choisir des colonnes**.
3. Recherchez _delta de temps_ dans la liste, puis cliquez sur **Ajouter**.
4. Déplacez la nouvelle colonne en place avant ou après la colonne _Description_ afin de pouvoir les lire côte à côte.
5. Cliquez sur **OK**.

Si vous trouvez une requête d’intérêt, envisagez de l’isoler en cliquant avec le bouton droit sur cette requête dans le panneau Détails du cadre, puis en choisissant Rechercher le **DNS**des **conversations** \> . Notez que le panneau conversations réseau passe directement à la conversation spécifique dans son journal de trafic UDP.

![Un suivi Netmon de la charge d’Outlook Online filtré par DNS et l’utilisation de rechercher des conversations puis du DNS pour limiter les résultats.](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

Dans Wireshark, vous pouvez créer une colonne pour les heures de DNS. Effectuez votre suivi (ou ouvrez un suivi) dans Wireshark et filtrez `dns`-le ou, plus particulièrement, `dns.time`. Cliquez sur une requête DNS, puis, dans le volet affichant les détails, développez les `Domain Name System (response)` détails. Vous verrez un champ pour l’heure (par exemple `[Time: 0.001111100 seconds]`,. Cliquez avec le bouton droit sur cette heure et sélectionnez **appliquer en tant que colonne**. Cela vous **permettra de créer un tri** plus rapide de votre suivi. Cliquez sur la nouvelle colonne pour trier les valeurs décroissantes afin de déterminer quel appel DNS a pris le plus de temps à résoudre.

[Une recherche sur SharePoint Online filtrée dans Wireshark par dns.time (en minuscules), avec l’heure des détails dans une colonne et triée par ordre croissant.](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Si vous souhaitez approfondir le temps de résolution DNS, essayez d’effectuer une PsPing sur le port DNS utilisé par TCP (par exemple, `psping <IP address of DNS server>:53`). Y a-t-il toujours un problème de performances ? Dans ce cas, le problème est plus vraisemblablement lié à un problème réseau plus large que le problème de l’application DNS que vous envisagez de résoudre. Il est également important de mentionner, là encore, qu’un ping vers outlook.office365.com vous indique où se déroule la résolution de noms DNS pour Outlook Online (par exemple, outlook-namnorthwest.office365.com).

Si le problème semble spécifique à DNS, il peut être nécessaire de contacter votre service informatique pour examiner les configurations DNS et les redirecteurs DNS afin d’examiner ce problème.

### <a name="proxy-scalability"></a>Évolutivité des proxys

Les services tels qu’Outlook Online dans Office 365 accordent aux clients plusieurs connexions à long terme. Par conséquent, chaque utilisateur peut utiliser plus de connexions qui nécessitent une durée de vie plus longue.  

#### <a name="tools"></a>Outils

Mathématiques  

#### <a name="what-to-look-for"></a>Éléments à rechercher

Il n’existe aucun outil de suivi ou de dépannage réseau spécifique à ce. Au lieu de cela, il est basé sur des calculs de bande passante et d’autres variables.  

### <a name="tcp-max-segment-size"></a>Taille maximale du segment TCP

Trouvé dans le SYN-SYN/ACK.  Effectuez cette vérification dans le suivi du réseau de performances que vous avez utilisé pour vous assurer que les paquets TCP sont configurés pour transporter la quantité maximale de données possible.

L’objectif est d’afficher un MSS de 1460 octets pour la transmission des données. Si vous êtes protégé par un proxy, ou si vous utilisez un NAT, n’oubliez pas d’exécuter ce test depuis le client vers proxy/sortie/NAT, et de proxy/sortie/NAT vers Office 365 pour obtenir les meilleurs résultats ! Il s’agit de différentes sessions TCP.

#### <a name="tools"></a>Outils

Moniteur

#### <a name="what-to-look-for"></a>Éléments à rechercher

La taille maximale de segment TCP (MSS) est un autre paramètre de la connexion à trois voies dans votre suivi réseau, ce qui signifie que vous trouverez les données dont vous avez besoin dans le paquet SYN-SYN/ACK. MSS est en fait relativement simple à voir.

Ouvrez le suivi du réseau de performances dont vous disposez et trouvez la connexion que vous êtes curieux, ou qui illustre le problème de performances.

> [!NOTE]
> Si vous examinez un suivi et devez trouver le trafic correspondant à votre conversation, filtrez par l’IP du client ou l’adresse IP du serveur proxy ou du point de sortie, ou les deux. En accédant directement, vous devrez effectuer un test ping de l’URL que vous testez pour l’adresse IP d’Office 365 dans le suivi, et filtrer par celle-ci.

Vous regardez le second stock de suivi ? Essayez d’utiliser des filtres pour vous orienter. Dans NetMon, exécutez une recherche basée sur l’URL, par exemple `Containsbin(framedata, ascii, "sphybridExample")`, notez le numéro de trame.

Dans Wireshark, utilisez des `frame contains "sphybridExample"`éléments comme. Si vous remarquez que vous avez trouvé le trafic Winsock (RWS) distant (il peut apparaître sous la forme [PSH, ACK] dans Wireshark), rappelez-vous que RWS connections peuvent être vues peu de points de SYN-SYN/ACK pertinents, comme indiqué précédemment.

À ce stade, vous pouvez enregistrer le numéro d’image, déposez le filtre, cliquez sur **tout le trafic** dans la fenêtre des conversations réseau dans Netmon pour examiner le syn le plus proche.

En outre, si vous n’avez pas reçu les informations d’adresse IP au moment du suivi, la recherche de votre URL dans le suivi (partie `sphybridExample-my.sharepoint.com`de, par exemple) vous donnera des adresses IP pour le filtrage.

Localisez la connexion dans le suivi que vous souhaitez voir. Pour ce faire, vous pouvez analyser le suivi, en le filtrant par adresse IP, ou en sélectionnant des ID de conversation spécifiques à l’aide de la fenêtre de conversation réseau dans Netmon. Une fois que vous avez trouvé le paquet SYN, développez TCP (dans NetMon) ou protocole de contrôle de transmission (dans Wireshark) dans le panneau de détails de trame. Développez options et MaxSegmentSize. Localisez le cadre SYN-ACK associé et développez options TCP et MaxSegmentSize. La plus petite des deux valeurs correspond à la taille maximale de votre segment. Dans cette illustration, j’utilise la colonne intégrée dans Netmon appelée TCP Troubleshoot.  

![Suivi réseau filtré dans Netmon à l’aide des colonnes intégrées.](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

La colonne intégrée se trouve en haut du panneau Détails du **cadre** . (Pour revenir à l’affichage normal, cliquez à nouveau sur **colonnes** , puis choisissez **fuseau horaire**.)

![Où trouver la liste déroulante des colonnes pour l’option Résolution des problèmes TCP (en haut du résumé de la trame).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Voici un suivi filtré dans Wireshark. Il existe un filtre spécifique à la valeur MSS ( `tcp.options.mss`). Les trames d’une négociation SYN, SYN/ACK et ACK sont liées au bas de l’équivalent Wireshark aux détails des trames (de sorte que frame 47 ACK, des liens vers 46 SYN/ACK, des liens vers 43 SYN) pour faciliter cette tâche.

![Suivi filtré dans Wireshark par TCP. options. MSS pour max segment Size (MSS).](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Si vous devez vérifier l' **accusé de réception sélectif** (rubrique suivante de cette matrice), ne fermez pas votre trace !

### <a name="selective-acknowledgment"></a>Accusé de réception sélectif

Trouvé dans le SYN-SYN/ACK. Doit être signalé comme autorisé dans les protocoles SYN et SYN/ACK. L’accusé de réception sélectif (SACK) permet une retransmission plus fluide des données lorsqu’un paquet ou des paquets sont manquants. Les appareils peuvent désactiver cette fonctionnalité, ce qui peut entraîner des problèmes de performances.

Si vous êtes protégé par un proxy, ou si vous utilisez un NAT, n’oubliez pas d’exécuter ce test depuis le client vers proxy/sortie/NAT, et de proxy/sortie/NAT vers Office 365 pour obtenir les meilleurs résultats ! Il s’agit de différentes sessions TCP.

#### <a name="tools"></a>Outils

Moniteur

#### <a name="what-to-look-for"></a>Éléments à rechercher

L’accusé de réception sélectif (SACK) est un autre paramètre dans le protocole de transfert SYN-SYN/ACK. Vous pouvez filtrer votre suivi pour SYN-SYN/ACK de nombreuses façons.

Localisez la connexion dans le suivi qui vous intéresse en analysant le suivi, en filtrant par adresse IP ou en cliquant sur un ID de conversation en utilisant la fenêtre conversations réseau dans Netmon. Une fois que vous avez trouvé le paquet SYN, développez TCP dans Netmon ou protocole de contrôle de transmission dans Wireshark dans la section Détails des cadres. Développez options TCP, puis SACK. Localisez le cadre SYN-ACK associé et développez options TCP et son champ SACK. La création d’un sac est autorisée dans les protocoles SYN et SYN/ACK. Voici les valeurs SACK telles qu’elles apparaissent dans Netmon et Wireshark.

![Accusé de réception sélectif (SACK) dans Netmon suite à TCP. Flags. syn = = 1.](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![SACK comme dans Wireshark avec le filtre tcp.flags.syn == 1.](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>Géolocalisation DNS

Où dans le monde d’Office 365 tente de résoudre vos effets d’appels DNS en votre vitesse de connexion.

Dans Outlook Online, une fois la première recherche DNS terminée, l’emplacement de ce DNS est utilisé pour se connecter à votre centre de centres le plus proche. Vous serez connecté à un serveur CAS Outlook Online, qui utilisera le réseau fédérateur pour se connecter au centre de données où vos données sont stockées. Cela est plus rapide.

Lors de l’accès à SharePoint Online, un utilisateur qui voyage à l’étranger est dirigé vers son centre de ligne de service actif, c’est-à-dire le contrôleur de service dont l’emplacement est basé sur la base d’origine de son locataire SPO (ainsi, un contrôleur de réseau aux États-Unis si l’utilisateur est basé sur les États-Unis).

Lync Online dispose de nœuds actifs dans plusieurs contrôleurs de service à la fois. Lorsque des demandes sont envoyées pour des instances Lync Online, le service DNS de Microsoft détermine l’origine de la demande et renvoie des adresses IP à partir du contrôleur de domaine régional le plus proche où Lync Online est actif.

> [!TIP]
> Vous avez besoin d’en savoir plus sur la façon dont les clients se connectent à Office 365 ? Jetez un œil à l’article de référence de [connectivité client](https://technet.microsoft.com/library/dn741250.aspx) (et ses graphiques utiles).

#### <a name="tools"></a>Outils

- Interroge
- PsPing

#### <a name="what-to-look-for"></a>Éléments à rechercher

Les demandes de résolution de nom provenant des serveurs DNS du client sur les serveurs DNS de Microsoft doivent, dans la plupart des cas, entraîner le renvoi par Microsoft DNS de l’adresse IP d’un centre de donnees régional. Qu’est-ce que cela signifie pour vous ? Si votre siège se trouve à Bangalore, en Inde, mais que vous êtes en déplacement aux États-Unis, lorsque votre navigateur envoie une demande pour Outlook Online, les serveurs DNS de Microsoft doivent transmettre vos adresses IP aux centres de centres aux États-Unis, un centre de donnees régional. Si des messages sont nécessaires à partir d’Outlook, ces données transitent sur le réseau principal rapide de Microsoft entre les centres de données.

Le DNS est plus rapide lorsque la résolution de noms est utilisée aussi près que possible de l’emplacement de l’utilisateur. Si vous êtes en Europe, vous souhaitez accéder à un DNS Microsoft en Europe et (idéalement) traiter un centre de donne en Europe. Les performances d’un client en Europe accédant à DNS et à un centre de centre d’Amérique seront plus lentes.

Exécutez l’outil ping sur outlook.office365.com pour déterminer où le monde de votre demande DNS est acheminé. Si vous êtes en Europe, vous devriez voir une réponse d’un peu comme outlook-emeawest.office365.com. En Amérique, attendez-vous à outlook-namnorthwest.office365.com.

Ouvrez l’invite de commandes sur l’ordinateur client (via \> Start \> Run cmd ou Windows \> Key type cmd). Tapez ping outlook.office365.com, puis appuyez sur entrée. N’oubliez pas d’indiquer-4 Si vous voulez demander la commande ping via IPv4. Vous pouvez ne pas obtenir de réponse des paquets ICMP, mais vous devez voir le nom du DNS vers lequel la demande a été routée. Si vous souhaitez afficher les numéros de latence pour cette connexion, essayez PsPing à l’adresse IP du serveur renvoyé par ping.  

![Commande ping d’outlook.office365.com affichant la résolution dans outlook-namnorthwest.](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing à l’adresse IP renvoyée par la commande ping vers outlook.office365.com avec une latence moyenne de 28 millisecondes.](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Résolution des problèmes liés aux applications Office 365

#### <a name="tools"></a>Outils

- Moniteur
- HTTPWatch
- Console F12 dans le navigateur

Nous n’aborderons pas les outils utilisés dans la résolution des problèmes spécifiques aux applications dans cet article propre au réseau. Toutefois, vous trouverez les ressources que vous *pouvez* utiliser [sur cette page](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
