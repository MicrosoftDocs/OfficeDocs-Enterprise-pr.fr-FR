---
title: Vérifier l'état du service Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Afficher l’état d’intégrité des services Office 365 avant d’appeler la prise en charge pour déterminer s’il existe une interruption de service Active
ms.openlocfilehash: 67595bddaed23222d09c0e7f6f5353b764722f83
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071220"
---
# <a name="how-to-check-office-365-service-health"></a>Vérifier l'état du service Office 365

Vous pouvez afficher l’état de santé d’Office 365, de Yammer, de Microsoft Dynamics CRM et des services Cloud Microsoft Intune sur la page d' **État du service** Office 365 dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting. 

Si vous ne parvenez pas à vous connecter au service portail de service, vous pouvez utiliser la [page État du service](https://status.office365.com) pour vérifier les problèmes connus qui vous empêchent de vous connecter à votre client.
  
### <a name="how-to-check-service-health"></a>Vérifier l'état du service

1. Accédez à [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) et connectez-vous avec un compte d'administrateur. 
    
    > [!NOTE]
    > Les personnes dotées d'un rôle d'administrateur général ou d'administrateur de service peuvent afficher l'état du service. Pour afficher l'état du service, les administrateurs Exchange, SharePoint et Skype Entreprise doivent aussi disposer d'un rôle d'administrateur portant sur ce service.
  
2. Pour ouvrir l’état du service, dans le centre d’administration, accédez à intégrité du**service**d' **intégrité** > ou cliquez sur la carte d' **intégrité des services** dans le tableau de **bord d’accueil**. La carte du tableau de bord indique s'il existe un problème lié au service actif et mène à la page détaillée d'état du service.
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. L'état d'intégrité de chaque service cloud apparaît dans un tableau avec une icône pour indiquer les différents états possibles.
    
> [!TIP]
> Vous pouvez également utiliser l'[application Office 365 Admin](https://go.microsoft.com/fwlink/p/?linkid=627216) sur votre appareil mobile pour afficher l'état du service, ce qui constitue un excellent moyen de vous tenir informé des notifications Push. 
  
### <a name="view-details-of-posted-service-health"></a>Afficher les détails relatifs à l'état du service publié

Dans l'affichage par défaut, tous les services et leur état d'intégrité actuel sont affichés. Pour filtrer votre vue sur les services rencontrant actuellement un incident, sélectionnez **incidents** dans la barre ombrée sur la gauche. La sélection des **avis** affiche uniquement les services pour lesquels un avis a déjà été publié. Dans l’affichage **tous les services** , cliquez sur l’état du service affiché pour ouvrir une vue récapitulative de l’avis ou de l’incident. 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
Le récapitulatif de l'avis ou de l'incident fournit les informations suivantes : 
  
![Capture d’écran des champs d’un avis de service](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Identifiant et récapitulatif du problème.
    
2. État actuel. Reportez-vous aux définitions d'état de cet article pour plus d'informations sur chaque état possible.
    
3. Description de la manière dont ce problème peut affecter les utilisateurs.
    
4. Heure à laquelle le problème s'est manifesté pour la première fois et heure à laquelle le message d'état du service a été mis à jour. Pendant toute la durée d'un problème, nous publions de fréquents messages pour vous informer de notre progression à y remédier.
    
5. Sélectionnez le lien **Afficher les détails** pour afficher plus d'informations sur ce problème, y compris l'historique de tous les messages publiés lors de sa résolution. 
    
### <a name="translate-service-health-details"></a>Traduire les détails d'état du service

Les explications relatives à l'état du service étant publiées en temps réel, elles ne sont pas traduites automatiquement dans votre langue, et les détails d'un événement de service sont uniquement disponibles en anglais. Pour traduire ces explications, procédez comme suit :
  
1. Accédez à [Translator](https://www.bing.com/translator/).
    
2. Sur la page **État du Service**, sélectionnez un avis ou un incident. Sous **Afficher les détails**, copiez le texte relatif au problème.
    
3. Dans Translator, collez le texte, puis sélectionnez **Traduire**.
    
### <a name="definitions"></a>Définitions

En règle générale, les services apparaissent comme intègres, sans autres informations. Lorsqu'un service présente un problème, ce problème est identifié sous forme d'avis ou d'incident et son état actuel s'affiche.
  
> [!TIP]
> Les événements de maintenance planifiée ne s'affichent pas dans l'état du service. Le **Centre de messages** vous permet de suivre les événements de maintenance planifiée. Filtrez les messages par Planification des modifications pour connaître le moment où une modification interviendra, son effet et comment vous y préparer. Pour plus d'informations, voir [Centre de messages dans Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093). 
  
### <a name="incidents-and-advisories"></a>Incidents et avis

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Un service accompagné d'un avis indique que nous sommes conscients du problème qui affecte certains utilisateurs, mais que ce service est toujours disponible. Un avis propose souvent une solution de contournement du problème, qui peut intermittent ou limité en termes d'impact sur les utilisateurs.  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Si un service présente un incident actif, cela signifie qu'il s'agit d'un problème critique et que le service ou une de ses fonctions principales n'est pas disponible. Par exemple, les utilisateurs peuvent ne pas être en mesure d'envoyer et de recevoir des e-mails ni de se connecter. Les incidents ont un impact significatif sur les utilisateurs. En cas d'incident, nous publions des mises à jour relatives à son examen, aux efforts déployés pour y remédier, et sa résolution apparaît dans le tableau de bord d'état du service.  <br/> |
   
### <a name="status-definitions"></a>Définitions des états

|**État**|**Définition**|
|:-----|:-----|
|**Examen en cours** | Nous sommes conscients d'un problème potentiel et recueillons des informations sur ce problème et son impact. |
|**Dégradation du service** | Nous avons identifié un problème susceptible d'affecter l'utilisation d'un service ou d'une fonctionnalité. Cet état peut s'afficher si un service s'avère plus lent qu'habituellement, s'il présente des interruptions intermittentes ou si une fonctionnalité est défaillante, par exemple. |
|**Interruption du service** | Cet état s'affiche si nous identifions un problème qui affecte la capacité des utilisateurs à accéder au service. Dans ce cas, le problème est significatif et peut se répéter. |
|**Service en cours de restauration** | La cause du problème a été identifiée, nous connaissons l'action corrective à appliquer et le service est en cours de restauration. |
|**Récupération étendue** | Cet état indique qu'une action corrective est en cours afin de restaurer le service pour la plupart des utilisateurs, mais qu'il faudra un certain temps pour qu'elle s'applique à tous les systèmes concernés. Cet état peut également s'afficher si nous proposons un correctif temporaire visant à réduire l'impact du problème en attendant un correctif définitif. |
|**Examen suspendu** | Cet état s'affiche si l'examen détaillé d'un problème potentiel implique plus d'informations de la part des clients afin de nous permettre de mieux l'étudier. Dans ce cas, nous vous indiquerons les données ou journaux dont nous avons besoin. |
|**Service restauré** | L'action corrective a permis de résoudre le problème sous-jacent et le service a été restauré. Pour en savoir plus, consultez les détails relatifs au problème. |
|**Publication du rapport post-incident** | Nous avons publié un rapport de l’incident post pour un problème spécifique qui inclut les informations de la cause première et les étapes suivantes pour éviter que le problème ne se reproduise. |
   
## <a name="history"></a>Historique

L’état du service vous permet de consulter l’état actuel de l’intégrité et d’afficher l’historique des avis de service et des incidents ayant influencé votre client au cours des 30 derniers jours. Pour afficher l'état passé de tous les services, sélectionnez **Afficher l'historique** sur la page **État du Service**. 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
La liste de tous les messages d'état des services publiés au cours de la période sélectionnée s'affiche comme suit :
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Vous pouvez afficher l'historique d'état au cours des 7 ou 30 derniers jours. Sélectionnez une ligne pour afficher plus de détails sur ce problème.
  
Pour plus d’informations sur notre engagement en matière de disponibilité, consultez la rubrique [opérations transparentes d’Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Laisser un commentaire

Nous mettons tout en œuvre pour que les informations que nous vous fournissons soient opportunes, précises et utiles. Pour évaluer nos interventions, sélectionnez un nombre d'étoiles. Après nous avoir attribué une note de 1 à 5 étoiles, vous pouvez envoyer des commentaires sur des détails spécifiques. Nous utiliserons vos commentaires pour affiner notre système d'état des services.
  
## <a name="see-also"></a>Voir aussi

[Rapports d’activité dans le centre d’administration Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)