---
title: "Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne politique"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Résumé : Créer Office 365 et de mobilité d’entreprise + d’abonnements d’essai de sécurité (EMS) avec les utilisateurs et les groupes pour un environnement de développement/test de campagne politique."
ms.openlocfilehash: 25d03e0aa521c8fdbf20c2dc3ff2fc46e1aabe2f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne politique

 **Résumé :** Créer Office 365 et de mobilité d’entreprise + d’abonnements d’essai de sécurité (EMS) avec les utilisateurs et les groupes pour un environnement de développement/test de campagne politique.
  
Suivez les instructions de cet article pour créer un environnement de développement/test qui inclut les comptes d’utilisateur simplifiée et des groupes pour la solution de [Conseils de sécurité de Microsoft pour les campagnes politiques, les organismes sans but lucratif et les autres organisations Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test Office 365

Dans cette phase, vous procurer des abonnements d’essai pour Office 365 E5 et mobilité d’entreprise + E5 de sécurité (EMS) pour une entreprise fictive représentant une campagne politique.
  
Tout d’abord, suivez les instructions de la **Phase 2** de l' [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS E5 et l’ajouter à la même organisation que votre abonnement d’évaluation d’Office 365.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
Ensuite, activez la licence EMS E5 pour votre compte d’administrateur global.
  
1. Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.
    
2. Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Phase 2 : Création et configuration de vos groupes Azure Active Directory (AD)

Dans cette phase, vous créez et configurez des groupes Azure AD pour votre campagne.
  
Tout d’abord, créez un ensemble de groupes pour une campagne politique typique avec le portail Azure.
  
1. Sous un onglet distinct dans votre navigateur, accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous en utilisant les informations d’identification du compte d’administrateur global pour votre abonnement d’évaluation d’Office 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > utilisateurs et groupes > tous les groupes de**.
    
3. Effectuez les étapes suivantes pour chaque nom de groupe dans cette liste :
    
  - Senior and strategic staff
    
  - IT staff
    
  - Analytics staff
    
  - Regular core staff
    
  - Operations staff
    
  - Field staff
    
1. Sur la lame de **tous les groupes** , cliquez sur **+ le nouveau groupe**.
    
2. Dans la zone **nom**, tapez le nom du groupe dans la liste.
    
3. Sélectionnez **dynamique utilisateur** **d’appartenance**.
    
4. Cliquez sur **Oui** pour **activer Office fonctionnalités**.
    
5. Cliquez sur **Ajouter des requêtes dynamiques**.
    
6. Dans **Ajouter des utilisateurs où**, sélectionnez le **département**.
    
7. Dans le champ suivant, sélectionnez **est égal à**.
    
8. Dans le champ suivant, tapez le nom du groupe dans la liste.
    
9. Cliquez sur **Ajouter la requête**, puis cliquez sur **créer**.
    
10. Cliquez sur **utilisateurs et groupes : tous les groupes**.
    
Ensuite, vous configurez les groupes pour que les membres reçoivent automatiquement des licences Office 365 E5 et EMS E5.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > licences > tous les produits**.
    
2. Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**, puis cliquez sur **+ affecter**.
    
3. De la lame **attribuer la licence** , cliquez sur **utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - Analytics staff
    
  - Field staff
    
  - IT staff
    
  - Operations staff
    
  - Regular core staff
    
  - Senior and strategic staff
    
5. Cliquez sur **Sélectionner**, puis cliquez sur **attribuer**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
## <a name="phase-3-add-your-user-accounts"></a>Phase 3 : Ajout de comptes d’utilisateurs

Dans cette phase, vous ajoutez les comptes d’utilisateurs de l’exemple pour votre campagne politique.
  
Tout d’abord, vous [connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Ensuite, renseignez le nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou de l’environnement de script intégré (ISE) :
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> L’utilisation d’un mot de passe commun ici est pour l’automatisation et la facilité de configuration d’un environnement de développement/test. Ce n’est pas recommandé pour les abonnements de la production. Que vous vous connectez avec chacun de ces nouveaux comptes d’utilisateurs, vous devrez modifier le mot de passe. 
  
Utilisez ces étapes pour vérifier que l’appartenance au groupe dynamique et l’octroi de licence selon le groupe fonctionnent correctement.
  
1. À partir de l’onglet **Accueil de Microsoft Office** de votre navigateur, cliquez sur la mosaïque de **l’Admin** .
    
2. À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **utilisateurs**.
    
3. Dans la liste des utilisateurs, cliquez sur **candidat**.
    
4. Dans le volet qui répertorie les propriétés du compte d’utilisateur **candidats** , vérifiez que :
    
  - Il est membre du groupe **Senior et personnel stratégique** (dans les **appartenances aux groupes**).
    
  - Il a été affecté aux **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5** licences ( **licences**).
    
5. Fermez le volet de compte d’utilisateur **candidat** .
    
## <a name="record-values-for-future-reference"></a>Enregistrez les valeurs, vous en aurez besoin plus tard.

Enregistrez ces valeurs pour travailler avec les abonnements aux versions d’évaluation d’Office 365 et d’EMS pour cet environnement de développement/test :
  
- Nom de l’organisation bénéficiant de l’abonnement à la version d’évaluation : _______________________________________________  
    
    Par exemple, pour le nom de domaine pour l’abonnement à la version d’évaluation de contoso.onmicrosoft.com, le nom de l’organisation est « contoso ».
    
- Le nom d’administrateur global de Office 365 : ___.onmicrosoft.com
    
    Enregistrer le mot de passe pour ce compte et le mot de passe initial commun pour les autres comptes d’utilisateur dans un emplacement sécurisé.
    
## <a name="next-step"></a>Étape suivante

Générer les quatre types différents de sites d’équipe SharePoint Online dans cet environnement de développement/test avec les [sites d’équipe de créer dans un environnement de développement/test de campagne politique](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Créer des sites d’équipe dans un environnement de développement/test de campagne politique](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




