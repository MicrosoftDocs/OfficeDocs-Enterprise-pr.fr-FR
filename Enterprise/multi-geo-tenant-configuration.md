---
title: Configuration du client OneDrive Entreprise Multi-Géo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Découvrez comment configurer OneDrive Entreprise Multi-Géo.
ms.openlocfilehash: 6c4a1012f3f26265ef88d82c55bb3ac11cc82da4
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849870"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Configuration du client OneDrive Entreprise Multi-Géo

Avant de configurer votre client OneDrive Entreprise Multi-Géo, reportez-vous à l’article relatif à la [planification de OneDrive Entreprise Multi-Géo](plan-for-multi-geo.md). Pour suivre la procédure décrite dans cet article, vous devez disposer de la liste des emplacements géographiques que vous souhaitez activer en tant qu’emplacements satellites et des utilisateurs test que vous souhaitez configurer pour ces emplacements.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Ajouter les fonctionnalités multigéographiques du plan Office 365 à votre client

Pour utiliser OneDrive Entreprise Multi-Géo, vous devez disposer du plan des _fonctionnalités multigéographiques dans Office 365_. Collaborez avec votre équipe de compte pour ajouter ce plan à votre client. Votre équipe de compte vous connectera avec le spécialiste de la licence approprié et configurera votre client.

Notez que le plan des _fonctionnalités multigéographiques dans Office 365_ est un plan de service au niveau utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement satellite. Vous pouvez ajouter des licences supplémentaires au fur et à mesure que vous ajoutez des utilisateurs dans des emplacements satellites.

Une fois que votre client a été configuré avec le plan des _fonctionnalités multigéographiques dans Office 365_, l’onglet **Emplacements géographiques** devient disponible dans le [centre d’administration OneDrive](https://admin.onedrive.com).

## <a name="add-satellite-locations-to-your-tenant"></a>Ajouter des emplacements satellites à votre client

Vous devez ajouter un emplacement satellite pour chaque emplacement géographique où vous souhaitez utiliser OneDrive Entreprise. Les emplacements géographiques disponibles sont affichés dans le tableau suivant :

<table>
<thead>
<tr class="header">
<th align="left"><strong>Emplacement</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asie-Pacifique</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australie</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">Canada</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europe / Moyen-Orient / Afrique</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">France</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">Japon</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Corée</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Amérique du Nord</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">Royaume-Uni</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Pour ajouter un emplacement satellite, procédez comme suit :

1. Ouvrez le [centre d’administration OneDrive](https://admin.onedrive.com).

2. Accédez à l’onglet **Emplacements géographiques**.

3. Cliquez sur **Ajouter un emplacement**.

4. Sélectionnez l’emplacement à ajouter, puis cliquez sur **Suivant**.

5. Saisissez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.

6. Cliquez sur **Fermer**.

La configuration peut prendre jusqu’à 72 heures selon la taille de votre client. Une fois que la configuration d’un emplacement satellite est terminée, vous recevrez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte sur l’onglet **Emplacements géographiques** dans le centre d’administration OneDrive, vous pouvez définir l’emplacement des données par défaut des utilisateurs sur cet emplacement géographique. 

> [!IMPORTANT]
> Votre nouvel emplacement satellite est configuré avec des paramètres par défaut. Cela vous permettra de configurer cet emplacement satellite en fonction de vos besoins de conformité locale.

## <a name="setting-users-preferred-data-location"></a>Définition de l’emplacement des données par défaut des utilisateurs
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Lorsque vous activez les emplacements satellites nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données par défaut approprié. Nous vous recommandons de définir un emplacement de données par défaut pour chaque utilisateur, même si cet utilisateur reste dans l’emplacement central.

> [!TIP]
> Nous vous recommandons de commencer les validations avec un utilisateur test ou un petit groupe d’utilisateurs avant de déployer Multi-Géo sur votre organisation à plus grande échelle.

Dans AAD, il existe deux types d’objets utilisateur : les utilisateurs cloud uniquement et les utilisateurs synchronisés. Suivez les instructions correspondant à votre type d’utilisateur.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide d’AD Connect 

Si les utilisateurs de votre entreprise sont synchronisés à partir d’un système Active Directory local avec Azure Active Directory, leur PreferredDataLocation doit être renseigné dans AD et synchronisé avec AAD. Suivez le processus décrit dans l’article [Synchronisation Azure AD Connect : modifier la configuration par défaut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) pour configurer la synchronisation de l’emplacement des données par défaut à partir d’Active Directory local avec Azure Active Directory.

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs sans OneDrive configuré, patientez au moins 24 heures après la synchronisation de l’emplacement des données par défaut d’un utilisateur avec Azure Active Directory pour que les modifications se propagent avant que l’utilisateur se connecte à OneDrive Entreprise. (La définition de l’emplacement des données par défaut avant la connexion de l’utilisateur pour configurer OneDrive Entreprise garantit que le nouveau OneDrive sera configuré à l’emplacement approprié.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Définition de l’emplacement des données par défaut pour les utilisateurs cloud uniquement 

Si les utilisateurs de votre entreprise ne sont pas synchronisés à partir d’un système Active Directory local avec Azure Active Directory, ce qui signifie qu’ils sont créés dans Office 365 ou Azure Active Directory, l’emplacement des données par défaut doit être défini à l’aide d’Azure Active Directory pour PowerShell.

Les procédures décrites dans cette section nécessitent le [module Microsoft Azure Active Directory Module pour Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si vous avez déjà installé Azure Active Directory pour PowerShell, vérifiez que vous effectuez la mise à jour vers la dernière version.

1.  Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2.  Exécutez `Connect-MsolService` et entrez les informations d’identification d’administrateur général pour votre client.

3.  Utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) pour définir l’emplacement des données par défaut pour chacun de vos utilisateurs. Par exemple :

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Vous pouvez vérifier pour confirmer que l’emplacement des données par défaut a été correctement mis à jour à l’aide de la cmdlet Get-MsolUser. Par exemple :

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs sans OneDrive configuré, patientez au moins 24 heures après la définition de l’emplacement des données par défaut d’un utilisateur pour que les modifications se propagent avant que l’utilisateur se connecte à OneDrive. (La définition de l’emplacement des données par défaut avant la connexion de l’utilisateur pour configurer OneDrive Entreprise garantit que le nouveau OneDrive sera configuré à l’emplacement approprié.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Configuration de OneDrive et l’effet de PDL

Si l’utilisateur possède déjà un site OneDrive créé dans le client, la définition de son PDL ne déplacera pas automatiquement son OneDrive existant. Pour déplacer le site OneDrive d’un utilisateur, reportez-vous à l’article relatif au [déplacement géographique de OneDrive Entreprise](move-onedrive-between-geo-locations.md) et suivez les instructions relatives au déplacement de OneDrive entre des emplacements géographiques.

Si l’utilisateur ne dispose pas d’un site OneDrive dans le client, OneDrive sera configuré pour lui conformément à sa valeur PDL, en supposant que le PDL pour l’utilisateur correspond à l’un des emplacements satellites de l’entreprise.

## <a name="configuring-multi-geo-search"></a>Configuration de la recherche Multi-Géo

Votre client Multi-Géo aura des fonctionnalités de recherche regroupées permettant à une requête de recherche de renvoyer des résultats de n’importe quel endroit dans le client.

Par défaut, les recherches effectuées à partir de ces points d’entrée renvoient des résultats regroupés, bien que chaque index de recherche se trouve dans son emplacement géographique approprié :

- OneDrive Entreprise

- Delve

- Page d’accueil SharePoint

- Centre de recherche

Par ailleurs, les fonctionnalités de recherche Multi-Géo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent l’API de recherche SharePoint.

Consultez [Configurer la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris des informations sur les limitations et les différences.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validation de la configuration de OneDrive Entreprise Multi-Géo

Vous trouverez ci-dessous des cas d’utilisation de base que vous pouvez inclure dans votre plan de validation avant de déployer OneDrive Entreprise Multi-Géo à grande échelle. Une fois que vous avez terminé ces tests et les cas d’utilisation supplémentaires adaptés à votre entreprise, vous pouvez ajouter les utilisateurs dans votre groupe pilote initial.

**OneDrive Entreprise**

Sélectionnez OneDrive à partir du lanceur d’applications Office 365 et confirmez que vous êtes automatiquement dirigé vers l’emplacement géographique approprié pour l’utilisateur, en fonction du PDL de l’utilisateur. OneDrive Entreprise doit à présent commencer la configuration à cet emplacement. Une fois la configuration terminée, essayez de charger et télécharger certains documents.

**Application mobile OneDrive**

Connectez-vous à votre application mobile OneDrive avec vos informations d’identification de compte test. Confirmez que vous pouvez voir vos fichiers OneDrive Entreprise et que vous pouvez interagir avec eux à partir de votre appareil mobile.

**Client de synchronisation OneDrive**

Vérifiez que le client de synchronisation OneDrive détecte automatiquement l’emplacement géographique de OneDrive Entreprise dès la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **Synchroniser** dans la bibliothèque OneDrive.

**Applications Office**

Confirmez que vous pouvez utiliser OneDrive Entreprise en vous connectant à partir d’une application Office, telle que Word. Ouvrez l’application Office, puis sélectionnez « OneDrive- <TenantName> ». Office détecte votre emplacement OneDrive et affiche les fichiers que vous pouvez ouvrir.

**Partage**

Essayez de partager des fichiers OneDrive. Vérifiez que le sélecteur de personnes affiche tous vos utilisateurs SharePoint en ligne indépendamment de leur emplacement géographique.
