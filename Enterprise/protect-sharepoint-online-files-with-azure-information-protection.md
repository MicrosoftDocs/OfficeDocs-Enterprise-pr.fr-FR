---
title: "Protéger les fichiers SharePoint Online avec Azure Information Protection"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Résumé : S’appliquent à la Protection des informations Azure pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel."
ms.openlocfilehash: bc2c7dbbcc254270cf2c7db3d3eed98b3f7872f6
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Protéger les fichiers SharePoint Online avec Azure Information Protection

 **Résumé :** Appliquer la Protection des informations Azure pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel.
  
Utilisez les étapes de cet article pour configurer la Protection d’informations Azure pour fournir le cryptage et des autorisations pour les fichiers dans un site d’équipe SharePoint Online hautement confidentiel. La protection de chiffrement et d’autorisations se déplace avec un fichier même lorsqu’il est téléchargé à partir du site. Pour plus d’informations sur les sites d’équipe SharePoint Online hautement confidentielles, voir les [fichiers et les sites SharePoint Online de la sécuriser](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Lorsque le chiffrement Azure Information Protection est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter le contenu de ces fichiers. La co-création, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent uniquement fonctionner avec les métadonnées (y compris les étiquettes Office 365), mais pas le contenu de ces fichiers (par exemple, des numéros de cartes de crédit au sein des fichiers). 
  
Tout d’abord, suivez les instructions dans [RMS d’Azure activer avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) pour votre abonnement à Office 365.
  
Ensuite, configurez Azure Information Protection avec une nouvelle sous-étiquette et une nouvelle stratégie étendue pour la protection et les autorisations de votre site d’équipe SharePoint Online hautement confidentiel.
  
1. Connectez-vous au portail Office 365 avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un onglet séparé de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si c’est la première fois que vous configurez la Protection des informations Azure, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet liste, cliquez sur **plus de services**, tapez les **informations**, puis cliquez sur **Azure la Protection des informations**.
    
5. Sur la lame de **protection des informations d’Azure** , cliquez sur **stratégies de portée > + Ajouter une nouvelle stratégie**.
    
6. Dans **nom de stratégie** et d’une description dans la zone **Description**, tapez un nom pour la nouvelle stratégie.
    
7. Cliquez sur **Sélectionner les utilisateurs ou les groupes d’obtiennent cette stratégie > groupes d’utilisateurs**, et puis sélectionnez membres du site d’accès groupe pour votre site d’équipe SharePoint en ligne très sensible. 
    
8. Cliquez sur **Sélectionnez > OK**.
    
9. Pour l’étiquette **Hautement confidentielles** , cliquez sur le bouton de sélection (...), puis cliquez sur **Ajouter une étiquette secondaire**.
    
10. Dans un **nom** et une description de l’étiquette dans la zone **Description**, tapez un nom pour l’étiquette secondaire.
    
11. **Définir des autorisations pour les documents et messages électroniques contenant cette étiquette**, cliquez sur **protéger**.
    
12. Dans la section de la **Protection** , cliquez sur **Azure (clé de nuage)**.
    
13. Sur la lame de **Protection** , sous **paramètres de Protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Sur la blade **d’Ajouter les autorisations** , sous **spécifier les utilisateurs et groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **DAS utilisateurs et des groupes** , sélectionnez le groupe d’accès membres site de votre site d’équipe SharePoint en ligne très sensible, puis cliquez sur **Sélectionner**.
    
16. Sous **autorisations de choisir le paramètre prédéfini**, désactivez les cases à cocher **impression**, **copie et extraction de contenu**et **vers l’avant** .
    
17. Cliquez deux fois sur **OK** .
    
18. Sur la blade **d’étiquette secondaire** , cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Sur la lame de **protection des informations de Azure - stratégies étendues** , cliquez sur **Publier**.
    
Voici la configuration finale de votre site d’équipe SharePoint Online hautement confidentiel.
  
![Étiquette Azure Information Protection pour un site d’équipe SharePoint Online isolé.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Vous pouvez maintenant commencer à créer des documents et à les protéger avec Azure Information Protection et votre nouvelle étiquette.
  
Vous devez [installer le client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur votre périphérique ou votre ordinateur Windows. Vous pouvez créer un script et automatiser l’installation, ou si les utilisateurs peuvent installer le client manuellement. Consultez les ressources suivantes :
  
- [Le côté client de la Protection des informations Azure](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [L’installation du client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Page d’installation manuelle de téléchargement](https://www.microsoft.com/download/details.aspx?id=53018)
    
Une fois installé, vos utilisateurs exécutent et puis reconnectez-vous à partir d’une application Office (par exemple, Microsoft Word) avec son compte Office 365. Une nouvelle barre de **Protection des informations** permet aux utilisateurs de sélectionner la nouvelle étiquette. Assurez-vous que vos utilisateurs connaissent le site d’équipe SharePoint Online et qui d’étiquette à utiliser, pour protéger leurs fichiers hautement confidentielles.
  
> [!NOTE]
> Si vous possédez plusieurs sites d’équipe SharePoint Online hautement sensibles, vous devez créer plusieurs stratégies étendues Azure Information Protection avec des sous-étiquettes et les paramètres ci-dessus. Les autorisations de chaque sous-étiquette doivent être définies pour le groupe d’accès des membres d’un site d’équipe SharePoint Online spécifique.  
  
## <a name="see-also"></a>See Also

[Sécurisation des fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sites SharePoint en ligne sécurisés dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d'autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




