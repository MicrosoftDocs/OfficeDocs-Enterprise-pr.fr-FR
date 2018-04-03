---
title: OneDrive pour la configuration des clients Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Apprenez à configurer les OneDrive d’entreprise Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive pour la configuration des clients Business Multi-Geo

Avant de configurer vos clients pour OneDrive pour entreprise Multi-Geo, veillez à ce que vous avez lu le [Plan pour OneDrive pour entreprise Multi-Geo](plan-for-multi-geo.md). Pour suivre les étapes décrites dans cet article, vous aurez besoin d’une liste des emplacements que vous souhaitez activer les utilisateurs de test que vous souhaitez configurer pour ces emplacements.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Ajouter les fonctionnalités Multi-Geo dans Office 365 plan pour vos clients

Pour utiliser OneDrive pour entreprise Multi-Geo, vous devez le plan de _Capacités Multi-Geo dans Office 365_ . Travailler avec votre équipe de compte à ajouter ce plan pour vos clients. Votre équipe de compte va vous connecter avec le spécialiste de la licence approprié et obtenir vos clients configurés.

Notez que le plan _Des fonctionnalités dans Office 365 Multi-Geo_ est un plan de service au niveau de l’utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement de setellite. Vous pouvez ajouter davantage de licences lorsque vous ajoutez des utilisateurs dans des emplacements de satellite au fil du temps.

Une fois que votre client a été configuré avec le plan de _Capacités Multi-Geo dans Office 365_ , l’onglet **emplacements de la zone géographique** devient disponible dans le [Centre d’administration OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Définir les emplacements de données autorisé (ADL) à vos clients

Vous devez définir un emplacement de données autorisées pour SharePoint pour chaque emplacement géographique où vous souhaitez utiliser OneDrive pour les entreprises. Geo-emplacements disponibles sont affichés dans le tableau suivant :

<table>
<thead>
<tr class="header">
<th align="left"><strong>Emplacement</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Amérique du Nord</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Europe / Moyen-Orient / Afrique</td>
<td align="left">EUROS</td>
</tr>
<tr class="odd">
<td align="left">Asie-Pacifique</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australie</td>
<td align="left">AUSTRALIE</td>
</tr>
<tr class="odd">
<td align="left">Japon</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Canada</td>
<td align="left">POUVEZ</td>
</tr>
<tr class="odd">
<td align="left">Royaume-Uni</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Corée</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

Pour ajouter un emplacement géographique de satellite

1. Ouvrir le [Centre d’administration OneDrive](https://admin.onedrive.com).

2. Accédez à l’onglet **emplacements de la zone géographique** .

3. Cliquez sur **Ajouter un emplacement**.

4. Sélectionnez l’emplacement où vous souhaitez ajouter, puis cliquez sur **suivant**.

5. Tapez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.

6. Cliquez sur **Fermer**.

Une fois la mise en service d’un emplacement de satellite est terminée, vous recevrez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte dans l’onglet **emplacements de la zone géographique** dans le centre d’administration OneDrive, vous pourrez définir l’emplacement de données par défaut des utilisateurs à cet emplacement-geo. 

> [!IMPORTANT]
> Votre nouvel emplacement géographique de satellites est établi avec les paramètres par défaut. Cela vous permettra de configurer cet emplacement géographique en fonction de vos besoins de conformité locale.

## <a name="setting-users-preferred-data-location"></a>Définition de l’emplacement par défaut des données utilisateurs
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Une fois que vous activez les emplacements de données nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données approprié. Nous vous conseillons de définir un emplacement de données par défaut pour tous les utilisateurs, même si cet utilisateur séjourne dans l’emplacement de données par défaut.

> [!TIP]
> Nous vous conseillons de commencer les validations avec un petit groupe d’utilisateurs ou un utilisateur de test avant de déployer les fonctionnalités Multi-Geo à votre organisation plus large.

Dans DAS, il existe deux types d’objets de l’utilisateur : cloud uniquement aux utilisateurs et synchronisé. Suivez les instructions correspondant à votre type d’utilisateur.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide de la connexion d’Active Directory 

Si les utilisateurs de votre entreprise sont synchronisées à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), leur PreferredDataLocation doit être remplie dans Active Directory et synchronisée avec DAS. Suivez le processus de [Azure Connect de AD sync : apporter une modification à la configuration par défaut](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) pour configurer par défaut synchronisation de l’emplacement des données de sur site AD pour le DAS.

Nous vous conseillons d’inclure définissant l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs avec aucun OneDrive mis en service, attendez au moins 24 heures après que le langage PDL d’un utilisateur est synchronisé avec DAS pour que les modifications de se propager avant que l’utilisateur se connecte à OneDrive pour les entreprises. (Définition des données par défaut emplacement avant que l’utilisateur se connecte à provisionner leur OneDrive pour les entreprises ainsi que OneDrive de nouveau l’utilisateur sera déployé dans l’emplacement correct).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Définition de l’emplacement de données par défaut pour le cloud uniquement les utilisateurs 

Si les utilisateurs de votre société ne sont pas synchronisés à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), c'est-à-dire qu’ils sont créés dans Office 365 ou DAS, puis PDL doit être défini à l’aide de PowerShell de DAS.

Les procédures de cette section nécessitent le [Microsoft Azure Active Directory pour Windows PowerShell un Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si vous avez déjà PowerShell DAS installé, vérifiez que vous mettez à jour vers la dernière version.

1.  Ouvrez le Module de Active Directory de Microsoft Azure pour Windows PowerShell.

2.  Exécutez `Connect-MsolService` et entrez les informations d’identification de l’administrateur global pour vos clients.

3.  L’applet de commande [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) permet de définir l’emplacement de données par défaut pour chacun de vos utilisateurs. Par exemple :

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Vous pouvez vérifier pour vous assurer que l’emplacement par défaut des données a été correctement mis à jour à l’aide de l’applet de commande Get-MsolUser. Par exemple :

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

Nous vous conseillons d’inclure définissant l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs avec aucun OneDrive mis en service, attendez au moins 24 heures après que PDL l’utilisateur est défini pour que les modifications de se propager avant que l’utilisateur se connecte à SharePoint OneDrive. (Définition des données par défaut emplacement avant que l’utilisateur se connecte à provisionner leur OneDrive pour les entreprises ainsi que OneDrive de nouveau l’utilisateur sera déployé dans l’emplacement correct).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Mise en service de la OneDrive et l’effet du langage PDL

Si l’utilisateur possède déjà un site de OneDrive créé sur le client, définissant leur PDL pas déplace automatiquement leur OneDrive existant. Pour déplacer les OneDrive d’un utilisateur, consultez [OneDrive pour déplacer de Business géo](move-onedrive-between-geo-locations.md) , suivez les instructions de OneDrive de déplacement entre les emplacements de la zone géographique.

Si l’utilisateur n’a pas un site de OneDrive dans le locataire, OneDrive sera déployé pour eux conformément à leur valeur PDL, en supposant le langage PDL pour l’utilisateur correspond à un des emplacements de données autorisé de la société (ADLs).

## <a name="configuring-multi-geo-search"></a>Configuration de la recherche de Multi-Geo

Vos clients Multi-Geo aient des fonctions de recherche d’agrégation permettant à une requête de recherche pour retourner les résultats de n’importe où dans le locataire.

Par défaut, les recherches à partir de ces points d’entrée renvoie des résultats de regroupement, même si chaque index de recherche se trouve dans son emplacement géographique appropriée :

- OneDrive pour les entreprises

- Delve

- Accueil SharePoint

- Centre de recherche

En outre, les fonctionnalités de recherche Multi-Geo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent le API de recherche de SharePoint.

Consultez [Configurer la recherche de OneDrive de professionnels Multi-Geo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris les limitations et les différences.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validation de l’OneDrive pour la configuration de Business Multi-Geo

Vous trouverez ci-dessous quelques exemples d’utilisation de base que vous voudrez peut-être inclure dans votre plan de validation avant le large déploiement OneDrive pour entreprise Multi-Geo à votre société. Une fois que vous avez terminé ces tests et les cas d’usage supplémentaires qui sont pertinentes pour votre société, vous pouvez choisir passer à l’ajout d’utilisateurs dans votre groupe pilote initial.

**OneDrive pour les entreprises**

Sélectionnez OneDrive à partir du Lanceur d’applications Office 365 et de confirmer que vous êtes automatiquement redirigé vers l’emplacement approprié du géographique de l’utilisateur, en fonction de PDL l’utilisateur. OneDrive pour l’entreprise doit maintenant commencer la mise en service à cet emplacement. Essayez une fois configuré, de transfert et le téléchargement de certains documents.

**Application de OneDrive Mobile**

Ouvrez une session dans votre application mobile de OneDrive avec vos informations d’identification du compte de test. Vérifiez que vous pouvez voir votre OneDrive pour les fichiers de l’entreprise et pouvez interagir avec eux à partir de votre appareil mobile.

**Client de synchronisation OneDrive**

Vérifiez que le client de synchronisation OneDrive détecte automatiquement votre OneDrive de géolocalisation métier lors de la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **synchroniser** dans la bibliothèque OneDrive.

**Applications Office**

Vérifiez que vous pouvez accéder à OneDrive pour l’entreprise en vous connectant à partir d’une application Office, tels que Word. Ouvrir l’Office application et sélectionnez « OneDrive – <TenantName>». Office détecte votre emplacement de OneDrive et vous montrer que vous pouvez ouvrir les fichiers.

**Sharing**

Essayez de partager des fichiers de OneDrive. Vérifiez que le sélecteur de personnes contient tous vos utilisateurs d’en ligne SharePoint, quel que soit leur emplacement géographique.
