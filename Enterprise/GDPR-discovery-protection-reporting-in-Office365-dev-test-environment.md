---
title: Découverte, protection et création de rapports en vertu du RGPD dans l’environnement de développement/test Office 365
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: Faire la démonstration des fonctionnalités du RGPD dans Office 365.
ms.openlocfilehash: d5be0967142725d3735eed0d97be581c8e40fee8
ms.sourcegitcommit: 76643a1b3363624c1a0cc4b0f282e9f354652d77
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
ms.locfileid: "19454845"
---
# <a name="gdpr-discovery-protection-and-reporting-in-the-office-365-devtest-environment"></a>Découverte, protection et création de rapports en vertu du RGPD dans l’environnement de développement/test Office 365

 **Résumé :** Faire la démonstration des fonctionnalités du RGPD dans Office 365. 
  
Cet article décrit comment configurer et faire la démonstration de la découverte, de la protection et de la création de rapports des informations d’identification personnelle (PII) en vertu du Règlement général sur la protection des données (RGPD) dans un environnement de développement/test Office 365.
  
## <a name="phase-1-create-and-configure-your-trial-office-365-subscription"></a>Étape 1 : Créer et configurer votre abonnement d’évaluation Office 365

Suivez d’abord les étapes de l’article [Phase 2 de l’environnement de développement/test Office 365](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription).

Ensuite, suivez ces étapes pour configurer le Gestionnaire eDiscovery :

1. Connectez-vous à votre client d’évaluation Office 365 avec votre compte d’administrateur général.
2. Sur la page d’accueil Office 365, cliquez sur **Sécurité et conformité**.
3. Dans le nouvel onglet Sécurité et conformité, cliquez sur **Autorisations** > **Gestionnaire eDiscovery**.
4. Cliquez sur **Modifier** pour le Gestionnaire eDiscovery, puis cliquez sur **Choisir le Gestionnaire eDiscovery**.
5. Cliquez sur **+ Ajouter**, recherchez le nom de votre compte d’administrateur général et ajoutez votre compte d’administrateur général comme Gestionnaire eDiscovery.
6. Cliquez sur **Terminé** > **Enregistrer** > **Fermer**.
  
## <a name="phase-2-add-personally-identifiable-information-to-your-tenant"></a>Phase 2 : Ajouter des informations d’identification personnelle à votre client

Dans cette phase, vous créez un document avec des données personnelles pour un ensemble d’exemples de numéro de compte bancaire international (IBAN) et le stockez sur un site SharePoint Online dans votre environnement de développement/test Office 365.

1. Sur votre ordinateur local, ouvrez Microsoft Word.
2. Collez le tableau suivant dans le fichier Word et enregistrez-le sous « IBAN.docx » sur votre ordinateur local.
    
    Nombre  |Pays  |Code |IBAN  |
    |---------|---------|---------|---------|
    |1     |  Autriche SEPA      | AT            |AT611904300234573201       |
    |2     |  Bulgarie SEPA       |BG    |BG80BNBG96611020345678      |
    |3     |  Danemark SEPA      |   DK      |DK5000400440116243      |
    |4     |  Finlande SEPA      |   FI      |FI2112345600000785         |
    |5     |  France SEPA       |   FR      |FR1420041010050500013M02606         |
    |6     |  Allemagne SEPA      |   DE      |DE89370400440532013000         |
    |7     |  Grèce SEPA       |   GR      |GR1601101250000000012300695         |
    |8     |  Italie SEPA       |    IT     |GR1601101250000000012300695         |
    |9     |  Pays-Bas SEPA      |   NL      |    NL91ABNA0417164300     |
    |10     | Pologne SEPA       |  PL       | PL27114020040000300201355387        |

3. Dans un nouvel onglet de votre navigateur, saisissez : **https://**\<Nom_de_votre_client\>**.sharepoint.com**
4. Cliquez sur **Documents** pour ouvrir la bibliothèque de documents de ce site. Si vous êtes invité à suivre une visite guidée relative à une nouvelle expérience de liste, cliquez sur **Suivant** jusqu’à ce qu’elle se termine.
5.  Cliquez sur **Charger** > **Fichiers** puis sélectionnez le document IBAN.docx créé à l’étape 2.

  
## <a name="phase-3-demonstrate-data-discovery"></a>Phase 3 : Faire la démonstration de la découverte des données

Dans cette phase, vous allez faire la démonstration de la recherche afin de trouver le document créé et stocké à la Phase 2, en fonction de son contenu contenant des IBAN.

1. Dans l’onglet Sécurité et conformité, cliquez sur **Accueil**, puis sur **Recherches et examens** > **Recherche de contenu**.
2. Créez un nouvel élément de recherche en cliquant sur **+**.
3. Dans une nouvelle fenêtre, fournissez les informations suivantes :  
    a. Nom : recherche IBAN  
    b. Où voulez-vous effectuer la recherche? : **Sélectionnez des sites spécifiques pour effectuer une recherche** (cliquez sur **+**), puis saisissez l’URL du site : **https://**\<Nom_de_votre_client\>**.sharepoint.com/**  
    c. Cliquez sur **Ajouter**, puis sur **OK**. Si un avertissement s’affiche, cliquez sur **OK**.  
    d. Cliquez sur **Suivant** dans la fenêtre **Nouvelle recherche**.  
    e. Pour **Que voulez-vous rechercher ?**  : **saisissez en faisant attention à la casse : « Numéro de compte bancaire international (IBAN) »**, puis cliquez sur **Rechercher**.

4. Vérifiez que vous voyez au moins un élément répertorié dans les résultats **Recherche IBAN**.


## <a name="phase-4-create-a-custom-sensitive-information-type-via-powershell"></a>Étape 4 : Créer un type d’informations sensibles personnalisé via PowerShell

Dans cette phase, vous créez un type d’informations sensibles personnalisé pour la société Contoso fictive à l’aide de Microsoft PowerShell. Contoso utilise un nombre de clients Contoso (CCN) pour identifier chaque client dans sa base de données client. Le CCN se compose de la façon suivante :
- Deux chiffres pour représenter l’année de la création de l’enregistrement.
    - Contoso a été fondée en 2002 ; par conséquent, la première valeur possible serait 02. 
- Trois décimales pour représenter l’agence partenaire qui a créé l’enregistrement.
    - Les valeurs possibles de l’agence sont comprises entre 000 et 999. 
- Un caractère alphabétique pour représenter le secteur d’activité.
    - Les valeurs possibles sont comprises entre a et z et sont sensibles à la casse.
- Un numéro de série à quatre chiffres. 
    - Les valeurs possibles du numéro de série sont comprises entre 0000 et 9999.   

Contoso fait toujours référence aux clients en utilisant un CCN dans la correspondance interne, la correspondance externe, les documents, et tout autre formulaire. Contoso a besoin d’un type d’élément sensible personnalisé pour détecter l’utilisation de CCN dans le contenu Office 365 afin d’appliquer la protection à l’utilisation de ce formulaire d’informations d’identification personnelle.

1. Suivez les instructions indiquées dans [Se connecter au Centre de sécurité et conformité Office 365 PowerShell à l’aide de l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) et connectez-vous au Centre de sécurité et conformité avec le nom d’utilisateur principal de votre compte d’administrateur général.
2. Exécutez les commandes PowerShell suivantes :

     ```
    #Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName#Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName
    ```
3. Exécutez les commandes PowerShell suivantes et copiez les GUID générés pour une instance ouverte du bloc-notes sur votre ordinateur dans l’ordre dans lequel ils sont répertoriés.
    ```
    #Generate three unique GUIDs
    Write-Host "GUID1 = "([guid]::NewGuid().Guid)
    Write-Host "GUID2 = "([guid]::NewGuid().Guid)
    Write-Host "GUID3 = "([guid]::NewGuid().Guid)
    ```
4. Sur votre ordinateur local, ouvrez une autre instance du bloc-notes et collez-la dans le contenu suivant :

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"> 
    <RulePack id="GUID1">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="GUID2" />
    <Details defaultLangCode="en"> 
    <LocalizedDetails langcode="en"> 
    <PublisherName>Contoso Ltd.</PublisherName> 
    <Name>Contoso Rule Package</Name> 
    <Description>Defines Contoso's custom set of classification rules</Description>
    </LocalizedDetails>
    </Details>
    </RulePack>
    <Rules>
    <!-- Contoso Customer Number (CCN) -->
    <Entity id="GUID3" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
    <IdMatch idRef="Regex_contoso_ccn" />
    <Match idRef="Keyword_contoso_ccn" />
    <Match idRef="Regex_eu_date" />
    </Pattern>
    </Entity>
    <Regex id="Regex_contoso_ccn">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</Regex>
    <Keyword id="Keyword_contoso_ccn">
    <Group matchStyle="word">
    <Term caseSensitive="false">customer number</Term>
    <Term caseSensitive="false">customer no</Term>
    <Term caseSensitive="false">customer #</Term>
    <Term caseSensitive="false">customer#</Term>
    <Term caseSensitive="false">Contoso customer</Term>
    </Group>
    </Keyword>
    <Regex id="Regex_eu_date"> (0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)? |feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|apr(ile|il)?|abr(il)?|avril |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)? |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}</Regex>
    <LocalizedStrings>
    <Resource idRef="GUID3">
    <Name default="true" langcode="en-us">Contoso Customer Number (CCN)</Name>
    <Description default="true" langcode="en-us">Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</Description>
    </Resource>
    </LocalizedStrings>
    </Rules>
    </RulePackage>
    ```
5. Remplacez les valeurs GUID1, GUID2 et GUID3 dans le texte XML de l’étape 4 par leurs valeurs à l’étape 3, puis enregistrez le contenu sur votre ordinateur local avec le nom ContosoCCN.xml.
6. Saisissez le chemin d’accès à votre fichier ContosoCCN.xml et exécutez les commandes suivantes.
    ```
    #Create new Sensitive Information Type
    $path="<path to the ContosoCCN.xml file, such as C:\Scripts\ContosoCCN.xml>"
    New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path $path -Encoding Byte -ReadCount 0)
    ```
7. Dans l’onglet Sécurité et conformité, cliquez sur **Classifications** > **Types d’informations sensibles**. Vous devriez voir le nombre de clients Contoso (CCN) dans la liste.

## <a name="phase-5-demonstrate-data-protection"></a>Phase 5 : Faire la démonstration de la protection des données

La protection des informations personnelles dans Office 365 inclut l’utilisation de fonctionnalités de protection contre la perte de données (DLP). Avec les stratégies DLP dans le Centre de sécurité et conformité Office 365, vous pouvez protéger automatiquement les informations sensibles dans Office 365.

Il existe plusieurs façons d’appliquer la protection. Éduquer et sensibiliser sur l’emplacement de stockage des données des citoyens européens dans votre environnement et sur la façon dont vos employés sont autorisés à les gérer représente un seul niveau de protection des informations à l’aide des stratégies DLP Office 365.

Dans cette phase, vous créez une nouvelle stratégie DLP et faites la démonstration de son application sur le fichier IBAN.docx stocké dans SharePoint Online en Phase 2, et lorsque vous tentez d’envoyer un e-mail contenant des IBAN.

1. Dans l’onglet Sécurité et conformité de votre navigateur, cliquez sur **Accueil**.
2. Cliquez sur **Protection contre la perte de données** > **Stratégie**.
3. Cliquez sur **+ Créer une stratégie**.
4. Dans **Démarrer avec un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé** > **Stratégie personnalisée** > **Suivant**.
5. Dans **Nommer votre stratégie**, fournissez les informations suivantes, puis cliquez sur **Suivant** : a. Nom : **Stratégie de données personnelles pour les citoyens de l’UE** b. Description : **Protéger les informations d’identification personnelle des citoyens européens**
6. Dans **Choisir des emplacements**, sélectionnez **Tous les emplacements dans Office 365**. Cela inclut le contenu des documents Messagerie Exchange, OneDrive et SharePoint. Puis cliquez sur **Suivant**.
7. Dans **Personnaliser le type de contenu à protéger**, cliquez sur **Rechercher le contenu qui contient :** puis cliquez sur **Modifier**.
8. Dans **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** > **Types d’informations sensibles**.
9. Dans **Types d’informations sensibles**, cliquez sur **+ Ajouter**.
10. Dans **Types d’informations sensibles**, recherchez **IBAN**, cochez la case **Numéro de compte bancaire international (IBAN)**, puis cliquez sur **Ajouter**.
11. Vérifiez que le type d’informations sensibles **Numéro de compte bancaire international (IBAN)** a été ajouté, puis cliquez **Terminé**.
12. Dans **Le contenu contient**, vérifiez que les types d’informations sensibles ont été ajoutés, puis sur **Enregistrer**.
13. Dans **Personnaliser le type de contenu à protéger**, confirmez que **Rechercher le contenu qui contient :** contient le **Numéro de compte bancaire international (IBAN)**, puis cliquez sur **Suivant**.
14. Dans **Détecter le contenu partagé qui contient :**, changez la valeur de **10** à **1**, puis cliquez sur **Suivant**.
15. Dans **Voulez-vous activer la stratégie ou faire d’abord un test ?**, choisissez les paramètres suivants, puis cliquez sur **Suivant**.  
    a. Sélectionnez l’option pour **Je voudrais d’abord faire un test**  
    b. Cochez la case pour **Afficher les conseils de stratégie en mode test** 
16. Dans **Vérifier vos paramètres**, cliquez sur **Créer** après avoir consulté les paramètres. REMARQUE : après avoir créé une nouvelle stratégie DLP, vous devrez patienter un certain temps avant qu’elle prenne effet.
17. Sur votre ordinateur local, ouvrez une instance privée de votre navigateur.
18. Dans la barre d’adresses, saisissez **https://**\<Nom_de_votre_client\>**. sharepoint.com** et connectez-vous à l’aide de votre compte d’administrateur général.
19. Cliquez sur **Documents**.
20. Cliquez sur le fichier nommé « IBAN.docx ». Vous devriez voir « Conseil de stratégie pour IBAN.docx ». Le fichier IBAN.docx a été partagé avec des destinataires externes, ce qui constitue une violation de la stratégie DLP. 
21. Dans la barre d'adresses, saisissez : **https://outlook.office365.com**
22. Cliquez sur **Nouveau** - **Message électronique** et fournissez les informations suivantes :  
    - **À :** \<une adresse e-mail personnelle\>  
    - **Objet :** Test RGPD  
    - **Corps :** copiez le tableau des valeurs indiquées ci-dessous.
  
        |Nombre  |Pays  |Code |IBAN  |
        |---------|---------|---------|---------|
        |1     |  Autriche SEPA      | AT            |AT611904300234573201       |
        |2     |  Bulgarie SEPA       |BG    |BG80BNBG96611020345678      |
        |3     |  Danemark SEPA      |   DK      |DK5000400440116243      |
        |4     |  Finlande SEPA      |   FI      |FI2112345600000785         |
        |5     |  France SEPA       |   FR      |FR1420041010050500013M02606         |
        |6     |  Allemagne SEPA      |   DE      |DE89370400440532013000         |
        |7     |  Grèce SEPA       |   GR      |GR1601101250000000012300695         |
        |8     |  Italie SEPA       |    IT     |GR1601101250000000012300695         |
        |9     |  Pays-Bas SEPA      |   NL      |   NL91ABNA0417164300      |
        |10     | Pologne SEPA       |  PL       | PL27114020040000300201355387        |
23. Vous verrez que la stratégie DLP a reconnu que le corps de l’e-mail contient des IBAN et vous fournit le conseil de stratégie dans la partie supérieure de la fenêtre du message.
24. Fermez l’instance privée de votre navigateur.


## <a name="phase-6-demonstrate-reporting"></a>Phase 6 : Faire la démonstration de la création de rapports
 
Dans cette phase, vous allez faire la démonstration de la création de rapports Office 365 basée sur la stratégie DLP configurée en Phase 5.

   1. Dans l’onglet Sécurité et conformité de votre navigateur, cliquez sur **Accueil**.
   2. Cliquez sur **Rapports** > **Tableau de bord** > **Correspondances de stratégies DLP**.
   3. Votre stratégie DLP vous aide à identifier et à protéger les informations sensibles de l’organisation. Par exemple, dans le rapport vous verrez que la stratégie a identifié le document contenant les IBAN stocké dans SharePoint Online.
  
## <a name="see-also"></a>Voir aussi

[Protection des informations Office 365 pour RGPD](office-365-information-protection-for-gdpr.md)

[RGPD pour Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/gdpr?toc=/microsoft-365/enterprise/toc.json)
