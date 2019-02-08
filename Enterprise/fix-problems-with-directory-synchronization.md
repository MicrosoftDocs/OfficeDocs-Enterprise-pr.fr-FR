---
title: Résoudre les problèmes de synchronisation d’annuaires pour Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Décrit les causes fréquentes de problèmes liés à la synchronisation d’annuaires dans Office 365 et fournit quelques méthodes pour vous aider à résoudre les problèmes et les résoudre.
ms.openlocfilehash: 2d567daa370d651a6eb9180db2f729d09b380226
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897307"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="31ec2-103">Résoudre les problèmes de synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="31ec2-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="31ec2-p101">Avec la synchronisation d’annuaires, vous pouvez continuer à gérer les utilisateurs et groupes locaux et synchronisez les ajouts, suppressions et modifications vers le nuage. Le programme d’installation est un peu compliqué, mais il peut parfois être difficile d’identifier la source des problèmes. Nous disposons de ressources pour vous aider à identifier les problèmes potentiels et à les résoudre.</span><span class="sxs-lookup"><span data-stu-id="31ec2-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="31ec2-107">Comment savoir si un élément est incorrect ?</span><span class="sxs-lookup"><span data-stu-id="31ec2-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="31ec2-108">La première indication que quelque chose est incorrect est lorsque la vignette de l’état de synchronisation d’annuaire dans le centre d’administration Office 365 indique un problème est survenu :</span><span class="sxs-lookup"><span data-stu-id="31ec2-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![L’état de synchronisation d’annuaire en mosaïque dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="31ec2-p102">Vous recevrez un courrier électronique (à l’autre application de messagerie et votre adresse e-mail d’administration) à partir d’Office 365 qui indique votre client a rencontré des erreurs de synchronisation d’annuaire. Pour plus d’informations, consultez [identifier des erreurs de synchronisation d’annuaire dans Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="31ec2-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="31ec2-112">Comment obtenir outil Azure Active Directory se connecter ?</span><span class="sxs-lookup"><span data-stu-id="31ec2-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="31ec2-p103">Dans le centre d’administration Office 365, accédez à \*\* utilisateurs \*\* \> **utilisateurs actifs**. Cliquez sur le menu **plus** et sélectionnez **la synchronisation d’annuaires**.</span><span class="sxs-lookup"><span data-stu-id="31ec2-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Dans le menu autres, choisissez la synchronisation d’annuaires](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="31ec2-116">Dans le centre d’administration Office 365 anciens, accédez aux **utilisateurs** \> **Utilisateurs actifs**et sélectionnez **configurer** en regard de **synchronisation Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="31ec2-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Sélectionnez définir en regard de synchronisation Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="31ec2-118">Suivez les [instructions de l’Assistant](set-up-directory-synchronization.md) pour télécharger Azure AD se connecter.</span><span class="sxs-lookup"><span data-stu-id="31ec2-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="31ec2-119">Si vous utilisez toujours la synchronisation Azure Active Directory (DirSync), jetez un œil à [comment résoudre les problèmes d’installation de l’outil de synchronisation Azure Active Directory et l’Assistant Configuration des messages d’erreur dans Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) pour plus d’informations sur la configuration système requise pour installer synchronisation d’annuaire, les autorisations dont vous avez besoin et comment résoudre les erreurs courantes.</span><span class="sxs-lookup"><span data-stu-id="31ec2-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="31ec2-120">Pour mettre à jour à partir de synchronisation Azure Active Directory pour établir la connexion Azure AD, voir [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="31ec2-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="31ec2-121">Résolution courantes entraîne des problèmes liés à la synchronisation d’annuaires dans Office 365</span><span class="sxs-lookup"><span data-stu-id="31ec2-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="31ec2-122">**Objets synchronisés ne sont pas apparaître ou mise à jour en ligne, ou je reçois des rapports d’erreurs de synchronisation à partir du Service.**</span><span class="sxs-lookup"><span data-stu-id="31ec2-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="31ec2-123">Résistance des attribut Identity synchronisation et en double</span><span class="sxs-lookup"><span data-stu-id="31ec2-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="31ec2-124">**J’ont une alerte dans le centre d’administration d’Office 365, ou reçois automatisée de messages électroniques qu’il n’a pas été un événement de synchronisation récents**</span><span class="sxs-lookup"><span data-stu-id="31ec2-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="31ec2-125">Résoudre les problèmes de connectivité avec Azure AD se connecter</span><span class="sxs-lookup"><span data-stu-id="31ec2-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="31ec2-126">Azure AD connecter les comptes et autorisations</span><span class="sxs-lookup"><span data-stu-id="31ec2-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="31ec2-127">Azure AD Connect sync : comment gérer le compte de service Azure AD</span><span class="sxs-lookup"><span data-stu-id="31ec2-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="31ec2-128">Synchronisation d’annuaire s’arrête Azure Active Directory ou que vous êtes averti que la synchronisation n’a pas encore inscrit dans plus d’un jour</span><span class="sxs-lookup"><span data-stu-id="31ec2-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="31ec2-129">**Les hachages de mot de passe ne sont pas synchronisation ou j’obtiens une alerte dans le centre d’administration Office 365 qu’il n’a pas été une synchronisation de hachage de mot de passe récents**</span><span class="sxs-lookup"><span data-stu-id="31ec2-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="31ec2-130">Implémentation de la synchronisation de hachage de mot de passe avec la synchronisation Azure Active Directory se connecter</span><span class="sxs-lookup"><span data-stu-id="31ec2-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="31ec2-131">**J’obtiens une alerte qui a dépassé le quota de l’objet**</span><span class="sxs-lookup"><span data-stu-id="31ec2-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="31ec2-p104">Nous disposons d’un quota de l’objet intégré pour protéger le service. Si vous avez trop d’objets dans votre annuaire qui doivent effectuer une synchronisation avec Office 365, vous devrez [Contact prend en charge pour les produits d’entreprise](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour augmenter le quota.</span><span class="sxs-lookup"><span data-stu-id="31ec2-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="31ec2-134">**J’ai besoin de savoir quels attributs sont synchronisés.**</span><span class="sxs-lookup"><span data-stu-id="31ec2-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="31ec2-135">Vous trouverez une liste de tous les attributs sont synchronisés entre le nuage [ici](https://go.microsoft.com/fwlink/p/?LinkId=396719)et en local.</span><span class="sxs-lookup"><span data-stu-id="31ec2-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="31ec2-136">**Je ne parviens pas à gérer ou supprimer des objets qui ont été synchronisées avec le nuage**</span><span class="sxs-lookup"><span data-stu-id="31ec2-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="31ec2-p105">Vous êtes prêt à gérer les objets dans le nuage uniquement ? Ou un objet qui a été supprimé localement, mais est bloqué dans le nuage ? Jetez un œil à ce [Dépannage des erreurs lors de la synchronisation](https://go.microsoft.com/fwlink/p/?linkid=842044) et la [prise en charge de l’article](https://go.microsoft.com/fwlink/p/?LinkId=396720) pour obtenir des instructions sur la façon de résoudre ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="31ec2-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="31ec2-140">**J’ai reçu un message d’erreur indiquant que mon entreprise avait dépassé le nombre d’objets pouvant être synchronisés.**</span><span class="sxs-lookup"><span data-stu-id="31ec2-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="31ec2-141">Vous pouvez en savoir plus sur ce problème [ici](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="31ec2-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="31ec2-142">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="31ec2-142">Other resources</span></span>

- [<span data-ttu-id="31ec2-143">Script de résolution des noms d'utilisateurs principaux en double</span><span class="sxs-lookup"><span data-stu-id="31ec2-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="31ec2-144">Comment faire pour préparer un domaine non routable (par exemple, domaine .local) pour la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="31ec2-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="31ec2-145">Script permettant de compter le nombre total d’objets synchronisé</span><span class="sxs-lookup"><span data-stu-id="31ec2-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="31ec2-146">Dépanner AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="31ec2-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="31ec2-147">Utiliser PowerShell pour résoudre les attributs DisplayName vides pour les groupes à extension messagerie</span><span class="sxs-lookup"><span data-stu-id="31ec2-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="31ec2-148">Utiliser PowerShell pour résoudre les UPN en double</span><span class="sxs-lookup"><span data-stu-id="31ec2-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="31ec2-149">Utiliser PowerShell pour résoudre les adresses de messagerie en double</span><span class="sxs-lookup"><span data-stu-id="31ec2-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="31ec2-150">Outils de diagnostic</span><span class="sxs-lookup"><span data-stu-id="31ec2-150">Diagnostic tools</span></span>

<span data-ttu-id="31ec2-p106">[Outil IDFix](prepare-directory-attributes-for-synch-with-idfix.md) est utilisé pour effectuer la recherche et la résolution des objets d’identité et de leurs attributs dans un environnement d’Active Directory sur site en vue de la migration vers Office 365. IDFix est destinée aux administrateurs Active Directory responsables de la synchronisation d’annuaire avec le service Office 365.</span><span class="sxs-lookup"><span data-stu-id="31ec2-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="31ec2-153">[Télécharger l’outil IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) à partir du centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="31ec2-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>