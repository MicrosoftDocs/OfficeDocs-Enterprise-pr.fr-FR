---
title: Sécurité de Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Résumé : Découvrez comment Contoso mappées leurs exigences de sécurité pour les fonctionnalités dans les offres de cloud de Microsoft et déterminez un chemin d’accès à la préparation de la sécurité en nuage.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914829"
---
# <a name="security-for-the-contoso-corporation"></a>Sécurité de Contoso Corporation

 **Résumé :** Comprendre comment Contoso mappées leurs exigences de sécurité pour les fonctionnalités dans les offres de cloud de Microsoft et déterminez un chemin d’accès à la préparation de la sécurité en nuage.
  
Contoso est grave sur leur sécurité des informations et de protection. Lors de la transition de leur infrastructure informatique sur un nuage-inclus, ils assurés que leurs exigences de sécurité locale ont été pris en charge et implémentés dans les offres de cloud de Microsoft.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>Exigences de sécurité de Contoso dans le nuage

Voici les exigences de sécurité de Contoso concernant le cloud :
  
- Authentification forte aux ressources du cloud
    
    L’accès aux ressources du cloud doit être authentifié, si possible, par le biais d’une authentification multifacteur.
    
- Chiffrement du trafic sur Internet
    
    Les données ne doivent jamais être envoyées en clair sur Internet. Utilisez toujours les connexions HTTPS, IPsec ou toute autre méthode de chiffrement des données de bout en bout.
    
- Chiffrement des données au repos dans le cloud
    
    Toutes les données doivent être chiffrées lorsqu’elles sont stockées sur des disques ou un autre emplacement dans le cloud.
    
- Listes de contrôle d’accès selon le principe des privilèges minimum
    
    Autorisations accordées aux comptes pour accéder aux ressources du cloud et limiter le nombre et l’étendue des actions conformément au principe de privilèges minimum.
    
## <a name="contosos-data-sensitivity-classification"></a>Classification de sensibilité des données de Contoso

Utilisation des informations de Microsoft du [Kit de ressources de classification des données](https://msdn.microsoft.com/library/hh204743.aspx), Contoso effectué une analyse de leurs données et déterminé les niveaux suivants.
  
|**Niveau 1 : valeur commerciale faible**|**Niveau 2 : valeur commerciale moyenne**|**Niveau 3 : valeur commerciale forte**|
|:-----|:-----|:-----|
|Les données sont chiffrées et accessibles uniquement par les utilisateurs authentifiés

  <br/> Niveau accordé à toutes les données stockées localement et dans le cloud et aux charges de travail, telles qu’Office 365. Les données sont chiffrées lorsqu’elles se trouvent dans le service et lorsqu’elles transitent entre le service et les appareils clients.  <br/> Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique.  <br/> |Niveau 1 avec une authentification et une protection renforcées contre la perte de données
  <br/> Une authentification forte est une authentification multifacteur avec validation SMS. La protection contre la perte de données permet de s’assurer que les informations sensibles ou critiques ne circulent pas à l’extérieur du réseau local.
  <br/> Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits.  <br/> |Niveau 2 avec des niveaux de chiffrement, d’authentification et d’audit plus élevés
  <br/> Niveaux de chiffrement des données au repos et dans le cloud les plus élevés, conformes aux réglementations locales, associés à une authentification multifacteur des cartes à puce et aux fonctionnalités d’audit et d’alerte ciblées.
  <br/> Les données de niveau 3 concernent, par exemple, les informations d’identification des clients et des partenaires, ainsi que les spécifications techniques de produits et les techniques de fabrication appartenant à l’entreprise.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Mappage des fonctionnalités et des offres de cloud Microsoft aux niveaux de données de Contoso

Le tableau suivant décrit le mappage des niveaux de données de Contoso aux fonctionnalités dans les offres cloud de Microsoft :
  
||**SaaS**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|Niveau 1 : valeur commerciale faible  <br/> | HTTPS pour toutes les connexions
 <br/>  Chiffrement des données stockées <br/> | Prise en charge des connexions HTTPS uniquement
 <br/>  Chiffrement des fichiers stockés dans Azure <br/> | HTTPS ou IPsec requis pour accéder au serveur
 <br/>  Azure Disk Encryption <br/> |
|Niveau 2 : valeur commerciale moyenne  <br/> | Authentification multifacteur (MFA) Azure AD avec SMS <br/> | Utilisation d’Azure Key Vault pour les clés de chiffrement
 <br/>  Azure AD MFA avec SMS <br/> | MFA avec SMS <br/> |
|Niveau 3 : valeur commerciale forte  <br/> | Azure Rights Management System (RMS)

 <br/>  Azure AD MFA avec cartes à puce <br/>  Accès conditionnel Intune <br/> | Azure RMS <br/>  Azure AD MFA avec cartes à puce <br/> | MFA avec cartes à puce <br/> |
   
## <a name="contosos-information-policies"></a>Stratégies des informations de Contoso

Le tableau suivant répertorie les stratégies de traitement des informations de Contoso.
  
||**Accès**|**Rétention des données**|**Protection des informations**|
|:-----|:-----|:-----|:-----|
|Niveau 1 : valeur commerciale faible  <br/> | Autoriser l’accès pour tous <br/> |6 mois  <br/> |Utiliser le chiffrement  <br/> |
|Niveau 2 : valeur commerciale moyenne  <br/> | Autoriser l’accès aux collaborateurs, aux sous-traitants et aux partenaires de Contoso
 <br/>  Utiliser MFA, TLS et MAM <br/> |2 ans  <br/> |Utiliser les valeurs de hachage pour l’intégrité des données  <br/> |
|Niveau 3 : valeur commerciale forte  <br/> | Autoriser l’accès aux cadres et aux responsables des équipes techniques et de fabrication
 <br/>  RMS avec périphériques réseau gérés uniquement <br/> |7 ans  <br/> |Utiliser des signatures numériques pour la non-répudiation des données  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Chemin d’accès de Contoso à l’évaluation de la sécurité dans le nuage

Contoso a établi la procédure suivante pour préparer la sécurité du cloud de Microsoft :
  
1. Optimiser les comptes Administrateur pour le cloud

    
    Contoso a effectué une révision complète des comptes Administrateur Windows Server AD existants et a configuré une série de groupes et de comptes Administrateurs dans le cloud.
    
2. Classer les données selon trois niveaux

    
    Contoso effectué une étude critique et déterminé les trois niveaux, qui a été utilisée pour déterminer le cloud Microsoft offre des fonctionnalités visant à protéger les données stratégiques de Contoso.
    
3. Déterminer les stratégies d’accès, de conservation et de protection des informations pour les niveaux de données

    
    En fonction des niveaux de données, Contoso a déterminé des exigences précises, qui seront utilisées pour qualifier les futures charges de travail informatiques déplacées vers le cloud.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Utilisation de Contoso de meilleures pratiques de sécurité Office 365

Conformément aux Office 365 meilleures pratiques de sécurité administrateurs de sécurité et le service informatique de Contoso ont déployé les éléments suivants :
  
- **Des comptes d’administrateur global par mot de passe fort très dédiés**
    
    Au lieu d’attribuer le rôle d’administrateur global aux comptes d’utilisateur de tous les jours, Contoso a créer trois, des comptes d’administrateur global par mot de passe fort très dédiés. Connexion avec un compte d’administrateur global est effectuée uniquement pour les tâches d’administration spécifiques et les mots de passe sont uniquement connus au personnel désigné. Administrateurs de la sécurité de Contoso disposent des rôles d’administrateur aux comptes appropriés à la fonction de cette personne informatique et responsabilité.
    
    Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **Authentification multifacteur (MFA) pour les comptes d’utilisateur importantes**
    
    MFA ajoute une couche de protection supplémentaire à la procédure de connexion en demandant aux utilisateurs à remercier un appel téléphonique, message texte ou une notification de l’application sur leur téléphone active après avoir entré correctement leur mot de passe. Avec MFA, comptes d’utilisateurs Office 365 sont protégés contre de connexion non autorisée, même si un mot de passe est compromis.
    
  - Pour vous protéger contre une compromission de l’abonnement à Office 365, Contoso activé MFA sur tous les trois comptes d’administrateur global.
    
  - Pour vous protéger contre les attaques par hameçonnage, dans laquelle une personne malveillante compromet les informations d’identification d’une personne dans l’organisation approuvée et envoie un message électronique malveillant, Contoso activé MFA sur tous les comptes d’utilisateur pour les responsables, y compris les cadres.
    
    Pour plus d’informations, voir [planifier l’authentification multifacteur pour les déploiements d’Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **Gestion des fonctions avancées de sécurité (ASM)**
    
    ASM utilise configuré les stratégies pour surveiller l’activité anormale. Définir des alertes avec ASM afin que les administrateurs informatiques sont avertis inhabituelle ou risque d’activités des utilisateurs, telles que le téléchargement de grandes quantités de données, les administrateurs de sécurité Contoso Échec de plusieurs tentatives de connexion ou des connexions à partir des adresses IP inconnus ou dangereuses
    
    Pour plus d’informations, voir [Vue d’ensemble de gestion avancées de sécurité dans Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Enregistrement d’audit de boîtes aux lettres et flux de messagerie sécurisée**
    
    Spécialistes de la sécurité Contoso utilisent Exchange Online Protection et Protection de menace avancées (DAV) pour protéger contre les programmes malveillants inconnus, les virus et les URL malveillantes transmis par le biais de messages électroniques. Contoso a également activé enregistrement d’audit pour déterminer qui a ouvert une session dans les boîtes aux lettres utilisateur, envoyés de messages et d’autres activités effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur.
    
    Pour plus d'informations, consultez les rubriques suivantes : 
    
  - [Protection contre le courrier indésirable pour Office 365](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Protection avancée contre les menaces pour les pièces jointes et liens fiables](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Activer l’audit de boîte aux lettres dans Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Protection contre la perte de données (DLP)**
    
    Contoso a identifié ses données sensibles et configuré les stratégies DLP pour Exchange Online, SharePoint Online et OneDrive empêcher les utilisateurs d’accidentellement ou intentionnellement partage des données. 
    
    Pour plus d’informations, reportez-vous à [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)

  
[Meilleures pratiques de sécurité pour Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




