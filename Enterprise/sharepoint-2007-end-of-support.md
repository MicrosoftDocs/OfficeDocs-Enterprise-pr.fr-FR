---
title: Feuille de route pour la fin de l’assistance pour SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: Sur 10 octobre 2017, prise en charge s’est terminée pour SharePoint Server 2007. Lisez cet article pour en savoir plus sur les options de mise à niveau, résoudre les problèmes, meilleures pratiques, configuration système requise, la mise à niveau et comment obtenir de l’aide de Microsoft Partners.
ms.openlocfilehash: b0d3eda690733b45ee82054e145642a5c76125d5
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604515"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour SharePoint Server 2007

Sur **le 10 octobre 2017**, Microsoft Office SharePoint Server 2007 atteint la fin du support. Si vous n’avez pas encore commencé à votre migration à partir de SharePoint Server 2007 vers Office 365 ou une version plus récente de SharePoint Server locaux, il est temps pour commencer la planification. Cet article décrit les ressources pour aider les utilisateurs migrer les données vers SharePoint Online, ou mettre à niveau de votre serveur SharePoint local. 
  
## <a name="what-does-end-of-support-mean"></a>Quel ne prend fin moyenne de la prise en charge ?

SharePoint Server, comme presque tous les produits Microsoft, dispose d’un cycle de vie de prise en charge au cours de laquelle Microsoft propose les nouvelles fonctionnalités, des correctifs, des correctifs de sécurité et ainsi de suite. Ce cycle de vie dure généralement dix ans à compter de la date de publication initiale du produit, et la fin de ce cycle de vie est appelée fin du produit de prise en charge. À la fin de la prise en charge, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire ;
    
- Correctifs pour les problèmes qui ont été identifiés et qui peut avoir un impact sur la stabilité et la facilité d’utilisation du serveur ;
    
- Correctifs de sécurité pour les vulnérabilités qui sont découvertes et qui peuvent rendre le serveur vulnérables aux failles de sécurité ; et 
    
- Mises à jour de fuseau horaire.
    
Si votre batterie de serveurs SharePoint Server 2007 sera toujours opérationnel après 10 octobre 2017, pas d’autres mises à jour, correctifs, ou feront des correctifs pour le produit (y compris les correctifs de sécurité et les correctifs) et Support de Microsoft ont sera entièrement décalées ses efforts de prise en charge pour versions plus récentes du produit. Car votre installation n’est plus pris en charge ou corrigés, comme des approches de la prise en charge de mise à niveau du produit, ou si vous migrer les données importantes.
  
> [!TIP]
> Si vous n’avez pas déjà planifié pour la migration ou mise à niveau, consultez : [options de migration de SharePoint 2007 à prendre en compte](sharepoint-2007-migration-options.md)pour obtenir des exemples d’où commencer. Vous pouvez également rechercher des [Partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peut aider avec la mise à niveau ou la migration vers Office 365 (ou les deux). 
  
Pour plus d’informations sur les serveurs Office 2007 a atteint la fin de la prise en charge, voir les [ressources pour vous aider à mettre à niveau à partir d’Office 2007 de serveurs et de clients](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Le premier taquet doit être le [site du cycle de vie du produit](https://go.microsoft.com/fwlink/?linkid=843148). Si vous disposez d’un produit Microsoft locale est chronologiques, vous devez vérifier sa date de fin du support donc qui, une année ou, out - ou tant que votre migration requièrent généralement - vous pouvez planifier la mise à niveau ou la migration. Lors du choix de l’étape suivante, il peut aider à prendre en compte en termes de ce qui serait suffire, mieux et meilleures lorsqu’il s’agit des fonctionnalités de produits. Voici un exemple :
  
|**Bonne**|**Meilleure**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Environnement hybride SharePoint  <br/> |
   
Si vous choisissez options sur le début de l’échelle (suffisant), n’oubliez pas que vous devrez commencer la planification de mise à niveau très peu après la migration à partir de SharePoint Server 2007 est terminée. (fin du support pour SharePoint Server 2007 est du 10 octobre 2017. Notez que les dates sont sujettes à modification et vérifiez le [site du cycle de vie du produit](https://support.microsoft.com/en-us/lifecycle).)
  
## <a name="where-can-i-go-next"></a>Où puis-je trouver suivant ?

SharePoint Server peut être installé localement sur vos propres serveurs, ou vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft Office 365. Vous pouvez choisir de :
  
- Migrer vers SharePoint Online
    
- Mise à niveau de SharePoint Server sur site
    
- Effectuer les deux opérations ci-dessus
    
- Implémenter une solution [hybride SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
Prenez note des coûts cachés associés au maintien d’une batterie de serveurs à l’avenir, maintenance ou personnalisations de migration et mise à niveau le matériel dont dépend SharePoint Server. Avoir une batterie de serveurs SharePoint Server locaux récompense si elle est nécessaire ; dans le cas contraire, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités, sans personnalisation importante, vous pouvez bénéficier d’une migration planifiée avec SharePoint Online.
  
> [!IMPORTANT]
> Il existe un autre si le contenu de SharePoint 2007 est rarement utilisé. Certains administrateurs de SharePoint peuvent choisir de [créer un abonnement à Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurer un nouveau site SharePoint Online et réduction en dehors de SharePoint 2007, correctement, prendre uniquement les documents les plus importants pour les sites SharePoint Online vierge. À partir de là, les données peuvent épuiser à partir du site SharePoint 2007 dans les archives. Permettre à penser à la façon dont les utilisateurs travaillent avec des données votre installation SharePoint 2007. Il peut y avoir des moyens pour résoudre ce problème. 
  
|**SharePoint Online (SPO)**|**SharePoint Server sur site**|
|:-----|:-----|
|Coût élevé dans le temps (plan / l’exécution / vérification)  <br/> |Coût élevé dans le temps (plan / l’exécution / vérification)  <br/> |
|Réduction des coûts de fonds (aucun achat de matériel)  <br/> |Coût élevé des fonds (matériel + développements / administrateurs)  <br/> |
|Coût unique dans la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession / maintenance  <br/> |Haute coût total de possession / maintenance  <br/> |
   
Lors de la migration vers Office 365, le déplacement unique aura un coût plus importante initial, alors que vous êtes organiser les données et à choisir les éléments à prendre vers le nuage et éléments à laisser. Toutefois, les mises à niveau seront automatiques à partir de là, vous devrez n’est plus gérer les mises à jour des configurations matérielle et logicielle et la disponibilité de votre batterie de serveurs bénéficient d’un contrat de niveau de Service ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online comprend toutes les fonctionnalités que vous avez besoin en consultant la description de service associé. Voici le lien vers toutes les Descriptions du Service Office 365 :
  
[Descriptions des services Office 365](https://go.microsoft.com/fwlink/?linkid=272060)
  
Il n’existe aucun moyen direct de migrer à partir de SharePoint 2007 vers SharePoint Online ; migrer vers SharePoint Online doit être effectuée manuellement. Si vous mettez à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, votre déplacement peut impliquer également à l’aide de l’API de Migration de SharePoint (pour migrer des informations dans OneDrive entreprise, par exemple).
  
|**Pro en ligne**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit matériel SPO et tous d’administration du matériel.  <br/> |Fonctionnalités disponibles peuvent être différentes entre SharePoint Server locaux et SPO.  <br/> |
|Que vous êtes administrateur global de votre abonnement, pouvez affecter des administrateurs aux sites SPO.  <br/> |Certaines actions disponibles à un administrateur de batterie de serveurs dans SharePoint Server locaux n’existent pas (ou ne sont pas nécessaires) inclus dans le rôle d’administrateur SharePoint dans Office 365.  <br/> |
|Microsoft applique des correctifs, résout et met à jour sous-jacent configuration matérielle et logicielle.  <br/> |Puisqu’il n’a pas accès au système de fichiers sous-jacent dans le service, les personnalisations sont limitées.  <br/> |
|Microsoft publie les [Contrats de niveau de Service](https://go.microsoft.com/fwlink/?linkid=843153) et déplace rapidement résoudre les incidents de niveau de service.  <br/> |Sauvegarde et de restauration et d’autres options de récupération sont automatisées par le service dans SharePoint Online, les sauvegardes sont remplacées si n’est pas utilisés.  <br/> |
|Test de la sécurité et de réglage des performances du serveur sont exécutées dans le service de manière continue par Microsoft.  <br/> |Modifications apportées à l’interface utilisateur et autres SharePoint sont installées par le service de fonctionnalités et devez peuvent être activées ou désactivées.  <br/> |
|Office 365 répond aux normes nombreux : [Office 365 conformité](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |Assistance [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> De la mise à niveau sera manuelle ou par le biais de l’API de Migration SPO décrites dans [SharePoint Online et OneDrive de route de Migration](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ingénieurs du support technique Microsoft, ni dans le centre de données, les employés ont d’administration d’un accès illimité à votre abonnement.  <br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge de la version la plus récente de SharePoint, ou si une batterie de serveurs secondaire est requis pour la mise à niveau.  <br/> |
|Partenaires peuvent aider à la tâche unique de la migration des données vers SharePoint Online.  <br/> ||
|Produits en ligne sont automatiquement mises à jour sur le service, ce qui signifie que bien que les fonctionnalités peuvent supprimer des, il n’est pas true de fin de prise en charge.  <br/> ||
   
Si vous avez décidé de créer un nouveau site Office 365 et serez migrer manuellement les données lui nécessaire, vous pouvez consulter vos droits options Office 365 ici :
  
[Options de plan Office 365](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mise à niveau de SharePoint Server sur site

Il n’est toujours aucun moyen d’ignorer les versions de mises à niveau de SharePoint, au moins pas à compter de la version de SharePoint Server 2016. Cela signifie que les mises à niveau accédez en série :
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
À prendre le chemin d’accès complet à partir de SharePoint 2007 vers SharePoint Server 2016 implique un investissement considérable de temps et implique un coût en termes de matériel mis à niveau (à l’esprit que SQL Server doit également être mis à niveau), logiciel et administration. Personnalisations doit être mis à niveau ou abandonnés, en fonction de l’importance de la fonctionnalité.
  
> [!NOTE]
> Il est possible de gérer votre batterie de serveurs SharePoint 2007-fin de vie, installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distincts exécuteront côte à côte), puis planifier et exécuter une migration manuelle de contenu (pour le téléchargement et de nouveau le téléchargement du contenu, pour exemple). Gardez à l’esprit les problèmes de déplacements manuels (tels que des documents en remplaçant le dernier compte modifié par l’alias du compte effectuant le déplacement manuel des déplacements) et les travaux qui doivent être effectuée à l’avance (par exemple, recréez les sites, sous-sites, autorisations et liste des structures). Là encore, il s’agit de l’heure à prendre en compte les données que vous pouvez déplacer vers le stockage, ou n’est plus nécessaire, une action qui permet de réduire l’impact de la migration.
  
Les deux cas, nettoyez votre avant l’environnement de mise à niveau. Être sûr de votre batterie de serveurs existante est fonctionnel avant la mise à niveau, vous mettez hors service (sûr) avant ! 
  
N’oubliez pas passer en revue les **chemins de mise à niveau pris en charge et non prises en charge**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des **personnalisations**, il est essentiel de qu'avoir un plan de mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro locale**|**Con locale**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, de configurer le matériel du serveur.  <br/> |Tous les correctifs et les sauts sont la responsabilité de votre société (puissent s’impliquer payante Support Microsoft si votre produit n’est pas à la fin de la prise en charge) :  <br/> |
|Ensemble complet des fonctionnalités de SharePoint Server sur site avec l’option de connexion de votre batterie de serveurs locale à un abonnement de SharePoint Online via hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité et la maintenance de tous les de SharePoint Server gérés sur site.  <br/> |
|Accès total pour une plus grande.  <br/> |[Les normes de conformité prises en charge par Office 365](https://go.microsoft.com/fwlink/?linkid=843165) doit être configuré manuellement sur site.  <br/> |
|Test de la sécurité et de réglage des performances de serveur, exécutées sur votre site (est sous votre contrôle).  <br/> |Office 365 peut rendre une fonctionnalités disponibles avec SharePoint Online qui ne fonctionnent pas avec SharePoint Server sur site  <br/> |
|Partenaires peuvent aider à la migration des données à la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utilisent pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme illustré dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, sauvegarde et restauration et autres options de récupération dans SharePoint Server locaux.  <br/> |SharePoint Server sur site est sensible aux cycles de vie du produit.  <br/> |
   
### <a name="upgrade-resources"></a>Ressources de mise à niveau

Début en sachant que vous répondent aux configurations matérielle et logicielle requises, puis suivez pris en charge les méthodes de mise à niveau.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limitations et frontières logicielles pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **La vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution hybride de SharePoint entre SharePoint Online et sur site

Si la réponse à vos besoins en matière de migration se trouve entre le self-control offerte par locale et le coût de possession offerte par SharePoint Online, vous pouvez vous connecter SharePoint Server 2013 ou 2016 batteries avec SharePoint Online via hybrides. [Découvrez les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint hybride intéressantes pour votre entreprise, familiarisez-vous avec les types existants de hybride et comment configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Office 365.
  
Il est un excellent moyen de voir comment cela fonctionne en créant un [environnement de développement/test Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Une fois que vous disposez d’une version d’évaluation ou d’abonnement à Office 365, vous serez pratique pour la création de collections de sites, sites Web, les bibliothèques de documents dans SharePoint Online à laquelle vous pouvez migrer les données (soit manuellement, par l’utilisation de l’API de Migration, ou - si vous souhaitez migrer mon Contenu de site à OneDrive entreprise - par le biais de l’Assistant hybride).
  
> [!NOTE]
> N’oubliez pas que votre batterie de serveurs SharePoint 2007 devront être mis à niveau sur site, SharePoint Server 2013 ou SharePoint Server 2016 pour utiliser l’option hybride 
  
## <a name="related-topics"></a>Voir aussi

[Résoudre les problèmes et reprendre la mise à niveau (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Résoudre les problèmes de mise à niveau (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Recherche pour Microsoft Partners contribuer à la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressources pour vous aider à mettre à niveau à partir d’Office 2007 de serveurs et de clients](upgrade-from-office-2007-servers-and-products.md)
  

