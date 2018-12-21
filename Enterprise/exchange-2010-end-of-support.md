---
title: Exchange 2010 fin de la feuille de route de prise en charge
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 avoisine la fin du support. Utilisez ce guide de planification comme un guide pour préparer la mise à niveau vers Exchange Online ou une version plus récente du serveur Exchange local.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: b45ad32a0a421d9834424e02838b6f941c259b9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "27382695"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 fin de la feuille de route de prise en charge

Sur **le 14 janvier 2020**, Exchange Server 2010 atteindra la fin du support. Si vous n’avez pas déjà commencé votre migration à partir d’Exchange 2010 vers Office 365 ou Exchange 2016, il est temps à démarrer votre planification.

## <a name="what-does-end-of-support-mean"></a>Quel ne prend fin moyenne de la prise en charge ?

Exchange Server, comme presque tous les produits Microsoft, dispose d’un cycle de vie de prise en charge au cours de laquelle nous fournissons des nouvelles fonctionnalités, des correctifs, des correctifs de sécurité et ainsi de suite. Ce cycle de vie dure généralement dix ans à compter de la date de publication initiale du produit, et la fin de ce cycle de vie est appelée fin du produit de prise en charge. Lorsque Exchange 2010 atteint la fin de la prise en charge sur 14 janvier 2020, Microsoft ne fournira plus :

- Support technique pour les problèmes qui peuvent se produire ;
- Correctifs pour les problèmes qui ont été identifiés et qui peut avoir un impact sur la stabilité et la facilité d’utilisation du serveur ;
- Correctifs de sécurité pour les vulnérabilités qui sont découvertes et qui peuvent rendre le serveur vulnérables aux failles de sécurité ;
- Mises à jour de fuseau horaire.

Votre installation d’Exchange 2010 continuera à s’exécuter après cette date. Toutefois, en raison des modifications mentionnées ci-dessus, il est vivement recommandé que vous migrez d’Exchange 2010 dès que possible.

Pour plus d’informations sur les serveurs Office 2010 proches de la fin de la prise en charge, voir les [ressources pour vous aider à mettre à niveau à partir d’Office 2010 des serveurs et clients](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Avec Exchange 2010 a atteint la fin de la prise en charge, il s’agit d’un moment idéal pour découvrir les différentes options et préparation d’un plan de migration. Vous pouvez :

- Migrer entièrement vers Office 365. Migrer des boîtes aux lettres à l’aide de hybride à basculement, minimal, ou la migration hybride, puis sur Supprimer sur site Active Directory et des serveurs Exchange.
- Migrer vos serveurs Exchange 2010 vers Exchange 2016 sur vos serveurs sur site.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Office 365, mais a l’intention de conserver DirSync ou Azure AD se connecter en place pour continuer à gérer les comptes d’utilisateurs à partir de sur site Active Directory, vous devez conserver au moins un Exchange server local. Si le dernier serveur Exchange est supprimé, vous ne pourrez pas apporter des modifications à des destinataires Exchange dans Exchange Online. Il s’agit, car la source d’autorité est conservée dans Active Directory sur site et les modifications doivent être apportées. Dans ce scénario, vous disposez des options suivantes :

- (**Recommandé**) Si vous pouvez migrer vos boîtes aux lettres vers Office 365 et mettre à niveau vos serveurs en 14 janvier 2020, utilisez Exchange 2010 pour se connecter à Office 365 et migrer les boîtes aux lettres. Ensuite, migration Exchange 2010 vers Exchange 2016 et désactiver tous les autres serveurs Exchange 2010.
- Si vous ne pouvez pas effectuer la migration de boîtes aux lettres et mise à niveau du serveur local à 14 janvier 2020, mettre à niveau vos serveurs d’Exchange 2010 local vers Exchange 2016 tout d’abord, puis utilisez 2016 Exchange pour se connecter à Office 365 et migrer les boîtes aux lettres.

> [!NOTE]
> Pendant un peu plus complexe, vous pouvez également migrer des boîtes aux lettres vers Office 365 lors de la migration de vos serveurs d’Exchange 2010 local vers Exchange 2016.

Les sections suivantes explorent chaque option en détail.

## <a name="migrate-to-office-365"></a>Migration vers Office 365

Migration de votre messagerie vers Office 365 est l’option meilleure et plus simple pour vous aider à retirer de votre déploiement Exchange 2010. Avec une migration vers Office 365, vous pouvez passer un tronçon unique à partir de l’ancienne technologie à la pointe de fonctionnalités, telles que :

- Fonctionnalités de conformité telles que les stratégies de rétention, sur Place et en attente pour litige, place eDiscovery, etc. ;
- Équipes Microsoft ;
- Power BI ;
- Boîte de réception focus ;
- Étudier Analytique ;

Office 365 obtient également les nouvelles fonctionnalités et les expériences de première et vous et vos utilisateurs peuvent généralement démarrer à les utiliser immédiatement. En plus des nouvelles fonctionnalités, vous n’aurez à vous préoccuper :

- Achat et maintenance du matériel ;
- Payer pour chauffage et refroidissement de vos serveurs ;
- Mise à jour sur les correctifs de sécurité, les produits et fuseau horaire ;
- Gestion du stockage et logiciels pour prendre en charge les exigences de conformité ;
- Mise à niveau vers une nouvelle version d’Exchange - vous n’êtes toujours sur la dernière version d’Exchange dans Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Comment dois-je migrer vers Office 365 ?

Selon votre organisation, vous disposez de plusieurs options qui vous aideront à accéder à Office 365. Lorsque vous choisissez une option de migration, vous devez prendre en compte certains éléments tels que le nombre de sièges ou vous devez déplacer les boîtes aux lettres, combien de temps vous souhaitez que la migration à la dernière, et si vous avez besoin d’une intégration transparente entre votre installation sur site et les Office 365 au cours de la migration. Ce tableau présente les options de migration et les facteurs les plus importants que vous devez déterminer la méthode que vous allez utiliser.

| **Option de migration**     | **Taille de l’organisation** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Migration à basculement        | Moins de 150 sièges  | Une semaine ou moins      |
| Migration hybride minimal | Moins de 150 sièges  | Quelques semaines ou moins |
| Migration hybride    | Plus de 150 sièges   | Quelques semaines ou plus |

Les sections suivantes fournissent une vue d’ensemble de ces méthodes. Consultez la rubrique [décider sur un chemin de migration](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) pour connaître les détails de chaque méthode.

### <a name="cutover-migration"></a>Migration à basculement

Une migration à basculement est un où, à une date préalable et une heure, vous allez migrer tous vos boîtes aux lettres, des groupes de distribution, contacts et ainsi de suite, vers Office 365 ; Lorsque vous avez terminé, vous devez arrêter les serveurs Exchange locaux et commencer à utiliser Office 365 exclusivement.

La méthode de migration à basculement est excellente pour les petites organisations qui n’ont pas très grand nombre de boîtes aux lettres, pour accéder rapidement à Office 365 et ne souhaitez pas traiter avec une partie de la complexité des autres méthodes. Mais elle également quelque peu limité, car elle doit être inférieur ou égal à achevé dans une semaine et car elle requiert que les utilisateurs de reconfigurer leurs profils Outlook. Pendant la migration à basculement peut gérer jusqu'à 2 000 boîtes aux lettres, nous vous recommandons vivement de que migrer un maximum de boîtes aux lettres de 150 avec cette méthode. Si vous essayez de migrer des boîtes aux lettres plus de 150, vous pouvez exécuter en dehors de temps pour transférer les boîtes aux lettres avant l’échéance et votre support technique personnel peut-être obtenir surchargé ont-elles utilisateurs reconfigurer Outlook.

Si vous envisagez d’effectuer une migration à basculement, voici quelques éléments à prendre en compte prendre en considération :

- Office 365 devra se connecter à vos serveurs Exchange 2010 à l’aide d’Outlook Anywhere sur le port TCP 443 ;
- Toutes les boîtes aux lettres locales seront déplacées vers Office 365 ;
- Vous aurez besoin d’un compte d’administrateur local qui dispose d’un accès pour lire le contenu des boîtes aux lettres des utilisateurs ;
- Le Exchange 2010 accepté domaines que vous souhaitez utiliser dans Office 365 besoin à ajouter en tant que domaines vérifiés dans le service ;
- Entre le moment où vous démarrez la migration et lorsque vous commencez la phase d’exécution, Office 365 synchronisera régulièrement les boîtes aux lettres locales et Office 365. Cela vous permet d’effectuer la migration sans vous préoccuper de messagerie en cours laissée dans vos boîtes aux lettres locales ;
- Les utilisateurs recevront des nouveaux mots de passe temporaires pour leur compte Office 365 que les utilisateurs ont besoin pour modifier les lors de la connexion à leurs boîtes aux lettres pour la première fois ;
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez ;
- Les utilisateurs devront définir un nouveau profil Outlook sur chacun de leurs périphériques et télécharger à nouveau de leur messagerie électronique. La quantité de messagerie Outlook télécharge peut varier. Pour plus d’informations, jetez un œil à [Modifier le nombre de messages pour conserver en mode hors connexion](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Pour en savoir plus sur la migration à basculement, jetez un œil à :

- [Vous devez savoir à propos d’une migration à basculement messagerie vers Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Effectuer une migration à basculement de messagerie vers Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimal

Hybride minimal ou express, la migration est une où vous avez quelques centaines boîtes aux lettres à migrer vers Office 365, peuvent effectuer la migration de quelques semaines et n’ont pas besoin des fonctionnalités de migration hybride avancées comme calendrier partagé d’informations de disponibilité plus d’informations.

Migration hybride minimale est idéale pour les entreprises à prendre plus de temps pour migrer leurs boîtes aux lettres vers Office 365, mais toujours plan pour effectuer la migration de quelques semaines. Vous obtenez des avantages de la migration hybride plus avancée sans de nombreux aspects complexes. Vous pouvez contrôler le nombre et les, les boîtes aux lettres sont migrés à un moment donné ; Boîtes aux lettres Office 365 seront créés avec le nom d’utilisateur et mots de passe de leurs comptes locaux ; et, à la différence des migrations à basculement, vos utilisateurs n’est pas nécessaire de recréer leurs profils Outlook.

Si vous pensez effectuer la migration hybride minimal, voici quelques points à prendre en compte :

- Vous devez effectuer une synchronisation d’annuaire unique entre les serveurs d’Active Directory sur site Office 365 ;
- Les utilisateurs seront en mesure de se connecter à leur boîte aux lettres Office 365 à l’aide du même nom d’utilisateur et mot de passe qu’ils utilisaient lorsque leur boîte aux lettres a été migrée ;
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez ;
- Les utilisateurs n’avez pas besoin de configurer un nouveau profil Outlook dans la plupart de leurs périphériques (certains téléphones Android antérieurs devront un nouveau profil) et ne sont pas accéder à leur messagerie électronique.

Pour en savoir plus sur la migration hybride minimal, jetez un œil à [Hybride Minimal utiliser rapidement migrer des boîtes aux lettres Exchange vers Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Hybride

Une migration complète hybride est un où votre organisation possède plusieurs centaines, jusqu'à des dizaines de milliers, de boîtes aux lettres et que vous souhaitez déplacer certains ou tous les vers Office 365. Étant donné que ces migrations sont généralement à long terme, migrations hybrides rendent possible :

- Afficher les utilisateurs locaux les informations de calendrier et de disponibilité pour les utilisateurs dans Office 365 et vice versa ;
- Voir une liste d’adresses globale unifiée qui contient des destinataires dans les locaux et Office 365 ;
- Afficher les cartes de destinataires Outlook complètes pour tous les utilisateurs, qu’ils soient locaux ou dans Office 365 ;
- Sécuriser les communications de messagerie entre les serveurs Exchange locaux et Office 365 à l’aide de TLS et des certificats ;
- Traiter les messages envoyés entre les serveurs Exchange locaux et Office 365 comme internes, leur permettant de :
- Être correctement évaluée et traités par les agents de transport et de conformité ciblage des messages internes ;
- Ignorer les filtres anti-spam.

Migrations hybrides complète sont recommandées pour les organisations qui doivent rester dans une configuration hybride pour le nombre de mois ou plus. Vous obtiendrez les fonctionnalités répertoriées plus haut dans cette section, plus la synchronisation d’annuaires, meilleures fonctionnalités de conformité intégrée et la possibilité de déplacer des boîtes aux lettres vers ou à partir d’Office 365 à l’aide de déplacements de boîtes aux lettres en ligne. Office 365 devient une extension de votre organisation locale.

Si vous envisagez d’effectuer une migration hybride, voici quelques points à prendre en compte :

- Migrations hybrides complète ne convient pas à tous les types d’organisations. En raison de la complexité des migrations hybrides complète, organisations comptant moins de quelques boîtes aux centaines lettres ne voient généralement avantages justifier l’effort et le coût nécessaire pour configurer un. Si cela ressemble à votre organisation, il est vivement recommandé que vous tenir compte des migrations à basculement ou minimales hybrides à la place.
- Vous devez configurer la synchronisation d’annuaires à l’aide d’Azure Active Directory se connecter (AADConnect) entre les serveurs d’Active Directory sur site Office 365 ;
- Les utilisateurs seront en mesure de se connecter à leur boîte aux lettres Office 365 à l’aide du même nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local (requiert Azure Active Directory se connecter à la synchronisation de mot de passe et/ou Active Directory Federation Services) ;
- Vous avez besoin d’une licence Office 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez ;
- Les utilisateurs n’avez pas besoin de configurer un nouveau profil Outlook dans la plupart de leurs périphériques (certains téléphones Android antérieurs devront un nouveau profil) et ne sont pas accéder à leur messagerie électronique.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Office 365, mais a l’intention de conserver DirSync ou Azure AD se connecter en place pour continuer à gérer les comptes d’utilisateurs à partir de sur site Active Directory, vous devez conserver au moins un Exchange server local. Si le dernier serveur Exchange est supprimé, vous ne pourrez pas apporter des modifications à des destinataires Exchange dans Exchange Online. Il s’agit, car la source d’autorité est conservée dans Active Directory sur site et les modifications doivent être apportées.

Si un sons de migration hybride vous convient, jetez un œil aux ressources suivantes pour vous aider avec votre migration :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- [Déploiements hybrides Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Assistant de configuration hybride](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [FAQ de l’assistant Configuration hybride](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Configuration requise pour un déploiement hybride](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Mise à niveau vers une version plus récente d’Exchange Server sur site

Pendant que nous pensons fortement que vous pouvez obtenir la meilleure expérience utilisateur et la valeur en entièrement migration vers Office 365, aussi bien que certaines organisations ont besoin de conserver des serveurs Exchange locaux. Cela peut être dû à des exigences réglementaires, afin de garantir des données n’est pas stockées dans un centre de données situé dans un autre pays, ou il est possible que vous disposez des paramètres uniques ou ne peut pas être requise dans le nuage, ou il peut s’agir simplement que vous avez besoin d’Exchange gérer les boîtes aux lettres du nuage, car vous utilisez toujours Active Directory local. Dans tous les cas pour lesquels vous choisissez ou devez conserver Exchange locale, vous devez vérifier que votre environnement Exchange 2010 est mis à niveau pour au moins Exchange 2013 ou 2016 Exchange et Exchange 2010 est supprimée avant la date de fin du Support.

Pour optimiser les performances, nous vous recommandons de mettre à niveau votre environnement local restant à 2016 Exchange. Vous n’avez pas besoin d’installer Exchange Server 2013 si vous souhaitez accéder directement à partir d’Exchange Server 2010 2016 du serveur Exchange.

2016 Exchange inclut toutes les fonctionnalités et améliorations incluses avec les versions précédentes d’Exchange, et il correspond le mieux à l’expérience disponible avec Office 365 (bien que certaines fonctionnalités sont disponibles uniquement dans Office 365). Découvrez quelques-unes des choses que vous avez été pas en mesure de :

| **Version d’Exchange**                     | **Fonctionnalités**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Architecture simplifiée en réduisant le nombre de rôles de serveur à trois (boîte aux lettres, accès au Client, Edge Transport)                                                                                                                                        |
|                                          | Stratégies de protection contre la perte (DLP) données assurent la fuite d’informations sensibles                                                                                                                                                                |
|                                          | Considérablement expérience améliorée dans Outlook Web App                                                                                                                                                                                                    |
| Exchange 2016                            | *Fonctionnalités d’Exchange 2013 et...*                                                                                                                                                                                                                   |
|                                          | Plus les rôles de serveur simplifié à la boîte aux lettres et de Transport Edge                                                                                                                                                                                   |
|                                          | DLP améliorée ainsi que l’intégration avec SharePoint                                                                                                                                                                                                  |
|                                          | Résilience améliorée de la base de données                                                                                                                                                                                                                         |
|                                          | Collaboration sur des documents en ligne                                                                                                                                                                                                                        |

| **Considération**                        | **Informations supplémentaires**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Prise en charge des dates de fin de                     | Comme Exchange 2010, chaque version d’Exchange a son propre date de fin du support technique :                                                                                                                                                                        |
|                                          | **Exchange 2013** - avril 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** - 2025 octobre                                                                                                                                                                                                                     |
|                                          | Plus la date de fin du support, plus tôt, vous devrez effectuer la migration d’une autre. Avril 2023 est beaucoup plus proche que vous ne le pensez !                                                                                                                 |
| Chemin de migration vers Exchange 2013 ou 2016  | La possibilité de migration d’Exchange 2010 vers une version plus récente est le même si vous choisissez d’Exchange 2013 ou 2016 Exchange :                                                                                                                              |
|                                          | Installer Exchange 2013 ou 2016 dans les services de déplacement d’organisation Exchange 2010 existants et autres infrastructure pour Exchange 2013 ou 2016 déplacer les boîtes aux lettres et des dossiers publics vers Exchange 2013 ou mise hors service 2016 restant des serveurs Exchange 2010  |
| Coexistence de version                      | Lors de la migration vers Exchange 2013 ou 2016 Exchange, vous pouvez installer une version dans une organisation Exchange 2010 existante. Cela vous permet de vous permettent d’installer un ou plusieurs serveurs Exchange 2013 ou 2016 Exchange et effectuer une migration.             |
| Matériel serveur                          | Configuration matérielle requise Server ont changé d’Exchange 2010. Vous devez vous assurer que le matériel que vous allez utiliser est compatible. Vous pouvez trouver plus d’informations sur la configuration matérielle requise pour chaque version ici :                                      |
|                                          | [Configuration système requise pour Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Configuration système requise pour Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Vous trouverez qu’avec les améliorations significatives des performances d’Exchange et l’augmentation de la puissance et la capacité de stockage de serveurs plus récents, vous aurez probablement besoin moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.                       |
| Version du système d'exploitation                 | Les versions minimales du système d’exploitation pris en charge pour chaque version sont les suivants :                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Vous trouverez plus d’informations sur la prise en charge du système d’exploitation au niveau de la [Matrice de support d’Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Niveau fonctionnel de la forêt répertoire actif | Minimum pris en charge Active Directory niveaux fonctionnels de forêt de chaque version sont les suivants :                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Vous trouverez plus d’informations sur le support de niveau fonctionnel de forêt au niveau de la [Matrice de support d’Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versions du client Office                   | Les versions du client Office prises en charge minimales pour chaque version sont les suivants :                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (avec les dernières mises à jour)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Vous trouverez plus d’informations sur la prise en charge du client Office à la [Matrice de support d’Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Vous pouvez utiliser les ressources suivantes pour vous aider avec votre migration :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- Modifications de schéma Active Directory pour de Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), groupes de [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Configuration système requise pour de Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), groupes de [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Conditions requises pour de Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), groupes de [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>Que se passe-t-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Office 365, vous pouvez prétendre à utiliser notre service FastTrack Microsoft. FastTrack fournit les meilleures pratiques, outils et ressources pour effectuer la migration vers Office 365 aussi transparente que possible. De plus, vous aurez un ingénieur du support réel qui vous guident tout au long de la migration, de planification et de conception à la migration de votre boîte aux lettres dernière. Si vous souhaitez en savoir plus sur FastTrack, jetez un œil à [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes pendant la migration vers Office 365 et que vous n’utilisez pas FastTrack ou votre migration vers une version plus récente d’Exchange Server, nous sommes ici pour vous aider. Voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Voir aussi

[Ressources pour vous aider à mettre à niveau à partir d’Office 2010 des serveurs et des clients](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Groupe de retraite Office (Communauté Microsoft Tech)](https://go.microsoft.com/fwlink/?linkid=842065)
