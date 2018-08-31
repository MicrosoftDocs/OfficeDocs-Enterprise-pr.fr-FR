---
title: Vue d’ensemble de l’authentification moderne hybride et conditions requises pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: Authentification moderne est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur. Il est disponible pour les déploiements hybrides de Skype pour Business server locaux et Exchange server locale, ainsi que-domaine fractionné Skype pour hybrides Business. Liens de cet article à des documents sur la configuration requise, le programme d’installation/désactivation de l’authentification moderne et pour des informations connexes client (par exemple clients Outlook et Skype) associés.
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240589"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Vue d’ensemble de l’authentification moderne hybride et conditions requises pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange

Authentification moderne est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur. Il est disponible pour les déploiements d’Office 365 hybride de Skype pour Business server locaux et Exchange server locale, ainsi que, domaine fractionné Skype pour hybrides Business. Liens de cet article à des documents sur la configuration requise, le programme d’installation/désactivation de l’authentification moderne et pour des informations connexes client (par exemple clients Outlook et Skype) associés. 
  
- [Quel est l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [Les modifications que lorsque vous utilisez l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Vérifier l’état de l’authentification moderne de votre environnement sur site](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Remplissent les conditions préalables d’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [Que dois-je savoir avant de commencer ?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Liste d’URL de l’authentification moderne](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>Quel est l’authentification moderne ?
<a name="BKMK_WhatisModAuth"> </a>

Lors de la discussion sur la communication entre un client (par exemple, votre ordinateur portable ou votre téléphone) et un serveur, Microsoft utilise la phrase « Authentification moderne ».
  
Authentification moderne est un terme générique pour une combinaison d’authentification et les méthodes d’autorisation, ainsi que des mesures de sécurité qui s’appuient sur les stratégies d’accès que vous connaissez peut-être déjà. Elle comprend :
  
- **Méthodes d’authentification**: l’authentification multifacteur ; Authentification basée sur certificat client ; et la bibliothèque de l’authentification Active Directory ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Méthodes d’autorisation**: implémentation protocole Microsoft du Open Authorization (OAuth). 
    
- **Stratégies d’accès conditionnel**: gestion d’Application Mobile (MAM) et accès conditionnel Azure Active Directory. 
    
Gestion des identités d’utilisateur avec l’authentification moderne permet aux administrateurs de différents outils à utiliser lorsqu’il s’agit de sécuriser les ressources et propose des méthodes plus sécurisés de gestion des identités pour les deux locaux (Exchange et Skype pour les entreprises), Exchange hybride et Skype pour les scénarios de domaine/fractionné-hybride.
  
Sachez que car Skype pour les entreprises travaille en étroite collaboration avec Exchange, le comportement d’ouverture de session Skype pour Business client, les utilisateurs verront est effectué par l’état de l’authentification modernes d’Exchange. Cela s’appliquent également si vous avez un Skype pour un environnement hybride de Business-domaine fractionné. En outre, le type de Skype pour un environnement hybride Business qui prend en charge l’utilisation de l’authentification moderne est souvent appelé un « domaine-fractionné » (dans un domaine fractionné, vous avez Skype pour Business Online et Skype pour Business-prem, et les utilisateurs sont hébergés dans deux emplacements).
  
 **Important** Savez-vous que, à compter d’août 2017, tous les clients Office 365 nouveau qui comprennent les Skype pour les entreprises en ligne et Exchange online aura moderne l’authentification est activée par défaut ? Clients préexistants n’aient pas une modification dans leur état d’agent de gestion par défaut, mais tous les nouveaux clients automatiquement prend en charge l’étendue des fonctionnalités d’identité que vous voir répertoriés ci-dessus. Pour vérifier votre statut de MA Skype pour les entreprises en ligne, vous pouvez utiliser Skype pour Business online PowerShell avec les informations d’identification d’administrateur Global. Exécutez 'Get-CsOAuthConfiguration' pour vérifier la sortie de - ClientADALAuthOverride. Si - ClientADALAuthOverride est « autorisé » votre authentification moderne est activé. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Les modifications que lorsque vous utilisez l’authentification moderne ?
<a name="BKMK_WhatChanges"> </a>

Lorsque l’authentification moderne avec Skype sur site pour l’entreprise ou le serveur Exchange, vous êtes toujours *authentifier* les utilisateurs locaux, mais l’histoire *d’Autoriser* leur accès à des modifications de ressources (comme les fichiers ou les messages électroniques). C’est pourquoi, même si l’authentification moderne est sur la communication client et serveur, les mesures prises au cours de la configuration des résultats de l’agent de gestion dans evoSTS (un Service jeton de sécurité utilisé par Azure AD) qui est définie en tant que serveur d’authentification pour Skype pour l’entreprise et Exchange server local. 
  
La modification d’evoSTS permet à votre site serveurs tirer parti d’OAuth (émission de jeton) pour autoriser les clients et permet également de vos méthodes de la sécurité utilisation locale courantes dans le nuage (par exemple, l’authentification multifacteur). En outre, l’evoSTS utilise des jetons qui permettent aux utilisateurs de demander l’accès aux ressources sans fournir leur mot de passe dans le cadre de la demande. Quel que soit l’où vos utilisateurs sont hébergés (en ligne ou sur site), et quel que soit l’emplacement héberge les ressources nécessaires, EvoSTS devient la base d’autorisation des utilisateurs et les clients une fois l’authentification modernes est configurée.
  
Voici un exemple de ce que je veux dire. Si Skype pour client d’entreprise a besoin d’accéder à Exchange server pour obtenir des informations de calendrier au nom d’un utilisateur, il utilise la bibliothèque de l’authentification Active Directory (ADAL) pour le faire. ADAL une bibliothèque de code vise à rendre disponible pour les applications clientes à l’aide de jetons de sécurité OAuth les ressources sécurisées dans votre répertoire. Works ADAL avec OAuth pour vérifier les revendications et à échanger les jetons (plutôt que les mots de passe), pour accorder l’accès à une ressource. Dans le passé, l’autorité dans une transaction, telles que celle-ci : le serveur qui sait comment valider les revendications utilisateur et émettre les jetons nécessaires--peut-être un Service d’émission de jeton de sécurité locale, ou encore Active Directory Federation Services. Toutefois, l’authentification moderne centralise cette autorité avec Azure Active Directory (AD Azure) dans le nuage.
  
Cela signifie également que même si votre serveur Exchange et Skype pour les environnements d’entreprise peuvent être entièrement locaux, le serveur d’autorisation sera en ligne et votre environnement local doit avoir la possibilité de créer et gérer une connexion à votre bureau abonnement 365 dans le nuage (et l’instance d’Azure Active Directory que votre abonnement utilise comme son répertoire).
  
Ce que ne change pas ? Si vous participez à une hybride domaine fractionné ou à l’aide de Skype pour l’entreprise et Exchange server locaux, tous les utilisateurs doivent tout d’abord s’authentifier *sur site* . Dans une implémentation hybride d’authentification moderne, Lyncdiscovery et la découverte automatique pointent sur votre serveur local. 
  
 **Important** Si vous avez besoin de connaître le Skype spécifique pour les topologies d’entreprise pris en charge par MA, qui est [décrite ici](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Vérifier l’état de l’authentification moderne de votre environnement sur site
<a name="BKMK_CheckStatus"> </a>

Parce que l’authentification moderne change le serveur d’autorisation utilisé lors de tirer parti des services OAuth/S2S, vous devez savoir si l’authentification moderne est activée ou désactivée pour votre Skype pour un environnement d’entreprise et Exchange. Vous pouvez vérifier l’état en votre Skype ou des serveurs d’entreprise, sur site, en exécutant la commande Get-CSOAuthConfiguration dans PowerShell. Si la commande renvoie une propriété 'OAuthServers' vide, l’authentification moderne est désactivée.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Remplissent les conditions préalables d’authentification moderne ?

Vérifiez et ces éléments de votre liste avant de poursuivre :
  
- **Skype pour professionnels spécifiques**
    
  - Tous les serveurs doivent disposer de SFB Server 2015 CU5 ou version ultérieure
    
  - **Exception** - survivabilité Branch Appliance (SBA) peut se trouver sur la version actuelle (basée sur Lync 2013) 
    
  - Votre domaine SIP est ajouté en tant qu’un domaine fédéré dans Office 365
    
  - Tous les SFB frontaux doivent disposer de connexions sortantes à internet, à l’URL de l’authentification Office 365 (TCP 443) et la racine du certificat connu CRL (TCP 80) répertoriées dans les lignes 1 et 2 de la section « authentification Office 365 et identité » du [Office 365 URL et IP plages d’adresses](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).
    
 **Remarque** Si votre Skype pour les serveurs frontaux Business utiliser un serveur proxy pour accéder à Internet, le numéro IP et Port de serveur proxy utilisé doit figurer dans la section configuration du fichier web.config pour chaque serveur frontal. 
  
- c:\Program files\Skype pour Business Server 2015\Web Components\Web ticket\int\web.config
    
- c:\Program files\Skype pour Business Server 2015\Web Components\Web ticket\ext\web.config
    
- \</System.identityModel.Services\>
    
     \<System.NET\> 
    
     \<defaultProxy\> 
    
     \<proxy 
    
     ProxyAddress = «http://192.168.100.60:8080» 
    
     valeur BypassOnLocal = « true » 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</System.NET\> 
    
    \<configuration\>
    
 **Important** Veillez à vous abonner au flux RSS pour [Office 365 URL et plages d’adresses IP](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) garder le contact avec les dernières listes d’URL requis. 
  
- **Serveur Exchange spécifique**
    
  - À l’aide de des serveurs Exchange 2013 CU19 et vers le haut, ou Exchange server 2016 CU8 et le haut.
    
  - Il n’existe aucun serveur Exchange 2010 dans l’environnement.
    
  - Le déchargement SSL n’est pas configuré. ● le chiffrement et une terminaison SSL est pris en charge.
    
  - En cas de votre environnement utilise une infrastructure de serveur proxy pour permettre aux serveurs pour se connecter à Internet, assurez-vous que tous les serveurs Exchange ont le serveur proxy défini dans la propriété [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Configuration requise de client et du protocole Exchange**
  
  - Les clients suivants prennent en charge l’authentification moderne :

  |**Clients**|**Protocole principal**|**Remarques**|
  |:-----|:-----|:-----|
  |Outlook 2013 et Outlook 2016  <br/> |MAPI sur HTTP  <br/> |MAPI sur HTTP doit être activé dans Exchange afin de tirer parti d’authentification moderne de ces clients (généralement activé ou la valeur True pour les nouvelles installations de Exchange 2013 Service Pack 1 et ci-dessus) ; Pour plus d’informations, voir [comment moderne fonctionnement de l’authentification pour les applications clientes Office 2013 et Office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Vérifiez que vous exécutez la build requise minimale d’Outlook ; consultez les [dernières mises à jour pour les versions d’Outlook qui utilisent Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 pour Mac  <br/> |Services Web Exchange  <br/> |  <br/> |
  |Outlook pour iOS et Android  <br/> |  <br/> |Pour plus d’informations, voir [Using hybride moderne Authentication with Outlook pour iOS et Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Clients Exchange ActiveSync (par exemple, iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Pour les clients Exchange ActiveSync qui prennent en charge l’authentification moderne, vous devez recréer le profil afin de passer de l’authentification de base à authentification moderne.  <br/> |

- **Conditions préalables générales**
    
  - Si vous utilisez ADFS, vous devez disposer de Windows 2012 R2 ADFS 3.0 et versions ultérieures pour la fédération
    
  - Vos configurations identity sont les types pris en charge par connexion DAS (telles que la synchronisation de hachage de mot de passe, l’authentification directe, sur site STS pris en charge par Office 365, etc.)
    
  - Vous avez DAS connexion configurée et le fonctionnement de la synchronisation et la réplication de l’utilisateur.
    
  - Vous avez vérifié que hybride fonctionne entre votre organisation locale et Office 365 :
    
  - Déclaration de prise en charge officielle pour Exchange hybride indique que vous devez disposer de mise à jour Cumulative actuelle ou mise à jour Cumulative actuelle - 1.
    
  - Vérifiez que les deux, un utilisateur de test sur site, ainsi que d’un utilisateur de test hybride hébergés dans Office 365, peuvent se connecter à la Skype pour le client de bureau Business (si vous souhaitez utiliser l’authentification moderne avec Skype) et Microsoft Outlook (si vous souhaitez donc utiliser l’authentification moderne avec Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Que dois-je savoir avant de commencer ?
<a name="BKMK_Whatelse"> </a>

1. Tous les scénarios pour les serveurs locaux mettent en œuvre la configuration modernes d’authentification locale (en fait, pour Skype pour les entreprises est une liste des topologies prises en charge) afin que le serveur responsable de l’authentification et autorisation dans le Cloud Microsoft) Service jeton de sécurité du DAS, appelé « evoSTS ») et mise à jour d’Azure Active Directory (DAS) sur l’URL ou les espaces de noms utilisés par votre installation locale de soit Skype pour Exchange ou de l’entreprise. Par conséquent, les serveurs locaux prennent une dépendance de Cloud Microsoft. Cette action peut être considéré comme configuration « authentification hybride ».
    
2. Cet article liens out à d’autres personnes qui vous aideront à choisir pris en charge des topologies d’authentification moderne (nécessaires uniquement pour Skype pour les entreprises) et des procédures articles ce plan les étapes de configuration, ou pour désactiver l’authentification moderne, les étapes pour Exchange local et Skype pour les entreprises locales. Favori cette page dans votre navigateur, si vous aurez besoin d’une base d’accueil pour l’authentification moderne dans votre environnement serveur.
    
## <a name="list-of-modern-authentication-urls"></a>Liste d’URL de l’authentification moderne
<a name="BKMK_URLListforMA"> </a>

- [Comment configurer le serveur Exchange local pour utiliser l’authentification moderne](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype pour les topologies métiers pris en charge avec l’authentification moderne](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Comment configurer Skype pour les entreprises locale pour utiliser l’authentification moderne](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

