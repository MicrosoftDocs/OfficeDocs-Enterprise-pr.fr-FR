---
title: Exchange Multi-Géo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez les fonctionnalités multigéographiques dans Exchange Online.
ms.openlocfilehash: 70db45bb7626c49a2c9cd6ec827bff6ca16d4673
ms.sourcegitcommit: 5e85536a6f53262136acfaac640f5d109a65f643
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "31765066"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Fonctionnalités multi-localisés dans Exchange Online

Dans un environnement multi-géo, vous pouvez sélectionner l'emplacement du contenu de la boîte aux lettres Exchange Online (données au repos) par utilisateur.

Vous pouvez placer des boîtes aux lettres dans des emplacements géographiques satellites en procédant comme suit:

- Création d'une nouvelle boîte aux lettres Exchange Online directement dans un emplacement géographique satellite.

- Déplacement d'une boîte aux lettres Exchange Online existante vers un emplacement géographique satellite en modifiant l'emplacement des données par défaut de l'utilisateur.

- Intégration d'une boîte aux lettres à partir d'une organisation Exchange locale directement à un emplacement géographique satellite.

## <a name="mailbox-placement-and-moves"></a>Placement et déplacement de boîtes aux lettres

Une fois que Microsoft a terminé les étapes de configuration multigéographiques prérequises, Exchange Online respecte l'attribut **PreferredDataLocation** sur les objets utilisateur dans Azure ad.

Exchange Online synchronise la propriété **PreferredDataLocation** à partir d'Azure ad dans la propriété **MailboxRegion** dans le service d'annuaire Exchange Online. La valeur de **MailboxRegion** détermine l'emplacement géographique où les boîtes aux lettres d'utilisateur et les boîtes aux lettres d'archivage associées seront placées. Il n'est pas possible de configurer la boîte aux lettres principale d'un utilisateur et les boîtes aux lettres d'archivage pour qu'elles résident dans des emplacements géographiques différents. Un seul emplacement géographique peut être configuré par objet utilisateur.

- Lorsque **PreferredDataLocation** est configuré sur un utilisateur disposant d'une boîte aux lettres existante, celle-ci est placée dans une file d'attente de relocalisation et déplacée automatiquement vers l'emplacement géographique spécifié.

- Lorsque **PreferredDataLocation** est configuré sur un utilisateur sans boîte aux lettres existante, lorsque vous approvisionnez la boîte aux lettres, elle est mise en service dans l'emplacement géographique spécifié.

- Lorsque **PreferredDataLocation** n'est pas spécifié sur un utilisateur, lorsque vous approvisionnez la boîte aux lettres, celle-ci est configurée à l'emplacement géographique central.

- Si le code **PreferredDataLocation** est incorrect (par exemple, un type Nan au lieu de Nam), la boîte aux lettres sera configurée à l'emplacement géographique central.

**Remarque**: les fonctionnalités multigéographiques et les réunions hébergées dans la région de Skype entreprise Online utilisent toutes deux la propriété **PreferredDataLocation** sur les objets utilisateur pour localiser les services. Si vous configurez des valeurs **PreferredDataLocation** sur des objets utilisateur pour des réunions hébergées dans le pays, la boîte aux lettres de ces utilisateurs est automatiquement déplacée vers l'emplacement géographique spécifié après l'activation de l'option multi-géo sur le client Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitations de fonctionnalité pour multi-géo dans Exchange Online

- Les fonctionnalités de sécurité et de conformité (par exemple, audit et eDiscovery) qui sont disponibles dans le centre d'administration Exchange ne sont pas disponibles dans les organisations multigéographiques. Au lieu de cela, vous devez utiliser le [Centre de sécurité Office 365 Security &](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.

- Les utilisateurs d'Outlook pour Mac peuvent être confronté à une perte temporaire d'accès à leur dossier d'archivage en ligne pendant que vous déplacez leur boîte aux lettres vers un nouvel emplacement géographique. Cette condition se produit lorsque les boîtes aux lettres principale et d'archivage de l'utilisateur se trouvent dans des emplacements géographiques différents, car les déplacements de boîtes aux lettres entre les zones géographiques peuvent se terminer à différents moments.

- Les utilisateurs ne peuvent pas partager des *dossiers de boîte aux lettres* dans des emplacements géographiques dans Outlook sur le Web (anciennement Outlook Web App ou OWA). Par exemple, un utilisateur de l'Union européenne ne peut pas utiliser Outlook sur le Web pour ouvrir un dossier partagé dans une boîte aux lettres située aux États-Unis. Toutefois, les utilisateurs d'Outlook sur le Web peuvent ouvrir d' *autres boîtes aux lettres* dans différents emplacements géographiques à l'aide d'une fenêtre de navigateur distincte, comme décrit dans [ouvrir la boîte aux lettres d'une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Remarque**: le partage de dossiers de boîte aux lettres entre géo est pris en charge dans Outlook sur Windows.

- Les dossiers publics sont pris en charge dans les organisations multigéographiques. Toutefois, les dossiers publics doivent rester à l'emplacement géographique central. Vous ne pouvez pas déplacer des dossiers publics vers des emplacements géographiques satellites.
