---
title: "Déployer la synchronisation d’annuaires (DirSync) Office 365 dans Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "Résumé : Déployez Azure AD Connect (DirSync) sur une machine virtuelle dans Azure pour synchroniser les comptes entre votre répertoire local et le client Azure AD de votre abonnement Office 365."
ms.openlocfilehash: c6ee337c49092ac5d2b3d30a54fc33b3f3e2bb58
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a>Déployer la synchronisation d’annuaires (DirSync) Office 365 dans Microsoft Azure

 **Résumé :** Déployez Azure AD Connect (DirSync) sur une machine virtuelle dans Azure pour synchroniser les comptes entre votre répertoire local et le client Azure AD de votre abonnement Office 365.
  
Azure Active Directory (AD) Connect (auparavant appelé outil de synchronisation d'annuaires ou outil DirSync.exe) est une application serveur à installer sur un serveur appartenant à un domaine pour synchroniser vos utilisateurs Windows Server Active Directory locaux sur le client Azure Active Directory de votre abonnement Office 365. Vous pouvez installer Azure AD Connect sur un serveur local, mais également sur une machine virtuelle dans Azure, pour les raisons suivantes :
  
- Vous pouvez mettre en service et configurer les serveurs cloud plus rapidement, les rendant ainsi disponibles plus tôt pour vos utilisateurs.
    
- Azure offre une meilleure disponibilité de site avec moins d'efforts.
    
- Vous pouvez réduire le nombre de serveurs locaux de votre organisation.
    
> [!IMPORTANT]
> Cette solution exige une connectivité entre votre réseau local et votre réseau virtuel Azure. Pour plus d'informations, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!IMPORTANT]
> Cet article décrit la synchronisation d'un domaine unique dans une forêt unique. Azure AD Connect synchronise tous les domaines Windows Server AD dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, voir l'article sur le [scénario de synchronisation d'annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
> [!NOTE]
> Office 365 utilise Azure Active Directory (Azure AD) pour son service d'annuaire. Votre abonnement à Office 365 comprend un client Azure AD. Ce client peut également être utilisé pour la gestion des identités de votre organisation avec d'autres charges de travail de cloud, y compris d'autres applications SaaS et des applications dans Azure. 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Vue d’ensemble du déploiement de la synchronisation d’annuaires Office 365 dans Azure
<a name="Overview"> </a>

Le diagramme suivant montre Azure connexion AD en cours d'exécution sur une machine virtuelle dans Azure (le serveur de synchronisation d'annuaire) qui synchronise une forêt de Windows Server, Active Directory sur site d'un abonnementOffice 365.
  
![Outil Azure AD Connect sur une machine virtuelle dans Azure synchronisant des comptes Azure locaux sur le client Azure AD d’un abonnement Office 365 avec le flux de trafic](images/CP_DirSyncOverview.png)
  
Dans le diagramme, il y a deux réseaux reliés par une connexion de site à site VPN ou ExpressRoute. Il existe un réseau local où se trouvent les contrôleurs de domaine Windows Server Active Directory et un réseau virtuel est Azure avec un serveur de synchronisation d'annuaire, qui est une machine virtuelle exécutant [Azure Connect de AD](https://www.microsoft.com/download/details.aspx?id=47594). Il existe deux flux de trafic principal à partir du serveur de synchronisation d'annuaire d'origine :
  
-  Azure AD Connect interroge un contrôleur de domaine sur le réseau local concernant les modifications apportées aux comptes et aux mots de passe.
    
-  Azure AD Connect envoie les modifications apportées aux comptes et aux mots de passe à l'instance Azure AD de votre abonnement Office 365. Le serveur DirSync étant situé dans une partie étendue de votre réseau local, ces modifications sont envoyées par le biais du serveur proxy du réseau local.
    
> [!NOTE]
> Cette solution décrit la synchronisation d'un domaine Active Directory unique dans une forêt Active Directory unique. Azure AD Connect synchronise tous les domaines Active Directory dans votre forêt Active Directory avec Office 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Office 365, reportez-vous à l'article sur le [scénario de synchronisation d'annuaires à plusieurs forêts avec authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
Dans les deux cas, le trafic provenant d'Azure AD Connect en cours d'exécution sur la machine virtuelle Azure est transféré vers une passerelle sur le réseau virtuel dans Azure, qui transfert ensuite le trafic via la connexion VPN ou ExpressRoute de site à site au périphérique de passerelle VPN sur le réseau local. L'infrastructure de routage du réseau local transfert par la suite le trafic à sa destination, par exemple un contrôleur de domaine ou un serveur proxy.
  
Le déploiement de cette solution comporte deux étapes principales :
  
1. La création d'un réseau virtuel Azure et l'établissement d'une connexion VPN de site à site vers votre réseau local. Pour plus d'informations, voir [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. L'installation d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) sur une machine virtuelle appartenant à un domaine dans Azure, puis la synchronisation de Windows Server AD local avec Office 365. Cela implique les étapes suivantes :
    
    Création d'un Ordinateur virtuel Azure pour exécuter Azure AD Connect.
    
    Installation et configuration d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    La configuration d'Azure AD Connect exige les informations d'identification (nom d'utilisateur et mot de passe) d'un compte d'administrateur Azure AD et d'un compte d'administrateur d'entreprise Windows Server AD. Azure AD Connect est exécuté immédiatement et régulièrement pour synchroniser la forêt Windows Server AD locale avec Office 365.
    
Avant de déployer cette solution en production, suivez les instructions dans [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md) pour définir cette configuration comme une preuve de concept, de démonstrations ou d'expérimentation.
  
> [!IMPORTANT]
> Une fois la configuration d’Azure AD Connect terminée, les informations d’identification de compte d’administrateur d’entreprise Windows Server AD ne sont pas enregistrées. 
  
> [!NOTE]
> Cette solution décrit la synchronisation d'une seule forêt Active Directory de Windows Server à Office 365. La topologie décrite dans cet article ne représente qu'un seul moyen de mettre en œuvre cette solution. La topologie de votre organisation peut-être différer en fonction de vos besoins réseau unique et les considérations sur la sécurité. 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a>Planification de l’hébergement d’un serveur DirSync pour Office 365 dans Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Conditions préalables

Avant de commencer, passez en revue les conditions préalables suivantes pour cette solution :
  
- Examinez le contenu de planification associé dans [Planification de votre réseau Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).
    
- Veillez à respecter toutes les [conditions préalables](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) pour la configuration du réseau virtuel Azure.
    
- Vous devez disposer d'un abonnement Office 365 qui inclut la fonctionnalité d'intégration Active Directory. Pour plus d'informations sur les abonnements Office 365, accédez à la [page d'abonnement Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).
    
- Vous devez configurer un Ordinateur virtuel Azure qui exécute Azure AD Connect pour synchroniser votre forêt Windows Server AD locale avec Office 365.
    
    Vous devez disposer des informations d'identification (noms et mots de passe) d'un compte d'administrateur d'entreprise Windows Server AD et d'un compte d'administrateur Active Directory Azure.
    
### <a name="solution-architecture-design-assumptions"></a>Hypothèses en matière de conception de l’architecture de la solution

La liste suivante décrit les choix de conception effectués pour cette solution.
  
- Cette solution utilise un seul réseau virtuel Azure avec une connexion VPN de site à site. Le réseau virtuel Azure héberge un sous-réseau unique qui contient un serveur, le serveur DirSync qui exécute Azure AD Connect. 
    
- Sur le réseau local, un contrôleur de domaine et des serveurs DNS existent.
    
- Azure AD Connect exécute la synchronisation de mot de passe à la place de l'authentification unique. Il est inutile de déployer une infrastructure AD FS (Active Directory Federation Services). Pour plus d'informations sur les options de synchronisation de mot de passe et d'authentification unique, voir [Scénarios d'intégration d'annuaire](https://go.microsoft.com/fwlink/p/?LinkId=393094).
    
Il existe des choix de conception supplémentaires que vous pourriez envisager lorsque vous déployez cette solution dans votre environnement. Ceux-ci incluent notamment :
  
- Si un réseau virtuel Azure existant comporte des serveurs DNS, déterminez si vous voulez que votre serveur DirSync les utilise pour la résolution de noms à la place des serveurs DNS sur le réseau local.
    
- Si un réseau virtuel Azure existant comporte des contrôleurs de domaine, déterminez si la configuration des services et sites Active Directory peut être une meilleure option pour vous. Le serveur DirSync peut interroger les contrôleurs de domaine dans le réseau virtuel Azure pour rechercher des modifications des comptes et des mots de passe à la place des contrôleurs de domaine sur le réseau local.
    
## <a name="deployment-roadmap"></a>Feuille de route de déploiement
<a name="DeploymentRoadmap"> </a>

Le déploiement d'Azure AD Connect sur une machine virtuelle dans Azure se compose de trois phases :
  
- Phase 1 : créer et configurer le réseau virtuel Azure
    
- Phase 2 : créer et configurer les machines virtuelles Azure
    
- Phase 3 : installer et configurer Azure AD Connect
    
Après le déploiement, vous devez également affecter des emplacements et des licences pour les nouveaux comptes d’utilisateur dans Office 365.
  
> [!TIP]
> Le [serveur DirSync du kit de déploiement Azure]((https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)) contient tous les blocs PowerShell Azure pour créer cette solution, les diagrammes au format Microsoft PowerPoint et Visio et un classeur de configuration Microsoft Excel qui génère des blocs de commandes PowerShell Azure correspondant à vos paramètres.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Phase 1 : créer et configurer le réseau virtuel Azure

Pour créer et configurer le réseau virtuel Azure, effectuez la [phase 1 en préparant votre réseau local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) et la [phase 2 en créant le réseau virtuel entre différents locaux dans Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) décrites dans la feuille de route de déploiement de l’article [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Voici la configuration finale.
  
![Phase 1 du serveur DirSync pour Office 365 hébergé dans Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Cette illustration montre un réseau local connecté à un réseau virtuel Azure via une connexion VPN ou ExpressRoute de site à site.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Phase 2 : créer et configurer les machines virtuelles Azure

Créez la machine virtuelle dans Azure en suivant les instructions décrites dans [Créer votre première machine virtuelle Windows dans le portail Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilisez les paramètres suivants :
  
- Dans le volet **De base**, sélectionnez le même abonnement, le même emplacement et le même groupe de ressources que votre réseau virtuel. Enregistrez le nom d'utilisateur et le mot de passe dans un emplacement sécurisé. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle.
    
- Dans le volet **Choisir une taille**, choisissez la taille **A2 Standard**.
    
- Dans le volet **Paramètres**, dans la section **Stockage**, sélectionnez le type de stockage **Standard**. Dans la section **Réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l'hébergement du serveur DirSync (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.
    
Vérifiez que votre serveur DirSync utilise correctement DNS en vérifiant votre DNS interne pour vous assurer qu’un enregistrement d’adresse (A) a été ajouté pour la machine virtuelle avec son adresse IP. 
  
Suivez les instructions décrites dans [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) pour vous connecter au serveur DirSync avec une connexion Bureau à distance. Une fois connecté, associez la machine virtuelle au domaine Windows Server AD local.
  
Pour qu’Azure AD Connect puisse accéder aux ressources Internet, vous devez configurer le serveur DirSync de sorte qu’il utilise le serveur proxy du réseau local. Nous vous recommandons de contacter votre administrateur réseau pour toute étape de configuration supplémentaire à effectuer.
  
Voici la configuration finale.
  
![Phase 2 du serveur DirSync pour Office 365 hébergé dans Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Cette illustration montre la machine virtuelle du serveur DirSync dans le réseau virtuel Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Phase 3 : installer et configurer Azure AD Connect

Procédez comme suit :
  
1. Connectez-vous au serveur DirSync à l'aide d'une connexion Bureau à distance avec un compte de domaine Windows Server AD qui possède des privilèges d'administrateur local. Voir [Se connecter à la machine virtuelle et ouvrir une session](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).
    
2. À partir du serveur DirSync, ouvrez l'article [Configurer la synchronisation d'annuaires pour Office 365]((https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)) et suivez les instructions pour la synchronisation d'annuaires avec la synchronisation de mot de passe.
    
> [!CAUTION]
> Le programme d'installation crée le compte **AAD_xxxxxxxxxxxx** dans l'unité d'organisation (UO) Utilisateurs locaux. Ne déplacez pas ou ne supprimez pas ce compte, ou la synchronisation échouera.
  
Voici la configuration finale.
  
![Phase 3 du serveur DirSync pour Office 365 hébergé dans Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Cette illustration montre le serveur DirSync avec Azure AD Connect dans le réseau virtuel Azure entre différents locaux.
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Affectation d’emplacements et de licences à des utilisateurs dans Office 365

Azure AD Connect ajoute des comptes à votre abonnement Office 365 à partir de Windows Server AD en local, mais pour que les utilisateurs se connectent à Office 365 et utilisent ses services, les comptes doivent être configurés avec un emplacement et des licences. Utilisez ces étapes pour ajouter l’emplacement et activer les licences pour les comptes d’utilisateur appropriés :
  
1. Connectez-vous à la [page du portail Office 365]((https://portal.office.com)), puis cliquez sur **Administrateur**.
    
2. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
3. Dans la liste des comptes d’utilisateur, sélectionnez la case à cocher en regard de l’utilisateur que vous souhaitez activer.
    
4. Sur la page de l'utilisateur, cliquez sur **Modifier** pour **Licences de produits**.
    
5. Sur la page **Licences de produit**, sélectionnez un emplacement pour l'utilisateur pour **Emplacement**, puis activez les licences appropriées pour l'utilisateur.
    
6. Lorsque vous avez terminé, cliquez sur **Enregistrer**, puis sur **Fermer** deux fois.
    
7. Revenez à l’étape 3 pour d’autres utilisateurs.
    
## <a name="see-also"></a>Voir aussi

<a name="DeploymentRoadmap"> </a>

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Télécharger Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurer la synchronisation d'annuaires pour Office 365]((https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846))
  
[Serveur DirSync du kit de déploiement Azure]((https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded))



