---
title: Réponse aux incidents de sécurité Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/27/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Cette solution indique les attaques vous quel la plus courantes la sécurité peut se présenter comme dans Office 365 et comment y répondre
ms.openlocfilehash: b9800070bde662603c731e2b8d64609b4f821cce
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="office-365-security-incident-response"></a><span data-ttu-id="b3dae-103">Réponse aux incidents de sécurité Office 365</span><span class="sxs-lookup"><span data-stu-id="b3dae-103">Office 365 Security Incident Response</span></span>

 <span data-ttu-id="b3dae-104">**Résumé :** Cette solution indique quelles sont les indicateurs pour les attaques de la sécurité les plus courantes dans Office 365, comment vérifier positive une attaque donnée et comment y répondre.</span><span class="sxs-lookup"><span data-stu-id="b3dae-104">**Summary:** This solution tells you what the indicators are for the most common cyber-security attacks in Office 365, how to positively confirm any given attack, and how to respond to it.</span></span>
  
## <a name="overview"></a><span data-ttu-id="b3dae-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b3dae-105">Overview</span></span>
<span data-ttu-id="b3dae-p101">Peuvent ne possédant pas toutes les attaques informatiques. Les pirates recherchent en permanence des nouvelles failles dans votre stratégie de défense ou ils exploitent anciennes. Savoir comment reconnaître une attaque vous permet de réagir plus rapidement à celui-ci, ce qui réduit la durée de l’incident de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b3dae-p101">Not all cyber attacks can be thwarted. Attackers are constantly looking for new weaknesses in your defensive strategy or they are exploiting old ones. Knowing how to recognize an attack allows you to respond to it faster, which shortens the duration of the security incident.</span></span>

<span data-ttu-id="b3dae-p102">Cette série d’article permet de comprendre qu’un type particulier d’attaque peut se présenter comme dans Office 365 et vous donne les étapes à que suivre pour répondre. Ils sont des points d’entrée rapide de la présentation :</span><span class="sxs-lookup"><span data-stu-id="b3dae-p102">This series of article helps you understand what a particular type of attack might look like in Office 365 and gives you steps you can take to respond. They are quick entry points to understanding:</span></span>
 
- <span data-ttu-id="b3dae-111">Quel l’attaque est et comment il fonctionne.</span><span class="sxs-lookup"><span data-stu-id="b3dae-111">What the attack is and how it works.</span></span>
- <span data-ttu-id="b3dae-112">Ce qui se connecte, appelés indicateurs de compromis (IOC), pour rechercher et comment les rechercher.</span><span class="sxs-lookup"><span data-stu-id="b3dae-112">What signs, called indicators of compromise (IOC), to look for and how to look for them.</span></span>
- <span data-ttu-id="b3dae-113">Comment positive confirmer l’attaque.</span><span class="sxs-lookup"><span data-stu-id="b3dae-113">How to positively confirm the attack.</span></span>
- <span data-ttu-id="b3dae-114">Étapes à suivre pour coupé l’attaque et une meilleure protègent de votre organisation à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="b3dae-114">Steps to take to cut off the attack and better protect your organization in the future.</span></span>
- <span data-ttu-id="b3dae-115">Des liens vers des informations détaillées sur chacun des attaquent de type.</span><span class="sxs-lookup"><span data-stu-id="b3dae-115">Links to in-depth information on each attack type.</span></span>

<span data-ttu-id="b3dae-116">Recherchez tous les mois comme d’autres articles seront ajoutés au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="b3dae-116">Check back here monthly as more articles will be added over time.</span></span>

## <a name="detect-and-remediate-articles"></a><span data-ttu-id="b3dae-117">Détecter et de corriger des Articles</span><span class="sxs-lookup"><span data-stu-id="b3dae-117">Detect and Remediate Articles</span></span>
- [<span data-ttu-id="b3dae-118">Détecter et résoudre les accorde consentement illicite dans Office 365</span><span class="sxs-lookup"><span data-stu-id="b3dae-118">Detect and Remediate Illicit Consent Grants in Office 365</span></span>](detect-and-remediate-illicit-consent-grants.md)
- [<span data-ttu-id="b3dae-119">Détecter et résoudre les règles d’Outlook et les attaques Injections de formulaires personnalisés dans Office 365</span><span class="sxs-lookup"><span data-stu-id="b3dae-119">Detect and Remediate Outlook Rules and Custom Forms Injections Attacks in Office 365</span></span>](detect-and-remediate-outlook-rules-forms-attack.md)
 
## <a name="secure-office-365-like-a-cybersecurity-pro"></a><span data-ttu-id="b3dae-120">Sécuriser Office 365 comme une sécurité pro</span><span class="sxs-lookup"><span data-stu-id="b3dae-120">Secure Office 365 like a cybersecurity pro</span></span>
<span data-ttu-id="b3dae-p103">Votre abonnement Office 365 est fourni avec un ensemble de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs puissantes.  Utiliser le [Guide de sécurité Office 365 : principaux des priorités pour les 30 premiers jours, 90 jours et au-delà](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) à mettre en œuvre les meilleures pratiques pour la sécurisation de votre client Office 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3dae-p103">Your Office 365 subscription comes with a powerful set of security capabilities that you can use to protect your data and your users.  Use the [Office 365 security roadmap: Top priorities for the first 30 days, 90 days, and beyond](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) to implement Microsoft recommended best practices for securing your Office 365 tenant.</span></span>
- <span data-ttu-id="b3dae-p104">Tâches à accomplir dans les 30 jours.  Ces ont une incidence immédiate et sont faible impact à vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b3dae-p104">Tasks to accomplish in the first 30 days.  These have immediate affect and are low-impact to your users.</span></span>
- <span data-ttu-id="b3dae-p105">Tâches à accomplir dans 90 jours. Ces prennent un peu plus de temps pour planifier et implémenter mais améliorer sensiblement votre sécurité</span><span class="sxs-lookup"><span data-stu-id="b3dae-p105">Tasks to accomplish in 90 days. These take a bit more time to plan and implement but greatly improve your security posture</span></span>
- <span data-ttu-id="b3dae-p106">Au-delà de 90 jours. Ces améliorations créer votre premier travail 90 jours.</span><span class="sxs-lookup"><span data-stu-id="b3dae-p106">Beyond 90 days. These enhancements build in your first 90 days work.</span></span>






