---
title: Feuille de route pour la fin de l’assistance pour Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
description: Le 11 avril 2017, Exchange Server 2007 est parvenu à la fin du support. Si vous n’avez pas encore commencé la migration d’Exchange 2007 vers Office 365 ou Exchange 2016, il est temps de commencer votre planification.
ms.openlocfilehash: 67e6a8f271fd8d553895ba086ed4b6ad11d9a877
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840351"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Exchange 2007

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Le **11 avril 2017**, Exchange Server 2007 est parvenu à la fin du support. Si vous n’avez pas encore commencé la migration d’Exchange 2007 vers Office 365 ou Exchange 2016, il est temps de commencer votre planification. 
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

Exchange Server, comme presque tous les produits Microsoft, a un cycle de vie de la prise en charge au cours duquel nous fournissons de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit. Étant donné qu’Exchange 2007 a atteint la fin de son support le 11 avril 2017, Microsoft ne fournit plus :
  
- Support technique pour les problèmes pouvant se produire ;
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur ;
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité ;
    
- Mises à jour de fuseau horaire.
    
Votre installation d’Exchange 2007 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées ci-dessus, nous vous recommandons vivement de procéder à une migration à partir d’Exchange 2007 dès que possible.
  
Pour plus d’informations sur les serveurs Office 2007 à la fin de la prise en charge, reportez-vous à la rubrique [plan Your Upgrade from Office 2007 Servers and Products](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Maintenant qu’Exchange 2007 a atteint sa fin de prise en charge, nous vous recommandons vivement d’explorer vos options et de préparer un plan de migration. Vous pouvez :
  
- Migrer vers Office 365 à l’aide de la migration de basculement, intermédiaire ou hybride ;
    
- Migrez vos serveurs Exchange 2007 vers une version plus récente d’Exchange sur vos serveurs locaux.
    
Les sections suivantes explorent chaque option plus en détail.
  
### <a name="migrate-to-office-365"></a>Migrer vers Office 365

La migration de votre courrier vers Office 365 est l’option la plus simple et la plus simple pour vous aider à supprimer votre déploiement Exchange 2007. Avec une migration vers Office 365, vous pouvez passer un seul tronçon de la technologie 10 ans à l’état des fonctionnalités art, comme suit :
  
- Les fonctionnalités de conformité telles que les stratégies de rétention, le blocage sur place et la mise en attente pour litige, la découverte électronique inaltérable et bien plus encore ;
    
- Groupes Office 365 ;
    
- Boîte de réception prioritaire ;
    
- Analyse Delve ;
    
- API REST pour l’accès par programme à la messagerie, aux calendriers, aux contacts, etc.
    
Office 365 fournit également de nouvelles fonctionnalités et des expériences, et vous pouvez généralement les utiliser immédiatement. En plus des nouvelles fonctionnalités, vous n’aurez pas à vous soucier des éléments suivants :
  
- L’achat et la maintenance de matériel ;
    
- Le paiement du chauffage et du refroidissement de vos serveurs ;
    
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire ;
    
- Maintenance du stockage et des logiciels pour prendre en charge les exigences de conformité ;
    
- Mise à niveau vers une nouvelle version d’Exchange : vous êtes toujours sur la dernière version d’Exchange dans Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Comment dois-je migrer vers Office 365 ?

En fonction de votre organisation, vous disposez de plusieurs options qui vous aideront à accéder à Office 365. Lors du choix d’une option de migration, vous devez prendre en compte quelques éléments comme le nombre de places ou de boîtes aux lettres que vous devez déplacer, la durée de la migration, et si vous avez besoin d’une intégration transparente entre votre installation locale et Office 365 pendant la migration. Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode que vous allez utiliser.
  
| |
|**Option de migration**|**Taille de l’Organisation**|**Duration**|
|:-----|:-----|:-----|
|Migration à basculement  <br/> |Moins de 150 sièges  <br/> |Une semaine ou moins  <br/> |
|Migration intermédiaire  <br/> |Plus de 150 sièges  <br/> |Quelques semaines  <br/> |
|Migration hybride complète  <br/> |Plusieurs centaines de milliers de sièges  <br/> |Quelques mois ou plus  <br/> |
   
Les sections suivantes vous donnent une vue d’ensemble de ces méthodes. Vérifiez que vous avez [choisi un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) pour connaître les détails de chaque méthode. 
  
#### <a name="cutover-migration"></a>Migration à basculement

Une migration à basculement est un emplacement où, à une date et une heure présélectionnées, vous allez migrer toutes vos boîtes aux lettres, groupes de distribution, contacts, etc. vers Office 365 ; Lorsque vous avez terminé, arrêtez vos serveurs Exchange locaux et commencez à utiliser Office 365 exclusivement.
  
La méthode de migration à basculement est idéale pour les petites organisations qui n’ont pas de très nombreuses boîtes aux lettres, qui souhaitent accéder rapidement à Office 365, et ne souhaitent pas faire face à certaines des complexités des autres méthodes. Toutefois, il est également quelque peu limité, car il doit être terminé dans une semaine ou moins, et parce qu’il nécessite que les utilisateurs reconfigurent leurs profils Outlook. Bien que la migration à basculement puisse gérer jusqu’à 2 000 boîtes aux lettres, nous vous recommandons vivement de migrer un maximum de 150 boîtes aux lettres avec cette méthode. Si vous essayez de migrer plus de 150 boîtes aux lettres, vous risquez de ne pas dépasser le temps de transférer toutes les boîtes aux lettres avant la date d’échéance, et votre équipe de support technique peut être submergée afin d’aider les utilisateurs à reconfigurer Outlook.
  
Si vous envisagez d’effectuer une migration à basculement, voici quelques éléments à prendre en compte :
  
- Office 365 doit se connecter à vos serveurs Exchange 2007 à l’aide d’Outlook Anywhere via le port TCP 443 ;
    
- Toutes les boîtes aux lettres locales seront déplacées vers Office 365 ;
    
- Vous aurez besoin d’un compte d’administrateur local qui a accès pour lire le contenu des boîtes aux lettres de vos utilisateurs ;
    
- Les domaines Exchange 2007 acceptés que vous souhaitez utiliser dans Office 365 doivent être ajoutés en tant que domaines vérifiés dans le service ;
    
- Entre le moment où vous démarrez la migration et le début de la phase de fin, Office 365 synchronise régulièrement Office 365 et les boîtes aux lettres locales. Cela vous permet d’effectuer la migration sans vous inquiéter de laisser le courrier électronique en arrière-plan dans vos boîtes aux lettres locales ;
    
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Office 365 qu’ils devront modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois ;
    
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
    
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier. La quantité de courriers électroniques qu’Outlook télécharge peut varier. Pour plus d’informations, consultez la rubrique [modifier le nombre de messages à conserver hors connexion](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Pour en savoir plus sur la migration à basculement, jetez un œil à :
  
- [Article relatif à ce que vous devez savoir sur une migration à basculement de la messagerie vers Office 365](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Effectuer une migration à basculement de la messagerie vers Office 365](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migration intermédiaire

Une migration intermédiaire est l’endroit où vous avez quelques centaines ou quelques milliers de boîtes aux lettres que vous souhaitez migrer vers Office 365, que vous devez prendre une semaine ou plus pour effectuer la migration et que vous n’avez besoin d’aucune des fonctionnalités avancées de migration hybride comme les informations de disponibilité partagées.
  
La migration intermédiaire est idéale pour les organisations qui ont besoin de plus de temps pour migrer leurs boîtes aux lettres vers Office 365, tout en planifiant la migration en quelques semaines. Vous pouvez migrer des boîtes aux lettres dans des « lots » qui vous permettent de contrôler le nombre de boîtes aux lettres qui sont migrées à un moment donné. Vous pouvez par lots utiliser des boîtes aux lettres d’utilisateurs dans le même service, par exemple, pour vous assurer qu’ils sont tous déplacés en même temps. Vous pouvez également laisser des boîtes aux lettres de direction jusqu’au dernier lot. Comme pour les migrations à basculement, vos utilisateurs devront recréer leurs profils Outlook.
  
Si vous envisagez d’effectuer une migration intermédiaire, voici quelques éléments à prendre en compte :
  
- Office 365 doit se connecter à vos serveurs Exchange 2007 à l’aide d’Outlook Anywhere via le port TCP 443 ;
    
- Vous aurez besoin d’un compte d’administrateur local qui a accès pour lire le contenu des boîtes aux lettres de vos utilisateurs ;
    
- Les domaines Exchange 2007 acceptés que vous souhaitez utiliser dans Office 365 doivent être ajoutés en tant que domaines vérifiés dans le service ;
    
- Vous devrez créer un fichier CSV avec le nom complet et l’adresse de messagerie de chaque boîte aux lettres que vous souhaitez migrer dans un lot. Vous devez également inclure un nouveau mot de passe pour chaque boîte aux lettres que vous migrez, puis envoyer son mot de passe à chaque utilisateur. L’utilisateur est invité à modifier le mot de passe la première fois qu’il se connecte à sa nouvelle boîte aux lettres Office 365 ;
    
- Entre le moment où vous démarrez le lot de migration et le début de la phase de fin, Office 365 synchronise régulièrement Office 365 et les boîtes aux lettres locales incluses dans le lot. Cela vous permet d’effectuer la migration sans vous inquiéter de laisser le courrier électronique en arrière-plan dans vos boîtes aux lettres locales ;
    
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Office 365 qu’ils devront modifier lorsqu’ils se connectent à leur boîte aux lettres pour la première fois ;
    
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
    
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier. La quantité de courriers électroniques qu’Outlook télécharge peut varier. Pour plus d’informations, consultez la rubrique [modifier le nombre de messages à conserver hors connexion](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Pour en savoir plus sur la migration intermédiaire, jetez un œil à :
  
- [Ce que vous devez savoir sur une migration de messagerie intermédiaire vers Office 365](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Effectuer une migration intermédiaire de la messagerie vers Office 365](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Hybride complet

Une migration hybride complète est un emplacement où votre organisation possède plusieurs centaines, jusqu’à dizaines de milliers, de boîtes aux lettres et vous souhaitez déplacer une partie ou la totalité d’entre elles vers Office 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides permettent d’effectuer les opérations suivantes :
  
- Afficher les informations de disponibilité des utilisateurs sur site pour les utilisateurs dans Office 365, et vice versa ;
    
- Afficher une liste d’adresses globale unifiée contenant des destinataires à la fois sur site et Office 365 ;
    
- Afficher toutes les cartes de destinataire Outlook pour tous les utilisateurs, qu’ils soient en local ou dans Office 365 ;
    
- Sécurisation des communications de messagerie entre les serveurs Exchange locaux et Office 365 à l’aide du protocole TLS et des certificats ;
    
- Traiter les messages envoyés entre des serveurs Exchange locaux et Office 365 comme internes, ce qui leur permet d’effectuer les opérations suivantes :
    
  - Être correctement évalué et traité par les agents de transport et de conformité ciblant les messages internes ;
    
  - Contourner les filtres anti-courrier indésirable.
    
Les migrations hybrides complètes sont idéales pour les organisations qui s’attendent à rester dans une configuration hybride pendant de nombreux mois ou plus. Vous bénéficierez des fonctionnalités répertoriées plus haut dans cette section, ainsi que de la synchronisation d’annuaires, des fonctionnalités de conformité intégrées et de la possibilité de déplacer des boîtes aux lettres vers et depuis Office 365 à l’aide de déplacements de boîtes aux lettres en ligne. Office 365 devient une extension de votre organisation locale.
  
Si vous envisagez d’effectuer une migration hybride complète, voici quelques éléments à prendre en compte :
  
- Les migrations hybrides complètes ne sont pas adaptées à tous les types d’organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas les avantages qui justifient les efforts et les coûts qu’il est nécessaire de définir. Si cela ressemble à votre organisation, nous vous recommandons vivement de prendre en compte le basculement ou les migrations intermédiaires ;
    
- Vous devez déployer au moins un serveur Exchange 2013 dans votre organisation Exchange 2007 pour qu’il se comporte comme un « serveur hybride ». Ce serveur va communiquer avec Office 365 pour le compte de vos serveurs Exchange 2007 ;
    
- Office 365 doit se connecter au « serveur hybride » à l’aide d’Outlook Anywhere via le port TCP 443 ;
    
- Vous devez configurer la synchronisation d’annuaires à l’aide d’Azure Active Directory Connect (AADConnect) entre vos serveurs Active Directory locaux et Office 365 ;
    
- Les utilisateurs peuvent se connecter à leur boîte aux lettres Office 365 en utilisant les mêmes nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local (nécessite Azure Active Directory Connect avec synchronisation de mot de passe et/ou services ADFS (Active Directory Federation Services));
    
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
    
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils (certains anciens téléphones Android peuvent avoir besoin d’un nouveau profil) et n’ont pas besoin de télécharger de nouveau leur courrier électronique.
    
Si une migration hybride complète vous paraît, jetez un œil aux ressources suivantes pour vous aider dans votre migration :
  
- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
    
- [Déploiements hybrides Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
    
- [Assistant de configuration hybride](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
    
- [FAQ de l’assistant Configuration hybride](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
    
- [Configuration requise pour un déploiement hybride](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrer vers une version plus récente d’Exchange Server

Bien que nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en migrant vers Office 365, nous comprenons également que certaines organisations doivent conserver leur courrier électronique en local. Cela peut être dû à des exigences réglementaires, afin de garantir que les données ne sont pas stockées dans un centre de données situé dans un autre pays, et ainsi de suite. Si vous choisissez de conserver votre courrier électronique en local, vous pouvez migrer votre environnement Exchange 2007 vers Exchange 2010, Exchange 2013 ou Exchange 2016.
  
Nous vous recommandons de migrer vers Exchange 2016 si vous ne pouvez pas effectuer une migration vers Office 365. Exchange 2016 inclut toutes les fonctionnalités et les améliorations incluses dans les versions précédentes d’Exchange, et correspond le mieux à l’expérience disponible avec Office 365 (même si certaines fonctionnalités sont disponibles uniquement dans Office 365). Voici quelques-unes des choses que vous avez été manquantes sur :
  
|**Version d’Exchange**|**Composants**|
|:-----|:-----|
|Exchange 2010  <br/> | Contrôle d’accès basé sur un rôle (autorisations sans ACL)  <br/>  Stratégies de boîte aux lettres Outlook Web Access  <br/>  Possibilité de partager des calendriers de disponibilité et de déléguer entre les organisations  <br/> |
|Exchange 2013  <br/> | *Fonctionnalités d’Exchange 2010 et...*  <br/>  Architecture simplifiée réduisant le nombre de rôles serveur à trois (boîte aux lettres, accès au client, transport Edge)  <br/>  Stratégies de protection contre la perte de données (DLP) pour éviter la fuite d’informations sensibles  <br/>  Amélioration significative de l’expérience Outlook Web App  <br/> |
|Exchange 2016  <br/> | *Fonctionnalités d’Exchange 2013 et...*  <br/>  Autres rôles serveur simplifiés pour le transport de boîtes aux lettres et de transport Edge uniquement  <br/>  Amélioration de DLP et intégration avec SharePoint  <br/>  Résilience de base de données améliorée  <br/>  Collaboration sur des documents en ligne  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Vers quelle version dois-je migrer ?

Nous vous recommandons de supposer initialement que vous allez migrer vers Exchange 2016. Ensuite, utilisez les informations suivantes pour confirmer votre hypothèse ou pour exclure Exchange 2016. Si vous ne pouvez pas migrer vers Exchange 2016 pour une raison ou une autre, effectuez le même processus avec Exchange 2013, et ainsi de suite.
  
|**Mûre**|**Informations supplémentaires**|
|:-----|:-----|
|Fin des dates de prise en charge  <br/> | À l’instar d’Exchange 2007, chaque version d’Exchange dispose de sa propre date de prise en charge :  <br/> **Exchange 2010** -janvier 2020  <br/> **Exchange 2013** -2023 avril  <br/> **Exchange 2016** -octobre 2025  <br/>  Avant la fin de la date de prise en charge, plus tôt vous devrez effectuer une autre migration. Le 2020 janvier est beaucoup plus proche que vous ne le pensez !  <br/> |
|Chemin de migration vers Exchange 2010 et 2013  <br/> |Voici les phases générales de la migration vers Exchange 2010 ou Exchange 2013 :  <br/> Installez Exchange 2010 ou 2013 dans votre organisation Exchange 2007 existante déplacer des services et une autre infrastructure vers Exchange 2010 ou 2013 déplacer des boîtes aux lettres et des dossiers publics vers Exchange 2010 ou 2013 désactiver les serveurs Exchange 2007 restants |
|Chemin de migration vers Exchange 2016  <br/> |Voici les phases générales de la migration vers Exchange 2016 :  <br/> Installation d’Exchange 2013 dans votre organisation Exchange 2007 votre organisation déplacer des services et une autre infrastructure vers Exchange 2013 déplacer des boîtes aux lettres et des dossiers publics vers Exchange 2013 désactiver les autres serveurs Exchange 2007 installer Exchange 2016 dans votre Organisation Exchange 2013. Déplacer des boîtes aux lettres, des dossiers publics, des services et une autre infrastructure vers Exchange 2016 (la commande n’a pas d’importance). Désactivez les serveurs Exchange 2013 [!NOTE] restants >> la migration d’Exchange 2013 vers Exchange 2016 est simple. Les deux versions ont presque les mêmes besoins en matière de matériel. Ceci, et le fait que ces versions sont si compatibles, signifie que vous pouvez reconstruire un serveur que vous avez acheté pour Exchange 2013 et y installer Exchange 2016. De plus, avec le déplacement de boîtes aux lettres en ligne, la plupart des utilisateurs ne remarqueront jamais que leur boîte aux lettres est déplacée du serveur, puis revenez après sa recréation avec Exchange 2016.           |
|Coexistence de la version  <br/> | Lors de la migration vers :  <br/> **Exchange 2016** Exchange 2016 ne peut pas être installé dans une organisation qui comprend un serveur Exchange 2007. Vous devez d’abord migrer vers Exchange 2010 ou 2013 (nous recommandons vivement Exchange 2013), de supprimer tous les serveurs Exchange 2007, puis de migrer vers Exchange 2016.  <br/> **Exchange 2010 ou exchange 2013** Vous pouvez installer Exchange 2010 ou Exchange 2013 dans une organisation Exchange 2007 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2010 ou 2013 et d’effectuer votre migration.  <br/> |
|Matériel serveur  <br/> | La configuration matérielle requise pour le serveur a changé par rapport à Exchange 2007. Vous devez vous assurer que le matériel que vous allez utiliser est compatible. Vous pouvez en savoir plus sur la configuration matérielle requise pour chaque version ici :  <br/> [Configuration requise pour Exchange 2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx) <br/> [Configuration requise pour Exchange 2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx) <br/> [Configuration requise pour Exchange 2010](https://technet.microsoft.com/library/aa996719%28v=exchg.141%29.aspx) <br/>  Les améliorations significatives des performances d’Exchange, ainsi que l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus récents, vous aurez probablement besoin de serveurs moins nombreux pour prendre en charge le même nombre de boîtes aux lettres.  <br/> |
|Version du système d'exploitation  <br/> | Les versions minimales de système d’exploitation prises en charge pour chaque version sont les suivantes :  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  Vous trouverez plus d’informations sur la prise en charge du système d’exploitation dans la [matrice de prise en charge d’Exchange](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Niveau fonctionnel de la forêt Active Directory  <br/> | Les niveaux fonctionnels de forêt Active Directory minimum pris en charge pour chaque version sont les suivants :  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Pour plus d’informations sur la prise en charge du niveau fonctionnel de la forêt, consultez la rubrique [Exchange Supporting Matrix](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versions du client Office  <br/> | Les versions de client Office minimales prises en charge pour chaque version sont les suivantes :  <br/> **Exchange 2016** Office 2010 (avec les dernières mises à jour)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **Exchange 2010** Office 2003  <br/>  Vous trouverez plus d’informations sur la prise en charge du client Office dans la [matrice de prise en charge d’Exchange](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Comment migrer ?

Si vous avez décidé de conserver votre courrier électronique en local, vous pouvez utiliser les ressources suivantes pour vous aider dans votre migration :
  
- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
    
- Modifications apportées au schéma Active Directory pour Exchange [2016](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Configuration système requise pour Exchange [2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/library/aa996719%28v=exchg.141%29.aspx)
    
- Conditions préalables pour Exchange [2016](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>Qu’en est-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Office 365, vous pouvez être autorisé à utiliser notre service FastTrack Microsoft. FastTrack fournit des meilleures pratiques, des outils et des ressources pour faciliter la migration vers Office 365. De plus, vous bénéficierez d’un véritable ingénieur de support qui vous guidera dans votre migration, de la planification et de la conception à la migration de votre dernière boîte aux lettres. Si vous souhaitez en savoir plus sur FastTrack, jetez un œil à [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Si vous rencontrez des problèmes lors de la migration vers Office 365 et que vous n’utilisez pas FastTrack ou que vous migrez vers une version plus récente d’Exchange Server, nous sommes là pour vous aider. Voici quelques ressources que vous pouvez utiliser :
  
- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [Support client](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>Voir aussi

[Ressources pour vous aider à mettre à niveau vos serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Groupe de retraite Office (Communauté Microsoft Tech)](https://go.microsoft.com/fwlink/?linkid=842065)
  

