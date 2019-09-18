---
title: Collaborer avec des invités dans un site
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Découvrez comment collaborer avec des invités sur un site SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017312"
---
# <a name="collaborate-with-guests-in-a-site"></a>Collaborer avec des invités dans un site

Si vous avez besoin de collaborer avec des invités dans des documents, des données et des listes, vous pouvez utiliser un site SharePoint. Les sites SharePoint modernes sont connectés aux groupes Office 365 qui peuvent gérer l’appartenance à un site et fournir des outils de collaboration supplémentaires tels qu’une boîte aux lettres et un calendrier partagés.

Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer un site SharePoint en vue de la collaboration avec des invités.

## <a name="azure-organizational-relationships-settings"></a>Paramètres Azure de relations organisationnelles

Le partage dans Microsoft 365 est régi par les paramètres de relations organisationnelles dans Azure Active Directory. Si le partage d’invités est désactivé ou restreint dans Azure AD, cela remplace tous les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de relations organisationnelles pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran de la page des paramètres des relations organisationnelles Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de relation organisationnelle

1. Connectez-vous à Microsoft Azure [https://portal.azure.com](https://portal.azure.com)à l’adresse.
2. Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.
3. Dans le volet de **vue d’ensemble** , cliquez sur **relations organisationnelles**.
4. Dans le volet **relations organisationnelles** , cliquez sur **paramètres**.
5. Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.
6. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **restrictions de collaboration** . Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.

## <a name="office-365-groups-guest-settings"></a>Les paramètres invités des groupes Office 365

Les sites SharePoint modernes utilisent les groupes Office 365 pour contrôler l’accès au site. Les paramètres invités des groupes Office 365 doivent être activés pour que l’accès invité dans les sites SharePoint fonctionne.

![Capture d’écran des paramètres invités des groupes Office 365 dans le centre d’administration Microsoft 365](media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Office 365

1. Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.
2. Cliquez sur **Services & compléments**.
3. Dans la liste, cliquez sur **groupes Office 365**.
4. Assurez-vous que les **membres de groupe Let en dehors de votre organisation accèdent au contenu de groupe** et que les **propriétaires de groupes ajoutent des personnes en dehors de votre organisation aux** cases à cocher sont activées.
5. Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage au niveau de l’organisation SharePoint

Pour que les invités aient accès aux sites SharePoint, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour des sites individuels. Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.

Si vous souhaitez autoriser le partage de fichiers et de dossiers avec des utilisateurs anonymes, sélectionnez **tout le monde**. Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **nouveau et invités existants**. Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.

![Capture d’écran des paramètres de partage au niveau de l’organisation SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage au niveau de l’organisation SharePoint

1. Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.
2. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, cliquez sur **partage**.
3. Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
4. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-site"></a>Créer un site

L’étape suivante consiste à créer le site que vous envisagez d’utiliser pour collaborer avec des invités.

Pour créer un site
1. Dans le centre d’administration SharePoint, sous **sites**, cliquez sur **sites actifs**.
2. Cliquez sur **Créer**.
3. Cliquez sur **site d’équipe**.
4. Tapez un nom de site et entrez un nom pour le propriétaire du groupe (propriétaire du site).
5. Sous **Paramètres avancés**, choisissez si vous souhaitez qu’il s’agit d’un site public ou privé.
6. Cliquez sur **Suivant**.
7. Cliquez sur **Terminer**.

Nous allons inviter les utilisateurs ultérieurement. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour ce site.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de partage au niveau du site SharePoint

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès souhaité pour ce site. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs**, mais que vous souhaitez que tous les invités s’authentifient pour ce site, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.

Notez que le site ne peut pas être partagé avec des utilisateurs anonymes (paramètre**tout le monde** ), mais avec des fichiers et des dossiers individuels.

![Capture d’écran des paramètres de partage externe du site SharePoint](media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres de partage au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **sites** , puis cliquez sur **sites actifs**.
2. Sélectionnez le site que vous venez de créer.
3. Dans le ruban, cliquez sur **partage**.
4. Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
5. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre site. L’accès au site est contrôlé par le biais du groupe Office 365 associé, c’est pourquoi nous allons y ajouter des utilisateurs.

Pour inviter des utilisateurs internes à un groupe
1. Accédez au site où vous souhaitez ajouter des utilisateurs.
2. Cliquez sur **membres** dans le coin supérieur droit.
3. Cliquez sur **Ajouter des membres**.
4. Tapez les noms ou les adresses de messagerie des utilisateurs que vous souhaitez inviter sur le site, puis cliquez sur **Enregistrer**.

Les utilisateurs invités ne peuvent pas être ajoutés à partir du site. Vous devez les ajouter à l’aide d’Outlook sur le Web.

Pour inviter des invités à un site
1. Dans Outlook sur le Web, sous **groupes**, cliquez sur le groupe dans lequel vous souhaitez ajouter des membres.
2. Ouvrez la carte de visite de groupe, puis, sous **autres options** (...), cliquez sur **Ajouter des membres**.
3. Tapez les adresses de messagerie des invités que vous souhaitez inviter, puis cliquez sur **Ajouter**.
4. Cliquez sur **Fermer**.

## <a name="see-also"></a>Voir aussi
