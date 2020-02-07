---
title: Préparer la synchronisation d’annuaires vers Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment préparer la mise en service des utilisateurs vers Office 365 à l’aide de la synchronisation d’annuaires et des avantages à long terme de cette méthode.
ms.openlocfilehash: 948db4d5dca8d5deb9844ff9a7ec652653a5ab6b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841171"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a>Préparer la synchronisation d’annuaires vers Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Les avantages de la synchronisation hybride des identités et des annuaires de votre organisation sont les suivants :
  
- Réduction des programmes d’administration au sein de votre organisation
- Activer le scénario d’authentification unique (facultatif)
- Automatisation des modifications de compte dans Office 365
    
Pour plus d’informations sur les avantages liés à l’utilisation de la synchronisation d’annuaires, consultez la rubrique feuille de [route de synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525398) et [identité hybride pour Office 365](plan-for-directory-synchronization.md).

Toutefois, la synchronisation d’annuaires nécessite une planification et une préparation afin de s’assurer que vos services de domaine Active Directory (AD DS) sont synchronisés avec le client Azure Active Directory (Azure AD) de votre abonnement Office 365 avec un minimum d’erreurs. 

Suivez les étapes ci-dessous pour obtenir les meilleurs résultats.
  
## <a name="1-directory-cleanup-tasks"></a>1. tâches de nettoyage d’annuaire

Avant de synchroniser vos services AD DS avec votre client Azure AD, vous devez nettoyer votre service AD DS.

> [!IMPORTANT]
> Si vous n’effectuez pas le nettoyage AD DS avant la synchronisation, le processus de déploiement peut avoir un impact significatif. Cela peut prendre des jours, voire des semaines, pour parcourir le cycle de synchronisation d’annuaires, l’identification des erreurs et la resynchronisation. 
  
Dans votre AD DS, effectuez les tâches de nettoyage suivantes pour chaque compte d’utilisateur auquel est attribuée une licence Office 365 :
  
1. Assurez-vous d’une adresse de messagerie unique et valide dans l’attribut **proxyAddresses** . 
  
2. Supprimez toutes les valeurs en double dans l’attribut **proxyAddresses** . 
    
3.  Dans la mesure du possible, vérifiez que la valeur de l’attribut **userPrincipalName** est valide et unique dans l’objet **User** de l’utilisateur. Pour une expérience de synchronisation optimale, vérifiez que l’UPN AD DS correspond à l’UPN Azure AD. Si un utilisateur n’a pas de valeur pour l’attribut **userPrincipalName** , l’objet **User** doit contenir une valeur valide et unique pour l’attribut **sAMAccountName** . Supprimez toutes les valeurs en double dans l’attribut **userPrincipalName** . 
    
4. Pour une utilisation optimale de la liste d’adresses globale (LAG), assurez-vous que les informations figurant dans les attributs suivants du compte d’utilisateur AD DS sont correctes :
    
  - givenName
  - surname
  - displayName
  - Fonction
  - Service
  - Bureau
  - Téléphone (bureau)
  - Téléphone mobile
  - Numéro de télécopie
  - Rue
  - Ville
  - Département ou région
  - Code postal
  - Pays ou région
    
## <a name="2-directory-object-and-attribute-preparation"></a>2. préparation de l’objet et des attributs de l’annuaire

La réussite de la synchronisation d’annuaires entre vos services de domaine Active Directory et Office 365 nécessite que vos attributs AD DS soient correctement préparés. Par exemple, vous devez vous assurer que des caractères spécifiques ne sont pas utilisés dans certains attributs synchronisés avec l’environnement Office 365. Les caractères inattendus ne provoquent pas l’échec de la synchronisation d’annuaires, mais peuvent renvoyer un avertissement. Les caractères non valides entraînent l’échec de la synchronisation d’annuaires.
  
La synchronisation d’annuaires échoue également si certains de vos utilisateurs AD DS possèdent un ou plusieurs attributs en double. Chaque utilisateur doit avoir des attributs uniques.
  
Les attributs que vous devez préparer sont répertoriés ici :
  
- **displayName**
    
  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365.
  - Si cet attribut existe dans l’objet User, il doit y avoir une valeur pour lui. Autrement dit, l’attribut ne doit pas être vide.
  - Nombre maximal de caractères : 256
    
- **givenName**
    
  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 ne l’exige pas ou ne l’utilise pas.
  - Nombre maximal de caractères : 64
    
- **e-mails**
    
  - La valeur de l’attribut doit être unique dans l’annuaire.
    
    > [!NOTE]
    > S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé. Les utilisateurs suivants n’apparaîtront pas dans Office 365. Vous devez modifier la valeur dans Office 365 ou modifier les deux valeurs dans AD DS afin que les deux utilisateurs apparaissent dans Office 365. 
  
- **mailnickname** (alias Exchange) 
    
  - La valeur de l’attribut ne peut pas commencer par un point (.).
  - La valeur de l’attribut doit être unique dans l’annuaire.
  
    > [!NOTE]
    > Les traits de soulignement (« _ ») dans le nom synchronisé indiquent que la valeur d’origine de cet attribut contient des caractères non valides. La valeur d’origine peut contenir des lettres, des chiffres et les caractères !, #, $,%, &, \*',, +,-,/, =, ?, ^, _, ', {, |,} et ~. Pour plus d’informations sur cet attribut, consultez la rubrique [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).
    >
      
- **proxyAddresses**
    
  - Attribut à valeurs multiples
  - Nombre maximal de caractères par valeur : 256
  - La valeur de l’attribut ne doit pas contenir d’espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides : \< \> (); , [ ] " '
    
    Notez que les caractères non valides s’appliquent aux caractères qui suivent le délimiteur de type et à «  : », ce qui signifie que SMTP :User@contso.com est autorisé, mais SMTP :user :M@contoso.com ne l’est pas.
    
    > [!IMPORTANT]
    > Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique. S’il existe des adresses en double ou indésirables, consultez la rubrique d’aide [suppression des adresses de proxy en double et indésirables dans Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Nombre maximal de caractère : 20
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides : [\ "|, \< \> / : + =;? \* ']
  - Si un utilisateur a un attribut **sAMAccountName** non valide mais qu’il dispose d’un attribut **userPrincipalName** valide, le compte d’utilisateur est créé dans Office 365. 
  - Si **sAMAccountName** et **userPrincipalName** sont tous deux incorrects, l’attribut **userPrincipalName** AD DS doit être mis à jour. 
    
- **sn** (nom) 
    
  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 ne l’exige pas ou ne l’utilise pas.
    
- **targetAddress**
    
    Il est nécessaire que l’attribut **TargetAddress** (par exemple, SMTP :Tom@contoso.com) qui est rempli pour l’utilisateur doit apparaître dans la lag Office 365. Dans les scénarios de migration de messagerie tiers, cela nécessite l’extension de schéma Office 365 pour les services de domaine Active Directory. L’extension de schéma Office 365 ajoutera également d’autres attributs utiles pour gérer les objets Office 365 qui sont renseignés à l’aide d’un outil de synchronisation d’annuaires à partir d’AD DS. Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution est ajouté. 
   
  - Nombre maximal de caractères : 256
  - La valeur de l’attribut ne doit pas contenir d’espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides \< \> : \ (); , [ ] "
  - Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.
    
- **userPrincipalName**
    
  - L’attribut **userPrincipalName** doit être au format de connexion de style Internet où le nom d’utilisateur est suivi par le signe arobase (@) et un nom de domaine : par exemple, user@contoso.com. Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.
  - Le nombre maximal de caractères pour l’attribut **userPrincipalName** est 113. Un nombre de caractères spécifique est autorisé avant et après le signe @, comme suit : 
  - Nombre maximal de caractères pour le nom d’utilisateur devant le signe arobase (@) : 64
  - Nombre maximal de caractères pour le nom de domaine qui suit le signe arobase (@) : 48
  - Caractères non valides : &amp; \* \% +/= ? { } | \< \> ( ) ; : , [ ] " '
  - Un tréma est également un caractère non valide.
  - Le caractère @ est requis dans chaque valeur **userPrincipalName** . 
  - Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName**. 
  - Le nom d’utilisateur ne peut pas se terminer par un point (.&amp;), une esperluette (), un espace ou un signe arobase (@).
  - Le nom d’utilisateur ne peut pas contenir d’espaces.
  - Les domaines routables doivent être utilisés ; par exemple, les domaines locaux ou internes ne peuvent pas être utilisés.
  - Unicode est converti en caractères de trait de soulignement.
  - **userPrincipalName** ne peut pas contenir de valeurs en double dans l’annuaire. 

Voir [Prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) pour utiliser l’outil IdFix pour identifier les erreurs dans les attributs de votre AD DS.
    
## <a name="3-prepare-the-userprincipalname-attribute"></a>3. préparer l’attribut userPrincipalName

Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation de se connecter à votre annuaire à l’aide de **sAMAccountName** ou de **userPrincipalName**. De même, les utilisateurs finaux peuvent se connecter à Office 365 à l’aide du nom d’utilisateur principal (UPN) de leur compte professionnel ou scolaire. La synchronisation d’annuaires tente de créer des utilisateurs dans Azure Active Directory à l’aide du même nom d’utilisateur principal qui se trouve dans votre AD DS. Le nom d’utilisateur principal est mis en forme comme une adresse de messagerie. 

Dans Office 365, le nom d’utilisateur principal est l’attribut par défaut utilisé pour générer l’adresse de messagerie. Il est facile d’obtenir le **userPrincipalName** (dans AD DS et dans Azure AD) et l’adresse de messagerie principale dans **proxyAddresses** définie sur différentes valeurs. Lorsqu’elles sont définies sur des valeurs différentes, les administrateurs et les utilisateurs finaux peuvent être confondus. 
  
Il est préférable d’aligner ces attributs afin de réduire la confusion. Pour répondre aux exigences de l’authentification unique avec les services ADFS (Active Directory Federation Services) 2,0, vous devez vous assurer que l’UPN dans Azure Active Directory et votre AD DS correspondent et utilise un espace de noms de domaine valide.
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Ajoutez un autre suffixe UPN à AD DS.

Vous devrez peut-être ajouter un autre suffixe UPN pour associer les informations d’identification d’entreprise de l’utilisateur à l’environnement Office 365. Un suffixe UPN est la partie d’un UPN située à droite du caractère @. Les UPN qui sont utilisés pour l’authentification unique peuvent contenir des lettres, des chiffres, des points, des traits d’unions et des traits de soulignement, mais aucun autre type de caractère.
  
Pour plus d’informations sur l’ajout d’un autre suffixe UPN à Active Directory, consultez la rubrique [préparer la synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a>5. faire correspondre l’UPN AD DS avec l’UPN Office 365

Si vous avez déjà configuré la synchronisation d’annuaires, il se peut que l’UPN de l’utilisateur pour Office 365 ne corresponde pas à l’UPN AD DS de l’utilisateur défini dans votre AD DS. Cela peut se produire lorsqu’un utilisateur obtient une licence avant la vérification du domaine. Pour résoudre ce problème, utilisez [PowerShell pour corriger le nom UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730) afin de mettre à jour l’UPN de l’utilisateur afin de s’assurer que l’upn Office 365 correspond au nom d’utilisateur et au domaine de l’entreprise. Si vous mettez à jour l’UPN dans AD DS et souhaitez le synchroniser avec l’identité Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Office 365 avant d’apporter les modifications dans AD DS. 
  
Découvrez également [Comment préparer un domaine non routable (par exemple, le domaine. local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md).


## <a name="next-steps"></a>Étapes suivantes

Consultez [la rubrique prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) pour vous aider à corriger les erreurs dans les attributs de votre AD DS avant la synchronisation d’annuaires.

Si vous avez corrigé toutes les erreurs d’attribut identifiées avec l’outil IdFix et que vous avez terminé les étapes 1 à 5 ci-dessus, voir [configurer la synchronisation d’annuaires](set-up-directory-synchronization.md).
