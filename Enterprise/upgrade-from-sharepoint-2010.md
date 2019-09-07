---
title: Mise à niveau à partir de SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 08/21/2019
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: Les extrémités de la prise en charge pour SharePoint 2010 et SharePoint Server 2010 se terminent le 13 octobre 2020. Utilisez cet article pour effectuer une mise à niveau vers SharePoint Online ou une version plus récente de SharePoint Server en local.
ms.openlocfilehash: c83d91b3ae8124312459033cb59524dec048fd03
ms.sourcegitcommit: af8175b2d7f84e5c835bbfba82c0b50fe555d9e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "36782431"
---
# <a name="upgrading-from-sharepoint-2010"></a>Mise à niveau à partir de SharePoint 2010

Microsoft SharePoint 2010 et SharePoint Server 2010 vont atteindre la fin de la prise en charge le **13 octobre 2020**. Cet article détaille les ressources pour vous aider à migrer vos données SharePoint Server 2010 existantes vers SharePoint Online dans Office 365 ou mettre à niveau votre environnement SharePoint Server 2010 sur site.
  
## <a name="what-is-end-of-support"></a>Qu’est-ce que la fin du support ?

Lorsque le logiciel SharePoint Server 2010 et SharePoint Foundation 2010 atteint la fin de son cycle de vie (la période pendant laquelle Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc.), il s’agit de la « fin du support » du logiciel, ou parfois, son « déclassement ». À la fin du support (ou EOS) d’un produit, rien ne s’arrête réellement ou cesse de fonctionner ; Toutefois, à la fin de la prise en charge du logiciel, Microsoft ne fournit plus :
  
- Support technique pour les problèmes pouvant se produire ;
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur ;
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité ;
    
- Mises à jour de fuseau horaire.
    
Cela signifie qu’il n’y aura pas de mises à jour, de correctifs ou de correctifs supplémentaires qui seront fournis pour le produit (y compris les correctifs de sécurité/correctifs), et le support Microsoft aura entièrement déplacé ses efforts de prise en charge vers des versions plus récentes. À la fin de la prise en charge des approches SharePoint Server 2010, vous devez tirer parti des opportunités de découper les données dont vous n’avez plus besoin avant de mettre à niveau le produit et/ou de migrer vos données importantes.
  
> [!NOTE]
> Le cycle de vie d’un logiciel dure généralement 10 ans après la date de publication initiale du produit. Vous pouvez rechercher des [fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peuvent vous aider à effectuer une mise à niveau vers la version suivante de votre logiciel ou avec la migration Office 365 (ou les deux). Assurez-vous que vous connaissez bien les dates de fin de prise en charge sur les technologies critiques sous-jacentes, notamment la version de SQL Server que vous utilisez avec SharePoint. 
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Tout d’abord, vérifiez la date à laquelle le support se termine sur le [site du cycle de vie du produit](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). Ensuite, veillez à planifier votre mise à niveau ou votre temps de migration avec la connaissance de cette date. N’oubliez pas que votre produit *ne fonctionnera pas* à la date indiquée et vous pouvez continuer son utilisation, mais, étant donné que votre installation ne sera plus corrigée après cette date, vous aurez besoin d’une stratégie qui vous aidera à effectuer une transition plus fluide vers la version suivante. du produit. 
  
Cette matrice permet de tracer un cours lorsqu’il s’agit de migrer les fonctionnalités du produit et les données utilisateur :
  
|**Fin du produit de support**|**Good**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 (en local)  <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 hybride avec SharePoint Online  <br/> |SharePoint Server 2016 (en local)  <br/> |
|||Recherche hybride sur le Cloud SharePoint  <br/> |
   
Si vous choisissez des options sur le bas de gamme (options utiles), vous devrez commencer à planifier une autre mise à niveau peu de temps après la migration de SharePoint Server 2010. 

Voici les trois chemins que vous pouvez suivre pour éviter la fin de la prise en charge de SharePoint Server 2010.

![Chemins de mise à niveau vers SharePoint Server 2010](./media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>La fin de la prise en charge de SharePoint Server 2010 et de SharePoint Foundation 2010 est prévue pour le 13 octobre 2020, mais n' *oubliez* pas que vous devez toujours vérifier le [site du cycle de vie des produits](https://support.microsoft.com/en-us/lifecycle) pour les dates les plus récentes.
>

  
## <a name="where-should-i-go-next"></a>Où dois-je aller ?

SharePoint Server 2013 et SharePoint Foundation 2013 peuvent être installés en local sur vos propres serveurs. Dans le cas contraire, vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft Office 365. Vous pouvez choisir l’une des actions suivantes :
  
- Migrer vers SharePoint Online
    
- Mettre à niveau SharePoint Server ou SharePoint Foundation en local
    
- Effectuer les deux opérations ci-dessus
    
- Implémenter une solution [hybride SharePoint](https://docs.microsoft.com/sharepoint/hybrid/hybrid) 
    
N’oubliez pas les coûts cachés associés à la maintenance d’une batterie de serveurs, la maintenance ou la migration des personnalisations, ainsi que la mise à niveau du matériel dont dépend SharePoint Server. Si vous êtes conscient de l’existence de tous ces éléments, il sera plus facile de poursuivre la mise à niveau locale. Dans le cas contraire, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation élevée, vous pouvez bénéficier d’une migration planifiée vers SharePoint Online. Il est également possible que pour votre environnement SharePoint Server sur site, vous pouvez choisir de placer des données dans SharePoint Online afin de réduire la quantité de gestion matérielle permettant de conserver toutes les données locales. Il peut s’avérer plus économique de déplacer certaines de vos données dans SharePoint Online.
  
> [!NOTE]
> Les administrateurs SharePoint peuvent [créer un abonnement Office 365](https://go.microsoft.com/fwlink/?linkid=843152), configurer un nouveau site SharePoint Online, puis se découper de sharepoint Server 2010 de façon propre, en prenant uniquement les documents les plus importants sur les sites SharePoint Online récents. À partir de là, toutes les données restantes peuvent être vidées du site SharePoint Server 2010 dans des archives locales. 
  
|**SharePoint Online**|**SharePoint Server en local**|
|:-----|:-----|
|Coût élevé dans le temps (planification/exécution/vérification)  <br/> |Coût élevé dans le temps (planification/exécution/vérification)  <br/> |
|Coût réduit des fonds (sans achat de matériel)  <br/> |Coût plus élevé des fonds (achats de matériel)  <br/> |
|Coût unique lors de la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession/maintenance  <br/> |Coût total de propriété/maintenance élevé  <br/> |
   
Lors de la migration vers Office 365, le déplacement unique aura un coût plus épais en temps passé à la planification, à l’avant (pendant que vous organisez les données et que vous décidez de ce que vous devez faire sur le Cloud et ce qu’il faut laisser derrière). Toutefois, une fois que vos données sont migrées, les mises à niveau sont automatiques à partir de ce point, étant donné que vous n’avez plus besoin de gérer les mises à jour matérielles et logicielles, et que le temps de mise à niveau de votre batterie de serveurs sera sauvegardé par un accord de niveau de service ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online offre toutes les fonctionnalités dont vous avez besoin en consultant sa [Description de service](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).
  
Il n’existe actuellement aucun moyen de migrer directement de SharePoint Server 2010 (ou SharePoint Foundation 2010) vers SharePoint Online, de sorte que la majeure partie du travail est manuelle. Cela vous permet d’archiver et de nettoyer les données et les sites qui ne sont plus nécessaires avant le déplacement. Vous pouvez archiver d’autres données dans le stockage. N’oubliez pas que ni SharePoint Server 2010 ni SharePoint Foundation 2010 ne cesseront de fonctionner à la fin du support, afin que les administrateurs puissent disposer d’une période pendant laquelle SharePoint est toujours en cours d’exécution si leurs clients oublient de déplacer certaines de leurs données.
  
Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, et que vous décidez de mettre des données dans SharePoint Online, votre déplacement peut également impliquer l’utilisation de l' [API de migration SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (pour migrer des informations vers OneDrive entreprise). 
  
|**Avantages de SharePoint Online**|**Inconvénient de SharePoint Online**|
|:-----|:-----|
|Microsoft fournit le matériel SPO et l’administration de toutes les ressources matérielles.  <br/> |Les fonctionnalités disponibles peuvent varier entre SharePoint Server sur site et SPO.  <br/> |
|Vous êtes l’administrateur général de votre abonnement et pouvez affecter des administrateurs aux sites SPO.  <br/> |Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas (ou ne sont pas nécessaires) dans le rôle d’administrateur SharePoint dans Office 365, mais l’administration de SharePoint, l’administration de la collection de sites et la propriété du site sont locales pour votre organisation.  <br/> |
|Microsoft applique les correctifs, les correctifs et les mises à jour du matériel et des logiciels sous-jacents (y compris les serveurs SQL sur lesquels SharePoint Online s’exécute).  <br/> |Étant donné qu’il n’y a aucun accès au système de fichiers sous-jacent dans le service, certaines personnalisations sont limitées.  <br/> |
|Microsoft publie des [contrats de niveau de service](https://go.microsoft.com/fwlink/?linkid=843153) et se déplace rapidement pour résoudre les incidents de niveau de service.  <br/> |La sauvegarde et la restauration, ainsi que d’autres options de récupération, sont automatisées par le service dans SharePoint Online : les sauvegardes sont remplacées si elles ne sont pas utilisées.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués en continu dans le service par Microsoft.  <br/> |Les modifications apportées à l’interface utilisateur et à d’autres fonctionnalités SharePoint sont installées par le service et doivent être activées ou désactivées.  <br/> |
|Office 365 répond à de nombreuses normes industrielles : [office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |L’assistance [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Ni les ingénieurs du support technique Microsoft, ni les employés du centre de connaissances ne disposent d’un accès administrateur illimité à votre abonnement.  <br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.  <br/> |
|Les fournisseurs de solutions peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.  <br/> |Toutes les modifications apportées à SharePoint Online ne figurent pas dans votre contrôle. Après la migration, les différences de conception dans les menus, les bibliothèques et les autres fonctionnalités peuvent affecter temporairement la convivialité.  <br/> |
|Les produits en ligne sont mis à jour automatiquement au sein du service, car bien que les fonctionnalités peuvent être déconseillées, il n’y a pas de fin de cycle de vie de support.  <br/> |Il y a une fin de cycle de vie de la prise en charge pour SharePoint Server (ou SharePoint Foundation), ainsi que les serveurs SQL sous-jacents.  <br/> |
   
Si vous avez décidé de créer un nouveau site Office 365 et que vous y migrerez manuellement les données nécessaires, vous pouvez consulter vos options de [plan Office 365](https://go.microsoft.com/fwlink/?linkid=843151).
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

À partir de la dernière version du produit SharePoint sur site (SharePoint Server 2016), les mises à niveau SharePoint Server doivent être *séquentielles*, ce qui signifie qu’il n’existe aucun moyen de procéder directement à la mise à niveau de sharepoint Server 2010 vers sharepoint server 2016. 
  
|||
|:-----|:-----|
||Chemin de mise à niveau série * * * * : **\>** sharepoint Server 2010 **\>** SharePoint server 2013 SharePoint Server 2016 |
   
Si vous choisissez de suivre le chemin d’accès complet de SharePoint 2010 vers SharePoint Server 2016, le temps et la planification seront pris en compte. Les mises à niveau impliquent un coût en termes de matériel mis à niveau (Sachez que les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. De plus, il se peut que les personnalisations doivent être mises à niveau, voire abandonnées. Veillez à recueillir des notes sur toutes vos personnalisations importantes avant de mettre à niveau votre batterie de serveurs SharePoint Server.
  
> [!NOTE]
> Il est possible de maintenir votre fin de prise en charge de la batterie de serveurs SharePoint 2010, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Ces déplacements manuels ont des pièges potentiels (par exemple, des documents provenant de 2010 ayant un compte modifié en dernier avec l’alias du compte qui effectue le déplacement manuel), et d’autres tâches doivent être exécutées à l’avance (recréation de sites, de sous-sites, d’autorisations et structures de liste). Il est opportun de prendre en compte les données que vous pouvez déplacer dans le stockage ou dont vous n’avez plus besoin. Cela peut réduire l’impact de la migration. Dans les deux cas, nettoyez votre environnement avant la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau et (si vous êtes sûr) avant de procéder à la désaffectation. 
  
N’oubliez pas de vérifier les **chemins de mise à niveau pris en charge et non pris en charge**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des **personnalisations**, nous vous recommandons de planifier votre mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Avantages sur site**|**Inconvénient sur site**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint (et de son SQL), depuis le serveur.  <br/> |Tous les correctifs et les réparations sont responsables de votre entreprise (mais vous pouvez contacter le support Microsoft payant si votre produit n’est pas à la fin du support) :  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.  <br/> |La mise à niveau, les correctifs, les correctifs de sécurité, les mises à niveau matérielles et toutes les opérations de maintenance de SharePoint Server et de la batterie de serveurs SQL sont gérés en local.  <br/> |
|Accès total pour des options de personnalisation plus importantes que SharePoint Online.  <br/> |Les [normes de conformité prises en charge par Office 365](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement sur site.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur, effectués sur votre site (sous votre contrôle).  <br/> |Office 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local.  <br/> |
|Les fournisseurs de solutions peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible au cycle de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par comparer les configurations matérielle et logicielle requises. Si vous ne remplissez pas les conditions requises de base pour la mise à niveau sur le matériel actuel, cela peut signifier que vous devez mettre à niveau le matériel de la batterie ou des serveurs SQL en premier, ou que vous pouvez décider de déplacer un certain pourcentage de vos sites vers le matériel « persistant » de SharePoint Online. Une fois que vous avez effectué votre évaluation, suivez les méthodes et les chemins de mise à niveau pris en charge.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Limites **et frontières logicielles pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et SharePoint Server en local

Une autre option (qui peut être le meilleur des mondes sur site et en ligne pour certains besoins en matière de migration) est un environnement hybride, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online pour créer un environnement hybride SharePoint : [en savoir plus sur les solutions hybrides SharePoint ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si vous décidez qu’une batterie de serveurs SharePoint Server hybride est votre objectif de migration, veillez à planifier les sites et les utilisateurs que vous devez passer à la mise en ligne, et ceux qui doivent rester en local. La révision et le classement du contenu de votre batterie SharePoint Server (déterminer les données qui ont un impact élevé, moyen ou faible sur votre entreprise) peuvent être utiles pour prendre cette décision. Il peut s’agir de la seule chose que vous devez partager avec SharePoint Online (a) pour les comptes d’utilisateur pour la connexion et (b) l’index de recherche SharePoint Server, ceci peut ne pas être clair tant que vous n’avez pas vu comment vos sites sont utilisés. Si, par la suite, votre société décide de migrer l’ensemble de votre contenu vers SharePoint Online, vous pouvez déplacer tous les comptes et données restants en ligne et mettre hors service votre batterie de serveurs locale, et la gestion/l’administration de la batterie de serveurs SharePoint sera effectuée via Office 365 consoles à partir de ce point.
  
Veillez à vous familiariser avec les types existants de l’environnement hybride et à configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Office 365.
  
Pour voir comment fonctionne une batterie de serveurs SharePoint hybride, vous pouvez créer un [environnement de développement/test Office 365](https://go.microsoft.com/fwlink/?linkid=843152). Une fois que vous avez une version d’évaluation ou que vous avez acheté l’abonnement Office 365, vous serez sur votre façon de créer les collections de sites, les sites Web et les bibliothèques de documents dans SharePoint Online vers lequel vous pouvez migrer des données (manuellement, à l’aide de l’API de migration ou-si vous voulez migrer mon Contenu du site dans OneDrive entreprise-via l’Assistant hybride).
  
> [!NOTE]
> N’oubliez pas que votre batterie de serveurs SharePoint Server 2010 doit d’abord être mise à niveau sur site, soit vers SharePoint Server 2013, soit vers SharePoint Server 2016 pour utiliser l’option hybride. SharePoint Foundation 2010 et SharePoint Foundation 2013 ne peuvent pas créer de connexions hybrides avec SharePoint Online. 

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour obtenir un résumé visuel des options de mise à niveau, de migration et de déplacement sur le Cloud pour les clients et les serveurs Office 2010 et Windows 7, consultez la [fin de l’affiche de la prise en charge](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf).

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

Cette affiche de page unique constitue un moyen rapide de comprendre les différents chemins que vous pouvez suivre pour empêcher les produits client et serveur Office 2010 et Windows 7 d’atteindre la fin du support, avec les chemins d’accès et la prise en charge des options préférés dans Microsoft 365 entreprise en surbrillance.

Vous pouvez également [Télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format Letter, Legal ou tabloïd (11 x 17).
        
## <a name="related-topics"></a>Sujets associés

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007 ou 2010](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Meilleures pratiques pour la mise à niveau de SharePoint 2010 vers SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Rechercher des fournisseurs de solutions Microsoft pour vous aider à la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Stratégie de maintenance de produit mise à jour pour SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Stratégie de maintenance de produit mise à jour pour SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

