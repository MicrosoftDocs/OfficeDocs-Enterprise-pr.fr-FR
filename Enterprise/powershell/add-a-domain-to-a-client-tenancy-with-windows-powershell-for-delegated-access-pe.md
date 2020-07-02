---
title: Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Résumé : utilisez Windows PowerShell pour Microsoft 365 pour ajouter un autre nom de domaine à un client existant.'
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997360"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

Vous pouvez créer et associer de nouveaux domaines à la location de votre client avec Windows PowerShell pour Microsoft 365 plus rapidement que l’utilisation du centre d’administration Microsoft 365.
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients. Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.
  
Vous avez également besoin des informations suivantes :
  
- Vous avez besoin du nom de domaine complet (FQDN) que votre client souhaite utiliser.
    
- Vous avez besoin du code **TenantID** du client.
    
- The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Vous devez savoir comment ajouter un enregistrement TXT à la zone DNS enregistrée pour votre bureau d’enregistrement DNS. Pour plus d’informations sur l’ajout d’un enregistrement TXT, consultez la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d’enregistrement DNS.
    
## <a name="create-domains"></a>Création de domaines

 Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.
  
> [!NOTE]
> Pour effectuer certaines de ces opérations, le compte d’administrateur partenaire avec lequel vous vous connectez doit être défini sur **administration complète** pour le paramètre **attribuer un accès administratif aux sociétés que vous prenez en charge** figurant dans les détails du compte administrateur dans le centre d’administration 365 de Microsoft. Pour plus d’informations sur la gestion des rôles d’administrateur partenaire, consultez la rubrique [partenaires : proposer une administration déléguée](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Création du domaine dans Azure Active Directory

Cette commande crée le domaine dans Azure Active Directory, mais ne l'associe pas au domaine inscrit publiquement. Cela vient lorsque vous prouvez que vous êtes propriétaire du domaine inscrit publiquement à Microsoft Microsoft 365 pour les entreprises.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Obtention des données pour l’enregistrement de vérification TXT DNS

 Microsoft 365 générera les données spécifiques que vous devez placer dans l’enregistrement de vérification TXT DNS. Pour obtenir les données, exécutez cette commande.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Elle vous fournira des résultats semblables à :
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Vous aurez besoin de ce texte pour créer l'enregistrement TXT dans la zone DNS enregistrée publiquement. Copiez-le et enregistrez-le. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Ajout d’un enregistrement TXT à la zone DNS enregistrée publiquement

Avant que Microsoft 365 n’accepte le trafic qui est dirigé vers le nom de domaine enregistré publiquement, vous devez prouver que vous êtes propriétaire du domaine et que vous disposez d’autorisations d’administrateur. Pour prouver que vous êtes propriétaire du domaine, créez un enregistrement TXT dans le domaine. Un enregistrement TXT n'a aucun effet sur votre domaine, et il peut être supprimé une fois qu'il est établi que vous êtes propriétaire du domaine. Pour créer les enregistrements TXT, suivez les procédures de la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.
  
Confirm the successful creation of the TXT record via nslookup. Follow this syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Elle vous fournira des résultats semblables à ceci :
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>Valider la propriété de domaine dans Microsoft 365

Dans cette dernière étape, vous validez auprès de Microsoft 365 que vous êtes propriétaire du domaine inscrit publiquement. Après cette étape, Microsoft 365 commencera à accepter le trafic acheminé vers le nouveau nom de domaine. Pour terminer la création du domaine et le processus d’inscription, exécutez cette commande. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Cette commande ne renvoie aucun résultat, par conséquent, pour vérifier qu’elle a fonctionné, exécutez la commande suivante.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Celle-ci renverra des résultats semblables à ce qui suit.
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>Voir aussi

#### 

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)

