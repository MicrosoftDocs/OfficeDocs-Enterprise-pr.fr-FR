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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Décrit les causes courantes des problèmes liés à la synchronisation d'annuaires dans Office 365 et fournit quelques méthodes pour les aider à les résoudre.
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085393"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="05a5d-103">Résoudre les problèmes de synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="05a5d-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="05a5d-p101">Avec la synchronisation d'annuaires, vous pouvez continuer à gérer les utilisateurs et les groupes locaux et synchroniser les ajouts, les suppressions et les modifications dans le Cloud. Toutefois, le programme d'installation est un peu compliqué et il peut parfois être difficile d'identifier la source des problèmes. Nous disposons de ressources pour vous aider à identifier les problèmes potentiels et à les résoudre.</span><span class="sxs-lookup"><span data-stu-id="05a5d-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="05a5d-107">Comment savoir si un problème est survenu?</span><span class="sxs-lookup"><span data-stu-id="05a5d-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="05a5d-108">La première indication que un élément est incorrect est lorsque la vignette d'État dirSync dans le centre d'administration Office 365 indique qu'il y a un problème:</span><span class="sxs-lookup"><span data-stu-id="05a5d-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Vignette d'État dirSync dans l'aperçu du centre d'administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="05a5d-p102">Vous recevrez également un message (vers l'autre courrier électronique et vers votre messagerie d'administrateur) à partir d'Office 365 qui indique que votre locataire a rencontré des erreurs de synchronisation d'annuaires. Pour plus d'informations, consultez la rubrique [identifier les erreurs de synchronisation d'annuaires dans Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="05a5d-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="05a5d-112">Comment puis-je obtenir l'outil Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="05a5d-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="05a5d-p103">dans le centre d'administration Office 365, accédez à \* \* utilisateurs \* \> \* utilisateurs **actifs**. Cliquez sur le menu **plus** , puis sélectionnez **synchronisation**d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="05a5d-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Dans le menu autres, sélectionnez synchronisation d'annuaires.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="05a5d-116">dans l'ancien centre d'administration Office 365, accédez \*\*\*\* \> à utilisateurs **actifs**, puis sélectionnez **configurer** en regard de **synchronisation Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="05a5d-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Choisissez configurer en regard de la synchronisation Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="05a5d-118">Suivez les [instructions de l'Assistant](set-up-directory-synchronization.md) pour télécharger Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="05a5d-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="05a5d-119">Si vous utilisez toujours Azure Active Directory Sync (dirSync), jetez un œil à la [façon de résoudre les problèmes liés à l'installation de l'outil de synchronisation Azure Active Directory et aux messages d'erreur de l'Assistant de configuration dans Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) pour plus d'informations sur la configuration système requise pour l'installation DirSync, les autorisations dont vous avez besoin et comment résoudre les erreurs courantes.</span><span class="sxs-lookup"><span data-stu-id="05a5d-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="05a5d-120">Pour effectuer une mise à jour à partir d'Azure Active Directory Sync vers Azure AD Connect, consultez [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="05a5d-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="05a5d-121">Résolution des causes courantes des problèmes liés à la synchronisation d'annuaires dans Office 365</span><span class="sxs-lookup"><span data-stu-id="05a5d-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="05a5d-122">**Les objets synchronisés n'apparaissent pas ou ne sont pas mis à jour en ligne, ou des rapports d'erreur de synchronisation proviennent du service.**</span><span class="sxs-lookup"><span data-stu-id="05a5d-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="05a5d-123">Synchronisation des identités et résilience d'attribut en double</span><span class="sxs-lookup"><span data-stu-id="05a5d-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="05a5d-124">**J'ai une alerte dans le centre d'administration Office 365 ou je reçois des courriers électroniques automatiques qu'il n'y a pas eu un événement de synchronisation récent**</span><span class="sxs-lookup"><span data-stu-id="05a5d-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="05a5d-125">Résolution des problèmes de connectivité avec Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="05a5d-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="05a5d-126">Autorisations et comptes Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="05a5d-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="05a5d-127">Synchronisation Azure AD Connect: comment gérer le compte de service Azure AD</span><span class="sxs-lookup"><span data-stu-id="05a5d-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="05a5d-128">La synchronisation d'annuaires vers Azure Active Directory s'arrête ou vous recevez un avertissement indiquant que la synchronisation n'a pas été enregistrée depuis plus d'une journée</span><span class="sxs-lookup"><span data-stu-id="05a5d-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="05a5d-129">**Les hachages de mot de passe ne sont pas synchronisés ou une alerte s'affiche dans le centre d'administration Office 365 qu'il n'y a pas eu une synchronisation récente de hachage de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="05a5d-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="05a5d-130">Implémentation de la synchronisation de hachage de mot de passe avec la synchronisation Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="05a5d-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="05a5d-131">**Je vois une alerte indiquant le dépassement du quota d'objet**</span><span class="sxs-lookup"><span data-stu-id="05a5d-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="05a5d-p104">Nous disposons d'un quota d'objets intégré pour aider à protéger le service. Si un trop grand nombre d'objets dans votre répertoire doivent être synchronisés avec Office 365, vous devrez [contacter le support technique pour les produits professionnels](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) afin d'augmenter votre quota.</span><span class="sxs-lookup"><span data-stu-id="05a5d-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="05a5d-134">**J’ai besoin de savoir quels attributs sont synchronisés.**</span><span class="sxs-lookup"><span data-stu-id="05a5d-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="05a5d-135">Vous pouvez trouver la liste de tous les attributs synchronisés entre l'organisation locale et le nuage dans ce [cas](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="05a5d-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="05a5d-136">**Je ne peux pas gérer ou supprimer des objets qui ont été synchronisés dans le Cloud**</span><span class="sxs-lookup"><span data-stu-id="05a5d-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="05a5d-p105">Êtes-vous prêt à gérer les objets dans le Cloud uniquement? Ou y a-t-il un objet qui a été supprimé en local, mais qui est bloqué dans le Cloud? Consultez cette rubrique relative à la [résolution des erreurs lors](https://go.microsoft.com/fwlink/p/?linkid=842044) de la synchronisation et de [l'article de support](https://go.microsoft.com/fwlink/p/?LinkId=396720) pour obtenir des instructions sur la résolution de ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="05a5d-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="05a5d-140">**J’ai reçu un message d’erreur indiquant que mon entreprise avait dépassé le nombre d’objets pouvant être synchronisés.**</span><span class="sxs-lookup"><span data-stu-id="05a5d-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="05a5d-141">Pour plus d'informations sur ce problème, consultez la [rubrique](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="05a5d-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="05a5d-142">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="05a5d-142">Other resources</span></span>

- [<span data-ttu-id="05a5d-143">Script de résolution des noms d'utilisateurs principaux en double</span><span class="sxs-lookup"><span data-stu-id="05a5d-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="05a5d-144">Préparation d'un domaine non routable (par exemple, domaine. local) pour la synchronisation d'annuaires</span><span class="sxs-lookup"><span data-stu-id="05a5d-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="05a5d-145">Script pour compter le nombre total d'objets synchronisés</span><span class="sxs-lookup"><span data-stu-id="05a5d-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="05a5d-146">Résoudre les problèmes liés à AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="05a5d-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="05a5d-147">Utiliser PowerShell pour corriger les attributs DisplayName vides pour les groupes à extension messagerie</span><span class="sxs-lookup"><span data-stu-id="05a5d-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="05a5d-148">Utiliser PowerShell pour corriger le nom UPN en double</span><span class="sxs-lookup"><span data-stu-id="05a5d-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="05a5d-149">Utiliser PowerShell pour corriger des adresses de messagerie en double</span><span class="sxs-lookup"><span data-stu-id="05a5d-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="05a5d-150">Outils de diagnostic</span><span class="sxs-lookup"><span data-stu-id="05a5d-150">Diagnostic tools</span></span>

<span data-ttu-id="05a5d-p106">L' [outil IDFix](prepare-directory-attributes-for-synch-with-idfix.md) permet de détecter et de résoudre les objets Identity et leurs attributs dans un environnement Active Directory local en vue de la migration vers Office 365. IDFix est destiné aux administrateurs Active Directory responsables de dirSync avec le service Office 365.</span><span class="sxs-lookup"><span data-stu-id="05a5d-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="05a5d-153">[Téléchargez l'outil IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) à partir du centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="05a5d-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>