---
title: Suppression des données Office 365 Skype entreprise
ms.author: robmazz
author: robmazz
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
description: Explication de la suppression de données dans Skype entreprise.
ms.openlocfilehash: 33fbb91d2fbfd0e3133bfa2cca2118643b702d95
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844305"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a>Suppression de données Skype entreprise dans Office 365

Skype Entreprise prend en charge l'archivage des messages instantanés de pair à pair et entre plusieurs utilisateurs, et des activités de chargement de contenu dans les réunions. La fonctionnalité d'archivage requiert Exchange et est contrôlée par l'attribut Archive permanente de la boîte aux lettres Exchange de l'utilisateur, qui archive les messages électroniques et le contenu Skype Entreprise.

Tout l'archivage réalisé dans Skype Entreprise est considéré comme « archivage de niveau utilisateur », car vous l'activez et le désactivez pour un ou plusieurs utilisateurs ou groupes d'utilisateurs spécifiques en créant, configurant et appliquant une stratégie d'archivage de niveau utilisateur à ces utilisateurs. Il n'existe aucun contrôle direct des paramètres d'archivage à partir du Centre d'administration Skype Entreprise.

Les types de contenu suivants ne sont pas archivés dans Skype entreprise :

- Transferts de fichiers d’égal à égal
- Audio/vidéo pour messages instantanés et conférences d’égal à égal
- Partage d'applications pour les messages instantanés et les conférences pair à pair
- Annotations de conférence 

## <a name="meeting-content-retention"></a>Rétention de contenu de réunion

Les clients qui utilisent Skype entreprise peuvent télécharger du contenu dans une réunion Skype entreprise en tant que pièces jointes, telles que des présentations PowerPoint, des fichiers OneNote et d’autres fichiers. La période de rétention du contenu téléchargé lors d’une réunion est la suivante :

- **Réunion** ponctuelle : le contenu est conservé pendant 15 jours à partir du moment où la dernière personne quitte la réunion.
- **Réunion périodique** -le contenu est conservé pendant 15 jours après que la dernière personne a quitté la dernière session de la réunion. Le minuteur déterminant la période de rétention est réinitialisé lorsqu’une personne participe à une même session dans les 15 jours. Par exemple, supposons qu’une réunion Skype entreprise est planifiée pour s’exécuter une fois par semaine pendant un an, et qu’un fichier est chargé vers la réunion au cours de la première instance. Si au moins une personne rejoint la session de réunion chaque semaine, le fichier est conservé dans les serveurs Skype entreprise Online pendant toute l’année plus 15 jours après la fin de la dernière réunion de la série.
- **Réunion Conférence maintenant** : le contenu est conservé pendant 8 heures après l’heure de fin de la réunion.

> [!NOTE]
> Si un utilisateur est sans licence ou désactivé (par exemple, si **msRTCSIP-UserEnabled** est défini sur *false*), puis qu’il est de nouveau sous licence ou réactivé, le contenu de la réunion n’est pas conservé.

## <a name="meeting-expiration"></a>Expiration de réunion

Les utilisateurs peuvent accéder à une réunion spécifique après la fin, sous réserve des périodes d’expiration suivantes :

- **Réunion** ponctuelle : la réunion expire 14 jours après l’heure de fin planifiée de la réunion.
- **Réunion périodique avec date de fin** : la réunion expire 14 jours après l’heure de fin planifiée de la dernière occurrence de réunion.
- **Réunion Conférence maintenant** : la réunion expire au bout de 8 heures.

## <a name="whiteboard-collaboration"></a>Collaboration sur le tableau blanc

Tous les participants verront les annotations qui y sont ajoutées. Lors de l’enregistrement d’un tableau blanc, le tableau blanc et toutes les annotations seront stockés sur Skype entreprise Server et seront conservés sur le serveur en fonction des stratégies d’expiration de contenu de réunion définies par l’administrateur.

## <a name="audio-test-service"></a>Service de test audio

Un échantillon court (environ 5 secondes) de votre voix est enregistré pendant l’appel du service de test audio. L’exemple de voix est utilisé par vous pour vérifier et/ou vérifier la qualité audio de votre appel Skype entreprise en fonction de la qualité de l’enregistrement. Lorsque l’appel du service de test audio prend fin, l’exemple de voix est supprimé.

## <a name="persistent-group-chat"></a>Conversation de groupe permanente

La conversation de groupe permanente stocke le contenu des conversations de groupe. Si ce niveau est activé, l’administrateur peut contrôler la période de rétention, le serveur sur lequel ces informations sont stockées, si l’historique de la conversation de groupe est archivé à des fins de conformité ou à d’autres fins, et gère/modifie les propriétés d’une salle. Les utilisateurs disposant de rôles différents ont un accès différent aux données persistantes, comme suit :

- Les administrateurs peuvent supprimer le contenu plus ancien (par exemple, le contenu publié avant une date donnée) à partir d’une salle de conversation afin de réduire considérablement la taille de la base de données. Ou bien, ils peuvent supprimer ou remplacer les messages considérés comme inappropriés pour une salle de conversation donnée (ou considéré comme non approprié).
- Les utilisateurs finaux, y compris les auteurs de messages, ne peuvent pas supprimer du contenu d’une salle de conversation.
- Les gestionnaires de salle de conversation peuvent désactiver les salles mais ne peuvent pas supprimer les salles. Seuls les administrateurs peuvent supprimer une salle de conversation une fois qu’elle a été créée.