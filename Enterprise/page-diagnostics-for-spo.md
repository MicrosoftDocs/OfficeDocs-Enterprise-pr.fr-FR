---
title: Utilisez l’outil de diagnostic de la Page pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
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
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540566"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Utilisez l’outil de diagnostic de la Page pour SharePoint Online

Cet article décrit comment vous pouvez utiliser l’outil de Diagnostic de la Page pour analyser les pages de publication classique et les pages des sites d’équipes classique, par rapport à un sous-ensemble des pratiques recommandées dans **SharePoint Online**. 
  
Sites d’équipe qui n’ont pas activée la publication ne peut pas faire utiliser CDN, mais toutes les autres règles sont applicables. Publication ajoute une surcharge supplémentaire afin de ne pas activer la publication pour obtenir la fonctionnalité CDN comme il un impact négatif sur les temps de chargement de page.
  
> [!IMPORTANT]
> L’outil de diagnostic de la Page ne s’exécutera pas par rapport à des bibliothèques de documents ou des pages de système, comme l’outil est conçu pour passer en revue les pages du site SharePoint. Une page *allitems.aspx* est un système. Si vous essayez d’exécuter l’outil sur une page de système, vous obtiendrez un message indiquant, « cette application doit s’exécuter uniquement sur les pages SharePoint. » > ![doit s’exécuter sur une page SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> Cela n’est pas une erreur dans l’outil car il n’existe aucune valeur pour l’évaluation des bibliothèques ou des pages de système. Accédez à une page de SharePoint non-système pour utiliser l’outil. Si vous souhaitez envoyer des commentaires sur l’outil cliquez sur l’onglet à propos et suivre la [liaison de commentaires](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>Comment utiliser l’outil de Diagnostic de la Page
<a name="useit"> </a>

1. À l’aide d’un navigateur Chrome, directement, ouvrez le [lien vers l’outil](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) ou ouvrez la recherche dans le [Stockage Web du navigateur Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) et installer l’extension de navigateur. 
    
    Examinez la politique de confidentialité utilisateur fourni dans la page description dans le magasin.
    
    Lorsque vous ajoutez l’outil à votre navigateur, vous verrez ce qui suit Notez des autorisations.
    
    ![Autorisations du magasin de chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    Cette notification est en place, car une page peut contenir du contenu à partir d’emplacements en dehors de SharePoint, selon les composants WebPart et les personnalisations dans la page. Cela signifie que l’outil lira les requêtes et réponses lorsque l’utilisateur clique sur le bouton Démarrer et uniquement pour l’onglet SharePoint actif où l’outil est en cours d’exécution. Ces informations sont capturées localement par le navigateur web et est disponibles par le biais de l’exportation pour créer un lien JSON dans l’outil. **Les informations ne sont pas envoyées à ou capturées par Microsoft.**
    
    > [!IMPORTANT]
    > Microsoft ne lit pas les données ou les sites Web que vous visitez et nous ne pas capturent des informations personnelles, les informations de site Web ou télécharger avec cet outil. Les seules informations enregistrées par l’outil sont le nom du client, count et si l’option de journalisation de prise en charge a été utilisée lors de l’exécution de l’outil de la règle. Ces informations sont destinées à analyser les problèmes rencontrés par nos clients et de garantir que la fonctionnalité de journalisation de prise en charge n’est pas détournement de Microsoft.
  
L’outil doit respecter le Microsoft Privacy stratégie accessible [ici](https://go.microsoft.com/fwlink/p/?linkid=857875). 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. (Facultatif) Si vous souhaitez utiliser l’outil en mode incognito Chrome, accédez à l’extension et cliquez sur « Autoriser dans incognito ».
    
3. Accédez à la page de publication classique SharePoint sur SharePoint Online que vous souhaitez consulter.
    
    > [!IMPORTANT]
    > Nous avons autorisé pour « chargement différé » des éléments dans les pages ; Par conséquent, l' **outil ne s’arrête pas automatiquement**. Si vous souhaitez arrêter la collection, vous pouvez cliquer sur **Arrêter**. (Il s’agit par défaut pour répondre à tous les scénarios de chargement de page) 
  
Avant de cliquer sur **Arrêter**, assurez-vous que les données de suivi réseau sont terminées. Dans le cas contraire, vous aurez un suivi partiel. 
  
En outre, l’outil est une Extension de navigateur et l’ouverture de plusieurs onglets ou windows autorise uniquement une seule instance active de l’outil à exécuter en même temps. Il s’agit d’une limitation des extensions dans le navigateur. 
  
4. Cliquez sur le logo de l’Extension ![Page Diagnostics pour logo SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) pour charger l’outil et vous est présentées avec la fenêtre contextuelle extension suivantes : 
    
    ![Outil de diagnostic de la page contextuelle](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    Démarrer et arrêter follow opérations le concept de base de lorsque vous cliquez sur Démarrer que vont et collection va commencer.
    
5. Le premier lien est le lien **sur** et fournit des conseils d’ordre général et les détails concernant l’outil, y compris un lien à cet article. Il inclut également un lien direct vers des recommandations sur les performances de SharePoint, une notification de tierce partie et une option pour fournir des commentaires à propos de l’outil. 
    
6. Consultez les informations de **temps et des URL de Page charge** **ID de corrélation, SPRequestDuration, SPIISLatency** . (Cette section est informatif et peut être utilisée à des fins de quelques.) 
    
  - **CorrelationID** est un élément important lorsque vous travaillez avec les équipes de support technique Microsoft, tel qu’il leur permet d’extraire des données de diagnostic supplémentaires. 
    
  - **SPRequestDuration** est le temps nécessaire pour traiter la page du serveur. Si ce temps est long, il ne signifie pas nécessairement que le serveur effectuait mal, mais peut également refléter le nombre d’appels et charger mis à la page sur le serveur, par exemple Navigation structurelle, les images de grande taille, beaucoup d’appels API pourrait contribuer à plus de temps serveur . 
    
  - **SPIISLatency** est la durée en millisecondes requis sur le serveur frontal Web lorsqu’il reçoit la demande de chargement de la page. Ceci est un indicateur de latence pour démarrer le traitement de la page et n’inclut pas le temps nécessaire pour l’application web répondre. 
    
  - **Temps de chargement de page** est le temps enregistré par la page à partir de l’heure de la demande à la date de la réponse a été reçue et lu par le navigateur. Temps supplémentaire est affectée par les performances de l’ordinateur et le temps que nécessaire pour le navigateur à charger. 
    
  - L' **URL** (Uniform Resource Locator) est l’adresse web de la page actuelle. 
    
7. Répertorie les règles de l' **onglet Diagnostic** et si un des sont marqués avec un rouge ![croisée](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), puis il existe des problèmes identifiés dans la page.
    
    Chaque règle possède son propre lien « informations supplémentaires » si vous cliquez dessus lorsqu’il est rouge. Qui vous dirige vers les détails de cette règle et comment résoudre le problème.
    
    ![Diagnostics Red - règle open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. Vérifier l’utilisateur en cours d’exécution en Standard
  
Vérification des performances de la page ne doit pas être réalisée connecté en tant qu’un compte de Service, un administrateur ou un administrateur de Collection de sites c'est-à-dire un compte avec des privilèges élevés. Fonctionnalités et autres scripts est chargés spécifiquement pour ces types de comptes et ne permet pas à une représentation réelle des performances de la page.
    
2. Demandes de contrôle pour SharePoint
  
La quantité de données et des demandes adressées au serveur doit être limitée comme une page surchargée subissent des performances médiocres. Ce contrôle vérifie le nombre de demandes effectuées dans SharePoint et signalera lorsque les demandes dépassent 6 demandes. La plupart des requêtes doit être mis en cache et par conséquent pas appelé pour chaque chargement de la page. Cache doit être configuré et utilisé au moins 15 minutes réduire le volume d’appels à une page à chaque utilisateur. Il s’agit d’un problème courant et dans la plupart des cas données modifie uniquement tous les jours, mais la page vérifie et extrait les données chaque fois pour chaque page pour chaque utilisateur qui est souvent inutile.
    
3. Vérifiez à l’aide du CDN
  
Réseaux de distribution de contenu ont été fournies par Microsoft et ceux qui sont référencés qu'ici sont les réseaux remise SharePoint Online contenu. Il existe plusieurs types disponibles ainsi que les différents services CDN comme CDN SharePoint, puis CDN dans Azure. [Utilisez les instructions suivantes](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. Vérification des tailles de grande Image
  
Images doivent être optimisés pour site web en utilisant une meilleure types web comme le format PNG. Rendus d’image doit également être utilisé et est disponibles dans SharePoint directement. Images / images supérieures à 100 Ko sont mis en surbrillance comme non optimisé pour site web. [Utilisez les conseils suivants pour optimiser les performances des images](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. Vérification de Navigation structurelle
  
Navigation structurelle a été conçue pour une utilisation dans SharePoint local où le cache d’objets peut être utilisée. Navigation structurelle n’est pas recommandée pour une utilisation dans SharePoint Online et doit être modifiée pour la Navigation gérée ou d’un fournisseur personnalisé. [Utilisez les instructions suivantes pour optimiser la navigation.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. Recherchez CENTI WebPart (CENTI - composant WebPart requête de contenu)
  
Le composant WebPart requête de contenu génère une charge élevée de SQL comme il parcourt tous les éléments de la requête pour chaque chargement de page, pour chaque utilisateur. Contrairement à une installation locale, il n’existe aucun cache disponible pour limiter le nombre de requêtes nécessaires pour remplir ce composant WebPart. En tant que telles CENTI lent et a un impact sur les performances globales de page c’est pourquoi il ne doit pas être utilisé. Utilisez le composant WebPart de recherche de contenu (CSWP) comme remplacement pour le composant WebPart de requête de contenu. [Utilisez les instructions suivantes relatives au composant WebPart de recherche contenu](https://go.microsoft.com/fwlink/?linkid=873245).
    
8. Fournit l' **onglet Trace réseau** *** des informations détaillées sur les demandes pour créer la page, ainsi que les réponses reçues. Les performances de chaque demande et réponse sont codés par couleur en fonction de leur impact sur les performances globales de la page c'est-à-dire vert \< 500 ms, jaune rouge et 500-1000ms \> 1000ms. 
    
    Cet onglet est une exportation à l’option JSON si vous souhaitez télécharger et partager les détails de la demande et la réponse.
    
    > [!IMPORTANT]
    > Pointez sur l’URL de raccourci pour afficher l’URL complète. 
  
    ![Suivi du réseau](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    Dans cette image rouge correspond à la page lui-même et qui s’affichera toujours rouge, sauf si la page se charge dans \< 1000ms (c'est-à-dire 1 seconde).
    
    Dans certains cas, *il n’y aura aucun indicateur de temps ou la couleur, car les éléments ont déjà été mis en cache par le navigateur* . Pour tester correctement, ouvrez la page, désactivez le cache du navigateur, puis cliquez sur **Démarrer** qui s’ensuit un chargement de page « à froid » et le chargement de page initial reflète la valeur true. Puis être comparé à la charge de la page « à chaud » comme qui aideront également à déterminer quels éléments sont en cours mis en cache dans la page. 
    
9. Si vous souhaitez partager ces informations ou des informations avec vos développeurs ou une personne de la prise en charge vous pouvez cliquer sur « Exporter au format JSON » en fonction de l’image ci-dessus, puis qui télécharge les résultats. Veuillez noter que le fichier peut ensuite être ouvert à l’aide d’une visionneuse de fichier JSON.
    
    > [!IMPORTANT]
    > Ces résultats contiendra les URL et par conséquent contient des informations d’identification personnelle (informations d’identification personnelle) et vous devez suivre les instructions de votre société avant de distribuer ces informations. 
  
10. Nous avons inclus une **fonctionnalité au niveau de prise en charge de Microsoft** qui ne doit être utilisé que lorsque vous travaillez directement sur un cas de prise en charge pour les performances. Utilisation de cette fonctionnalité ne fournira aucun avantage vous lorsqu’elle est utilisée sans notre équipe de Support. Il est en fait que la page effectuer lentement et continuer à utiliser la fonctionnalité peut être considéré comme « détourner » du service. Il n’existe aucune autre information lors de l’utilisation de cette fonctionnalité dans l’outil lorsque les informations supplémentaires sont ajoutées à la journalisation dans le service. 
    
    Aucune modification n’est visible, sauf que vous serez ainsi averti que vous avez activé cette fonction et votre page va considérablement réduire les performances par 2 à 3 fois ralentir les performances, tout en qui est activé. Il est pertinente pour la page spécifique et de la session active. Pour cette raison, il doit être utilisé avec modération et uniquement lorsque activement commencé avec notre équipe de support technique.
    
    Pour activer la fonctionnalité ouvrez l’outil et utiliser ALT-MAJ + L, qui affiche ensuite « activer la journalisation au niveau de la prise en charge ». Cliquez sur que la case à cocher, puis cliquez sur démarrent pour recharger la page et de générer la journalisation détaillée pour la prise en charge à analyser.
    
    ![Option de prise en charge est activée](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    Un élément important pour ce est l’ID de corrélation que l’équipe de Support utilisera ensuite ce numéro pour extraire les informations nécessaires. Copiez l’ID de corrélation et qui fournissent pour prendre en charge comme ils ne peuvent pas effectuer le travail requis sans l’ID terminée.
    

