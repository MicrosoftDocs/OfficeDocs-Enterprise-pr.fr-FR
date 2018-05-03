---
title: Détecter et personnalisés et règles Outlook de corriger des formulaires Injections attaques dans Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Découvrez comment identifier et corriger les règles d’Outlook et les attaques d’injections de formulaires personnalisés dans Office 365
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>Détecter et résoudre les règles d’Outlook et les attaques Injections de formulaires personnalisés dans Office 365

**Résumé** Découvrez comment identifier et corriger les règles d’Outlook et les attaques d’injections formulaires personnalisés dans Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Quel est l’attaque par injection de formulaires personnalisés et les règles d’Outlook ?
Une fois une personne malveillante a franchi un compte dans votre location et obtient, il doit y essayer et établir un moyen de rester dans ou un moyen pour revenir une fois qu’ils sont détectés et supprimés. Il s’agit d’établissement d’un mécanisme de persistance. Deux méthodes que cela sont en exploitant les règles Outlook ou en insérant des formulaires personnalisés dans Outlook. Dans les deux cas, la règle ou le formulaire est synchronisé à partir du service nuage vers le client de bureau, pour un format complet et ré-installation du logiciel client n’éliminer le mécanisme d’injection. C’est pourquoi lorsque le logiciel client Outlook se reconnecte à la boîte aux lettres dans le nuage il sera télécharger à nouveau les règles et les formulaires du nuage. Une fois les règles et les formulaires sont en place, l’intrus les utilise pour exécuter du code à distance ou personnalisé, généralement pour installer des logiciels malveillants sur l’ordinateur local. Le programme malveillant puis nouveau vol des informations d’identification ou d’autres activités illicite. Ici, la bonne nouvelle est que si vous conservez vos clients à la dernière version, vous n’êtes pas le risque que les deux mécanismes de bloquent les valeurs par défaut du client Outlook en cours. 

En règle générale, les attaques suivent ces modèles :

L’exploitation de règles
1. L’intrus vol le nom d’utilisateur et le mot de passe de l’un de vos utilisateurs.
2. L’intrus se connecte ensuite à la boîte aux lettres Exchange des utilisateurs. La boîte aux lettres peut être dans Exchange online ou Exchange sur site.
3. L’intrus crée ensuite une règle de transfert dans la boîte aux lettres qui est déclenché lorsque la boîte aux lettres reçoit un message électronique qui correspond aux critères de la règle. Les critères de la règle et le contenu du courrier électronique déclencheur est personnalisée pour eux.
4. Il envoie le courrier électronique déclencheur à l’utilisateur qui est à l’aide de leur boîte aux lettres normalement.
5. Lorsque le message est reçu, la règle est déclenchée. L’action de la règle est généralement pour lancer une application sur un serveur (WebDAV).
6. L’application installe généralement les logiciels malveillants, tels [Powershell Empire](https://www.powershellempire.com/), localement sur l’ordinateur de l’utilisateur.
7. Le programme malveillant permet à l’intrus peut voler de nouveau le nom d’utilisateur et mot de passe ou autre information d’identification de l’ordinateur local et effectuer d’autres actions malveillantes.

L’exploitation de formulaires
1. L’intrus vol le nom d’utilisateur et le mot de passe de l’un de vos utilisateurs.
2. L’intrus ensuite se connecter à la boîte aux lettres Exchange des utilisateurs. La boîte aux lettres peut être dans Exchange online ou Exchange sur site.
3. L’intrus crée un modèle de formulaire de messagerie personnalisé et insère dans la boîte aux lettres de l’utilisateur.  Le formulaire personnalisé est déclenché lorsque la boîte aux lettres reçoit un message électronique qui requiert la boîte aux lettres pour charger le formulaire personnalisé. Le formulaire personnalisé et le format des courriers électroniques sont personnalisées pour eux.
4. Il envoie le courrier électronique déclencheur à l’utilisateur, qui est à l’aide de leur boîte aux lettres normalement.
5. Lorsque le message est reçu, le formulaire est chargé. Le formulaire lance une application sur un serveur (WebDAV).
6. L’application installe généralement les logiciels malveillants, tels [Powershell Empire](https://www.powershellempire.com/), localement sur l’ordinateur de l’utilisateur.
7. Le programme malveillant permet à l’intrus peut voler de nouveau le nom d’utilisateur et mot de passe ou autre information d’identification de l’ordinateur local et effectuer d’autres actions malveillantes.


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Les règles une et attaque par Injection de formulaires personnalisé peut ressembler à Office 365 ?

Ces mécanismes de persistance sont peu de chances d’être remarqué par vos utilisateurs et peuvent dans certains cas, même être invisibles leur.  Cet article vous indique comment rechercher des sept signes (indicateurs de compromission) répertoriées ci-dessous. Si vous trouvez un de ces, vous devez suivre des étapes de mise à jour.

- Indicateurs des règles de compromettre
    - Action de la règle consiste à démarrer une application.
    - Règle fait référence à un EXE, ZIP ou URL.
    - Sur l’ordinateur local, recherchez le nouveau processus démarre qui proviennent de l’identifiant personnel Outlook.
- Indicateurs de la compromission de formulaires personnalisés 
    - Formulaire personnalisé présent enregistrée en tant que leur propre classe de message.
    - Classe de message contient du code exécutable.
    - Généralement stockées dans les dossiers boîte de réception ou la bibliothèque des formulaires personnels.
    - Formulaire est nommé IPM. Note. [nom personnalisé].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Étapes pour la recherche de signes d’attaque et de le confirmer
Vous pouvez utiliser une de ces deux méthodes pour confirmer l’attaque.
- Examinez manuellement les règles et les formulaires pour chaque boîte aux lettres à l’aide du client Outlook.  Cette méthode est complète, mais vous ne pouvez vérifier utilisateur de boîte aux lettres à un moment qui peut être beaucoup de temps si vous disposez de plusieurs utilisateurs à vérifier.  Il peut également entraîner une violation de l’ordinateur sur lequel vous exécutez la vérification de.
- Utilisez le script PowerShell [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) pour vider automatiquement tous les messages des formulaires personnalisés pour tous les utilisateurs et les règles de transfert dans votre location. Il s’agit de la méthode plus rapide et plus sûre avec le moins de surcharge.


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Confirmer l’attaque règles à l’aide du client Outlook
1. Ouvrez le client Outlook aux utilisateurs en tant que l’utilisateur.  L’utilisateur peut qu’en examinant les règles de leur boîte aux lettres.
2. Consultez l’article [Gérer les messages à l’aide de règles](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010) pour les procédures à suivre ouvrir l’interface de règles dans les versions 2007, 2010 ou 2013 d’Outlook.
3. Recherchez les règles de l’utilisateur n’a pas été créé, ou les règles inattendues ou les règles avec des noms suspects.
4. Recherchez dans la description de la règle pour les actions de règle qui démarrer et l’application ou faire référence à un. EXE. Fichier ZIP ou pour le lancement d’une URL.
5. Apparence pour tous les nouveaux processus qui démarre à l’aide de l’ID du processus Outlook.  Reportez-vous à [trouver l’ID de processus](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Étapes pour confirmer l’attaque de formulaires à l’aide du client Outlook
1. Ouvrez le client Outlook de l’utilisateur en tant que l’utilisateur.
2. Suivez les étapes dans [Afficher l’onglet Développeur](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45) pour la version utilisateur d’Outlook.
3. Ouvrez l’onglet Développeur maintenant visibles dans Outlook, cliquez sur **créer un formulaire**.
4. Dans la liste **Rechercher dans** , sélectionnez la **boîte de réception** . Recherchez les formulaires personnalisés.  Formulaires personnalisés sont assez rares pour que si vous avez tout les formulaires personnalisés, il est important de plus près.
5. Examinez les formulaires personnalisés, notamment celles marqués comme étant masqués.
6. Ouvrir les formulaires personnalisés et dans le groupe **formulaire** , cliquez sur **Afficher le Code** pour voir ce qui s’exécute lorsque le formulaire est chargé.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Étapes pour confirmer l’attaque de règles et les formulaires à l’aide de PowerShell
Le moyen le plus simple pour vérifier les règles d’un ou des formulaires personnalisés attaque consiste à exécuter le script PowerShell [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) .  Ce script se connecte à chaque boîte aux lettres dans votre client et exporte toutes les règles et deux fichiers .csv de formulaires.

#### <a name="pre-requisites"></a>Conditions préalables
Vous devez disposer des droits d’un administrateur global pour exécuter le script, car le script se connecte à chaque boîte aux lettres dans la location pour lire les règles et les formulaires.

1. Connectez-vous à l’ordinateur que vous allez exécuter le script avec des droits d’administrateur local.
2. Téléchargez ou copiez le script Get-AllTenantRulesAndForms.ps1 à partir de référentiels dans un dossier à partir duquel vous allez exécuter il.  Le script crée deux fichiers date marqué dans ce dossier, MailboxFormsExport-aaaa-mm-dd.csv et MailboxRulesExport-aaaa-mm-dd.csv.
3. Ouvrez une instance PowerShell en tant qu’administrateur et ouvrez le dossier que vous avez enregistré le script.
4. Exécutez la ligne de commande PowerShell suivante `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interprétation de la sortie

MailboxRulesExport -*aaaa-mm-jj*.csv – examiner les règles (une par ligne) pour les conditions d’action qui incluent des applications ou des fichiers exécutables.
- ActionType (colonne A) – si vous voyez la valeur « ID_ACTION_CUSTOM », la règle est probablement malveillant.
- IsPotentiallyMalicious (colonne D) – si cette valeur est « TRUE », la règle est probablement malveillant.
- ActionCommand (colonne G) – si une application ou un fichier avec un .exe, extension .zip ou une entrée qui fait référence à une URL, qui n’est pas supposé être présent, indique la règle est probablement malveillant.

MailboxFormsExport -*aaaa-mm-jj*.csv – en règle générale, l’utilisation des formulaires personnalisés est très rare.  Si vous trouvez dans ce classeur, vous ouvrez la boîte aux lettres de cet utilisateur et examinez le formulaire proprement dit.  Si votre organisation y n'avez pas placées il intentionnellement, il est probable malveillant.



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Comment arrêter et corriger l’attaque règles Outlook et les formulaires
Si vous trouvez toute preuve d’une de ces attaques, correction est simple, supprimez simplement la règle ou un formulaire à partir de la boîte aux lettres. Vous pouvez le faire avec le client Outlook ou à l’aide de PowerShell à distance pour supprimer des règles.

### <a name="using-outlook"></a>À l’aide d’Outlook
1. Identifiez tous les périphériques de l’utilisateur a utilisé avec Outlook.  Ils devront tous être nettoyé de programmes malveillants potentiels.  Ne pas autoriser l’utilisateur d’ouverture de session et utilisation du courrier électronique jusqu'à ce que tous les périphériques sont nettoyés.
2. Suivez les étapes de [suppression d’une règle](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F) pour chaque périphérique.
3. Si vous ne savez pas la présence d’autres programmes malveillants, mettre et réinstallez tous les logiciels sur l’appareil.  Pour les appareils mobiles, vous pouvez suivre les étapes de fabricants pour réinitialiser le périphérique à l’image d’usine.
4. Installez les dernières versions d’Outlook.  N’oubliez pas que la version actuelle d’Outlook bloque les deux types de cette attaque par défaut.
5. Une fois que toutes les copies hors connexion de la boîte aux lettres ont été supprimées, réinitialiser le mot de passe utilisateur (utilisez une haute qualité) et suivez les étapes de [l’authentification multifacteur le programme d’installation pour les utilisateurs d’Office 365](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6) si MFA n’a pas déjà été activé. Cela garantit que les informations d’identification de l’utilisateur ne sont pas exposées via d’autres moyens (par exemple, l’hameçonnage ou le mot de passe réutiliser).

### <a name="using-powershell"></a>À l’aide de PowerShell
Il existe deux cmdlets PowerShell à distance, que vous pouvez utiliser pour supprimer ou désactiver des règles dangereuses. Suivez les étapes.
 
Étapes de boîtes aux lettres qui se trouvent sur un serveur Exchange

1. Connectez-vous au serveur Exchange à l’aide de PowerShell à distance. Suivez les étapes de [se connecter à l’aide de PowerShell à distance les serveurs Exchange](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps).
2. Si vous souhaitez supprimer complètement une règle unique, plusieurs règles ou toutes les règles d’une utilisation de la boîte aux lettres la [cmdlet Remove-boîte de réception règle ](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)- Utilisez cette option pour supprimer complètement d’un, plusieurs ou toutes les règles de la boîte aux lettres.
3. Si vous souhaitez conserver la règle et son contenu examinés, utilisez la [cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

Étapes de boîtes aux lettres dans Exchange Online
1. Suivez les étapes de [se connecter à Exchange Online à l’aide de PowerShell](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).
2.  Si vous souhaitez supprimer complètement une règle unique, plusieurs règles ou toutes les règles à partir d’une boîte aux lettres, utilisent l' [applet de commande Remove-boîte de réception règle](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps).
3.  Si vous souhaitez conserver la règle et son contenu examinés, utilisez la [cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

## <a name="how-to-minimize-future-attacks"></a>Comment faire pour réduire les attaques à venir

### <a name="first-protect-your-accounts"></a>Premier : protéger vos comptes

Les attaques de formulaires et les règles sont uniquement utilisés par une personne malveillante après leur vol ou violation d’un des comptes de l’utilisateur. Par conséquent, la première étape pour empêcher l’utilisation de ces exploitations par rapport à votre organisation est de façon restrictive protéger vos comptes d’utilisateurs.  Certaines des méthodes plus courantes que les comptes sont déclenchées sont des attaques par hameçonnage ou [projection de mot de passe](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/) .



La meilleure façon pour protéger vos comptes d’utilisateurs et notamment vos comptes d’administrateur, consiste à [configurer l’authentification multifacteur pour les utilisateurs d’Office 365](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).  Vous devez également :
<ol>
    <li>Surveiller la façon dont vos comptes d’utilisateurs sont <a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">accessibles et utilisables</a>. Vous ne pouvez pas empêcher la rupture initiale, mais vous va raccourcir la durée et l’impact de la violation par détecter plus tôt. Vous pouvez utiliser ces : <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">stratégies de sécurité d’application Office 365 dans le nuage</a> à surveiller de comptes et alerte sur l’activité inhabituelle.<ol type="a">
            <li><b>Plusieurs tentatives de connexion ayant échoué</b> Cette stratégie profiles votre environnement et les alertes de déclencheurs lorsque les utilisateurs effectuent plusieurs activités d’ouverture de session ayant échoué en une seule session par rapport à la planification apprise, ce qui peut indiquer une violation de la tentative.</li>
            <li><b>Il est impossible de voyage</b> - Cette stratégie, les profils de votre environnement et déclenche des alertes lorsque des activités sont détectées dans le même utilisateur dans des emplacements différents dans un délai plus court que le temps de trajet prévu entre les deux emplacements. Cela peut indiquer qu’un autre utilisateur utilise les mêmes informations d’identification. Détection de ce comportement anormal nécessite une période d’apprentissage initiale de sept jours au cours de laquelle il a eu le modèle d’activité d’un nouvel utilisateur.</li>
            <li><b>Inhabituelle empruntée activité (par utilisateur)</b> - Cette stratégie, les profils de votre environnement et déclenche des alertes lorsque les utilisateurs effectuent plusieurs activités représentées dans une seule session par rapport à la ligne de base appris, qui peut indiquer une violation de la tentative.</li>
        </ol>
    </li>
    <li>Tirer parti des outils tels que le <a href="https://securescore.office.com/">Score de sécuriser Office 365</a> pour gérer les configurations de compte de sécurité et les comportements. 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>Deuxième : Conserver vos clients Outlook en cours
Entièrement mis à jour et les correctifs des versions d’Outlook 2013 et 2016 désactiver l’action de règle/formulaire « Démarrer l’Application » par défaut.  Cela permet de garantir que, même si une personne malveillante atteinte du compte, les actions de règle et de formulaire seront bloquées.  Vous pouvez installer les correctifs de sécurité et les dernières mises à jour en suivant les étapes décrites dans les [mises à jour Office installer](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5).

Voici les versions de correctif pour votre Outlook 2013 et les clients de 2016 :
- Outlook 2013 : 15.0.4937.1000 ou supérieur
- Outlook 2016 : 16.0.4534.1001 ou supérieur

Pour plus d’informations sur les correctifs de sécurité individuels, consultez :

- [Correctif de sécurité pour Outlook 2013](https://support.microsoft.com/en-us/help/3191938) 
- [Correctif de sécurité Outlook 2016](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>Troisième : Surveiller vos clients Outlook
Notez que même avec les correctifs et mises à jour installées, il est possible, pour une personne malveillante modifier la configuration de l’ordinateur local pour réactiver le comportement « Démarrer l’Application ». Vous pouvez utiliser la [Gestion avancée des stratégies de groupe](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/) pour surveiller et appliquer les stratégies de l’ordinateur local sur vos clients.  
Vous pouvez pour voir si « Démarrer l’Application » a été réactivée via une substitution dans le Registre en utilisant les informations sur la [façon d’afficher le Registre système à l’aide de versions 64 bits de Windows](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows).  Vérifiez ces sous-clés : 

- Outlook 2016 : HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013 : HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

Recherchez la clé EnableUnsafeClientMailRules. Si elle est présente et est défini sur 1, le correctif de sécurité Outlook a été remplacé et l’ordinateur est vulnérable à l’attaque/règles du formulaire. Si la valeur est 0, l’action « Démarrer l’Application » est désactivée.  Si la version mise à jour et correctif d’Outlook est installée et que cette clé de Registre n’est pas présente, un système n’est pas vulnérable aux attaques de ces.

Clients avec des installations d’Exchange sur site envisagez le blocage des versions antérieures d’Outlook qui n’ont pas de correctifs disponibles. Vous trouverez plus d’informations sur cette procédure dans l’article [client Outlook de configurer le blocage](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Sécuriser Office 365 comme une sécurité pro
Votre abonnement Office 365 est fourni avec un ensemble de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs puissantes.  Utiliser le [Guide de sécurité Office 365 : principaux des priorités pour les 30 premiers jours, 90 jours et au-delà](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) à mettre en œuvre les meilleures pratiques pour la sécurisation de votre client Office 365 de Microsoft.
- Tâches à accomplir dans les 30 jours.  Ces ont une incidence immédiate et sont faible impact à vos utilisateurs.
- Tâches à accomplir dans 90 jours. Ces prennent un peu plus de temps pour planifier et implémenter mais sensiblement améliorer votre sécurité.
- Au-delà de 90 jours. Ces améliorations créer votre premier travail 90 jours.

## <a name="see-also"></a>Voir aussi :
- [Règles Outlook malveillant](https://silentbreaksecurity.com/malicious-outlook-rules/) par SilentBreak sécurité Post sur vecteur de règles fournit une analyse détaillée de la façon des règles d’Outlook. 
- [Le protocole MAPI sur HTTP et Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) sur le blog de Sensepost sur Mailrule Pwnage présente un outil appelé règle qui vous permet d’exploiter des boîtes aux lettres via les règles d’Outlook.
- [Shells et formulaires outlook](https://sensepost.com/blog/2017/outlook-forms-and-shells/) sur le blog de Sensepost sur vecteur de menace de formulaires. 
- [Codebase de règle](https://github.com/sensepost/ruler)
- [Indicateurs de règle de compromis](https://github.com/sensepost/notruler/blob/master/iocs.md)