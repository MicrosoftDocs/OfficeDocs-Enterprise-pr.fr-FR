---
title: "Protéger les fichiers SharePoint Online avec Azure la Protection des informations"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/16/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
---

# Protéger les fichiers SharePoint Online avec Azure la Protection des informations

 **Résumé :** Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d'un site d'équipe SharePoint Online hautement confidentiel.
  
Suivez les étapes décrites dans cet article pour configurer Azure Information Protection pour assurer le chiffrement et configurer les autorisations des fichiers d'un site d'équipe SharePoint Online hautement confidentiel. La protection du chiffrement et des autorisations accompagne un fichier même lorsqu'il est téléchargé à partir du site. Pour en savoir plus sur les sites d'équipe SharePoint Online hautement confidentiels, consultez la rubrique [Sécurisation des fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
Avant de commencer, suivez les instructions de l'article [Comment activer Azure Rights Management à partir du centre d'administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) selon l'abonnement Office 365 que vous avez souscrit.
  
Ensuite, configurez l'étiquette Azure Information Protection - Hautement confidentiel avec la protection et les autorisations destinées à votre site d'équipe SharePoint Online hautement confidentiel.
  
1. Connectez-vous au portail Office 365 avec un compte qui possède le rôle d'administrateur de sécurité ou l'administrateur de la société. Pour obtenir de l'aide, consultez [permettant de se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un onglet séparé de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
4. Dans le panneau **Azure Information Protection - Stratégie globale**, cliquez sur **Hautement confidentiel** dans la liste des étiquettes.
    
5. Dans le panneau **Étiquette : Hautement confidentiel**, cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
6. Dans la section **Protection**, cliquez sur **Azure RMS**.
    
7. Dans le panneau **Protection**, cliquez sur **+ Ajouter des autorisations** sous **Paramètres de protection**.
    
8. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
9. Dans le volet **DAS utilisateurs et des groupes**, sélectionnez le groupe d'accès membres site de votre site d'équipe SharePoint en ligne très sensible, puis cliquez sur **Sélectionner**.
    
10. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer**, **Copier et extraire le contenu** et **Transférer**.
    
11. Cliquez deux fois sur **OK**.
    
12. Dans le panneau **Étiquette : Hautement confidentiel**, cliquez sur **Enregistrer**.
    
13. Dans le panneau **Azure Information Protection - Stratégie globale**, cliquez sur **Publier**.
    
Il s'agit de votre configuration résultante de votre site d'équipe SharePoint Online hautement confidentiel.
  
![Étiquette Azure Information Protection pour un site d'équipe SharePoint Online isolé.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Vous pouvez maintenant commencer à créer des documents et à les protéger avec Azure Information Protection et l'étiquette Hautement confidentiel.
  
Vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur votre périphérique ou votre ordinateur Windows. Vous pouvez créer un script et automatiser l'installation, ou les utilisateurs peuvent installer le client manuellement. Consultez les ressources suivantes :
  
- [Côté client d'Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Installation du client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Page de téléchargement pour l'installation manuelle](https://www.microsoft.com/download/details.aspx?id=53018)
    
Une fois installé, vos utilisateurs exécutent une application Office (par exemple, Microsoft Word) pour se connecter avec leur compte Office 365. Une nouvelle barre d'outils **Critère de diffusion** vous permet de sélectionner l'étiquette **Hautement confidentiel**. Assurez-vous que vos utilisateurs connaissent le site d'équipe SharePoint Online pour stocker leurs fichiers hautement confidentiels.
  
> [!NOTE]
> Si vous avez plusieurs sites d'équipe SharePoint en ligne très sensibles, vous devez créer plusieurs étiquettes de Protection des informations Azure avec les paramètres ci-dessus, avec les autorisations pour chaque étiquette définie au groupe d'accès site membres d'une équipe SharePoint en ligne spécifique site.
  
## See Also

#### 

[Sécurisation des fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sécuriser les sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d'autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

