---
title: "Diagramme accessible  Options de plateforme Microsoft Lync 2013"
ms.author: v-suboh
author: v-suboh
ms.date: 1/27/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: "Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Lync 2013, qui est disponible dans la rubrique Diagrammes techniques."
---

# Diagramme accessible : Options de plateforme Microsoft Lync 2013

Cet article est une version texte accessible du diagramme intitulé Options de plateforme Microsoft Lync 2013, qui est disponible dans la rubrique [Diagrammes techniques](http://go.microsoft.com/fwlink/?LinkID=519139).
  
Cette affiche décrit ce que les architectes et les décideurs d'entreprise (BDM) doivent savoir sur les déploiements Lync Online (Office 365) et Lync Server et inclut :
  
- Une comparaison de quatre options de déploiement : Lync Online (Office 365), hybride Lync Online/Server, Lync Server et Lync Server hébergé par le fournisseur. 
    
- Deux exemples de scénarios de déploiement de Lync 2013.
    
## Une comparaison de quatre déploiements distincts pour la plateforme Lync 2013.

La comparaison fournit des informations sur chaque option de déploiement dans les sections suivantes :
  
- Une vue d'ensemble des différentes fonctionnalités de déploiement
    
- Avantages de l'implémentation de chaque option de déploiement
    
- Critères de licence
    
- Tâches architecturales requises
    
- Responsabilités des professionnels informatiques pour l'implémentation de chaque option de déploiement
    
### Vue d'ensemble

#### Lync Online (Office 365)

Gagnez en efficacité et optimisez les coûts avec les plans partagés au sein d'une architecture mutualisée de Office 365.
  
Le schéma associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de compte entre l'environnement local des services de domaine Active Directory et le client Azure Active Directory. 
  
Description des fonctions et fonctionnalités :
  
- Software as a Service (SaaS).
    
- L'ensemble riche de fonctionnalités est toujours à jour.
    
- Comprend un client Azure Active Directory pour les comptes en ligne, qui peut être utilisé avec d'autres applications. 
    
- L'intégration Directory comprend la synchronisation des mots de passe et des noms de compte entre l'environnement des services de domaine Active Directory et le client Azure Active Directory.
    
- Si l'authentification unique (SSO) est une exigence, les services ADFS (Active Directory Federation Services) doivent être implémentés. 
    
- La communication client sur Internet est chiffrée et authentifiée.
    
- La connectivité à l'équipement téléphonique hérité (réseau téléphonique commuté) est disponible par le biais de fournisseurs tiers.
    
#### Déploiement hybride Lync Online/Server (domaine séparé)

Vous pouvez associer les avantages d'Office 365 à un déploiement local de Lync 2013.
  
Le diagramme associé représente Office 365 avec Lync Online où certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne. Un serveur Edge déployé local est également représenté.
  
Description des fonctions et fonctionnalités :
  
- Certains utilisateurs sont hébergés localement et d'autres sont hébergés en ligne, mais ils partagent tous le même domaine SIP (contoso.com, par exemple).
    
- Utilisez votre infrastructure Lync Server 2013 existante, notamment les connexions au réseau téléphonique commuté (RTC).
    
- Ajoutez de nouveaux utilisateurs Lync Online facilement lorsqu'ils n'ont pas besoin du RTC.
    
- Migrez progressivement de Lync en local vers Lync Online, selon votre planification.
    
- Intégrez d'autres applications Office 365, y compris Exchange Online et SharePoint Online.
    
#### Lync Server

Dans ce déploiement, vous êtes propriétaire de tous les éléments. Le diagramme associé présente une infrastructure Lync Server avec un environnement local des services de domaine Active Directory dans lequel les utilisateurs sont hébergés localement.
  
Description des fonctions et fonctionnalités :
  
- Planification et dimensionnement de la capacité.
    
- Configuration et acquisition du serveur.
    
- Déploiement.
    
- Mise à l'échelle, mise à jour corrective et opérations.
    
- Sauvegarde des données.
    
- Maintenance du basculement et de la récupération d'urgence.
    
- Connexion de l'infrastructure Lync Server 2013 au RTC
    
- Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).
    
#### Lync Server hébergé par le fournisseur

Dans ce déploiement, votre fournisseur possède tous les éléments. Le diagramme associé représente le réseau d'un fournisseur comprenant ses serveurs et équipement avec une connexion à un environnement local.
  
Description des fonctions et fonctionnalités :
  
- Planification et dimensionnement de la capacité.
    
- Configuration et acquisition du serveur.
    
- Déploiement.
    
- Mise à l'échelle, mise à jour corrective et opérations.
    
- Sauvegarde des données.
    
- Maintenance du basculement et de la récupération d'urgence.
    
- Intégration à des équipements téléphoniques existants, tels que des autocommutateurs privés (PBX).
    
- Par ailleurs, le fournisseur peut :
    
  - Installer ses serveurs et équipements dans son propre réseau à l'aide d'une connexion à votre réseau local (trait plein).
    
  - Installer ses serveurs sur votre réseau local (ligne en pointillés).
    
### Avantages de l'implémentation de chaque option de déploiement

#### Lync Online (Office 365)

- Aucune charge de fonctionnement liée aux serveurs locaux ou aux logiciels serveur.
    
- Fonctionnalités de communication de Lync Server 2013 en tant que service cloud.
    
- Fonctionnalités de présence, de messagerie instantanée, d'appels audio et vidéo, de réunions en ligne denses et de conférences sur le web.
    
- Utilisées pour les organisations dispersées sur le plan géographique ou dont les employés principalement mobiles.
    
#### Déploiement hybride Lync Online/Server (domaine séparé)

- Utilisez Lync Online pour les utilisateurs distants et l'intégration avec des partenaires commerciaux.
    
- Facilitez une migration à partir de Lync en local vers Lync Online.
    
- Prenez en charge des sites distants sans utiliser l'équipement d'une filiale.
    
- Ajoutez facilement la prise en charge de Lync dans les nouvelles acquisitions d'entreprise.
    
#### Lync Server

- Solutions de cloud privées.
    
- Les solutions hautement personnalisées.
    
- Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.
    
- Restrictions de confidentialité qui empêchent la synchronisation des comptes AD DS avec Office 365.
    
- Organisations qui souhaitent bénéficier du contrôle de l'ensemble de la plateforme et de la solution.
    
- Remplacement de PBX par Voix Entreprise de Lync.
    
#### Lync Server hébergé par le fournisseur

- Organisations qui veulent bénéficier des fonctionnalités de Lync Server mais qui souhaitent externaliser leur déploiement et leur maintenance.
    
- Solutions fournisseur.
    
- Les solutions hautement personnalisées.
    
- Solutions héritées avec composants tiers qui dépendent du matériel et des logiciels non pris en charge par Lync Online.
    
- Remplacement de PBX par Voix Entreprise de Lync.
    
### Critères de licence

#### Lync Online (Office 365)

Modèle d'abonnement.
  
#### Déploiement hybride Lync Online/Server (domaine séparé)

- Office 365  Modèle d'abonnement. Aucune licence supplémentaire nécessaire. 
    
- Local  Toutes les licences locales s'appliquent. 
    
#### Lync Server

- Système d'exploitation du serveur
    
- SQL Server
    
- Licence de serveur Lync 2013
    
- Licence d'accès au client Lync 2013
    
#### Lync Server hébergé par le fournisseur

Les coûts dépendent de l'accord conclu avec votre fournisseur de la solution Lync.
  
### Tâches d'architecture

Cette section répertorie les tâches d'architecture pour chaque option de déploiement.
  
#### Lync Online (Office 365)

- Planifier et concevoir la synchronisation d'annuaires.
    
- Garantir la capacité et la disponibilité du réseau grâce à des pare-feu, des serveurs proxy, des passerelles et des liaisons WAN.
    
- Acquérir des certificats SSL tiers pour fournir une sécurité d'entreprise pour les offres de service Office 365.
    
- Décider si vous souhaitez vous connecter à Office 365 en utilisant le protocole IPv6.
    
#### Déploiement hybride Lync Online/Server (domaine séparé)

En plus des tâches pour les environnements Office 365 et locaux :
  
- Déterminez les besoins en matière d'intégration de fonctionnalités avec les versions locales et en ligne d'Exchange Server et de SharePoint.
    
- Si nécessaire, déterminez le périphérique de serveur proxy à utiliser pour les demandes provenant de Office 365.
    
#### Lync Server

Concevez l'environnement Lync dans un environnement local existant :
  
- Topologie Lync pour les filiales et les bureaux principaux.
    
- Matériel de serveur, y compris la virtualisation.
    
- Intégration avec les services de domaine Active Directory et le DNS.
    
- Équilibrage de charge pour les pools de serveurs Lync.
    
- Basculement et récupération d'urgence.
    
#### Lync Server hébergé par le fournisseur

- Pour une installation informatique, déterminez la connexion au réseau du fournisseur de services.
    
- Pour une installation locale, déterminez l'emplacement des serveurs Lync du fournisseur sur votre réseau.
    
- Pour les deux types d'installation, déterminez l'intégration avec AD DS et votre équipement PBX.
    
### Responsabilités des professionnels de l'informatique

Cette section répertorie les responsabilités des professionnels de l'informatique pour chaque option de déploiement.
  
#### Lync Online (Office 365)

Déployez et gérez Lync Online (Office 365) :
  
- Implémentation du plan de synchronisation d'annuaires.
    
- Planification et implémentation du routage et des enregistrements DNS internes et externes.
    
- Configurez le proxy ou pare-feu pour l'adresse IP Office 365 et les exigences d'URL.
    
- Gérez les comptes d'utilisateurs et les paramètres Lync Online.
    
#### Déploiement hybride Lync Online/Server (domaine séparé)

En plus des tâches pour les environnements Office 365 et locaux :
  
- Configurez le périphérique de serveur proxy, si nécessaire.
    
- Configurez l'intégration de fonctionnalités avec les versions locales et en ligne d'Exchange Server et de SharePoint.
    
#### Lync Server

Déployez et gérez Lync Server dans un environnement local :
  
- Configuration des serveurs.
    
- Déployez la topologie de Lync.
    
- Mettez à jour les serveurs Lync.
    
- Ajoutez ou supprimez des serveurs de topologie en fonction de l'utilisation.
    
- Implémentez l'environnement de basculement et de récupération d'urgence.
    
#### Lync Server hébergé par le fournisseur

Collaborez avec le fournisseur pour :
  
- Intégrer Lync Server à votre réseau.
    
- Intégrer Lync Server avec d'autres produits ou solutions personnalisées Microsoft.
    
- S'assurer que le contrat de niveau de service (SLA) du fournisseur est respecté.
    
## Deux exemples de scénarios de déploiement de Lync 2013

### Composants de la synchronisation d'annuaires dans Microsoft Azure

Le déploiement des composants de synchronisation d'annuaires Office 365 dans Azure est plus rapide grâce à la capacité de déploiement de machines virtuelles à la demande.
  
Le diagramme associé présente Lync Online avec un client Azure Active Directory qui synchronise les mots de passe et les noms de comptes entre l'environnement local Active Directory et le client Azure Active Directory.
  
 **Serveur de synchronisation d'annuaires uniquement**. Plutôt que de déployer le serveur de synchronisation d'annuaires 64 bits dans votre environnement local, mettez en service une machine virtuelle dans Azure sur Internet.
  
 **Synchronisation d'annuaires + AD FS**. Cette option vous permet de prendre en charge les identités fédérées Office 365 (SSO) sans ajouter de matériel à votre infrastructure locale. Elle fournit également la résilience si l'environnement Active Directory local n'est pas disponible. Les fonctionnalités de cette option sont les suivantes :
  
- Composants d'intégration d'annuaire exécutés en tant que machines virtuelles Azure.
    
- AD FS est publié sur Internet par le biais de proxies AD FS s'exécutant en tant que machines virtuelles Azure.
    
- Le trafic d'authentification du client, pour les utilisateurs qui se connectent à partir de n'importe quel endroit, est géré par les serveurs et les proxies AD FS qui sont déployés en tant que machines virtuelles Azure.
    
### Intégration de Lync avec Exchange et SharePoint dans Office 365

#### Lync Server avec Exchange Online et SharePoint Online

Le diagramme associé représente Office 365 avec Exchange Online et SharePoint Online connectés à une batterie de serveurs Lync Server 2013 locale.
  
Ce déploiement offre les possibilités suivantes :
  
- Utiliser l'intégralité des fonctionnalités de Lync Server 2013.
    
- Utiliser vos équipements téléphoniques existants, tels que les PBX.
    
- Utiliser Exchange Online pour la messagerie, l'allègement de la charge des serveurs de messagerie et de l'espace de stockage local.
    
- Utiliser SharePoint Online pour la collaboration, l'allègement de la charge de maintenance des serveurs SharePoint locaux.
    
- Utiliser les fonctionnalités intégrées de Lync, d'Exchange et de SharePoint, notamment la messagerie unifiée dans Office 365.
    
#### Exchange Server avec Lync Online

Le diagramme associé représente Office 365 avec Lync Online connecté à une batterie de serveurs Exchange Server locale.
  
Ce déploiement offre les possibilités suivantes :
  
- Utiliser votre infrastructure Exchange existante.
    
- Utiliser Lync Online pour les fonctionnalités de présence, de messagerie instantanée et de conférence.
    

