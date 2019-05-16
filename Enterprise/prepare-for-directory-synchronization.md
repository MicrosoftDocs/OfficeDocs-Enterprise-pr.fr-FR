---
title: Préparer l’attribution des utilisateurs via la synchronisation d’annuaires dans Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
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
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071030"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Préparer l’attribution des utilisateurs via la synchronisation d’annuaires dans Office 365

La mise en service des utilisateurs à l’aide de la synchronisation d’annuaires nécessite une planification et une préparation supérieures à la simple gestion de votre compte professionnel ou scolaire directement dans Office 365. Les tâches de planification et de préparation supplémentaires sont nécessaires pour s’assurer que votre annuaire Active Directory local se synchronise correctement avec Azure Active Directory. Les avantages de votre organisation sont les suivants:
  
- Réduction des programmes d’administration au sein de votre organisation
- Activer le scénario d’authentification unique (facultatif)
- Automatisation des modifications de compte dans Office 365
    
Pour plus d’informations sur les avantages liés à l’utilisation de la synchronisation d’annuaires, voir feuille de [route de synchronisation]( https://go.microsoft.com/fwlink/p/?LinkId=525398) d’annuaires et présentation de l' [identité Office 365 et d’Azure Active Directory](about-office-365-identity.md).
  
Pour déterminer le scénario le mieux adapté à votre organisation, consultez la [comparaison des outils d’intégration d’annuaire](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Tâches de nettoyage d’annuaire

Avant de commencer la synchronisation de votre annuaire, vous devez nettoyer votre répertoire.
  
Vérifiez également les [attributs synchronisés avec Azure Active Directory par Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Si vous n’effectuez pas de nettoyage d’annuaire avant de procéder à la synchronisation, le processus de déploiement peut avoir un impact significatif. Cela peut prendre des jours, voire des semaines, pour parcourir le cycle de synchronisation d’annuaires, l’identification des erreurs et la resynchronisation. 
  
Dans votre annuaire local, effectuez les tâches de nettoyage suivantes:
  
1. Assurez-vous que chaque utilisateur qui sera affecté aux offres de service Office 365 dispose d’une adresse de messagerie unique et valide dans l’attribut **proxyAddresses** . 
    
2. Supprimez toutes les valeurs en double dans l’attribut **proxyAddresses** . 
    
3.  Si possible, assurez-vous que chaque utilisateur qui sera affecté aux offres de service Office 365 a une valeur valide et unique pour l’attribut **userPrincipalName** dans l’objet **utilisateur** de l’utilisateur. Pour optimiser l’expérience de synchronisation, vérifiez que l’UPN Active Directory local correspond à l’UPN Cloud. Si un utilisateur n’a pas de valeur pour l’attribut **userPrincipalName** , l’objet **User** doit contenir une valeur valide et unique pour l’attribut **sAMAccountName** . Supprimez toutes les valeurs en double dans l’attribut **userPrincipalName** . 
    
4. Pour une utilisation optimale de la liste d’adresses globale (LAG), assurez-vous que les informations contenues dans les attributs suivants sont correctes:
    
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
    
## <a name="directory-object-and-attribute-preparation"></a>Préparation de l’objet d’annuaire et de l’attribut

La réussite de la synchronisation d’annuaires entre votre répertoire local et Office 365 nécessite que vos attributs d’annuaire locaux soient correctement préparés. Par exemple, vous devez vous assurer que des caractères spécifiques ne sont pas utilisés dans certains attributs synchronisés avec l’environnement Office 365. Les caractères inattendus ne provoquent pas l’échec de la synchronisation d’annuaires, mais peuvent renvoyer un avertissement. Les caractères non valides entraînent l’échec de la synchronisation d’annuaires.
  
La synchronisation d’annuaires échoue également si certains de vos utilisateurs Active Directory disposent d’un ou plusieurs attributs en double. Chaque utilisateur doit avoir des attributs uniques.
  
Les attributs que vous devez préparer sont répertoriés ici:
  
 **Remarque:** Vous pouvez également utiliser l' [outil IdFix](install-and-run-idfix.md) pour simplifier ce processus. 
  
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
    > S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé. Les utilisateurs suivants n’apparaîtront pas dans Office 365. Vous devez modifier la valeur dans Office 365 ou modifier les deux valeurs dans l’annuaire local afin que les deux utilisateurs apparaissent dans Office 365. 
  
- **mailnickname** (Alias Exchange) 
    
  - La valeur de l’attribut ne peut pas commencer par un point (.).
  - La valeur de l’attribut doit être unique dans l’annuaire.
    
- **proxyAddresses**
    
  - Attribut à valeurs multiples
  - Nombre maximal de caractères par valeur: 256
  - La valeur de l’attribut ne doit pas contenir d’espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides: \< \> (); , [ ] "
    
    Notez que les caractères non valides s’appliquent aux caractères qui suivent le délimiteur de type et à «:», ce qui signifie que SMTP:User@contso.com est autorisé, mais SMTP:user:M@contoso.com ne l’est pas.
    
    > [!IMPORTANT]
    > Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique. S’il existe des adresses en double ou indésirables, consultez la rubrique d’aide [suppression des adresses de proxy en double et indésirables dans Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Nombre maximal de caractère : 20
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides: [\ "|, \< \> /: + =;? \* ]
  - Si un utilisateur a un attribut **sAMAccountName** non valide mais qu’il dispose d’un attribut **userPrincipalName** valide, le compte d’utilisateur est créé dans Office 365. 
  - Si **sAMAccountName** et **userPrincipalName** sont tous deux incorrects, l’attribut **userPrincipalName** Active Directory local doit être mis à jour. 
    
- **sn** Surname 
    
  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 ne l’exige pas ou ne l’utilise pas.
    
- **targetAddress**
    
    Il est nécessaire que l’attribut **TargetAddress** (par exemple, SMTP:Tom@contoso.com) qui est rempli pour l’utilisateur doit apparaître dans la lag Office 365. Dans les scénarios de migration de messagerie tiers, cela nécessite l’extension de schéma Office 365 pour l’annuaire local. L’extension de schéma Office 365 ajoute également d’autres attributs utiles pour gérer les objets Office 365 qui sont renseignés à l’aide d’un outil de synchronisation d’annuaires à partir de l’annuaire local. Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution est ajouté. 
   
  - Nombre maximal de caractères : 256
  - La valeur de l’attribut ne doit pas contenir d’espace.
  - La valeur de l’attribut doit être unique dans l’annuaire.
  - Caractères non valides \< \> : \ (); , [ ] "
  - Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.
    
- **userPrincipalName**
    
  - L’attribut **userPrincipalName** doit être au format de connexion de style Internet où le nom d’utilisateur est suivi par le signe arobase (@) et un nom de domaine: par exemple, user@contoso.com. Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.
  - Le nombre maximal de caractères pour l’attribut **userPrincipalName** est 113. Un nombre de caractères spécifique est autorisé avant et après le signe @, comme suit: 
  - Nombre maximum de caractères pour le nom d’utilisateur devant le caractère arrobase (@) : 64
  - Nombre maximal de caractères pour le nom de domaine qui suit le signe arobase (@): 48
  - Caractères non valides: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "
  - Un tréma est également un caractère non valide.
  - Le caractère @ est requis dans chaque valeur **userPrincipalName** . 
  - Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName**. 
  - Le nom d’utilisateur ne peut pas se terminer par un point (.)&amp;, une esperluette (), un espace ou un signe arobase (@).
  - Le nom d’utilisateur ne peut pas contenir d’espaces.
  - Les domaines routables doivent être utilisés; par exemple, les domaines locaux ou internes ne peuvent pas être utilisés.
  - Unicode est converti en caractères de trait de soulignement.
  - **userPrincipalName** ne peut pas contenir de valeurs en double dans l’annuaire. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Préparation de l’attribut userPrincipalName

Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation de se connecter à votre annuaire à l’aide de **sAMAccountName** ou de **userPrincipalName**. De même, les utilisateurs finaux peuvent se connecter à Office 365 à l’aide du nom d’utilisateur principal (UPN) de leur compte professionnel ou scolaire. La synchronisation d’annuaires tente de créer des utilisateurs dans Azure Active Directory à l’aide du même nom d’utilisateur principal qui se trouve dans votre annuaire local. Le nom d’utilisateur principal est mis en forme comme une adresse de messagerie. 

Dans Office 365, le nom d’utilisateur principal est l’attribut par défaut utilisé pour générer l’adresse de messagerie. Il est facile d’obtenir la valeur **userPrincipalName** (sur site et dans Azure Active Directory) et l’adresse de messagerie principale dans **proxyAddresses** est définie sur des valeurs différentes. Lorsqu’elles sont définies sur des valeurs différentes, les administrateurs et les utilisateurs finaux peuvent être confondus. 
  
Il est préférable d’aligner ces attributs afin de réduire la confusion. Pour répondre aux exigences de l’authentification unique avec les services ADFS (Active Directory Federation Services) 2,0, vous devez vous assurer que l’UPN dans Azure Active Directory et votre annuaire Active Directory local correspondent et qu’ils utilisent un espace de noms de domaine valide.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Ajouter un autre suffixe UPN à AD DS

Vous devrez peut-être ajouter un autre suffixe UPN pour associer les informations d’identification d’entreprise de l’utilisateur à l’environnement Office 365. Un suffixe UPN est la partie d’un UPN située à droite du caractère @. Les UPN qui sont utilisés pour l’authentification unique peuvent contenir des lettres, des chiffres, des points, des traits d’unions et des traits de soulignement, mais aucun autre type de caractère.
  
Pour plus d’informations sur l’ajout d’un autre suffixe UPN à Active Directory, consultez la rubrique [préparer la synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Faire correspondre l’UPN local au nom UPN Office 365

Si vous avez déjà configuré la synchronisation d’annuaires, il se peut que l’UPN de l’utilisateur pour Office 365 ne corresponde pas à l’UPN local de l’utilisateur défini dans votre service d’annuaire local. Cela peut se produire lorsqu’un utilisateur obtient une licence avant la vérification du domaine. Pour résoudre ce problème, utilisez [PowerShell pour corriger le nom UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730) afin de mettre à jour l’UPN de l’utilisateur afin de s’assurer que l’upn Office 365 correspond au nom d’utilisateur et au domaine de l’entreprise. Si vous mettez à jour l’UPN dans le service d’annuaire local et souhaitez le synchroniser avec l’identité Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Office 365 avant d’effectuer les modifications en local. 
  
Voir aussi [Comment préparer un domaine non routable (tel que le domaine. local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Outils d’intégration d’annuaire

La synchronisation d’annuaires est la synchronisation des objets d’annuaire (utilisateurs, groupes et contacts) à partir de votre environnement Active Directory local vers l’infrastructure d’annuaire Office 365, Azure Active Directory. Consultez la rubrique [Outils d’intégration d’annuaire](https://go.microsoft.com/fwlink/p/?LinkID=510956) pour obtenir la liste des outils disponibles et leur fonctionnalité. L’outil recommandé est [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Pour plus d’informations sur Azure Active Directory Connect, reportez-vous à [la rubrique intégration de vos identités locales à Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Lorsque les comptes d’utilisateur sont synchronisés avec le répertoire Office 365 pour la première fois, ils sont marqués comme non activés. Ils ne peuvent pas envoyer ou recevoir des courriers électroniques, et ils ne consomment pas de licences d’abonnement. Lorsque vous êtes prêt à attribuer des abonnements Office 365 à des utilisateurs spécifiques, vous devez les sélectionner et les activer en [attribuant des licences aux utilisateurs dans Office 365 pour les entreprises](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
Vous pouvez également utiliser [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) pour attribuer des licences. Découvrez [comment utiliser PowerShell pour attribuer automatiquement des licences à vos utilisateurs Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) pour une solution automatisée.