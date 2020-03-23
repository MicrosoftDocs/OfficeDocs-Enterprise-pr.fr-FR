---
title: Exchange multigéographique
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Découvrez les fonctionnalités multigéographiques d’Exchange Online.
ms.openlocfilehash: 27b636e1fb7f209a425a070f8024a1cdd461f59b
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890546"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Fonctionnalités multigéographiques d’Exchange Online

Dans un environnement multigéographique, vous pouvez sélectionner l’emplacement du contenu de la boîte aux lettres Exchange Online (données au repos) de chaque utilisateur.

Vous pouvez positionner des boîtes aux lettres dans des emplacements géographiques satellites en effectuant les opérations suivantes :

- Création d’une boîte aux lettres Exchange Online directement dans un emplacement géographique satellite.

- Déplacement d’une boîte aux lettres Exchange Online existante vers un emplacement géographique satellite en modifiant la position par défaut des données de l’utilisateur.

- Intégration d’une boîte aux lettres d’une organisation Exchange locale directement dans un emplacement géographique satellite.

## <a name="mailbox-placement-and-moves"></a>Positionnement et déplacement de boîte aux lettres

Une fois que Microsoft a accompli la procédure de configuration multigéographique requise, Exchange Online respecte l’attribut **PreferredDataLocation** des objets utilisateur dans Azure AD.

Exchange Online synchronise la propriété **MailboxRegion** du service d’annuaire Exchange Online avec la propriété **PreferredDataLocation** d’Azure AD. La valeur de **MailboxRegion** détermine l’emplacement géographique où seront placées les boîtes aux lettres utilisateur et toutes les boîtes aux lettres d’archivage associées à celles-ci. Il n’est pas possible de configurer la boîte aux lettres principale et les boîtes aux lettres d’archivage d’un utilisateur pour les faire résider dans emplacements géographiques différents. Un seul emplacement géographique peut être configuré par objet utilisateur.

- Lorsque la valeur de la propriété **PreferredDataLocation** est configurée sur un utilisateur disposant déjà d’une boîte aux lettres, celle-ci est placée dans une file d’attente de déplacement, puis déplacée automatiquement vers l’emplacement géographique spécifié.

- Lorsque la valeur de la propriété **PreferredDataLocation** est configurée sur un utilisateur ne disposant pas encore d’une boîte aux lettres, quand vous approvisionnez la boîte aux lettres, celle-ci est configurée dans l’emplacement géographique spécifié.

- Lorsque la valeur de la propriété **PreferredDataLocation** n’est pas spécifiée sur un utilisateur, quand vous approvisionnez la boîte aux lettres, celle-ci est configurée dans l’emplacement géographique central.

- Si le code **PreferredDataLocation** est incorrect (par exemple, un type de NaN au lieu de NAM), la boîte aux lettres est approvisionnée dans l’emplacement géographique central.

**Remarque** : les fonctionnalités multigéographiques et les réunions Skype Entreprise Online hébergées au niveau régional utilisent toutes deux la propriété **PreferredDataLocation** sur les objets utilisateur pour localiser les services. Si vous configurez les valeurs de **PreferredDataLocation** sur des objets utilisateur pour des réunions organisées par région, la boîte aux lettres des utilisateurs correspondants est automatiquement déplacée vers l’emplacement géographique spécifié après activation de la fonction multigéographique sur le client Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitations des fonctionnalités multigéographiques dans Exchange Online

- Les fonctionnalités de sécurité et de conformité (par exemple, d’audit et d’eDiscovery) disponibles dans le Centre d’administration Exchange ne le sont pas dans des organisations multigéographiques. Au lieu de cela, vous devez utiliser le [Centre de sécurité et conformité Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.

- Les utilisateurs d’Outlook pour Mac peuvent être confrontés à une perte temporaire d’accès à leur dossier Archive en ligne pendant que vous déplacez leur boîte aux lettres vers un nouvel emplacement géographique. Cette situation se produit quand les boîtes aux lettres principale et d’archivage de l’utilisateur se trouvent dans des emplacements géographiques différents, car des déplacements inter-géographiques de boîtes aux lettres peuvent s’accomplir à des moments différents.

- Les utilisateurs ne peuvent pas partager des *dossiers de boîte aux lettres* entre plusieurs emplacements géographiques dans Outlook sur le web (précédemment nommé Outlook web App ou OWA). Par exemple, un utilisateur résidant dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé figurant dans une boîte aux lettres située aux États-Unis. En revanche, les utilisateurs d’Outlook sur le web peuvent ouvrir d’*autres boîtes aux lettres* situées dans différents emplacements géographiques dans une fenêtre de navigateur distincte, comme décrit dans [Ouvrir la boîte aux lettres d’un autre utilisateur dans une nouvelle fenêtre de navigateur dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Remarque** : le partage inter-géographique de dossier de boîte aux lettres est pris en charge dans Outlook sous Windows.

- Les dossiers publics sont pris en charge dans les organisations multigéographiques. Toutefois, ils doivent rester dans l’emplacement géographique central. Vous ne pouvez pas déplacer des dossiers publics vers des emplacements géographiques satellites.

- Dans un environnement multi-géographique, l’audit de boîte aux lettres inter-géographique n’est pas pris en charge. Par exemple, si un utilisateur se voit attribuer les autorisations d’accès à une boîte aux lettres partagée dans un autre emplacement géographique, les actions de boîte aux lettres effectuées par cet utilisateur ne sont pas enregistrées dans le journal d’audit de la boîte aux lettres partagée. Pour plus d’informations, voir [Gérer l’audit de boîte aux lettres](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide).
