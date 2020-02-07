---
title: Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Résumé : Utilisez Windows PowerShell pour Office 365 pour ajouter un autre nom de domaine à un locataire de client existant.'
ms.openlocfilehash: 3097ac1574f946a8bd0c82eb25892107ce39b9be
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844275"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="77f10-103">Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="77f10-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="77f10-104">**Résumé :** Utilisez Windows PowerShell pour Office 365 pour ajouter un autre nom de domaine à un locataire de client existant.</span><span class="sxs-lookup"><span data-stu-id="77f10-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="77f10-105">Vous pouvez créer des domaines et les associer à la location de votre client avec Windows PowerShell pour Office 365 plus rapidement qu'en utilisant le Centre d'administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77f10-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="77f10-106">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="77f10-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="77f10-107">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="77f10-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="77f10-108">Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients.</span><span class="sxs-lookup"><span data-stu-id="77f10-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="77f10-109">Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations AOBO (Administrer au nom de) pour les locations clientes et peuvent donc gérer les locations du client et créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="77f10-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="77f10-110">Ce qu'il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="77f10-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="77f10-p102">Les procédures décrites dans cette rubrique exigent une connexion à Windows PowerShell pour Office 365. Pour plus d'informations, voir [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="77f10-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="77f10-113">Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.</span><span class="sxs-lookup"><span data-stu-id="77f10-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="77f10-114">Vous avez également besoin des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="77f10-114">You also need the following information:</span></span>
  
- <span data-ttu-id="77f10-115">Vous avez besoin du nom de domaine complet (FQDN) que votre client souhaite utiliser.</span><span class="sxs-lookup"><span data-stu-id="77f10-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="77f10-116">Vous avez besoin du code **TenantID** du client.</span><span class="sxs-lookup"><span data-stu-id="77f10-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="77f10-p103">Le nom de domaine complet doit être enregistré auprès d'un bureau d'enregistrement de domaines DNS Internet, comme GoDaddy. Pour plus d'informations sur l'inscription publique d'un nom de domaine, voir [Comment acheter un nom de domaine](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="77f10-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="77f10-p104">Vous devez savoir comment ajouter un enregistrement TXT à la zone DNS enregistrée pour votre bureau d'enregistrement DNS. Pour plus d'informations sur la façon d'ajouter un enregistrement TXT, voir [Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS pour Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.</span><span class="sxs-lookup"><span data-stu-id="77f10-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="77f10-122">Création de domaines</span><span class="sxs-lookup"><span data-stu-id="77f10-122">Create domains</span></span>

 <span data-ttu-id="77f10-p105">Vos clients vous demanderont probablement de créer des domaines supplémentaires à associer à leur location, car ils ne voudront probablement pas que le domaine<domain>.onmicrosoft.comsoit le domaine principal qui représente leur identité d'entreprise aux yeux du monde entier. Cette procédure vous guide au fil du processus de création d'un domaine associé à la location de votre client.</span><span class="sxs-lookup"><span data-stu-id="77f10-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="77f10-125">Pour effectuer certaines de ces opérations, le compte d’administrateur partenaire avec lequel vous vous connectez doit être défini sur **administration complète** pour le paramètre **attribuer un accès administratif aux sociétés que vous prenez en charge** figurant dans les détails du compte administrateur dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="77f10-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="77f10-126">Pour plus d'informations sur la gestion des rôles d'administrateur de partenaire, voir[Partenaires : proposer l'administration déléguée](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="77f10-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="77f10-127">Création du domaine dans Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="77f10-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="77f10-128">Cette commande crée le domaine dans Azure Active Directory, mais ne l'associe pas au domaine inscrit publiquement.</span><span class="sxs-lookup"><span data-stu-id="77f10-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="77f10-129">Cette association a lieu lorsque vous prouvez à Microsoft Office 365 pour entreprises que vous êtes propriétaire du domaine inscrit publiquement.</span><span class="sxs-lookup"><span data-stu-id="77f10-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="77f10-130">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="77f10-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="77f10-131">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77f10-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="77f10-132">Obtention des données pour l’enregistrement de vérification TXT DNS</span><span class="sxs-lookup"><span data-stu-id="77f10-132">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="77f10-p109">Office 365 générera les données spécifiques que vous devrez placer dans l'enregistrement de vérification TXT DNS. Pour obtenir les données, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="77f10-p109">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="77f10-135">Elle vous fournira des résultats semblables à :</span><span class="sxs-lookup"><span data-stu-id="77f10-135">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="77f10-136">Vous aurez besoin de ce texte pour créer l'enregistrement TXT dans la zone DNS enregistrée publiquement.</span><span class="sxs-lookup"><span data-stu-id="77f10-136">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="77f10-137">Copiez-le et enregistrez-le.</span><span class="sxs-lookup"><span data-stu-id="77f10-137">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="77f10-138">Ajout d’un enregistrement TXT à la zone DNS enregistrée publiquement</span><span class="sxs-lookup"><span data-stu-id="77f10-138">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="77f10-139">Avant qu'Office 365 ne commence à accepter le trafic dirigé vers le nom de domaine enregistré publiquement, vous devez prouver que vous êtes propriétaire du domaine et que vous disposez des autorisations d'administrateur pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="77f10-139">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="77f10-140">Pour prouver que vous êtes propriétaire du domaine, créez un enregistrement TXT dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="77f10-140">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="77f10-141">Un enregistrement TXT n'a aucun effet sur votre domaine, et il peut être supprimé une fois qu'il est établi que vous êtes propriétaire du domaine.</span><span class="sxs-lookup"><span data-stu-id="77f10-141">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="77f10-142">Pour créer les enregistrements TXT, suivez les procédures décrites dans [Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS pour Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="77f10-142">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="77f10-143">Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.</span><span class="sxs-lookup"><span data-stu-id="77f10-143">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="77f10-p112">Confirmez la création de l'enregistrement TXT via nslookup. Suivez cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="77f10-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="77f10-146">Elle vous fournira des résultats semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="77f10-146">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="77f10-147">Confirmation de la propriété du domaine dans Office 365</span><span class="sxs-lookup"><span data-stu-id="77f10-147">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="77f10-p113">Dans cette dernière étape, vous confirmez à Office 365 que vous êtes propriétaire du domaine inscrit publiquement. Après cette étape, Office 365 va commencer à accepter le trafic acheminé vers le nouveau nom de domaine. Pour terminer la création du domaine et le processus d'inscription, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="77f10-p113">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="77f10-151">Cette commande ne renvoie aucun résultat, par conséquent, pour vérifier qu’elle a fonctionné, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="77f10-151">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="77f10-152">Celle-ci renverra des résultats semblables à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="77f10-152">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="77f10-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77f10-153">See also</span></span>

#### 

[<span data-ttu-id="77f10-154">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="77f10-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

