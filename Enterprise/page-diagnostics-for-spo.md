---
title: Utilisez l’outil de diagnostic de la Page pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Utilisez les tests de diagnostic Page outil SharePoint afin d’analyser vos pages classique contre les meilleures pratiques recommandées pour SharePoint Online.
ms.openlocfilehash: 1524befc0003006cfab9100aafc7d3deda2a37d2
ms.sourcegitcommit: 5be99683fb2de87f723264c8a1123451d31ea43b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26253615"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utilisez l’outil de diagnostic de la Page pour SharePoint Online

Cet article décrit comment vous pouvez utiliser l’outil de Diagnostic de la Page pour analyser les pages de publication classique et les pages des sites d’équipes classique, par rapport à un sous-ensemble des pratiques recommandées dans **SharePoint Online**. 
  
Sites d’équipe qui n’ont pas activée la publication ne peut pas faire utiliser CDN, mais toutes les autres règles sont applicables. Publication ajoute une surcharge supplémentaire afin de ne pas activer la publication pour obtenir la fonctionnalité CDN comme il un impact négatif sur les temps de chargement de page.

**Remarque que V1.05 a été publié Veuillez mettre à jour votre extension, si vous avez déjà installé**. Si vous ne savez pas quelle version que vous avez puis cliquez sur le « Sur » pour vérifier qu’il.
  
> [!IMPORTANT]
> L’outil de diagnostic de la Page ne s’exécutera pas par rapport à des bibliothèques de documents ou des pages de système, comme l’outil est conçu pour passer en revue les pages du site SharePoint. Une page *allitems.aspx* est un système. Si vous essayez d’exécuter l’outil sur une page de système, vous recevrez un message indiquant, « cette application doit s’exécuter uniquement sur les pages SharePoint. »<br/> ![Doit s’exécuter sur une page SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Cela n’est pas une erreur dans l’outil car il n’existe aucune valeur pour l’évaluation des bibliothèques ou des pages de système. Accédez à une page de SharePoint non-système pour utiliser l’outil. Si cela se produit sur une page SharePoint, vérifiez la page maître comme nous l’avons vu clients supprimer le SharePoint MetaTags et ensuite la page n’est plus une page SharePoint. Si vous souhaitez envoyer des commentaires sur l’outil cliquez sur l’onglet à propos et suivre la [liaison de commentaires](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installer l’outil de Diagnostic de la Page

> [!IMPORTANT]
> Microsoft ne lit pas les données ou les sites Web que vous visitez et nous ne pas capturent des informations personnelles, les informations de site Web ou télécharger avec cet outil. Les seules informations enregistrées par l’outil sont le nom du client, count et si l’option de journalisation de prise en charge a été utilisée lors de l’exécution de l’outil de la règle. Ces informations sont destinées à analyser les problèmes rencontrés par nos clients et de garantir que la fonctionnalité de journalisation de prise en charge n’est pas détournement de Microsoft.

1. À l’aide d’un navigateur Chrome, directement, ouvrez le [lien vers l’outil](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) ou ouvrez la recherche dans le [Stockage Web du navigateur Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) et installer l’extension de navigateur. Examinez la politique de confidentialité utilisateur fourni dans la page description dans le magasin. Lorsque vous ajoutez l’outil à votre navigateur, vous verrez ce qui suit Notez des autorisations.<br/>![Autorisations du magasin de chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Cette notification est en place, car une page peut contenir du contenu à partir d’emplacements en dehors de SharePoint, selon les composants WebPart et les personnalisations dans la page. Cela signifie que l’outil lira les requêtes et réponses lorsque l’utilisateur clique sur le bouton Démarrer et uniquement pour l’onglet SharePoint actif où l’outil est en cours d’exécution. Ces informations sont capturées localement par le navigateur web et est disponibles par le biais de l’exportation pour créer un lien JSON dans l’outil. **Les informations ne sont pas envoyées à ou capturées par Microsoft.** (L’outil respecte le Microsoft Privacy stratégie accessible [ici](https://go.microsoft.com/fwlink/p/?linkid=857875).)<br/><br/>La fonctionnalité « Exporter au format JSON » dans l’outil est également pourquoi l’autorisation « Gestion des téléchargements » est nécessaire. Suivez votre confidentialité de la société avant de partager le fichier JSON en dehors de votre organisation, comme les résultats contiennent des URL et qui peut être classée en tant que PII (informations d’identification personnelle).
    
2. (Cette étape est facultative) Si vous souhaitez utiliser l’outil en mode incognito Chrome, accédez à l’extension et cliquez sur **Autoriser dans incognito**.
    
3. Accédez à la page de publication classique SharePoint sur SharePoint Online que vous souhaitez consulter. Nous avons autorisé pour « chargement différé » des éléments dans les pages ; Par conséquent, l' **outil ne s’arrête pas automatiquement**. Si vous souhaitez arrêter la collection, vous pouvez cliquer sur **Arrêter**. (Il s’agit par défaut pour répondre à tous les scénarios de chargement de page.) Avant de cliquer sur **Arrêter**, assurez-vous que les données de suivi réseau sont terminées. Dans le cas contraire, vous aurez un suivi partiel. En outre, l’outil est une Extension de navigateur et l’ouverture de plusieurs onglets ou windows autorise uniquement une seule instance active de l’outil à exécuter en même temps. Il s’agit d’une limitation des extensions dans le navigateur. 
  
4. Cliquez sur le logo de l’Extension ![Page Diagnostics pour logo SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) pour charger l’outil et vous est présentées avec la fenêtre contextuelle extension suivantes :<br/> ![Outil de diagnostic de la page contextuelle](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Démarrer et arrêter follow opérations le concept de base de lorsque vous cliquez sur Démarrer que vont et collection va commencer.

Lisez les sections suivantes pour en savoir plus sur les informations fournies dans l’outil.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Vous verrez dans l’outil de diagnostic de la Page
    
1. Le lien **sur** fournira des conseils d’ordre général et des détails concernant l’outil, y compris un lien à cet article. Il inclut également un lien direct vers des recommandations sur les performances de SharePoint, une notification de tierce partie et une option pour fournir des commentaires à propos de l’outil. 
    
2. Les détails de **l’ID de corrélation, SPRequestDuration, SPIISLatency**, **temps de chargement de Page**et **URL** sont d’information et peuvent être utilisés à des fins de quelques. 
    
  - **CorrelationID** est un élément important lorsque vous travaillez avec les équipes de support technique Microsoft, tel qu’il leur permet d’extraire des données de diagnostic supplémentaires. 
    
  - **SPRequestDuration** est le temps nécessaire pour traiter la page du serveur. Si ce temps est long, il ne signifie pas nécessairement que le serveur effectuait mal, mais peut également refléter le nombre d’appels et charger mis à la page sur le serveur, par exemple Navigation structurelle, les images de grande taille, beaucoup d’appels API pourrait contribuer à plus de temps serveur . 
    
  - **SPIISLatency** est la durée en millisecondes requis sur le serveur frontal Web lorsqu’il reçoit la demande de chargement de la page. Ceci est un indicateur de latence pour démarrer le traitement de la page et n’inclut pas le temps nécessaire pour l’application web répondre. 
    
  - **Temps de chargement de page** est le temps enregistré par la page à partir de l’heure de la demande à la date de la réponse a été reçue et lu par le navigateur. Temps supplémentaire est affectée par les performances de l’ordinateur et le temps que nécessaire pour le navigateur à charger. 
    
  - L' **URL** (Uniform Resource Locator) est l’adresse web de la page actuelle. 
    
3. Répertorie les règles de l' [onglet **Diagnostic** ](#how-to-use-the-diagnostic-tab) et si un des sont marqués avec un rouge ![croisée](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), puis il existe des problèmes identifiés dans la page.<br/>Chaque règle possède son propre lien « plus d’informations » que vous cliquez sur si un élément est rouge. Qui vous dirige vers les détails de cette règle et comment résoudre le problème.<br/>![Diagnostics Red - règle open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Un [onglet de **suivi réseau** ](#how-to-use-the-network-trace-tab) fournit plus d’informations sur la page Créer des demandes et réponses.

## <a name="how-to-use-the-diagnostic-tab"></a>Comment utiliser l’onglet Diagnostics

1. **Vérification en cours d’exécution en tant qu’utilisateur Standard**  Vérification des performances de la page ne doit pas être réalisée connecté en tant qu’un compte de Service, administrateur ou administrateur de Collection de sites ou n’importe quel compte avec des privilèges élevés. Fonctionnalités et les scripts supplémentaires sont chargés spécifiquement pour ces types de comptes, afin que les résultats ne seront pas une représentation réelle de performances de la page.
    
2. **Vérifier les demandes pour SharePoint**  La quantité de données et des demandes adressées au serveur doit être limitée comme une page surchargée subissent des performances médiocres. Ce contrôle vérifie le nombre de demandes effectuées dans SharePoint et signalera lorsque les demandes dépassent 6 demandes. La plupart des requêtes doit être mis en cache et par conséquent pas appelé pour chaque chargement de la page. Cache doit être configuré et utilisé au moins 15 minutes réduire le volume d’appels à une page à chaque utilisateur. Il s’agit d’un problème courant et dans la plupart des cas données modifie uniquement tous les jours, mais la page vérifie et extrait les données chaque fois pour chaque page pour chaque utilisateur qui est souvent inutile.
    
3. **Vérifiez à l’aide du CDN**  Réseaux de distribution de contenu (CDN) ont été fournies par Microsoft et ceux qui sont référencés qu'ici sont les réseaux remise SharePoint Online contenu. Il existe plusieurs types disponibles ainsi que les différents services CDN comme CDN SharePoint, puis CDN dans Azure. [Utilisez les instructions suivantes](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Vérifier les tailles de grande Image**  Images doivent être optimisés pour site web en utilisant une meilleure types web comme le format PNG. Rendus d’image doit également être utilisé et est disponibles dans SharePoint directement. Images / images supérieures à 100 Ko sont mis en surbrillance comme non optimisé pour site web. [Utilisez les conseils suivants pour optimiser les performances des images](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Recherchez la Navigation structurelle**  Navigation structurelle a été conçue pour une utilisation dans SharePoint local où le cache d’objets peut être utilisée. Navigation structurelle n’est pas recommandée pour une utilisation dans SharePoint Online et doit être modifiée pour la Navigation gérée ou d’un fournisseur personnalisé. [Utilisez les instructions suivantes pour optimiser la navigation.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Recherchez le composant WebPart CENTI** (CENTI - composant WebPart requête de contenu)  Le composant WebPart requête de contenu génère une charge élevée de SQL comme il parcourt tous les éléments de la requête pour chaque chargement de page, pour chaque utilisateur. Contrairement à une installation locale, il n’existe aucun cache disponible pour limiter le nombre de requêtes nécessaires pour remplir ce composant WebPart. En tant que telles CENTI lent et a un impact sur les performances globales de page c’est pourquoi il ne doit pas être utilisé. Utilisez le composant WebPart de recherche de contenu (CSWP) comme remplacement pour le composant WebPart de requête de contenu. [Utilisez les instructions suivantes relatives au composant WebPart de recherche contenu](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>L’utilisation de l’onglet suivi du réseau
    
L’onglet **Trace réseau** fournit des informations détaillées sur les demandes pour créer la page, ainsi que les réponses reçues. 

1. **Recherchez les temps de chargement des éléments marqués comme rouge**. Les performances de chaque demande et réponse sont couleur, en fonction de leur impact sur les performances globales de la page comme suit :
- Vert : \< 500 ms
- Jaune : 500-1000ms
- Rouge : \> 1000ms
<br/>![Suivi du réseau](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/>Dans l’image ci-dessus, l’élément rouge se rapporte à la page par défaut. Il affiche toujours rouge, sauf si la page se charge dans \< 1000ms (inférieur à 1 seconde).

2. **Temps de chargement d’élément de test**. Dans certains cas, il n’y aura aucun indicateur de temps ou la couleur, car les éléments ont déjà été mis en cache par le navigateur. Pour tester correctement, ouvrez la page, désactivez le cache du navigateur, puis cliquez sur **Démarrer** qui s’ensuit un chargement de page « à froid » et le chargement de page initial reflète la valeur true. Puis être comparé à la charge de la page « à chaud » comme qui aideront également à déterminer quels éléments sont en cours mis en cache dans la page. 
    
3. **Détails pertinents partager avec d’autres personnes qui peuvent aider à étudier des problèmes**. Pour partager les informations fournies dans l’outil avec vos développeurs ou une personne du support technique ou le plus d’informations, cliquez sur **Exporter vers JSON** (comme illustré dans l’image ci-dessus). Vous permettre de télécharger les résultats, visibles avec une visionneuse de fichier JSON.

> [!IMPORTANT]
> Ces résultats contiennent des URL et qui peut être considéré comme PII (informations d’identification personnelle). Veillez à suivre les instructions de votre organisation avant de distribuer ces informations. 

## <a name="engaging-with-microsoft-support"></a>Soumissions avec prise en charge de Microsoft
   
Nous avons inclus une **fonctionnalité au niveau de prise en charge de Microsoft** qui ne doit être utilisé que lorsque vous travaillez directement sur un cas de prise en charge pour les performances. Utilisation de cette fonctionnalité ne fournira aucun avantage vous lorsqu’elle est utilisée sans notre équipe de Support. Il est en fait que la page effectuer lentement et continuer à utiliser la fonctionnalité peut être considéré comme « détourner » du service. Il n’existe aucune autre information lors de l’utilisation de cette fonctionnalité dans l’outil lorsque les informations supplémentaires sont ajoutées à la journalisation dans le service. 

Aucune modification n’est visible, sauf que vous serez ainsi averti que vous avez activé cette fonction et votre page va considérablement réduire les performances par 2 à 3 fois ralentir les performances, tout en qui est activé. Il est pertinente pour la page spécifique et de la session active. Pour cette raison, il doit être utilisé avec modération et uniquement lorsque activement commencé avec notre équipe de support technique.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Pour activer la fonctionnalité de niveau de Support Microsoft

1. Ouvrez l’outil de diagnostic de la Page.
2. Sur votre clavier, appuyez sur ALT-MAJ-L. **Activer la journalisation au niveau de la prise en charge**s’affiche. 
3. Activez la case à cocher, puis cliquez sur **Démarrer** pour recharger la page et de générer la journalisation détaillée de la prise en charge à analyser.<br/>![Option de prise en charge est activée](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Un élément important pour ce est l’ID de corrélation que l’équipe de Support utilisera ensuite ce numéro pour extraire les informations nécessaires. Copiez l’ID de corrélation (en haut de l’outil de diagnostic de la Page) et qui fournissent pour prendre en charge comme ils ne peuvent pas effectuer le travail requis sans l’ID terminée.
    
## <a name="related-topics"></a>Rubriques connexes

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)
