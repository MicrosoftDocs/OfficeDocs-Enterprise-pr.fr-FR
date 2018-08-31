---
title: Préparer la mise en service des utilisateurs via  la synchronisation d’annuaires vers Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment préparer la mise en service des utilisateurs vers Office 365 à l’aide de la synchronisation d’annuaires et les avantages à long terme de l’utilisation de cette méthode.
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540590"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Préparer la mise en service des utilisateurs via  la synchronisation d’annuaires vers Office 365

Mise en service des utilisateurs avec la synchronisation d’annuaires requiert plus de planification et de préparation à la gestion des simplement de votre compte professionnel ou de l’école directement dans Office 365. Les tâches de planification et de préparation supplémentaires sont nécessaires pour vous assurer que votre environnement sur site Active Directory synchronise correctement pour Azure Active Directory. L’ajout à votre organisation les avantages :
  
- Réduction des programmes d'administration au sein de votre organisation
- En activant le scénario d’authentification unique
- Automatisation des modifications de compte dans Office 365
    
Pour plus d’informations sur les avantages de l’utilisation de la synchronisation d’annuaires, voir [Guide de synchronisation de répertoire]( https://go.microsoft.com/fwlink/p/?LinkId=525398) et les [identités Office 365 et Azure Active Directory](about-office-365-identity.md).
  
Pour déterminer quel scénario est le mieux pour votre organisation, passez en revue la [comparaison des outils de l’intégration directory](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Tâches de nettoyage d’annuaire

Avant de commencer la synchronisation de votre annuaire, vous devez nettoyer votre annuaire.
  
Consultez également les [attributs synchronisés avec Azure Active Directory par Azure AD se connecter](https://go.microsoft.com/fwlink/p/?LinkId=746480).
  
> [!IMPORTANT]
> Si vous n’effectuez le nettoyage d’annuaire avant la synchronisation, il peut y avoir une incidence négative importante sur le processus de déploiement. Il peut prendre plusieurs jours ou semaines, transitent par le cycle de synchronisation d’annuaire, qui identifie les erreurs et resynchronisation. 
  
Dans votre annuaire local, effectuez les tâches de nettoyage suivantes :
  
1. Assurez-vous que chaque utilisateur auquel des offres de service Office 365 seront attribuées dispose d’une adresse électronique valide et unique dans l’attribut **proxyAddresses**. 
    
2. Supprimez les valeurs en double dans l'attribut **proxyAddresses**. 
    
3.  Si possible, assurez-vous que chaque utilisateur qui sera attribué offres de services Office 365 a pour valeur pour l’attribut **userPrincipalName** valide et unique dans l’objet **utilisateur** de l’utilisateur. Pour une meilleure expérience de synchronisation, vérifiez l’UPN sur site Active Directory établit une correspondance avec le nuage UPN. Si un utilisateur ne dispose pas d’une valeur pour l’attribut **userPrincipalName** , l’objet **utilisateur** doit contenir une valeur valide et unique pour l’attribut **sAMAccountName** . Supprimez les valeurs en double dans l’attribut **userPrincipalName** . 
    
4. Pour une utilisation optimale de la liste d'adresses globale (LAG), assurez-vous que les informations des attributs suivants sont correctes :
    
  - givenName 
  - nom
  - displayName
  - Fonction
  - Service
  - Bureau
  - Téléphone (bureau)
  - Téléphone mobile
  - Numéro de télécopie
  - Rue
  - Ville
  - Département ou province
  - Code postal
  - Pays ou région
    
## <a name="directory-object-and-attribute-preparation"></a>Préparation d'objet et attribut d'annuaire

Synchronisation d’annuaires réussie entre votre annuaire local et d’Office 365 nécessite que votre attributs d’annuaire local sont correctement préparés. Par exemple, vous devez vous assurer que les caractères spécifiques ne sont pas utilisés dans certains attributs sont synchronisés avec l’environnement Office 365. Caractères inattendus ne provoquent pas la synchronisation d’annuaires échoue mais peuvent retourner un message d’avertissement. Caractères non valides entraîne la synchronisation d’annuaires échoue.
  
La synchronisation d’annuaires échouera également si certains de vos utilisateurs Active Directory ont un ou plusieurs attributs en double. Chaque utilisateur doit disposer des attributs uniques.
  
Vous devez préparer les attributs sont répertoriés ici :
  
 **Remarque :** Vous pouvez également utiliser l' [outil IdFix](install-and-run-idfix.md) pour rendre ce processus beaucoup plus facile. 
  
- **displayName**
    
  - Si l'attribut existe dans l'objet utilisateur, il sera synchronisé avec Office 365.
  - Si cet attribut existe dans l'objet utilisateur, une valeur doit lui être attribuée. En d'autres termes, il ne doit pas être vide.
  - Nombre maximal de caractères : 256
    
- **givenName **
    
  - Si l'attribut est présent dans l'objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 n'exige pas son utilisation.
  - Nombre maximal de caractères : 64
    
- **messagerie**
    
  - La valeur de l’attribut doit être unique dans l’annuaire.
    
    > [!NOTE]
    > S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé. Les utilisateurs suivants n’apparaissent pas dans Office 365. Vous devez modifier la valeur dans Office 365, ou modifier les deux valeurs dans le répertoire local afin que les deux utilisateurs dans Office 365. 
  
- **mailNickname** (alias Exchange) 
    
  - La valeur d’attribut ne peut pas commencer par un point (.).
  - La valeur de l’attribut doit être unique dans l’annuaire.
    
- **proxyAddresses **
    
  - Attribut à valeur multiple
  - Nombre maximal de caractères par valeur : 256
  - La valeur d’attribut ne doit pas contenir un espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides : \< \> () ; , [ ] "
    
    Notez que les caractères non valides s’appliquent pour les caractères qui suivent le séparateur de type et « : », telle que SMTP:User@contso.com est autorisée, mais n’est pas SMTP:user:M@contoso.com.
    
    > [!IMPORTANT]
    > Toutes les adresses SMTP Simple Mail Transport Protocol () doivent se conformer aux standards de messagerie électronique. S’il existent d’adresses en doublons ou indésirables, consultez la rubrique [suppression proxy dupliqué et indésirable adresses dans Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Nombre maximal de caractères : 20
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides : [\ "|, / : \< \> + = ; ? \* ]
  - Si un utilisateur présente un attribut **sAMAccountName** non valide, mais dispose d'un attribut **userPrincipalName** valide, le compte d'utilisateur est créé dans Office 365. 
  - Si les **attributs sAMAccountName** et **userPrincipalName** ne sont pas valides, l’attribut **userPrincipalName** de Active Directory local doit être mis à jour. 
    
- **sn** (surname, patronyme) 
    
  - Si l'attribut est présent dans l'objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 n'exige pas son utilisation.
    
- **targetAddress**
    
    Il est nécessaire que l’attribut **targetAddress** (par exemple, SMTP:tom@contoso.com) qui est remplie pour l’utilisateur doit apparaître dans la liste d’adresses globale de Office 365. Dans les scénarios de la migration de messagerie tiers, cela nécessite l’extension du schéma Office 365 pour le répertoire local. L’extension de schéma Office 365 serait également ajouter d’autres attributs utiles pour gérer les objets Office 365 qui sont remplis à l’aide d’un outil de synchronisation d’annuaire à partir de l’annuaire local. Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution doit être ajouté. 
   
  - Nombre maximal de caractères : 256
  - La valeur d’attribut ne doit pas contenir un espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides : \ \< \> () ; , [ ] "
  - Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent respecter les normes de messagerie électronique.
    
- **userPrincipalName**
    
  - L’attribut **userPrincipalName** doit être au format de connexion style Internet où le nom d’utilisateur est suivi par l’arobase (@) et un nom de domaine : par exemple, user@contoso.com. Toutes les adresses SMTP Simple Mail Transport Protocol () doivent se conformer aux standards de messagerie électronique.
  - Le nombre maximal de caractères pour l’attribut **userPrincipalName** est de 113. Un nombre spécifique de caractères est autorisé avant et après le signe (@), comme suit : 
  - Nombre maximal de caractères du nom d'utilisateur précédant l'arobase (@) : 64
  - Nombre maximal de caractères du nom de domaine suivant l'arobase (@) : 48
  - Caractères non valides : \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Un tréma est également un caractère non valide.
  - Le caractère @ est requis dans chaque valeur **userPrincipalName** . 
  - Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName**. 
  - Le nom d’utilisateur ne peut pas se terminer par un point (.), une esperluette (&amp;), un espace ou une arobase (@).
  - Le nom d’utilisateur ne peut pas contenir d’espaces.
  - Domaines routables doivent être utilisés ; par exemple, les domaines locales ou internes ne peut être utilisés.
  - Unicode est converti en caractères de trait de soulignement.
  - L’attribut **userPrincipalName** ne peut pas contenir de valeurs en double dans l’annuaire. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Préparation de l'attribut userPrincipalName

Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation pour vous connecter à votre répertoire en utilisant **userPrincipalName**ou **sAMAccountName** . De même, les utilisateurs finaux peuvent se connecter à Office 365 à l’aide du nom d’utilisateur principal (UPN) de leur travail ou école compte. La synchronisation d’annuaires tente de créer de nouveaux utilisateurs dans Azure Active Directory à l’aide de la même UPN qui se trouve dans votre répertoire local. L’UPN est mis en forme comme une adresse de messagerie. 

Dans Office 365, l’UPN est l’attribut par défaut qui est utilisé pour générer l’adresse de messagerie. Il est facile d’obtenir **l’attribut userPrincipalName** (sur site et dans Azure Active Directory) et l’adresse de messagerie principale dans **proxyAddresses** valeurs différentes. Lorsqu’ils sont définis à des valeurs différentes, il peut être source de confusion pour les administrateurs et les utilisateurs finaux. 
  
Il est préférable d’aligner ces attributs pour réduire les risques de confusion. Pour satisfaire les exigences d’authentification unique avec Active Directory Federation Services (AD FS) 2.0, vous devez vous assurer que l’UPN dans Azure Active Directory et Active Directory local correspondent et qu’ils utilisent un espace de noms de domaine valide.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Ajouter un autre suffixe UPN à AD DS

Vous devrez peut-être ajouter un autre suffixe UPN pour associer des informations d’identification d’entreprise de l’utilisateur à l’environnement Office 365. Un suffixe UPN est la partie d’un nom UPN à droite le caractère @. UPN qui est utilisés pour l’authentification unique peut contenir des lettres, chiffres, périodes, tirets et des traits de soulignement, mais aucun autre type de caractères.
  
Pour plus d’informations sur la façon d’ajouter un autre suffixe UPN à Active Directory, voir [préparer la synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Correspond à l’UPN local avec la Office 365 UPN

Si vous avez déjà configuré la synchronisation d’annuaires, UPN de l’utilisateur pour Office 365 peut correspondre pas UPN local de l’utilisateur qui est défini dans votre service d’annuaire local. Cela peut se produire lorsqu’un utilisateur a été attribué une licence avant le domaine a été vérifié. Pour résoudre ce problème, utiliser [PowerShell pour résoudre les UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730) pour mettre à jour le nom UPN de l’utilisateur pour vous assurer qu’Office 365 UPN établit une correspondance avec le nom d’utilisateur d’entreprise et le domaine. Si vous mettez à jour l’UPN dans le service d’annuaire local et que vous souhaitez synchroniser avec l’identité d’Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Office 365 avant de rendre les modifications locales. 
  
Voir aussi [comment préparer un domaine non routable (par exemple, domaine .local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Outils de l’intégration d’annuaire

La synchronisation d’annuaires est la synchronisation des objets d’annuaire (utilisateurs, groupes et contacts) à partir de votre environnement d’Active Directory sur site à l’infrastructure d’annuaire Office 365, Azure Active Directory. Pour obtenir la liste des outils disponibles et leurs fonctionnalités, voir [Outils de l’intégration d’annuaire](https://go.microsoft.com/fwlink/p/?LinkID=510956) . L’outil recommandé est [Microsoft Azure Active Directory se connecter](https://go.microsoft.com/fwlink/p/?LinkID=510956). Pour plus d’informations sur Azure Active Directory se connecter, voir [intégration des identités avec Azure Active Directory local](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Lorsque des comptes d’utilisateur sont synchronisés avec l’annuaire Office 365 pour la première fois, ils sont marqués comme non activée. Ils ne peuvent pas envoyer ou recevoir du courrier électronique, et ils n’utilisent pas de licences d’abonnement. Lorsque vous êtes prêt à affecter des abonnements Office 365 à des utilisateurs spécifiques, vous devez sélectionner et les activer à [attribuer des licences aux utilisateurs dans Office 365 pour entreprises](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
Vous pouvez également utiliser [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) pour attribuer des licences. Une solution automatisée, voir [comment utiliser PowerShell pour attribuer automatiquement des licences à vos utilisateurs d’Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) .