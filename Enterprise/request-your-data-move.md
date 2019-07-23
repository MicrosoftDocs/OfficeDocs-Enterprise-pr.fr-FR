---
title: Procédure de demande d'un déplacement de données
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 07/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: Les clients Office 365 existants devront envoyer une demande avant la date d'échéance de leur pays afin que les données client de leurs services Office 365 soient déplacées vers leur nouvelle région.
ms.openlocfilehash: b1fc5606549597eb91990f3675d4d867d0605f04
ms.sourcegitcommit: 626ffb9907d5225acccf94095f54c8244df8dd49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "35818022"
---
# <a name="how-to-request-your-data-move"></a>Procédure de demande d’un déplacement de données

> [!NOTE]
> Les informations sur cette page s'appliquent uniquement aux utilisateurs qui disposaient déjà de clients Office 365 avant le lancement des nouveaux centres de données dans leur région. 
  
Les clients Office 365 existants sont autorisés à demander une migration précoce pour les données client principales de leur organisation au repos.  
  
## <a name="when-can-i-request-a-move"></a>Quand puis-je demander un déplacement ?

|**Clients avec une adresse de facturation en/au**|**Début de période de la demande**|**Date d'échéance de la demande**|
|:-----|:-----|:-----|
|Japon  <br/> |1er août 2016  <br/> |31 octobre 2016  <br/> |
|Australie, Nouvelle-Zélande, Fidji  <br/> |1er août 2016  <br/> |31 octobre 2016  <br/> |
|Inde  <br/> |1er août 2016  <br/> |31 octobre 2016  <br/> |
|Canada  <br/> |1er août 2016  <br/> |31 octobre 2016  <br/> |
|Royaume-Uni  <br/> |15 mars 2017  <br/> |15 septembre 2017  <br/> |
|Corée du Sud  <br/> |1er mai 2017  <br/> |31 octobre 2017  <br/> |
|France  <br/> |14 mars 2018  <br/> |15 septembre 2018  <br/> |
|Émirats arabes unis  <br/> |15 juillet 2019  <br/> |31 janvier 2020  <br/> |
|Afrique du Sud  <br/> |Vision  <br/> |Vision  <br/> |
   
## <a name="how-to-request-a-move"></a>Procédure de demande d’un déplacement

Les clients éligibles verront une page dans leur [Centre d’administration](https://aka.ms/365admin), ce qui leur permettra de demander que leurs données client fondamentales soient déplacées vers leur nouvelle région de centre de données.  
  
Pour accéder à la page dans le centre d’administration 365 de Microsoft, dans le volet de navigation à gauche, développez **paramètres**, puis cliquez sur profil de l' **organisation**.
  
![Menu paramètres avec profil organisationnel mis en surbrillance](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
Sur la page **Profil de l'organisation**, faites défiler jusqu'à la section sur l' **option concernant l'emplacement des données**. 
  
![Carte de résidence des données](media/dataresidencyae.jpg)
  
**Vous ne verrez peut-être pas cette section si l’une des conditions suivantes est appliquée**:
- Votre client n’est pas éligible au programme de déplacement.  Le droit est déterminé par le pays d’inscription du client.
- Toutes vos données se trouvent déjà dans la nouvelle région (reportez-vous à la section sur l’emplacement des données de la page). 
  
Si votre organisation a des besoins en matière de résidence des données et que vous devez demander une migration précoce, cliquez sur **modifier** en haut à droite de la section. Une nouvelle section apparaîtra sur le côté droit de votre écran en expliquant les détails du programme de déplacement. Sélectionnez le bouton bascule en regard du texte indiquant : **Oui, mon organisation a des besoins spécifiques en matière d'emplacement des données**. Cliquez ensuite sur **Enregistrer**.
  
![Écran de l'action d'abonnement dans le centre de données](media/dataresidencyflyoutae.jpg)
  
Le texte de la section sur l' **option concernant l'emplacement des données** change et indique : **Votre organisation a demandé à déplacer ses données client essentielles**. Vous recevez également un message de confirmation dans votre centre de messages. Cela permet de confirmer que votre demande de déplacement a abouti. 


  
## <a name="what-happens-after-requesting-a-move"></a>Que se passe-t-il une fois la demande de déplacement effectuée ?

Après avoir demandé un déplacement, nous allons vous déplacer aussi rapidement que les contraintes opérationnelles le permettent. En raison de la nature imprévisible de la plupart des contraintes, nous ne pouvons pas vous communiquer une date spécifique ou une période pour les déplacements. Vous recevrez une notification une fois le déplacement terminé.
  
Les déplacements peuvent prendre jusqu'à 24 mois à compter de la date d'échéance de la demande pour votre pays.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft Teams ne prend pas encore en charge la migration du contenu client des centres de données en région vers des centres de données dans le pays où les données de résidence de Microsoft teams sont disponibles.  Par conséquent, seuls les nouveaux clients auront toutes leurs données stockées dans le pays dans les nouvelles régions où Microsoft teams prend en charge la résidence des données.  En savoir plus sur la résidence des données Office 365 sur l’emplacement de votre entreprise [où se trouvent vos données?](https://products.office.com/where-is-your-data-located)   

## <a name="optional-actions-before-you-request-a-move"></a>Actions facultatives avant d’effectuer une demande de déplacement

Effectuez les opérations suivantes selon vos besoins.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Si vous utilisez un pare-feu reposant sur l’adresse IP, ajoutez des règles d’autorisation pour les nouvelles adresses IP.

Nous vous recommandons d'utiliser le filtrage DNS pour les pare-feu au lieu des adresses IP. Aucune nouvelle entrée DNS n'est requise.
  
Si vous utilisez un pare-feu reposant sur l'adresse IP pour la connectivité Internet, vous devez ajouter des règles d'autorisation pour les nouvelles adresses IP de la région de centres de données de destination. Des adresses IP pour les nouvelles régions de centres de données en plus de nouveaux serveurs sont constamment ajoutés aux [URL et plages d'adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkId=229631).
  
Consultez la documentation relative à votre pare-feu pour obtenir plus d'informations sur la procédure d'ajout de règles d'autorisation (également appelé ajout à la liste verte).
  
Après avoir ajouté des adresses IP, vous souhaiterez peut-être tester la connectivité à la nouvelle région de centres de données. Pour ce faire, nous vous recommandons de créer un [client d'évaluation gratuit pendant 30 jours](https://go.microsoft.com/fwlink/?LinkId=522463) dès que la région de centres de données sera disponible. 
  
### <a name="test-using-a-new-tenant"></a>Test à l’aide d’un nouveau client

Si vous souhaitez tester la connectivité avant le déplacement, vous pouvez configurer un [nouveau client d'évaluation gratuit pendant 30 jours](https://go.microsoft.com/fwlink/?LinkId=522463) dès que la nouvelle région de centres de données est disponible, et l'utiliser pour tester Office 365 hébergé dans la nouvelle région de centres de données. 
  
Le client d'évaluation ne peut pas être associé à votre client existant :
  
- Les utilisateurs doivent utiliser un compte d'évaluation différent pour leur test.
    
- Il n’existe aucun moyen de déplacer des données entre les clients.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Notification adressée aux utilisateurs concernant la mise à jour des paramètres Exchange obsolètes sur les appareils mobiles

Si les utilisateurs disposent d’un appareil mobile avec le serveur Exchange défini sur **m.Outlook.com** ou **podxxxxx.Outlook.com**, nous vous recommandons de passer à **Outlook.office365.com**, en suivant les instructions indiquées dans [set up a Mobile Device to Synchronize. avec votre compte](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Sujets associés

[Transfert de données principales vers le nouveau centre de données Office 365 régions centres](moving-data-to-new-datacenter-geos.md)

[FAQ général relatif au déplacement de données](data-move-faq.md)

[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/en-us/regions/)
  

