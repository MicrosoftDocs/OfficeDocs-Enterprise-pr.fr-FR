---
title: Capacités multi-Geo dans Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Développez votre présence sur Office 365 dans plusieurs régions géographiques avec des capacités multi-geo dans Exchange en ligne.
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="06d17-103">Capacités multi-Geo dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="06d17-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="06d17-p101">Les fonctionnalités de multi-Geo dans Office 365 permettent un mono-utilisateur à couvrir plusieurs emplacements géographiques (zones géographiques). Lorsque Multi-Geo est activée, les clients peuvent sélectionner l’emplacement du contenu de boîte aux lettres Exchange Online (données au repos) sur une base par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="06d17-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="06d17-p102">Votre emplacement de clients initial (appelée « par défaut » ou « endroit ») est déterminé en fonction de votre adresse de facturation. Lorsque Multi-Geo est activé, vous pouvez placer des boîtes aux lettres dans les emplacements supplémentaires « satellite » par :</span><span class="sxs-lookup"><span data-stu-id="06d17-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="06d17-108">Création d’une nouvelle boîte aux lettres Exchange Online directement dans un satellite.</span><span class="sxs-lookup"><span data-stu-id="06d17-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="06d17-109">Déplacement d’une boîte aux lettres Exchange Online existant dans un satellite.</span><span class="sxs-lookup"><span data-stu-id="06d17-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="06d17-110">Intégration d’une boîte aux lettres d’une organisation d’Exchange local directement dans un satellite.</span><span class="sxs-lookup"><span data-stu-id="06d17-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="06d17-111">Les zones géographiques suivantes sont disponibles pour utilisation dans une configuration Multi-Geo :</span><span class="sxs-lookup"><span data-stu-id="06d17-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="06d17-112">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="06d17-112">Asia Pacific</span></span>

- <span data-ttu-id="06d17-113">Australie</span><span class="sxs-lookup"><span data-stu-id="06d17-113">Australia</span></span>

- <span data-ttu-id="06d17-114">Canada</span><span class="sxs-lookup"><span data-stu-id="06d17-114">Canada</span></span>

- <span data-ttu-id="06d17-115">Union européenne</span><span class="sxs-lookup"><span data-stu-id="06d17-115">European Union</span></span>

- <span data-ttu-id="06d17-116">Inde (actuellement uniquement disponible pour les clients avec des adresses de facturation en Inde)</span><span class="sxs-lookup"><span data-stu-id="06d17-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="06d17-117">Japon</span><span class="sxs-lookup"><span data-stu-id="06d17-117">Japan</span></span>

- <span data-ttu-id="06d17-118">Corée</span><span class="sxs-lookup"><span data-stu-id="06d17-118">Korea</span></span>

- <span data-ttu-id="06d17-119">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="06d17-119">United Kingdom</span></span>

- <span data-ttu-id="06d17-120">États-Unis</span><span class="sxs-lookup"><span data-stu-id="06d17-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="06d17-121">Configuration du logiciel requis</span><span class="sxs-lookup"><span data-stu-id="06d17-121">Prerequisite configuration</span></span>
<span data-ttu-id="06d17-p103">Avant de commencer à l’aide de fonctions de Multi-Geo dans Exchange en ligne, Microsoft a besoin configurer vos clients Exchange Online pour la prise en charge Multi-Geo. Ce processus de configuration unique est déclenché lorsque vous commandez des licences Multi-Geo et devez prennent généralement moins de 30 jours pour terminer.</span><span class="sxs-lookup"><span data-stu-id="06d17-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="06d17-p104">Vous recevrez des notifications dans le [Centre de messages d’Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) lorsque votre configuration a démarré et est terminée. Configuration est automatiquement déclenchée lorsque vous achetez des licences Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="06d17-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="06d17-126">Se déplace et le positionnement de la boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="06d17-126">Mailbox placement and moves</span></span>
<span data-ttu-id="06d17-127">Microsoft après les étapes de configuration Multi-Geo requis, Exchange Online respecte l’attribut **PreferredDataLocation** sur les objets utilisateur dans Active Directory Azure.</span><span class="sxs-lookup"><span data-stu-id="06d17-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="06d17-p105">En ligne Exchange synchronise la propriété **PreferredDataLocation** à partir d’AD Azure dans la propriété **MailboxRegion** dans le service d’annuaire Exchange en ligne. La valeur de **MailboxRegion** détermine le géographique où seront placés les boîtes aux lettres et boîtes aux lettres d’archive associé. Il n’est pas possible de configurer boîte aux lettres et archivage boîtes aux lettres principales un utilisateur pour résident dans des zones géographiques différentes. Seul Geo peut être configuré par un objet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="06d17-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="06d17-132">Lorsque **PreferredDataLocation** est configuré pour un utilisateur avec une boîte aux lettres existante, la boîte aux lettres sera automatiquement déplacé vers la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="06d17-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="06d17-133">Lorsque **PreferredDataLocation** est configuré pour un utilisateur sans une boîte aux lettres existante, la boîte aux lettres sera déployé dans la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="06d17-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="06d17-134">Si aucun Geo n’est spécifié, la boîte aux lettres sera placé dans la zone géographique de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="06d17-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="06d17-p106">**Remarque**: les capacités Multi-Geo et Skype pour des réunions en ligne Business régional hébergé à la fois utilisent la propriété **PreferredDataLocation** sur les objets utilisateur pour localiser les services. Si vous configurez les valeurs de **PreferredDataLocation** sur les objets de l’utilisateur pour les réunions régional hébergées, la boîte aux lettres et OneDrive pour les utilisateurs automatiquement va à la zone géographique spécifiée après que Multi-Geo est activé sur le client Office 365.</span><span class="sxs-lookup"><span data-stu-id="06d17-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox and OneDrive for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="06d17-137">Limitations de fonctionnalités pour Multi-Geo dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="06d17-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="06d17-p107">Uniquement les boîtes aux lettres de l’utilisateur, boîtes aux lettres de ressource (salle et équipement de boîtes aux lettres) et les boîtes aux lettres partagées prennent en charge les fonctionnalités de Multi-Geo. Vous pouvez uniquement placer des boîtes aux lettres des dossiers publics et les groupes d’Office 365 dans géographique d’origine du client.</span><span class="sxs-lookup"><span data-stu-id="06d17-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="06d17-p108">Respect de la réglementation de sécurité et de fonctionnalités (par exemple, l’audit et e-Discovery) qui sont disponibles dans le centre d’administration Exchange (FAC) ne sont pas disponibles dans les organisations de Multi-Geo. Au lieu de cela, vous devez utiliser la [sécurité de Microsoft Office 365 et de centre de conformité](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) pour configurer les fonctionnalités de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="06d17-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="06d17-p109">Outlook pour les utilisateurs de Mac peut rencontrer une perte temporaire de l’accès à leur dossier d’archivage en ligne pendant que vous déplacez sa boîte aux lettres à un nouveau Geo. Cette situation se produit lorsque le l’utilisateur primaire et boîtes aux lettres d’archive dans géographiques différents, car le déplacement de boîtes aux lettres cross-Geo peut se terminer à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="06d17-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="06d17-p110">Les utilisateurs ne peuvent pas partager des *dossiers de boîtes aux lettres* entre les zones géographiques dans Outlook sur le web (anciennement Outlook Web App ou OWA). Par exemple, un utilisateur dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé dans une boîte aux lettres se trouvant aux États-Unis. Toutefois, Outlook sur les utilisateurs du web peut ouvrir les *autres boîtes aux lettres* dans des zones géographiques différentes en utilisant une fenêtre distincte du navigateur, comme décrit dans [Ouvrir boîte aux lettres d’une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="06d17-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="06d17-147">**Remarque**: le partage des dossiers de boîte aux lettres de Cross-Geo est pris en charge dans Outlook sous Windows.</span><span class="sxs-lookup"><span data-stu-id="06d17-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="06d17-p111">Actuellement, la délégation de calendrier cross-Geo n’est pas pris en charge dans Outlook sur le web. Délégation de calendrier Cross-Geo est pris en charge dans Outlook sous Windows.</span><span class="sxs-lookup"><span data-stu-id="06d17-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="06d17-150">Administration</span><span class="sxs-lookup"><span data-stu-id="06d17-150">Administration</span></span> 
<span data-ttu-id="06d17-p112">PowerShell distant est nécessaire pour afficher et configurer les propriétés relatives à la zone géographique dans votre environnement Office 365. Pour plus d’informations sur les différents modules PowerShell permettant de gérer Office 365, voir [Gestion d’Office 365 et Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="06d17-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="06d17-p113">Vous devez la v1.1.166.0 de [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) ou en version ultérieurement à 1.x pour voir la propriété **PreferredDataLocation** sur les objets utilisateur. Pour vous connecter à Azure AD PowerShell, voir [se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="06d17-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="06d17-155">Pour vous connecter à Exchange Online PowerShell, voir [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="06d17-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="06d17-156">Se connecter directement à une région à l’aide d’Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="06d17-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="06d17-p114">En règle générale, Exchange Online PowerShell se connecte par défaut Geo. Toutefois, vous pouvez également vous connecter directement à des zones géographiques de celle par défaut. En raison des améliorations de performances, nous vous recommandons de connexion directe à la Geo non défini par défaut lorsque vous gérez uniquement les utilisateurs de cette zone géographique.</span><span class="sxs-lookup"><span data-stu-id="06d17-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="06d17-p115">Pour vous connecter à une zone géographique spécifique, le paramètre *ConnectionUri* est différent dans les instructions de connexion régulières. Le reste des commandes et des valeurs sont les mêmes. Les étapes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="06d17-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="06d17-163">Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="06d17-164">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail ou le compte de l’établissement et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="06d17-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="06d17-p116">Remplacer `<emailaddress>` avec l’adresse de messagerie de **toutes** les boîtes aux lettres dans la cible géographique et exécutez la commande suivante. Vos autorisations sur la boîte aux lettres et de la relation avec vos informations d’identification à l’étape 1 ne sont pas un facteur ; l’adresse de messagerie indique simplement Exchange en ligne permettant de se connecter.</span><span class="sxs-lookup"><span data-stu-id="06d17-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="06d17-167">Par exemple, si olga@contoso.onmicrosoft.com est l’adresse de messagerie d’une boîte aux lettres valide dans le géographique que vous voulez vous connecter, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="06d17-168">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="06d17-169">Exigences de version Azure Connect de la publicité</span><span class="sxs-lookup"><span data-stu-id="06d17-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="06d17-p117">Connecter des DAS version 1.1.524.0 ou version ultérieure est la seule méthode prise en charge pour la définition de la propriété **PreferredDataLocation** sur les objets utilisateur sont synchronisés sur les sites Active Directory. Pour obtenir des instructions détaillées, reportez-vous à la section [la synchronisation Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="06d17-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="06d17-172">Codes de zone géographique</span><span class="sxs-lookup"><span data-stu-id="06d17-172">Geo Codes</span></span>
<span data-ttu-id="06d17-p118">Codes à trois lettres vous permet de spécifier la zone géographique dans la propriété **PreferredDataLocation** . Le tableau suivant répertorie les codes pour les zones géographiques disponibles :</span><span class="sxs-lookup"><span data-stu-id="06d17-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="06d17-175">Géo</span><span class="sxs-lookup"><span data-stu-id="06d17-175">Geo</span></span> |<span data-ttu-id="06d17-176">Code</span><span class="sxs-lookup"><span data-stu-id="06d17-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="06d17-177">Asie/Pacifique</span><span class="sxs-lookup"><span data-stu-id="06d17-177">Asia/Pacific</span></span> |<span data-ttu-id="06d17-178">APC</span><span class="sxs-lookup"><span data-stu-id="06d17-178">APC</span></span> |
|<span data-ttu-id="06d17-179">Australie</span><span class="sxs-lookup"><span data-stu-id="06d17-179">Australia</span></span> |<span data-ttu-id="06d17-180">AUSTRALIE</span><span class="sxs-lookup"><span data-stu-id="06d17-180">AUS</span></span> |
|<span data-ttu-id="06d17-181">Canada</span><span class="sxs-lookup"><span data-stu-id="06d17-181">Canada</span></span> |<span data-ttu-id="06d17-182">POUVEZ</span><span class="sxs-lookup"><span data-stu-id="06d17-182">CAN</span></span> |
|<span data-ttu-id="06d17-183">Union européenne</span><span class="sxs-lookup"><span data-stu-id="06d17-183">European Union</span></span> |<span data-ttu-id="06d17-184">EUROS</span><span class="sxs-lookup"><span data-stu-id="06d17-184">EUR</span></span> |
|<span data-ttu-id="06d17-185">Inde</span><span class="sxs-lookup"><span data-stu-id="06d17-185">India</span></span> |<span data-ttu-id="06d17-186">IND</span><span class="sxs-lookup"><span data-stu-id="06d17-186">IND</span></span> |
|<span data-ttu-id="06d17-187">Japon</span><span class="sxs-lookup"><span data-stu-id="06d17-187">Japan</span></span> |<span data-ttu-id="06d17-188">JPN</span><span class="sxs-lookup"><span data-stu-id="06d17-188">JPN</span></span> |
|<span data-ttu-id="06d17-189">Corée</span><span class="sxs-lookup"><span data-stu-id="06d17-189">Korea</span></span> |<span data-ttu-id="06d17-190">KOR</span><span class="sxs-lookup"><span data-stu-id="06d17-190">KOR</span></span> |
|<span data-ttu-id="06d17-191">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="06d17-191">United Kingdom</span></span> |<span data-ttu-id="06d17-192">GBR</span><span class="sxs-lookup"><span data-stu-id="06d17-192">GBR</span></span> |
|<span data-ttu-id="06d17-193">États-Unis</span><span class="sxs-lookup"><span data-stu-id="06d17-193">United States</span></span> |<span data-ttu-id="06d17-194">NAM</span><span class="sxs-lookup"><span data-stu-id="06d17-194">NAM</span></span> |

<span data-ttu-id="06d17-p119">**Remarque**: les propriétés **PreferredDataLocation** et **MailboxRegion** sont des chaînes avec aucune vérification des erreurs. Si vous entrez une valeur non valide (par exemple, NAN), que la boîte aux lettres est placé dans la zone géographique de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="06d17-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="06d17-197">Permet d’afficher les zones géographiques disponibles qui sont configurées dans votre organisation Exchange en ligne</span><span class="sxs-lookup"><span data-stu-id="06d17-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="06d17-198">Pour afficher la liste des géographiques configurées dans votre organisation Exchange Online, exécutez la commande suivante dans Exchange Online PowerShell :</span><span class="sxs-lookup"><span data-stu-id="06d17-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="06d17-199">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="06d17-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="06d17-200">Trouver l’emplacement géographique d’une boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="06d17-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="06d17-201">L’applet de commande **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés de géo-associées suivantes sur les boîtes aux lettres :</span><span class="sxs-lookup"><span data-stu-id="06d17-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="06d17-202">**Base de données**: les 3 premières lettres du nom de la base de données correspondent au code géographique, qui vous indique où se trouve actuellement la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="06d17-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="06d17-203">**MailboxRegion**: Spécifie le code géographique qui a été défini par l’administrateur (synchronisé dans Azure annonce à partir de **PreferredDataLocation** ).</span><span class="sxs-lookup"><span data-stu-id="06d17-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="06d17-204">**MailboxRegionLastUpdateTime**: indique lorsque MailboxRegion a été mises à jour (manuellement ou automatiquement).</span><span class="sxs-lookup"><span data-stu-id="06d17-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="06d17-205">Pour afficher les propriétés d’une boîte aux lettres, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="06d17-206">Par exemple, pour afficher les informations Geo pour la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="06d17-207">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="06d17-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="06d17-208">Si le code géographique dans le nom de la base de données ne correspond pas à la valeur de **MailboxRegion** , la boîte aux lettres sera automatiquement déplacé vers le Geo spécifié par la valeur de **MailboxRegion** (Exchange Online recherche une incompatibilité entre ces valeurs de propriété).</span><span class="sxs-lookup"><span data-stu-id="06d17-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="06d17-209">Déplacer une boîte aux lettres du nuage existante à une zone géographique spécifique</span><span class="sxs-lookup"><span data-stu-id="06d17-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="06d17-210">Utilisez les applets de commande **Get-MsolUser** et **MsolUser de l’ensemble** du Module AD Azure pour Windows PowerShell pour afficher ou spécifier la zone géographique où seront stockées les boîtes aux lettres de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="06d17-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="06d17-211">Pour afficher la valeur de **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="06d17-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="06d17-212">Par exemple, pour afficher la valeur de **PreferredDataLocation** pour la michelle@contoso.onmicrosoft.com utilisateur, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="06d17-213">Le résultat de la commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="06d17-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="06d17-214">Pour modifier la valeur de **PreferredDataLocation** pour un objet utilisateur nuage uniquement, utilisez la syntaxe suivante dans Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="06d17-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="06d17-215">Par exemple, pour définir la valeur de **PreferredDataLocation** à l’Union européenne (en euros) pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="06d17-216">**Notes**:</span><span class="sxs-lookup"><span data-stu-id="06d17-216">**Notes**:</span></span>

- <span data-ttu-id="06d17-p120">Comme mentionné précédemment pour les objets utilisateur synchronisé sur site Active Directory, vous ne pouvez pas utiliser cette procédure. Vous devez modifier la valeur **PreferredDataLocation** à l’aide de la connexion des DAS. Pour plus d’informations, consultez [sync d’Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="06d17-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="06d17-220">Le temps nécessaire pour déplacer une boîte aux lettres dépend de plusieurs facteurs :</span><span class="sxs-lookup"><span data-stu-id="06d17-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="06d17-221">La taille et le type de boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="06d17-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="06d17-222">Le nombre de boîtes aux lettres en cours de déplacement.</span><span class="sxs-lookup"><span data-stu-id="06d17-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="06d17-223">La disponibilité des ressources de la déplacer.</span><span class="sxs-lookup"><span data-stu-id="06d17-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="06d17-224">Boîtes aux lettres de transfert désactivé sur Litigation Hold</span><span class="sxs-lookup"><span data-stu-id="06d17-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="06d17-p121">Désactivé les boîtes aux lettres sur Litigation Hold et qui sont conservés pour e-Discovery à des fins ne peut pas être déplacés en modifiant leur valeur **PreferredDataLocation** dans leur état désactivé. Pour déplacer une boîte aux lettres désactivée sur gel :</span><span class="sxs-lookup"><span data-stu-id="06d17-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="06d17-227">Temporairement attribuer une licence à la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="06d17-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="06d17-228">Modifier la **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="06d17-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="06d17-229">Supprimer la licence de la boîte aux lettres après que qu’il a été déplacé vers la zone géographique sélectionnée à replacer dans un état désactivé.</span><span class="sxs-lookup"><span data-stu-id="06d17-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="06d17-230">Créer des nouvelles boîtes aux lettres du nuage dans une zone géographique spécifique</span><span class="sxs-lookup"><span data-stu-id="06d17-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="06d17-231">Pour créer une nouvelle boîte aux lettres dans une zone géographique spécifique, vous devez effectuer une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="06d17-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="06d17-232">Configurer la valeur **PreferredDataLocation** , comme décrit dans la section *avant de* la boîte aux lettres est créé dans Exchange en ligne (par exemple, en configurant la valeur **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence).</span><span class="sxs-lookup"><span data-stu-id="06d17-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="06d17-233">Attribuer une licence en même temps que vous définissez la valeur **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="06d17-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="06d17-234">Pour créer un nuage uniquement sous licence utilisateur (DAS se connecte pas synchronisé) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Azure AD PowerShell :</span><span class="sxs-lookup"><span data-stu-id="06d17-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="06d17-235">Cet exemple montre comment créer un nouveau compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="06d17-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="06d17-236">Nom principal d’utilisateur : ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="06d17-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="06d17-237">Prénom : Elizabeth</span><span class="sxs-lookup"><span data-stu-id="06d17-237">First name: Elizabeth</span></span>

- <span data-ttu-id="06d17-238">Nom : Brunner</span><span class="sxs-lookup"><span data-stu-id="06d17-238">Last name: Brunner</span></span>

- <span data-ttu-id="06d17-239">Nom d’affichage Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="06d17-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="06d17-240">Mot de passe : générée de manière aléatoire et apparaissent dans les résultats de la commande (dans la mesure où nous n’utilisons pas le paramètre de *mot de passe* )</span><span class="sxs-lookup"><span data-stu-id="06d17-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="06d17-241">Licence : contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="06d17-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="06d17-242">3-emplacement : Australie (Australie)</span><span class="sxs-lookup"><span data-stu-id="06d17-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="06d17-243">Pour plus d’informations sur la création de comptes d’utilisateur et la recherche des valeurs de LicenseAssignment dans Azure AD PowerShell, consultez [créer les comptes d’utilisateurs avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) et [Afficher les licences et les services avec Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="06d17-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="06d17-p122">Si vous utilisez Exchange PowerShell pour activer une boîte aux lettres et ont besoin de la boîte aux lettres doit être créé directement dans la zone géographique qui est spécifié dans **PreferredDataLocation**, vous devez utiliser Exchange Online une applet de commande **Enable-Mailbox** ou **New-Mailbox** directement sur le service en nuage. Si vous utilisez l’applet de commande **Enable-RemoteMailbox** sur site Exchange, la boîte aux lettres sera créé dans la région par défaut.</span><span class="sxs-lookup"><span data-stu-id="06d17-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="06d17-246">Existante intégrée sur site boîtes aux lettres dans une zone géographique spécifique</span><span class="sxs-lookup"><span data-stu-id="06d17-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="06d17-247">Vous pouvez utiliser les outils d’intégration standard et processus pour migrer une boîte aux lettres d’une organisation d’Exchange en local vers Exchange Online, y compris le [tableau de bord de Migration dans l’estimation à l’achèvement](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)et l’applet de commande [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) dans Exchange en ligne PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06d17-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="06d17-p123">La première étape consiste à vérifier qu'un objet utilisateur existe pour chaque boîte aux lettres onboarded, et vérifiez que la valeur correcte de la **PreferredDataLocation** est configurée dans Active Directory Azure. Les outils d’intégration respecteront la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement à la zone géographique spécifié.</span><span class="sxs-lookup"><span data-stu-id="06d17-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="06d17-250">Ou bien, vous pouvez utiliser les étapes suivantes pour les boîtes aux lettres intégrés directement dans une région à l’aide de l’applet de commande [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) dans PowerShell en ligne d’Exchange.</span><span class="sxs-lookup"><span data-stu-id="06d17-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="06d17-p124">Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres soit onboarded et que **PreferredDataLocation** est définie sur la valeur souhaitée dans Azure AD. La valeur de **PreferredDataLocation** est synchronisée avec l’attribut **MailboxRegion** de l’objet utilisateur de messagerie correspondant dans Exchange en ligne.</span><span class="sxs-lookup"><span data-stu-id="06d17-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="06d17-253">Se connecter directement à la spécifique satellite géo utilisant les instructions de connexion à partir de plus haut dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="06d17-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="06d17-254">Dans Exchange Online PowerShell, stocker les informations d’identification d’administrateur local qui est utilisé pour effectuer une migration de boîtes aux lettres dans une variable en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="06d17-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="06d17-255">Dans Exchange Online PowerShell, créez un nouveau **New-MoveRequest** similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="06d17-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="06d17-256">Répétez l’étape #4 pour chaque boîte aux lettres que vous avez besoin pour migrer d’Exchange local vers le satellite géo, vous êtes actuellement connecté à.</span><span class="sxs-lookup"><span data-stu-id="06d17-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="06d17-257">Si vous avez besoin migrer des boîtes aux lettres supplémentaires vers un autre satellite géo, répétez les étapes 2 à 4 pour chaque spécifique satellite géo.</span><span class="sxs-lookup"><span data-stu-id="06d17-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="06d17-258">Création de rapports multi-Geo</span><span class="sxs-lookup"><span data-stu-id="06d17-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="06d17-p125">**Rapports d’utilisation Multi-Geo** dans le centre d’administration Office 365 affiche le nombre d’utilisateurs par zone géographique. Le rapport affiche la distribution des utilisateurs pour le mois en cours et fournit des données historiques pour les 6 derniers mois.</span><span class="sxs-lookup"><span data-stu-id="06d17-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
