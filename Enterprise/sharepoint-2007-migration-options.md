---
title: Options de migration de SharePoint 2007 à prendre en compte
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 a atteint la fin du support, et il est temps de mise à niveau. Utilisez cet article pour vous aider à créer votre plan.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169876"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Options de migration de SharePoint 2007 à prendre en compte

Microsoft SharePoint 2007 et SharePoint Server 2007 ont atteint la fin de la prise en charge. Il est temps de mise à niveau ! Cet article fournit des informations sur les options de migration.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Stratégies de mise à niveau courantes pour SharePoint

Il existe plusieurs méthodes de mise à niveau d’un environnement SharePoint Server. Si vous disposez d’une batterie de serveurs Microsoft Office SharePoint Server 2007, voici quelques exemples des méthodes de mise à niveau :
  
- Liaison de bases de données
    
- Mise à niveau côte à côte
    
- Mise à niveau sur place
    
- Mise à niveau hybride (sur place avec bases de données détachées / distincts par attachement de base de données)
    
- Hybrides SharePoint (connexion à SharePoint sur site et en ligne)
    
- Déplacer manuellement les données entre les collections de sites ou des bibliothèques
    
- Assistant FastTrack mise à niveau vers Office 365 ([Gestionnaire de déploiement SharePoint Online](https://aka.ms/spoguidance))
    
- API de migration pour SharePoint Online (SPO) dans Office 365
    
Ce qui convient le mieux ?
  
Vos connaissances de votre batterie de serveurs fait et est utilisé pour est une puissance tactique lorsqu’il s’agit de mise à niveau. La façon dont les personnes utilisent la batterie de serveurs SharePoint vous aidera à choisir parmi les options.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 a également une mise à niveau progressive ne sont-elles ne pas décrites ici. Pour afficher la liste de mise à niveau spécifiques à l’étape articles voir la [fin de SharePoint Server 2007 de prendre en charge la feuille de route](sharepoint-2007-end-of-support.md). 
  
N’oubliez pas de vérifier le [Cycle de vie du produit](https://support.microsoft.com/en-us/lifecycle/search) et la configuration système requise pour la version de SharePoint, vous mettez à niveau vers. Ainsi, vous allez à l’esprit lors de la prochaine mise à niveau sera nécessaire (par exemple, si vous placez un produit hérité comme SharePoint Server 2010 pour planifier les mises à niveau plus, vous devez connaître sa date de fin du support technique que) et de vous assurer que vous disposez de matériel qui prend en charge votre plan. 
  
Si vous projetez de transition certains ou tous, vos sites SharePoint vers Office 365 dans le nuage, il s’agit d’une durée de signets un lien vers les [Descriptions de Service pour Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Vous devez les Descriptions de Service pour en savoir plus sur les fonctionnalités de SharePoint Online et comment ils peuvent différer sur site SharePoint Server. Mise à niveau fonctionnels Microsoft Office SharePoint Server 2007 batteries de serveurs. Si votre installation a sites risquent d’être endommagés, corrigez-les avant la mise à niveau.
  
## <a name="a-note-about-managing-risk"></a>Une remarque à propos de la gestion des risques

Les méthodes telles que côte-à-côte sont importants dans le schéma de la logique de mise à niveau. Lorsque vous mettez à niveau côte à côte, vous gérer votre batterie de serveurs Microsoft Office SharePoint Server 2007, mais créiez une batterie de serveurs la prochaine version de celle-ci (SharePoint Server 2010) sur le nouveau matériel. Cela permet de trois manières :
  
1. Vous avez un emplacement pour effectuer des sauvegardes de vos bases de données Microsoft Office SharePoint Server 2007 pour mettre à niveau séparément, à l’aide de base de données de joindre.
    
2. Si vous déterminez qu’uniquement un petit nombre de bibliothèques de documents critiques et d’autres informations sont utilisées dans votre batterie de serveurs Microsoft Office SharePoint Server 2007, vous pouvez choisir déplacer manuellement les données à partir de Microsoft Office SharePoint Server 2007 vers SharePoint Server 2010 , ou uniquement des sites et des sites Web à la prochaine version (ce qui peut faciliter votre travail).
    
3. Moins vous en faites à le Microsoft Office SharePoint Server 2007 batterie de serveurs, directement, le plus sûre contient les mettre à niveau les données de la batterie.
    
Méthodes de mise à niveau sur Place agira directement sur votre batterie de serveurs Microsoft Office SharePoint Server 2007, ce qui vous moins facile d’options pour abandonner un chemin d’accès et de commencer à nouveau votre environnement vierge. Créez autant que possible, dans certaines des mesures de sécurité (comme prenant et test des sauvegardes de l’environnement d’origine). Par exemple, si votre batterie de serveurs Microsoft Office SharePoint Server 2007 est virtuel et il est dupliqué à des fins de sauvegarde et restauration, puis sauvegarder et restaurer les bases de données plus récentes avant votre fenêtre de service pour la mise à niveau. Sachant que vous avez la possibilité pour restaurer la base de données de sauvegardes ne le pourront pas uniquement vous fournir une tolérance de pannes, il peut vous fournir tranquille.
  
> [!TIP]
> Documents de meilleures pratiques pour la mise à niveau existent pour [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)et [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). Vous pouvez également rechercher des [Partenaires Microsoft](https://partnercenter.microsoft.com/en-us/pcv/search) familiarisés avec les mises à niveau ou les migrations Office 365. 
  
## <a name="make-your-plan"></a>Rendre votre plan

Si vous devez mettre à niveau, vous avez besoin d’un plan et une taille ne tient pas dans ces cas. Votre plan peut être aussi simple que « Créer un abonnement à Office 365 avec SharePoint Online, enregistrer un domaine et rediriger les personnes pour enregistrer leurs fichiers ». Et il ne peut pas être. La décision vous appartient et il est jusqu'à ce que vous et vos utilisateurs vraiment besoin.
  
> [!NOTE]
> Il est déconseillé d’exécuter sur le logiciel dont cycle de vie est terminée. Les produits qui se trouvent en dehors de la prise en charge sont corrigés ne sont plus lorsque des problèmes sont détectés. Cela signifie également qu’en cas de nouvelles menaces de sécurité, il n’y aura aucun des correctifs de sécurité ou de car les produits de fin du cycle de vie ne sont plus pris en charge. Veuillez éviter cette situation ! 
  
### <a name="first-know-your-farm"></a>Tout d’abord, connaître votre batterie de serveurs

Lors de la mise à niveau, votre prise de décision doit être basée sur ce que fait votre batterie de serveurs pour votre organisation. Quel besoin qu’il satisfait ? Quel est son rôle ? Chaque batterie de serveurs de votre entreprise peut avoir un rôle différent. Certains de vos batteries de serveurs SharePoint peuvent être *critique* , certaines peuvent être des fichiers d’archives--là sûr. Ou, si votre batterie de serveurs remplit plusieurs rôles à la fois, vous devrez connaître faire les collections de sites, sites Web ou même des bibliothèques de documents, les personnalisations, et importance. Analyse de vos données à ce niveau peut sembler beaucoup de travail, mais il gagner du temps et des efforts de maîtriser votre domaine avant de mettre à niveau ou à la migration, il. Une fois que vous connaissez tous les composants de déplacement et les fichiers binaires principaux, vous saurez également que vous avez atteint limites et pourrez laisser. Que la base de connaissances bénéficiera seulement vous allez transférer. 
  
Par conséquent, les utilisateurs témoignages est plus importante sur votre batterie de serveurs SharePoint ?
  
- Fonctionnalités SharePoint intégrées
    
- Le corpus de données de grande taille (par exemple une archive de fichiers)
    
- Disponibilité
    
- Applications critiques, des composants WebPart ou des documents dans la batterie de serveurs (batterie critique Mission)
    
- Les normes de conformité remplies
    
- Personnalisations
    
Si vous exécutez un élément essentiel pour votre entreprise à partir de votre batterie de serveurs SharePoint, par exemple il se comporte comme un catalogue de données critiques sur la configuration requise du service client volumineux, peuvent placer une coche en regard de « Applications critiques », mais également serait « Disponibilité »--autrement dit, votre entreprise affecté si vous n’a pas pu utiliser SharePoint pendant un certain temps. De même, vous pouvez vérifier 'Personnalisations' car la critique services de votre batterie de serveurs offre basés sur code personnalisé, les définitions de site ou un certain nombre de personnalisations qui fonctionnent ensemble.
  
Si SharePoint répondent à ces besoins sans avoir à faire tout ce qu’à l’extérieur de l’aide qu’est intégrée au logiciel et vous généralement le mettre à jour et exécutez normale administration et de maintenance, vous avez choisi « SharePoint intégrés » : cela peut également être votre raison du assis sur une version antérieure de SharePoint. En d’autres termes, il fait déjà ce que vous le souhaitez, et vous n’avez pas encore nécessaires pour mettre à niveau jusqu'à maintenant, à Microsoft Office SharePoint Server 2007 fin du support.
  
Lorsque vous liste à puces ces éléments, vous créez des critères pour la mise à niveau. En d’autres termes, toute mise à niveau aurait répondre à cette barre à prendre en compte. Cela vous donne un moyen pour les méthodes qui ne rentrent pas actuellement vos besoins en matière de la règle.
  
### <a name="a-simple-sample-plan"></a>Un exemple simple de plan

Il devront peut-être être plus large consensus avec des cadres dirigeants et autres administrateurs sur le chemin d’accès que prendra votre mise à niveau de SharePoint. Les administrateurs SharePoint Server souvent collaborer avec les administrateurs de Microsoft SQL Server, travailler avec des équipes réseau et de sécurité et bien plus encore. S’il existe un grand nombre de participants, vous devrez peut-être créer contrat pour ou régler, votre plan de mise à niveau et migration. Par exemple, si vous migrez les données afin que la partie de votre entreprise utilise SharePoint Online dans Office 365, il sera probablement doivent être réglage des performances ou test à l’intérieur de votre réseau. Les équipes concernés doivent être informés à l’avance.
  
Dans mon exemple simple, j’afficher proposition d’un administrateur SharePoint et ensuite répertorier le plan toutes les parties prenantes convenus. Pour plus de clarté, documenter vos contrats et les décisions.
  
Le plan commence après une analyse approfondie d’une batterie de serveurs et essaie d’identifier le rôle de la batterie de serveurs, les points faibles et autres informations importantes conduisant à restreindre les résultats de certaines options de mise à niveau. Ensuite, une proposition de mise à niveau est effectuée par l’administrateur SharePoint et les parties prenantes d’accord sur un plan d’action.
  
Ma liste de puces « plus important » :
  
- Disponibilité, les fonctionnalités intégrées dans SharePoint et les normes de conformité.
    
- La plupart des données sont sur trois collections de sites, avec un espace de travail de réunion utilisé par une équipe de développement particulièrement importante et l’utilisation intensive dans plusieurs fuseaux horaires dans le monde.
    
- Il existe 17 autres sites qui sont fréquemment utilisées.
    
- Deux bibliothèques de documents (espace de travail de réunion et des Documents sur la collection de sites racine) sont plus grandes (plus 8000 documents chaque). Nous disposons d’un grand nombre de documents archivés et liste contenant des pièces jointes de feuille de calcul.
    
- Il existe en quatorze listes de bibliothèques contenant des données sensibles qui doivent rester en conformité.
    
- Nous DEVONS ont la possibilité d’effectuer des suspensions et e-discovery partout où nous sommes.
    
- Certaines de ces données doivent rester sur site, en raison des règles InfoSec.
    
 **Mes options de mise à niveau et migration :**
  
|||
|:-----|:-----|
|**Oui** <br/> |**Non** <br/> |
|Attachement de bases de données mise à niveau avec la base de données  <br/> |Mise à niveau sur place  <br/> |
|Mise à niveau avec des batteries de serveurs côte à côte  <br/> |Mise à niveau hybride  <br/> |
|API de migration à SPO dans Office 365 (pour les données de site personnel)  <br/> |Environnement hybride SharePoint (ne pas encore nécessaire)  <br/> |
|Certains migrations manuelle des données vers SharePoint Online pour les données critiques  <br/> |Mise à niveau d’Assistant FastTrack vers Office 365  <br/> |
   
 **Mon projet proposé :**
  
Mise à niveau locale, avec les versions de SharePoint côte à côte, certaines virtualisé, afin que nous pouvons mettre à niveau les bases de données premier. Accédez à partir de SharePoint 2007 vers SharePoint 2010. Les développeurs et les administrateurs tester la batterie de serveurs qui en résulte. Utilisateurs test de la batterie de serveurs qui en résulte. Résoudre les problèmes d’arrêt de l’afficher pendant ce temps. Encore une fois, côte à côte, mise à niveau SharePoint 2010 bases de données vers SharePoint 2013. Pilote/test utilisateur test. Résoudre les problèmes d’arrêt de l’afficher pendant ce temps.
  
- Prendre en compte si une recherche fédérée déploiement hybride avec SPO répond à vos besoins.
    
- Si vous souhaitez mettre à niveau vers SharePoint Online à partir de là, prenez en compte [l’assistance FastTrack](https://fasttrack.microsoft.com) . 
    
- Déterminer si les collections de sites peuvent être transférées à un abonnement à Office 365. (Office 365 est conforme aux [normes de conformité](https://technet.microsoft.com/library/office-365-compliance.aspx)de nombreuses. Office 365 a [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) et peut faire [contient](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) par le Centre de conformité.) 
    
Sinon, passez à une mise à niveau côte à côte pour SharePoint Server 2016.
  
> [!NOTE]
> Entre les recommandations effectuées par les administrateurs de planification de la mise à niveau et le processus sont les conversations qui se produisent avec les autres parties prenantes sur lesquels repose la mise à niveau. Par exemple, parfois économiques forcer aux administrateurs de modifier leurs plans. Quelle que soit la décision finale est, vous devez documenter le plan convenus What ' s, à l’avenir. Il peut ressembler à ceci : 
  
 **Mon plan d’action :**
  
Sur site, nous utilisons un environnement virtuel pour créer par défaut de SharePoint Server 2010 et 2013. SharePoint Server 2016 sont construits sur le nouveau matériel conforme à la configuration système requise pour 2016. Nous attache une mise à niveau des bases de données à partir de SharePoint 2007 par le biais de toutes les versions entre SharePoint Server 2016 et de base de données. Recréation de personnalisations principaux et de tester dans SharePoint Server 2016 environnement à ce stade, si des fonctionnalités natives de ne pas déjà nos besoins. Si nous réussissent, nous disposons d’une batterie de serveurs locale sur un nouveau matériel avec des bases de données mis à niveau et les personnalisations moins. Nous allons attacher les bases de données de contenu mis à niveau pour les nouvelles collections de sites dans SharePoint Server 2013, test, pilote/utilisateur test, et puis procédez comme un serveur DNS plus vers le nouvel environnement SharePoint Server 2016 usage live.
  
- Nous allons étudier non fédéré de hybride entre SharePoint Server 2016 et SharePoint Online maintenant.
    
- Environ 35 % de nos sites peut être activée dans les nouveaux sites SPO avec les domaines de la redirection ou, en définitive, deviennent OneDrive pour le stockage d’entreprise. Vous recherchez d’autres possibilités pour convertir des sites ou acheminer des nouveaux sites à SPO.
    
- Certains de cette partie de la migration sera manuelle, par glisser-déplacer vers OneDrive pour les sites personnels métiers et d’autres API de migration.
    
Plus d’étapes, ou un nombre de liens vers des instructions de mise à niveau spécifiques doit suivre un plan. L’ordinateur de MOSS 2007 ne doit pas être désactivé et environnements virtuels doivent être maintenues dans un souci de comparaison ; Toutefois, la mise à niveau sera terminée lorsque les utilisateurs sont redirigés vers SharePoint Server 2016.
  
Souvent principaux facteurs lors du choix d’une méthode sont le coût total de la mise à niveau et le coût dans le temps (vous verrez plus d’informations dans l’article Guide de Migration de SharePoint). Toutefois, planification avance tireront parti vous considérablement dans la définition des attentes, en choisissant avec soin, et encadrer la réussite ressemblera.
  
## <a name="related-links"></a>Liens associés

[Ressources pour vous aider à mettre à niveau à partir d’Office 2007 de serveurs et de clients](upgrade-from-office-2007-servers-and-products.md)
  
[Recherche Policy de Lifecycle de Microsoft and du cycle de vie](https://support.microsoft.com/en-us/lifecycle)
  
[Recherche pour Microsoft Partners qui peut aider avec la mise à niveau ou la migration](https://partnercenter.microsoft.com/en-us/pcv/search)
  

