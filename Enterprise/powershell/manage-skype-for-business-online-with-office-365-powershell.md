---
title: Gestion de Skype Entreprise Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: ac3933b3a208f41db5c569de3455ce1244133927
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747564"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="81bad-103">Gestion de Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81bad-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="81bad-104">Une des tâches principales de tout administrateur de Skype Entreprise Online est la gestion des stratégies.</span><span class="sxs-lookup"><span data-stu-id="81bad-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="81bad-105">Bien que vous puissiez effectuer certaines de ces tâches dans le Centre d’administration Microsoft 365, d’autres tâches sont beaucoup plus rapides et plus simples à exécuter dans Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81bad-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="81bad-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="81bad-106">Before you start</span></span>

<span data-ttu-id="81bad-107">Téléchargez et installez le [module du connecteur Skype entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366), puis redémarrez votre ordinateur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="81bad-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="81bad-108">Se connecter à l’aide du nom et du mot de passe d’un compte d’administrateur Skype entreprise Online</span><span class="sxs-lookup"><span data-stu-id="81bad-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="81bad-109">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="81bad-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="81bad-110">Dans la boîte de dialogue **demande d’informations d’identification Windows PowerShell** , tapez le nom et le mot de passe de votre compte d’administrateur Skype entreprise Online, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="81bad-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="81bad-111">Se connecter à l’aide d’un compte d’administrateur Skype entreprise Online avec l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="81bad-111">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="81bad-112">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="81bad-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="81bad-113">Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez le nom de votre compte d’administrateur Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="81bad-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="81bad-114">Dans la boîte de dialogue **se connecter à votre compte** , saisissez votre mot de passe d’administrateur Skype entreprise Online, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="81bad-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="81bad-115">Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **vérifier**.</span><span class="sxs-lookup"><span data-stu-id="81bad-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="81bad-116">Pour plus d'informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="81bad-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="81bad-117">Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81bad-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="81bad-118">Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81bad-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="81bad-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81bad-119">See also</span></span>

[<span data-ttu-id="81bad-120">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81bad-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="81bad-121">Mise en route d’Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81bad-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="81bad-122">Références de l’applet de commande PowerShell Skype entreprise</span><span class="sxs-lookup"><span data-stu-id="81bad-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

