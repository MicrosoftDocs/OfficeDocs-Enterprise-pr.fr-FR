---
title: Créer un extranet B2B avec des invités gérés
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: Découvrez comment créer un site extranet B2B ou une équipe avec des utilisateurs d’invités gérés à partir d’une organisation partenaire.
ms.openlocfilehash: cdf4470920a307d569fcfd650f40c77f4a5423a4
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549063"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Créer un extranet B2B avec des invités gérés

Vous pouvez utiliser la [gestion des droits Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) pour créer un extranet B2B afin de collaborer avec une organisation partenaire qui utilise Azure Active Directory. Cela permet aux utilisateurs de s’inscrire automatiquement sur le site extranet ou l’équipe et de recevoir un accès via un flux de travail d’approbation.

Avec cette méthode de partage des ressources pour la collaboration, l’organisation partenaire peut aider les utilisateurs invités à se terminer et à les approuver, en réduisant la charge de travail de votre service informatique et en permettant aux personnes les plus familières de l’accord de collaboration de gérer les utilisateurs. Access.

Cet article décrit les étapes à suivre pour créer un package de ressources (dans ce cas, un site ou une équipe) que vous pouvez partager avec une organisation partenaire par le biais d’un modèle d’enregistrement d’accès libre-service. 

Avant de commencer, créez le site ou l’équipe que vous souhaitez partager avec l’organisation partenaire et activez-le pour le partage d’invité. Pour plus d’informations, consultez la rubrique [collaborer avec des invités dans un site](collaborate-in-a-site.md) ou [collaborer avec des invités dans une équipe](collaborate-as-a-team.md) . Nous vous recommandons également de consulter la rubrique [Create a Secure Guest Sharing Environment](create-a-secure-guest-sharing-environment.md) pour obtenir des informations sur les fonctionnalités de sécurité et de conformité que vous pouvez utiliser pour gérer vos stratégies de gouvernance lors de la collaboration avec des invités.

## <a name="connect-the-partner-organization"></a>Connecter l’organisation partenaire

Pour inviter des invités à partir d’une organisation partenaire, vous devez ajouter le domaine du partenaire en tant qu’organisation connectée dans Azure Active Directory.

Pour ajouter une organisation connectée
1. Dans [Azure Active Directory](https://aad.portal.azure.com), cliquez sur **gouvernance des identités**.
2. Cliquez sur **organisations connectées**.
4. Cliquez sur **Ajouter une organisation connectée**.
5. Tapez un nom et une description pour l’organisation, puis cliquez sur **suivant : répertoire + domaine**.
6. Cliquez sur **Ajouter un répertoire + domaine**.
7. Tapez le domaine de l’organisation à laquelle vous souhaitez vous connecter, puis cliquez sur **Ajouter**.
8. Cliquez sur **se connecter**, puis sur **suivant : organisateurs**.
9. Ajoutez des personnes de votre organisation ou de l’organisation à laquelle vous vous connectez, auxquelles vous souhaitez approuver l’accès des utilisateurs invités.
10. Cliquez sur **suivant : examiner + créer**.
11. Passez en revue les paramètres que vous avez choisis, puis cliquez sur **créer**.

    ![Capture d’écran de la page organisations connectées dans Azure Active Directory](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Choisir les ressources à partager

La première étape de sélection des ressources à partager avec une organisation partenaire consiste à créer un catalogue pour les contenir.

Pour créer un catalogue
1. Dans [Azure Active Directory](https://aad.portal.azure.com), cliquez sur **gouvernance des identités**.
2. Cliquez sur **catalogues**.
3. Cliquez sur **nouveau catalogue**.
4. Tapez un nom et une description pour le catalogue et assurez-vous que **activé** et **activé pour les utilisateurs externes** sont définis sur **Oui**.
5. Cliquez sur **Créer**.

   ![Capture d’écran de la page de catalogues dans Azure Active Directory Identity Governance](media/identity-governance-catalogs.png)

Une fois le catalogue créé, vous ajoutez le site ou l’équipe SharePoint que vous souhaitez partager avec l’organisation partenaire.

Pour ajouter des ressources à un catalogue
1. Dans Azure AD Identity Government, cliquez sur **catalogues**, puis cliquez sur le catalogue dans lequel vous souhaitez ajouter des ressources.
2. Cliquez sur **ressources** , puis sur **Ajouter des ressources**.
3. Sélectionnez les équipes ou les sites SharePoint que vous souhaitez inclure dans votre extranet, puis cliquez sur **Ajouter**.

   ![Capture d’écran de la page de ressources de catalogue dans Azure Active Directory Identity Governance](media/identity-governance-catalog-resource.png)

Une fois que vous avez défini les ressources que vous souhaitez partager, l’étape suivante consiste à créer un package Access, qui définit le type d’accès accordé aux utilisateurs partenaires et le processus d’approbation des nouveaux utilisateurs partenaires qui demandent l’accès.

Pour créer un package Access
1. Dans Azure AD Identity Government, cliquez sur **catalogues**, puis cliquez sur le catalogue dans lequel vous souhaitez créer un package Access.
2. Cliquez sur **packages d’accès**, puis sur **nouveau package Access**.
3. Tapez un nom et une description pour le package d’accès, puis cliquez sur **suivant : rôles de ressource**.
4. Choisissez les ressources du catalogue que vous souhaitez utiliser pour votre extranet.
5. Pour chaque ressource, dans la colonne **rôle** , choisissez le rôle d’utilisateur que vous souhaitez accorder aux utilisateurs invités qui utilisent l’extranet.
6. Cliquez sur **suivant : demandes**.
7. Sous **utilisateurs pouvant demander l’accès**, choisissez **pour les utilisateurs qui ne se trouvent pas dans votre répertoire**.
8. Assurez-vous que l’option **organisations connectées spécifique** est sélectionnée, puis cliquez sur **Ajouter des répertoires**.
9. Choisissez l’organisation connectée que vous avez ajoutée précédemment, puis cliquez sur **Sélectionner** .
10. Sous **approbation**, sélectionnez **Oui** pour **demander une approbation**.
11. Sous **premier approbateur**, sélectionnez l’un des organisateurs ajoutés précédemment ou choisissez un utilisateur spécifique.
12. Cliquez sur **Ajouter un secours** et sélectionnez un approbateur de secours.
13. Sous **activer**, sélectionnez **Oui**.
14. Cliquez sur **suivant : cycle de vie**.
15. Choisissez les paramètres d’expiration et de révision d’accès que vous souhaitez utiliser, puis cliquez sur **suivant : examiner + créer**.
16. Vérifiez vos paramètres, puis cliquez sur **créer**.

    ![Capture d’écran de l’écran des packages d’accès dans Azure Active Directory Identity Governance](media/identity-governance-access-packages.png)

Si vous êtes un partenaire d’une grande organisation, vous souhaiterez peut-être masquer le package d’accès. Si le package est masqué, les utilisateurs de l’organisation partenaire ne verront pas le package sur leur portail d' *accès My* . Au lieu de cela, ils doivent recevoir un lien direct pour s’inscrire au package. Le fait de masquer le package Access peut réduire le nombre de demandes d’accès inappropriées et permettre de conserver les packages d’accès disponibles organisés sur le portail de l’organisation partenaire.

Pour définir le masquage d’un package Access
1. Dans Azure AD Identity Government, cliquez sur **packages d’accès**, puis sur votre package d’accès.
2. Sur la page **vue d’ensemble** , cliquez sur **modifier**.
3. Sous **Propriétés**, choisissez **Oui** pour **Masquer**, puis cliquez sur **Enregistrer**.

   ![Capture d’écran d’un écran modifier les propriétés du package d’accès](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Inviter des utilisateurs partenaires

Si vous définissez le package Access sur masqué, vous devez envoyer un lien direct à l’organisation partenaire afin qu’il puisse demander l’accès à votre site ou équipe.

Pour trouver le lien portail d’accès
1. Dans Azure AD Identity Government, cliquez sur **packages d’accès**, puis sur votre package d’accès.
2. Sur la page **vue d’ensemble** , cliquez sur **copier dans le presse-papiers** pour le **lien mon portail d’accès**.

   ![Capture d’écran des propriétés de package Access avec le lien du portail Access](media/identity-governance-access-portal-link.png)

Une fois que vous avez copié le lien, vous pouvez le partager avec votre contact auprès de l’organisation partenaire et l’envoyer aux utilisateurs de son équipe de collaboration.

## <a name="see-also"></a>Voir aussi

[Créer un environnement de partage sécurisé avec des invités](create-a-secure-guest-sharing-environment.md)

