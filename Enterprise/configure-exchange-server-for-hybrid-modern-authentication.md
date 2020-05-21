---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: L’authentification moderne hybride (HMA), est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, et est disponible pour les déploiements hybrides Exchange Server locaux.
ms.openlocfilehash: c52eecbe57567276de94aac913b7b82db8c5e404
ms.sourcegitcommit: 72a4938f1372e7f3693b53bcabac0c5d18305a1d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44326441"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

L’authentification moderne hybride (HMA), est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, et est disponible pour les déploiements hybrides Exchange Server locaux.
  
## <a name="fyi"></a>Pour info

Avant de commencer, j’appelle :
  
- HMA d’authentification moderne hybride \>
    
- Exch Exchange sur site \>
    
- Exchange Online \> exo
    
En outre, *si un graphisme de cet article a un objet « grisé » ou « grisé », cela signifie que l’élément affiché en gris n’est pas inclus dans la configuration spécifique* à la HMA. 
  
## <a name="enabling-hybrid-modern-authentication"></a>Activation de l’authentification moderne hybride

L’activation de la haute-HMA sur signifie :
  
1. Assurez-vous que vous remplissez les configuration requise avant de commencer.
    
1. Étant donné que de nombreux **éléments prérequis** sont communs à la fois à Skype entreprise et à Exchange, une [vue d’ensemble de l’authentification moderne hybride et des prérequis pour l’utiliser avec des serveurs Skype entreprise et Exchange locaux](hybrid-modern-auth-overview.md). Procédez comme suit avant de commencer l’une des étapes décrites dans cet article.
    
2. Ajout d’URL de service Web sur site sous forme de noms principaux de service (SPN) dans Azure AD.
    
3. Vérifier que tous les répertoires virtuels sont activés pour HMA
    
4. Vérification de l’objet serveur d’authentification EvoSTS
    
5. Activation de la haute HMA dans EXCH.
    
 **Note** Votre version de l’agent de gestion du support Office est-elle ? Découvrez [le fonctionnement de l’authentification moderne pour les applications clientes office 2013 et office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Vérifier que vous remplissez toutes les conditions préalables

Étant donné que de nombreuses conditions préalables sont communes à la fois pour Skype entreprise et Exchange, consultez la [rubrique vue d’ensemble de l’authentification moderne hybride et conditions préalables pour l’utiliser avec des serveurs Skype entreprise et Exchange locaux](hybrid-modern-auth-overview.md). Procédez comme suit *avant* de commencer l’une des étapes décrites dans cet article. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajouter des URL de service Web sur site en tant que SPN dans Azure AD

Exécutez les commandes qui affectent vos URL de service Web local en tant que SPN Azure AD. Les SPN sont utilisés par les ordinateurs clients et les appareils au cours de l’authentification et de l’autorisation. Toutes les URL pouvant être utilisées pour se connecter à Azure Active Directory (AAD) doivent être enregistrées dans AAD (cela inclut les espaces de noms internes et externes).
  
Tout d’abord, Rassemblez toutes les URL que vous devez ajouter dans AAD. Exécutez ces commandes en local :
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Assurez-vous que les URL auxquelles les clients peuvent se connecter sont répertoriées en tant que noms principaux du service HTTPs dans AAD.
  
1. Tout d’abord, connectez-vous à AAD en utilisant [ces instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

 **Note** Vous devez utiliser l’option Connect-MsolService à partir de cette page pour pouvoir utiliser la commande ci-dessous. 
    
2. Pour vos URL liées à Exchange, tapez la commande suivante :
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Prenez note de (et de capture d’écran pour une comparaison ultérieure) la sortie de cette commande, qui doit inclure une URL https:// *autodiscover.yourdomain.com* et https:// *mail.yourdomain.com* , mais qui se composent principalement de noms principaux de contenu commençant par 00000002-0000-0ff1-CE00-000000000000/. S’il existe des URL https://de votre local qui ne sont pas disponibles, nous devons ajouter ces enregistrements spécifiques à cette liste. 
  
3. Si vos enregistrements MAPI/HTTP, EWS, ActiveSync, OAB et Autodiscover internes et externes ne s’affichent pas dans cette liste, vous devez les ajouter à l’aide de la commande ci-dessous (les exemples d’URL sont « `mail.corp.contoso.com` » et «» `owa.contoso.com` , mais vous pouvez **remplacer les URL d’exemple par les vôtres** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant de nouveau la commande Get-MsolServicePrincipal à partir de l’étape 2 et en examinant la sortie. Comparez la liste/capture d’écran de l’avant à la nouvelle liste de noms principaux de vente (vous pouvez également créer une capture d’écran de la nouvelle liste pour vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. À l’aide de notre exemple, la liste des SPN inclut désormais les URL spécifiques `https://mail.corp.contoso.com` et `https://owa.contoso.com` . 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Vérifier que les répertoires virtuels sont correctement configurés

Maintenant, vérifiez que OAuth est correctement activé dans Exchange sur tous les répertoires virtuels qu’Outlook peut utiliser en exécutant les commandes suivantes :

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Vérifiez la sortie pour vous assurer que le protocole **OAuth** est activé sur chacune de ces VDirs, il ressemblera à ceci (et la clé à examiner est « OAuth »); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
Si OAuth est absent de n’importe quel serveur et de l’un des quatre répertoires virtuels, vous devez l’ajouter en utilisant les commandes appropriées avant de continuer ([Set-MapiVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-mapivirtualdirectory?view=exchange-ps), [Set-WebServicesVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-webservicesvirtualdirectory?view=exchange-ps), [Set-OABVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/email-addresses-and-address-books/set-oabvirtualdirectory?view=exchange-ps)et [Set-AutodiscoverVirtualDirectory permet](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-autodiscovervirtualdirectory?view=exchange-ps)).
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Vérifiez que l’objet serveur d’authentification EvoSTS est présent.

Revenez à l’environnement de commande Exchange Management Shell pour cette dernière commande. À présent, vous pouvez vérifier que votre site local dispose d’une entrée pour le fournisseur d’authentification evoSTS :
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

Votre sortie doit afficher un AuthServer du nom EvoSts et l’État « Enabled » doit être true. Si ce n’est pas le cas, vous devez télécharger et exécuter la version la plus récente de l’Assistant Configuration hybride.
  
 **Important** Si vous utilisez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS n’est pas créé. 
  
## <a name="enable-hma"></a>Activer la HMA

Exécutez la commande suivante dans l’environnement de commande Exchange Management Shell :

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Vérifié

Une fois que vous activez HMA, la prochaine connexion d’un client utilisera le nouveau flux d’authentification. Notez que l’activation de la mémoire HMA ne déclenche pas une nouvelle authentification pour un client. Les clients se ré-authentifient en fonction de la durée de vie des jetons d’authentification et/ou des certificats dont ils disposent.
  
Vous devez également maintenir la touche CTRL enfoncée en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans le bac Windows notifications) et cliquez sur « état de la connexion ». Recherchez l’adresse SMTP du client par rapport à un « type d’authentification » de « porteur \* », qui représente le jeton du porteur utilisé dans OAuth.
  
 **Note** Vous avez besoin de configurer Skype entreprise avec HMA ? Vous aurez besoin de deux articles : un qui répertorie les [topologies prises en charge](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)et un autre qui vous montre [Comment effectuer la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Utilisation de l’authentification moderne hybride avec Outlook pour iOS et Android

Si vous êtes un client local utilisant Exchange Server sur le port TCP 443, veuillez autoriser les plages d’adresses IP suivantes : <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> 
  

## <a name="related-topics"></a>Sujets associés

[Vue d’ensemble de l’authentification moderne hybride et conditions préalables à son utilisation avec des serveurs Skype entreprise et Exchange locaux](hybrid-modern-auth-overview.md) 
  
Forcer les utilisateurs d’Outlook à l’authentification moderne  
[Conditions requises pour la configuration de l’authentification moderne pour la transition à partir d’Office 365 dédié/ITAR vers vNext](modern-authentication-configuration.md)
