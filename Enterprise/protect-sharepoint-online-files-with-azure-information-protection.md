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
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Résumé : Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel."
ms.openlocfilehash: 5beba188cadc88c15ec75ed2adb4899d9b41b8ec
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Protéger les fichiers SharePoint Online avec Azure Information Protection

 **Résumé :** Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel.
  
Suivez les étapes décrites dans cet article pour configurer Azure Information Protection pour assurer le chiffrement et configurer les autorisations des fichiers d’un site d’équipe SharePoint Online hautement confidentiel. La protection du chiffrement et des autorisations accompagne un fichier même lorsqu’il est téléchargé à partir du site. Pour en savoir plus sur les sites d’équipe SharePoint Online hautement confidentiels, consultez la rubrique [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Lorsque le chiffrement Azure Information Protection est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter le contenu de ces fichiers. La co-création, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent uniquement fonctionner avec les métadonnées (y compris les étiquettes Office 365), mais pas le contenu de ces fichiers (par exemple, des numéros de cartes de crédit au sein des fichiers). 
  
Tout d’abord, suivez les instructions contenues dans [Activer Azure RMS avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) pour votre abonnement Office 365.
  
Ensuite, configurez Azure Information Protection avec une nouvelle sous-étiquette et une nouvelle stratégie étendue pour la protection et les autorisations de votre site d’équipe SharePoint Online hautement confidentiel.
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
5. Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.
    
6. Saisissez le nom de la nouvelle stratégie dans **Nom de la stratégie** et une description dans **Description**.
    
7. Cliquez sur **Sélectionnez les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateur/Groupes**, puis sélectionnez le groupe d’accès des membres de votre site d’équipe SharePoint Online hautement sensible.  
    
8. Cliquez sur **Sélectionner > OK**.
    
9. Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.
    
10. Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.
    
11. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
12. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
13. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **Utilisateurs et groupes AAD**, sélectionnez le groupe d’accès Membres de votre site d’équipe SharePoint Online hautement sensible, puis cliquez sur **Sélectionner**.
    
16. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.
    
17. Cliquez deux fois sur **OK**.
    
18. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Dans le panneau **Azure Information Protection – Stratégies étendues**, cliquez sur **Publier**.
    
Voici la configuration finale de votre site d’équipe SharePoint Online hautement confidentiel.
  
![Étiquette Azure Information Protection pour un site d’équipe SharePoint Online isolé.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Vous pouvez maintenant commencer à créer des documents et à les protéger avec Azure Information Protection et votre nouvelle étiquette.
  
Vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur votre périphérique ou votre ordinateur Windows. Vous pouvez créer un script et automatiser l’installation, ou les utilisateurs peuvent installer le client manuellement. Consultez les ressources suivantes :
  
- [Côté client d’Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Installation du client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Page de téléchargement de l’installation manuelle](https://www.microsoft.com/download/details.aspx?id=53018)
    
Une fois l’installation effectuée, vos utilisateurs exécutent une application Office (par exemple, Microsoft Word) pour se connecter avec leur compte Office 365. Une nouvelle barre **Information Protection** permet aux utilisateurs de sélectionner la nouvelle étiquette. Assurez-vous que vos utilisateurs connaissent le site d’équipe SharePoint Online et savent quelle étiquette utiliser, afin de protéger leurs fichiers hautement confidentiels.
  
> [!NOTE]
> Si vous possédez plusieurs sites d’équipe SharePoint Online hautement sensibles, vous devez créer plusieurs stratégies étendues Azure Information Protection avec des sous-étiquettes et les paramètres ci-dessus. Les autorisations de chaque sous-étiquette doivent être définies pour le groupe d’accès des membres d’un site d’équipe SharePoint Online spécifique. 
  
## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sécuriser les sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




