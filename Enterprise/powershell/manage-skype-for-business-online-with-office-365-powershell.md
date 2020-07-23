---
title: Gestion de Skype entreprise Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour gérer des stratégies Skype entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230440"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="8aa28-103">Gestion de Skype entreprise Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aa28-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="8aa28-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="8aa28-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="8aa28-105">Une des tâches principales de tout administrateur de Skype Entreprise Online est la gestion des stratégies.</span><span class="sxs-lookup"><span data-stu-id="8aa28-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="8aa28-106">Bien que vous puissiez effectuer certaines de ces tâches dans le centre d’administration 365 de Microsoft, les autres tâches sont beaucoup plus rapides et plus faciles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8aa28-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="8aa28-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="8aa28-107">Before you start</span></span>

<span data-ttu-id="8aa28-108">Téléchargez et installez le [module du connecteur Skype entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366), puis redémarrez votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8aa28-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="8aa28-109">Se connecter à l’aide du nom et du mot de passe d’un compte d’administrateur Skype entreprise Online</span><span class="sxs-lookup"><span data-stu-id="8aa28-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="8aa28-110">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8aa28-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="8aa28-111">Dans la boîte de dialogue **demande d’informations d’identification Windows PowerShell** , tapez le nom et le mot de passe de votre compte d’administrateur Skype entreprise Online, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8aa28-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="8aa28-112">Se connecter à l’aide d’un compte d’administrateur Skype entreprise Online avec l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="8aa28-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="8aa28-113">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8aa28-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="8aa28-114">Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez le nom de votre compte d’administrateur Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="8aa28-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="8aa28-115">Dans la boîte de dialogue **se connecter à votre compte** , saisissez votre mot de passe d’administrateur Skype entreprise Online, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="8aa28-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="8aa28-116">Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **vérifier**.</span><span class="sxs-lookup"><span data-stu-id="8aa28-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="8aa28-117">Pour plus d’informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8aa28-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="8aa28-118">Gestion des stratégies Skype entreprise Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aa28-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="8aa28-119">Affecter des stratégies Skype entreprise Online par utilisateur avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aa28-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="8aa28-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aa28-120">See also</span></span>

[<span data-ttu-id="8aa28-121">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aa28-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8aa28-122">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8aa28-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="8aa28-123">Références de l’applet de commande PowerShell Skype entreprise</span><span class="sxs-lookup"><span data-stu-id="8aa28-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

