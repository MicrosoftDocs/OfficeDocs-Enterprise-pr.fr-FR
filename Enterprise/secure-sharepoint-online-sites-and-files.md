---
title: Sécurisation des fichiers et sites SharePoint Online
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 'Résumé : Configuration des recommandations pour la protection de fichiers dans SharePoint Online et Office 365.'
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Sécuriser des sites et des fichiers SharePoint Online

 **Résumé :** Configuration des recommandations pour la protection de fichiers dans SharePoint Online et Office 365.
  
Cet article fournit des recommandations pour la configuration des sites d’équipe SharePoint Online et protection de fichier qui équilibre entre la sécurité en toute simplicité de collaboration. Cet article définit quatre différentes configurations, en commençant par un site public au sein de votre organisation avec les stratégies de partage plus ouverts. Chaque configuration supplémentaire représente une étape significative des protection, mais la capacité à accéder et collaborer sur des ressources est réduite à l’ensemble pertinent d’utilisateurs. Utilisez ces recommandations comme point de départ et ajuster les configurations afin de répondre aux besoins de votre organisation. 
  
Les configurations décrites dans cet article respectent les recommandations de Microsoft quant aux trois niveaux de protection des données, des identités et des appareils :
  
- Protection Base de référence
    
- Protection Sensible
    
- Protection Hautement confidentiel
    
Pour plus d’informations sur ces niveaux et les fonctionnalités recommandées pour chacun d’eux, consultez les ressources suivantes. 
  
- [Protection des identités et des appareils pour Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Solutions de protection des fichiers dans Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Vue d’ensemble des fonctionnalités

Les recommandations pour les sites d’équipe SharePoint Online s’appuient sur différentes fonctionnalités d’Office 365. Pour les sites hautement confidentiels, Azure Information Protection est recommandé. Ceci est inclus dans Enterprise Mobility + Security (EMS). 
  
L’illustration suivante montre les configurations recommandées pour quatre sites d’équipe SharePoint Online.
  
![Configuration recommandée pour les sites SharePoint](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
Comme illustré :
  
- La protection Base de référence a deux options pour les sites d’équipe SharePoint Online : un site public et un site privé. Les sites publics peuvent être découverts et sont accessibles par toute personne de l’organisation. Les sites privés peuvent être détectés et sont accessibles seulement par les membres du site. Ces deux configurations de site permettent le partage en dehors du groupe. 
    
- Les sites pour la protection Hautement confidentiel et Sensible sont des sites privés avec un accès limité aux seuls membres de groupes spécifiques.
    
- Les étiquettes Office 365 permettent de classifier les données avec le niveau de protection nécessaire. Chacun des sites d’équipe SharePoint Online est configuré pour étiqueter automatiquement les fichiers dans des bibliothèques de documents avec une étiquette par défaut pour le site. Correspondant aux configurations des quatre sites, les étiquettes de cet exemple sont Public interne, Privé, Sensible et Hautement confidentiel. Les utilisateurs peuvent changer les étiquettes, mais cette configuration garantit que tous les fichiers reçoivent une étiquette par défaut.
    
- Des stratégies de protection contre la perte de données sont configurées pour les étiquettes Office 365 Sensible et Hautement confidentiel, pour avertir ou empêcher les utilisateurs quand ils tentent d’envoyer des fichiers de ces types à l’extérieur de l’organisation.
    
- Pour les sites configurés avec la protection Hautement confidentiel, Azure Information Protection chiffre les fichiers et accorde des autorisations sur ceux-ci.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Paramètres au niveau du locataire pour SharePoint Online et OneDrive Entreprise

SharePoint Online et OneDrive Entreprise incluent des paramètres au niveau du locataire qui affectent tous les sites et tous les utilisateurs. Certains de ces paramètres peuvent également être ajustés au niveau du site dans un sens plus restrictif (mais pas moins). Cette section décrit les paramètres au niveau du locataire qui affectent la sécurité et la collaboration. 
  
### <a name="sharing"></a>Partage

Pour cette solution, nous recommandons les paramètres au niveau du locataire suivants :
  
- Conservez la stratégie de partage par défaut qui autorise le partage complet avec tous les types de comptes, notamment le partage anonyme.
    
- Si nécessaire, spécifiez que les liens anonymes doivent expirer.
    
- Changez le type de lien par défaut pour le partage en Interne. Ceci permet d’éviter les fuites accidentelles de données à l’extérieur de votre organisation.
    
S’il peut sembler contre-intuitif d’autoriser le partage externe, cette approche offre néanmoins plus de contrôle sur le partage de fichiers que l’envoi de fichiers par e-mail. SharePoint Online et Outlook fonctionnent ensemble pour fournir une collaboration sécurisée sur les fichiers. 
  
- Par défaut, Outlook partage un lien vers un fichier au lieu d’envoyer le fichier dans un e-mail. 
    
- SharePoint Online et OneDrive Entreprise facilitent le partage de liens vers des fichiers avec des collaborateurs qui se trouvent à l’intérieur et à l’extérieur de votre organisation
    
Vous disposez aussi de contrôles permettant de régir le partage externe. Par exemple, vous pouvez :
  
- Désactiver une liaison d’invité anonyme.
    
- Révoquer l’accès utilisateur à un site.
    
- Voir qui a accès à un site ou un document spécifique.
    
- Spécifier que les liens de partage anonyme doivent expirer (paramètre au niveau du locataire).
    
- Limiter qui peut partager à l’extérieur de votre organisation (paramètre au niveau du locataire).
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Utiliser le partage externe avec la protection contre la perte de données

Si vous n’autorisez pas le partage externe, les utilisateurs avec une entreprise avez besoin trouveront méthodes et autres outils. Microsoft vous recommande de que vous associer un partage externe avec les stratégies DLP pour protéger les fichiers sensibles et hautement confidentielles.
  
### <a name="device-access-settings"></a>Paramètres d’accès d’appareil

Paramètres d’accès de périphérique pour SharePoint Online et OneDrive pour l’entreprise vous permettent de déterminer si l’accès est limité au navigateur uniquement (les fichiers ne peuvent pas être téléchargés) ou si l’accès est bloqué. Ces paramètres sont actuellement dans la première version et s’appliquent à l’échelle du locataire. Bientôt disponible est la possibilité de configurer des stratégies d’accès de périphérique au niveau du site. Pour cette solution, nous vous recommandons de ne pas à l’aide des paramètres d’accès de périphérique qui s’appliquent à l’échelle du locataire.
  
Pour utiliser les paramètres d’accès d’appareil quand ils sont en version First Release : [Configurer les options Standard Release et First Release dans Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### <a name="onedrive-for-business"></a>OneDrive Entreprise

Examinez ces paramètres pour décider si vous voulez changer les paramètres par défaut pour les sites OneDrive Entreprise. Actuellement, les paramètres d’accès de partage et d’appareil sont dupliqués à partir du Centre d’administration SharePoint Online et s’appliquent aux deux environnements.
  
## <a name="sharepoint-team-site-configuration"></a>Configuration des sites d’équipe SharePoint

Le tableau suivant récapitule la configuration pour chacun des sites d’équipe décrites précédemment dans cet article. Utilisez ces recommandations comme point de départ et ajustez les types et les configurations de site pour répondre aux besoins de votre organisation. Toutes les organisations n’ont pas nécessairement besoin de chacun de ces types de site. Seul un petit nombre d’organisations a besoin d’une protection hautement confidentielle.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Protection Base de référence #1** <br/> |**Protection Base de référence #2** <br/> |**Protection Sensible** <br/> |**Hautement confidentiel** <br/> |
|Description  <br/> |Découverte et collaboration ouvertes au sein de l’organisation.  <br/> |Site privé et groupe avec partage autorisé en dehors du groupe.  <br/> |Site isolé, dans lequel les niveaux d’accès sont définis par l’appartenance à des groupes spécifiques. Le partage est autorisé uniquement aux membres du site. La protection contre la perte de données avertit les utilisateurs quand ils tentent d’envoyer des fichiers à l’extérieur de l’organisation.  <br/> |Site isolé + chiffrement des fichiers et autorisations avec Azure Information Protection. La protection contre la perte de données empêche les utilisateurs d’envoyer des fichiers à l’extérieur de l’organisation.  <br/> |
|Site d’équipe privé ou public  <br/> |Public  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|Qui a accès ?  <br/> |Toute personne de l’organisation, notamment les utilisateurs B2B et les utilisateurs invités.  <br/> |Membres du site uniquement. Les autres personnes peuvent demander l’accès.  <br/> |Membres du site uniquement. Les autres personnes peuvent demander l’accès.  <br/> |Membres uniquement. Les autres personnes ne peuvent pas demander l’accès.  <br/> |
|Contrôles de partage au niveau du site  <br/> |Partage autorisé avec n’importe qui. Paramètres par défaut.  <br/> |Partage autorisé avec n’importe qui. Paramètres par défaut.  <br/> |Les membres ne peuvent pas partager l’accès au site.  <br/> Les non-membres peuvent demander l’accès au site, mais ces demandes doivent être traitées par un administrateur du site.  <br/> |Les membres ne peuvent pas partager l’accès au site.  <br/> Les non-membres ne peuvent pas demander l’accès au site ou au contenu.  <br/> |
|Contrôles d’accès d’appareil au niveau du site  <br/> |Pas de contrôles supplémentaires.  <br/> |Pas de contrôles supplémentaires.  <br/> |Les contrôles au niveau du site sont bientôt disponibles : ils empêchent les utilisateurs de télécharger des fichiers sur des appareils non conformes ou non joints au domaine. Ceci permet un accès via le navigateur uniquement à partir de tous les autres appareils.  <br/> |Les contrôles au niveau du site sont bientôt disponibles : ils bloquent le téléchargement des fichiers sur des appareils non conformes ou non joints au domaine.  <br/> |
|Étiquettes Office 365  <br/> |Public interne  <br/> |Private  <br/> |Sensible  <br/> |Hautement confidentiel  <br/> |
|Stratégies de protection contre la perte de données  <br/> |||Avertissez les utilisateurs lors de l’envoi des fichiers qui sont étiquetés comme sensibles à l’extérieur de l’organisation.  <br/> Pour bloquer le partage externe des types de données sensibles, comme des numéros de carte de crédit ou d’autres données personnelles, vous pouvez configurer des stratégies supplémentaires de protection contre la perte de données pour ces types de données (notamment les types de données personnalisés que vous configurez).  <br/> |Empêchez les utilisateurs d’envoyer des fichiers qui sont étiquetés comme hautement confidentiels à l’extérieur de l’organisation. Autorisez les utilisateurs à passer outre ceci en donnant une justification, indiquant notamment avec qui ils partagent le fichier.  <br/> |
|Azure Information Protection  <br/> ||||Utilisez Azure Information Protection pour chiffrer automatiquement les fichiers et leur accorder des autorisations. Cette protection se déplace avec les fichiers au cas où ils sortent de l’organisation.   <br/> Office 365 ne peut pas lire les fichiers cryptés avec la Protection des informations Azure. En outre, les stratégies DLP ne peuvent fonctionner avec les métadonnées (y compris les étiquettes) mais pas le contenu de ces fichiers (par exemple les numéros de carte de crédit dans les fichiers).  <br/> |
   
Pour savoir comment déployer les quatre types différents de sites d’équipe SharePoint Online dans cette solution, consultez [les sites déployer SharePoint Online à trois niveaux de protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Pour les étapes créer un environnement de développement/test, consultez [les sites SharePoint Online de la sécuriser dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Étiquettes et classification Office 365

L’utilisation des étiquettes Office 365 est recommandée pour les environnements comportant des données sensibles. Après avoir configuré et publié des étiquettes Office 365 :
  
- Vous pouvez appliquer une étiquette par défaut à une bibliothèque de documents dans un site d’équipe SharePoint Online, afin que tous les documents figurant dans cette bibliothèque obtiennent l’étiquette par défaut.  
    
- Vous pouvez appliquer des étiquettes au contenu automatiquement s’il répond à des conditions spécifiques.
    
- Vous pouvez appliquer des stratégies DLP qui sont basées sur les étiquettes d’Office 365.
    
- Les personnes de votre organisation peuvent appliquer une étiquette manuellement au contenu dans Outlook sur le web, Outlook 2010 et les versions ultérieur, OneDrive pour les groupes d’entreprises, SharePoint Online et Office 365. Les utilisateurs souvent connaissent mieux le type de contenu, ils collaborent avec, leur permettant de classer et de la stratégie DLP approprié appliqué.
    
![Configuration recommandée pour les sites SharePoint](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Comme illustré, cette solution inclut la création des étiquettes suivantes :
  
- Hautement confidentiel
    
- Sensible
    
- Privé
    
- Public interne
    
Ces étiquettes sont mises en correspondance avec les sites recommandés dans les illustrations et graphiques figurant plus haut dans cet article. Cette solution recommande de configurer des stratégies DLP pour empêcher la fuite de fichiers portant l’étiquette Sensible et Hautement confidentiel.
  
Pour connaître les étapes de configuration des étiquettes Office 365 et des stratégies de protection contre la perte de données dans cette solution, consultez [Protéger des fichiers SharePoint Online avec des étiquettes Office 365 et la protection contre la perte de données](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Azure Information Protection

Utilisez Azure Information Protection pour appliquer des étiquettes et des protections qui accompagnent les fichiers, quel que soit leur emplacement. Pour cette solution, nous vous recommandons d’utiliser une stratégie délimitée Azure Information Protection et une sous-étiquette de l’étiquette Hautement confidentiel pour chiffrer et accorder des autorisations sur les fichiers qui doivent être protégés avec le plus haut niveau de sécurité. 
  
Attention, quand le chiffrement Azure Information Protection est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter le contenu de ces fichiers. La co-édition, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent fonctionner seulement avec les métadonnées (notamment les étiquettes Office 365), mais pas avec le contenu de ces fichiers (comme des numéros de carte de crédit dans des fichiers).
  
![Azure Information Protection est configuré dans Azure et des étiquettes apparaissent dans la barre d’outils du client](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Comme illustré :
  
- Vous configurez les stratégies de Protection des informations Azure et étiquettes dans le portail Microsoft Azure. Configuration d’une étiquette secondaire d’une stratégie de Protection des informations Azure étendue est recommandé.
    
- Protection des informations Azure les étiquettes afficher sous la forme d’une barre de **protection des informations** dans les applications Office.
    
### <a name="adding-permissions-for-external-users"></a>Ajout d’autorisations pour les utilisateurs externes

Il existe deux méthodes que vous pouvez accorder aux utilisateurs externes l’accès aux fichiers protégés par la Protection des informations Azure. Dans ces deux cas, les utilisateurs externes doivent avoir un compte Azure. Si les utilisateurs externes ne sont pas membres d’une organisation qui utilise AD Azure, ils peuvent obtenir un compte Azure individuel à l’aide de cette page d’inscription : [https://aka.ms/aip-signup](https://aka.ms/aip-signup).
  
- Ajouter des utilisateurs externes à un groupe Azure AD qui est utilisé pour configurer la protection d’une étiquette
    
     Vous devez d’abord ajouter le compte en tant qu’un utilisateur B2B dans votre répertoire. Il peut prendre quelques heures pour [l’appartenance au groupe de mise en cache par Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). Avec cette méthode, les autorisations sont accordées à tous les fichiers existants protégés par l’étiquette (même les fichiers protégés avant l’ajout d’un utilisateur pour le groupe d’annonces Azure).
    
- Ajouter des utilisateurs externes directement à la protection d’étiquette
    
     Vous pouvez ajouter tous les utilisateurs d’une organisation (par exemple, Fabrikam.com), un groupe Azure AD (par exemple, un groupe financier au sein d’une organisation) ou un utilisateur individuel. Par exemple, vous pouvez ajouter une équipe externe de régulateurs à la protection d’une étiquette. Avec cette méthode, les autorisations sont accordées uniquement aux fichiers protégés avec l’étiquette une fois que l’entité externe est ajoutée à la protection.
    
### <a name="deploying-and-using-azure-information-protection"></a>Déploiement et utilisation d’Azure Information Protection

Pour connaître les étapes de configuration d’Azure Information Protection dans cette solution, consultez [Protéger des fichiers SharePoint Online avec Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Solutions de sécurité](security-solutions.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Sécuriser les sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



