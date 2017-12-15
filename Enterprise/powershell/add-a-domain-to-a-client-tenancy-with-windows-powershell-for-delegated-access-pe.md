---
title: "Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "Résumé : Utilisez Windows PowerShell pour Office 365 pour ajouter un autre nom de domaine à un locataire de client existant."
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="62b5e-103">Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="62b5e-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="62b5e-104">**Résumé :** Utiliser Windows PowerShell pour Office 365 pour ajouter un nom de domaine de remplacement à un locataire client existant.</span><span class="sxs-lookup"><span data-stu-id="62b5e-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="62b5e-105">Vous pouvez créer de nouveaux domaines et les associer à la location de votre client avec Windows PowerShell pour Office 365 plus rapidement qu'en utilisant le Centre d'administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="62b5e-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Office 365 admin center.</span></span>
  
<span data-ttu-id="62b5e-p101">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients. Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations Administrer au nom de sur leslocations clientes. Ainsi, ils peuvent administrer les locations clientes et créer des rapports les concernant.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p101">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="62b5e-110">Ce qu'il faut savoir avant de commencer ?</span><span class="sxs-lookup"><span data-stu-id="62b5e-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="62b5e-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="62b5e-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="62b5e-112">Vous avez également besoin des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="62b5e-112">You also need the following information:</span></span>
  
- <span data-ttu-id="62b5e-113">Vous avez besoin du nom de domaine complet (FQDN) que votre client souhaite utiliser.</span><span class="sxs-lookup"><span data-stu-id="62b5e-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="62b5e-114">Vous avez besoin du code **TenantID** du client.</span><span class="sxs-lookup"><span data-stu-id="62b5e-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="62b5e-p102">Le nom de domaine complet doit être enregistré auprès d'un bureau d'enregistrement de domaines DNS Internet, comme GoDaddy. Pour plus d'informations sur l'inscription publique d'un nom de domaine, voir [Comment acheter un nom de domaine](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="62b5e-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="62b5e-p103">Vous devez savoir comment ajouter un enregistrement TXT à la zone DNS enregistrée pour votre bureau d'enregistrement DNS. Pour plus d'informations sur la façon d'ajouter un enregistrement TXT, voir [Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS pour Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="62b5e-120">Création de domaines</span><span class="sxs-lookup"><span data-stu-id="62b5e-120">Create domains</span></span>

 <span data-ttu-id="62b5e-p104">Vos clients vous demanderont probablement de créer des domaines supplémentaires à associer à leur location, car ils ne voudront probablement pas que le domaine<domain>.onmicrosoft.comsoit le domaine principal qui représente leur identité d'entreprise aux yeux du monde entier. Cette procédure vous guide au fil du processus de création d'un domaine associé à la location de votre client.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62b5e-p105">Pour effectuer certaines de ces opérations, le compte administrateur partenaire auquel vous vous connectez doit être défini sur **Administration complète** pour le paramètre **Accorder un accès administrateur aux sociétés que vous assistez** qui se trouve dans les détails du compte administrateur dans le Centre d'administration Office 365. Pour plus d'informations sur la gestion des rôles d'administrateur de partenaire, voir[Partenaires : proposer l'administration déléguée](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="62b5e-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="62b5e-125">Création du domaine dans Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="62b5e-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="62b5e-p106">Cette commande crée le domaine dans Azure Active Directory, mais ne l'associe pas au domaine inscrit publiquement. Cette association a lieu lorsque vous prouvez à Microsoft Office 365 pour les entreprises que vous êtes propriétaire du domaine inscrit publiquement.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p106">This command creates the domain in Azure Active Directory but does not associate it with the publically registered domain. That comes when you prove that you own the publically registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="62b5e-128">Obtention des données pour l'enregistrement de vérification TXT DNS</span><span class="sxs-lookup"><span data-stu-id="62b5e-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="62b5e-p107">Office 365 générera les données spécifiques que vous devrez placer dans l'enregistrement de vérification TXT DNS. Pour obtenir les données, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="62b5e-131">Elle vous fournira des résultats semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="62b5e-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="62b5e-p108">Vous aurez besoin de ce texte pour créer l'enregistrement TXT dans la zone DNS enregistrée publiquement. Copiez-le et enregistrez-le.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p108">You will need this text to create the TXT record in the publically registered DNS zone. Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="62b5e-134">Ajout d'un enregistrement TXT à la zone DNS enregistrée publiquement</span><span class="sxs-lookup"><span data-stu-id="62b5e-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="62b5e-p109">Avant qu'Office 365 commence à accepter le trafic dirigé vers le nom de domaine enregistré publiquement, vous devez prouver que vous êtes propriétaire du domaine et que vous disposez des autorisations d'administrateur pour celui-ci. Pour prouver que vous êtes propriétaire du domaine, créez un enregistrement TXT dans le domaine. Un enregistrement TXT n'a aucun effet sur votre domaine, et il peut être supprimé une fois qu'il est établi que vous êtes propriétaire du domaine. Pour créer les enregistrements TXT, suivez les procédures décrites dans [Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS pour Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p109">Before Office 365 will start accepting traffic that is directed to the publically registered domain name, you must prove that you own and have administrator permissions to the domain. You prove you own the domain by creating a TXT record in the domain. A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established. To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="62b5e-p110">Confirmez la création de l'enregistrement TXT via nslookup. Suivez cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="62b5e-142">Elle vous fournira des résultats semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="62b5e-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="62b5e-143">Confirmation de la propriété du domaine dans Office 365</span><span class="sxs-lookup"><span data-stu-id="62b5e-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="62b5e-p111">Dans cette dernière étape, vous confirmez à Office 365 que vous êtes propriétaire du domaine inscrit publiquement. Après cette étape, Office 365 va commencer à accepter le trafic acheminé vers le nouveau nom de domaine. Pour terminer la création du domaine et le processus d'inscription, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="62b5e-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="62b5e-147">Cette commande ne renvoie aucun résultat, par conséquent, pour vérifier qu'elle a fonctionné, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="62b5e-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="62b5e-148">Celle-ci renverra des résultats semblables à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="62b5e-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="62b5e-149">See also</span><span class="sxs-lookup"><span data-stu-id="62b5e-149">See also</span></span>

#### 

[<span data-ttu-id="62b5e-150">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="62b5e-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

