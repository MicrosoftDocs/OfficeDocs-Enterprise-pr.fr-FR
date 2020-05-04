---
title: Prise en charge du protocole IPv6 dans les services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Résumé : décrit la prise en charge du protocole IPv6 dans les composants Microsoft Office 365 et dans les offres gouvernementales Office 365.'
ms.openlocfilehash: 939b5653981cb78dfa316e0baf1c498a3db97904
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009309"
---
# <a name="ipv6-support-in-office-365-services"></a>Prise en charge du protocole IPv6 dans les services Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Office 365 prend en charge IPv6 et IPv4 ; Toutefois, toutes les fonctionnalités Office 365 ne sont pas entièrement activées avec IPv6. Cela signifie que vous devez utiliser IPv4 et IPv6 pour vous connecter à Office 365. Si vous filtrez votre trafic sortant vers Office 365, la liste complète des adresses IPv6 prises en charge par Office 365 est disponible dans l’article [URL office 365 et plages d’adresses IP](urls-and-ip-address-ranges.md). Une fois que votre réseau est configuré et que les adresses IPv6 appropriées sont autorisées, vous pouvez télécharger le [plan de test IPv6 Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du centre de téléchargement Microsoft.
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Prise en charge D’ipv6 dans le service d’abonnement Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux filaires et sans fil. Si vous souhaitez contrôler les communications vers Exchange Online, utilisez les plages d’adresses IP dans les [URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online et IPv6

 **Office 365 Administration G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il essaiera d’utiliser IPv6 par défaut.
  
 **Cloud mutualisé public** Microsoft Active le protocole IPv6 SharePoint Online à votre demande. Vous devez fournir les adresses IP de routage CIDR pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour IPv6 pour être activée pour votre client. Une fois le protocole IPv6 activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge le protocole IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux filaires et sans fil. Si vous souhaitez contrôler les communications vers SharePoint Online, utilisez les plages d’adresses IP dans les [URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md).
  
 **Office 365 Administration G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il essaiera d’utiliser IPv6 par défaut.
  
### <a name="skype-for-business-and-ipv6"></a>Skype entreprise et IPv6

N’oubliez pas que le protocole IPv6 n’est pas pris en charge dans Skype entreprise et qu’il ne peut plus être activé.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission a lieu sur le protocole de sécurité de la couche de transport. Pour la plage EOP, utilisez des [URL et des plages d’adresses IP Office 365](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Prise en charge D’ipv6 pour les offres gouvernementales Office 365

La prise en charge du protocole IPv6 d’Office 365 pour les offres gouvernementales est conforme à la note Office of Management and Budget (OMB) pour les responsables informatiques des cadres dirigeants des services et agences exécutifs, ainsi qu’à l’adoption du protocole IPv6 (Internet Protocol version 6). [Microsoft Office 365 pour le gouvernement](https://go.microsoft.com/fwlink/p/?LinkId=325414) est un service mutualisée qui stocke les données du gouvernement américain dans un Cloud communautaire séparé. Comme les autres offres Office 365, il offre des services de productivité et de collaboration, notamment Exchange Online, Skype entreprise, SharePoint Online et les applications Microsoft 365 pour les entreprises. 

Les offres gouvernementales de Microsoft Office 365 s’appliquent uniquement à 2013 et versions ultérieures. Pour plus d’informations sur les offres gouvernementales Office 365, voir [annonce d’office 365 pour le gouvernement : un Cloud communautaire pour le gouvernement américain](https://go.microsoft.com/fwlink/p/?LinkId=325414). Le trafic international en matière de réglementations sur les armes (ITAR) est un ensemble de réglementations gouvernementales américaines qui contrôlent l’exportation et l’importation d’articles et de services liés à la défense sur la [liste des munitions américaines (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). 

Microsoft Office 365 pour entreprises fournit des services d’hébergement dédiés pour les solutions de productivité Microsoft qui prennent en charge les exigences en matière de sécurité, de confidentialité et de conformité réglementaire pour les agences fédérales américaines requérant la certification FISMA (Federal Information Security Management) et les entités commerciales soumises à ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Éléments à prendre en compte lors de l’utilisation D’ipv6 et Office 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, reportez-vous à cet [article d’instructions](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Pour déterminer les versions IP utilisées sur votre réseau, prenez en compte les points suivants :
  
- Si l’affichage de la commande **ipconfig** à l’invite de commandes contient des lignes nommées « adresse IPv6 » ou « adresse IPv6 temporaire », cela indique que vous avez le protocole IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « FE80 » et correspondent à des lignes nommées « adresse IPv6 de liaison locale », vous n’avez pas IPv6 dans votre environnement.

Ces considérations peuvent s’appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge l’achat par carte de crédit sur IPv6. Cela ne s’applique pas au Cloud communautaire du gouvernement (GCC) car les gouvernements disposent d’une licence d’accord entreprise (EA).

- IPv6 ne prend pas en charge certains scénarios RMS (Rights Management Services).

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES) car BlackBerry ne prend pas en charge IPv6.

- Si vous utilisez les services ADFS (Active Directory Federation Services) avec Office 365, la publication de votre point de terminaison réseau AD FS vers Office 365 à l’aide du protocole IPv6 n’est pas prise en charge. Vous ne devez pas inclure les enregistrements AAAA dans l’entrée DNS AD FS lors de l’utilisation d’Exchange Online. 

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Voir aussi

[Feuille de route d’apprentissage IPv6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guide de survie IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
