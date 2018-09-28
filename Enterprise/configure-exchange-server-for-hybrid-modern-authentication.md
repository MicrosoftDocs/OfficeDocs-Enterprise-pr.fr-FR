---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Hybride modernes d’authentification (zone), est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur et est disponible pour les déploiements de hybride Exchange server sur site.
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975192"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride

Hybride modernes d’authentification (zone), est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur et est disponible pour les déploiements de hybride Exchange server sur site.
  
## <a name="fyi"></a>MONEY

Avant de commencer, appeler :
  
- Authentification moderne hybride \> zone
    
- Exchange local \> EXCH
    
- Exchange Online \> EXO
    
En outre, *que si un graphique dans cet article est un objet qui a « grisé » ou « estompé » ce qui signifie que l’élément en gris n’est pas inclus dans la configuration de la zone spécifique* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Activation de l’authentification moderne hybride

Activation de zone signifie :
  
1. En vérifiant que vous remplissez les conditions préalables avant de commencer.
    
1. Depuis de nombreuses **conditions préalables** sont courants pour les deux Skype pour les entreprises et Exchange, [vue d’ensemble de l’authentification moderne hybride et les conditions préalables pour l’utiliser avec locale Skype pour l’entreprise et les serveurs Exchange](hybrid-modern-auth-overview.md). Cela avant de commencer une des étapes de cet article.
    
2. Ajout de local URL du service web en tant que des noms principaux de Service (SPN) dans Azure AD.
    
3. En vous assurant de tous les répertoires virtuels sont activés pour la zone
    
4. Vérification de l’objet serveur d’authentification EvoSTS
    
5. Activation de la zone de change
    
 **Remarque** Votre version de Microsoft Office ne prend en charge MA ? Voir [moderne comment fonctionne l’authentification pour les applications clientes Office 2013 et Office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Assurez-vous que vous disposez de tous les préalables

Étant donné que plusieurs conditions préalables sont courants pour les deux Skype pour les entreprises et Exchange, consultez [hybride moderne Authentication overview et les conditions préalables pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange](hybrid-modern-auth-overview.md). Cette *avant de* commencer l’une des étapes de cet article. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajoutez sur site web service URL en tant que des noms principaux de service dans Azure AD

Exécutez les commandes qu’attribuer à votre site web local des URL de service que Azure AD SPN. noms principaux de service sont utilisés par les ordinateurs clients et périphériques durant l’authentification et d’autorisation. Toutes les URL qui peuvent être utilisés pour se connecter à partir de locaux pour Azure Active Directory (DAS) doivent être inscrit dans DAS (Cela inclut les espaces de noms internes et externes).
  
Tout d’abord, rassemblez toutes les URL que vous devez ajouter dans DAS. Exécutez ces commandes locale :
  
- Get-MapiVirtualDirectory | Serveur FL,\*url\*
    
- Get-WebServicesVirtualDirectory | Serveur FL,\*url\*
    
- **Get-ActiveSyncVirtualDirectory | Serveur FL,\*url\***
    
- Get-OABVirtualDirectory | Serveur FL,\*url\*
    
Vérifiez que les URL que les clients peuvent se connecter à sont répertoriées sous les noms principaux de service HTTPS dans DAS.
  
1. Tout d’abord, connectez-vous à DAS avec [ces instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).
    
2. Pour Exchange URL associées, tapez la commande suivante :
    
- Get-MsolServicePrincipal - AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | Sélectionnez - ExpandProperty ServicePrincipalNames
    
Prendre note des (et la capture d’écran pour comparaison ultérieure) le résultat de cette commande, qui doit inclure un https:// * découverte automatique. *votre_domaine* .com * et URL https:// *mail.yourdomain.com* mais se composent principalement des noms principaux de service qui commencent par 00000002-0000-0ff1-ce00-000000000000 /. Si l’URL https:// votre sur site qui ne figurent pas nous vous devrez ajouter ces enregistrements spécifiques à cette liste. 
  
3. Si vous ne voyez pas vos enregistrements MAPI/HTTP, EWS, ActiveSync, carnet d’adresses et de découverte automatique internes et externes dans cette liste, vous devez les ajouter à l’aide de la commande ci-dessous (URL de l’exemple sont '`mail.corp.contoso.com`'et'`owa.contoso.com`», mais vous avez **Remplacer les exemples d’URL avec vos propres** ) : <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Vérifiez que vos nouveaux enregistrements ont été ajoutés à exécuter à nouveau la commande Get-MsolServicePrincipal à l’étape 2 et la recherche par le biais de la sortie. Comparez la liste / capture d’écran d’avant à la nouvelle liste des noms principaux de service (vous pouvez également capture d’écran de la nouvelle liste de vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. Allez dans notre exemple, la liste des noms principaux de service système incluent désormais les URL spécifiques `https://mail.corp.contoso.com` et `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Vérifier que les répertoires virtuels sont configurés correctement

Vérifiez maintenant OAuth est correctement activé dans Exchange sur tous les répertoires virtuels Outlook peut utiliser en exécutant les commandes suivantes :

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

Vérification de la sortie pour vous assurer que **OAuth** est activée sur chacun de ces VDirs, il doit ressembler à ceci (et l’essentiel à examiner est « OAuth ») ; 
  
 **[PS] C:\Windows\System32\>Get-MapiVirtualDirectory | serveur fl,\*url\*,\*auth\***
  
 **Serveur : EX1**
  
 **InternalUrl :`https://mail.contoso.com/mapi`**
  
 **ExternalUrl :`https://mail.contoso.com/mapi`**
  
 **IISAuthenticationMethods : {Ntlm, OAuth, négocier}**
  
 **InternalAuthenticationMethods : {Ntlm, OAuth, négocier}**
  
 **ExternalAuthenticationMethods : {Ntlm, OAuth, négocier}**
  
Si OAuth est manquant à partir de n’importe quel serveur et n’importe lequel des quatre répertoires virtuels que vous souhaitez ajouter à l’aide des commandes avant de continuer.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Vérifiez que l’objet de serveur d’authentification EvoSTS est établie.

Revenez à locale Exchange Management Shell pour cette dernière commande. Vous pouvez maintenant valider que votre site dispose d’une entrée pour le fournisseur d’authentification evoSTS :
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
La sortie doit s’afficher une AuthServer de l’EvoSts nom et l’état « Activé » doit avoir la valeur True. Si vous ne voyez pas cela, vous devez téléchargez et exécutez la version la plus récente de l’Assistant Configuration hybride.
  
 **Important** Si vous exécutez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS n’est créé. 
  
## <a name="enable-hma"></a>Activer la zone de mémoire haute

Exécutez la commande suivante dans Exchange Management Shell, locale :

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Vérifier

Une fois que vous activez la zone, la prochaine connexion d’un client utilise le nouveau flux d’authentification. Notez que le mise en marche de zone ne déclenche une nouvelle authentification pour les clients. Le clients réauthentifier en fonction de la durée de vie des jetons d’authentification ou qu’ils ont des certificats.
  
Vous devez également maintenez enfoncée la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit sur l’icône pour le client Outlook (également dans la barre d’état Windows Notifications), cliquez sur état de la connexion. Recherchez l’adresse du client SMTP par rapport à un type de « Authentification » de ' illimitées\*», qui représente le jeton de support utilisé dans OAuth.
  
 **Remarque** Nécessaire de configurer Skype pour les entreprises avec zone ? Vous aurez besoin de deux articles : une qui répertorie les [topologies prises en charge](https://technet.microsoft.com/en-us/library/mt803262.aspx)et une qui vous montre [comment effectuer la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de l’authentification moderne hybride et conditions requises pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange](hybrid-modern-auth-overview.md) 
  

