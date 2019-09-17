---
title: Collaborer avec des invités sur un document
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Découvrez comment collaborer avec des invités sur un document dans SharePoint et OneDrive.
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992403"
---
# <a name="collaborate-with-guests-on-a-document"></a>Collaborer avec des invités sur un document

Si vous avez besoin de collaborer avec des invités sur des documents dans SharePoint ou OneDrive, vous pouvez leur envoyer un lien de partage vers le document. Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 requises pour configurer des liens de partage pour SharePoint et OneDrive.

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

## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage au niveau de l’organisation SharePoint

Pour que les invités aient accès à un document dans SharePoint ou OneDrive, les paramètres de partage au niveau de l’organisation OneDrive et SharePoint doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’Organisation pour SharePoint déterminent les paramètres disponibles pour les sites SharePoint individuels. Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation. Le paramètre au niveau de l’Organisation pour OneDrive détermine quel niveau de partage est disponible dans les bibliothèques OneDrive des utilisateurs.

Pour SharePiont et OneDrive, si vous voulez autoriser le partage de fichiers et de dossiers avec des utilisateurs anonymes, sélectionnez **tout le monde**. Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **nouveau et invités existants**. 

Pour SharePoint, choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.

![Capture d’écran des paramètres de partage au niveau de l’organisation SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage au niveau de l’organisation SharePoint

1. Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.
2. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, cliquez sur **partage**.
3. Assurez-vous que le partage externe pour SharePoint ou OneDrive est défini sur **tout le monde** ou sur **des invités nouveaux et existants**. (Notez que le paramètre OneDrive ne peut pas être plus permissif que le paramètre SharePoint.)
4. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

## <a name="sharepoint-organization-level-default-link-settings"></a>Paramètres de lien par défaut au niveau de l’organisation SharePoint

Les paramètres de lien de fichier et de dossier par défaut déterminent l’option de lien qui est présentée par défaut à l’utilisateur lorsqu’il partage un fichier ou un dossier. Les utilisateurs peuvent remplacer le type de lien par l’une des autres options avant de procéder au partage si vous le souhaitez.

N’oubliez pas que ce paramètre affecte les sites SharePoint de votre organisation, ainsi que OneDrive.

Choisissez le type de lien sélectionné par défaut lorsque les utilisateurs partagent des fichiers et des dossiers :

- **Toute personne disposant du lien** : choisissez cette option si vous envisagez de partager un grand nombre de fichiers et de dossiers avec des utilisateurs anonymes. Si vous souhaitez autoriser les liens de *tous les utilisateurs* mais s’inquiète du partage anonyme accidentel, envisagez l’une des autres options par défaut. Ce type de lien n’est disponible que si vous avez activé le partage d’un **utilisateur** .
- **Uniquement les personnes de votre organisation** : choisissez cette option si vous pensez que le partage de fichiers et de dossiers doit être associé à des personnes au sein de votre organisation.
- **Personnes spécifiques** : envisagez cette option si vous envisagez de faire beaucoup de partage de fichiers et de dossiers avec des invités. Ce type de lien fonctionne avec les invités et les requiert pour s’authentifier.
 
![Capture d’écran des paramètres de partage de fichiers et de dossiers au niveau de l’organisation SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


Pour définir les paramètres de lien par défaut de l’organisation OneDrive et SharePoint

1. Accédez à la page de partage dans le centre d’administration SharePoint.
2. Sous **liens de fichiers et de dossiers**, sélectionnez le lien de partage par défaut à utiliser.
3. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de partage au niveau du site SharePoint

Si vous partagez des fichiers et des fodlers qui se trouvent dans un site SharePoint, vous devez également vérifier les paramètres de partage au niveau du site pour ce site.

![Capture d’écran des paramètres de partage externe du site SharePoint](media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres de partage au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **sites** , puis cliquez sur **sites actifs**.
2. Sélectionnez le site que vous venez de créer.
3. Dans le ruban, cliquez sur **partage**.
4. Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
5. Si vous avez apporté des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage des invités sont désormais configurés, de sorte que les utilisateurs peuvent désormais partager des fichiers et des dossiers avec des invités. Pour plus d’informations, voir [partager des fichiers et des dossiers OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) et [partager des fichiers ou des dossiers SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) .

## <a name="see-also"></a>Voir aussi
