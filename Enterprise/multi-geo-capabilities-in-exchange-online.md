---
title: Fonctionnalités multi-localisés dans Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Développez votre présence d’Office 365 à plusieurs régions géographiques avec des capacités multi-localisés dans Exchange Online.
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200737"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="789f0-103">Fonctionnalités multi-localisés dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="789f0-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="789f0-p101">Fonctionnalités multi-localisés dans Office 365 activer un seul client de couvrir plusieurs emplacements géographiques. Lorsque multi-geo est activée, les clients pouvant sélectionner l’emplacement du contenu des boîtes aux lettres Exchange Online (données au repos) par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="789f0-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="789f0-p102">Votre emplacement initiale du client (désigné comme emplacement central) est déterminée en fonction de votre adresse de facturation. Lorsque multi-geo est activé, vous pouvez placer des boîtes aux lettres dans les emplacements satellites supplémentaires par :</span><span class="sxs-lookup"><span data-stu-id="789f0-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="789f0-108">Création d’une nouvelle boîte aux lettres Exchange Online directement dans un emplacement satellites.</span><span class="sxs-lookup"><span data-stu-id="789f0-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="789f0-109">Déplacement d’une boîte aux lettres Exchange Online existant dans un emplacement satellites.</span><span class="sxs-lookup"><span data-stu-id="789f0-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="789f0-110">Intégration d’une boîte aux lettres d’une organisation d’Exchange sur site directement dans un emplacement satellites.</span><span class="sxs-lookup"><span data-stu-id="789f0-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="789f0-111">Geo aux emplacements suivants sont disponibles pour une utilisation dans une configuration Multi-localisés :</span><span class="sxs-lookup"><span data-stu-id="789f0-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="789f0-112">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="789f0-112">Asia Pacific</span></span>

- <span data-ttu-id="789f0-113">Australie</span><span class="sxs-lookup"><span data-stu-id="789f0-113">Australia</span></span>

- <span data-ttu-id="789f0-114">Canada</span><span class="sxs-lookup"><span data-stu-id="789f0-114">Canada</span></span>

- <span data-ttu-id="789f0-115">Union européenne</span><span class="sxs-lookup"><span data-stu-id="789f0-115">European Union</span></span>

- <span data-ttu-id="789f0-116">France</span><span class="sxs-lookup"><span data-stu-id="789f0-116">France</span></span>

- <span data-ttu-id="789f0-117">Inde</span><span class="sxs-lookup"><span data-stu-id="789f0-117">India</span></span>

- <span data-ttu-id="789f0-118">Japon</span><span class="sxs-lookup"><span data-stu-id="789f0-118">Japan</span></span>

- <span data-ttu-id="789f0-119">Corée</span><span class="sxs-lookup"><span data-stu-id="789f0-119">Korea</span></span>

- <span data-ttu-id="789f0-120">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="789f0-120">United Kingdom</span></span>

- <span data-ttu-id="789f0-121">États-Unis</span><span class="sxs-lookup"><span data-stu-id="789f0-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="789f0-122">Configuration du logiciel requis</span><span class="sxs-lookup"><span data-stu-id="789f0-122">Prerequisite configuration</span></span>
<span data-ttu-id="789f0-p103">Avant de pouvoir commencer à l’aide de fonctionnalités Multi-localisés dans Exchange Online, Microsoft a besoin configurer votre client pour la prise en charge multi-geo Exchange Online. Ce processus de configuration unique est déclenché une fois que vous commandez Qu'office 365 Multi-localisés et les licences s’affichent-ils dans votre client. Ce processus de configuration unique adopter généralement moins de 30 jours. Pour Office 365 Multi-localisés, contactez votre représentant Microsoft. Pour plus d’informations, voir https://aka.ms/Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="789f0-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="789f0-p104">Vous allez recevoir des notifications dans le [Centre de messages Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) lorsque votre configuration est terminée. Configuration est automatiquement déclenchée une fois vos licences multi-geo s’affichent-ils dans votre client.</span><span class="sxs-lookup"><span data-stu-id="789f0-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="789f0-130">Déplacements et l’emplacement de la boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="789f0-130">Mailbox placement and moves</span></span>
<span data-ttu-id="789f0-131">Microsoft après les étapes de configuration multi-localisés requis, Exchange Online respecte l’attribut **PreferredDataLocation** sur les objets utilisateur dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="789f0-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="789f0-p105">Exchange Online synchronise la propriété **PreferredDataLocation** d’Azure Active Directory dans la propriété **MailboxRegion** dans le service d’annuaire Exchange Online. La valeur de **MailboxRegion** détermine le géographique où les boîtes aux lettres utilisateur et des boîtes aux lettres d’archive associé seront placées. Il n’est pas possible de configurer principales boîte aux lettres et archivage boîtes aux lettres un utilisateur pour résident dans des emplacements différents localisés. Qu’un seul emplacement géographique peut être configuré par l’objet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="789f0-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="789f0-136">Lorsque **PreferredDataLocation** est configuré sur un utilisateur disposant d’une boîte aux lettres existante, la boîte aux lettres est de placer dans une file d’attente de déplacement et automatiquement déplacés vers l’emplacement géographique spécifié.</span><span class="sxs-lookup"><span data-stu-id="789f0-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="789f0-137">Lorsque **PreferredDataLocation** est configuré sur un utilisateur sans une boîte aux lettres existante, la boîte aux lettres système mis en service à l’emplacement géographique spécifié.</span><span class="sxs-lookup"><span data-stu-id="789f0-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="789f0-138">Lorsque **PreferredDataLocation** sur un utilisateur n’est pas spécifié, la boîte aux lettres est placé dans le site central.</span><span class="sxs-lookup"><span data-stu-id="789f0-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="789f0-139">Si le code **PreferredDataLocation** est incorrect (par exemple, un type de NAN au lieu du nom), la boîte aux lettres est placé dans le site central.</span><span class="sxs-lookup"><span data-stu-id="789f0-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="789f0-p106">**Remarque**: fonctionnalités multi-geo et Skype pour les réunions en ligne Business régional hébergée par les deux permet de la propriété **PreferredDataLocation** sur les objets utilisateur localisent les services. Si vous configurez des valeurs **PreferredDataLocation** sur les objets utilisateur pour les réunions régional hébergées, la boîte aux lettres pour ces utilisateurs est automatiquement déplacée vers l’emplacement géographique spécifiée après que multi-geo est activée sur le client Office 365.</span><span class="sxs-lookup"><span data-stu-id="789f0-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="789f0-142">Limitations des fonctions pour Multi-localisés dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="789f0-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="789f0-p107">Uniquement les boîtes aux lettres, les boîtes aux lettres de ressources (boîtes aux lettres de salles et équipements) et boîtes aux lettres partagées prennent en charge les fonctionnalités multi-localisés. Boîtes aux lettres de dossier public et de groupes d’Office 365 restent dans l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="789f0-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="789f0-p108">Sécurité et conformité fonctionnalités (par exemple, l’audit et découverte électronique) qui sont disponibles dans le centre d’administration Exchange (CAE) ne sont pas disponibles dans les organisations multi-localisés. Au lieu de cela, vous devez utiliser [Office 365 sécurité & centre de conformité](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="789f0-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="789f0-p109">Outlook pour Mac peut-être entraîner une perte temporaire de l’accès à leur dossier Archive en ligne pendant que vous déplacez leur boîte aux lettres vers un nouvel emplacement géographique. Cette condition se produit lorsque le serveur principal de l’utilisateur archive les boîtes aux lettres sont localisés différents endroits, car les déplacements de boîtes aux lettres cross-Geo peuvent terminer à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="789f0-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="789f0-p110">Les utilisateurs ne peuvent pas partager des *dossiers de boîte aux lettres* entre les différents emplacements localisés dans Outlook sur le web (anciennement appelé Outlook Web App ou OWA). Par exemple, un utilisateur dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé dans une boîte aux lettres qui se trouve aux États-Unis. Toutefois, Outlook sur les utilisateurs Web pouvez ouvrir les *autres boîtes aux lettres* dans différentes zones géographiques à l’aide d’une fenêtre de navigateur distincte comme décrit dans [Ouvrir la boîte aux lettres d’une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="789f0-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="789f0-152">**Remarque**: partage de dossiers de boîte aux lettres Cross-geo est pris en charge dans Outlook sur Windows.</span><span class="sxs-lookup"><span data-stu-id="789f0-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="789f0-153">Administration</span><span class="sxs-lookup"><span data-stu-id="789f0-153">Administration</span></span> 
<span data-ttu-id="789f0-p111">PowerShell distant est nécessaire pour afficher et configurer les propriétés de géolocalisation multiples dans votre environnement Office 365. Pour plus d’informations sur les différents modules PowerShell permettant de gérer Office 365, voir [Gérer Office 365 et Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="789f0-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="789f0-p112">Vous devez le [Module Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version ultérieure d’en 1.x pour voir la propriété **PreferredDataLocation** sur les objets utilisateur. Les objets utilisateur synchronisés via DAS Connect dans DAS ne peut pas avoir à leur valeur **PreferredDataLocation** modifiée directement via PowerShell DAS. Les objets utilisateur en nuage uniquement peuvent être modifiés via PowerShell DAS. Pour vous connecter à Windows Azure AD PowerShell, voir [se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="789f0-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="789f0-160">Pour vous connecter à Exchange Online PowerShell, voir [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="789f0-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="789f0-161">Vous connecter directement à une région à l’aide d’Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="789f0-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="789f0-p113">En règle générale, Exchange Online PowerShell se connecte à l’emplacement de géolocalisation par défaut. Mais, vous pouvez également vous connecter directement à des emplacements par défaut non localisés. En raison des améliorations des performances, nous vous recommandons de connexion directement à l’emplacement géographique non par défaut lorsque vous gérez uniquement les utilisateurs de cet emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="789f0-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="789f0-p114">Pour vous connecter à une région, le paramètre *ConnectionUri* est différent dans les instructions de connexion standard. Le reste des commandes et valeurs sont les mêmes. Les étapes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="789f0-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="789f0-168">Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="789f0-169">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre bureau ou une école et mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="789f0-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="789f0-p115">Remplacez `<emailaddress>` avec l’adresse de messagerie **d’une** boîte aux lettres dans l’emplacement géographique de cible et exécutez la commande suivante. Vos autorisations sur la boîte aux lettres et de la relation à vos informations d’identification à l’étape 1 ne sont pas un facteur ; l’adresse de messagerie simplement indique à Exchange Online où se connecter.</span><span class="sxs-lookup"><span data-stu-id="789f0-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="789f0-172">Par exemple, si olga@contoso.onmicrosoft.com est l’adresse de messagerie d’une boîte aux lettres valide dans le localisés que vous souhaitez vous connecter, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="789f0-173">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="789f0-174">Azure AD Connect version requise</span><span class="sxs-lookup"><span data-stu-id="789f0-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="789f0-p116">Connexion DAS version 1.1.524.0 ou version ultérieur est le seul moyen pour définir la propriété **PreferredDataLocation** sur les objets utilisateur qui sont synchronisés de sur site Active Directory. Les objets utilisateur synchronisés via DAS Connect dans DAS ne peut pas avoir à leur valeur **PreferredDataLocation** modifiée directement via PowerShell DAS. Les objets utilisateur en nuage uniquement peuvent être modifiés via PowerShell DAS. Pour des instructions détaillées, consultez la rubrique [synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="789f0-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="789f0-179">Codes localisés</span><span class="sxs-lookup"><span data-stu-id="789f0-179">Geo Codes</span></span>
<span data-ttu-id="789f0-p117">Codes de trois lettres vous permet de spécifier la localisés dans la propriété **PreferredDataLocation** . Le tableau suivant répertorie les codes pour les zones géographiques disponibles :</span><span class="sxs-lookup"><span data-stu-id="789f0-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="789f0-182">Géo</span><span class="sxs-lookup"><span data-stu-id="789f0-182">Geo</span></span> |<span data-ttu-id="789f0-183">Code</span><span class="sxs-lookup"><span data-stu-id="789f0-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="789f0-184">Asie/Pacifique</span><span class="sxs-lookup"><span data-stu-id="789f0-184">Asia/Pacific</span></span> |<span data-ttu-id="789f0-185">APC</span><span class="sxs-lookup"><span data-stu-id="789f0-185">APC</span></span> |
|<span data-ttu-id="789f0-186">Australie</span><span class="sxs-lookup"><span data-stu-id="789f0-186">Australia</span></span> |<span data-ttu-id="789f0-187">AUS</span><span class="sxs-lookup"><span data-stu-id="789f0-187">AUS</span></span> |
|<span data-ttu-id="789f0-188">Canada</span><span class="sxs-lookup"><span data-stu-id="789f0-188">Canada</span></span> |<span data-ttu-id="789f0-189">CAN</span><span class="sxs-lookup"><span data-stu-id="789f0-189">CAN</span></span> |
|<span data-ttu-id="789f0-190">Union européenne</span><span class="sxs-lookup"><span data-stu-id="789f0-190">European Union</span></span> |<span data-ttu-id="789f0-191">EUR</span><span class="sxs-lookup"><span data-stu-id="789f0-191">EUR</span></span> |
|<span data-ttu-id="789f0-192">France</span><span class="sxs-lookup"><span data-stu-id="789f0-192">France</span></span> |<span data-ttu-id="789f0-193">FRA</span><span class="sxs-lookup"><span data-stu-id="789f0-193">FRA</span></span>|
|<span data-ttu-id="789f0-194">Inde</span><span class="sxs-lookup"><span data-stu-id="789f0-194">India</span></span> |<span data-ttu-id="789f0-195">IND</span><span class="sxs-lookup"><span data-stu-id="789f0-195">IND</span></span> |
|<span data-ttu-id="789f0-196">Japon</span><span class="sxs-lookup"><span data-stu-id="789f0-196">Japan</span></span> |<span data-ttu-id="789f0-197">JPN</span><span class="sxs-lookup"><span data-stu-id="789f0-197">JPN</span></span> |
|<span data-ttu-id="789f0-198">Corée</span><span class="sxs-lookup"><span data-stu-id="789f0-198">Korea</span></span> |<span data-ttu-id="789f0-199">KOR</span><span class="sxs-lookup"><span data-stu-id="789f0-199">KOR</span></span> |
|<span data-ttu-id="789f0-200">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="789f0-200">United Kingdom</span></span> |<span data-ttu-id="789f0-201">GBR</span><span class="sxs-lookup"><span data-stu-id="789f0-201">GBR</span></span> |
|<span data-ttu-id="789f0-202">États-Unis</span><span class="sxs-lookup"><span data-stu-id="789f0-202">United States</span></span> |<span data-ttu-id="789f0-203">NAM</span><span class="sxs-lookup"><span data-stu-id="789f0-203">NAM</span></span> |

<span data-ttu-id="789f0-p118">**Remarque**: les propriétés **PreferredDataLocation** et **MailboxRegion** sont des chaînes avec aucune vérification des erreurs. Si vous entrez une valeur non valide (par exemple, NAN), que la boîte aux lettres est placé dans la valeur par défaut localisés.</span><span class="sxs-lookup"><span data-stu-id="789f0-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="789f0-206">Afficher les zones géographiques disponibles qui sont configurées dans votre organisation Exchange Online</span><span class="sxs-lookup"><span data-stu-id="789f0-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="789f0-207">Pour afficher la liste des zones géographiques configurées dans votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :</span><span class="sxs-lookup"><span data-stu-id="789f0-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="789f0-208">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="789f0-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="789f0-209">Afficher la valeur par défaut géographique de votre organisation Exchange Online</span><span class="sxs-lookup"><span data-stu-id="789f0-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="789f0-210">Pour afficher la localisés par défaut de votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :</span><span class="sxs-lookup"><span data-stu-id="789f0-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="789f0-211">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="789f0-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="789f0-212">Rechercher l’emplacement géographique d’une boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="789f0-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="789f0-213">Propriétés de boîtes aux lettres associées à l’applet de commande **Get-Mailbox** dans Exchange Online PowerShell affiche le multi-geo suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="789f0-p119">**Base de données**: les 3 lettres du nom de base de données correspondent au code localisés, qui indique où se trouve actuellement la boîte aux lettres. Propriété doit être utilisée pour **ArchiveDatabase** de Online Archive boîtes aux lettres.</span><span class="sxs-lookup"><span data-stu-id="789f0-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="789f0-216">**MailboxRegion**: Spécifie le code d’emplacement géographique qui a été défini par l’administrateur (synchronisée à partir de **PreferredDataLocation** dans Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="789f0-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="789f0-217">**MailboxRegionLastUpdateTime**: indique quand MailboxRegion a été modifiée (automatiquement ou manuellement).</span><span class="sxs-lookup"><span data-stu-id="789f0-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="789f0-218">Pour afficher les propriétés d’une boîte aux lettres, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="789f0-219">Par exemple, pour afficher les informations de localisés de la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="789f0-220">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="789f0-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="789f0-221">**Remarque :** Si le code d’emplacement géographique dans le nom de base de données ne correspond pas à la valeur de **MailboxRegion** , la boîte aux lettres sera automatiquement à placer dans une file d’attente de déplacement et déplacée vers l’emplacement géographique spécifié par la valeur **MailboxRegion** (Exchange Online cherche une non-concordance entre ces valeurs de propriété).</span><span class="sxs-lookup"><span data-stu-id="789f0-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="789f0-222">Déplacer une boîte aux lettres en nuage uniquement existante à une région</span><span class="sxs-lookup"><span data-stu-id="789f0-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="789f0-p120">Un utilisateur en nuage uniquement est un utilisateur pas opération au client via DAS Connect. Cet utilisateur a été créé directement dans Azure AD. Utilisez les applets de commande **Get-MsolUser** et **Set-MsolUser** dans le Module Azure AD pour Windows PowerShell pour afficher ou spécifier la zone géographique où seront stockés les boîtes aux lettres d’un utilisateur en nuage uniquement.</span><span class="sxs-lookup"><span data-stu-id="789f0-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="789f0-226">Pour afficher la valeur **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="789f0-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="789f0-227">Par exemple, pour afficher la valeur **PreferredDataLocation** pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="789f0-228">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="789f0-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="789f0-229">Pour modifier la valeur **PreferredDataLocation** pour un objet utilisateur en nuage uniquement, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="789f0-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="789f0-230">Par exemple, pour définir la valeur **PreferredDataLocation** à l’Union européenne (EUR) localisés pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="789f0-231">**Remarques** :</span><span class="sxs-lookup"><span data-stu-id="789f0-231">**Notes**:</span></span>

- <span data-ttu-id="789f0-p121">Comme mentionné précédemment vous ne pouvez pas utiliser cette procédure pour les objets utilisateur synchronisé de sur site Active Directory. Vous devez modifier la valeur **PreferredDataLocation** à l’aide de DAS se connecter. Pour plus d’informations, voir [synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="789f0-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="789f0-235">La durée nécessaire pour déplacer un mailboxfrom que son geo actuel vers le nouvel emplacement géographique de votre choix dépend de plusieurs facteurs :</span><span class="sxs-lookup"><span data-stu-id="789f0-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="789f0-236">La taille et le type de boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="789f0-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="789f0-237">Le nombre de boîtes aux lettres en cours de déplacement.</span><span class="sxs-lookup"><span data-stu-id="789f0-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="789f0-238">La disponibilité des ressources de déplacement.</span><span class="sxs-lookup"><span data-stu-id="789f0-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="789f0-239">Déplacement désactivé les boîtes aux lettres en conservation pour litige</span><span class="sxs-lookup"><span data-stu-id="789f0-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="789f0-p122">Désactivé les boîtes aux lettres en conservation pour litige sont conservées pour la découverte électronique à des fins ne peuvent pas être déplacés en modifiant leur valeur **PreferredDataLocation** dans leur état désactivé. Pour déplacer une boîte aux lettres désactivée en attente pour litige :</span><span class="sxs-lookup"><span data-stu-id="789f0-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="789f0-242">Temporairement attribuer une licence à la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="789f0-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="789f0-243">Modifier la **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="789f0-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="789f0-244">Supprimer la licence de la boîte aux lettres après que qu’il a été déplacée vers l’emplacement géographique sélectionné à replacer dans un état désactivé.</span><span class="sxs-lookup"><span data-stu-id="789f0-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="789f0-245">Créer des nouvelles boîtes aux lettres en nuage dans une région</span><span class="sxs-lookup"><span data-stu-id="789f0-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="789f0-246">Pour créer une nouvelle boîte aux lettres dans un emplacement géographique spécifique, vous devez effectuer une de ces étapes :</span><span class="sxs-lookup"><span data-stu-id="789f0-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="789f0-p123">Configurer la valeur **PreferredDataLocation** , comme décrit dans la précédente section *avant de* que la boîte aux lettres est créé dans Exchange Online. Par exemple, configurez la valeur de **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence.</span><span class="sxs-lookup"><span data-stu-id="789f0-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="789f0-249">Attribuer une licence en même temps que vous définissez la valeur **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="789f0-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="789f0-250">Pour créer un nouvel en nuage uniquement sous licence utilisateur (DAS se connectent pas synchronisé) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Windows Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="789f0-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="789f0-251">Cet exemple montre comment créer un nouveau compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="789f0-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="789f0-252">Nom d’utilisateur principal : ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="789f0-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="789f0-253">Prénom : Elizabeth</span><span class="sxs-lookup"><span data-stu-id="789f0-253">First name: Elizabeth</span></span>

- <span data-ttu-id="789f0-254">Nom : Alain Durand</span><span class="sxs-lookup"><span data-stu-id="789f0-254">Last name: Brunner</span></span>

- <span data-ttu-id="789f0-255">Nom d’affichage Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="789f0-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="789f0-256">Mot de passe : générée de manière aléatoire et affichées dans les résultats de la commande (parce que nous n’utilisons pas le paramètre de *mot de passe* )</span><span class="sxs-lookup"><span data-stu-id="789f0-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="789f0-257">Licence : contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="789f0-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="789f0-258">Emplacement : Australie (Australie)</span><span class="sxs-lookup"><span data-stu-id="789f0-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="789f0-259">Pour plus d’informations sur la création de nouveaux comptes d’utilisateur et de rechercher des valeurs LicenseAssignment dans Windows Azure AD PowerShell, voir [créer les comptes d’utilisateurs avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) et [Afficher les licences et les services Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="789f0-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="789f0-p124">**Remarque :** Si vous utilisez Exchange Online PowerShell pour activer une boîte aux lettres et doivent être créées directement dans le localisés qui est spécifié dans **PreferredDataLocation**la boîte aux lettres, vous devez utiliser une cmdlet comme **Enable-Mailbox** ou \*\*New-boîte aux lettres Exchange Online \*\*directement sur le service en nuage. Si vous utilisez l’applet de commande **Enable-RemoteMailbox** locale Exchange, la boîte aux lettres sera créée dans la valeur par défaut localisés.</span><span class="sxs-lookup"><span data-stu-id="789f0-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="789f0-262">Intégré existant boîtes aux lettres locales dans une région</span><span class="sxs-lookup"><span data-stu-id="789f0-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="789f0-263">Vous pouvez utiliser les outils d’intégration standard et les processus pour migrer une boîte aux lettres d’une organisation d’Exchange local vers Exchange Online, y compris le [tableau de bord de Migration dans le CAE](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)et l’applet de commande [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) dans Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="789f0-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="789f0-p125">La première étape consiste à vérifier qu'un objet utilisateur existe pour chaque boîte aux lettres onboarded, et vérifiez que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migreront les boîtes aux lettres directement à la Geo spécifié.</span><span class="sxs-lookup"><span data-stu-id="789f0-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="789f0-266">Ou bien, vous pouvez utiliser les étapes suivantes pour les boîtes aux lettres intégrées directement dans un emplacement géographique spécifique à l’aide de l’applet de commande [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) dans Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="789f0-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="789f0-p126">Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres onboarded et que **PreferredDataLocation** est définie sur la valeur souhaitée dans Azure AD. La valeur de **PreferredDataLocation** sera synchronisée dans l’attribut **MailboxRegion** de l’objet utilisateur de messagerie correspondant dans Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="789f0-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="789f0-269">Connectez-vous directement à la satellite spécifique localisés en suivant les instructions de connexion à partir de plus haut dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="789f0-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="789f0-270">Dans Exchange Online PowerShell, stockent les informations d’identification d’administrateur local qui est utilisé pour effectuer une migration de boîtes aux lettres dans une variable en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="789f0-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="789f0-271">Dans Exchange Online PowerShell, créez un nouveau **New-MoveRequest** similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="789f0-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="789f0-272">Répétez l’étape 4 # pour chaque boîte aux lettres à migrer à partir d’Exchange en local à l’emplacement de satellites que vous êtes actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="789f0-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="789f0-273">Si vous avez besoin migrer des boîtes aux lettres supplémentaires à un emplacement différent satellites, répétez les étapes 2 à 4 pour chaque emplacement satellites spécifiques.</span><span class="sxs-lookup"><span data-stu-id="789f0-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="789f0-274">Création de rapports multi-localisés</span><span class="sxs-lookup"><span data-stu-id="789f0-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="789f0-p127">**Rapports d’utilisation Multi-localisés** dans le centre d’administration Office 365 affiche le nombre d’utilisateurs par emplacement géographique. Le rapport affiche la distribution des utilisateurs pour le mois en cours et fournit des données d’historique pour les 6 derniers mois.</span><span class="sxs-lookup"><span data-stu-id="789f0-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
