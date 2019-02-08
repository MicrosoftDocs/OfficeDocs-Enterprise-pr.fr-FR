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
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Résoudre les problèmes de synchronisation d’annuaires pour Office 365

Avec la synchronisation d’annuaires, vous pouvez continuer à gérer les utilisateurs et groupes locaux et synchronisez les ajouts, suppressions et modifications vers le nuage. Le programme d’installation est un peu compliqué, mais il peut parfois être difficile d’identifier la source des problèmes. Nous disposons de ressources pour vous aider à identifier les problèmes potentiels et à les résoudre.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Comment savoir si un élément est incorrect ?

La première indication que quelque chose est incorrect est lorsque la vignette de l’état de synchronisation d’annuaire dans le centre d’administration Office 365 indique un problème est survenu :
  
![L’état de synchronisation d’annuaire en mosaïque dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Vous recevrez un courrier électronique (à l’autre application de messagerie et votre adresse e-mail d’administration) à partir d’Office 365 qui indique votre client a rencontré des erreurs de synchronisation d’annuaire. Pour plus d’informations, consultez [identifier des erreurs de synchronisation d’annuaire dans Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Comment obtenir outil Azure Active Directory se connecter ?

Dans le centre d’administration Office 365, accédez à ** utilisateurs ** \> **utilisateurs actifs**. Cliquez sur le menu **plus** et sélectionnez **la synchronisation d’annuaires**. 
  
![Dans le menu autres, choisissez la synchronisation d’annuaires](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Dans le centre d’administration Office 365 anciens, accédez aux **utilisateurs** \> **Utilisateurs actifs**et sélectionnez **configurer** en regard de **synchronisation Active Directory**. 
  
![Sélectionnez définir en regard de synchronisation Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Suivez les [instructions de l’Assistant](set-up-directory-synchronization.md) pour télécharger Azure AD se connecter. 
  
Si vous utilisez toujours la synchronisation Azure Active Directory (DirSync), jetez un œil à [comment résoudre les problèmes d’installation de l’outil de synchronisation Azure Active Directory et l’Assistant Configuration des messages d’erreur dans Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) pour plus d’informations sur la configuration système requise pour installer synchronisation d’annuaire, les autorisations dont vous avez besoin et comment résoudre les erreurs courantes. 
  
Pour mettre à jour à partir de synchronisation Azure Active Directory pour établir la connexion Azure AD, voir [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Résolution courantes entraîne des problèmes liés à la synchronisation d’annuaires dans Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Objets synchronisés ne sont pas apparaître ou mise à jour en ligne, ou je reçois des rapports d’erreurs de synchronisation à partir du Service.**

- [Résistance des attribut Identity synchronisation et en double](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**J’ont une alerte dans le centre d’administration d’Office 365, ou reçois automatisée de messages électroniques qu’il n’a pas été un événement de synchronisation récents**
- [Résoudre les problèmes de connectivité avec Azure AD se connecter](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD connecter les comptes et autorisations](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect sync : comment gérer le compte de service Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Synchronisation d’annuaire s’arrête Azure Active Directory ou que vous êtes averti que la synchronisation n’a pas encore inscrit dans plus d’un jour](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Les hachages de mot de passe ne sont pas synchronisation ou j’obtiens une alerte dans le centre d’administration Office 365 qu’il n’a pas été une synchronisation de hachage de mot de passe récents**
- [Implémentation de la synchronisation de hachage de mot de passe avec la synchronisation Azure Active Directory se connecter](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**J’obtiens une alerte qui a dépassé le quota de l’objet**
- Nous disposons d’un quota de l’objet intégré pour protéger le service. Si vous avez trop d’objets dans votre annuaire qui doivent effectuer une synchronisation avec Office 365, vous devrez [Contact prend en charge pour les produits d’entreprise](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour augmenter le quota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**J’ai besoin de savoir quels attributs sont synchronisés.**
- Vous trouverez une liste de tous les attributs sont synchronisés entre le nuage [ici](https://go.microsoft.com/fwlink/p/?LinkId=396719)et en local.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Je ne parviens pas à gérer ou supprimer des objets qui ont été synchronisées avec le nuage**
- Vous êtes prêt à gérer les objets dans le nuage uniquement ? Ou un objet qui a été supprimé localement, mais est bloqué dans le nuage ? Jetez un œil à ce [Dépannage des erreurs lors de la synchronisation](https://go.microsoft.com/fwlink/p/?linkid=842044) et la [prise en charge de l’article](https://go.microsoft.com/fwlink/p/?LinkId=396720) pour obtenir des instructions sur la façon de résoudre ces problèmes.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**J’ai reçu un message d’erreur indiquant que mon entreprise avait dépassé le nombre d’objets pouvant être synchronisés.**
- Vous pouvez en savoir plus sur ce problème [ici](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Autres ressources

- [Script de résolution des noms d'utilisateurs principaux en double](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Comment faire pour préparer un domaine non routable (par exemple, domaine .local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script permettant de compter le nombre total d’objets synchronisé](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Dépanner AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Utiliser PowerShell pour résoudre les attributs DisplayName vides pour les groupes à extension messagerie](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Utiliser PowerShell pour résoudre les UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Utiliser PowerShell pour résoudre les adresses de messagerie en double](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Outils de diagnostic

[Outil IDFix](prepare-directory-attributes-for-synch-with-idfix.md) est utilisé pour effectuer la recherche et la résolution des objets d’identité et de leurs attributs dans un environnement d’Active Directory sur site en vue de la migration vers Office 365. IDFix est destinée aux administrateurs Active Directory responsables de la synchronisation d’annuaire avec le service Office 365. 

[Télécharger l’outil IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) à partir du centre de téléchargement Microsoft.