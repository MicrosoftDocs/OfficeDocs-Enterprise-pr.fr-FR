---
title: Planification du réseau et de la migration pour Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contient des liens vers des informations sur la planification de réseau et de test et la migration vers Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223056"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planification du réseau et de la migration pour Office 365

Cet article contient des liens vers des informations sur la planification et de test de réseau et la migration vers Office 365.
  
Avant de déployer Office 365 pour la première fois ou de migrer vers Office 365, vous pouvez utiliser les informations figurant dans ces rubriques pour estimer la bande passante dont vous avez besoin, puis pour tester et vérifier que vous disposez de suffisamment de bande passante pour déployer Office 365 ou migrer vers Office 365.

||
|:-----|
| Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Voir Cloud Microsoft Networking d’affiche architectes d’entreprise](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Pour savoir comment optimiser votre réseau pour Office 365 et d’autres plateformes en nuage de Microsoft et services, voir le poster [Microsoft Cloud mise en réseau pour les architectes de l’entreprise](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimation des besoins en bande passante réseau
<a name="EstimateBandwidthRequirements"> </a>

L’utilisation d’Office 365 peut augmenter l’utilisation des circuits internet de votre organisation. Il est important de déterminer si la quantité de bande passante disponible est suffisant pour traiter l’augmentation estimée après le déploiement d’Office 365 est entièrement tout en laissant au moins de 20 % la capacité à gérer le plus de jours.
  
Pour estimer la bande passante, procédez comme suit :
  
1. Évaluer le nombre de clients qui utiliseront chaque sortie Internet. Permettent de gérer autant que possible la connexion de notre réseau multi-to. 
    
2. Déterminer les fonctionnalités et les services Office 365 sera disponibles pour les clients à utiliser. Vous aurez probablement des groupes de personnes avec différents services ou les profils d’utilisation.
    
3. Mesurer l’utilisation du réseau pour un groupe pilote de clients. Assurez-vous que les clients pilotes sont représentant les profils de personnes dans l’organisation, ainsi que les différents emplacements géographiques différents. Vous pouvez vérification vos résultats par rapport à notre anciens calculateurs pour [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)et [Skype pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=321551) ou l' [étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , que nous effectuées sur votre propre réseau. 
    
4. Utilisez les mesures à partir du groupe pilote pour tirer les conclusions besoins de l’organisation toute entière et testez de nouveau pour valider les estimations avant d’apporter des modifications à votre réseau.
    
## <a name="test-your-existing-network"></a>Tester votre réseau existant
<a name="calculators"> </a>

 **Outils réseau.** Tester et valider votre bande passante Internet pour déterminer les contraintes de latence, de chargement et téléchargement. Ces outils vous aideront à déterminer les fonctionnalités de votre réseau pour la migration ainsi qu’une fois que vous avez déployé entièrement. 
  
- [L’Analyseur de Message Microsoft](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer est un outil efficace pour résoudre les problèmes réseau. L’Analyseur de message capture, affiche et analyse le trafic de messagerie basée sur le protocole et les messages système. L’Analyseur de message vous permet également d’importer, regrouper et analyser les données à partir des fichiers journaux et de suivi.
    
- [Analyseur de connectivité à distance Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): teste la connectivité dans votre environnement Exchange Online.
    
- Utilisez l' [Assistant de récupération pour Office 365 et de prise en charge de Microsoft](https://diagnostics.office.com/#/Download?env=SOC) pour résoudre les problèmes d’Outlook et Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

Un peu plus attentivement ces meilleures pratiques pour plus d’informations sur l’amélioration de votre expérience avec Office 365.
  
1. Vous souhaitez commencer à aider vos utilisateurs immédiatement ? Pour obtenir des conseils sur l’utilisation d’Office 365, notamment SharePoint Online, Exchange Online et Lync Online, lorsque votre réseau n’est pas juste coopération, voir [meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . Cet article fournit des liens des charges de contenu sur TechNet et Support.office.com pour optimiser votre expérience avec Office 365 et inclut des informations sur les méthodes pour personnaliser vos pages web et comment définir les paramètres d’Internet Explorer pour la meilleure expérience Office 365. 
    
2. Lisez les [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau. 
    
3. Améliorer les performances de migration de messagerie en gérant avec soin la planification des mises à jour de Windows. Vous pouvez mettre à jour vos ordinateurs clients par lots et assurez-vous que tous les ordinateurs clients sont mis à jour avant la migration vers Office 365 afin de réguler l’utilisation de la bande passante réseau. Pour plus d’informations, voir [mettre à jour et configurer les bureaux pour Office 365 pour les dernières mises à jour manuellement](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Le trafic réseau de Office 365 effectue mieux lorsqu’il a traité comme un service Internet approuvé et autorisé à contourner le filtrage traditionnel et analyse par certaines organisations sur le trafic réseau vers les services Internet non approuvés. Cela inclut généralement la suppression sortant traitement telles que l’authentification utilisateur du proxy et l’inspection des paquets, tout en garantissant local sortant vers Internet avec la traduction d’adresses réseau (NAT) approprié et suffisamment gérer l’augmentation de la capacité de bande passante demandes de réseau. Pour plus d’instructions sur la configuration de votre réseau pour gérer Office 365 en tant que service Internet approuvé sur votre réseau, reportez-vous aux [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
    
1. Vérifiez les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Le trafic supplémentaire sur le point d’Office 365 entraîne une augmentation des connexions sortantes proxy ainsi que d’une augmentation du trafic sécurisé sur TLS/SSL.
    
2. Si votre proxy sortant nécessitent l’authentification des utilisateurs, vous pouvez rencontrer une perte de fonctionnalité ou de connectivité lente. Ignorer la nécessité d’authentification pour les domaines d’Office 365 peut réduire cette charge.
    
3. Si vous disposez d’un grand nombre de calendriers et de boîtes aux lettres partagés, vous pourrez voir une augmentation du nombre de connexions à partir d’Outlook vers Exchange. Par exemple, le client Outlook peut ouvrir jusqu’à deux connexions supplémentaires pour chaque calendrier partagé en cours d’utilisation. Dans ce cas, assurez-vous que le proxy sortant peut gérer les connexions, ou contournez le proxy pour les connexions à Office 365 pour Outlook.
    
4. Déterminer le nombre maximal de périphériques pris en charge pour une adresse IP publique et comment équilibrer la charge entre plusieurs adresses IP. Pour plus d’informations, voir [prise en charge NAT avec Office 365](nat-support-with-office-365.md).
    
5. Si vous êtes inspecter les connexions sortantes sur les ordinateurs sur votre réseau, en ignorant ce filtrage aux domaines Office 365 améliorer connectivité et performances. En outre, en ignorant inspection sortante souvent élimine le besoin d’une seule sortie Internet et permet local sortant Internet pour les demandes du réseau Office 365 destiné.
    
6. Certains clients de trouver les paramètres de réseau interne peuvent affecter les performances. Paramètres de taille de l’unité de transmission maximale, réseau la négociation automatique ou la détection automatique et sous-optimal itinéraires vers Internet sont des emplacements communs à consulter.
    
## <a name="network-planning-reference-for-office-365"></a>Référence de planification réseau pour Office 365
<a name="NetReference"> </a>

Les rubriques suivantes contiennent des informations de référence détaillées sur Office 365 réseau.
  
- [Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Connectivité client](client-connectivity.md)
    
- [Réseaux de distribution de contenu](content-delivery-networks.md)
    
- [Enregistrements de nom DNS externes pour Office 365](external-domain-name-system-records.md)
    
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
    
- [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)
    
- [Académie virtuelle Microsoft : Gestion des performances Office 365](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Mise en réseau vidéo Office 365 Forum aux Questions (FAQ)](office-365-video-networking-faq.md)
    
- [Planifier les périphériques réseau qui se connectent aux services Office 365](plan-for-network-devices.md)
    
- [Conseillers de déploiement pour les services Office 365](deployment-advisors-for-office-365.md)
    

