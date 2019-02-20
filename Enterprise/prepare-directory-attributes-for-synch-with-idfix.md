---
title: Préparation des attributs d'annuaire pour la synchronisation avec Office 365 à l'aide de l'outil IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Fournit des instructions sur l'utilisation de IdFix pour préparer et nettoyer votre annuaire local avant la synchronisation avec Office 365.
ms.openlocfilehash: cdfee8178f731d20c799f550d1dacb0a04a72cae
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085093"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Préparation des attributs d'annuaire pour la synchronisation avec Office 365 à l'aide de l'outil IdFix
Cette rubrique contient des instructions détaillées sur l'exécution de l'outil IdFix, des erreurs courantes que vous pouvez rencontrer, des corrections suggérées, des exemples et des pratiques recommandées pour la procédure à suivre si vous avez un grand nombre d'erreurs.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correction des erreurs dans votre annuaire à l'aide de l'interface utilisateur graphique d'IdFix
[Exécutez l'outil IdFix Office 365](install-and-run-idfix.md) pour rechercher des problèmes dans votre répertoire, puis corrigez les erreurs dans l'interface utilisateur, comme décrit dans cette rubrique. Si une table vide est renvoyée par l'outil, aucune erreur n'a été détectée. Si votre annuaire présente de nombreux problèmes, il peut être écrasant lorsque l'outil renvoie les erreurs. Pour résoudre ce problème, vous pouvez corriger toutes les erreurs d'un type, puis passer au type suivant. 
  
1. Avant de commencer à apporter des modifications, examinons les recommandations présentées par IdFix.
    
2. Passez en revue la liste des erreurs renvoyée par IdFix. Vous pouvez trier les erreurs par type d'erreur en cliquant sur **ERREUR** en haut de la colonne qui répertorie les types d'erreur. Si plusieurs erreurs sont associées à un attribut unique, les erreurs sont combinées sur une seule ligne. Si possible, IdFix présente une recommandation pour un correctif dans la colonne **METTRE À JOUR**. Le correctif est basé sur une vérification des autres attributs associés à un objet. Ceux-ci sont généralement meilleurs que ce qui est déjà dans l'annuaire, mais vous êtes la seule personne à pouvoir décider de ce qui est vraiment pertinent. 
    
3. Si IdFix a une suggestion de correctif pour une erreur de duplication, le correctif est identifié par l'un des trois indicateurs au début de la valeur dans la colonne **Update** , par exemple `[E]john.doe@contoso.com`. Si vous acceptez la suggestion, lorsque vous appliquez la modification, l'indicateur n'est pas inséré dans le répertoire. Seule la valeur suivant l'indicateur de suggestion sera appliquée, par exemple, `john.doe@contoso.com`. Si vous souhaitez accepter la suggestion, sélectionnez l'action correspondante dans la colonne **action** . Les indicateurs indiquent les actions suivantes: 
    
 - **[C]** Action suggérée **TERMINER**. La valeur n'a pas besoin d'être modifiée.
    
 - **[E]** Action suggérée **MODIFIER**. La valeur doit être modifiée pour éviter un conflit avec une autre valeur dans l'annuaire.
    
 - **[R]** Action suggérée **SUPPRIMER**. La valeur est un proxy SMTP sur un objet non-mail et peut probablement être supprimée en toute sécurité.
    
4. Une fois que vous avez lu et compris les erreurs, mettez à jour l'entrée dans la colonne **mise à jour** avec vos modifications, puis, dans la colonne **action** , sélectionnez les actions que doit effectuer IdFix pour implémenter la modification. Par exemple, deux utilisateurs peuvent avoir `proxyAddress` identifié comme doublon. Un seul utilisateur peut utiliser le `proxyAddress` pour la remise du courrier. Pour résoudre ce problème, marquez la colonne **action** comme étant **terminée** pour l'utilisateur avec la valeur correcte, puis sélectionnez la colonne **action** **supprimer** pour l'autre utilisateur. Cette opération supprime `proxyAddress` l'attribut de l'utilisateur auquel elle `proxyAddress` n'appartient pas et n'apporte aucune modification à l'utilisateur pour lequel `proxyAddress` cela est correct.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Erreurs courantes et correctifs détectés par IdFix
Le tableau suivant décrit les erreurs qui sont détectées par IdFix, fournit les correctifs les plus fréquemment recommandés par l'outil et, dans certains cas, donne des exemples concernant la façon de les corriger.

|**«**|**Description du type d'erreur**|**Correctif suggéré**|**Exemple**|
|:-----|:-----|:-----|:-----|
|**caractère** | Caractères non valides. La valeur contient un caractère qui n'est pas valide. | Le correctif suggéré pour l'erreur indiquée dans la colonne **METTRE À JOUR** indique la valeur avec le caractère non valide supprimé.  <br/> | Un espace de fin à la fin d'une adresse de messagerie valide est un caractère illégal, par exemple:  <br/> " `user@contoso.com` "  <br/> Un espace de début à la fin d'une adresse de messagerie valide est un caractère illégal, par exemple:  <br/> " ` user@contoso.com `"  <br/>  Le `ú` caractère est un caractère non valide. |
|**doublon** | Entrée en double. La valeur a un doublon dans la recherche. Toutes les valeurs en double seront affichées comme des erreurs. | Modifiez ou supprimez des valeurs pour éliminer les doublons. L'outil ne fournit pas de solution pour les doublons. Vous devez choisir lequel des deux doublons est correct et supprimer les entrées en double. ||
|**format** | Erreur de mise en forme. La valeur n'est pas conforme aux exigences de format pour l'utilisation de l'attribut. | La mise à jour suggérée affichera la valeur avec tout caractère non valide supprimé. S'il n'y a aucun caractère non valide, les colonnes Mettre à jour et Valeur sont identiques. Vous devez déterminer les éléments que vous souhaitez dans la colonne Mettre à jour. L'outil ne suggère pas de solution pour toutes les erreurs de mise en forme. | Par exemple, les adresses SMTP doivent être conformes à la norme RFC 2822 et la fonction mailNickName ne peut pas commencer ou se terminer par un point. Pour plus d'informations sur les exigences de format pour les attributs d'annuaire, voir «préparation de l'objet et des attributs d'annuaire» dans [Prepare to provision Users with Directory Synchronization to Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domaine de niveau supérieur. Cela s'applique aux valeurs soumises à la mise en forme [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Si le domaine de niveau supérieur n'est pas routable sur Internet, il est identifié comme une erreur. Par exemple, une adresse SMTP se terminant par. local n'est pas routable sur Internet et provoque cette erreur. |Remplacez la valeur par un domaine routable sur Internet tel `.com` que `.net`ou. | `myaddress@fourthcoffee.local` Basculez `fourthcoffee.com` vers ou un autre domaine routable sur Internet.  <br/> Pour obtenir des instructions, consultez [la rubrique How to prepare a non routable Domain (par exemple, le domaine. local) pour la synchronisation d'annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Erreur de partie domaine. Cela s'applique aux valeurs soumises au formatage RFC 2822. Si la partie domaine de la valeur n'est pas valide ni conforme à la norme RFC 2822, cette erreur est renvoyée. | Remplacez la valeur par celle qui est conforme à la norme RFC 2822. Par exemple, assurez-vous qu'il ne contient pas d'espaces ni de caractères illégaux. | Remplacez `myaddress@fourth coffee.com` par `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Erreur de partie locale. Cela s'applique aux valeurs soumises au formatage RFC 2822. Si la partie locale de la valeur n'est pas valide ni conforme à la norme RFC 2822, cette erreur est renvoyée. |Remplacez la valeur par celle qui est conforme à la norme RFC 2822. Par exemple, assurez-vous qu'il ne contient pas d'espaces ni de caractères illégaux. |Remplacez `my"work"address@fourthcoffee.com` par `myworkaddress@fourthcoffee.com`. |
|**longueur** | Erreur de longueur. La valeur n'est pas conforme à la limite de longueur de l'attribut. Cela est courant lorsque le schéma d'annuaire a été modifié.  | La mise à jour suggérée par IdFix tronquera la valeur à la longueur acceptable.  <br/> Sachez que cela peut produire des résultats imprévus. Vous devez examiner le correctif suggéré et le modifier si nécessaire avant de cliquer sur **Appliquer**. ||
|**vide**  | Erreur vide ou null. La valeur n'est pas conforme à la restriction null pour les attributs à synchroniser. Seuls quelques attributs doivent contenir une valeur. | Si possible, la mise à jour suggérée s'appuiera sur d'autres valeurs d'attributs pour générer un substitut probable. ||
|**mailmatch** | Cela s'applique uniquement à Office 365 dédié. La valeur ne correspond pas à l'attribut de messagerie. | La mise à jour suggérée sera la valeur d'attribut de messagerie avec le préfixe «SMTP:». ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Opérations que vous pouvez effectuer à l'aide d'IdFix
Pour corriger une erreur, sélectionnez une option dans la liste déroulante **action** . Le tableau suivant décrit les **actions** que vous pouvez effectuer sur les attributs à l'aide de l'outil IdFix. Si vous laissez la colonne **action** vide, l'outil IdFix n'effectuera aucune action sur cette erreur spécifique dans l'annuaire. 

|**TRANSACTIONNELLE**|**Description de l'action**|**Exemple**|
|:-----|:-----|:-----|
|**TERMINER** | La valeur d'origine est acceptable et ne doit pas être changée même si elle est identifiée comme une erreur. | Deux utilisateurs ont une proxyAddress identifiée comme doublon. Un seul peut utiliser la valeur pour la remise du courrier. Marquez l'utilisateur avec la valeur correcte en tant que **TERMINER**. |
|**INSTALLATION** | La valeur de l'attribut sera supprimée de l'objet source. Dans le cas d'un attribut à valeurs multiples, par exemple `proxyAddresses`, seule la valeur individuelle affichée sera supprimée. | Deux utilisateurs ont une proxyAddress identifiée comme doublon. Une seule peut utiliser la valeur pour la remise du courrier. Marquez l'utilisateur avec la valeur en double en tant que **SUPPRIMER**. |
|**ÉDITION** | Les informations contenues dans la colonne **mettre à jour** seront utilisées pour modifier la valeur de l'attribut. Si une valeur de **mise à jour** valide a été suggérée par IdFix, puis à partir de la colonne **action** , sélectionnez **modifier** , puis passez à l'erreur suivante. Si vous n'aimez pas la suggestion, tapez-en une nouvelle dans la colonne **mettre à jour** , puis, dans la colonne **action** , sélectionnez **modifier**. ||
|**RÉTABLIR** | Cette option n’est disponible que si l’utilisateur a effectué une restauration à partir d’un journal de transactions. Si vous sélectionnez **ANNULER**, la valeur initiale de l’attribut est rétablie. ||
|**FAIL** | Cette valeur est renvoyée uniquement si une valeur de **mise à jour** a un conflit inconnu avec les règles AD DS. Dans ce cas, vous pouvez modifier de nouveau la valeur de la colonne de **mise à jour** si vous connaissez la cause de l'échec. Il peut être nécessaire d'analyser les valeurs de l'objet à l'aide d'ADSI Edit. Pour plus d'informations, consultez la rubrique [ADSI Edit (adsiedit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Après avoir choisi une **ACTION** pour une erreur ou un lot d'erreurs, cliquez sur **Appliquer**. Lorsque vous cliquez sur **Appliquer**, l'outil effectue les modifications dans l'annuaire. Vous pouvez corriger plusieurs erreurs avant de cliquer sur **Appliquer** et IdFix les modifie toutes simultanément.

RéExécutez IdFix pour vous assurer que les corrections que vous avez apportées n'ont pas introduit de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est recommandé de suivre le processus quelques fois avant de procéder à la synchronisation.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Modification du jeu de règles utilisé par IdFix
Par défaut, IdFix utilise l'ensemble de règles mutualisée pour tester les entrées de votre répertoire. Il s'agit de l'ensemble de règles approprié pour la plupart des clients Office 365 = clients. Toutefois, si vous êtes un client Office 365 dédié ou ITAR (trafic international dans les réglementations sur les armes), vous pouvez configurer IdFix pour qu'il utilise le jeu de règles dédié à la place. Si vous n'êtes pas sûr de votre type de client, vous pouvez en toute sécurité ignorer cette étape. Pour définir le jeu de règles sur dédié, cliquez sur l'icône d'engrenage dans la barre de menus, puis cliquez sur **dédié**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Modification de l'étendue de la recherche utilisée par IdFix
Par défaut, IdFix effectue des recherches dans l'intégralité de l'annuaire. Si vous le souhaitez, vous pouvez configurer l'outil pour qu'il effectue une recherche dans une sous-arborescence spécifique. Pour ce faire, dans la barre de menu, cliquez sur l'icône de filtre et indiquez une sous-arborescence valide.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Restauration de vos modifications à l'aide de l'interface utilisateur graphique d'IdFix
Chaque fois que vous cliquez sur **appliquer** pour appliquer les modifications, l'outil IdFix crée un fichier distinct, appelé journal des transactions, qui répertorie les modifications que vous venez d'effectuer. Vous pouvez utiliser le journal des transactions pour restaurer uniquement les modifications qui se trouvent dans le journal le plus récent en cas d'erreur. Si vous avez commis une erreur lors de la mise à jour, vous pouvez annuler les dernières modifications appliquées en cliquant sur **Annuler**. Lorsque vous cliquez sur **Annuler**, IdFix utilise le journal des transactions pour annuler uniquement les modifications qui se trouvent dans le journal des transactions le plus récent. Pour plus d'informations sur l'utilisation du journal des transactions, voir [Reference: Office 365 IdFix transaction log](idfix-transaction-log.md).