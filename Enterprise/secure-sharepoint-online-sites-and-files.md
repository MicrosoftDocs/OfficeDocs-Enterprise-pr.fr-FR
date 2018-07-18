---
title: Sécuriser des sites et des fichiers SharePoint Online
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 'Résumé : Recommandations de configuration pour la protection des fichiers dans SharePoint Online et Office 365.'
ms.openlocfilehash: 806f9880347a5fa4aff29206651d86b0e18da3a4
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319225"
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Sécuriser des sites et des fichiers SharePoint Online

 **Résumé :** Recommandations de configuration pour la protection des fichiers dans SharePoint Online et Office 365.
  
Cet article fournit des recommandations pour configurer les sites d’équipe SharePoint Online et la protection des fichiers d’une façon qui combine sécurité et simplicité de collaboration. Cet article définit quatre configurations différentes, en commençant par un site public au sein de votre organisation avec les stratégies de partage les plus ouvertes. Chacune des autres configurations représente une amélioration significative de la protection, mais limite l’accès aux ressources et les possibilités de collaboration à l’ensemble d’utilisateurs concerné. Utilisez ces recommandations comme point de départ et ajustez les configurations pour répondre aux besoins de votre organisation. 
  
Les configurations décrites dans cet article respectent les recommandations de Microsoft quant aux trois niveaux de protection des données, des identités et des appareils :
  
- Protection Base de référence
    
- Protection Sensible
    
- Protection Hautement confidentiel
    
Pour plus d’informations sur ces niveaux et les fonctionnalités recommandées pour chacun d’eux, consultez les ressources suivantes. 
  
- [Protection des appareils et de l’identité pour Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Solutions de protection des fichiers dans Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Vue d’ensemble des fonctionnalités

Les recommandations concernant les sites d’équipe SharePoint Online mobilisent un grand nombre de fonctionnalités Office 365. Pour les sites hautement confidentiels, le service Azure Information Protection est recommandé. Ce service est inclus dans EMS (Enterprise Mobility + Security). 
  
L’illustration suivante montre les configurations recommandées pour quatre sites d’équipe SharePoint Online.

![Configuration recommandée pour les sites SharePoint](Media/SharePoint-site-configuration-v2.png)

Comme illustré :
  
- La protection de référence inclut deux options pour les sites d’équipe SharePoint Online : un site public et un site privé. Les sites publics peuvent être recherchés et sont accessibles à toute personne de l’organisation. Les sites privés peuvent uniquement être recherchés par les membres du site et seuls ces derniers peuvent y accéder. Ces deux configurations de site permettent le partage en dehors du groupe. 
    
- Les sites pour la protection Hautement confidentiel et Sensible sont des sites privés avec un accès limité aux seuls membres de groupes spécifiques.
    
- Les étiquettes Office 365 permettent de classer les données avec le niveau de protection voulu. Chacun des sites d’équipe SharePoint Online est configuré de façon à attribuer automatiquement une étiquette par défaut, propre au site, aux fichiers figurant dans les bibliothèques de documents. Correspondant aux quatre configurations de site, les étiquettes de cet exemple sont Public interne, Privé, Sensible et Hautement confidentiel. Les utilisateurs peuvent modifier les étiquettes, mais cette configuration garantit que tous les fichiers reçoivent une étiquette par défaut.
    
- Les stratégies de protection contre la perte de données sont configurées pour les étiquettes Office 365 Sensible et Hautement confidentiel afin de prévenir les utilisateurs quand ils essaient d’envoyer ces types de fichiers à l’extérieur de l’organisation, ou de les en empêcher.
    
- S’il est utile pour votre scénario, vous pouvez chiffrer et accorder des autorisations à des fichiers hautement confidentiels grâce à Azure Information Protection. Cela n’est pas recommandé pour tous les clients.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Paramètres à l’échelle du client pour SharePoint Online et OneDrive Entreprise

SharePoint Online et OneDrive Entreprise incluent des paramètres à l’échelle du client qui concernent tous les sites et les utilisateurs. Certains de ces paramètres peuvent également être ajustés au niveau du site pour que ce dernier soit plus restrictif (mais pas moins). Cette section décrit les paramètres à l’échelle du client qui concernent la sécurité et la collaboration. 
  
### <a name="sharing"></a>Partage

Pour cette solution, nous recommandons les paramètres au niveau du locataire suivants :
  
- Conservez la stratégie de partage par défaut qui autorise le partage complet avec tous les types de comptes, notamment le partage anonyme.
    
- Configurez les liens anonymes de sorte à ce qu’ils expirent, si vous le souhaitez.
    
- Modifiez le type de liaison par défaut pour le partage sur Interne. Cela contribue à la prévention des fuites accidentelles de données à l’extérieur de votre organisation.
    
Bien qu’il puisse sembler contre-intuitif d’autoriser le partage externe, cette approche offre davantage de contrôle sur le partage de fichiers par rapport à l’envoi de fichiers par courrier électronique. SharePoint Online et Outlook fonctionnent ensemble pour sécuriser la collaboration sur les fichiers. 
  
- Par défaut, Outlook partage un lien vers un fichier au lieu d’envoyer le fichier dans un e-mail. 
    
- SharePoint Online et OneDrive Entreprise facilitent le partage de liens vers des fichiers avec des collaborateurs qui se trouvent à l’intérieur et à l’extérieur de votre organisation
    
Vous avez également des contrôles pour vous aider à gérer le partage externe. Par exemple, vous pouvez :
  
- désactiver un lien invité anonyme ;
    
- Révoquer l’accès utilisateur à un site.
    
- Voir qui a accès à un site ou un document spécifique.
    
- Spécifier que les liens de partage anonyme doivent expirer (paramètre au niveau du locataire).
    
- Limiter qui peut partager à l’extérieur de votre organisation (paramètre au niveau du locataire).
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Utiliser le partage externe avec la protection contre la perte de données

Si vous n’autorisez pas le partage externe, les utilisateurs ayant des besoins métier trouveront d’autres outils et d’autres méthodes. Microsoft vous recommande de combiner le partage externe avec des stratégies de protection contre la perte de données pour protéger les fichiers sensibles et hautement confidentiels.
  
### <a name="device-access-settings"></a>Paramètres d’accès d’appareil

Les paramètres d’accès d’appareil pour SharePoint Online et OneDrive Entreprise vous permettent de déterminer si l’accès est limité au navigateur uniquement (les fichiers ne peuvent pas être téléchargés) ou si l’accès est bloqué. Ces paramètres sont actuellement en version First Release et s’appliquent au niveau du client. La possibilité de configurer des stratégies d’accès d’appareil au niveau du site sera bientôt disponible. Pour cette solution, nous recommandons de ne pas utiliser des paramètres d’accès d’appareil qui s’appliquent au niveau du client.
  
Pour utiliser les paramètres d’accès d’appareil quand ils sont en version First Release : [Configurer les options Standard Release et First Release dans Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### <a name="onedrive-for-business"></a>OneDrive Entreprise

Consultez ces paramètres pour décider si vous souhaitez modifier les paramètres par défaut pour les sites OneDrive Entreprise. Actuellement, le partage et les paramètres d’accès aux appareils sont dupliqués à partir du centre d’administration SharePoint Online et s’appliquent aux deux environnements.
  
## <a name="sharepoint-team-site-configuration"></a>Configuration d’un site d’équipe SharePoint

Le tableau suivant récapitule la configuration pour chacun des sites d’équipe décrits plus haut dans cet article. Utilisez ces configurations comme recommandations de point de départ et ajustez les configurations et les types de site pour répondre aux besoins de votre organisation. Les organisations n’ont pas toutes besoin de tous les types de site. Seules quelques organisations requièrent la protection hautement confidentielle.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Protection Base de référence #1** <br/> |**Protection Base de référence #2** <br/> |**Protection Sensible** <br/> |**Hautement confidentiel** <br/> |
|Description  <br/> |Découverte et collaboration ouvertes au sein de l’organisation.  <br/> |Site privé et groupe avec partage autorisé en dehors du groupe.  <br/> |Site isolé, dans lequel les niveaux d’accès sont définis par l’appartenance à des groupes spécifiques. Le partage est autorisé uniquement aux membres du site. La protection contre la perte de données avertit les utilisateurs quand ils tentent d’envoyer des fichiers à l’extérieur de l’organisation.  <br/> |Site isolé + chiffrement des fichiers et autorisations avec Azure Information Protection. La protection contre la perte de données empêche les utilisateurs d’envoyer des fichiers à l’extérieur de l’organisation.  <br/> |
|Site d’équipe privé ou public  <br/> |Public  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|Qui a accès ?  <br/> |Tous les membres de l’organisation, y compris les utilisateurs B2B et les utilisateurs invités.  <br/> |Les membres du site uniquement. D’autres utilisateurs peuvent demander l’accès.  <br/> |Les membres du site uniquement. D’autres utilisateurs peuvent demander l’accès.  <br/> |Uniquement les membres. Personne d’autre ne peut demander l’accès.  <br/> |
|Contrôles de partage au niveau du site  <br/> |Partage autorisé avec tout le monde. Paramètres par défaut.  <br/> |Partage autorisé avec tout le monde. Paramètres par défaut.  <br/> |Les membres ne peuvent pas partager l’accès au site.  <br/> Les non-membres peuvent demander l’accès au site, mais ces demandes doivent être traitées par un administrateur du site.  <br/> |Les membres ne peuvent pas partager l’accès au site.  <br/> Les non-membres ne peuvent pas demander l’accès au site ou au contenu.  <br/> |
|Contrôles d’accès d’appareil au niveau du site  <br/> |Pas de contrôles supplémentaires.  <br/> |Aucun contrôle supplémentaire.  <br/> |Les contrôles au niveau du site seront bientôt disponibles et empêcheront les utilisateurs de télécharger des fichiers sur des appareils non conformes ou non liés à un domaine. Cela permet un accès par navigateur uniquement à partir de tous les autres appareils.  <br/> |Les contrôles au niveau du site, qui bloquent le téléchargement de fichiers sur des appareils non conformes ou non joints à un domaine, seront bientôt disponibles.  <br/> |
|Étiquettes Office 365  <br/> |Public interne  <br/> |Private  <br/> |Sensible  <br/> |Hautement confidentiel  <br/> |
|Stratégies de protection contre la perte de données  <br/> |||Avertissez les utilisateurs lors de l’envoi des fichiers qui sont étiquetés comme sensibles à l’extérieur de l’organisation.  <br/> Pour bloquer le partage externe de types de données sensibles, telles que les numéros de carte de crédit ou d’autres données personnelles, vous pouvez configurer des stratégies de protection contre la perte de données supplémentaires pour ces types de données (y compris les types de données personnalisés que vous configurez).  <br/> |Empêchent les utilisateurs d’envoyer des fichiers portant l’étiquette Hautement confidentiel en dehors de l’organisation. Autorisent les utilisateurs à passer outre ce paramètre en fournissant une justification, notamment en indiquant la personne avec laquelle ils partagent le fichier.  <br/> |
|Azure Information Protection  <br/> ||||Utilisez Azure Information Protection pour chiffrer automatiquement les fichiers et leur accorder des autorisations. Cette protection se déplace avec les fichiers au cas où ils sortent de l’organisation.  <br/> Office 365 ne peut pas lire les fichiers chiffrés avec Azure Information Protection. En outre, les stratégies de protection contre la perte de données (DLP) peuvent fonctionner uniquement avec les métadonnées (y compris les étiquettes), et pas avec le contenu de ces fichiers (par exemple, des numéros de cartes de crédit au sein des fichiers).  <br/> |
   
Pour connaître les étapes de déploiement des quatre différents types de sites d’équipe SharePoint Online dans cette solution, consultez l’article relatif au [déploiement de sites SharePoint Online pour trois niveaux de protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Pour connaître la procédure de création d’un environnement de développement/test, reportez-vous à l’article relatif à la [sécurisation des sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Classification et étiquettes Office 365

L’utilisation des étiquettes Office 365 est recommandée pour les environnements comportant des données sensibles. Après avoir configuré et publié des étiquettes Office 365 :
  
- Vous pouvez appliquer une étiquette par défaut à une bibliothèque de documents dans un site d’équipe SharePoint Online, afin que tous les documents figurant dans cette bibliothèque obtiennent l’étiquette par défaut. 
    
- Vous pouvez appliquer des étiquettes au contenu automatiquement s’il répond à des conditions spécifiques.
    
- Vous pouvez appliquer des stratégies de protection contre la perte de données qui reposent sur les étiquettes Office 365.
    
- Des personnes de votre organisation peuvent appliquer une étiquette manuellement au contenu dans Outlook sur le web, Outlook 2010 et versions ultérieures, OneDrive Entreprise, SharePoint Online et les groupes Office 365. Les utilisateurs savent souvent mieux quel type de contenu ils utilisent, ils peuvent donc le classer et appliquer la stratégie DLP appropriée.
    
![Configuration recommandée pour les sites SharePoint](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Comme illustré, cette solution inclut la création des étiquettes suivantes :
  
- Hautement confidentiel
    
- Sensible
    
- Private
    
- Public interne
    
Ces étiquettes sont mises en correspondance avec les sites recommandés dans les illustrations et graphiques figurant plus haut dans cet article. Cette solution recommande de configurer des stratégies DLP pour empêcher la fuite de fichiers portant l’étiquette Sensible et Hautement confidentiel.
  
Pour connaître les étapes de configuration des étiquettes Office 365 et des stratégies de protection contre la perte de données dans cette solution, consultez [Protéger des fichiers SharePoint Online avec des étiquettes Office 365 et la protection contre la perte de données](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Azure Information Protection

Si cela se justifie pour votre scénario de sécurité, vous pouvez utiliser Azure Information Protection pour appliquer des étiquettes et des protections qui accompagnent les fichiers, quel que soit leur emplacement. Les étiquettes Azure Information Protection sont différentes des étiquettes Office 365. Pour cette solution, nous vous recommandons d’utiliser une stratégie délimitée Azure Information Protection et une sous-étiquette de l’étiquette Hautement confidentiel pour chiffrer et accorder des autorisations sur les fichiers qui doivent être protégés avec le plus haut niveau de sécurité. 
  
Attention, quand le chiffrement Azure Information Protection est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter le contenu de ces fichiers. La co-édition, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent fonctionner seulement avec les métadonnées (notamment les étiquettes Office 365), mais pas avec le contenu de ces fichiers (comme des numéros de carte de crédit dans des fichiers).
  
![Azure Information Protection est configuré dans Azure et des étiquettes apparaissent dans la barre d’outils du client](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Comme illustré :
  
- Vous configurez des stratégies et des étiquettes Azure Information Protection dans le portail Microsoft Azure. Nous vous recommandons de configurer une sous-étiquette d’une stratégie Azure Information Protection délimitée.
    
- Les étiquettes Azure Information Protection apparaissent sous la forme d’une barre **Information Protection** dans les applications Office.
    
### <a name="adding-permissions-for-external-users"></a>Ajout d’autorisations pour les utilisateurs externes

Il existe deux façons d’accorder à des utilisateurs externes un accès à des fichiers protégés par le service Azure Information Protection. Dans les deux cas, les utilisateurs externes doivent disposer d’un compte Azure Active Directory. Si les utilisateurs externes ne sont pas membres d’une organisation qui utilise Azure AD, ils peuvent obtenir un compte Azure AD individuel via cette page d’inscription : [https://aka.ms/aip-signup](https://aka.ms/aip-signup)
  
- Ajouter des utilisateurs externes à un groupe Azure AD qui est utilisé pour configurer la protection d’une étiquette
    
     Vous devez tout d’abord ajouter le compte en tant qu’utilisateur B2B dans votre répertoire. La [mise en cache de l’appartenance au groupe par Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management) peut prendre quelques heures. Avec cette méthode, les autorisations sont accordées à tous les fichiers existants protégés avec l’étiquette (même les fichiers protégés avant l’ajout d’un utilisateur au groupe Azure AD).
    
- Ajouter des utilisateurs externes directement à la protection d’étiquette
    
     Vous pouvez ajouter tous les utilisateurs d’une organisation (par exemple, Fabrikam.com), un groupe Azure AD (par exemple, un groupe financier au sein d’une organisation) ou un utilisateur individuel. Par exemple, vous pouvez ajouter une équipe externe de régulateurs à la protection d’une étiquette. Avec cette méthode, les autorisations sont accordées uniquement aux fichiers protégés avec l’étiquette une fois que l’entité externe est ajoutée à la protection.
    
### <a name="deploying-and-using-azure-information-protection"></a>Déploiement et utilisation d’Azure Information Protection

Pour connaître les étapes de configuration d’Azure Information Protection dans cette solution, consultez [Protéger des fichiers SharePoint Online avec Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Solutions de sécurité](security-solutions.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Sécuriser les sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



