---
title: Application d’une protection aux données personnelles dans Office 365
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Découvrez comment utiliser les stratégies de protection contre la perte de données (DLP) pour protéger les données personnelles dans Office 365.
ms.openlocfilehash: 80b0129ade12824ae5d6190042622ea55ac1d427
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915069"
---
# <a name="apply-protection-to-personal-data-in-office-365"></a>Application d’une protection aux données personnelles dans Office 365

La protection des informations personnelles dans Office 365 inclut l’utilisation de fonctionnalités de protection contre la perte de données. Avec les stratégies DLP dans le centre de sécurité et conformité Office 365, vous pouvez identifier, surveiller et protéger automatiquement les informations sensibles dans Office 365.

Cette rubrique décrit comment utiliser la protection contre la perte de données pour protéger les données personnelles. Elle répertorie également les autres fonctionnalités de protection qui peuvent être utilisées pour se conformer au règlement général sur la protection des données (RGPD), notamment en définissant des autorisations dans les bibliothèques SharePoint et en utilisant des stratégies d’accès aux appareils.

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a>Application d’une protection à l’aide de la protection contre la perte de données dans Office 365

Avec la protection contre la perte de données, vous pouvez :

-   identifier les informations sensibles dans de nombreux emplacements ;

-   empêcher le partage accidentel d’informations sensibles ;

-   aider les utilisateurs à respecter les règles de conformité sans interrompre leur flux de travail ; et

-   consulter les rapports DLP présentant le contenu qui correspond aux stratégies DLP de votre organisation.

Pour plus d’informations, reportez-vous à [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/fr-FR/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

![Options de création d’une stratégie de protection contre la perte de données](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

Cette illustration montre les options permettant de créer une stratégie DLP :

-   Sélectionnez la protection à appliquer. La protection peut inclure :

    -   Des conseils de stratégie pour les utilisateurs

    -   Un rapport par e-mail pour les administrateurs

    -   Des processus empêchant le partage en externe, en interne ou les deux

-   Sélectionnez les critères pour l’application de la protection. « Appliquer la protection... ...aux documents ayant le type de contenu... » : vous pouvez configurer la stratégie pour qu’elle utilise des types d’informations sensibles et/ou des étiquettes.

### <a name="using-dlp-for-gdpr-compliance"></a>Utilisation de la protection contre la perte de données pour le respect du RGPD

L’une des utilisations principales de la protection contre la perte de données Office 365 consiste à identifier les données personnelles liées à des résidents de l’UE dans votre environnement Office 365. La protection contre la perte de données Office 365 peut indiquer à vos équipes de conformité l’endroit où sont stockées les informations personnelles dans SharePoint Online et OneDrive Entreprise, ou leur signaler quand des utilisateurs envoient des courriers électroniques contenant des informations personnelles. La protection contre la perte de données peut également fournir des conseils de stratégie à vos salariés lorsqu’ils manipulent des informations personnelles liées à des personnes résidant dans l’UE.

En indiquant ainsi où les données des résidents de l’UE sont stockées dans votre environnement, en faisant de la sensibilisation à ce sujet et en comprenant comment vos salariés sont autorisés à les manipuler, vous appliquez un premier niveau de protection des informations selon la protection contre la perte de données d’Office 365. Souvent, les salariés qui ont déjà accès à ce type d’informations ont besoin de cet accès pour effectuer leur travail quotidien. L’application de stratégies DLP pour respecter le RGPD ne requiert pas nécessairement une restriction d’accès.

Toutefois, le respect du RGPD implique généralement une évaluation des risques de l’organisation d’un point de vue juridique et de la sécurité des informations, l’identification du type des informations personnelles et de l’endroit où elles sont stockées, ainsi que de la justification juridique pour le stockage et le traitement de ces informations. En fonction de cette évaluation, la mise en œuvre de stratégies pour protéger l’organisation et respecter le RGPD peut nécessiter la suppression de l’accès des employés aux documents contenant des informations personnelles sur des résidents de l’UE. Si une protection supplémentaire est requise, une protection DLP supplémentaire peut être configurée.

Le tableau suivant répertorie trois configurations de protection à l’aide de la DLP. La première configuration, Sensibilisation, peut être utilisée comme niveau minimal et point de départ de la protection pour le RGPD.

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a>Exemple de niveaux de protection pouvant être configurés avec des stratégies DLP et utilisés pour le respect du RGPD

<table>
<thead>
<tr class="header">
<th align="left"><strong>Niveau de protection</strong></th>
<th align="left"><strong>Configuration DLP pour les documents contenant des informations personnelles liées aux données de résidents de l’UE</strong></th>
<th align="left"><strong>Avantages et risques</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Sensibilisation</td>
<td align="left"><p>Envoi de notifications par courrier électronique aux équipes de conformité lorsque ces données sont détectées dans des documents figurant dans SharePoint Online et OneDrive Entreprise.</p>
<p>Personnalisation et affichage de conseils de stratégie destinés aux employés dans SharePoint et OneDrive Entreprise lors de l’accès à des documents contenant ces données.</p>
<p>Détection et signalement du partage de ces données.</p></td>
<td align="left"><p>Les équipes de conformité et les salariés sont sensibilisés et savent où sont stockées ces données.</p>
<p>Les salariés connaissent la stratégie d’entreprise concernant la gestion des documents contenant ces données.</p>
<p>Les salariés peuvent quand même partager ces données en interne ou en externe.</p>
<p>Vous pouvez consulter les rapports DLP pour les données partagées et décider si vous devez augmenter la protection.</p></td>
</tr>
<tr class="even">
<td align="left">Empêcher le partage externe</td>
<td align="left"><p>Restriction d’accès aux documents contenant ces données dans SharePoint Online et OneDrive Entreprise lorsque ce contenu est partagé avec des utilisateurs externes.</p>
<p>Blocage de l’envoi de messages électroniques comportant des documents contenant ces données à des destinataires externes.</p>
<p>Détection et signalement du partage de ces données.</p></td>
<td align="left"><p>Le partage externe de ces données est bloqué mais les employés peuvent utiliser ces données en interne.</p>
<p>Vous pouvez consulter les rapports DLP des données partagées en interne et décider si vous devez augmenter cette protection.</p></td>
</tr>
<tr class="odd">
<td align="left">Empêcher le partage interne et externe</td>
<td align="left"><p>Restriction de l’accès aux documents contenant ces données dans SharePoint Online et OneDrive Entreprise lorsque ce contenu est partagé en interne ou en externe.</p>
<p>Blocage de l’envoi de messages électroniques contenant ces données à des destinataires externes et internes.</p></td>
<td align="left"><p>Le partage interne et externe de ces données est bloqué.</p>
<p>Les employés peuvent ne pas pouvoir effectuer des tâches nécessitant l’utilisation de ces données.</p>
<p>Vous pouvez consulter les rapports DLP pour les données partagées en interne ou en externe et décider si les utilisateurs finaux doivent être formés.</p></td>
</tr>
</tbody>
</table>

Remarque : plus le niveau de protection est élevé, plus la possibilité pour les utilisateurs d’accéder aux informations est restreinte, et cela peut éventuellement avoir un impact sur leur productivité ou la possibilité pour eux d’effectuer leurs tâches quotidiennes. L’augmentation des niveaux de protection par l’implémentation de stratégies qui ont un impact sur les salariés est généralement accompagnée d’une formation des utilisateurs finaux, de l’explication des nouvelles stratégies et procédures de sécurité aux utilisateurs pour les aider à continuer à être productifs dans un environnement plus sécurisé.

### <a name="example-dlp-policy-for-gdpr--awareness"></a>Exemple de stratégie DLP pour le RGPD — Sensibilisation 

Nom : Sensibilisation pour les données personnelles soumises au RGPD.

Description : Afficher des conseils de stratégie aux employés, avertir les équipes de conformité lorsque ces données se trouvent dans des documents dans SharePoint Online et OneDrive Entreprise, détecter le partage de ces données en dehors de votre organisation et le signaler.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Commande</strong></th>
<th align="left"><strong>Paramètres</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Choisir les informations à protéger</td>
<td align="left">Sélectionnez un modèle de stratégie personnalisé.</td>
</tr>
<tr class="even">
<td align="left">Emplacements</td>
<td align="left">Tous les emplacements dans Office 365</td>
</tr>
<tr class="odd">
<td align="left">Chercher du contenu qui contient</td>
<td align="left">Cliquez sur « Modifier » et ajoutez tous les types d’informations sensibles traités dans votre environnement.</td>
</tr>
<tr class="even">
<td align="left">Détecter quand ce contenu est partagé</td>
<td align="left">Cochez cette case, puis sélectionnez « avec des personnes se trouvant en dehors de mon organisation ».</td>
</tr>
<tr class="odd">
<td align="left">Avertir les utilisateurs lorsque le contenu correspond aux paramètres de la stratégie</td>
<td align="left"><p>Cochez cette case (« Afficher des conseils de stratégie aux utilisateurs et leur envoyer une notification par courrier électronique ».)</p>
<p>Cliquez sur « Personnaliser le conseil et le courrier électronique » et mettez à jour les champs pour votre environnement. Consultez les notifications par défaut dans cet article : <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">Envoyer des notifications par courrier électronique et afficher des conseils de stratégie pour les stratégies DLP</a>.</p></td>
</tr>
<tr class="even">
<td align="left">Détecter quand une quantité spécifique d’informations sensibles est partagée à un moment donné</td>
<td align="left"><p>« Détecter quand du contenu partagé contient : Au moins ____ instances du même type d’informations sensibles » : définissez ce paramètre sur 1.</p>
<p>« Envoyer des rapports d’incident par courrier électronique » : cochez cette case. Cliquez sur « Choisir quoi inclure dans le rapport et qui le reçoit ». Veillez à ajouter votre équipe de conformité.</p>
<p>« Déterminer qui peut accéder au contenu et remplacer la stratégie » : désactivez cette case à cocher pour recevoir des notifications concernant les informations sensibles sans empêcher les utilisateurs d’y accéder.</p></td>
</tr>
</tbody>
</table>

Tous les emplacements incluent :

-   SharePoint Online

-   Les comptes OneDrive Entreprise

-   Les boîtes aux lettres Exchange

Étant donné que la recherche de contenu ne vous permet actuellement pas de tester les types d’informations sensibles dans les courriers électroniques, vous pouvez créer des stratégies distinctes pour Exchange avec un sous-ensemble de types d’informations sensibles dans chaque stratégie et surveiller le déploiement de ces stratégies.

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a>Protection supplémentaire pouvant être appliquée pour protéger les données personnelles dans Office 365

Les types d’informations sensibles, les libellés et les stratégies de protection contre la perte de données vous aident à identifier les documents contenant des données spécifiques et à appliquer la protection. Toutefois, pour que ces protections s’appliquent, les autorisations appropriées doivent être définies pour l’accès aux données, les utilisateurs doivent posséder des comptes non compromis et des appareils intègres.

L’illustration suivante détaille une protection supplémentaire que vous pouvez appliquer pour protéger l’accès aux données personnelles.

![Protection supplémentaire pour protéger l’accès aux données personnelles](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

Pour l’accessibilité, le tableau suivant fournit les mêmes informations que l’illustration.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Portée de la protection</strong></th>
<th align="left"><strong>Fonctionnalités</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Protection au niveau du document et du courrier électronique (y compris le courrier en transit, mais pas les boîtes aux lettres au repos pour l’instant)</td>
<td align="left"><p>Types d’informations sensibles</p>
<p>Libellés Office</p>
<p>Stratégies de protection contre la perte de données</p>
<p>Chiffrement des messages Office 365 pour la messagerie</p></td>
</tr>
<tr class="even">
<td align="left">Protection au niveau du site et de la bibliothèque (inclut les sites SharePoint Online et OneDrive Entreprise)</td>
<td align="left"><p>Autorisations pour les sites et les bibliothèques SharePoint Online et OneDrive Entreprise</p>
<p>Stratégies de partage externe pour SharePoint Online et OneDrive Entreprise (au niveau du site)</p>
<p>Stratégies d’accès aux appareils au niveau du site</p></td>
</tr>
<tr class="odd">
<td align="left">Protection de l’accès aux services (inclut l’accès à tous les services dans Office 365)</td>
<td align="left"><p>Protection de l’accès aux identités et aux appareils dans la suite Enterprise Mobility + Security (EMS)</p>
<p>Gestion des accès privilégiés</p>
<p>Fonctionnalités de sécurité Windows 10</p></td>
</tr>
</tbody>
</table>

Le reste de cet article fournit des informations supplémentaires sur chacune de ces catégories de protection.

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a>Fonctionnalités pouvant être utilisées avec le RGPD

Vous pouvez utiliser les fonctionnalités suivantes dans un environnement configuré pour le respect du RGPD. Ces fonctionnalités ne sont pas nécessaires pour le respect du RGPD, mais elles peuvent être utilisées sans nuire à votre capacité à détecter, protéger, surveiller et signaler les données liées au respect du RGPD.

Clé client : permet aux clients de fournir et de garder le contrôle sur les clés de chiffrement utilisées pour chiffrer les données au repos dans Office 365. Recommandé uniquement pour les clients ayant besoin, à titre réglementaire, de gérer leurs propres clés de chiffrement.

Customer Lockbox : vous permet de contrôler l’accès des ingénieurs de support Microsoft à vos données, si nécessaire, pour résoudre un problème technique au cas par cas. Vous pouvez décider d’accorder ou non l’accès à vos données à l’ingénieur de support. Un délai d’expiration est fourni avec chaque demande.

## <a name="site-and-library-level-protection"></a>Protection au niveau du site et de la bibliothèque

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a>Autorisations pour les bibliothèques SharePoint et OneDrive Entreprise

Utilisez des autorisations dans SharePoint pour établir ou restreindre l’accès des utilisateurs au site ou à son contenu. Ajoutez des utilisateurs individuels ou des groupes Azure Active Directory aux groupes SharePoint par défaut. Vous pouvez également créer un groupe personnalisé pour un contrôle plus précis.

![Niveaux d’autorisation de Contrôle total à Afficher uniquement](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

L’illustration représente les niveaux d’autorisation complète de contrôle pour l’affichage seul. Le tableau ci-dessous présente les mêmes informations.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Contrôle total</strong></th>
<th align="left"><strong>Concevoir</strong></th>
<th align="left"><strong>Modifier</strong></th>
<th align="left"><strong>Contribuer</strong></th>
<th align="left"><strong>Lire</strong></th>
<th align="left"><strong>Afficher uniquement</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">Contribuer + approuver et personnaliser</td>
<td align="left">Contribuer + ajouter, modifier et supprimer des listes (pas seulement des éléments de liste)</td>
<td align="left">Afficher, ajouter, mettre à jour et supprimer des éléments de liste et des documents</td>
<td align="left">Afficher et télécharger</td>
<td align="left">Afficher, pas de téléchargement</td>
</tr>
</tbody>
</table>

Plus d’informations :

-   [Présentation des niveaux d’autorisation dans SharePoint](https://support.office.com/fr-FR/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [Présentation des groupes SharePoint](https://support.office.com/fr-FR/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a>Stratégies de partage externe pour les bibliothèques SharePoint et OneDrive Entreprise

De nombreuses organisations autorisent le partage externe pour encourager la collaboration. Découvrez comment vos paramètres client sont configurés. Ensuite, passez en revue les paramètres de partage externe pour les sites qui contiennent des données personnelles.

Un utilisateur externe est une personne extérieure à votre organisation qui est invitée à accéder à vos sites et documents SharePoint Online, mais ne dispose d’aucune licence pour votre abonnement SharePoint Online ou Microsoft Office 365.

Les stratégies de partage externe s’appliquent à SharePoint Online et OneDrive Entreprise.

-   Vous devez être administrateur SharePoint Online pour configurer des stratégies de partage.

-   Vous devez être propriétaire de site ou disposer des autorisations Contrôle total pour partager un site ou un document avec des utilisateurs externes.

Le tableau suivant récapitule les contrôles que vous pouvez configurer.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Catégorie de contrôle</strong></th>
<th align="left"><strong>Options</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Type de partage</td>
<td align="left"><p>Ne pas autoriser le partage en dehors de votre organisation (cette option peut être définie pour des collections de sites individuelles)</p>
<p>Autoriser le partage avec des utilisateurs externes authentifiés uniquement (les options Autoriser nouveaux et Limiter aux existants peuvent être définies pour les collections de sites individuelles)*</p>
<p>Autoriser le partage à des utilisateurs externes avec un lien d’accès anonyme (cette option peut être définie pour des collections de sites individuelles)</p>
<p>Limiter le partage externe à l’aide de domaines (liste de domaines autorisés et de domaines bloqués)</p>
<p>Choisir le type de lien par défaut (anonyme, partageable au sein de la société ou restreint)</p>
</td>
</tr>
<tr class="even">
<td align="left">Ce que les utilisateurs externes peuvent faire</td>
<td align="left"><p>Empêcher les utilisateurs externes de partager des fichiers, des dossiers et des sites qu’ils ne possèdent pas</p>
<p>Exiger que les utilisateurs externes acceptent les invitations de partage avec le même compte que celui auquel l’invitation a été envoyée</p></td>
</tr>
<tr class="odd">
<td align="left">Notifications</td>
<td align="left"><p>Actuellement disponible uniquement dans OneDrive Entreprise. Avertir les propriétaires dans les cas suivants :</p>
- <p>Des utilisateurs invitent des utilisateurs externes supplémentaires à collaborer sur des fichiers partagés</p>
- <p>Les utilisateurs externes acceptent les invitations à accéder aux fichiers</p>
- <p>Un lien d’accès anonyme est créé ou modifié</p></td>
</tr>
</tbody>
</table>

Plus d’informations :

-   
  [Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)

-   [Partager des sites ou des documents avec des personnes extérieures à votre organisation](https://support.office.com/fr-FR/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a>Stratégies d’accès aux appareils au niveau du site

SharePoint Online et OneDrive Entreprise vous permettent de configurer des stratégies d’accès aux appareils au niveau du site. Cela vous permet de configurer plus de protection pour les sites comportant des données sensibles.

Si vous configurez des stratégies d’accès aux appareils au niveau du site, veillez à les coordonner avec les stratégies au niveau du client et également avec les stratégies d’accès configurées dans Azure Active Directory, Intune et Intune App Management.

Les stratégies d’accès aux appareils pour SharePoint et OneDrive Entreprise nécessitent des stratégies de prise en charge dans Azure Active Directory et Microsoft Intune en fonction du scénario que vous mettez en place. Le tableau suivant récapitule les objectifs que vous pouvez atteindre avec des stratégies d’accès aux appareils et indique quels produits nécessitent des stratégies de prise en charge.

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">Autoriser l’accès uniquement à partir d’emplacements d’adresse IP spécifiques</th>
<th align="left">Empêcher les utilisateurs de télécharger des fichiers sur des appareils non associés à un domaine</th>
<th align="left">Bloquer l’accès sur les appareils non associés à un domaine</th>
<th align="left">Empêcher les utilisateurs de télécharger des fichiers sur des appareils non conformes</th>
<th align="left">Bloquer l’accès sur les appareils non conformes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Centre d’administration SharePoint</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
<tr class="even">
<td align="left">Azure Active Directory</td>
<td align="left"></td>
<td align="left">Oui</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
<tr class="odd">
<td align="left">Microsoft Intune</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
</tbody>
</table>

Plus d’informations : [Centre d’administration SharePoint Online : Contrôler l’accès à partir d’appareils non gérés](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US).

## <a name="service-access-protection-for-identities-and-devices"></a>Protection de l’accès au service pour les appareils et les identités

Microsoft vous recommande de configurer la protection pour les identités et les appareils qui accèdent au service. Le travail que vous effectuez pour protéger l’accès aux services Office 365 peut également être utilisé pour protéger l’accès à d’autres services SaaS et PaaS, et même à des applications dans d’autres fournisseurs cloud.

La protection de l’accès pour les appareils et les identités fournit une référence de base de la protection pour garantir que les identités ne sont pas compromises, que les appareils sont sûrs et que les données des organisations figurant sur les appareils sont isolées et protégées.

Pour obtenir des recommandations pour commencer et des instructions de configuration, reportez-vous à [Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](https://docs.microsoft.com/fr-FR/microsoft-365-enterprise/microsoft-security-guidance).

Pour les environnements d’identité hybrides avec AD FS, reportez-vous aux [configurations et aux stratégies de sécurité recommandées](https://docs.microsoft.com/fr-FR/microsoft-365-enterprise/microsoft-security-guidance).

L’illustration suivante décrit les relations entre les services cloud (SaaS, PaaS), les types de comptes (comptes de domaine clients et comptes B2B) et les fonctionnalités de service d’accès. Il est important de noter les fonctionnalités qui peuvent être utilisées avec les comptes B2B.

![Services cloud, types de comptes et fonctionnalités d’accès](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

Pour l’accessibilité, le reste de cette section décrit cette illustration.

### <a name="cloud-services"></a>Services de cloud

Azure Active Directory fournit un accès basé sur l’identité à n’importe quel service cloud, y compris les fournisseurs non-Microsoft tels qu’Amazon Web Services. L’illustration montre Office 365, une « autres application SaaS » et une « application PaaS ». Les flèches pointent d’Azure Active Directory vers chacun de ces services, et montrent qu’Azure Active Directory peut être utilisé pour l’authentification à tous ces types d’application.

### <a name="types-of-accounts"></a>Types de comptes

Les comptes de domaine clients sont des comptes que vous ajoutez à votre client et que vous gérez directement. Les comptes B2B sont des comptes pour les utilisateurs extérieurs à votre organisation que vous invitez pour collaborer avec eux. Il peut s’agir d’autres comptes Office 365, de comptes d’autres organisations ou de comptes clients (par exemple, Gmail). L’illustration montre les deux types de comptes dans Azure Active Directory.

### <a name="capabilities"></a>Fonctionnalités

Les fonctionnalités figurant dans le tableau suivant protègent les identités et les appareils. Le tableau indique les fonctionnalités qui peuvent également être utilisées avec des comptes B2B, comme dans l’illustration.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Fonctionnalité</strong></th>
<th align="left"><strong>Fonctionne avec les comptes de domaine clients</strong></th>
<th align="left"><strong>Fonctionne avec les comptes Azure B2B (sans licence supplémentaire)</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Authentification multifacteur et accès conditionnel</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
<tr class="even">
<td align="left">Azure AD Identity Protection</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
<tr class="odd">
<td align="left">Azure AD Privileged Identity Management</td>
<td align="left">Oui</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Gestion des applications mobiles (MAM)</td>
<td align="left">Oui</td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">Gestion et inscription des appareils</td>
<td align="left">Oui</td>
<td align="left">Seule une organisation peut gérer un appareil</td>
</tr>
<tr class="even">
<td align="left">Fonctionnalités de sécurité Windows 10 (l’accès conditionnel basé sur la conformité de l’appareil nécessite une gestion des appareils)</td>
<td align="left">Oui</td>
<td align="left">Oui</td>
</tr>
</tbody>
</table>

Vous pouvez ajouter des licences à des comptes B2B pour donner à ces utilisateurs des fonctionnalités supplémentaires, si nécessaire, pour protéger l’accès à des données personnelles dans votre environnement.
