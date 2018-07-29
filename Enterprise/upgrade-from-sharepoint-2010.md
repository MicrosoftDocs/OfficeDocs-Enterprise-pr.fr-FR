---
title: Mise à niveau de SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 et SharePoint Server 2010 approchent la fin de la prise en charge. Utilisez cet article comme un guide de mise à niveau vers SharePoint Online ou une version plus récente de SharePoint Server locaux.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169866"
---
# <a name="upgrading-from-sharepoint-2010"></a>Mise à niveau de SharePoint 2010

Dans l’OPO 13, 2020, Microsoft Office SharePoint Server 2010 atteint la fin du support. Cet article décrit les ressources pour aider les utilisateurs migrer leurs données SharePoint Server 2010 vers SharePoint Online, ou mettre à niveau de votre serveur SharePoint local.
  
## <a name="what-is-end-of-support"></a>Quelle est la fin de la prise en charge ?

Lorsque votre logiciel SharePoint Server 2010 et SharePoint Foundation 2010 atteint la fin de son cycle de vie de prise en charge (la durée pendant laquelle Microsoft propose les nouvelles fonctionnalités, des correctifs, des correctifs de sécurité, etc.) il s’agit « fin du logiciel de la prise en charge », ou, Parfois, son « retraite ». À la fin de la prise en charge (ou EOS) d’un produit, nothing réellement arrête ou cesse de fonctionner ; Toutefois, à la fin de la prise en charge du logiciel, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire ;
    
- Correctifs pour les problèmes qui ont été identifiés et qui peut avoir un impact sur la stabilité et la facilité d’utilisation du serveur ;
    
- Correctifs de sécurité pour les vulnérabilités qui sont découvertes et qui peuvent rendre le serveur vulnérables aux failles de sécurité ;
    
- Mises à jour de fuseau horaire.
    
Cela signifie, il y aura aucune autre mises à jour, correctifs, ou feront des correctifs pour le produit (y compris les correctifs/correctifs de sécurité), et Support de Microsoft sera ont entièrement décalées vers ses efforts de prise en charge pour les versions les plus récentes. Approche de la fin de la prise en charge de SharePoint Server 2010, vous devez tirer parti des opportunités pour réduire les données que vous n’avez plus besoin avant la mise à niveau du produit et/ou la migration de vos données importantes.
  
> [!NOTE]
> Un cycle de vie logiciel dure généralement dix ans à compter de la date de publication initiale du produit. Vous pouvez rechercher des [Partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peut aider avec la mise à niveau vers la prochaine version de votre logiciel ou migration vers Office 365 (ou les deux). Assurez-vous que vous êtes au courant de fin des dates de prise en charge sur les technologies sous-jacentes critiques, notamment de la version de SQL server, que vous utilisez avec SharePoint. 
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Tout d’abord, vérifiez la date à laquelle s’achève prise en charge sur le [site du cycle de vie du produit](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). Ensuite, n’oubliez pas de planifier votre mise à niveau ou la migration de temps avec la base de connaissances de cette date. N’oubliez pas que votre produit *ne sont pas cesser de fonctionner* à la date répertoriés et vous pouvez continuer à son utilisation, mais que, dans la mesure où sera corrigée de votre installation n’est plus après cette date, vous souhaiterez une stratégie qui vous aideront à mieux transition vers la version suivante du produit. 
  
Cette matrice permet de tracer un cours en matière de migration des fonctionnalités de produits et les données utilisateur :
  
|**fin du support produit**|**Bonne**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride SharePoint  <br/> |SharePoint Server 2016 (localement)  <br/> |
|||Recherche de nuage SharePoint hybride  <br/> |
   
Si vous choisissez options sur le début de l’échelle (bonne options), vous devez commencer à planifier une mise à niveau une autre dès la fin de la migration à partir de SharePoint Server 2010. (fin du support pour SharePoint Server 2010 et SharePoint Foundation 2010 sont planifiés pour le 13 octobre 2020, mais *Sachez* vous devez toujours vérifier le [site du cycle de vie du produit](https://support.microsoft.com/en-us/lifecycle) pour les dates plus précises !) 
  
## <a name="where-should-i-go-next"></a>Où puis-je suivant ?

SharePoint Server 2013 et SharePoint Foundation 2013 peuvent être installé localement sur vos propres serveurs. Dans le cas contraire, vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft Office 365. Vous pouvez choisir de :
  
- Migrer vers SharePoint Online
    
- Mise à niveau de SharePoint Server ou SharePoint Foundation sur site
    
- Effectuer les deux opérations ci-dessus
    
- Implémenter une solution [hybride SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Prenez note des coûts cachés associés au maintien d’une batterie de serveurs à l’avenir, maintenance ou personnalisations de migration et mise à niveau le matériel dont dépend SharePoint Server. Si vous êtes au courant et avez pris en compte pour tous ces éléments, il ne sera plus facile de continuer la mise à niveau sur site. Dans le cas contraire, si vous exécutez votre batterie de serveurs sur les serveurs SharePoint hérité sans personnalisation importante, vous pouvez tirer parti d’une migration planifiée avec SharePoint Online. Il est également possible que locale magasins SharePoint Server peuvent opter pour mettre des données dans SharePoint Online pour réduire la quantité de gestion du matériel conservant tous leurs données sur site implique. Il peut être plus économique déplacer certaines de vos données dans SharePoint Online.
  
> [!NOTE]
> Les administrateurs SharePoint peuvent [créer un abonnement à Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurer un nouveau site SharePoint Online et réduction en dehors de SharePoint Server 2010, correctement, prendre uniquement les documents les plus importants pour les sites SharePoint Online vierge. À partir de là, toutes les données restantes peuvent épuiser à partir du site SharePoint Server 2010 dans les archives locales. 
  
|**SharePoint Online (SPO)**|**SharePoint Server sur site**|
|:-----|:-----|
|Coût élevé dans le temps (plan / l’exécution / vérification)  <br/> |Coût élevé dans le temps (plan / l’exécution / vérification)  <br/> |
|Réduction des coûts de fonds (aucun achat de matériel)  <br/> |Coût élevé des fonds (matériel)  <br/> |
|Coût unique dans la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession / maintenance  <br/> |Haute coût total de possession / maintenance  <br/> |
   
Lors de la migration vers Office 365, l’unique déplace de système un coût plus importante dans le temps consacré à planification préalable (alors que vous êtes organiser les données et à choisir les éléments à prendre vers le nuage et éléments à laisser). Toutefois, une fois la migration de vos données, mises à niveau seront automatiques à partir de là, voir que vous devrez n’est plus gérer les mises à jour des configurations matérielle et logicielle et la disponibilité de votre batterie de serveurs bénéficient d’un contrat de niveau de Service ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online offre toutes les fonctionnalités que vous avez besoin en consultant la description de service associé. Voici le lien vers toutes les Descriptions du Service Office 365 :
  
[Descriptions du Service Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Il n’est pas actuellement un moyen par lequel vous pouvez migrer directement à partir de SharePoint Server 2010 (ou SharePoint Foundation 2010) pour SharePoint Online, donc quantité de travail est manuel. Cela vous donne la possibilité pour l’archivage et nettoyage des données et les sites qui ne sont plus nécessaires, avant le déplacement. Vous pouvez archiver les autres données dans le stockage. N’oubliez pas également que SharePoint Server 2010 ni SharePoint Foundation 2010 cessera de fonctionner à la fin de la prise en charge, les administrateurs peuvent ont une période pendant laquelle SharePoint est en cours d’exécution si leurs clients oubliez déplacer certaines de leurs données.
  
Si vous mettez à niveau vers SharePoint Server 2013 ou SharePoint Server 2016 et décidez de mettre les données dans SharePoint Online, votre déplacement peut impliquer également à l’aide de l' [API de Migration de SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (pour migrer des informations dans OneDrive entreprise). 
  
|**Pro en ligne**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit matériel SPO et tous d’administration du matériel.  <br/> |Fonctionnalités disponibles peuvent être différentes entre SharePoint Server locaux et SPO.  <br/> |
|Que vous êtes administrateur global de votre abonnement, pouvez affecter des administrateurs aux sites SPO.  <br/> |Certaines actions disponibles à un administrateur de batterie de serveurs dans SharePoint Server locaux n’existent pas (ou ne sont pas nécessaires) au rôle administrateur SharePoint dans Office 365, mais l’Administration de SharePoint, Administration de la Collection de sites et la propriété de Site sont locaux votre organisation  <br/> |
|Microsoft applique des correctifs, correctifs et mises à jour sous-jacent matérielle et logicielle (y compris les serveurs SQL Server sur lequel s’exécute SharePoint Online).  <br/> |Puisqu’il n’a pas accès au système de fichiers sous-jacent dans le service, les personnalisations sont limitées.  <br/> |
|Microsoft publie les [Contrats de niveau de Service](https://go.microsoft.com/fwlink/?linkid=843153) et déplace rapidement résoudre les incidents de niveau de service.  <br/> |Sauvegarde et de restauration et d’autres options de récupération sont automatisées par le service dans SharePoint Online, les sauvegardes sont remplacées si n’est pas utilisés.  <br/> |
|Test de la sécurité et de réglage des performances du serveur sont exécutées dans le service de manière continue par Microsoft.  <br/> |Modifications apportées à l’interface utilisateur et autres SharePoint sont installées par le service de fonctionnalités et devez peuvent être activées ou désactivées.  <br/> |
|Office 365 répond aux normes nombreux : [Office 365 conformité](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |Assistance [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> De la mise à niveau sera manuelle ou par le biais de l’API de Migration SPO décrites dans [SharePoint Online et OneDrive de route de Migration](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ingénieurs du support technique Microsoft, ni dans le centre de données, les employés ont d’administration d’un accès illimité à votre abonnement.  <br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge de la version la plus récente de SharePoint, ou si une batterie de serveurs secondaire est requis pour la mise à niveau.  <br/> |
|Partenaires peuvent aider à la tâche unique de la migration des données vers SharePoint Online.  <br/> |Toutes les modifications à SharePoint Online sont dans le contrôle. Après la migration, concevoir des différences dans les menus, les bibliothèques et autres fonctionnalités temporairement peuvent affecter les possibilités d’utilisation.  <br/> |
|Produits en ligne sont automatiquement mises à jour sur le service, ce qui signifie que bien que les fonctionnalités peuvent supprimer des, il n’est pas true de fin de la prise en charge du cycle de vie.  <br/> |Fin de la prise en charge du cycle de vie pour SharePoint Server (ou SharePoint Foundation) est ainsi que les serveurs SQL sous-jacente.  <br/> |
   
Si vous avez décidé de créer un nouveau site Office 365 et serez migrer manuellement les données lui nécessaire, vous pouvez consulter vos droits options Office 365 ici :
  
[Options de plan Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mise à niveau de SharePoint Server sur site

Comme la dernière version du produit SharePoint local (SharePoint Server 2016), les mises à niveau de SharePoint Server doivent être *en série* , qui signifie qu’il n’existe aucun moyen de mise à niveau à partir de SharePoint Server 2010 vers SharePoint Server 2016, directement. 
  
|||
|:-----|:-----|
||Chemin d’accès de la mise à niveau en série *** : SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint Server 2016 |
   
Si vous choisissez de suivre le chemin d’accès complet à partir de SharePoint 2010 pour SharePoint Server 2016, cela peut prendre un temps et de planification. Mises à niveau impliquent un coût en termes d’administration, logiciel et matériel mis à niveau (à l’esprit que SQL Server doit également être mis à niveau). Outre, les personnalisations peuvent doivent être mis à niveau, ou même abandonnés. Veillez à collecter des notes sur toutes vos personnalisations critique avant de mettre à niveau votre batterie de serveurs SharePoint.
  
> [!NOTE]
> Il est possible de mettre à jour votre fin de la batterie de serveurs prise en charge de SharePoint 2010, installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distincts exécuteront côte à côte), puis planifier et exécuter une migration manuelle de contenu (pour le téléchargement et de nouveau le téléchargement du contenu, pour exemple). Il existe des pièges potentiels à ces déplacements manuels (tels que les documents provenant de 2010 ayant un dernier compte modifié en cours avec l’alias du compte effectuant le déplacement manuel), et certaines tâches doivent être effectuées à l’avance (recréation de sites, sous-sites, les autorisations et structures de liste). Il est temps à prendre en compte ce que vous pouvez passer dans le stockage, ou n’est plus de données doivent. Cela peut réduire l’impact de la migration. Les deux cas, nettoyez votre avant l’environnement de mise à niveau. Être sûr de votre batterie de serveurs existante est fonctionnel avant la mise à niveau, vous mettez hors service (sûr) avant ! 
  
N’oubliez pas passer en revue les **chemins de mise à niveau pris en charge et non prises en charge**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des **personnalisations**, il est essentiel de qu'avoir un plan de mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro locale**|**Con locale**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint (et son SQL), du matériel serveur haut.  <br/> |Tous les correctifs et les sauts sont la responsabilité de votre société (mais payante Support Microsoft peuvent prendre part si votre produit n’est pas à la fin de la prise en charge) :  <br/> |
|Ensemble complet des fonctionnalités de SharePoint Server sur site avec l’option de connexion de votre batterie de serveurs locale à un abonnement de SharePoint Online via hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité, mises à niveau du matériel et la maintenance de tous les de batterie de serveurs SharePoint Server et de SQL sont gérées en local.  <br/> |
|Accès total pour les options de personnalisation plus qu’avec SharePoint Online.  <br/> |[Les normes de conformité prises en charge par Office 365](https://go.microsoft.com/fwlink/?linkid=843165) doit être configuré manuellement sur site.  <br/> |
|Test de la sécurité et de réglage des performances de serveur, exécutées sur votre site (sous votre contrôle).  <br/> |Office 365 peut rendre une fonctionnalités disponibles avec SharePoint Online qui ne fonctionnent pas avec SharePoint Server sur site  <br/> |
|Partenaires peuvent aider à la migration des données à la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utilisent pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme illustré dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, sauvegarde et restauration et autres options de récupération dans SharePoint Server locaux.  <br/> |SharePoint Server sur site est sensible aux cycles de vie du produit.  <br/> |
   
### <a name="upgrade-resources"></a>Ressources de mise à niveau

Commencez par comparaison des configurations matérielle et logicielle requises. Si vous ne répondent aux exigences de base pour la mise à niveau sur la configuration matérielle actuelle, qui peut signifier vous devez mettre à niveau le matériel dans la batterie de serveurs ou les serveurs SQL tout d’abord, ou que vous pouvez décider de déplacer un pourcentage de vos sites vers le matériel « à » de SharePoint Online. Une fois que vous avez créé votre évaluation, suivez les chemins de mise à niveau pris en charge et les méthodes.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limitations et frontières logicielles pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **La vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Créer une solution hybride de SharePoint entre SharePoint Online et SharePoint Server locaux

Une autre option (qui peut être la meilleure des locaux et tirent en ligne pour une migration doit) est un hybride, vous pouvez vous connecter SharePoint Server 2013 ou batteries de serveurs 2016 à SharePoint Online pour créer un environnement hybride SharePoint : [en savoir plus sur les solutions hybrides SharePoint ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si vous décidez de qu'une batterie de serveurs SharePoint hybride est votre objectif de migration, n’oubliez pas de planifier les sites et les utilisateurs, vous devez placer en ligne, et qui doivent rester locale. Un examen et le classement de contenu de votre batterie SharePoint Server (déterminer quelles données seront élevée, moyenne ou faible impact à votre société) peuvent être utiles de prise de décision. Il s’agit peut-être que la seule chose que vous devez partager avec SharePoint Online est les comptes d’utilisateurs (a) pour le nom de connexion et (b) l’index de recherche SharePoint Server--peut-être pas effacer jusqu'à ce que vous examinez comment vos sites sont utilisés. Si votre société décide plus loin de tout votre contenu migrer vers SharePoint Online, vous pouvez déplacer tous les autres comptes et les données en ligne et mettre hors service de votre batterie de serveurs locale, et gestion de la batterie de serveurs SharePoint sera effectuée via Office 365 consoles à partir de ce point.
  
Veillez à vous familiariser avec les types existants de hybride et comment configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Office 365.
  
Il est un excellent moyen de voir le fonctionne d’une batterie de serveurs SharePoint hybride en créant un [environnement de développement/test Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Une fois que vous disposez d’une version d’évaluation ou d’abonnement à Office 365, vous serez pratique pour la création de collections de sites, sites Web, les bibliothèques de documents dans SharePoint Online à laquelle vous pouvez migrer les données (soit manuellement, par l’utilisation de l’API de Migration, ou - si vous souhaitez migrer mon Contenu de site à OneDrive entreprise - par le biais de l’Assistant hybride).
  
> [!NOTE]
> N’oubliez pas que votre batterie de serveurs SharePoint Server 2010 devez tout d’abord être mis à niveau sur site, SharePoint Server 2013 ou SharePoint Server 2016 pour utiliser l’option hybride. SharePoint Foundation 2010 et SharePoint Foundation 2013 Impossible de créer les connexions hybride avec SharePoint Online. 
  
## <a name="related-topics"></a>Voir aussi

[Ressources pour aider à la mise à niveau à partir d’Office 2007 ou 2010 serveurs et clients](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Meilleures pratiques pour la mise à niveau de SharePoint 2010 vers SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Recherche pour Microsoft Partners contribuer à la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Stratégie de maintenance de produit mise à jour pour SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Stratégie de maintenance de produit mise à jour pour SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

