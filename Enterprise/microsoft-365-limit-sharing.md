---
title: Limiter le partage dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
search.appverid:
- SPO160
- MET150
f1.keywords: NOCSH
ms.custom: ''
localization_priority: Priority
description: Découvrez les options pour limiter ou désactiver le partage dans Microsoft 365.
ms.openlocfilehash: 37adff58949f1970b0b8cba4a5b3d9a7fa01e5f9
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549143"
---
# <a name="limit-sharing-in-microsoft-365"></a>Limiter le partage dans Microsoft 365

Bien que vous ne puissiez pas désactiver le partage interne complètement ou supprimer le bouton partager des sites, vous pouvez limiter le partage dans Microsoft 365 pour répondre aux besoins de votre organisation.

Les méthodes de partage de fichiers sont répertoriées dans le tableau ci-dessous. Cliquez sur le lien dans la colonne **Méthode de partage** pour obtenir des informations détaillées.

|Méthode de partage|Description|Limiter les options|
|:-------------|:----------|:-------------|
|[Un groupe ou une équipe Office 365](#office-365-group-or-team)|Les personnes disposant d’un accès à une équipe Microsoft Teams ou à un groupe Office 365 disposent d’un accès en modification aux fichiers du site SharePoint associé.|Si le groupe ou l’équipe est privé, les invitations de partage à rejoindre l’équipe accèdent au propriétaire pour approbation. Les administrateurs peuvent désactiver l'accès invité pour empêcher l'accès par des personnes extérieures à l'organisation.
|
|[Site SharePoint](#sharepoint-site)|Les utilisateurs peuvent bénéficier d'un accès Propriétaire, Membre ou Visiteur à un site SharePoint et auront ce niveau d'accès aux fichiers du site.|Les autorisations de site peuvent être limitées de sorte que seuls les propriétaires de site puissent partager le site.|
|[Partager avec des personnes spécifiques](#sharing-with-specific-people)|Les membres du site et les personnes disposant des autorisations de modification peuvent octroyer des autorisations directes aux fichiers et dossiers, ou les partager en utilisant *des personnes spécifiques* des liens.|Les autorisations de site peuvent être limitées de sorte que seuls les propriétaires de site puissent partager les fichiers et les dossiers. Dans ce cas, l’accès direct et le partage de liens *des personnes spécifiques* par les membres du site est transmis au propriétaire du site pour approbation.|
|[Partage d’invités SharePoint](#sharepoint-guest-sharing)|Les propriétaires et les membres du site SharePoint peuvent partager des fichiers et des dossiers avec des personnes extérieures à l’organisation.|Le partage d’invités peut être désactivé pour l’ensemble de l’organisation ou des sites individuels.|
|[*Membres de votre organisation* partage de liens](#people-in-your-organization-sharing-links)|Les propriétaires et les membres du site SharePoint peuvent partager des fichiers à l’aide des liens des *membres de votre organisation*, ce qui peut fonctionner pour toute personne au sein de l’organisation.|Les liens *des membres de votre organisation* peuvent être désactivés au niveau du site.|
|[Courrier électronique](#email)|Les personnes ayant accès à un fichier peuvent l'envoyer à d'autres par e-mail.|Les administrateurs peuvent crypter des fichiers en utilisant des étiquettes de sensibilité pour éviter qu'ils ne soient partagés avec des personnes non autorisées.|
|[Télécharger ou copier le dossier](#download-or-file-copy)|Les personnes qui ont accès à un fichier peuvent télécharger ou copier celle-ci et la partager avec d’autres personnes en dehors de l’étendue de Microsoft 365.|Les administrateurs peuvent crypter des fichiers en utilisant des étiquettes de sensibilité pour éviter qu'ils ne soient partagés avec des personnes non autorisées.|

Bien que vous puissiez utiliser les contrôles d’administration décrits dans cet article pour limiter le partage au sein de votre organisation, nous vous recommandons vivement d’utiliser les fonctionnalités de sécurité et de conformité disponibles dans Microsoft 365 pour créer un environnement de partage sécurisé. Consultez [la collaboration de fichiers dans SharePoint avec Microsoft 365](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) et [Teams pour les informations hautement réglementées](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)pour plus d’informations.

Pour comprendre comment le partage est utilisé au sein de votre organisation, [exécuter un rapport sur le partage de fichiers et de dossiers](https://docs.microsoft.com/sharepoint/sharing-reports).

## <a name="office-365-group-or-team"></a>Un groupe ou une équipe Office 365

Si vous voulez limiter le partage dans un groupe Office 365 ou une équipe Microsoft Teams, il est important de rendre le groupe ou l’équipe privé. Les membres de votre organisation peuvent rejoindre un groupe public ou une équipe à tout moment. À moins que le groupe ou l’équipe ne soit privé, vous ne pouvez pas limiter le partage de l’équipe ou de ses fichiers au sein de l’organisation.

### <a name="guest-sharing"></a>Partage d’invités

Si vous voulez empêcher l’accès invité dans Teams, vous pouvez désactiver le partage d’invités dans le centre d’administration Teams.

Pour désactiver le partage d’invités pour les Teams
1. Dans le centre d’administration Teams, développez les**Paramètres à l’échelle de l’organisation**, puis cliquez sur **accès invité**.
2. Désactivez **Autoriser l’accès invité dans Teams**.
3. Cliquez sur **Enregistrer**.

Si vous voulez empêcher l’accès invité dans les groupes Office 365, vous pouvez désactiver les paramètres d’accès invité des groupes dans le Centre d’administration Microsoft 365.

Pour désactiver le partage d’invités pour les groupes Office 365
1. Dans le Centre d’administration Microsoft 365, cliquez sur **Paramètres**, puis sur **Paramètres**.
2. Sous l’onglet **services**, cliquez sur **Groupes Office 365**.
3. Désactivez les cases à cocher **Permettre aux membres du groupe à l’extérieur de votre organisation à accéder au contenu de groupe** et **Permettre aux propriétaires de groupe d’ajouter des personnes extérieures à votre organisation à des groupes**.
4. Cliquez sur **Enregistrer les modifications**.

    ![Capture d’écran des paramètres de partage de groupes Office 365 dans le Centre d’administration Microsoft 365](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> Si vous voulez empêcher le partage d’invités pour un groupe ou une équipe spécifique, vous pouvez le faire à l’aide de Microsoft PowerShell. Consultez [Bloquer les utilisateurs invités d’un groupe spécifique](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group) pour les détails.

Vous pouvez limiter le partage d’invités aux utilisateurs de domaines spécifiques en autorisant ou en bloquant les domaines dans Azure Active Directory. Cela affecte également le partage d’invités dans SharePoint si vous avez activé [SharePoint et l’intégration de OneDrive à l’aide d’Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).

Pour autoriser uniquement les invitations de partage à partir de domaines spécifiés
1. Dans Azure Active Directory, dans la page vue d’ensemble, cliquez sur **relations organisationnelles**.
2. Cliquez sur **Paramètres**.
3. Sous **Restrictions de collaboration**, sélectionnez **Refuser les invitations aux domaines spécifiés** ou **Autoriser les invitations uniquement aux domaines spécifiés**, puis tapez les domaines que vous voulez utiliser.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres de restrictions de collaboration dans Azure Active Directory](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>Site SharePoint

Vous pouvez limiter le partage de sites SharePoint uniquement aux propriétaires de sites. Cela empêche les membres du site de partager le site. Rappelez-vous que si le site est connecté à un groupe Office 365, les membres du groupe peuvent inviter d’autres personnes au groupe et ces utilisateurs pourront accéder au site.

Pour limiter le partage de sites aux propriétaires
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Sélectionnez les**Propriétaires et membres du site, et les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’autorisations de partage dans un site SharePoint](media/sharepoint-site-sharing-permissions-level-two.png)

Vous pouvez empêcher les utilisateurs qui ne sont pas membres du site de demander l’accès en désactivant les demandes d’accès.

Pour désactiver les demandes d’accès
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Désactivez **Autoriser les demandes d’accès**, puis cliquez sur **Enregistrer**.

Vous pouvez limiter le partage de sites à des domaines spécifiques en autorisant ou en bloquant les domaines pour le site.

Pour limiter le partage de sites par domaine
1. Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.
2. Cliquez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Paramètres avancés pour le partage externe**, cochez la case **Limiter le partage externe par domaine**.
5. Ajoutez les domaines que vous voulez autoriser ou bloquer, puis cliquez sur **Enregistrer**.
6. Cliquez sur **Enregistrer**.

    ![Capture d’écran des domaines autorisés-paramètre au niveau du site](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a>Partager avec des personnes spécifiques

Si vous voulez limiter le partage d’un site ou de son contenu, vous pouvez configurer le site pour autoriser uniquement les propriétaires de site à partager des fichiers, des dossiers et le site. Lorsque cette option est configurée, les membres du site tentent de partager des fichiers ou des dossiers à l’aide des liens *Personnes spécifiques* sont dirigés vers le propriétaire du site pour approbation.

Pour limiter le partage du site, des fichiers et des dossiers aux propriétaires
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Sélectionnez **Seuls les propriétaires de site peuvent partager des fichiers, des dossiers et le site**.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’autorisations de partage dans un site SharePoint](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>Partage d’invités SharePoint

Si vous voulez empêcher le partage de fichiers et de dossiers SharePoint ou OneDrive avec des personnes externes à votre organisation, vous pouvez désactiver le partage d’invités pour l’ensemble de l’organisation ou pour un site individuel.

Pour désactiver le partage d’invités SharePoint pour votre organisation
1. Dans le Centre d’administration SharePoint, sous **Stratégies**, cliquez sur **Partage**.
2. Sous **Partage externe**, faites glisser le curseur SharePoint vers le **Uniquement les membres de votre organisation.**.
3. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](media/sharepoint-tenant-sharing-off.png)


Pour désactiver le partage d’invités pour un site
1. Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.
2. Cliquez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Partage externe**, sélectionnez **Uniquement les membres de votre organisation**, puis cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres de SharePoint au niveau du site](media/sharepoint-site-external-sharing-settings-off.png)

Si vous voulez autoriser le partage avec des personnes externes à votre organisation, mais que vous voulez vous assurer que tout le monde s’authentifie, vous pouvez désactiver les liens *Tout le monde* (partage anonyme) pour l’ensemble de l’organisation ou pour un site individuel.

Pour désactiver les liens *Tout le monde* au niveau de l’organisation
1. Dans le Centre d’administration SharePoint, sous **Stratégies**, cliquez sur **Partage**.
2. Sous **Partage externe**, faites glisser le curseur SharePoint vers le **Invités nouveaux et existants**.
3. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres de SharePoint au niveau du site](media/sharepoint-guest-sharing-new-and-existing-guests.png)

Pour désactiver les liens *Tout le monde* d’un site
1. Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.
2. Cliquez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Partage externe**, choisissez **Invités nouveaux et existants**, puis cliquez **Enregistrer**.

    ![Capture d’écran des paramètres de SharePoint au niveau du site](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*Membres de votre organisation* partage de liens

Par défaut, les membres d’un site peuvent partager des fichiers et des dossiers avec d’autres membres de votre organisation à l’aide d’un lien*Membres de votre organisation *. Vous pouvez désactiver les liens *Membres de votre organisation* à l’aide de PowerShell :

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

Par exemple :

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a>E-mail

Vous pouvez empêcher le partage indésirable de messages électroniques à l’aide du chiffrement. Cela empêche les messages électroniques transférés ou partagés avec d’autres utilisateurs non autorisés. Le chiffrement de courrier peut être activé à l’aide d’étiquettes de confidentialité. Consultez [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) pour les détails.

## <a name="download-or-file-copy"></a>Télécharger ou copier le dossier

Les utilisateurs qui ont accès à des fichiers et des dossiers dans Microsoft 365 peuvent télécharger et copier des fichiers sur un support externe. Pour réduire le risque de partage de fichiers indésirables, vous pouvez chiffrer le contenu à l’aide d’étiquettes de confidentialité.

## <a name="see-also"></a>Voir aussi

[Références sur les paramètres de partage d’invités de Microsoft 365](microsoft-365-guest-settings.md)
