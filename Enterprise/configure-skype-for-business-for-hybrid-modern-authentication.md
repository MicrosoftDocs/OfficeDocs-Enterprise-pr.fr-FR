---
title: Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: L’authentification moderne est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, est disponible pour Skype entreprise Server en local et Exchange Server en local, ainsi qu’hybrides Skype entreprise mixtes.
ms.openlocfilehash: 5db33a39ff58ae2aa21968c2f092c8ac29af5681
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493331"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride

L’authentification moderne est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, est disponible pour Skype entreprise Server en local et Exchange Server en local, ainsi qu’hybrides Skype entreprise mixtes.
  
 **Important** Souhaitez-vous en savoir plus sur l’authentification moderne (MA) et pourquoi choisir de l’utiliser dans votre entreprise ou organisation? Pour obtenir une vue d’ensemble, consultez [ce document](hybrid-modern-auth-overview.md) . Si vous avez besoin de savoir quelles topologies Skype entreprise sont prises en charge avec MA, il est documenté ici. 
  
 **Avant de commencer**, j’appelle: 
  
- MA de \> l’authentification moderne
    
- HMA d’authentification \> moderne hybride
    
- Exch Exchange sur site \>
    
- Exchange Online \> exo
    
- SFB locale \> Skype entreprise
    
- et Skype entreprise Online \> SFBO
    
En outre, * si un graphique de cet article a un objet «grisé» ou «grisé», cela signifie que l’élément affiché en gris **n’est pas** inclus dans la configuration propre à ma. * 
  
## <a name="read-the-summary"></a>Lire le résumé

Cette synthèse fait bouillir le processus en des étapes qui pourraient autrement être perdues pendant l’exécution, et est utile pour une liste de vérification globale pour assurer le suivi de l’endroit où vous vous trouvez dans le processus.
  
1. Tout d’abord, assurez-vous que vous remplissez toutes les conditions préalables.
    
1. Étant donné que de nombreuses **conditions préalables** sont communes pour Skype entreprise et Exchange, [consultez l’article de vue d’ensemble pour votre liste de vérification pré-req](hybrid-modern-auth-overview.md). Procédez comme suit *avant* de commencer l’une des étapes décrites dans cet article. 
    
2. Collectez les informations propres à la HMA dont vous aurez besoin dans un fichier, ou OneNote.
    
3. Activez l’authentification moderne pour EXO (si elle n’est pas déjà activée).
    
4. Activez l’authentification moderne pour SFBO (si elle n’est pas déjà activée).
    
5. Activez l’authentification moderne hybride pour Exchange sur site.
    
6. Activez l’authentification moderne hybride pour Skype entreprise en local.
    
Remarque ces étapes activent MA pour SFB, SFBO, EXCH et EXO, autrement dit, tous les produits pouvant participer à une configuration HMA de SFB et SFBO (y compris les dépendances de EXCH/EXO). En d’autres termes, si vos utilisateurs sont hébergés dans ou si des boîtes aux lettres sont créées dans n’importe quelle partie de l’environnement hybride (EXO + SFBO, EXO + SFB, EXCH + SFBO ou EXCH + SFB), votre produit fini se présente comme suit:
  
![Une topologie de 6 Skype entreprise HMA mixte est associée aux quatre emplacements possibles.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Comme vous pouvez le constater, il y a quatre emplacements différents pour activer MA! Pour une expérience utilisateur optimale, nous vous recommandons d’activer MA dans les quatre emplacements. Si vous ne pouvez pas activer l’agent de session sur tous ces emplacements, ajustez les étapes de façon à activer MA uniquement aux emplacements nécessaires pour votre environnement.
  
Consultez la rubrique relative à la [prise en charge de Skype entreprise avec ma](https://technet.microsoft.com/en-us/library/mt803262.aspx) pour les topologies prises en charge. 
  
 **Important** Vérifiez que vous avez rempli toutes les conditions préalables avant de commencer. Ces informations s’affichent [ici](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Collecter toutes les informations propres à la HMA

Une fois que vous avez vérifié que vous répondez aux [conditions préalables](hybrid-modern-auth-overview.md) pour utiliser l’authentification moderne (voir la remarque ci-dessus), vous devez créer un fichier pour conserver les informations dont vous aurez besoin pour configurer la mémoire haute définition dans les étapes à venir. Exemples utilisés dans cet article: 
  
- **Domaine SIP/SMTP**
    
  - Ex. contoso.com (est fédéré avec Office 365)
    
- **ID de locataire**
    
  - GUID qui représente votre client Office 365 (à la connexion de contoso.onmicrosoft.com).
    
- **URL du service Web SFB 2015 CU5**
    
Vous aurez besoin d’une URL de service Web interne et externe pour tous les pools SfB 2015 déployés. Pour obtenir ces informations, exécutez la commande suivante à partir de Skype entreprise Management Shell:
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. Internehttps://lyncwebint01.contoso.com
    
- Ex. Façonhttps://lyncwebext01.contoso.com
    
Si vous utilisez un serveur Standard Edition, l’URL interne sera vide. Dans ce cas, utilisez le nom de domaine complet du pool pour l’URL interne.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Activer l’authentification moderne pour EXO

Suivez les instructions ci-dessous: [Exchange Online: comment activer votre client pour l’authentification moderne.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Activer l’authentification moderne pour SFBO

Suivez les instructions ci-dessous: [Skype entreprise Online: activez votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Activer l’authentification moderne hybride pour Exchange sur site

Suivez les instructions ci-dessous: [procédure de configuration d’Exchange Server local pour utiliser l’authentification moderne hybride](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Activer l’authentification moderne hybride pour Skype entreprise en local

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajouter des URL de service Web sur site en tant que SPN dans Azure AD

À présent, vous devez exécuter des commandes pour ajouter les URL (collectées précédemment) en tant que principaux de service dans SFBO.
  
 **Note** Les noms de principaux du service (SPN) identifient les services Web et les associent à un principal de sécurité (par exemple, un nom de compte ou un groupe) afin que le service puisse agir au nom d’un utilisateur autorisé. Les clients qui s’authentifient sur un serveur utilisent les informations contenues dans les noms principaux de client. 
  
1. Tout d’abord, connectez-vous à AAD en utilisant [ces instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).
    
2. Exécutez cette commande, en local, pour obtenir la liste des URL de service Web SFB.

   Notez que le AppPrincipalId commence par `00000004`. Cela correspond à Skype entreprise online.
    
   Notez (et capture d’écran pour une comparaison ultérieure) la sortie de cette commande, qui inclura une URL SE et WS, mais qui se composent essentiellement `00000004-0000-0ff1-ce00-000000000000/`de noms principaux de service qui commencent par.
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. Si les URL SFB internes **ou** externes de l’organisation locale sont manquantes (par exemple https://lyncwebint01.contoso.com , https://lyncwebext01.contoso.com) nous devons ajouter ces enregistrements spécifiques à cette liste. 
    
    N’oubliez pas de remplacer *les exemples d’URL* ci-dessous par vos URL réelles dans la commande Add Commands! 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant de nouveau la commande Get-MsolServicePrincipal à partir de l’étape 2 et en examinant la sortie. Comparez la liste/capture d’écran de l’avant à la nouvelle liste de noms principaux de vente (vous pouvez également créer une capture d’écran de la nouvelle liste pour vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. À l’aide de notre exemple, la liste des SPN inclut désormais les URL https://lyncweb01.contoso.com spécifiques https://lyncwebext01.contoso.com/et.
    
### <a name="create-the-evosts-auth-server-object"></a>Créer l’objet serveur d’authentification EvoSTS

Exécutez la commande suivante dans Skype entreprise Management Shell.
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a>Activer l’authentification moderne hybride

Il s’agit de l’étape qui active l’agent de session. Toutes les étapes précédentes peuvent être exécutées à l’avance sans modifier le flux d’authentification du client. Lorsque vous êtes prêt à modifier le flux d’authentification, exécutez la commande suivante dans Skype for Business Management Shell. 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a>Vérifié

Une fois que vous activez HMA, la prochaine connexion d’un client utilisera le nouveau flux d’authentification. Notez que l’activation de la mémoire HMA ne déclenche pas une nouvelle authentification pour un client. Les clients se ré-authentifient en fonction de la durée de vie des jetons d’authentification et/ou des certificats dont ils disposent.
  
Pour tester que la haute-dernière fonctionne après l’avoir activée, déconnectez-vous d’un client Windows SFB de test et veillez à cliquer sur «supprimer mes informations d’identification». Reconnectez-vous. Le client doit maintenant utiliser le flux d’authentification moderne et votre connexion inclut désormais une invite **Office 365** pour un compte professionnel ou scolaire, vu juste avant que le client ne contacte le serveur et vous connecte. 
  
Vous devez également vérifier les «informations de configuration» pour les clients Skype entreprise pour une «autorité OAuth». Pour effectuer cette action sur votre ordinateur client, maintenez la touche CTRL enfoncée simultanément en cliquant avec le bouton droit sur l’icône Skype entreprise dans le bac de notification Windows. Cliquez sur informations de configuration dans le menu qui s’affiche. Dans la fenêtre «informations de configuration de Skype entreprise» qui s’affichent sur le bureau, recherchez les éléments suivants:
  
![Les informations de configuration d’un client Skype entreprise qui utilisent l’authentification moderne indiquent une URL d’autorisation OAUTH Lync https://login.windows.net/common/oauth2/authorizeet EWS de.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
Vous devez également maintenir la touche CTRL enfoncée en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans le bac Windows notifications) et cliquez sur «état de la connexion». Recherchez l’adresse SMTP du client par rapport à un type d’authentification «porteur\*», qui représente le jeton du porteur utilisé dans OAuth.
  
## <a name="related-articles"></a>Articles connexes

[Revenez à la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) . 
  
Avez-vous besoin de savoir comment utiliser l’authentification moderne (ADAL) pour vos clients Skype entreprise? Nous avons les étapes à suivre [ici](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
Souhaitez-vous lire ces étapes telles qu’elles apparaissent pour Exchange Server, en local, sans SFB? Ces étapes sont disponibles ici.
  

