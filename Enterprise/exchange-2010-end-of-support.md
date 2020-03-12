---
title: Feuille de route pour la fin de la prise en charge d'Exchange 2010
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 09/16/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 est à la fin de la prise en charge. Utilisez cette feuille de route de planification comme guide pour préparer la mise à niveau vers Exchange Online ou une version plus récente d’Exchange Server en local.
ms.openlocfilehash: d5118d0abf02464b47bfb4a368d42b0921c19ec5
ms.sourcegitcommit: 1c646afb10db9d3d1e6a346089b7845268b0c9d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "42605569"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge d'Exchange 2010

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Le **13 octobre 2020**, Exchange Server 2010 atteindra la fin de la prise en charge. Si vous n’avez pas encore commencé la migration d’Exchange 2010 vers Office 365 ou Exchange 2016, il est temps de commencer votre planification.

## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

Exchange Server, comme presque tous les produits Microsoft, a un cycle de vie de la prise en charge au cours duquel nous fournissons de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit.
Lorsque Exchange 2010 atteint la fin du support le 13 octobre 2020, Microsoft ne fournit plus les éléments suivants :

- Support technique pour les problèmes pouvant se produire ;
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur ;
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité ;
- Mises à jour de fuseau horaire.

Votre installation d’Exchange 2010 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées ci-dessus, nous vous recommandons vivement de procéder à une migration à partir d’Exchange 2010 dès que possible.

Pour plus d’informations sur les serveurs Office 2010 à la fin de la prise en charge, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Quelles sont les options ?

Avec Exchange 2010 de la fin de la prise en charge, il s’agit d’un excellent moment pour explorer vos options et préparer un plan de migration. Vous pouvez :

- Migrer entièrement vers Office 365. Migrez les boîtes aux lettres à l’aide du basculement, d’un environnement hybride minimal ou d’une migration hybride complète, puis supprimez les serveurs Exchange locaux et Active Directory.
- Migrez vos serveurs Exchange 2010 vers Exchange 2016 sur vos serveurs locaux.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Office 365, mais qu’elle envisage de maintenir DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Exchange local. Si le dernier serveur Exchange est supprimé, vous ne pourrez pas modifier les destinataires Exchange dans Exchange Online. En effet, la source d’autorité reste dans votre annuaire Active Directory local et des modifications doivent y être apportées. Dans ce scénario, vous disposez des options suivantes :

- (**Recommandé**) Si vous pouvez migrer vos boîtes aux lettres vers Office 365 et mettre à niveau vos serveurs le 13 octobre 2020, utilisez Exchange 2010 pour vous connecter à Office 365 et migrer les boîtes aux lettres. Ensuite, migrez Exchange 2010 vers Exchange 2016 et désactivez tous les autres serveurs Exchange 2010.
- Si vous ne pouvez pas effectuer la mise à niveau de la migration de boîtes aux lettres et du serveur local avant le 13 octobre 2020, mettez d’abord à niveau vos serveurs Exchange 2010 sur site vers Exchange 2016, puis utilisez Exchange 2016 pour vous connecter à Office 365 et migrer les boîtes aux lettres.

> [!NOTE]
> Bien qu’un peu plus complexe, vous pouvez également migrer des boîtes aux lettres vers Office 365 lors de la migration de vos serveurs Exchange 2010 locaux vers Exchange 2016.

Voici les trois chemins que vous pouvez suivre pour éviter la fin de la prise en charge d’Exchange Server 2010.

![Chemins de mise à niveau vers Exchange Server 2010](./media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Les sections suivantes explorent chaque option plus en détail.

## <a name="migrate-to-office-365"></a>Migrer vers Office 365

La migration de votre courrier vers Office 365 est l’option la plus simple et la plus simple pour vous aider à supprimer votre déploiement Exchange 2010. Avec une migration vers Office 365, vous pouvez effectuer un seul tronçon de l’ancienne technologie vers les fonctionnalités de pointe, comme suit :

- Les fonctionnalités de conformité telles que les stratégies de rétention, le blocage sur place et la mise en attente pour litige, la découverte électronique inaltérable et bien plus encore ;
- Microsoft teams ;
- Power BI ;
- Boîte de réception prioritaire ;
- Analyse Delve ;

Office 365 fournit également de nouvelles fonctionnalités et des expériences, et vous pouvez généralement les utiliser immédiatement. En plus des nouvelles fonctionnalités, vous n’aurez pas à vous soucier des éléments suivants :

- L’achat et la maintenance de matériel ;
- Le paiement du chauffage et du refroidissement de vos serveurs ;
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire ;
- Maintenance du stockage et des logiciels pour prendre en charge les exigences de conformité ;
- Mise à niveau vers une nouvelle version d’Exchange : vous êtes toujours sur la dernière version d’Exchange dans Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Comment dois-je migrer vers Office 365 ?

En fonction de votre organisation, vous disposez de plusieurs options qui vous aideront à accéder à Office 365. Lors du choix d’une option de migration, vous devez prendre en compte quelques éléments comme le nombre de places ou de boîtes aux lettres que vous devez déplacer, la durée de la migration, et si vous avez besoin d’une intégration transparente entre votre installation locale et Office 365 pendant la migration. Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode que vous allez utiliser.

| **Option de migration**     | **Taille de l’Organisation** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Migration à basculement        | Moins de 150 sièges  | Une semaine ou moins      |
| Migration hybride minimale | Moins de 150 sièges  | Quelques semaines ou moins |
| Migration hybride complète    | Plus de 150 sièges   | Quelques semaines ou plus |

Les sections suivantes vous donnent une vue d’ensemble de ces méthodes. Vérifiez que vous avez [choisi un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) pour connaître les détails de chaque méthode.

### <a name="cutover-migration"></a>Migration à basculement

Une migration à basculement est un emplacement où, à une date et une heure présélectionnées, vous allez migrer toutes vos boîtes aux lettres, groupes de distribution, contacts, etc. vers Office 365 ; Lorsque vous avez terminé, arrêtez vos serveurs Exchange locaux et commencez à utiliser Office 365 exclusivement.

La méthode de migration à basculement est idéale pour les petites organisations qui n’ont pas de très nombreuses boîtes aux lettres, qui souhaitent accéder rapidement à Office 365, et ne souhaitent pas faire face à certaines des complexités des autres méthodes. Toutefois, il est également quelque peu limité, car il doit être terminé dans une semaine ou moins, et parce qu’il nécessite que les utilisateurs reconfigurent leurs profils Outlook. Bien que la migration à basculement puisse gérer jusqu’à 2 000 boîtes aux lettres, nous vous recommandons vivement de migrer un maximum de 150 boîtes aux lettres avec cette méthode. Si vous essayez de migrer plus de 150 boîtes aux lettres, vous risquez de ne pas dépasser le temps de transférer toutes les boîtes aux lettres avant la date d’échéance, et votre équipe de support technique peut être submergée afin d’aider les utilisateurs à reconfigurer Outlook.

Si vous envisagez d’effectuer une migration à basculement, voici quelques éléments à prendre en compte :

- Office 365 doit se connecter à vos serveurs Exchange 2010 à l’aide d’Outlook Anywhere via le port TCP 443 ;
- Toutes les boîtes aux lettres locales seront déplacées vers Office 365 ;
- Vous aurez besoin d’un compte d’administrateur local qui a accès pour lire le contenu des boîtes aux lettres de vos utilisateurs ;
- Les domaines Exchange 2010 acceptés que vous souhaitez utiliser dans Office 365 doivent être ajoutés en tant que domaines vérifiés dans le service ;
- Entre le moment où vous démarrez la migration et le début de la phase de fin, Office 365 synchronise régulièrement Office 365 et les boîtes aux lettres locales. Cela vous permet d’effectuer la migration sans vous inquiéter de laisser le courrier électronique en arrière-plan dans vos boîtes aux lettres locales ;
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Office 365 qu’ils devront modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois ;
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier. La quantité de courriers électroniques qu’Outlook télécharge peut varier. Pour plus d’informations, consultez la rubrique [modifier le nombre de messages à conserver hors connexion](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Pour en savoir plus sur la migration à basculement, jetez un œil à :

- [Ce que vous devez savoir sur une migration de courrier à basculement vers Office 365](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Effectuer une migration à basculement de la messagerie vers Office 365](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimale

Une migration minimale hybride ou explicite est un emplacement où vous avez quelques centaines de boîtes aux lettres que vous souhaitez migrer vers Office 365, pouvez effectuer la migration en quelques semaines et n’avez pas besoin des fonctionnalités de migration hybride avancées comme les informations de disponibilité partagées.

Une migration hybride minimale est idéale pour les organisations qui ont besoin de plus de temps pour migrer leurs boîtes aux lettres vers Office 365, tout en préservant la migration en quelques semaines. Vous bénéficiez de la migration hybride complète plus avancée sans beaucoup de complexités. Vous pouvez contrôler le nombre de boîtes aux lettres qui sont migrées à un moment donné ; Les boîtes aux lettres Office 365 seront créées avec le nom d’utilisateur et les mots de passe de leurs comptes locaux ; Contrairement aux migrations à basculement, vos utilisateurs n’ont pas besoin de recréer leurs profils Outlook.

Si vous envisagez d’effectuer une migration hybride minimale, voici quelques éléments à prendre en compte :

- Vous devrez effectuer une synchronisation d’annuaires à usage unique entre vos serveurs Active Directory locaux et Office 365 ;
- Les utilisateurs peuvent se connecter à leur boîte aux lettres Office 365 en utilisant les mêmes nom d’utilisateur et mot de passe qu’ils utilisaient lors de la migration de leur boîte aux lettres.
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils (certains anciens téléphones Android peuvent avoir besoin d’un nouveau profil) et n’ont pas besoin de télécharger de nouveau leur courrier électronique.

Pour en savoir plus sur la migration hybride minimale, jetez un œil à la rubrique [utilisation d’un environnement hybride minimal pour migrer rapidement des boîtes aux lettres Exchange vers Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Hybride complet

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

- Les migrations hybrides complètes ne sont pas adaptées à tous les types d’organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas les avantages qui justifient les efforts et les coûts qu’il est nécessaire de définir. Si cela ressemble à votre organisation, nous vous recommandons vivement de prendre en compte le basculement ou les migrations hybrides minimales ;
- Vous devez configurer la synchronisation d’annuaires à l’aide d’Azure Active Directory Connect (AADConnect) entre vos serveurs Active Directory locaux et Office 365 ;
- Les utilisateurs peuvent se connecter à leur boîte aux lettres Office 365 en utilisant les mêmes nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local (nécessite Azure Active Directory Connect avec synchronisation de mot de passe et/ou services ADFS (Active Directory Federation Services));
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez ;
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils (certains anciens téléphones Android peuvent avoir besoin d’un nouveau profil) et n’ont pas besoin de télécharger de nouveau leur courrier électronique.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Office 365, mais qu’elle envisage de maintenir DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Exchange local. Si le dernier serveur Exchange est supprimé, vous ne pourrez pas modifier les destinataires Exchange dans Exchange Online. En effet, la source d’autorité reste dans votre annuaire Active Directory local et des modifications doivent y être apportées.

Si une migration hybride complète vous paraît, jetez un œil aux ressources suivantes pour vous aider dans votre migration :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- [Déploiements hybrides Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
- [Assistant de configuration hybride](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
- [FAQ de l’assistant Configuration hybride](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
- [Configuration requise pour un déploiement hybride](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Effectuer une mise à niveau vers une version plus récente d’Exchange Server en local

Bien que nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en effectuant une migration complète vers Office 365, nous comprenons également que certaines organisations doivent conserver certains serveurs Exchange en local. Cela peut être dû à des exigences réglementaires, afin de garantir que les données ne sont pas stockées dans un centre de données situé dans un autre pays, ou parce que vous avez des paramètres ou des exigences uniques qui ne peuvent pas être satisfaits dans le Cloud, ou que vous pouvez simplement utiliser Exchange pour gérer les boîtes aux lettres Cloud, car vous utilisez toujours Active Directory en local. Dans tous les cas pour lesquels vous choisissez ou devez conserver Exchange local, vous devez vous assurer que votre environnement Exchange 2010 est mis à niveau vers au moins Exchange 2013 ou Exchange 2016 et qu’Exchange 2010 est supprimé avant la fin de la date de prise en charge.

Pour une expérience optimale, nous vous recommandons de mettre à niveau votre environnement local restant vers Exchange 2016. Vous n’avez pas besoin d’installer Exchange Server 2013 si vous voulez effectuer directement à partir d’Exchange Server 2010 vers Exchange Server 2016.

Exchange 2016 inclut toutes les fonctionnalités et les améliorations incluses dans les versions précédentes d’Exchange, et correspond le mieux à l’expérience disponible avec Office 365 (même si certaines fonctionnalités sont disponibles uniquement dans Office 365). Voici quelques-unes des choses que vous avez été manquantes sur :

| **Version d’Exchange**                     | **Composants**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Architecture simplifiée réduisant le nombre de rôles serveur à trois (boîte aux lettres, accès au client, transport Edge)                                                                                                                                        |
|                                          | Stratégies de protection contre la perte de données (DLP) pour éviter la fuite d’informations sensibles                                                                                                                                                                |
|                                          | Amélioration significative de l’expérience Outlook Web App                                                                                                                                                                                                    |
| Exchange 2016                            | *Fonctionnalités d’Exchange 2013 et...*                                                                                                                                                                                                                   |
|                                          | Autres rôles serveur simplifiés pour le transport de boîtes aux lettres et de transport Edge uniquement                                                                                                                                                                                   |
|                                          | Amélioration de DLP et intégration avec SharePoint                                                                                                                                                                                                  |
|                                          | Résilience de base de données améliorée                                                                                                                                                                                                                         |
|                                          | Collaboration sur des documents en ligne                                                                                                                                                                                                                        |

| **Mûre**                        | **Informations supplémentaires**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fin des dates de prise en charge                     | À l’instar d’Exchange 2010, chaque version d’Exchange dispose de sa propre date de prise en charge :                                                                                                                                                                        |
|                                          | **Exchange 2013** -2023 avril                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -octobre 2025                                                                                                                                                                                                                     |
|                                          | Avant la fin de la date de prise en charge, plus tôt vous devrez effectuer une autre migration. Le 2023 avril est beaucoup plus proche que vous ne le pensez !                                                                                                                 |
| Chemin de migration vers Exchange 2013 ou 2016  | Le chemin de migration d’Exchange 2010 vers une version plus récente est le même que vous choisissiez Exchange 2013 ou Exchange 2016 :                                                                                                                              |
|                                          | Installez Exchange 2013 ou 2016 dans votre organisation Exchange 2010 existante déplacer des services et une autre infrastructure vers Exchange 2013 ou 2016 déplacer des boîtes aux lettres et des dossiers publics vers Exchange 2013 ou 2016 désactiver les serveurs Exchange 2010 restants  |
| Coexistence de la version                      | Lors de la migration vers Exchange 2013 ou Exchange 2016, vous pouvez installer l’une ou l’autre de ces versions dans une organisation Exchange 2010 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2013 ou Exchange 2016 et d’effectuer votre migration.             |
| Matériel serveur                          | La configuration matérielle requise pour le serveur a changé par rapport à Exchange 2010. Vous devez vous assurer que le matériel que vous allez utiliser est compatible. Vous pouvez en savoir plus sur la configuration matérielle requise pour chaque version ici :                                      |
|                                          | [Configuration requise pour Exchange 2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Configuration requise pour Exchange 2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Les améliorations significatives des performances d’Exchange, ainsi que l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus récents, vous aurez probablement besoin de serveurs moins nombreux pour prendre en charge le même nombre de boîtes aux lettres.                       |
| Version du système d'exploitation                 | Les versions minimales de système d’exploitation prises en charge pour chaque version sont les suivantes :                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Vous trouverez plus d’informations sur la prise en charge du système d’exploitation dans la [matrice de prise en charge d’Exchange](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Niveau fonctionnel de la forêt Active Directory | Les niveaux fonctionnels de forêt Active Directory minimum pris en charge pour chaque version sont les suivants :                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Pour plus d’informations sur la prise en charge du niveau fonctionnel de la forêt, consultez la rubrique [Exchange Supporting Matrix](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versions du client Office                   | Les versions de client Office minimales prises en charge pour chaque version sont les suivantes :                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (avec les dernières mises à jour)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Vous trouverez plus d’informations sur la prise en charge du client Office dans la [matrice de prise en charge d’Exchange](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Vous pouvez utiliser les ressources suivantes pour vous aider dans votre migration :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- Modifications apportées au schéma Active Directory pour Exchange [2016](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx)
- Configuration système requise pour Exchange [2016](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)
- Conditions préalables pour Exchange [2016](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf).

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

Cette affiche d’une page est un moyen rapide pour connaître les différents chemins que vous pouvez prendre pour empêcher les produits client et serveur Office 2010 et Windows 7 d’arriver à la fin de la prise en charge, avec les chemins d’accès et la prise en charge des options préférés dans Microsoft 365 Entreprise mis en surbrillance.

Vous pouvez également [télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).
      
## <a name="what-if-i-need-help"></a>Qu’en est-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Office 365, vous pouvez être autorisé à utiliser notre service FastTrack Microsoft. FastTrack fournit des meilleures pratiques, des outils et des ressources pour faciliter la migration vers Office 365. De plus, vous bénéficierez d’un véritable ingénieur de support qui vous guidera dans votre migration, de la planification et de la conception à la migration de votre dernière boîte aux lettres. Si vous souhaitez en savoir plus sur FastTrack, jetez un œil à [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes lors de la migration vers Office 365 et que vous n’utilisez pas FastTrack ou que vous migrez vers une version plus récente d’Exchange Server, nous sommes là pour vous aider. Voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>Sujets associés

[Ressources facilitant la mise à jour de vos clients et serveurs Office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)