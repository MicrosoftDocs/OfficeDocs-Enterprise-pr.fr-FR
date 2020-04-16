---
title: Vue d’ensemble de l’authentification moderne hybride et conditions préalables à l’utilisation de Skype entreprise et des serveurs Exchange locaux
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: L’authentification moderne est une méthode de gestion des identités qui offre une authentification et une autorisation plus sécurisées pour les utilisateurs. Elle est disponible pour les déploiements hybrides de Skype entreprise Server en local et Exchange Server en local, ainsi que pour les hybrides Skype entreprise mixtes de domaine. Cet article fournit des liens vers des documents connexes sur les conditions préalables, la configuration/la désactivation de l’authentification moderne et la mise en relation avec certains clients (par exemple, Informations sur les clients Outlook et Skype).
ms.openlocfilehash: 325c34ec636ce9661b25f7b8be83ce8cbf61a291
ms.sourcegitcommit: d4814245d57313f2e94cd819b85ac1550fdeaf3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "43516455"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Vue d’ensemble de l’authentification moderne hybride et conditions préalables à son utilisation avec des serveurs Skype entreprise et Exchange locaux

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

_L’authentification moderne_ est une méthode de gestion des identités qui offre une authentification et une autorisation plus sécurisées pour les utilisateurs. Elle est disponible pour les déploiements hybrides Office 365 de Skype entreprise Server en local et Exchange Server en local, ainsi que les hybrides Skype entreprise mixtes de domaine. Cet article fournit des liens vers des documents connexes sur les conditions préalables, la configuration/la désactivation de l’authentification moderne et la mise en relation avec certains clients (par exemple, Informations sur les clients Outlook et Skype).
  
- [Qu’est-ce que l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Quelles sont les modifications apportées lorsque j’utilise l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Vérifier l’état d’authentification moderne de votre environnement local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Répondez-vous aux conditions préalables d’authentification modernes ?](#do-you-meet-modern-authentication-prerequisites)
- [Que dois-je savoir d’autre avant de commencer ?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Qu’est-ce que l’authentification moderne ?
<a name="BKMK_WhatisModAuth"> </a>

L’authentification moderne est un terme générique pour une combinaison de méthodes d’authentification et d’autorisation entre un client (par exemple, votre ordinateur portable ou votre téléphone) et un serveur, ainsi que certaines mesures de sécurité qui s’appuient sur des stratégies d’accès que vous connaissez peut-être déjà. Elle comprend :
  
- **Méthodes d’authentification**: Multi-Factor Authentication (MFA); authentification par carte à puce ; authentification basée sur les certificats clients
- **Méthodes d’autorisation**: mise en œuvre par Microsoft de l’autorisation d’ouverture (OAuth)
- **Stratégies d’accès conditionnel**: gestion des applications mobiles (MAM) et accès conditionnel Azure Active Directory

La gestion des identités des utilisateurs avec l’authentification moderne offre aux administrateurs de nombreux outils différents à utiliser pour sécuriser les ressources et offre des méthodes plus sûres de gestion des identités à la fois sur site (Exchange et Skype entreprise), dans des scénarios hybrides Exchange hybride et Skype entreprise.
  
Gardez à l’esprit que, étant donné que Skype entreprise travaille en étroite collaboration avec Exchange, le comportement de connexion des utilisateurs du client Skype entreprise sera affecté par l’état d’authentification moderne d’Exchange. Cela s’applique également si vous disposez d’une architecture hybride de _domaine mixte_ Skype entreprise, dans laquelle vous disposez de Skype entreprise Online et de Skype entreprise en local, avec des utilisateurs hébergés aux deux emplacements.

Pour plus d’informations sur l’authentification moderne dans Office 365, voir [prise en charge des applications clientes office 365-authentification moderne](office-365-client-support-modern-authentication.md).
  
> [!IMPORTANT]
> Depuis le 2017 août, tous les nouveaux locataires Office 365 qui incluent Skype entreprise Online et Exchange Online disposent d’une authentification moderne activée par défaut. Les locataires préexistants n’auront pas de modification dans leur état MA par défaut, mais tous les nouveaux clients prennent automatiquement en charge l’ensemble étendu de fonctionnalités d’identité que vous voyez ci-dessus. Pour vérifier l’état de MA, reportez-vous à la section [vérifier l’état de l’authentification moderne de votre environnement local](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Quelles sont les modifications apportées lorsque j’utilise l’authentification moderne ?
<a name="BKMK_WhatChanges"> </a>

Lors de l’utilisation de l’authentification moderne avec Skype entreprise ou Exchange Server local, vous *authentifiez* toujours les utilisateurs locaux, mais le scénario d' *autorisation* de leur accès aux ressources (comme les fichiers ou les courriers électroniques) change. C’est pourquoi, bien que l’authentification moderne concerne la communication entre les clients et les serveurs, les étapes suivies lors de la configuration de l’agent de gestion génèrent une evoSTS (un service d’émission de jeton de sécurité utilisé par Azure AD) défini en tant que serveur d’authentification pour Skype entreprise et Exchange Server en local.
  
La modification apportée à evoSTS permet à vos serveurs locaux de tirer parti de OAuth (émission de jeton) pour autoriser vos clients, et permet également à vos serveurs locaux d’utiliser des méthodes de sécurité communes dans le Cloud (comme l’authentification multifacteur). En outre, le evoSTS émet des jetons qui permettent aux utilisateurs de demander l’accès à des ressources sans fournir leur mot de passe dans le cadre de la demande. Quelle que soit l’endroit où les utilisateurs sont hébergés (en ligne ou en local), et quel que soit l’emplacement héberge la ressource nécessaire, EvoSTS deviendra le cœur de l’autorisation des utilisateurs et des clients une fois l’authentification moderne configurée.
  
Par exemple, si un client Skype entreprise a besoin d’accéder à Exchange Server pour obtenir des informations de calendrier pour le compte d’un utilisateur, il utilise la bibliothèque d’authentification Active Directory (ADAL) pour le faire. ADAL est une bibliothèque de code conçue pour mettre les ressources sécurisées dans votre répertoire à la disposition des applications clientes à l’aide de jetons de sécurité OAuth. ADAL fonctionne avec OAuth pour vérifier les revendications et échanger des jetons (plutôt que des mots de passe), pour accorder à un utilisateur l’accès à une ressource. Dans le passé, l’autorité dans une transaction telle que la suivante, le serveur qui sait valider les revendications utilisateur et émettre les jetons nécessaires, aurait pu être un service d’émission de jeton de sécurité sur site, voire Active Directory Federation Services. Toutefois, l’authentification moderne centralise cette autorité à l’aide d’Azure Active Directory (AAD).
  
Cela signifie également que même si vos environnements Exchange Server et Skype entreprise peuvent être entièrement en local, le serveur d’autorisation sera en ligne, et votre environnement local doit pouvoir créer et maintenir une connexion à votre abonnement Office 365 dans le Cloud (et l’instance Azure Active Directory que votre abonnement utilise comme annuaires).
  
Qu’est-ce qui ne change pas ? Que vous soyez dans un environnement hybride de domaine mixte ou que vous utilisiez Skype entreprise et Exchange Server en local, tous les utilisateurs doivent d’abord s’authentifier *en local*. Dans une implémentation hybride de l’authentification moderne, le _Lyncdiscovery_ et le service de _découverte automatique_ pointent tous deux vers votre serveur local.
  
> [!IMPORTANT]
> Si vous avez besoin de déterminer les topologies Skype entreprise spécifiques prises en charge avec l’agent de gestion, ce [document est décrit ci-dessous](https://technet.microsoft.com/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Vérifier l’état d’authentification moderne de votre environnement local
<a name="BKMK_CheckStatus"> </a>

Étant donné que l’authentification moderne modifie le serveur d’autorisation utilisé lorsque les services utilisent OAuth/S2S, vous devez déterminer si l’authentification moderne est activée ou désactivée pour vos environnements Skype entreprise et Exchange sur site. Vous pouvez vérifier l’état de vos serveurs Exchange en exécutant la commande PowerShell suivante :

```powershell
Get-OrganizationConfig | ft OAuth*
```

Si la valeur de la propriété _OAuth2ClientProfileEnabled_ est **false**, l’authentification moderne est désactivée.

Pour plus d’informations sur la cmdlet Get-OrganizationConfig, consultez la rubrique [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig).

Vous pouvez vérifier vos serveurs Skype entreprise en exécutant la commande PowerShell suivante :

```powershell
Get-CSOAuthConfiguration
```

Si la commande renvoie une propriété _OAuthServers_ vide ou si la valeur de la propriété _ClientADALAuthOverride_ n’est pas **autorisée**, l’authentification moderne est désactivée.

Pour plus d’informations sur la cmdlet Get-applet csoauthconfiguration, consultez la rubrique [Get-applet csoauthconfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration).
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Répondez-vous aux conditions préalables d’authentification modernes ?

Vérifiez et vérifiez ces éléments en dehors de votre liste avant de continuer :
  
- **Spécifique Skype entreprise**
  - Tous les serveurs doivent disposer de la mise à jour cumulative 2017 (CU5) pour Skype entreprise Server 2015 ou version ultérieure
    - **Exception** -survivabilité Branch Appliance (SBA) peut être sur la version actuelle (basée sur Lync 2013)
  - Votre domaine SIP est ajouté en tant que domaine fédéré dans Office 365
  - Tous les serveurs frontaux SFB doivent disposer de connexions sortantes vers Internet, des URL d’authentification Office 365 (TCP 443) et des listes de révocation de certificats racines connues (TCP 80) répertoriées dans les lignes 56 et 125 de la section « Microsoft 365 Common and Office » des [URL et des plages d’adresses IP d’office 365](urls-and-ip-address-ranges.md).
  
- **Skype entreprise en local dans un environnement hybride Office 365**
  - Un déploiement de Skype entreprise Server 2019 avec tous les serveurs exécutant Skype entreprise Server 2019.
  - Un déploiement de Skype entreprise Server 2015 avec tous les serveurs exécutant Skype entreprise Server 2015.
  - Un déploiement avec un maximum de deux versions de serveur différentes, comme décrit ci-dessous :
    - Skype Entreprise Server 2015
    - Skype entreprise Server 2019
  - Les mises à jour cumulatives les plus récentes doivent être installées sur tous les serveurs Skype entreprise, reportez-vous à la rubrique [mises à jour de Skype entreprise Server](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) pour trouver et gérer toutes les mises à jour disponibles.
  - Il n’existe pas de Lync Server 2010 ou 2013 dans l’environnement hybride.

>[!NOTE]
>Si vos serveurs frontaux Skype entreprise utilisent un serveur proxy pour l’accès Internet, le numéro de port et l’adresse IP du serveur proxy utilisés doivent être entrés dans la section Configuration du fichier Web. config pour chaque serveur frontal.
  
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> N’oubliez pas de vous abonner au flux RSS pour les [URL et les plages d’adresses IP Office 365](urls-and-ip-address-ranges.md) afin de rester à jour avec les dernières listes des URL requises.
  
- **Exchange Server spécifique**
  - Vous utilisez Exchange Server 2013 CU19 et up, Exchange Server 2016 CU8 et up, ou Exchange Server 2019 CU1 et up.
  - Il n’y a pas de serveur Exchange Server 2010 dans l’environnement.
  - Le déchargement SSL n’est pas configuré. L’arrêt de SSL et le rechiffrement sont pris en charge.
  - Dans l’éventualité où votre environnement utilise une infrastructure de serveur proxy pour permettre aux serveurs de se connecter à Internet, vérifiez que tous les serveurs Exchange ont le serveur proxy défini dans la propriété [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) .
  
- **Exchange Server local dans un environnement hybride Office 365**

  - Si vous utilisez Exchange Server 2013, les rôles serveur de boîtes aux lettres et d’accès au client doivent être installés sur au moins un serveur. Bien qu’il soit possible d’installer les rôles de boîte aux lettres et d’accès au client sur des serveurs distincts, nous vous recommandons vivement d’installer les deux rôles sur le même serveur afin de renforcer la fiabilité et d’améliorer les performances.
  - Si vous utilisez Exchange Server 2016 ou une version ultérieure, le rôle serveur de boîtes aux lettres doit être installé sur au moins un serveur.
  - Il n’y a pas de serveur Exchange 2007 ou 2010 dans l’environnement hybride.
  - Les mises à jour cumulatives les plus récentes doivent être installées sur tous les serveurs Exchange, consultez [la rubrique mettre à niveau Exchange vers les dernières mises à jour cumulatives](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) pour rechercher et gérer toutes les mises à jour disponibles.

- **Configuration requise pour le client et le protocole Exchange**
  
  - Les clients suivants prennent en charge l’authentification moderne :

  |**Clients**|**Protocole principal**|**Notes**|
  |:-----|:-----|:-----|
  |Outlook 2013 et Outlook 2016  <br/> |MAPI sur HTTP  <br/> |MAPI sur HTTP doit être activé dans Exchange afin de tirer parti de l’authentification moderne avec ces clients (généralement activé ou vrai pour les nouvelles installations d’Exchange 2013 Service Pack 1 et versions ultérieures); Pour plus d’informations, voir fonctionnement [de l’authentification moderne pour les applications clientes office 2013 et office 2016](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Assurez-vous que vous exécutez la version minimale requise d’Outlook ; consultez [les dernières mises à jour pour les versions d’Outlook qui utilisent Windows Installer (MSI)](https://docs.microsoft.com/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 pour Mac  <br/> |Services Web Exchange  <br/> |  <br/> |
  |Outlook pour iOS et Android  <br/> |  <br/> |Pour plus d’informations, consultez la rubrique [utilisation de l’authentification moderne hybride avec Outlook pour iOS et Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Clients Exchange ActiveSync (par exemple, iOS11 mail)  <br/> |Exchange ActiveSync  <br/> |Pour les clients Exchange ActiveSync qui prennent en charge l’authentification moderne, vous devez recréer le profil afin de passer de l’authentification de base à l’authentification moderne.  <br/> |

- **Conditions préalables générales**
  - Si vous utilisez ADFS, vous devez avoir Windows 2012 R2 ADFS 3,0 et versions ultérieures pour la Fédération.
  - Vos configurations d’identité sont l’un des types pris en charge par AAD Connect (par exemple, synchronisation de hachage de mot de passe, authentification directe, STS local pris en charge par Office 365, et cetera.)
  - Vous avez une connexion AAD configurée et fonctionnant pour la réplication et la synchronisation des utilisateurs.
  - Vous avez vérifié que le mode hybride est configuré à l’aide du mode de topologie hybride Exchange classique entre votre environnement local et Office 365. Déclaration officielle de l’assistance pour Exchange hybride : indique que vous devez être en cours de mise à jour cumulative ou CU-1.
    > [!NOTE]
    > L’authentification moderne hybride n’est pas prise en charge avec l' [agent hybride](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).

  - Assurez-vous qu’un utilisateur de test local, ainsi qu’un utilisateur test hybride hébergé dans Office 365, peuvent se connecter au client de bureau Skype entreprise (si vous souhaitez utiliser l’authentification moderne avec Skype) et Microsoft Outlook (si vous souhaitez utiliser l’authentification moderne avec Exchange).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Que dois-je savoir d’autre avant de commencer ?
<a name="BKMK_Whatelse"> </a>

- Tous les scénarios pour les serveurs locaux impliquent la configuration de l’authentification moderne en local (en fait, pour Skype entreprise, il existe une liste des topologies prises en charge, de sorte que le serveur responsable de l’authentification et de l’autorisation se trouve dans le Cloud Microsoft (service d’émission de jeton de sécurité AAD, appelé « evoSTS ») et mise à jour d’Azure Active Directory (AAD) sur les URL ou espaces de noms utilisés par votre installation locale de Skype entreprise ou Exchange. Par conséquent, les serveurs locaux prennent une dépendance de Microsoft Cloud. Cette action peut être considérée comme une configuration de l’authentification hybride.
- Cet article fournit des liens vers d’autres personnes qui vous aideront à choisir les topologies d’authentification moderne prises en charge (nécessaires uniquement pour Skype entreprise) et les procédures qui décrivent les étapes de configuration, ou les étapes à suivre pour désactiver l’authentification moderne, pour Exchange sur site et Skype entreprise en local. Favorisez cette page dans votre navigateur si vous avez besoin d’une base de démarrage pour utiliser l’authentification moderne dans votre environnement de serveur.

## <a name="related-topics"></a>Rubriques connexes
<a name="BKMK_URLListforMA"> </a>

- [Procédure de configuration d’Exchange Server local pour utiliser l’authentification moderne](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Topologies Skype entreprise prises en charge avec l’authentification moderne](https://technet.microsoft.com/library/mt803262.aspx)
- [Procédure de configuration de Skype entreprise en local pour utiliser l’authentification moderne](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
