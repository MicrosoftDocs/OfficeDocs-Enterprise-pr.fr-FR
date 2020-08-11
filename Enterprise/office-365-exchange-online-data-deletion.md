---
title: Microsoft 365 suppression des données Exchange Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Découvrez comment les suppressions de données conditionnelles et logicielles pour les boîtes aux lettres et les éléments dans les boîtes aux lettres sont gérées dans Exchange Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d7e96bb6bdb46cc81be6a684cb0f3cc1db354d9
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606580"
---
# <a name="exchange-online-data-deletion-in-microsoft-365"></a>Suppression de données Exchange Online dans Microsoft 365

Dans Exchange Online, il existe deux types de suppressions : les suppressions douces et les suppressions matérielles. Cela s’applique aux boîtes aux lettres et aux éléments d’une boîte aux lettres.

## <a name="soft-deleted-and-hard-deleted-mailboxes"></a>Boîtes aux lettres supprimées (récupérables) et supprimées de manière irréversible
Une boîte aux lettres utilisateur supprimée (récupérable) est une boîte aux lettres qui a été supprimée à l’aide du centre d’administration 365 de Microsoft ou de la cmdlet Remove-Mailbox et qui se trouve toujours dans la corbeille Azure Active Directory pendant moins de 30 jours. Une boîte aux lettres peut être supprimée de manière récupérable de l’une des manières suivantes :
- Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur est supprimé de manière récupérable (l’objet utilisateur est hors de portée ou dans le conteneur de la corbeille).
- Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur a été supprimé de manière irréversible, mais la boîte aux lettres Exchange Online est en conservation pour litige ou en conservation eDiscovery.
- Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur a été purgé au cours des 30 derniers jours ; la longueur maximale de rétention Exchange Online permet de conserver la boîte aux lettres dans un état supprimé (récupérable) avant qu’elle ne soit définitivement purgée et irrécupérable.

Une boîte aux lettres utilisateur supprimée de manière irréversible est une boîte aux lettres qui a été supprimée de l’une des manières suivantes :
- La boîte aux lettres utilisateur a été supprimée de manière récupérable pendant plus de 30 jours et l’utilisateur Azure Active Directory associé a été supprimé de manière irréversible. Tout le contenu des boîtes aux lettres, comme les courriers électroniques, les contacts et les fichiers, est définitivement supprimé.
- Le compte d’utilisateur associé à la boîte aux lettres de l’utilisateur a été supprimé de manière irréversible dans Azure Active Directory. La boîte aux lettres utilisateur est désormais supprimée de manière récupérable dans Exchange Online et reste en état de suppression récupérable pendant 30 jours. Si, dans la période de 30 jours, un nouvel utilisateur Azure Active Directory est synchronisé à partir du compte de destinataire d’origine avec le même **ExchangeGuid** ou **ArchiveGuid**, et que le nouveau compte est concédé sous licence pour Exchange Online, une suppression matérielle de la boîte aux lettres de l’utilisateur d’origine sera effectuée. Tout le contenu des boîtes aux lettres, comme les courriers électroniques, les contacts et les fichiers, est définitivement supprimé.
- Une boîte aux lettres supprimée (récupérable) est supprimée à l’aide de **Remove-Mailbox-PermanentlyDelete**.

Les scénarios de suppression ci-dessus supposent que la boîte aux lettres de l’utilisateur n’est pas dans l’un des États de suspension, comme la conservation pour litige ou la découverte électronique. S’il existe un type de conservation sur la boîte aux lettres, la boîte aux lettres ne peut pas être supprimée. Pour tous les types de destinataires de messagerie, tous les paramètres de [conservation](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) sont ignorés et n’ont aucun effet sur les suppressions ou suppressions logicielles.

## <a name="soft-deleted-and-hard-deleted-items"></a>Éléments supprimés et supprimés définitivement
Lorsqu’un utilisateur supprime un élément de boîte aux lettres (par exemple, un message électronique, un contact, un rendez-vous de calendrier ou une tâche), l’élément est déplacé vers le dossier éléments récupérables et dans un sous-dossier nommé « suppressions ». Il s’agit d’une suppression douce. La durée de conservation dans le dossier Suppressions des éléments supprimés dépend de la période de rétention des éléments supprimés qui est définie pour la boîte aux lettres. Une boîte aux lettres Exchange Online conserve les éléments supprimés pendant 14 jours par défaut, mais les administrateurs Exchange Online peuvent modifier ce paramètre pour augmenter la période maximale de 30 jours. (Pour obtenir la procédure détaillée d’augmentation de la période de rétention des éléments supprimés pour une boîte aux lettres Exchange Online, voir [modifier la durée de conservation des éléments supprimés définitivement pour une boîte aux lettres Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).) Les utilisateurs peuvent récupérer ou purger les éléments supprimés avant l’expiration du délai de rétention d’un élément supprimé. Pour ce faire, ils utilisent la fonctionnalité récupérer les éléments supprimés dans Microsoft Outlook ou Outlook sur le Web.

Si un utilisateur efface un élément supprimé à l’aide de la fonctionnalité récupérer les éléments supprimés dans Outlook ou Outlook sur le Web, il s’agit d’une suppression matérielle. Dans Exchange Online, la récupération d’élément unique est activée par défaut lors de la création d’une nouvelle boîte aux lettres, de sorte qu’un administrateur peut toujours [récupérer](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) des éléments supprimés définitivement avant l’expiration de la période de rétention des éléments supprimés. En outre, si un message est modifié par un utilisateur ou un processus, des copies de l'élément d'origine sont également conservées lorsque la fonctionnalité de récupération d'élément unique est activée.

## <a name="page-zeroing"></a>Mise à zéro des pages
La mise à *zéro* est un mécanisme de sécurité qui écrit des zéros ou un modèle binaire sur les données supprimées de manière à ce que les données supprimées soient plus difficiles à récupérer. Dans Exchange Online, les bases de données de boîtes aux lettres utilisent des *pages* comme leur unité de stockage et implémentent un processus de remplacement appelé mise à *zéro de page*. La mise à zéro des pages est activée par défaut et ne peut pas être désactivée par les clients ou par Microsoft. Les opérations de mise à zéro des pages sont enregistrées dans les fichiers journaux des transactions de sorte que toutes les copies d’une base de données donnée soient mises à zéro par page de la même manière. La mise à zéro d’une page sur une copie de base de données active fait en sorte que la page soit remise à zéro sur les copies passives de la base de données.

La mise à zéro des pages écrit un modèle binaire sur les enregistrements supprimés définitivement. Le modèle de mise à zéro des pages est spécifique aux opérations ESE (Extensible Storage Engine) (le nom du moteur de base de données interne utilisé par les serveurs dans Exchange Online) et il est différent pour les opérations d’exécution et les opérations de maintenance de la base de données en arrière-plan. (La maintenance de base de données en arrière-plan est un processus qui analyse en continu et analyse chaque base de données. Sa fonction principale est de totaliser les pages de base de données, mais elle gère également le nettoyage des enregistrements et des pages qui n’ont pas été annulés en raison d’un blocage de la Banque.)

Le tableau suivant répertorie les schémas de remplissage qui correspondent à des opérations d'exécution particulières.

| Opération d’exécution d’ESE   | Modèle de remplissage |
|--------------------------|--------------|
| Remplacement                  | R            |
| Suppression d'enregistrement/de valeur longue | D            |
| Espace de page libéré         | H            |


Le tableau suivant répertorie les schémas de remplissage correspondant à des opérations spécifiques effectuées pendant une opération de maintenance de base de données ESE en arrière-plan.

| Opération de maintenance de base de données ESE en arrière-plan | Modèle de remplissage |
|-----------------------------------------------|--------------|
| Suppression d’enregistrement                                 | D            |
| Suppression de valeur longue                             | L            |
| Espace libéré sur la page partiellement utilisée       | Z            |
| Espace libéré sur la page inutilisée               | U            |


### <a name="page-zeroing-process"></a>Processus de mise à zéro des pages
Le processus de mise à zéro des pages dépend du scénario de suppression. Le tableau suivant décrit les scénarios de suppression de base de données et les circonstances dans lesquelles les fonctions de mise à zéro des pages sont exécutées.

| Scénario de suppression de base de données | Processus et délai nécessaire à ESE pour mettre à zéro les données de la base de données |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| L’élément expire en fonction de la période de rétention des éléments supprimés. | Un thread asynchrone écrit un masque binaire sur les données supprimées. Cette action se produit dans les millisecondes suivant la suppression de l'enregistrement. Si le processus de banque se bloque alors que le travail de mise à zéro asynchrone est toujours en attente (ou le nettoyage du magasin de version est annulé en raison de la croissance du magasin de versions), la mise à zéro est effectuée lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données. |
| Scénario d’affichage : expiration des éléments d’Outlook/Outlook sur l’affichage des dossiers Web (par exemple, affichage conversation) | La mise à zéro des données a lieu lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données. |
| Déplacer une boîte aux lettres/supprimer un scénario de boîte aux lettres : boîte aux lettres source supprimée (expiration de la boîte aux lettres supprimée) | La mise à zéro des données a lieu lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données. |

### <a name="mailbox-data-types-without-page-zeroing"></a>Types de données de boîte aux lettres sans mise à zéro des pages
Les types de données de boîte aux lettres suivants n’ont aucune disposition pour la mise à zéro des pages :
- **Journaux de transactions de la base de données de boîtes aux lettres** : lorsque les journaux de transactions sont supprimés dans le cadre d’opérations normales, le système de fichiers n’est pas mis à zéro pour les blocs qui stockaient les fichiers journaux supprimés. Il est probable que le système de fichiers réutilise rapidement cet espace disponible pour les journaux nouvellement créés, mais il n’y a aucune garantie que cela se produira.
- **Fichiers du catalogue d’indexation de contenu** : Exchange Online utilise Search Foundation (également appelé Fast) pour la fonctionnalité d’indexation de la recherche. Le catalogue d’index de recherche est composé de plusieurs douzaines de fichiers stockés sur le même volume que le fichier de base de données de boîtes aux lettres. Lorsqu'un message est définitivement supprimé de la base de données de boîtes aux lettres, le contenu associé dans le catalogue de recherche n'est pas immédiatement supprimé. La suppression de contenu se produit lorsque Search Foundation effectue une fusion (ou une fusion principale) de nombreux petits fichiers de catalogue dans un fichier unique plus volumineux. Une fois la fusion principale terminée, les fichiers de catalogue plus petits sont supprimés. Aucun processus de mise à zéro des blocs stockant les fichiers de catalogue supprimés.

## <a name="continuous-replication"></a>Réplication continue
La réplication continue (également appelée envoi et relecture de journaux) est une technologie dans Exchange Online qui crée et gère des copies de chaque base de données de boîtes aux lettres pour fournir une haute disponibilité, la résilience de site et la récupération d’urgence. La réplication continue exploite la prise en charge de la récupération d’urgence de base de données Exchange Server pour fournir une technologie qui effectue la mise à jour asynchrone d’une ou plusieurs copies d’une base de données de boîtes aux lettres. Chaque serveur de boîtes aux lettres enregistre les mises à jour de base de données effectuées sur une base de données active (par exemple, l’activité de courrier électronique de l’utilisateur) sous la forme d’enregistrements de journal dans un ensemble séquentiel de fichiers journaux de transactions de 1 Mo. Cet ensemble de fichiers est appelé flux de journal. Dans une réplication continue, le flux de journal est également utilisé pour mettre à jour de manière asynchrone une ou plusieurs copies d’une base de données. Pour cela, il suffit de transmettre les journaux à un emplacement contenant une copie passive de la base de données active, puis de les relire dans la copie passive de la base de données. Si tous les journaux de la base de données active sont relus par rapport à une copie passive de la base de données, les deux bases de données sont équivalentes, ce qui explique que toute modification physique apportée à une base de données active est répliquée sur toutes les copies passives de cette base de données.

Toute suppression d’une base de données de boîtes aux lettres, qu’il s’agisse d’un élément de boîte aux lettres ou d’une boîte aux lettres entière, et si une suppression récupérable ou une suppression définitive, représente une modification physique de la base de données active. La mise à zéro des pages implique également d’apporter des modifications physiques à la base de données active. Ces modifications sont écrites dans les fichiers journaux par le biais d’un processus appelé réplication continue et, lorsque ces fichiers journaux sont relus par rapport à des copies passives de la base de données, les mêmes modifications physiques sont apportées à ces bases de données passives.