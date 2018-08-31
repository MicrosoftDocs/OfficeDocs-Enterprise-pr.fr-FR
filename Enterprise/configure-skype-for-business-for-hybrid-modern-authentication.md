---
title: Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Authentification moderne, est une méthode de gestion des identités qui offre le plus sécurisée authentification et autorisation utilisateur, n’est disponible pour Skype pour Business server locaux et Exchange server locale, ainsi que-domaine fractionné Skype pour hybrides Business.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540675"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride

Authentification moderne, est une méthode de gestion des identités qui offre le plus sécurisée authentification et autorisation utilisateur, n’est disponible pour Skype pour Business server locaux et Exchange server locale, ainsi que-domaine fractionné Skype pour hybrides Business.
  
 **Important** Vous souhaitez en savoir plus sur l’authentification moderne (MA) et pourquoi vous pouvez utiliser dans votre société ou organisation ? Vérifiez [ce document](hybrid-modern-auth-overview.md) pour une vue d’ensemble. Si vous avez besoin de savoir quels Skype pour les topologies d’entreprise sont pris en charge par MA, qui est décrite ici ! 
  
 **Avant de commencer**, appeler : 
  
- Authentification moderne \> MA
    
- Authentification moderne hybride \> zone
    
- Exchange local \> EXCH
    
- Exchange Online \> EXO
    
- Skype pour Business local \> SFB
    
- et Skype pour les entreprises en ligne \> SFBO
    
En outre, * si un graphique dans cet article dispose d’un objet qui a « grisé » ou « estompé » qui signifie que l’élément indiqué dans gris **n’est pas** inclus dans une configuration spécifique à l’agent de gestion. * 
  
## <a name="read-the-summary"></a>Lisez le résumé

Ce résumé limite le processus en étapes qui pourraient sinon perdues lors de l’exécution et sont adapté à une liste de contrôle globale d’effectuer le suivi d’où vous vous trouvez dans le processus.
  
1. Tout d’abord, assurez-vous que vous disposez de tous les éléments prérequis.
    
1. Depuis de nombreuses **conditions préalables** sont courants pour les deux Skype pour les entreprises et Exchange, [consultez l’article vue d’ensemble de votre liste de vérification de condition requise](hybrid-modern-auth-overview.md). Cette *avant de* commencer l’une des étapes de cet article. 
    
2. Collecter les informations spécifiques à la zone que vous avez besoin dans un fichier ou OneNote.
    
3. Activer sur moderne Authentication for EXO (si elle n’est pas déjà activée).
    
4. Activer sur moderne Authentication for SFBO (si elle n’est pas déjà activée).
    
5. Activer l’authentification de moderne hybride pour Exchange local.
    
6. Activer l’authentification de moderne hybride pour Skype pour l’entreprise locale.
    
Notez que ces étapes activer MA pour SFB, SFBO, EXCH et EXO--autrement dit, tous les produits qui peuvent participer à une configuration de zone de SFB et SFBO (y compris les dépendances sur EXCH/EXO). En d’autres termes, si vos utilisateurs sont hébergés dans les boîtes aux lettres créés dans n’importe quelle partie du hybride (EXO + SFBO, EXO + SFB, EXCH + SFBO, ou EXCH + SFB), votre produit fini ressemble à ceci :
  
![Un Skype 6 mixte pour la topologie de zone business a MA tous les emplacements possibles quatre.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Comme vous pouvez le constater, il existe quatre emplacements différents pour activer MA ! Pour une expérience utilisateur optimale, nous vous recommandons de que vous allumez MA dans les quatre de ces emplacements. Si vous ne pouvez pas activer MA dans tous les emplacements de ces, ajustez les étapes afin que vous allumez MA uniquement dans les emplacements qui sont nécessaires pour votre environnement.
  
Consultez la [rubrique prise en charge pour Skype pour les entreprises avec MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) pour les topologies prises en charge. 
  
 **Important** Vérifiez que vous avez répondu à toutes les conditions préalables avant de commencer. Vous trouverez ces informations [ici](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Collecte toutes les informations spécifiques à la zone dont vous aurez besoin

Une fois que vous avez à double contrôle que vous remplissez les [conditions requises](hybrid-modern-auth-overview.md) pour utiliser l’authentification moderne (voir la Remarque ci-dessus), vous devez créer un fichier pour contenir les informations nécessaires pour la configuration de zone dans les étapes à venir. Exemples de cet article : 
  
- **Domaine SIP/SMTP**
    
  - Par exemple contoso.com (est fédéré avec Office 365)
    
- **ID de client**
    
  - GUID qui représente votre client Office 365 (lors de la connexion de contoso.onmicrosoft.com).
    
- **URL du Service Web SFB 2015 CU5**
    
Vous aurez besoin d’URL du service web internes et externes pour tous les pools SfB 2015 déployés. Pour obtenir ces, exécutez ce qui suit à partir de Skype pour Business Management Shell :
  
Get-CsService - WebServer | Nom PoolFqdn Select-Object, InternalFqdn, | FL
  
- Exemple interne :https://lyncwebint01.contoso.com
    
- Exemple : externe :https://lyncwebext01.contoso.com
    
Si vous utilisez un serveur Standard Edition server, l’URL interne est vide. Dans ce cas, utilisez le nom complet du pool de l’URL interne.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Activer l’authentification moderne pour EXO

Suivez les instructions fournies ici : [Exchange Online : l’activation de votre client pour l’authentification moderne.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Activer l’authentification moderne pour SFBO

Suivez les instructions fournies ici : [Skype pour Business Online : activer votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Activer l’authentification de moderne hybride pour Exchange local

Suivez les instructions fournies ici : [comment configurer le serveur Exchange local pour utiliser l’authentification moderne hybride](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Activer l’authentification de moderne hybride pour Skype pour l’entreprise locale

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajoutez sur site web service URL en tant que des noms principaux de service dans Azure AD

Vous devez maintenant exécuter des commandes pour ajouter les URL (précédemment collectées) en tant qu’entités de Service dans SFBO.
  
 **Remarque** Noms principaux de service (SPN) identifient les services web et les associer à une entité de sécurité (telles que le nom de compte ou groupe) afin que le service peut agir pour le compte d’un utilisateur autorisé. Clients s’authentifier sur un serveur de tirer parti des informations de noms principaux de service contenues dans. 
  
1. Tout d’abord, connectez-vous à DAS avec [ces instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).
    
2. Exécutez cette commande sur site, pour obtenir une liste d’URL de service web SFB.
    
  - Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Sélectionnez ServicePrincipalNames - ExpandProperty
    
    Notez que le AppPrincipalId commence par '00000004'. Ceci correspond à Skype pour Business Online.
    
    Prendre note des (et la capture d’écran pour comparaison ultérieure) le résultat de cette commande, qui sera inclure une SE et l’URL de WS, mais se composent principalement des noms principaux de service qui commencent par 00000004-0000-0ff1-ce00-000000000000 /.
    
3. Si interne **ou** externe SFB URL locale sont manquantes (par exemple, https://lyncwebint01.contoso.com et https://lyncwebext01.contoso.com) nous devons ajouter ces enregistrements spécifiques à cette liste. 
    
    Veillez à remplacer *les URL de l’exemple* ci-dessous, avec vos URL réelle dans les commandes Ajouter ! 
    
  - $x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (« *https://lyncwebint01.contoso.com/* ») 
    
  - $x.ServicePrincipalnames.Add (« *https://lyncwebext01.contoso.com/* ») 
    
  - Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames
    
4. Vérifiez que vos nouveaux enregistrements ont été ajoutés à exécuter à nouveau la commande Get-MsolServicePrincipal à l’étape 2 et la recherche par le biais de la sortie. Comparez la liste / capture d’écran d’avant à la nouvelle liste des noms principaux de service (vous pouvez également capture d’écran de la nouvelle liste de vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. Allez dans notre exemple, la liste des noms principaux de service système incluent désormais les URL spécifiques https://lyncweb01.contoso.com et https://autodiscover.contoso.com.
    
### <a name="create-the-evosts-auth-server-object"></a>Créer l’objet de serveur d’authentification EvoSTS

Exécutez la commande suivante dans le Skype pour Business Management Shell.
  
- New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml AcceptSecurityIdentifierInformation - $true-Type AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>Activer l’authentification moderne hybride

Il s’agit de l’étape qui active réellement MA. Toutes les étapes précédentes peuvent être exécutées à l’avance sans modifier le flux d’authentification client. Lorsque vous êtes prêt à modifier le flux d’authentification, exécutez cette commande dans le Skype pour Business Management Shell. 
  
- Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>Vérifier

Une fois que vous activez la zone, la prochaine connexion d’un client utilise le nouveau flux d’authentification. Notez que le mise en marche de zone ne déclenche une nouvelle authentification pour les clients. Le clients réauthentifier en fonction de la durée de vie des jetons d’authentification ou qu’ils ont des certificats.
  
Pour vérifier que la zone fonctionne une fois que vous avez activé cette fonction, vous déconnecter d’un client Windows SFB test et veillez à cliquer sur « Supprimer mes informations d’identification ». Connectez-vous à nouveau. Le client doit désormais utiliser le flux d’authentification moderne et votre nom d’utilisateur inclut une invite **Office 365** pour un bureau ou une école compte, vu juste avant le client contacte le serveur et vous connecte. 
  
Vous devez également vérifier les informations de Configuration pour Skype pour les Clients d’entreprise pour une autorité de OAuth. Pour ce faire, sur l’ordinateur client, maintenez la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit le Skype pour entreprise icône dans la barre de Notification Windows. Dans le menu qui apparaît, cliquez sur informations de Configuration. Dans la fenêtre « Skype pour les informations de Configuration de Business » qui s’affiche sur le bureau, recherchez les éléments suivants :
  
![Les informations de Configuration d’un Skype pour Business Client en utilisant l’authentification moderne indiquent un Lync et les URL d’autorité OAUTH EWS de https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
Vous devez également maintenez enfoncée la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit sur l’icône pour le client Outlook (également dans la barre d’état Windows Notifications), cliquez sur état de la connexion. Recherchez l’adresse du client SMTP par rapport à un type d’authentification de ' illimitées\*», qui représente le jeton de support utilisé dans OAuth.
  
## <a name="related-articles"></a>Articles connexes

[Lien vers la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) . 
  
Vous devez savoir comment utiliser l’authentification moderne (ADAL) pour votre Skype pour les clients d’entreprise ? Nous avons étapes [ici](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
Voulez-vous pour lire comme suit lorsqu’ils s’affichent pour Exchange Server, sur site, en cours d’exécution sans SFB ? Ces étapes sont disponibles.
  

