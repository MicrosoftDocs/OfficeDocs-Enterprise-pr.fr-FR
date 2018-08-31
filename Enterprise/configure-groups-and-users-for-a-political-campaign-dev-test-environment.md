---
title: Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne politique
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
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: 'Résumé : Créez des abonnements d’essai Office 365 et Enterprise Mobility + Security (EMS) avec des utilisateurs et des groupes pour un environnement de développement/test de campagne électorale.'
ms.openlocfilehash: c58782185d0638f7a6a9e14ee7e4516f1852908b
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915689"
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne électorale

 **Résumé : ** Créez des abonnements d’essai Office 365 et Enterprise Mobility + Security (EMS) avec des utilisateurs et des groupes pour un environnement de développement/test de campagne électorale.
  
Suivez les instructions de cet article pour créer un environnement de développement/test incluant des comptes d’utilisateurs simplifiés et des groupes pour la solution des [conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations souples](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md).
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test Office 365

Dans cette phase, vous obtenez des abonnements d’essai pour Office 365 E5 et Enterprise Mobility + Security (EMS) E5 pour une entreprise fictive qui représente une campagne électorale.
  
Suivez d’abord les instructions de la **Phase 2** de l’[environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS E5 et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur général de votre abonnement d’essai. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la vignette **Administration**.
    
3. Sous l’onglet **Centre d’administration Office** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Enterprise Mobility + Security E5**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
Ensuite, activez la licence EMS E5 pour votre compte Administrateur général.
  
1. Sous l’onglet **Centre d’administration Office 365** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Cliquez sur votre compte Administrateur général, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet **Licences de produit**, activez la licence de produit pour **Enterprise Mobility + Security E5** en sélectionnant **Activer**, cliquez sur **Enregistrer**, cliquez deux fois sur **Fermer**.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Phase 2 : Création et configuration de vos groupes Azure Active Directory (AD)

Dans cette phase, vous créez et configurez des groupes Azure AD pour votre campagne.
  
Commencez par créer un ensemble de groupes pour une campagne électorale standard avec le portail Azure.
  
1. Dans un onglet distinct dans votre navigateur, accédez au portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous avec les informations d’identification du compte Administrateur général de votre abonnement d’essai Office 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Utilisateurs et groupes > Tous les groupes**.
    
3. Procédez comme suit pour chaque nom de groupe dans cette liste :
    
  - Senior and strategic staff
    
  - IT staff
    
  - Analytics staff
    
  - Regular core staff
    
  - Operations staff
    
  - Field staff
    
1. Dans le panneau **Tous les groupes**, cliquez sur **+ Nouveau groupe**.
    
2. Tapez le nom du groupe de la liste dans **Nom**.
    
3. Sélectionnez **Utilisateur dynamique** dans **Appartenance**.
    
4. Cliquez sur **Oui** pour **Activer les fonctionnalités Office**.
    
5. Cliquez sur **Ajouter une requête dynamique**.
    
6. Dans **Ajouter des utilisateurs où**, sélectionnez **Service**.
    
7. Dans le champ suivant, sélectionnez **Est égal à**.
    
8. Dans le champ suivant, tapez le nom du groupe de la liste.
    
9. Cliquez sur **Ajouter une requête**, puis cliquez sur **Créer**.
    
10. Cliquez sur **Utilisateurs et groupes - Tous les groupes**.
    
Ensuite, vous configurez les groupes afin que des licences Office 365 E5 et EMS E5 soient attribuées automatiquement aux membres.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > Licences > Tous les produits**.
    
2. Dans la liste, sélectionnez **Enterprise Mobility + Security E5** et **Office 365 Entreprise E5**, puis cliquez sur **+ Affecter**.
    
3. Dans le panneau **Affecter une licence**, cliquez sur **Utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - Analytics staff
    
  - Field staff
    
  - IT staff
    
  - Operations staff
    
  - Regular core staff
    
  - Senior and strategic staff
    
5. Cliquez sur **Sélectionner**, puis sur **Affecter**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
## <a name="phase-3-add-your-user-accounts"></a>Phase 3 : Ajout de comptes d’utilisateurs

Dans cette phase, vous ajoutez les comptes d’utilisateurs de l’exemple pour votre campagne politique.
  
Vous devez d’abord vous [connecter au module PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
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
> L’utilisation d’un mot de passe commun permet d’automatiser et de faciliter la configuration d’un environnement de développement/test. Il n’est pas recommandé de l’utiliser dans un environnement de production. Lorsque vous vous connectez avec chacun de ces nouveaux comptes d’utilisateur, vous êtes invité à changer le mot de passe. 
  
Utilisez ces étapes pour vérifier que l’appartenance au groupe dynamique et l’octroi de licence selon le groupe fonctionnent correctement.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Administration**.
    
2. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Utilisateurs**.
    
3. Dans la liste des utilisateurs, cliquez sur **Candidat**.
    
4. Dans le volet qui répertorie les propriétés du compte d’utilisateur **Candidat**, vérifiez que les situations suivantes sont satisfaites :
    
  - Il est membre du groupe **Senior and strategic staff** (dans **Appartenances aux groupes**).
    
  - Les licences **Enterprise Mobility + Security E5** et **Office 365 Entreprise E5** lui ont été affectées (dans **Licences des produits**).
    
5. Fermez le volet du compte d’utilisateur **Candidat**.
    
## <a name="record-values-for-future-reference"></a>Enregistrez les valeurs, vous en aurez besoin plus tard.

Enregistrez ces valeurs pour utiliser les abonnements aux versions d’évaluation d’Office 365 et d’EMS pour cet environnement de développement/test :
  
- Nom de l’organisation bénéficiant de l’abonnement à la version d’évaluation : ![](./media/Common-Images/TableLine.png) 
    
    Par exemple, pour le nom de domaine de l’abonnement à la version d’évaluation de contoso.onmicrosoft.com, le nom de l’organisation est « contoso ».
    
- Nom de l’administrateur général Office 365 : ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Enregistrez le mot de passe pour ce compte et le mot de passe initial commun pour les autres comptes d’utilisateurs dans un emplacement sécurisé.
    
## <a name="next-step"></a>Étape suivante

Créez les quatre différents types de sites d’équipe SharePoint Online dans cet environnement de développement/test en vous reportant à [Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




