---
title: Résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
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
description: Décrit les causes courantes des problèmes liés à la synchronisation d’annuaires dans Office 365 et fournit quelques méthodes pour les aider à les résoudre.
ms.openlocfilehash: cb2ec57331d227f0965095ee0782f13af935d569
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711906"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365

Avec la synchronisation d’annuaires, vous pouvez continuer à gérer les utilisateurs et les groupes locaux et synchroniser les ajouts, les suppressions et les modifications dans le Cloud. Toutefois, le programme d’installation est un peu compliqué et il peut parfois être difficile d’identifier la source des problèmes. Nous disposons de ressources pour vous aider à identifier les problèmes potentiels et à les résoudre.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Comment savoir si un problème est survenu ?

La première indication que un élément est incorrect est lorsque la vignette d’État DirSync dans le centre d’administration Microsoft 365 indique qu’il y a un problème.
  
Vous recevrez également un message (vers l’autre courrier électronique et vers votre messagerie d’administrateur) de Microsoft 365 qui indique que votre locataire a rencontré des erreurs de synchronisation d’annuaires. Pour plus d’informations, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Comment puis-je obtenir l’outil Azure Active Directory Connect ?

Dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com), **accédez à utilisateurs** \> **actifs**. Cliquez sur le menu **plus** (trois points) et sélectionnez **synchronisation d’annuaires**. 
  
Suivez les [instructions de l’Assistant](set-up-directory-synchronization.md) pour télécharger Azure ad Connect. 
  
Si vous utilisez toujours Azure Active Directory Sync (DirSync), consultez la rubrique relative à la résolution des problèmes liés à l’installation de l' [outil de synchronisation Azure Active Directory et aux messages d’erreur de l’Assistant Configuration dans Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) pour plus d’informations sur la configuration système requise pour installer DirSync, les autorisations dont vous avez besoin et sur la résolution des erreurs courantes. 
  
Pour effectuer une mise à jour à partir d’Azure Active Directory Sync vers Azure AD Connect, consultez [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Résolution des causes courantes des problèmes liés à la synchronisation d’annuaires dans Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Les objets synchronisés n’apparaissent pas ou ne sont pas mis à jour en ligne, ou des rapports d’erreur de synchronisation proviennent du service.**

- [Synchronisation des identités et résilience des attributs en double](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**J’ai une alerte dans le centre d’administration, ou je reçois des courriers électroniques automatiques qu’il n’y a pas eu un événement de synchronisation récent**
- [Résoudre les problèmes de connectivité avec Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Comptes et autorisations Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Synchronisation Azure AD Connect : gérer le compte de service Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [La synchronisation d’annuaires avec Azure Active Directory s’arrête ou vous êtes informé qu’aucune synchronisation n’a été enregistrée depuis plus d’une journée](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Les hachages de mot de passe ne sont pas synchronisés ou une alerte s’affiche dans le centre d’administration pour signaler qu’il n’y a pas eu une synchronisation récente de hachage de mot de passe**
- [Mise en œuvre de la synchronisation du hachage de mot de passe avec la synchronisation Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Je vois une alerte indiquant le dépassement du quota d’objet**
- Nous disposons d’un quota d’objets intégré pour aider à protéger le service. Si vous avez trop d’objets dans votre répertoire qui doivent être synchronisés avec Microsoft 365, vous devrez [contacter le support technique pour les produits professionnels](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) afin d’augmenter votre quota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**J’ai besoin de savoir quels attributs sont synchronisés**
- Vous pouvez trouver la liste de tous les attributs synchronisés entre l’organisation locale et le nuage dans ce [cas](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Je ne peux pas gérer ou supprimer des objets qui ont été synchronisés dans le Cloud**
- Êtes-vous prêt à gérer les objets dans le Cloud uniquement ? Ou y a-t-il un objet qui a été supprimé en local, mais qui est bloqué dans le Cloud ? Consultez cette rubrique relative à la [résolution des erreurs lors](https://go.microsoft.com/fwlink/p/?linkid=842044) de la synchronisation et de [l’article de support](https://go.microsoft.com/fwlink/p/?LinkId=396720) pour obtenir des instructions sur la résolution de ces problèmes.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**J’ai reçu un message d’erreur indiquant que mon entreprise a dépassé le nombre d’objets pouvant être synchronisés.**
- Pour plus d’informations sur ce problème, consultez la [rubrique](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Autres ressources

- [Script de résolution des noms d'utilisateurs principaux en double](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Préparation d’un domaine non routable (par exemple, domaine. local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script pour compter le nombre total d’objets synchronisés](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Résoudre les problèmes liés à AD FS 2,0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Utiliser PowerShell pour corriger les attributs DisplayName vides pour les groupes à extension messagerie](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Utiliser PowerShell pour corriger le nom UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Utiliser PowerShell pour corriger des adresses de messagerie en double](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Outils de diagnostic

L' [outil IDFix](prepare-directory-attributes-for-synch-with-idfix.md) permet de détecter et de résoudre les objets Identity et leurs attributs dans un environnement Active Directory local en préparation à la migration vers Microsoft 365. IDFix est destiné aux administrateurs Active Directory responsables de la synchronisation d’annuaires avec le service Microsoft 365. 

[Téléchargez l’outil IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) à partir du centre de téléchargement Microsoft.