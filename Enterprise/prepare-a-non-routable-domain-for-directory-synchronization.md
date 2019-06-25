---
title: Préparation d’un domaine non routable pour la synchronisation d’annuaires
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Pour savoir comment procéder, si vous avez un domaine non-routale associé à vos utilisateurs locaux avant de procéder à une synchronisation avec Office 365.
ms.openlocfilehash: cf7b901c3aaf6f49e4ecd92d27b9a6d9b8951d40
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203633"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="63cee-103">Préparation d’un domaine non routable pour la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="63cee-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="63cee-104">Lorsque vous synchronisez votre annuaire local avec Office 365, vous devez disposer d’un domaine vérifié dans Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="63cee-104">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory.</span></span> <span data-ttu-id="63cee-105">Seuls les noms d’utilisateur principal (UPN) associés au domaine local sont synchronisés.</span><span class="sxs-lookup"><span data-stu-id="63cee-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="63cee-106">Toutefois, tout nom UPN contenant un domaine non routable, par exemple. local (par exemple, Billa @ contoso. local), sera synchronisé avec un domaine. onmicrosoft.com (comme billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="63cee-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="63cee-107">Si vous utilisez actuellement un domaine. local pour vos comptes d’utilisateur dans Active Directory, il est recommandé de les modifier afin qu’ils utilisent un domaine vérifié (par exemple, billa@contoso.com) afin de se synchroniser correctement avec votre domaine Office 365.</span><span class="sxs-lookup"><span data-stu-id="63cee-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="63cee-108">Que se passe-t-il si j’ai uniquement un domaine local sur site?</span><span class="sxs-lookup"><span data-stu-id="63cee-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="63cee-109">Le dernier outil que vous pouvez utiliser pour synchroniser Active Directory avec Azure Active Directory est nommé Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="63cee-109">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect.</span></span> <span data-ttu-id="63cee-110">Pour plus d'informations, voir [Intégration de vos identités locales avec Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="63cee-110">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="63cee-111">Azure AD Connect synchronise le nom d’utilisateur et le mot de passe de vos utilisateurs afin que les utilisateurs puissent se connecter avec les mêmes informations d’identification qu’ils utilisent localement.</span><span class="sxs-lookup"><span data-stu-id="63cee-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="63cee-112">Toutefois, Azure AD Connect synchronise uniquement les utilisateurs avec les domaines qui sont vérifiés par Office 365.</span><span class="sxs-lookup"><span data-stu-id="63cee-112">However, Azure AD Connect only synchronizes users to domains that are verified by Office 365.</span></span> <span data-ttu-id="63cee-113">Cela signifie que le domaine est également vérifié par Azure Active Directory car les identités Office 365 sont gérées par Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="63cee-113">This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory.</span></span> <span data-ttu-id="63cee-114">En d’autres termes, le domaine doit être un domaine Internet valide (par exemple,. com,. org, .net,. US, etc.).</span><span class="sxs-lookup"><span data-stu-id="63cee-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="63cee-115">Si votre Active Directory interne utilise uniquement un domaine qui n’est pas routable (par exemple,. local), il ne peut pas correspondre au domaine vérifié que vous avez sur Office 365.</span><span class="sxs-lookup"><span data-stu-id="63cee-115">If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365.</span></span> <span data-ttu-id="63cee-116">Vous pouvez résoudre ce problème en modifiant votre domaine principal dans votre organisation Active Directory locale ou en ajoutant un ou plusieurs suffixes UPN.</span><span class="sxs-lookup"><span data-stu-id="63cee-116">You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="63cee-117">**Modifier votre domaine principal**</span><span class="sxs-lookup"><span data-stu-id="63cee-117">**Change your primary domain**</span></span>

<span data-ttu-id="63cee-118">Modifiez votre domaine principal en un domaine que vous avez vérifié dans Office 365, par exemple, contoso.com.</span><span class="sxs-lookup"><span data-stu-id="63cee-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="63cee-119">Chaque utilisateur ayant le domaine contoso. local est ensuite mis à jour vers contoso.com.</span><span class="sxs-lookup"><span data-stu-id="63cee-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="63cee-120">Pour obtenir des instructions, consultez [la rubrique How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span><span class="sxs-lookup"><span data-stu-id="63cee-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="63cee-121">Il s’agit d’un processus très important, mais une solution plus facile est décrite dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="63cee-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="63cee-122">**Ajouter des suffixes UPN et mettre à jour vos utilisateurs vers eux**</span><span class="sxs-lookup"><span data-stu-id="63cee-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="63cee-123">Vous pouvez résoudre le problème. local en enregistrant de nouveaux suffixes ou suffixes UPN dans Active Directory pour qu’ils correspondent au domaine (ou aux domaines) que vous avez vérifié dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="63cee-123">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365.</span></span> <span data-ttu-id="63cee-124">Après avoir enregistré le nouveau suffixe, vous mettez à jour l’utilisateur UPN pour remplacer le fichier. local par le nouveau nom de domaine par exemple, de sorte qu’un compte d’utilisateur ressemble à billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="63cee-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="63cee-125">Une fois que vous avez mis à jour l’UPN pour utiliser le domaine vérifié, vous êtes prêt à synchroniser votre annuaire Active Directory local avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="63cee-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="63cee-126">**Étape 1: ajouter le nouveau suffixe UPN**</span><span class="sxs-lookup"><span data-stu-id="63cee-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="63cee-127">Sur le serveur sur lequel s’exécutent les services de domaine Active Directory (AD DS), dans le gestionnaire de serveur, choisissez **Outils** \> **domaines et approbations Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="63cee-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="63cee-128">**Ou, si vous n’avez pas Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="63cee-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="63cee-129">Appuyez sur la **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez dans Domain. msc, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63cee-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Choisissez domaines et approbations Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="63cee-131">Dans la fenêtre **domaines et approbations Active Directory** , cliquez avec le bouton droit sur **domaines et approbations Active Directory**, puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="63cee-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Cliquez avec le bouton droit sur domaines et approbations ActiveDirectory, puis choisissez Propriétés.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="63cee-133">Dans l' **onglet suffixes UPN** , dans la zone **autres suffixes UPN** , tapez votre nouveau suffixe ou suffixe UPN, puis choisissez **Ajouter** \> \*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="63cee-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Ajouter un nouveau suffixe UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="63cee-135">Choisissez **OK** lorsque vous avez terminé d’ajouter des suffixes.</span><span class="sxs-lookup"><span data-stu-id="63cee-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="63cee-136">**Étape 2: modifier le suffixe UPN pour les utilisateurs existants**</span><span class="sxs-lookup"><span data-stu-id="63cee-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="63cee-137">Sur le serveur sur lequel s’exécute les services de domaine Active Directory (AD DS), dans le gestionnaire de serveur, sélectionnez **Outils** \> **utilisateurs et ordinateurs Active Directory Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="63cee-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="63cee-138">**Ou, si vous n’avez pas Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="63cee-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="63cee-139">Appuyez sur la **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez dsa. msc, puis cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="63cee-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="63cee-140">Sélectionnez un utilisateur, cliquez avec le bouton droit, puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="63cee-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="63cee-141">Dans l’onglet **compte** , dans la liste déroulante suffixe UPN, choisissez le nouveau suffixe UPN, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="63cee-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Ajouter un nouveau suffixe UPN pour un utilisateur](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="63cee-143">Effectuez ces étapes pour chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="63cee-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="63cee-144">**Vous pouvez également utiliser Windows PowerShell pour modifier le suffixe UPN pour tous les utilisateurs**</span><span class="sxs-lookup"><span data-stu-id="63cee-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="63cee-145">Si vous avez un grand nombre d’utilisateurs à mettre à jour, il est plus facile d’utiliser Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63cee-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="63cee-146">L’exemple suivant utilise les cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) et [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) pour remplacer tous les suffixes contoso. local par contoso.com.</span><span class="sxs-lookup"><span data-stu-id="63cee-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="63cee-147">Exécutez les commandes Windows PowerShell suivantes pour mettre à jour tous les suffixes contoso. local vers contoso.com:</span><span class="sxs-lookup"><span data-stu-id="63cee-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="63cee-148">Consultez la rubrique [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) pour en savoir plus sur l’utilisation de Windows PowerShell dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="63cee-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

