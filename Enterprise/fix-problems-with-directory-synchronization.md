---
title: Résoudre les problèmes de synchronisation d’annuaires pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Décrit les causes fréquentes des problèmes de synchronisation d’annuaires dans Office 365 et fournit plusieurs méthodes de résolution.
ms.openlocfilehash: faf0f061b8f2798054e63f3338b8076c0ec88f73
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46570967"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Résoudre les problèmes de synchronisation d’annuaires pour Microsoft 365

Avec la synchronisation d’annuaires, vous pouvez continuer à gérer les utilisateurs et les groupes sur site et à synchroniser les ajouts, les suppressions et les modifications dans le nuage. Cependant, la configuration est un peu compliquée, et il est parfois difficile d’identifier la source des problèmes. Nous vous proposons des ressources pour vous aider à identifier les problèmes potentiels et à les corriger.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Comment savoir si un problème se pose ?

La première indication qu’un problème est incorrect se produit lorsque la vignette de l’état de la synchronisation d’annuaire dans le centre d’administration Microsoft 365 indique un problème.
  
Vous allez également recevoir un message (adressé à votre adresse de messagerie de secours et à l’adresse de messagerie de l’administrateur) de Microsoft 365, indiquant que votre client a rencontré des erreurs de synchronisation d’annuaires. Pour plus d’informations, voir [Identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Comment obtenir l’outil Azure Active Directory Connect ?

Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com), accédez à **Utilisateurs** \> **Utilisateurs actifs**. Cliquez sur le menu **Plus** (points de suspension), puis sélectionnez **Synchronisation d’annuaires**. 
  
Suivez les [instructions de l’Assistant](set-up-directory-synchronization.md) pour télécharger Azure AD Connect. 
  
Si vous utilisez toujours la synchronisation Azure Active Directory (Azure AD) (DirSync), consultez la page [Résolution des messages d’erreur lors de l’installation de l’outil de synchronisation Azure Active Directory et de l’Assistant Configuration dans Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) pour plus d’informations sur la configuration requise pour installer la synchronisation d’annuaires, les autorisations requises et le dépannage des erreurs courantes. 
  
Pour effectuer la mise à jour à partir d’Azure AD Sync vers Azure AD Connect, voir [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Résolution des problèmes courants liés à la synchronisation d’annuaires dans Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Les objets synchronisés n’apparaissent pas ou ne sont pas mis à jour en ligne, ou j’obtiens des rapports d’erreurs de synchronisation du service.

- [Synchronisation des identités et résilience des attributs en double](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>J’ai reçu une alerte dans le centre d’administration, ou je reçois des messages automatisés indiquant qu’il n’y a pas eu d’événement de synchronisation récemment
- [Résoudre les problèmes de connectivité avec Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Comptes et autorisations Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Synchronisation Azure AD Connect : gérer le compte de service Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [La synchronisation d’annuaires avec Azure Active Directory s’arrête ou vous êtes informé qu’aucune synchronisation n’a été enregistrée depuis plus d’une journée](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Les hachages de mot de passe ne sont pas synchronisés ou une alerte dans le centre d’administration indique qu’il n’existe aucune synchronisation récente de hachage de mot de passe
- [Mise en œuvre de la synchronisation du hachage de mot de passe avec la synchronisation Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Une alerte indiquant un dépassement du quota d’objets apparaît
- Un quota d’objets prédéfini permet de protéger le service. Si trop d’objets dans votre annuaire doivent être synchronisés avec Microsoft 365, vous devrez [Contacter le support technique des produits professionnels](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour augmenter votre quota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>J’ai besoin de savoir quels attributs sont synchronisés.
- La liste des attributs synchronisés entre l’environnement local et le cloud est [disponible ici](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Je ne peux pas gérer ou supprimer les objets synchronisés avec le cloud
- Êtes-vous prêt à gérer les objets dans le nuage uniquement ? Ou existe-t-il un objet qui a été supprimé sur site, mais qui est bloqué dans le nuage ? Consultez cet [Résolution des erreurs lors de la synchronisation](https://go.microsoft.com/fwlink/p/?linkid=842044) et [article du support technique](https://go.microsoft.com/fwlink/p/?LinkId=396720) pour obtenir des instructions sur la résolution de ces problèmes.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>J’ai reçu un message d’erreur indiquant que mon entreprise avait dépassé le nombre d’objets pouvant être synchronisés.
- Vous pouvez consulter davantage d’informations sur le problème [ici](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Autres ressources

- [Script de résolution des noms d’utilisateurs principaux en double](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Préparation d’un domaine non routable (par exemple, le domaine .local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script de décompte du nombre total d’objets synchronisés](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Résoudre les problèmes d’AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Utiliser PowerShell pour corriger les attributs DisplayName vides pour les groupes à extension messagerie](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Utiliser PowerShell pour corriger les noms d’utilisateurs principaux en double](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Utiliser PowerShell pour corriger les adresses de courrier en double](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
