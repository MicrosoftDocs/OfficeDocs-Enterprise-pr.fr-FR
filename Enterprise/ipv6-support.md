---
title: Prise en charge du protocole IPv6 dans les services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Résumé : Décrit la prise en charge IPv6 dans les composants Microsoft Office 365 et dans les offres Office 365 pour le gouvernement.'
ms.openlocfilehash: 74752988803728ef4c319e368150b90f7e5d2599
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223126"
---
# <a name="ipv6-support-in-office-365-services"></a>Prise en charge du protocole IPv6 dans les services Office 365

 **Résumé**: décrit la prise en charge IPv6 dans les composants Microsoft Office 365 et dans les offres Office 365 pour le gouvernement.
  
Office 365 prend en charge IPv6 et IPv4 ; Toutefois, pas toutes les fonctionnalités d’Office 365 sont entièrement activées avec le protocole IPv6. Cela signifie que vous devez utiliser à la fois IPv4 et IPv6 pour se connecter à Office 365. Si vous filtrez le trafic sortant vers Office 365, vous trouverez la liste complète des adresses IPv6 sont prises en charge par Office 365 dans l’article [Office 365 URL et plages d’adresses IP](https://go.microsoft.com/fwlink/?LinkId=293744). Une fois que votre réseau est configuré et les adresses IPv6 appropriées sont autorisées, vous pouvez télécharger le [plan de test Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du Microsoft Download Center.
  
||
|:-----|
| Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Prise en charge d’IPv6 dans le service d’abonnement Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilise IPv6 par défaut sur les réseaux avec et sans fil. Si vous souhaitez contrôler les communications vers Exchange Online, utilisez les plages d’adresses IP dans [Office 365 URL et plages d’adresses IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online et IPv6

 **Office 365 pour le gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il essaiera d’utiliser IPv6 par défaut.
  
 **Cloud public de plusieurs client** Permet à Microsoft SharePoint Online IPv6 à votre demande. Vous devez fournir que le routage CIDR indiquées des adresses IP pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour IPv6 à activer pour votre client. Une fois que le protocole IPv6 est activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut sur les réseaux avec et sans fil. Si vous souhaitez contrôler les communications avec SharePoint Online, utilisez les plages d’adresses IP dans [Office 365 URL et plages d’adresses IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
 **Office 365 pour le gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il essaiera d’utiliser IPv6 par défaut.
  
### <a name="skype-for-business-and-ipv6"></a>Skype pour les entreprises et IPv6

Microsoft Active IPv6 pour Skype pour les entreprises à votre requête dans le nuage public multiclients et abonnements Office 365 pour le gouvernement G1/G3/G4/K1. Après avoir activé, si le programme que vous utilisez pour vous connecter à Skype pour les entreprises prend en charge IPv6, il utilise IPv6 par défaut. Si vous souhaitez contrôler les communications à Skype pour les entreprises, utilisez les plages d’adresses IP dans [Office 365 URL et plages d’adresses IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
Sachez IPv6 n’est pas disponible dans toutes les régions et Microsoft n’est peut-être pas en mesure d’activer pour votre client à ce stade.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission est effectuée par le protocole de Transport Layer Security. Pour la plage EOP, utilisez [Office 365 URL et plages d’adresses IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Prise en charge du protocole IPv6 pour les offres Office 365 pour le gouvernement

Prise en charge du protocole IPv6 Office 365 pour les offres pour le gouvernement est conforme à la gestion d’Office et le protocole Budget (OMB) pour les directeurs informatiques des départements exécutif et organismes, ainsi que le Federal gouvernement d’Adoption d’Internet Protocol Version 6 (IPv6 ) protocole. [Microsoft Office 365 pour le gouvernement](https://go.microsoft.com/fwlink/p/?LinkId=325414) est un service de plusieurs client qui stocke les données d’administration dans un nuage communautaire séparé. Comme d’autres offres Office 365, il fournit des services de collaboration et de productivité, notamment Exchange Online, Skype pour les entreprises, SharePoint Online et Office Professionnel Plus. Les offres de gouvernement Microsoft Office 365 s’appliquent uniquement pour 2013 et versions ultérieures. Pour plus d’informations sur les offres de gouvernement Office 365, voir [annonce Office 365 pour le gouvernement : A nous gouvernement Communauté du cloud computing](https://go.microsoft.com/fwlink/p/?LinkId=325414). Le trafic international dans les réglementations armes (ITAR) est un ensemble de la réglementation américaine qui contrôlent l’exportation et importation de défense les articles et des services sur [Liste de Munitions États-Unis (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 pour entreprises fournit des services d’hébergement dédiés pour les solutions de productivité de Microsoft qui prennent en charge la sécurité, de confidentialité et les exigences de conformité aux exigences réglementaires pour nous agences fédérales nécessitant Federal Information Security Certification de gestion (FISMA) et les entités commerciales soumises aux ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Eléments à prendre en compte lors de l'utilisation du protocole IPv6 et d'Office 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, voir [IPv6 pour Microsoft Windows : Forum aux Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). Pour déterminer quelles versions IP sont utilisées sur votre réseau, prenez en compte les éléments suivants :
  
- Si l’affichage de la commande IPConfig à l’invite de commandes contient des lignes nommées « Adresse IPv6 » ou « Adresse IPv6 temporaire », vous disposez du protocole IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « fe80 » et correspondent aux lignes nommées « Adresse IPv6 de liaison locale », vous ne disposez du protocole IPv6 dans votre environnement.

Les considérations suivantes peuvent s'appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge les achats par carte de crédit via IPv6. Cela ne s’applique pas au nuage communautaire destiné aux gouvernements (CCG) car les gouvernements disposent d’une gestion des licences de Contrat Entreprise (EA).

- Le protocole IPv6 ne prend pas en charge certains scénarios de services RMS.

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES) car BlackBerry ne prend pas en charge IPv6.

Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Voir aussi

[Blanc de Position de la technologie Microsoft](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[V6 et v4 TCP/IP](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[Guide de survie d’IPv6](https://go.microsoft.com/fwlink/p/?LinkID=237480)
