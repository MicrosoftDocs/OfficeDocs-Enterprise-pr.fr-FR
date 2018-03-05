---
title: "À l’aide d’Azure AD pour l’authentification du serveur SharePoint"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "Résumé : Apprenez à contourner Azure Access Control Service et SAML 1.1 permet d’authentifier les utilisateurs de SharePoint Server avec Azure Active Directory."
ms.openlocfilehash: e346a79fae32c19e14ce852257d5643041faf5d4
ms.sourcegitcommit: b1cb876c8a8fca1c2d67b2bc8282f1361066962c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>À l’aide d’Azure AD pour l’authentification du serveur SharePoint

 **Résumé :** Apprenez à authentifier les utilisateurs de SharePoint Server 2016 avec Azure Active Directory.
  
> [!NOTE]
> Cet article est basé sur le travail de Kirk Evans, responsable de programme Principal de Microsoft. 

<blockquote>
<p>Cet article fait référence aux exemples de code permettant d’interagir avec Azure Active Directory graphique. Vous pouvez télécharger les exemples de code [ici](https://1drv.ms/u/s!AuAlJmH2xI6Kg3ItzF78krMFxJu3).</p>
</blockquote>

SharePoint Server 2016 offre la possibilité d’authentifier les utilisateurs à l’aide de l’authentification basée sur les revendications, ce qui vous permet de gérer vos utilisateurs en les authentifiant avec différents fournisseurs d’identité que vous faites confiance, mais une autre personne gère. Par exemple, au lieu de gérer l’authentification des utilisateurs par le biais de Services de domaine Active Directory (AD DS), vous pouvez activer les utilisateurs s’authentifient à l’aide d’Azure Active Directory (AD Azure). Cela permet l’authentification des utilisateurs de nuage uniquement avec le suffixe onmicrosoft.com dans leur nom d’utilisateur, les utilisateurs synchronisé avec un répertoire local et a invité les utilisateurs invités à partir d’autres annuaires. Il vous permet également de tirer parti des fonctionnalités AD Azure telles que l’authentification à facteurs multiples et des fonctionnalités avancées de création de rapports.

> [!IMPORTANT]
> La solution décrite dans cet article peut également être utilisée avec SharePoint Server 2013 ; Cependant, souvenez-vous que SharePoint Server 2013 est proche de la fin du support standard. Pour plus d’informations, consultez la [Politique de Microsoft](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) et les [Mises à jour produit la stratégie de traitement pour SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

Cet article explique comment vous pouvez utiliser AD Azure pour authentifier les utilisateurs au lieu de vos locaux sur les services AD DS. Dans cette configuration, AD Azure devient un fournisseur d’identité approuvé pour 2016 du serveur SharePoint. Cette configuration ajoute une méthode d’authentification de l’utilisateur qui est distincte de l’authentification AD DS utilisée par l’installation de SharePoint Server 2016 lui-même. Pour bénéficier de cet article, vous devez être familiarisé avec WS-Federation. Pour plus d’informations, consultez [Présentation de WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).

![À l’aide d’Azure AD pour l’authentification de SharePoint](images/SAML11/fig1-architecture.png)

Auparavant, cette configuration aurait nécessité un service de fédération comme Azure Access Control Service (ACS) dans le nuage ou dans un environnement qui héberge les Services de fédération Active Directory (Active Directory Federation Services) transformer les jetons SAML 2.0 à la version 1.1 de SAML. Cette transformation n’est plus nécessaire car Azure annonce maintenant permet des jetons SAML 1.1 émettrices. Le schéma ci-dessus illustre le fonctionnement de l’authentification pour les utilisateurs de SharePoint 2016 dans cette configuration, montrant qu’il n’est plus une condition requise pour un rôle d’intermédiaire effectuer cette transformation.

> [!NOTE]
> Cette configuration fonctionne si la batterie de serveurs SharePoint est hébergé dans les ordinateurs virtuels Azure ou sur site. Il ne nécessite pas l’ouverture des ports de pare-feu supplémentaire à part garantir que les utilisateurs peut accéder à Azure Active Directory à partir de leur navigateur.

Pour plus d’informations sur l’accessibilité de 2016 de SharePoint, consultez les [Directives d’accessibilité dans SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Vue d’ensemble de la configuration

Suivez ces étapes générales pour configurer votre environnement pour utiliser AD Azure comme un fournisseur d’identité SharePoint Server 2016.

1. Créer un nouveau répertoire de publicité Azure ou utilisez votre répertoire existant.
2. Assurez-vous que la zone de l’application web que vous souhaitez sécuriser avec Azure AD est configurée pour utiliser SSL.
3. Créez une nouvelle application d’entreprise dans Active Directory Azure.
4. Configurez un nouveau fournisseur d’identité approuvé dans SharePoint Server 2016.
5. Définissez les autorisations pour l’application web.
6. Ajouter une stratégie d’émission de jeton SAML 1.1 dans Azure AD.
7. Vérifiez le nouveau fournisseur.

Les sections suivantes décrivent comment effectuer ces tâches.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Étape 1 : Créer un nouveau répertoire de publicité Azure ou utilisez votre répertoire existant

Dans le portail Azure ([https://portal.azure.com](https://portal.azure.com)), créez un nouveau répertoire. Fournir le nom de l’organisation, nom de domaine d’origine et le pays ou la région.

![Création d’un répertoire](images/SAML11/fig2-createdirectory.png) 

 Si vous avez déjà un répertoire tel que celui utilisé pour Microsoft Office 365 ou votre abonnement Microsoft Azure, vous pouvez utiliser ce répertoire à la place. Vous devez disposer des autorisations pour enregistrer les applications dans le répertoire.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Étape 2 : Assurez-vous que la zone de l’application web que vous souhaitez sécuriser avec Azure AD est configurée pour utiliser SSL

Cet article a été écrit à l’aide de l’architecture de référence dans la zone [exécuter une batterie de serveurs SharePoint Server 2016 dans Azure à haute disponibilité](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Les scripts accompagnant l’article utilisés pour déployer la solution décrite dans [cet article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) créent un site qui n’utilise pas SSL.  

À l’aide de SAML requiert l’application configurée pour utiliser SSL. Si votre application web de SharePoint n’est pas configurée pour utiliser SSL, procédez comme suit pour créer un nouveau certificat auto-signé pour configurer l’application web pour SSL. Cette configuration est destinée uniquement à un environnement de laboratoire et n’est pas destinée à être production. Environnements de production doivent utiliser un certificat signé.

1. Accédez à **l’Administration centrale** > **Gestion des applications** > **Gérer les Applications Web**et choisissez l’application web qui doit être étendu pour utiliser SSL. Sélectionnez l’application web et cliquez sur le bouton de **ruban de l’étendre** . Étendre l’application web pour utiliser la même URL, mais utiliser SSL avec le port 443.</br>![Extension de l’application web vers un autre site IIS](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. Dans le Gestionnaire des services Internet (IIS), double-cliquez sur **Certificats de serveur**.
3. Dans le volet **Actions** , cliquez sur **Créer un certificat auto-signé**. Tapez un nom convivial pour le certificat dans la spécifier un nom convivial pour la zone de certificat, puis cliquez sur **OK**.
4. À partir de la boîte de dialogue **Modifier la liaison de Site** , assurez-vous que le nom d’hôte est le même que le nom convivial, comme illustré dans l’image suivante.</br>![Modification de la liaison de site dans IIS](images/SAML11/fig4-editsitebinding.png)</br>

Chacun des serveurs web frontaux de la batterie de serveurs SharePoint nécessite la configuration du certificat pour la liaison de site dans IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Étape 3 : Créer une nouvelle application d’entreprise dans Active Directory Azure

1. Dans le portail Azure ([https://portal.azure.com](https://portal.azure.com)), ouvrir votre répertoire AD Azure. **Les Applications d’entreprise**, puis cliquez sur **nouvelle application**. Choisissez **l’application Non-galerie**. Fournir un nom, comme *L’intégration SharePoint SAML* et cliquez sur **Ajouter**.</br>![Ajout d’une nouvelle application de bibliothèque non](images/SAML11/fig5-addnongalleryapp.png)</br>
2. Cliquez sur le lien dans le volet de navigation pour configurer l’application ouverture de session unique. Remplacez la liste déroulante **Mode d’ouverture de session unique** **basée sur SAML session** pour afficher les propriétés de configuration de l’application SAML. Configurer les propriétés suivantes :</br>
    - Identificateur :`urn:sharepoint:portal.contoso.local`
    - URL de la réponse :`https://portal.contoso.local/_trust/default.aspx`
    - URL de session :`https://portal.contoso.local/_trust/default.aspx`
    - Identificateur de l’utilisateur :`user.userprincipalname`</br>
    - Remarque : N’oubliez pas de modifier les URL en remplaçant *portal.contoso.local* par l’URL du site SharePoint que vous souhaitez sécuriser.</br>
3. Définir une table (semblable au tableau 1 ci-dessous) qui contient les lignes suivantes :</br> 
    - Domaine
    - Chemin d’accès complet au fichier de certificat de signature de SAML
    - SAML Single Sign-On service URL (en remplaçant */saml2* par */wsfed*)
    - ID d’objet application. </br>
Copiez la valeur de *l’identificateur* de la propriété *Realm* dans une table (voir tableau 1 ci-dessous.)
4. Enregistrez vos modifications.
5. Cliquez sur le lien **configurer (nom de l’application)** pour accéder à la page de connexion configurer.</br>![Configuration d’une connexion unique sur la page](images/SAML11/fig7-configssopage.png)</br> 
    -  Cliquez sur le lien **SAML certificat de signature - brutes** pour télécharger le certificat de signature SAML sous la forme d’un fichier avec l’extension .cer. Copiez et collez le chemin d’accès complet au fichier téléchargé dans votre table.
    - Copiez et collez le lien SAML Sign-On Service URL unique dans votre remplacement de la partie */saml2* de l’URL avec */wsfed*.</br>
6.  Naviguez vers le volet des **Propriétés** de l’application. Copiez et collez la valeur de l’ID d’objet dans la table que vous définissez dans l’étape 3.</br>![Volet des propriétés de l’application](images/SAML11/fig8-propertiespane.png)</br>
7. En utilisant les valeurs que vous avez capturé, assurez-vous que la table que vous définissez dans l’étape 3 ressemble au tableau 1 ci-dessous.


| Tableau 1 : Les valeurs capturées  |  |
|---------|---------|
|Domaine | `urn:sharepoint:portal.contoso.local` |
|Chemin d’accès complet au fichier de certificat de signature de SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|URL du service d’authentification unique SAML (remplacez /saml2 par /wsfed) " | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|ID de l’objet application | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Remplacez la valeur de */saml2* dans l’URL */wsfed*. Le point de terminaison */saml2* traitera les jetons SAML 2.0. Le point de terminaison */wsfed* permet les jetons SAML 1.1 de traitement et est obligatoire pour la fédération de SharePoint 2016 SAML.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Étape 4 : Configurez un nouveau fournisseur d’identité approuvé dans SharePoint Server 2016

Ouvrir une session sur le serveur SharePoint Server 2016 et ouvrir le Shell de gestion SharePoint 2016. Renseignez les valeurs de $realm, $wsfedurl et $filepath dans le tableau 1 et exécutez les commandes suivantes pour configurer un nouveau fournisseur d’identité approuvé.

> [!TIP]
> Si vous êtes novice dans l’utilisation de PowerShell ou que vous souhaitez en savoir plus sur la manière dont PowerShell fonctionne, consultez [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object 
System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name”
```

Ensuite, procédez comme suit pour activer le fournisseur d’identité approuvé pour votre application :
1. Dans l’Administration centrale, accédez à **Gérer les applications Web** et sélectionnez l’application web que vous souhaitez sécuriser avec AD Azure. 
2. Dans le ruban, cliquez sur **Fournisseurs d’authentification** et cliquez sur la zone que vous souhaitez utiliser.
3. Sélectionnez le **fournisseur d’identité de confiance** et le fournisseur d’identité que vous venez d’enregistrer nommé *AzureAD*.  
4. Le paramètre URL de la page de connexion, sélectionnez la **page de connexion personnalisée** et fournir la valeur « /_trust/ ». 
5. Cliquez sur **OK**.

![Configuration de votre fournisseur d’authentification](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>Étape 5 : Définir les autorisations

Les utilisateurs qui seront AD Azure se connecter et accéder à SharePoint doivent accéder à l’application. 

1. Dans le portail d’Azure, ouvrez le répertoire de publicité Azure. **Les Applications d’entreprise**, puis cliquez sur **toutes les applications**. Cliquez sur l’application que vous avez créée précédemment (intégration de SAML SharePoint).
2. Cliquez sur **utilisateurs et groupes**. 
3. Cliquez sur **Ajouter un utilisateur** pour ajouter un utilisateur ou un groupe qui dispose des autorisations pour se connecter à SharePoint à l’aide d’Active Directory Azure.
4. Sélectionnez l’utilisateur ou le groupe, puis cliquez sur **attribuer**.
 
L’utilisateur possède l’autorisation dans Active Directory Azure, mais aussi autorisation doit être accordée dans SharePoint. Utilisez les étapes suivantes pour définir des autorisations pour accéder à l’application web.

1. Dans l’Administration centrale, cliquez sur **Gestion des applications**.
2. Dans la section **Applications web** de la page **Gestion des applications**, cliquez sur **Gérer les applications web**.
3. Cliquez sur l'application web appropriée, puis sur **Stratégie de l'utilisateur**.
4. Dans la stratégie d’Application Web, cliquez sur **Ajouter des utilisateurs**.</br>![Recherche d’un utilisateur en revendication de nom](images/SAML11/fig11-searchbynameclaim.png)</br>
5. Dans la boîte de dialogue **Ajouter des utilisateurs**, cliquez sur la zone appropriée dans **Zones**, puis sur **Suivant**.
6. Dans la boîte de dialogue de **stratégie pour une Application Web** , dans la section **Sélectionner les utilisateurs** , cliquez sur l’icône **Parcourir** .
7. Dans la zone de texte **Rechercher** , tapez le nom de connexion d’un utilisateur dans le répertoire et cliquez sur **Rechercher**. </br>Exemple : *demouser@blueskyabove.onmicrosoft.com*.
8. Sous l’en-tête AzureAD dans la liste, sélectionnez la propriété name et cliquez sur **Ajouter** , puis cliquez sur **OK** pour fermer la boîte de dialogue.
9. Dans autorisations, cliquez sur **Contrôle total**.</br>![L’autorisation de contrôle total à un utilisateur de revendications](images/SAML11/fig12-grantfullcontrol.png)</br>
10. Cliquez sur **Terminer**, puis sur **OK**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Étape 6 : Ajouter une stratégie d’émission de jeton SAML 1.1 dans Azure AD

Lorsque l’application Azure AD est créée dans le portail, il utilise par défaut SAML 2.0. SharePoint Server 2016 requiert le format du jeton SAML 1.1. Le script suivant supprime la stratégie de SAML 2.0 par défaut et ajouter une nouvelle stratégie pour les jetons SAML 1.1 de problème.

```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```

## <a name="step-7-verify-the-new-provider"></a>Étape 7 : Vérifiez le nouveau fournisseur

Ouvrez un navigateur vers l’URL de l’application web que vous avez configurés dans les étapes précédentes. Vous êtes redirigé vers la session dans Azure AD.

![Signature dans Azure annonce configuré pour la fédération](images/SAML11/fig13-examplesignin.png)

Vous êtes invité si vous souhaitez rester connecté.

![Rester connecté ?](images/SAML11/fig14-staysignedin.png)

Enfin, vous pouvez accéder au site connecté en tant qu’un utilisateur à partir de votre client Azure Active Directory.

![Utilisateur connecté à SharePoint](images/SAML11/fig15-signedinsharepoint.png)


## <a name="additional-resources"></a>Ressources supplémentaires

[Présentation de WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Participer à la discussion

|**Contactez-nous**|**Description**|
|:-----|:-----|
|**De quelles solutions avez-vous besoin ?** <br/> |Nous sommes en train de créer du contenu pour les solutions qui s'étendent sur plusieurs produits et services Microsoft. Donnez-nous votre avis sur nos solutions entre serveurs ou demandez des solutions spécifiques en envoyant un courrier électronique à [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Participer à la discussion sur les solutions** <br/> |Si vous êtes passionné par les solutions basées sur le cloud, rejoignez le conseil consultatif de l’adoption cloud (CAAB) pour interagir avec une communauté vaste et dynamique de développeurs de contenu Microsoft, de professionnels du secteur et de clients venant du monde entier. Pour participer, ajoutez-vous en tant que membre de l’espace [CAAB (Conseil consultatif de l’adoption cloud)](https://aka.ms/caab) de la communauté Microsoft Tech et envoyez-nous un message électronique à l’adresse [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Tout le monde peut lire le contenu lié à la communauté sur le [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Toutefois, les membres CAAB reçoivent des invitations à des webinaires privés qui décrivent les nouvelles solutions et ressources relatives à l’adoption cloud.<br/> |
|**Obtenir l'image que vous voyez ici** <br/> |Si vous voulez obtenir une copie modifiable de l’image que vous voyez dans cet article, nous serons ravis de vous l’envoyer. Envoyez-nous votre demande par courrier électronique, en incluant l’URL et le titre de l’illustration, à [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   

