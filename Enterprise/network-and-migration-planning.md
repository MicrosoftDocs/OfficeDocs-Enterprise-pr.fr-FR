---
title: Planification du réseau et de la migration pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contient des liens vers des informations sur la planification et le test du réseau, ainsi que sur la migration vers Office 365.
ms.openlocfilehash: 88dd3e4fca66855e8204b452aea6cfb4c659d201
ms.sourcegitcommit: bb5b7bd241f58491198de2d74dbdce76f7bb8f62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419382"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planification du réseau et de la migration pour Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Cet article contient des liens vers des informations sur la planification et le test du réseau, ainsi que sur la migration vers Office 365.
  
Avant de déployer pour la première fois ou de migrer vers Office 365, vous pouvez utiliser les informations de ces rubriques pour estimer la bande passante dont vous avez besoin, puis pour tester et vérifier que vous disposez d’une bande passante suffisante pour déployer ou migrer vers Office 365.

||
|:-----|
| Cet article fait partie de la [planification réseau et du réglage des performances pour Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Consultez l’affiche mise en réseau Cloud Microsoft pour les architectes d’entreprise](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Pour connaître les étapes permettant d’optimiser votre réseau pour Office 365 et les autres services et plateformes Cloud Microsoft, consultez l’affiche [mise en réseau Cloud Microsoft pour les architectes d’entreprise](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimer les besoins en bande passante réseau
<a name="EstimateBandwidthRequirements"> </a>

L’utilisation d’Office 365 peut augmenter l’utilisation du circuit Internet de votre organisation. Il est important de déterminer si la quantité de bande passante actuellement disponible est suffisante pour gérer l’augmentation estimée une fois qu’Office 365 est entièrement déployé, tout en laissant au moins 20% de capacité pour gérer le plus important de jours.
  
Pour estimer la bande passante, procédez comme suit :
  
1. Évaluez le nombre de clients qui utiliseront chaque sortie Internet. Laissez notre réseau multi-Terabit gérer autant que possible la connexion. 
    
2. Déterminez les services et fonctionnalités Office 365 qui seront disponibles pour les clients. Vous aurez probablement des groupes de personnes avec différents services ou profils d’utilisation.
    
3. Mesurez l’utilisation du réseau pour un groupe pilote de clients. Assurez-vous que les clients pilotes sont représentatifs des différents profils des personnes de l’organisation, ainsi que des différents emplacements géographiques. Vous pouvez vérifier vos résultats par rapport à nos anciennes calculatrices pour [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)et [Skype entreprise](https://go.microsoft.com/fwlink/p/?LinkId=321551) ou à l' [étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que nous avons effectuée sur notre propre réseau. 
    
4. Utilisez les mesures du groupe pilote pour extrapoler l’ensemble des besoins de l’organisation et effectuer un nouveau test pour valider les estimations avant d’apporter des modifications à votre réseau.
    
## <a name="test-your-existing-network"></a>Tester votre réseau existant
<a name="calculators"> </a>

 **Outils réseau.** Testez et validez votre bande passante Internet afin de déterminer les contraintes de téléchargement, de chargement et de latence. Ces outils vous aideront à déterminer les capacités de votre réseau pour la migration, ainsi qu’une fois que vous avez effectué entièrement le déploiement. 
    
- [Analyseur de connectivité à distance Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): teste la connectivité dans votre environnement Exchange Online.
    
- Utilisez l' [Assistant support et récupération de Microsoft pour office 365](https://diagnostics.office.com/#/Download?env=SOC) pour résoudre les problèmes liés à Outlook et à Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Meilleures pratiques pour la planification réseau et l’amélioration des performances de migration pour Office 365
<a name="BestPractices"> </a>

Approfondissez ces meilleures pratiques pour obtenir plus d’informations sur l’amélioration de votre expérience Office 365.
  
1. Vous souhaitez commencer à aider vos utilisateurs immédiatement ? Consultez les [meilleures pratiques pour l’utilisation d’office 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) pour obtenir des conseils sur l’utilisation d’Office 365, notamment SharePoint Online, Exchange Online et Lync Online, lorsque votre réseau n’est pas coopéré. Cet article fournit des liens vers des charges de contenu sur TechNet et Support.office.com pour l’optimisation de votre expérience Office 365 et inclut des informations sur des méthodes simples pour personnaliser vos pages Web et sur la façon de définir vos paramètres Internet Explorer pour la meilleure expérience Office 365. 
    
2. Lisez les [principes de connectivité réseau office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité permettant de gérer le trafic Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. Cet article vous aidera à comprendre les instructions les plus récentes pour optimiser en toute sécurité la connectivité réseau Office 365. 
    
3. Améliorez les performances de migration de messagerie en gérant soigneusement la planification des mises à jour Windows. Vous pouvez mettre à jour vos ordinateurs clients par lots et vous assurer que tous les ordinateurs clients sont mis à jour avant la migration vers Office 365 afin de réguler l’utilisation de la bande passante réseau. Pour plus d’informations, reportez-vous [à mise à jour manuelle et configuration des ordinateurs de bureau pour Office 365 pour les dernières mises à jour](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Le trafic réseau Office 365 fonctionne de manière optimale lorsqu’il est traité comme un service Internet approuvé et qu’il est autorisé à contourner la plupart des filtres et analyses traditionnels que certaines organisations placent sur le trafic réseau vers des services Internet non approuvés. Cela inclut généralement la suppression du traitement sortant, comme l’authentification des utilisateurs proxy et l’inspection des paquets, ainsi que la transmission de sortie locale vers Internet avec la traduction d’adresses réseau (NAT) et une capacité de bande passante suffisantes pour gérer les demandes réseau accrues. Reportez-vous à la rubrique [Managing office 365 Endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)pour obtenir des instructions supplémentaires sur la configuration de votre réseau pour qu’il gère Office 365 comme service Internet approuvé sur votre réseau.
    
1. Assurez-vous que la [gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Le trafic supplémentaire vers Office 365 entraîne une augmentation des connexions proxy sortantes, ainsi qu’une augmentation du trafic sécurisé sur TLS/SSL.
    
2. Si vos serveurs proxy sortants nécessitent une authentification de l’utilisateur, vous pouvez être confronté à une faible connectivité ou à une perte de fonctionnalité. Le contournement de l’exigence d’authentification pour les domaines Office 365 peut réduire cette charge.
    
3. Si vous avez un grand nombre de calendriers et de boîtes aux lettres partagés, vous pouvez constater une augmentation du nombre de connexions entre Outlook et Exchange. Par exemple, le client Outlook peut ouvrir jusqu’à deux connexions supplémentaires pour chaque calendrier partagé utilisé. Dans ce cas, assurez-vous que le proxy de sortie peut gérer les connexions ou contourner le proxy pour les connexions à Office 365 pour Outlook.
    
4. Déterminez le nombre maximal d’appareils pris en charge pour une adresse IP publique et le mode d’équilibrage de charge sur plusieurs adresses IP. Pour plus d'informations, voir l'article [Prise en charge NAT avec Office 365](nat-support-with-office-365.md).
    
5. Si vous examinez les connexions sortantes à partir d’ordinateurs de votre réseau, le filtrage vers les domaines Office 365 améliorera la connectivité et les performances. En outre, le contournement de l’inspection sortante supprime souvent la nécessité d’une sortie Internet unique et permet la sortie Internet locale pour les demandes de réseau Office 365.
    
6. Certains clients trouvent des paramètres réseau internes qui peuvent affecter les performances. Les paramètres tels que la taille de l’unité de transmission maximale (MTU), la négociation automatique réseau ou la détection automatique, ainsi que les itinéraires sous-optimaux vers Internet sont des emplacements courants.
    
## <a name="network-planning-reference-for-office-365"></a>Référence de planification réseau pour Office 365
<a name="NetReference"> </a>

Ces rubriques contiennent des informations détaillées sur le réseau Office 365.
  
- [Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Réseaux de distribution de contenu](content-delivery-networks.md)
    
- [Enregistrements DNS externes pour Office 365](external-domain-name-system-records.md)
    
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
    
- [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)
    
- [Forum aux questions sur la mise en réseau vidéo d’Office 365 (FAQ)](office-365-video-networking-faq.md)
    
- [Planifier les périphériques réseau qui se connectent aux services Office 365](plan-for-network-devices.md)
    
- [Guides de configuration pour les services Office 365](setup-guides-for-office-365.md)
 
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
