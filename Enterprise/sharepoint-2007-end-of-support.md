---
title: Feuille de route pour la fin de l’assistance pour SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
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
description: Le 10 octobre 2017, la prise en charge de SharePoint Server 2007 s’est terminée. Lisez cet article pour en savoir plus sur les options de mise à niveau, la résolution des problèmes, les meilleures pratiques, la configuration système requise, les étapes de mise à niveau et comment obtenir de l’aide des partenaires Microsoft.
ms.openlocfilehash: 561619559fd43131518a0032d3b28dc556f2d8b0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996528"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour SharePoint Server 2007

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Le **10 octobre 2017**, Microsoft Office SharePoint Server 2007 est parvenu à la fin du support. Si vous n’avez pas commencé la migration de SharePoint Server 2007 vers Microsoft 365 ou une version plus récente de SharePoint Server en local, il est maintenant temps de commencer la planification. Cet article détaille les ressources pour aider les utilisateurs à migrer des données vers SharePoint Online ou à mettre à niveau votre serveur SharePoint Server local. 
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

SharePoint Server, comme presque tous les produits Microsoft, a un cycle de vie de la prise en charge au cours duquel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit. À la fin de l’assistance, Microsoft ne fournit plus :
  
- Support technique pour les problèmes pouvant se produire ;
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur ;
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité ; les 
    
- Mises à jour de fuseau horaire.
    
Bien que votre batterie de serveurs SharePoint Server 2007 soit toujours opérationnelle après le 10 octobre 2017, aucune mise à jour, correctifs ou correctifs supplémentaires ne sera fourni pour le produit (y compris les correctifs de sécurité/correctifs) et le support Microsoft aura entièrement déplacé ses efforts de support vers des versions plus récentes du produit. Étant donné que votre installation ne sera plus prise en charge ou corrigée, les approches de prise en charge doivent être mises à niveau ou migrer des données importantes.
  
> [!TIP]
> Si vous n’avez pas encore planifié de mise à niveau ou de migration, reportez-vous à la rubrique suivante : [options de migration de SharePoint 2007](sharepoint-2007-migration-options.md)pour obtenir des exemples de démarrage. Vous pouvez également rechercher des [partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peuvent vous aider à effectuer une mise à niveau ou une migration Microsoft 365 (ou les deux). 
  
Pour plus d’informations sur les serveurs Office 2007 qui arrivent à la fin de la prise en charge, consultez la rubrique [ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Votre première étape doit être le [site du cycle de vie du produit](https://go.microsoft.com/fwlink/?linkid=843148). Si vous disposez d’un produit Microsoft local qui est âgé, vous devez vérifier sa fin de la date de prise en charge, de sorte qu’une année ou une durée telle que vos migrations soient généralement nécessaires, vous pouvez planifier la mise à niveau ou les migrations. Lors du choix de l’étape suivante, il peut être utile de réfléchir sur ce qui serait suffisamment efficace, mieux et mieux en ce qui concerne les fonctionnalités du produit. Voici un exemple :
  
|**Bon**|**Parfaite**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride SharePoint  <br/> |SharePoint Server 2016  <br/> |
|||Environnement hybride SharePoint  <br/> |
   
Si vous choisissez des options sur le bas de l’unité, n’oubliez pas de planifier la mise à niveau dès que la migration à partir de SharePoint Server 2007 est terminée. (la fin de la prise en charge de SharePoint Server 2007 est le 10 octobre 2017. Veuillez noter que ces dates sont sujettes à modification et à la vérification du [site du cycle de vie des produits](https://support.microsoft.com/lifecycle).)
  
## <a name="where-can-i-go-next"></a>Que faire ensuite ?

SharePoint Server peut être installé en local sur vos propres serveurs ou vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Vous pouvez choisir l’une des actions suivantes :
  
- Migrer vers SharePoint Online
    
- Mettre à niveau SharePoint Server en local
    
- Effectuer les deux opérations ci-dessus
    
- Implémenter une solution [hybride SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 
    
N’oubliez pas les coûts cachés associés à la maintenance d’une batterie de serveurs, la maintenance ou la migration des personnalisations, ainsi que la mise à niveau du matériel dont dépend SharePoint Server. Avoir une batterie de serveurs SharePoint Server locale est gratifiante si elle est une nécessité ; dans le cas contraire, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités, sans personnalisation élevée, vous pouvez bénéficier d’une migration planifiée vers SharePoint Online.
  
> [!IMPORTANT]
> Il existe une autre option si le contenu dans SharePoint 2007 n’est pas fréquemment utilisé. Certains administrateurs SharePoint peuvent choisir de créer un abonnement Microsoft 365, de configurer un nouveau site SharePoint Online, puis de le découper de SharePoint 2007, de façon propre, en prenant uniquement les documents les plus importants sur les sites SharePoint Online récents. À partir de là, les données peuvent être vidées du site SharePoint 2007 en archives. Expliquez comment les utilisateurs utilisent les données de votre installation SharePoint 2007. Il peut y avoir des méthodes créatives pour résoudre ce problème. 
  
|**SharePoint Online (SPO)**|**SharePoint Server en local**|
|:-----|:-----|
|Coût élevé dans le temps (planification/exécution/vérification)  <br/> |Coût élevé dans le temps (planification/exécution/vérification)  <br/> |
|Coût réduit des fonds (sans achat de matériel)  <br/> |Coût plus élevé des fonds (matériel + développeurs/administrateurs)  <br/> |
|Coût unique lors de la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession/maintenance  <br/> |Coût total de propriété/maintenance élevé  <br/> |
   
Lorsque vous procédez à une migration vers Microsoft 365, le déplacement unique aura un coût plus lourd, tout en organisant les données et en décidant des éléments à prendre dans le Cloud et ce qu’il faut laisser derrière. Toutefois, les mises à niveau seront automatiques à partir de ce point, il n’est plus nécessaire de gérer les mises à jour matérielles et logicielles, et le temps de mise à niveau de votre batterie de serveurs sera sauvegardé par un contrat de niveau de service ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online dispose de toutes les fonctionnalités dont vous avez besoin en examinant la description de service associée. Consultez [les descriptions de service Microsoft 365 et Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Il n’existe aucun moyen direct de migrer de SharePoint 2007 vers SharePoint Online ; votre déplacement vers SharePoint Online s’effectuera manuellement. Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, votre déplacement peut également impliquer l’utilisation de l’API de migration SharePoint (pour migrer des informations vers OneDrive entreprise, par exemple).
  
|**Online Pro**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit le matériel SPO et l’administration de toutes les ressources matérielles.  <br/> |Les fonctionnalités disponibles peuvent varier entre SharePoint Server sur site et SPO.  <br/> |
|Vous êtes l’administrateur général de votre abonnement et pouvez affecter des administrateurs aux sites SPO.  <br/> |Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas (ou ne sont pas nécessaires) incluses dans le rôle d’administrateur SharePoint dans Microsoft 365.  <br/> |
|Microsoft applique les correctifs, les correctifs et les mises à jour sur le matériel et les logiciels sous-jacents.  <br/> |Étant donné qu’il n’y a aucun accès au système de fichiers sous-jacent dans le service, certaines personnalisations sont limitées.  <br/> |
|Microsoft publie des [contrats de niveau de service](https://go.microsoft.com/fwlink/?linkid=843153) et se déplace rapidement pour résoudre les incidents de niveau de service.  <br/> |La sauvegarde et la restauration, ainsi que d’autres options de récupération, sont automatisées par le service dans SharePoint Online : les sauvegardes sont remplacées si elles ne sont pas utilisées.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués en continu dans le service par Microsoft.  <br/> |Les modifications apportées à l’interface utilisateur et à d’autres fonctionnalités SharePoint sont installées par le service et doivent être activées ou désactivées.  <br/> |
|Microsoft 365 répond à de nombreuses normes industrielles : [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |L’assistance [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ni les ingénieurs du support technique Microsoft, ni les employés du centre de connaissances ne disposent d’un accès administrateur illimité à votre abonnement.  <br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement au sein du service, car bien que les fonctionnalités peuvent être déconseillées, il n’y a pas de finalisation de la prise en charge.  <br/> ||
   
Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer les données manuellement en fonction de vos besoins, vous pouvez consulter vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe pas de méthode historique permettant d’ignorer les versions des mises à niveau SharePoint, du moins à la version de SharePoint Server 2016. Cela signifie que les mises à niveau sont en série :
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Pour tirer le chemin entier de SharePoint 2007 vers SharePoint Server 2016, il s’agit d’un investissement considérable de temps et implique un coût en termes de matériel mis à niveau (Sachez que les serveurs SQL Server doivent également être mis à niveau), logiciel et administration. Les personnalisations doivent être mises à niveau ou abandonnées, en fonction de la criticité de la fonctionnalité.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 de fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Tenez compte de certaines des pièges liés aux déplacements manuels (par exemple, les déplacements de documents qui remplacent le dernier compte modifié avec l’alias du compte qui effectue le déplacement manuel) et le travail qui doit être réalisé à l’avance (comme la recréation de sites, de sous-sites, d’autorisations et de structures de listes). Encore une fois, il s’agit du temps nécessaire pour prendre en compte les données que vous pouvez déplacer dans le stockage ou qui n’ont plus besoin d’une action qui peut réduire l’impact de la migration.
  
Dans les deux cas, nettoyez votre environnement avant la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau et (si vous êtes sûr) avant de procéder à la désaffectation. 
  
N’oubliez pas de vérifier les **chemins de mise à niveau pris en charge et non pris en charge**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des **personnalisations**, nous vous recommandons de planifier votre mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, depuis le serveur.  <br/> |Tous les sauts et correctifs sont la responsabilité de votre société (vous pouvez engager le support Microsoft payant si votre produit n’est pas à la fin du support) :  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.  <br/> |La mise à niveau, les correctifs, les correctifs de sécurité et la maintenance de SharePoint Server sur site.  <br/> |
|Accès total pour une personnalisation accrue.  <br/> |Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur, effectués sur votre site, dépendent de votre contrôle.  <br/> |Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local  <br/> |
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible au cycle de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par savoir que vous répondez à la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Limites **et frontières logicielles pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et l’environnement local

Si la réponse à vos besoins en matière de migration se trouve entre l’auto-contrôle offert par les locaux et le coût de possession le plus bas offert par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online, via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint Server hybride bénéficiera de votre entreprise, vous devez vous familiariser avec les types d’hybrides existants et configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
[Offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |L’assistance [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> | | Ni les ingénieurs du support technique Microsoft, ni les employés du centre de connaissances ne disposent d’un accès administrateur illimité à votre abonnement.  <br/> | Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.  <br/> | | Les partenaires peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.  <br/> || | Les produits en ligne sont mis à jour automatiquement au sein du service, car bien que les fonctionnalités peuvent être déconseillées, il n’y a pas de finalisation de la prise en charge.  <br/> ||
   
Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer les données manuellement en fonction de vos besoins, vous pouvez consulter vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe pas de méthode historique permettant d’ignorer les versions des mises à niveau SharePoint, du moins à la version de SharePoint Server 2016. Cela signifie que les mises à niveau sont en série :
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Pour tirer le chemin entier de SharePoint 2007 vers SharePoint Server 2016, il s’agit d’un investissement considérable de temps et implique un coût en termes de matériel mis à niveau (Sachez que les serveurs SQL Server doivent également être mis à niveau), logiciel et administration. Les personnalisations doivent être mises à niveau ou abandonnées, en fonction de la criticité de la fonctionnalité.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 de fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Tenez compte de certaines des pièges liés aux déplacements manuels (par exemple, les déplacements de documents qui remplacent le dernier compte modifié avec l’alias du compte qui effectue le déplacement manuel) et le travail qui doit être réalisé à l’avance (comme la recréation de sites, de sous-sites, d’autorisations et de structures de listes). Encore une fois, il s’agit du temps nécessaire pour prendre en compte les données que vous pouvez déplacer dans le stockage ou qui n’ont plus besoin d’une action qui peut réduire l’impact de la migration.
  
Dans les deux cas, nettoyez votre environnement avant la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau et (si vous êtes sûr) avant de procéder à la désaffectation. 
  
N’oubliez pas de vérifier les **chemins de mise à niveau pris en charge et non pris en charge**: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des **personnalisations**, nous vous recommandons de planifier votre mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, depuis le serveur.  <br/> |Tous les sauts et correctifs sont la responsabilité de votre société (vous pouvez engager le support Microsoft payant si votre produit n’est pas à la fin du support) :  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.  <br/> |La mise à niveau, les correctifs, les correctifs de sécurité et la maintenance de SharePoint Server sur site.  <br/> |
|Accès total pour une personnalisation accrue.  <br/> |Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur, effectués sur votre site, dépendent de votre contrôle.  <br/> |Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local  <br/> |
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible au cycle de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par savoir que vous répondez à la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Limites **et frontières logicielles pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et l’environnement local

Si la réponse à vos besoins en matière de migration se trouve entre l’auto-contrôle offert par les locaux et le coût de possession le plus bas offert par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online, via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint Server hybride bénéficiera de votre entreprise, vous devez vous familiariser avec les types d’hybrides existants et configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
La création d’un environnement de développement/test Microsoft 365, que vous pouvez configurer avec des [guides de laboratoire de test](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides), constitue un bon moyen de voir ce fonctionnement. Une fois que vous avez acheté une version d’évaluation ou un abonnement à Microsoft 365, vous serez en mesure de créer les collections de sites, les sites Web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données (manuellement, à l’aide de l’API de migration ou-si vous souhaitez migrer mon contenu de site vers OneDrive entreprise, via l’Assistant hybride).
  
> [!NOTE]
> N’oubliez pas que votre batterie de serveurs SharePoint 2007 doit être mise à niveau, en local, vers SharePoint Server 2013 ou SharePoint Server 2016 de manière à utiliser l’option hybride 
  
## <a name="related-topics"></a>Voir aussi

[Résolution des problèmes et reprise de la mise à niveau (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Résoudre les problèmes de mise à niveau (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Rechercher des partenaires Microsoft pour faciliter la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  

