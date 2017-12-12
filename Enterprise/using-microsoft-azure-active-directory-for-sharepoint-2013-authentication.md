---
title: "Utilisation de Microsoft Azure Active Directory pour l'authentification SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "Résumé : Apprenez à utiliser le Service de contrôle d'accès pour authentifier les utilisateurs de SharePoint Server 2013 avec Azure Active Directory."
---

# Utilisation de Microsoft Azure Active Directory pour l'authentification SharePoint 2013

 **Résumé :** Apprenez à utiliser le Service de contrôle d'accès pour authentifier les utilisateurs de SharePoint Server 2013 avec Azure Active Directory.
  
Il peut s'avérer plus facile de gérer vos utilisateurs en les authentifiant avec des fournisseurs d'identité différents. Si vous y pensez, il peut être pratique d'utiliser un fournisseur d'identité de confiance tandis qu'une autre personne s'occupe de la gestion. Par exemple, vous pouvez disposer d'un type d'authentification pour les utilisateurs qui accèdent à SharePoint Server 2013 dans le cloud et d'un autre pour les utilisateurs SharePoint 2013 dans votre environnement local. Le Service de contrôle d'accès Azure rend ces choix possibles.
  
Cet article vous explique comment utiliser le service de contrôle d'accès Azure pour authentifier vos utilisateurs SharePoint 2013 avec Azure AD, au lieu d'utiliser votre instance Active Directory locale. Dans cette configuration, Azure AD devient un fournisseur d'identité approuvé pour SharePoint 2013. Cette configuration ajoute une méthode d'authentification utilisateur distincte de l'authentification Active Directory utilisée par l'installation SharePoint 2013 proprement dite. Pour pouvoir tirer parti de cet article, vous devez connaître WS-Federation. Pour plus d'informations, voir l'article de [présentation de WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).
  
Le schéma suivant illustre le fonctionnement de l'authentification pour les utilisateurs SharePoint 2013 dans cette configuration.
  
![Utilisateurs authentifiés via Azure Active Directory](images/SP_AzureAD.png)
  
L'exemple utilisé dans cet article est fourni par Kirk Evans, architecte Microsoft pour le centre d'excellence Azure.
  
Pour plus d'informations sur l'accessibilité SharePoint 2013, voir [Accessibilité pour SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).
  
## Vue d'ensemble de la configuration

Suivez la procédure générale suivante pour configurer votre environnement pour utiliser Azure AD comme fournisseur d'identité SharePoint 2013.
  
1. Créez un nouveau client et espace de noms Azure AD.
    
2. Ajoutez un fournisseur d'identité WS-Federation.
    
3. Ajoutez une application par partie de confiance SharePoint.
    
4. Créez un certificat auto-signé à utiliser pour SSL.
    
5. Créez un groupe de règles pour l'authentification basée sur les revendications.
    
6. Configurez le certificat X.509.
    
7. Créez un mappage de revendications.
    
8. Configurez SharePoint pour le nouveau fournisseur d'identité.
    
9. Définissez les autorisations.
    
10. Vérifiez le nouveau fournisseur.
    
## Création du client et de l'espace de noms Azure AD.

Procédez comme suit pour créer un client Azure AD et un espace de noms associé. Dans cet exemple, nous utilisons l'espace de noms « blueskyabove ».
  
1. Dans le portail de gestion Azure, cliquez sur **Active Directory**, puis créez un client Azure AD.
    
2. Cliquez sur **Espaces de noms Access Control** et créez un espace de noms.
    
3. Cliquez sur **Gérer** dans la barre du bas pour ouvrir cet emplacement : https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.
    
4. Ouvrez Windows PowerShell. Utilisez le Module Microsoft Online Services pour Windows PowerShell, qui est requis pour l'installation de Azure pour les cmdlets Windows PowerShell.
    
5. Dans l'invite de commandes Windows PowerShell, saisissez la commande  `Connect-Msolservice`, puis saisissez vos informations d'identification.
    
    > [!NOTE]
    > Pour plus d'informations sur l'utilisation de Azure pour les cmdlets Windows PowerShell, voir [Gestion d'Azure AD à l'aide de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124). 
  
6. Dans l'invite de commandes Windows PowerShell, saisissez les commandes suivantes :
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    L'illustration suivante montre les données obtenues.
    
     ![Création de noms de principal de service](images/ServicePrincipalNames.jpg)
  
## Ajout d'un fournisseur d'identité WS-Federation à l'espace de noms

Procédez comme suit pour ajouter un nouveau fournisseur d'identité WS-Federation à l'espace de noms blueskyabove.
  
1. Dans le portail de gestion Azure, accédez à **Active Directory** > **Espaces de noms Access Control**, cliquez sur **Créer une nouvelle instance**, puis cliquez sur **Gérer**.
    
2. Dans le portail Azure Access Control, cliquez sur **Fournisseurs d'identité** > **Ajouter**, comme illustré dans la capture suivante.
    
     ![Boîte de dialogue des fournisseurs d'identité dans Azure](images/Identity.jpg)
  
3. Cliquez sur **Fournisseur d'identité WS-Federation**, comme illustré dans la figure suivante, puis cliquez sur **Suivant**.
    
     ![Paramètres d'ajout de fournisseur d'identité](images/AddIdentity.jpg)
  
4. Indiquez le nom complet et le texte du lien d'ouverture de session, puis cliquez sur **Enregistrer**. Pour l'URL des métadonnées WS-Federation, saisissez https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. La capture suivante illustre la définition des paramètres.
    
     ![Fournisseur d'identité de la fédération](images/FederationIdentity.jpg)
  
## Ajoutez SharePoint comme application par partie de confiance.

Procédez comme suit pour ajouter SharePoint comme application par partie de confiance.
  
Pour plus d'informations sur les paramètres des applications par partie de confiance, voir [Applications par partie de confiance](https://go.microsoft.com/fwlink/p/?LinkId=393125).
  
1. Dans le portail Azure Access Control, cliquez sur **Applications par partie de confiance**, puis cliquez sur **Ajouter**, comme illustré dans la capture suivante.
    
     ![Paramètres d'application de partie de confiance](images/RelyingPartyApplications.jpg)
  
## Création d'un certificat auto-signé à utiliser pour SSL

Procédez comme suit pour créer un certificat auto-signé à utiliser pour sécuriser les communications sur SSL.
  
1. Étendez l'application web pour utiliser la même URL que le site de publication, mais utilisez SSL avec le port 443, comme illustré dans la capture suivante.
    
     ![Paramètres permettant d'étendre l'application](images/ExtendWebApp.jpg)
  
2. Dans le Gestionnaire des services Internet (IIS), double-cliquez sur **Certificats de serveur**.
    
3. Dans le volet **Actions**, cliquez sur **Créer un certificat auto-signé**. Saisissez un nom convivial pour le certificat dans la case **Indiquer un nom convivial pour le certificat**, puis cliquez sur **OK**.
    
4. Dans la boîte de dialogue **Modifier la liaison de site**, vérifiez que le nom d'hôte est le même que le nom convivial, comme illustré dans les captures suivantes.
    
     ![Assistant Créer un certificat auto-signé](images/SelfSignedCert.jpg)
  
     ![Nom d'hôte dans la boîte de dialogue Modifier les liaisons](images/SelfSignedCert1.jpg)
  
5. Dans le portail de gestion Azure, cliquez sur la machine virtuelle que vous souhaitez configurer, puis cliquez sur **Points de terminaison**.
    
6. Cliquez sur **Ajouter**, puis cliquez sur **-->** (pour Suivant).
    
7. Dans **Nom**, saisissez le nom du point de terminaison.
    
8. Dans **Port public** et **Port privé**, saisissez les numéros de port que vous souhaitez utiliser, puis cliquez sur la coche pour terminer. Ces numéros peuvent être différents. Pour les besoins de cet article, nous utilisons le port 443, comme indiqué dans la capture suivante.
    
     ![Paramètres de point de terminaison dans Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > Pour plus d'informations sur l'ajout d'un point de terminaison à une machine virtuelle dans Azure, voir [Comment configurer des points de terminaison sur une machine virtuelle](https://go.microsoft.com/fwlink/p/?LinkId=393126). 
  
9. Dans le portail de services Access Control, ajoutez une partie de confiance, comme illustré dans la capture suivante.
    
     ![Paramètres d'application d'ajout de partie de confiance](images/AddRelyingParty.jpg)
  
## Créez un groupe de règles pour l'authentification basée sur les revendications.

Procédez comme suit pour créer un groupe de règles pour contrôler l'authentification basée sur les revendications.
  
1. Dans le volet gauche, cliquez sur **Groupes de règles**, puis cliquez sur **Ajouter**.
    
2. Saisissez le nom du groupe de règles, cliquez sur **Enregistrer**, puis cliquez sur **Générer**. Pour les besoins de cet article, nous utilisons le **Default Rule Group for. spvms.cloudapp.net**, comme illustré dans la capture suivante.
    
     ![Paramètres de groupe de règles dans Azure](images/RuleGroup.jpg)
  
     ![Règles après sélection de l'option Générer](images/GenerateRules.jpg)
  
    > [!NOTE]
    > Pour plus d'informations sur la création de groupes de règles, voir [Règles et groupes de règles](https://go.microsoft.com/fwlink/p/?LinkId=393128). 
  
3. Cliquez sur le groupe de règles que vous souhaitez modifier, puis cliquez sur la règle de revendication que vous souhaitez modifier. Pour les besoins de cet article, nous ajoutons une règle de revendication au groupe pour transmettre la règle **name** en tant que règle **upn**, comme illustré dans la capture suivante.
    
     ![Règles de revendication dans le contrôle d'accès Azure](images/ClaimRules.jpg)
  
4. Supprimez la règle de revendication existante nommée **upn** et laissez la règle de **Name Claim to UPN**, comme illustré dans la capture suivante.
    
     ![Paramètres de règles dans le contrôle d'accès Azure](images/ClaimToUPN.jpg)
  
## Configurer le certificat X.509

Procédez comme suit pour configurer le certificat X.509 à utiliser pour la signature des jetons.
  
1. Dans le volet Service du contrôle d'accès, sous **Développement**, cliquez sur **Intégration d'applications**.
    
2. Dans **Référence du point de terminaison**, localisez le fichier **Federation.xml** qui est associé à votre client Azure, puis copiez l'emplacement dans la barre d'adresses d'un navigateur.
    
3. Dans le fichier **Federation.xml**, recherchez la section **RoleDescriptor** et copiez les informations de l'élément _<X509Certificate>_, comme illustré dans la capture suivante.
    
     ![Élément de certificat X509 du fichier Federation.xml](images/X509Cert.jpg)
  
4. À la racine du lecteur C:\\, créez un dossier nommé **Certificates**.
    
5. Enregistrez les informations de l'élément X509Certificate dans le dossier C:\\Certificats avec le nom de fichier **AcsTokenSigning.cer**.
    
    > [!NOTE]
    > Le nom de fichier doit être enregistré avec une extension .cer. 
  
     ![Sauvegarde de l'élément X509Certificate en tant que fichier](images/X509Cert_Save.jpg)
  
## Création d'un mappage de revendications à l'aide de Windows PowerShell

Procédez comme suit pour créer un mappage de revendications à l'aide de Windows PowerShell.
  
Vérifiez que vous êtes membre :
  
1. du rôle serveur fixe **securityadmin** sur l'instance SQL Server.
    
2. du rôle de base de données fixe **db_owner** sur toutes les bases de données à mettre à jour.
    
3. du groupe Administrateurs sur le serveur sur lequel vous exécutez les cmdlets Windows PowerShell.
    
Un administrateur peut utiliser l'applet de commande **Add-SPShellAdmin** pour accorder des autorisations d'utilisation des applets de commande SharePoint 2013.
  
> [!NOTE]
> Si vous ne disposez pas des autorisations, contactez votre administrateur d'installation ou votre administrateur SQL Server afin de les demander. Pour plus d'informations sur les autorisations Windows PowerShell, voir [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx). 
  
1. Dans le menu **Démarrer**, cliquez sur **Tous les programmes**.
    
2. Cliquez sur **Produits Microsoft SharePoint 2013**.
    
3. Cliquez sur **SharePoint 2013 Management Shell**.
    
4. À l'invite de commandes Windows PowerShell, entrez les commandes suivantes pour créer un mappage de revendications :
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## Configuration de SharePoint pour le nouveau fournisseur d'identité

Procédez comme suit pour configurer votre installation SharePoint avec le nouveau fournisseur d'identité pour Azure AD.
  
1. Vérifiez que le compte d'utilisateur qui exécute cette procédure est membre du groupe SharePoint Administrateurs de batterie.
    
2. Dans la page d'accueil de l'Administration centrale, cliquez sur **Gestion des applications**.
    
3. Dans la section **Applications web** de la page **Gestion des applications**, cliquez sur **Gérer les applications web**.
    
4. Cliquez sur l'application Web appropriée.
    
5. Dans le ruban, cliquez sur **Fournisseurs d'authentification**.
    
6. Sous **Zone**, cliquez sur le nom de la zone. Par exemple, **Par défaut**.
    
7. Dans la section **Types d'authentification basée sur les revendications** de la page **Modifier l'authentification**, sélectionnez **Fournisseur d'identité approuvé**, puis cliquez sur le nom de votre fournisseur, **ACS Provider** aux fins de cet article. Cliquez sur **OK**.
    
8. La capture suivante illustre le paramètre de **Trusted Provider**.
    
![Paramètre de fournisseur approuvé dans une application web](images/AddProvider_Azure.jpg)
  
## Définition des autorisations

Procédez comme suit pour définir les autorisations pour accéder à l'application web.
  
1. Sur la page d'accueil de l'Administration centrale, cliquez sur **Gestion des applications**.
    
2. Dans la section **Applications web** de la page **Gestion des applications**, cliquez sur **Gérer les applications web**.
    
3. Cliquez sur l'application web appropriée, puis sur **Stratégie de l'utilisateur**.
    
4. Dans **Stratégie de l'application web**, cliquez sur **Ajouter des utilisateurs**.
    
5. Dans la boîte de dialogue **Ajouter des utilisateurs**, cliquez sur la zone appropriée dans **Zones**, puis sur **Suivant**.
    
6. Dans la boîte de dialogue **Ajouter des utilisateurs**, saisissez user2@blueskyabove.onmicrosoft.com (fournisseur ACS).
    
7. Dans **Autorisations**, cliquez sur **Contrôle total**.
    
8. Cliquez sur **Terminer**, puis sur **OK**.
    
La capture suivante illustre la section **Ajouter des utilisateurs** d'une application web existante.
  
![Ajout d'utilisateurs à une application web existante](images/AddUsers_Azure.jpg)
  
## Vérification du nouveau fournisseur

Procédez comme suit pour vérifier que le nouveau fournisseur d'identité fonctionne en vous assurant que le nouveau fournisseur d'authentification s'affiche à l'invite de connexion.
  
1. Connectez-vous en utilisant le nouveau fournisseur nommé **Blue Sky Above**, comme illustré dans la capture suivante.
    
     ![Boîte de dialogue de connexion affichant le nouveau fournisseur approuvé](images/BlueSkyAbove.jpg)
  
## Ressources supplémentaires

[Présentation de WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
**Participer à la discussion**

|**Contactez-nous**|**Description**|
|:-----|:-----|
|**De quelles solutions avez-vous besoin ?** <br/> |Nous sommes en train de créer du contenu pour les solutions qui s'étendent sur plusieurs produits et services Microsoft. Donnez-nous votre avis sur nos solutions entre serveurs ou demandez des solutions spécifiques en envoyant un courrier électronique à [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?Subject=[Solution%20Feedback]:%20).  <br/> |
|**Participer à la discussion sur les solutions** <br/> |Si la recherche de solutions vous passionne, rejoignez notre conseil consultatif pour les solutions (SAB) pour vous connecter à une communauté plus large et dynamique, composée de développeurs de contenu pour les solutions Microsoft, de professionnels du secteur et de clients du monde entier. Pour nous rejoindre, envoyez un courrier électronique à [SAB@microsoft.com](mailto:sab@microsoft.com?Subject=Request%20to%20join%20the%20Solutions%20Advisory%20Board). Le contenu publié par la communauté est accessible à tous sur le [blog SAB](http://blogs.technet.com/b/solutions_advisory_board/). Toutefois, les membres du SAB ont accès à des webinaires privés sur les solutions et peuvent participer au réseau Yammer SAB.  <br/> |
|**Obtenir l'image que vous voyez ici** <br/> |Si vous voulez obtenir une copie modifiable de l'image que vous voyez dans le contenu [Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md), nous serons ravis de vous l'envoyer. Envoyez-nous votre demande par courrier électronique, en incluant l'URL et le titre de l'illustration, à [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

