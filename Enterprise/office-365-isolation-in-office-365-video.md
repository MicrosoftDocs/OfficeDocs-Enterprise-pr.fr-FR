---
title: Isolation du client dans Office 365 Video
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Résumé : explication de l’isolation du client dans la vidéo Office 365.'
ms.openlocfilehash: d3d7f71260d74d598a8cc72962c2ab1ea1f2e6c3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998697"
---
# <a name="tenant-isolation-in-office-365-video"></a>Isolation du client dans Office 365 Video

> [!NOTE]
> La vidéo Office 365 sera remplacée par Microsoft Stream. Pour en savoir plus sur le nouveau service vidéo d’entreprise qui ajoute de l’intelligence à la collaboration vidéo et en savoir plus sur les plans de transition pour les clients vidéo actuels de Microsoft 365, voir [Office 365 vidéo transition vers Microsoft Stream Overview](https://docs.microsoft.com/stream/migrate-from-office-365).

## <a name="introduction"></a>Introduction

Le stockage Azure est utilisé pour stocker des données pour plusieurs services Office 365, y compris Office 365 vidéo et Sway. Le stockage Azure inclut le stockage BLOB, qui est un magasin d’objets Cloud hautement évolutif, basé sur REST, qui est utilisé pour le stockage des données non structurées. Le stockage Azure utilise un modèle de contrôle d’accès simple ; chaque abonnement Azure peut créer un ou plusieurs comptes de stockage. Chaque compte de stockage possède une clé secrète unique utilisée pour contrôler l’accès à toutes les données de ce compte de stockage. Cela prend en charge le scénario classique dans lequel le stockage est associé aux applications et ces applications ont un contrôle total sur leurs données associées ; par exemple, Sway stocke le contenu dans le stockage Azure. Tout le contenu du client pour Sway est stocké dans des comptes de stockage Azure partagés. Le contenu de chaque utilisateur se trouve dans une arborescence de répertoires distincte des objets BLOB dans le stockage Azure.

Les systèmes qui gèrent l’accès aux environnements client (par exemple, le portail Azure, SMAPI, etc.) sont isolés dans une application Azure gérée par Microsoft. Cela sépare logiquement l’infrastructure d’accès au client des applications clientes et de la couche de stockage.

## <a name="tenant-isolation-in-office-365-video"></a>Isolation du client dans Office 365 Video

La [vidéo Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) est un portail d’entreprise qui offre aux organisations une destination hautement sécurisée à l’échelle de l’Organisation pour la publication, le partage et la découverte de contenu vidéo. Dans la vidéo Office 365, les vidéos de chaque client sont isolées et chiffrées dans tous les emplacements, et sont uniquement disponibles pour les utilisateurs authentifiés qui ont accès et des autorisations aux vidéos de l’organisation. La vidéo Office 365 utilise une combinaison de technologies pour ce faire :

- SharePoint Online est utilisé pour le stockage du fichier vidéo et des métadonnées (titre, description, etc.). Elle fournit également la couche de sécurité et de conformité (y compris l’authentification) et les fonctionnalités de recherche.
- Azure Media Services fournit des fonctionnalités de transcodage, de diffusion en continu, de diffusion en continu et de remise sécurisée (à l’aide du chiffrement AES).

[Azure Media Services](https://azure.microsoft.com/services/media-services/) est une offre de services de plateforme comme un service pour l’activation de flux de travail multimédia de bout en bout dans le Cloud. La plateforme fournit une API REST pour le chargement, le codage, le chiffrement (avec PlayReady) et la remise de médias via des centres de contenu Azure dans le monde entier.

Tous les téléchargements pour la vidéo Office 365 se produisent via HTTPs. Lorsqu’un fichier vidéo est chargé, il est stocké dans SharePoint Online, et une copie du fichier est envoyée via un canal chiffré vers les services multimédias Azure. Azure Media Services transcode la vidéo en plusieurs formats optimisés pour l’expérience de visualisation (par exemple, mobile, bande passante faible, bande passante élevée, etc.). Ces fichiers, ainsi que le fichier d’origine acquis pendant le chargement, sont stockés dans Azure BLOB Storage. Les fichiers sont chiffrés à 128 l’aide de l’algorithme de package de chiffrement commun MPEG (ou une version antérieure de PlayReady) pour la lecture, puis chiffrés à l’aide du chiffrement de stockage AES 256 avant d’être stockés dans Azure BLOB Storage. (À l’aide du kit de développement logiciel (SDK) du client Azure Media Services, les clients peuvent contrôler le chiffrement utilisé. Par exemple, un client peut appliquer le chiffrement de stockage Azure Media Services (AES 256) à une ressource multimédia à forte valeur avant de le charger Azure BLOB Storage.)

Azure Media Services génère également une miniature pour la vidéo, qu’il transmet avec des métadonnées de miniature à SharePoint Online via un canal chiffré.
