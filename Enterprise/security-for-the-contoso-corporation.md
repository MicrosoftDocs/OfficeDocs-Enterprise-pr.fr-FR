---
title: "Sécurité de Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "Résumé : Comprendre comment Contoso mappés aux impératifs de sécurité à des fonctions dans les offres en nuage de Microsoft et de déterminer un chemin d’accès vers le cloud d’évaluation de la sécurité."
ms.openlocfilehash: 4d38f58595f0043e1a02106b6428b92dabad2e17
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="security-for-the-contoso-corporation"></a>Sécurité de Contoso Corporation

 **Résumé :** Comprendre comment Contoso mappés aux impératifs de sécurité à des fonctions dans les offres en nuage de Microsoft et de déterminer un chemin d’accès vers le cloud d’évaluation de la sécurité.
  
Contoso est grave sur leur protection et la sécurité des informations. Lors de la transition de leur infrastructure informatique à un nuage-inclus, ils assuré que leurs exigences de sécurité sur site ont été pris en charge et mis en œuvre dans les offres en nuage de Microsoft.
  
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
    
## <a name="contosos-data-sensitivity-classification"></a>Classification de la sensibilité des données de Contoso

En utilisant les informations de Microsoft [Shared Computer Toolkit de Classification de données](https://msdn.microsoft.com/library/hh204743.aspx), Contoso a effectué une analyse de leurs données et déterminé les niveaux suivants.
  
|**Niveau 1 : Faible valeur commerciale**|**Niveau 2 : Valeur d’entreprise**|**Niveau 3 : Une valeur ajoutée élevée**|
|:-----|:-----|:-----|
|Les données sont cryptées et disponible uniquement aux utilisateurs authentifiés  <br/> Niveau accordé à toutes les données stockées localement et dans le cloud et aux charges de travail, telles qu’Office 365. Les données sont chiffrées lorsqu’elles se trouvent dans le service et lorsqu’elles transitent entre le service et les appareils clients.  <br/> Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique.  <br/> |Au niveau 1 plus forte protection contre les fuites d’authentification et de données  <br/> Authentification forte inclut une authentification multifacteur avec validation de SMS. Prévention des fuites de données garantit que les informations sensibles ou critiques ne circulent pas en dehors du réseau local.  <br/> Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits.  <br/> |Niveau 2 ainsi que les niveaux les plus élevés de cryptage, d’authentification et d’audit  <br/> Les plus hauts niveaux de cryptage pour données au repos et dans le cloud, conforme aux réglementations régionales, combinée avec une authentification multifacteur avec cartes à puce granulaire d’audit et d’alerte.  <br/> Les données de niveau 3 concernent, par exemple, les informations d’identification des clients et des partenaires, ainsi que les spécifications techniques de produits et les techniques de fabrication appartenant à l’entreprise.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Offres de cloud de Microsoft et les fonctionnalités de mappage à des niveaux de données de Contoso

Le tableau suivant décrit le mappage des niveaux de données de Contoso aux fonctionnalités dans les offres cloud de Microsoft :
  
||**SaaS**|**PaaS Azure**|**IaaS Azure**|
|:-----|:-----|:-----|:-----|
|Niveau 1 : valeur commerciale faible  <br/> | HTTPS pour toutes les connexions <br/>  Chiffrement des données stockées <br/> | Prend en charge uniquement les connexions HTTPS <br/>  Chiffrement des fichiers stockés dans Azure <br/> | Demander IPsec ou HTTPS pour accéder au serveur <br/>  Azure Disk Encryption <br/> |
|Niveau 2 : valeur commerciale moyenne  <br/> | Authentification multifacteur (MFA) Azure AD avec SMS <br/> | Utilisez Azure clé de coffre-fort pour les clés de cryptage <br/>  Azure AD MFA avec SMS <br/> | MFA avec SMS <br/> |
|Niveau 3 : valeur commerciale forte  <br/> | Système de gestion de droits Azure (RMS) <br/>  Azure AD MFA avec cartes à puce <br/>  Accès conditionnel Intune <br/> | Azure RMS <br/>  Azure AD MFA avec cartes à puce <br/> | MFA avec cartes à puce <br/> |
   
## <a name="contosos-information-policies"></a>Stratégies d’informations de Contoso

Le tableau suivant répertorie les stratégies de traitement des informations de Contoso.
  
||**Accès**|**Rétention des données**|**Protection des informations**|
|:-----|:-----|:-----|:-----|
|Niveau 1 : valeur commerciale faible  <br/> | Autoriser l’accès pour tous <br/> |6 mois  <br/> |Utiliser le chiffrement  <br/> |
|Niveau 2 : valeur commerciale moyenne  <br/> | Autoriser l’accès pour les employés, les sous-traitants et les partenaires de Contoso <br/>  Utiliser MFA, TLS et MAM <br/> |2 ans  <br/> |Utiliser les valeurs de hachage pour l’intégrité des données  <br/> |
|Niveau 3 : valeur commerciale forte  <br/> | Autoriser l’accès aux cadres dirigeants et les responsables dans l’ingénierie et de fabrication <br/>  RMS avec périphériques réseau gérés uniquement <br/> |7 ans  <br/> |Utiliser des signatures numériques pour la non-répudiation des données  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Chemin d’accès de Contoso cloud évaluation de la sécurité

Contoso a établi la procédure suivante pour préparer la sécurité du cloud de Microsoft :
  
1. Optimiser les comptes d’administrateur pour le nuage
    
    Contoso a effectué une révision complète des comptes Administrateur Windows Server AD existants et a configuré une série de groupes et de comptes Administrateurs dans le cloud.
    
2. Effectuer une analyse de classification de données en trois niveaux
    
    Contoso effectué un examen minutieux et déterminé les trois niveaux, qui a été utilisée pour déterminer le cloud de Microsoft offre des fonctionnalités visant à protéger les données les plus précieuses de Contoso.
    
3. Déterminer les stratégies de protection des informations, de rétention et d’accès pour les niveaux de données
    
    En fonction des niveaux de données, Contoso a déterminé des exigences précises, qui seront utilisées pour qualifier les futures charges de travail informatiques déplacées vers le cloud.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Utilisation de Contoso de meilleures pratiques de sécurité d’Office 365

Conformément à Office 365 meilleures pratiques de sécurité, les administrateurs de sécurité et le service informatique de Contoso ont déployé les éléments suivants :
  
- **Des comptes d’administrateur global avec des mots de passe très forts dédiés**
    
    Plutôt que d’assigner le rôle d’administrateur global pour les comptes d’utilisateurs de tous les jours, Contoso a créer trois, des comptes d’administrateur global avec des mots de passe très forts dédiés. La connexion avec un compte d’administrateur global est faite uniquement pour des tâches d’administration spécifiques et les mots de passe sont uniquement connus au personnel désigné. Administrateurs de la sécurité de Contoso ont attribué des rôles d’administrateur aux comptes appropriés à la fonction de travail de ce personnel et la responsabilité.
    
    Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **Plusieurs facteurs d’authentification (AMF) pour les comptes d’utilisateur important**
    
    AMF ajoute une couche de protection supplémentaire pour le processus de connexion en demandant aux utilisateurs accuser réception d’un appel téléphonique, un message de texte ou une notification de l’application sur leur téléphone intelligent après avoir correctement entré son mot de passe. Avec AMF, comptes d’utilisateurs Office 365 contre reconnectez-vous non autorisée même si un mot de passe du compte est compromis.
    
  - Protection contre un compromis de l’abonnement à Office 365, Contoso activé AMF sur tous les trois comptes d’administrateur global.
    
  - Pour vous protéger contre les attaques par phishing, dans lequel un attaquant compromet les informations d’identification d’une personne de confiance dans l’organisation et envoie les messages électroniques malveillants, Contoso activé AMF sur tous les comptes d’utilisateur pour les responsables, y compris le personnel de direction.
    
    Pour plus d’informations, reportez-vous à la section [planifier plusieurs facteurs d’authentification pour les déploiements d’Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **Gestion de la sécurité avancée (ASM)**
    
    ASM utilise configuré des stratégies pour surveiller une activité anormale. Configurer les alertes avec ASM afin que les administrateurs soient avertis inhabituels ou risqué d’activités des utilisateurs, telles que le téléchargement de grandes quantités de données, les administrateurs de sécurité Contoso Échec de plusieurs tentatives de connexion, ou des connexions à partir des adresses IP inconnus ou nuisibles
    
    Pour plus d’informations, consultez [Vue d’ensemble de gestion avancée de sécurité dans Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Flux de la messagerie électronique sécurisée et de boîte aux lettres de journal d’audit**
    
    Spécialistes de la sécurité Contoso utilisent Exchange Online Protection et Advanced Threat Protection (ATP) pour vous protéger contre les programmes malveillants inconnus, les virus et les URL malveillantes transmises par le biais de messages électroniques. Contoso dispose également d’audit de boîte aux lettres activée journalisation pour déterminer qui a ouvert une session dans les boîtes aux lettres de l’utilisateur, envoyés de messages et les autres activités effectuées par un administrateur, un utilisateur délégué ou du propriétaire de boîte aux lettres.
    
    Pour plus d’informations, voir : 
    
  - [Protection anti-Spam de messagerie Office 365](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Protection contre les menaces avancées des liens sécurisés et les pièces jointes sûres](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Activer l’audit de boîte aux lettres dans Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Data Loss Prevention (DLP)**
    
    Contoso a identifié ses données sensibles et configuré des stratégies DLP pour Exchange Online, SharePoint Online et OneDrive aider à empêcher les utilisateurs de partage des données accidentellement ou intentionnellement. 
    
    Pour plus d’informations, consultez [vue d’ensemble des stratégies de prévention de perte de données](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Meilleures pratiques de sécurité pour Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




