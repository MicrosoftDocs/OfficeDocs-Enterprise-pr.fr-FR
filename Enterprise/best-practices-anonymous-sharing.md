---
title: Meilleures pratiques pour le partage non authentifié
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
f1.keywords: NOCSH
description: Découvrez les meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés.
ms.openlocfilehash: 38afdcb2d59547144e57656971395c48506bcbbf
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549123"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés

Le partage non authentifié (liens *Tout le monde*) est pratique et utile dans différents scénarios. Les liens *Tout le monde* sont la méthode la plus simple pour partager : les personnes peuvent ouvrir le lien sans authentification et sont libres de le transmettre à d’autres personnes.

En règle générale, l’ensemble du contenu d’une organisation ne nécessite pas de partage non authentifié. Cet article décrit les options possibles pour vous aider à créer un environnement dans lequel vos utilisateurs peuvent partager des fichiers et des dossiers de manière non authentifiée, mais où des éléments de protection sont mis en place pour protéger le contenu de votre organisation.

> [!NOTE]
> Pour que le partage non authentifié puisse fonctionner, vous devez l’activer pour votre organisation et pour le site ou l’équipe qui sera concerné. Pour plus d’informations sur le scénario que vous souhaitez mettre en place, voir [Collaborer avec des personnes extérieures à votre organisation](collaborating-with-people-outside-your-organization.md).

## <a name="set-an-expiration-date-for-anyone-links"></a>Définir une date d’expiration pour les liens Tout le monde

Les fichiers sont souvent stockés dans des sites, des groupes et des équipes pendant une période prolongée. Il peut arriver qu’une stratégie de rétention des données nécessite la conservation des fichiers pendant plusieurs années. Si ces fichiers sont partagés avec des personnes non authentifiées, cela peut entraîner un accès inattendu et des modifications aux fichiers dans le futur. Pour atténuer cette possibilité, vous pouvez configurer un délai d’expiration pour les liens *Tout le monde*.

Une fois qu' un lien *Tout le monde* arrive à expiration, il ne peut plus être utilisé pour accéder au contenu.

Pour définir une date d’expiration pour les liens Tout le monde
1. Ouvrez le centre d’administration SharePoint Online.
2. Dans la barre de navigation de gauche, cliquez sur **Partage**.
3. Sous **Paramètres avancés pour les liens Tout le monde**, cochez la case **Ces liens doivent expirer dans tant de jours**.</br>
   ![Capture d’écran des paramètres d’expiration du lien Tout le monde au niveau de l’organisation dans SharePoint](media/sharepoint-organization-anyone-link-expiration.png)
4. Tapez un nombre de jours dans la zone, puis cliquez sur **Enregistrer**.

Notez qu’une fois qu' un lien *Tout le monde* arrive à expiration, le fichier ou dossier peut être repartagé avec un nouveau lien *Tout le monde*.

## <a name="set-link-permissions"></a>Définir les autorisations de lien

Par défaut, les liens *Tout le monde* d’un fichier permettent aux utilisateurs de modifier le fichier, et les liens *Tout le monde* d’un dossier permettent aux utilisateurs de modifier et d’afficher des fichiers, mais aussi de charger de nouveaux fichiers dans le dossier. Vous pouvez modifier ces autorisations pour les fichiers et les dossiers indépendamment de la lecture seule.

Si vous voulez autoriser le partage non authentifié, mais que vous craignez que des personnes non authentifiées modifient le contenu de votre organisation, vous pouvez définir les autorisations des fichiers et des dossiers sur **Vue**.

Pour établir des autorisations pour les liens Tout le monde
1. Ouvrez le centre d’administration SharePoint Online.
2. Dans la barre de navigation de gauche, cliquez sur **Partage**.
3. Sous **Paramètres avancés pour les liens Tout le monde**, sélectionnez les autorisations d’accès aux fichiers et dossiers que vous souhaitez.</br>
   ![Capture d’écran des paramètres d’autorisation du lien Tout le monde au niveau de l’organisation dans SharePoint](media/sharepoint-organization-anyone-link-permissions.png)

Lorsque les liens *Tout le monde* sont paramétrés sur **Vue**, les utilisateurs peuvent encore partager des fichiers et des dossiers avec des invités et leur octroyer des autorisations de modification à l’aide des liens *Personnes spécifiques*. Ces liens nécessitent que les personnes extérieures à votre organisation s’authentifient en tant qu’invités. Vous pouvez effectuer le suivi et l’audit de l’activité des invités sur les fichiers et dossiers partagés avec ces liens.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Définir le type de lien par défaut de sorte qu’il fonctionne uniquement pour les membres de votre organisation

Lorsque le partage *Tout le monde* est activé pour votre organisation, le lien de partage par défaut est normalement réglé sur **Tout le monde**. Bien que cette fonctionnalité soit commode pour les utilisateurs, elle peut augmenter le risque d’un partage non authentifié involontaire. Si un utilisateur oublie de modifier le type de lien lors du partage d’un document sensible, il peut créer sans le vouloir un lien de partage qui ne nécessite pas d’authentification.

Vous pouvez réduire ce risque en modifiant le paramètre de lien par défaut en un lien qui fonctionne uniquement pour les personnes internes à votre organisation. Les utilisateurs qui souhaitent partager des documents avec des personnes non authentifiées doivent ensuite sélectionner cette option.

Pour définir le lien de partage de fichier et de dossier par défaut
1. Dans le centre d’administration SharePoint, dans le volet de gauche, cliquez sur **Partage**.
2. Sous **Liens de fichier et de dossier**, sélectionnez **Uniquement les membres de votre organisation**.</br>
   ![Capture d’écran du paramètre de type de lien par défaut de SharePoint](media/sharepoint-default-sharing-link-company-link.png)
3. Cliquez sur **Enregistrer**

## <a name="protect-against-malicious-files"></a>Se protéger contre les fichiers malveillants

Lorsque vous autorisez des utilisateurs anonymes à télécharger des fichiers, vous accroissez le risque de charger un fichier malveillant. Dans Microsoft 365, vous pouvez utiliser la fonctionnalité *pièces jointes fiables* dans la Protection avancée contre les menaces pour analyser automatiquement les fichiers téléchargés et mettre en quarantaine les fichiers jugés dangereux.

Pour activer les pièces jointes fiables
1. Ouvrez le centre d’administration de la [sécurité Microsoft 365](https://security.microsoft.com).
2. Dans la barre de navigation de gauche, cliquez sur **Stratégies**.
3. Sous **Protection contre les menaces**, cliquez sur **pièces jointes fiables ATP (Office 365)**.
4. Cochez la case **Activer ATP pour SharePoint, OneDrive et Microsoft Teams**, puis cliquez sur **Enregistrer**.</br>
   ![Capture d’écran du paramètre pièces jointes fiables dans le centre de sécurité et conformité](media/safe-attachments-setting.png)

## <a name="add-copyright-information-to-your-files"></a>Ajouter des informations de copyright à vos fichiers

Si vous utilisez des étiquettes de confidentialité dans le centre d’administration de la conformité Microsoft 365, vous pouvez configurer vos étiquettes pour ajouter automatiquement un filigrane, un en-tête ou un pied de page aux documents Office de votre organisation. De cette façon, vous pouvez vous assurer que les fichiers partagés contiennent des informations de copyright ou de propriété.

Pour ajouter un pied de page à un fichier étiqueté
1. Ouvrez le [centre d’administration de la conformité Microsoft 365](https://compliance.microsoft.com).
2. Dans le volet de navigation gauche, sous **Classification**, cliquez sur **Etiquettes de confidentialité**.
3. Cliquez sur l’étiquette à laquelle vous voulez ajouter un pied de page, puis sur **Modifier l'étiquette**.
4. Cliquez sur l’onglet **Marquage du contenu**, puis réglez l’option marquage du contenu sur **Activé**.
5. Cochez la case correspondant au type de texte à ajouter, puis cliquez sur **Personnaliser le texte**.
6. Tapez le texte que vous souhaitez ajouter à vos documents, sélectionnez les options de texte souhaitées, puis cliquez sur **Enregistrer**.</br>
   ![Capture d’écran des paramètres de marquage de contenu pour une étiquette de confidentialité](media/content-marking-for-anonymous-sharing.png)
7. Cliquez sur **Enregistrer**, puis sur **Fermer**.

Avec l’option marquage de contenu activée pour l’étiquette, le texte spécifié est ajouté aux documents Office lorsqu’un utilisateur applique cette étiquette.

## <a name="see-also"></a>Voir aussi


[Vue d’ensemble des étiquettes de confidentialité](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](sharing-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-a-secure-guest-sharing-environment.md)