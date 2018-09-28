---
title: Gestion de Skype Entreprise Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965191"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="39076-103">Gestion de Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="39076-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="39076-104">**Résumé :** Utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.</span><span class="sxs-lookup"><span data-stu-id="39076-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="39076-p101">Parmi les principales tâches de n’importe quel Skype pour l’administrateur d’entreprise en ligne est la gestion des stratégies. Bien que vous pouvez effectuer certaines de ces tâches dans le centre d’administration d’Office 365, les autres tâches sont beaucoup plus rapide et plus facile dans Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39076-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="39076-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="39076-107">Before you start</span></span>

<span data-ttu-id="39076-108">Télécharger et installer le [Skype pour le module Business Connector en ligne](https://www.microsoft.com/en-us/download/details.aspx?id=39366), puis redémarrez votre ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="39076-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="39076-109">Se connecter en utilisant un Skype pour le mot de passe et le nom du compte administrateur Business en ligne</span><span class="sxs-lookup"><span data-stu-id="39076-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="39076-110">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="39076-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="39076-111">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre Skype pour le nom du compte administrateur Business en ligne et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="39076-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="39076-112">Se connecter en utilisant un Skype pour Business en ligne compte d’administrateur avec l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="39076-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="39076-113">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="39076-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="39076-114">Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez votre Skype pour le nom du compte administrateur Business en ligne.</span><span class="sxs-lookup"><span data-stu-id="39076-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="39076-115">Dans la boîte de dialogue **se connecter à votre compte** , tapez votre Skype Business Online mot de passe administrateur, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="39076-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="39076-116">Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="39076-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="39076-117">Pour plus d'informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="39076-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="39076-118">Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="39076-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="39076-119">Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="39076-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="39076-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39076-120">See also</span></span>

[<span data-ttu-id="39076-121">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="39076-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="39076-122">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="39076-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="39076-123">Skype pour les références d’applet de commande PowerShell Business</span><span class="sxs-lookup"><span data-stu-id="39076-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

