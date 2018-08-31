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
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Fournit des instructions sur l’utilisation d’IdFix pour préparer et nettoyer votre annuaire local avant la synchronisation avec Office 365.
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540580"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Préparation des attributs d'annuaire pour la synchronisation avec Office 365 à l'aide de l'outil IdFix
Cette rubrique contient des instructions détaillées sur l’exécution de l’outil IdFix, vous pouvez rencontrer, les erreurs fréquentes suggérés correctifs, des exemples et des meilleures pratiques pour que faire si vous avez un grand nombre d’erreurs.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correction des erreurs dans votre annuaire à l'aide de l'interface utilisateur graphique d'IdFix
[Exécutez l’outil IdFix d’Office 365](install-and-run-idfix.md) pour rechercher les problèmes dans votre répertoire et résoudre les erreurs dans l’interface utilisateur comme décrit dans cette rubrique. Si un tableau vide est renvoyé par l’outil, aucune erreur ont été découverts. S’il existe un grand nombre de problèmes dans votre annuaire, il peut être une lourde lorsque l’outil renvoie les erreurs. Une manière d’effectuer ce changement consiste à corriger toutes les erreurs d’un type de tout d’abord, puis passez au type immédiatement. 
  
1. Avant de commencer à apporter des modifications, examinons les recommandations présentées par IdFix.
    
2. Passez en revue la liste des erreurs renvoyée par IdFix. Vous pouvez trier les erreurs par type d'erreur en cliquant sur **ERREUR** en haut de la colonne qui répertorie les types d'erreur. Si plusieurs erreurs sont associées à un attribut unique, les erreurs sont combinées sur une seule ligne. Si possible, IdFix présente une recommandation pour un correctif dans la colonne **METTRE À JOUR**. Le correctif est basé sur une vérification des autres attributs associés à un objet. Ceux-ci sont généralement meilleurs que ce qui est déjà dans l'annuaire, mais vous êtes la seule personne à pouvoir décider de ce qui est vraiment pertinent. 
    
3. Si IdFix a une suggestion pour un correctif pour une erreur de duplication, le correctif est identifié par un des trois indicateurs au début de la valeur dans la colonne de la **mise à jour** , par exemple, `[E]john.doe@contoso.com`. Si vous acceptez la proposition, lorsque vous appliquez la modification de que l’indicateur ne sera insérée dans le répertoire. Seule la valeur suivant la suggestion indicateur sera appliqué, par exemple, `john.doe@contoso.com`. Si vous souhaitez accepter la suggestion, sélectionnez l’action correspondante dans la colonne **ACTION** . Les indicateurs indiquent les actions comme suit : 
    
 - **[C]** Action suggérée **TERMINER**. La valeur n'a pas besoin d'être modifiée.
    
 - **[E]** Action suggérée **MODIFIER**. La valeur doit être modifiée pour éviter un conflit avec une autre valeur dans l'annuaire.
    
 - **[R]** Action suggérée **SUPPRIMER**. La valeur est un proxy SMTP sur un objet non-mail et peut probablement être supprimée en toute sécurité.
    
4. Une fois que vous avez lu et compris les erreurs, mettre à jour de l’entrée dans la colonne **mettre à jour** avec vos modifications, puis dans l' **ACTION** colonne Sélectionnez ce que vous voulez IdFix à suivre pour implémenter la modification. Par exemple, deux utilisateurs peuvent avoir un `proxyAddress` identifiés comme en double. Seul un utilisateur peut utiliser le `proxyAddress` pour remise de messages. Pour résoudre ce problème, sélectionnez la colonne **ACTION** **complète** pour l’utilisateur avec la valeur correcte et marquer la colonne **ACTION** **Supprimer** l’autre utilisateur. Cette commande supprime la `proxyAddress` attribut à partir de l’utilisateur auquel cette `proxyAddress` n’appartient pas et aucune modification à l’utilisateur pour lequel ce `proxyAddress` est correct.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Erreurs courantes et correctifs détectés par IdFix
Le tableau suivant décrit les erreurs qui sont détectées par IdFix, fournit les correctifs les plus fréquemment recommandés par l'outil et, dans certains cas, donne des exemples concernant la façon de les corriger.

|**ERREUR**|**Description du type d'erreur**|**Correctif suggéré**|**Exemple**|
|:-----|:-----|:-----|:-----|
|**caractère** | Caractères non valides. La valeur contient un caractère qui n'est pas valide. | Le correctif suggéré pour l'erreur indiquée dans la colonne **METTRE À JOUR** indique la valeur avec le caractère non valide supprimé.  <br/> | Un espace de fin à la fin d’une adresse de messagerie valide est un caractère non autorisé, par exemple :  <br/> " `user@contoso.com` "  <br/> Un espace de début au début d’une adresse de messagerie valide est un caractère non autorisé, par exemple :  <br/> " ` user@contoso.com `"  <br/>  Le `ú` caractère est un caractère non autorisé. |
|**doublon** | Entrée en double. La valeur a un doublon dans la recherche. Toutes les valeurs en double seront affichées comme des erreurs. | Modifiez ou supprimez des valeurs pour éliminer les doublons. L'outil ne fournit pas de solution pour les doublons. Vous devez choisir lequel des deux doublons est correct et supprimer les entrées en double. ||
|**format** | Erreur de mise en forme. La valeur n'est pas conforme aux exigences de format pour l'utilisation de l'attribut. | La mise à jour suggérée affichera la valeur avec tout caractère non valide supprimé. S'il n'y a aucun caractère non valide, les colonnes Mettre à jour et Valeur sont identiques. Vous devez déterminer les éléments que vous souhaitez dans la colonne Mettre à jour. L'outil ne suggère pas de solution pour toutes les erreurs de mise en forme. | Par exemple les adresses SMTP doivent être conformes à RFC 2822 et mailNickName ne peut pas commencer ou se terminer par un point. Pour plus d’informations sur le format requis pour les attributs d’annuaire, voir « Préparation Directory objet et attribut » dans [Prepare to provision utilisateurs par le biais de la synchronisation d’annuaires vers Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domaine de niveau supérieur. Cela s’applique aux valeurs soumis à la mise en forme de [la norme RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Si le domaine de niveau supérieur n’est pas routable internet ce sera identifié comme une erreur. Par exemple, une adresse SMTP se terminant par .local n’est pas routable internet et cette erreur. |Modifiez la valeur pour un domaine routable par internet tel que `.com` ou `.net`. | Modification `myaddress@fourthcoffee.local` à `fourthcoffee.com` ou un autre domaine routable par internet.  <br/> Pour plus d’informations, voir [comment préparer un domaine non routable (par exemple, domaine .local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Erreur de partie domaine. Cela s'applique aux valeurs soumises au formatage RFC 2822. Si la partie domaine de la valeur n'est pas valide ni conforme à la norme RFC 2822, cette erreur est renvoyée. | Modifiez la valeur pour qu’il est conforme à la norme RFC 2822. Par exemple, assurez-vous qu’il ne contient pas les espaces ou les caractères non autorisés. | Modification `myaddress@fourth coffee.com` à `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Erreur de partie locale. Cela s'applique aux valeurs soumises au formatage RFC 2822. Si la partie locale de la valeur n'est pas valide ni conforme à la norme RFC 2822, cette erreur est renvoyée. |Modifiez la valeur pour qu’il est conforme à la norme RFC 2822. Par exemple, assurez-vous qu’il ne contient pas les espaces ou les caractères non autorisés. |Modification `my"work"address@fourthcoffee.com` à `myworkaddress@fourthcoffee.com`. |
|**longueur** | Erreur de longueur. La valeur n'est pas conforme à la limite de longueur de l'attribut. Cela est courant lorsque le schéma d'annuaire a été modifié.  | La mise à jour suggérée par IdFix tronquera la valeur à la longueur acceptable.  <br/> Sachez que cela peut produire des résultats imprévus. Vous devez examiner le correctif suggéré et le modifier si nécessaire avant de cliquer sur **Appliquer**. ||
|**vide**  | Erreur vide ou null. La valeur n'est pas conforme à la restriction null pour les attributs à synchroniser. Seuls quelques attributs doivent contenir une valeur. | Si possible, la mise à jour suggérée s'appuiera sur d'autres valeurs d'attributs pour générer un substitut probable. ||
|**mailmatch** | Cela s’applique à Office 365 dédiée uniquement. La valeur ne correspond pas à l’attribut mail. | La mise à jour suggérée sera la valeur d’attribut de messagerie par le préfixe « SMTP : ». ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Opérations que vous pouvez effectuer à l'aide d'IdFix
Pour corriger une erreur, vous sélectionnez une option dans la liste déroulante **ACTION** . Le tableau suivant décrit les opérations de **l’ACTION** que vous pouvez effectuer sur les attributs à l’aide de l’outil IdFix. Si vous laissez la colonne **ACTION** vide, l’outil IdFix prendra pas n’importe quelle action sur cette erreur spécifique dans le répertoire. 

|**ACTION**|**Description de l'action**|**Exemple**|
|:-----|:-----|:-----|
|**TERMINER** | La valeur d'origine est acceptable et ne doit pas être changée même si elle est identifiée comme une erreur. | Deux utilisateurs ont une proxyAddress identifiée comme doublon. Un seul peut utiliser la valeur pour la remise du courrier. Marquez l'utilisateur avec la valeur correcte en tant que **TERMINER**. |
|**SUPPRIMER** | La valeur d’attribut sera supprimée de l’objet source. Dans le cas d’un attribut à valeurs multiples, par exemple, `proxyAddresses`, seule la valeur individuelle indiquée sera supprimée. | Deux utilisateurs ont une proxyAddress identifiée comme doublon. Une seule peut utiliser la valeur pour la remise du courrier. Marquez l'utilisateur avec la valeur en double en tant que **SUPPRIMER**. |
|**MODIFIER** | Les informations contenues dans la colonne de la **mise à jour** permet de modifier la valeur d’attribut. Si une valeur valide de la **mise à jour** a été suggérée par IdFix, puis dans la colonne **ACTION** , sélectionnez **Modifier** et passer à l’erreur suivante. Si vous n’aimez pas la proposition, entrez une nouvelle valeur dans la colonne de la **mise à jour** et puis, dans la colonne **ACTION** sélectionnez **Modifier**. ||
|**ANNULER** | Cette option n’est disponible que si l’utilisateur a effectué une restauration à partir d’un journal de transactions. Si vous sélectionnez **ANNULER**, la valeur initiale de l’attribut est rétablie. ||
|**FAIL** | Cette valeur est renvoyée uniquement si une valeur de **mise à jour** a un conflit avec les règles de domaine Active Directory inconnu. Dans ce cas, vous pouvez modifier la valeur dans la colonne de la **mise à jour** à nouveau si vous connaissez l’échec. Il peut être nécessaire analyser les valeurs de l’objet à l’aide de l’éditeur ADSI. Pour plus d’informations, voir [ADSI Edit (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Après avoir choisi une **ACTION** pour une erreur ou un lot d'erreurs, cliquez sur **Appliquer**. Lorsque vous cliquez sur **Appliquer**, l'outil effectue les modifications dans l'annuaire. Vous pouvez corriger plusieurs erreurs avant de cliquer sur **Appliquer** et IdFix les modifie toutes simultanément.

Exécutez IdFix pour vous assurer que les correctifs que vous avez apportées n’a pas introduire de nouvelles erreurs. Vous pouvez répéter ces étapes autant de fois que nécessaire. Il est conseillé de suivre le processus de quelques heures avant la synchronisation.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Modification du jeu de règles utilisé par IdFix
Par défaut, IdFix utilise la règle multiclients à tester les entrées dans le répertoire. Il s’agit de la règle de droite définie pour la plupart des Office 365 = clients. Toutefois, si vous êtes un client ITAR (trafic International règlements armes) ou Office 365 dédiée, vous pouvez configurer IdFix pour utiliser la règle dédiée à la place. Si vous ne savez pas quel type de client vous êtes, vous pouvez ignorer cette étape. Pour définir l’ensemble de règles à dédié, cliquez sur l’icône représentant un engrenage dans la barre de menus, puis sur **dédié**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Modification de l'étendue de la recherche utilisée par IdFix
Par défaut, IdFix effectue des recherches dans l'intégralité de l'annuaire. Si vous le souhaitez, vous pouvez configurer l'outil pour qu'il effectue une recherche dans une sous-arborescence spécifique. Pour ce faire, dans la barre de menu, cliquez sur l'icône de filtre et indiquez une sous-arborescence valide.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Restauration de vos modifications à l'aide de l'interface utilisateur graphique d'IdFix
Chaque fois que vous cliquez sur **Appliquer** pour appliquer les modifications, l’outil IdFix crée un fichier distinct appelé un journal des transactions qui répertorie les modifications que vous venez de créer. Vous pouvez utiliser le journal des transactions à restaurer uniquement les modifications qui se trouvent dans le journal plus récent en cas d’erreur. Si vous faites une erreur pendant que vous mettez à jour, vous pouvez annuler les modifications appliquées le plus récemment en cliquant sur **Annuler**. Lorsque vous cliquez sur **Annuler**, IdFix utilise le journal des transactions à restaurer uniquement les modifications qui se trouvent dans le journal des transactions plus récent. Pour plus d’informations sur l’utilisation du journal des transactions, voir [référence : journal des transactions IdFix d’Office 365](idfix-transaction-log.md).