---
title: RGPD pour Skype Entreprise Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment satisfaire aux exigences du RGPD dans les environnements locaux Skype Entreprise Server et Lync Server.
ms.openlocfilehash: eac57a7044a5eeb828857c7aabd15c5ca1443c96
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-skype-for-business-server-and-lync-server"></a>RGPD pour Skype Entreprise Server et Lync Server

La plupart des données de Skype Entreprise Server et de Lync Server sont stockées dans Exchange Server. Ces données incluent les éléments suivants :

-   Historique des conversations

-   Notifications de messagerie vocale et transcriptions

-   Invitations aux réunions

Reportez-vous aux procédures définies pour le [RGPD pour Exchange Server](gdpr-for-exchange-server.md) afin de rechercher, exporter ou supprimer ces types de données dans le cadre de demandes liées au RGPD.

Les listes de contacts sont stockées dans la base de données SQL Server. Elles peuvent être exportées de plusieurs manières, décrites ci-dessous :

-   Les utilisateurs finaux eux-mêmes peuvent exporter des contacts en cliquant avec le bouton droit de la souris sur l’en-tête du groupe et en sélectionnant Copier. Tous les contacts de ce groupe seront ainsi copiés dans le Presse-papiers et pourront ensuite être collés dans n’importe quelle application.

-   Vous pouvez utiliser la cmdlet [Export-CsUserData](https://docs.microsoft.com/fr-FR/powershell/module/skype/export-csuserdata) pour exporter ces données.

Le contenu chargé dans des réunions (comme des documents ou fichiers PowerPoint) ou le contenu généré lors d’une réunion (comme le tableau blanc, des sondages ou des questions et réponses) est stocké dans l’organisateur de fichiers. Il peut également être exporté si des utilisateurs finaux se reconnectent à une réunion qui n’a pas expiré et téléchargent un contenu qui y a été chargé ou prennent des captures d’écran dans le cas où le contenu a été généré.

Les réunions MeetNow qui ne se trouvent pas dans le calendrier Exchange, tout comme la liste de contacts et les droits des contacts (famille, collègue, etc.) se trouvent dans la base de données utilisateur. Dans Lync Server 2013 et les versions ultérieures, vous pouvez utiliser la cmdlet [Export-CsUserData](https://docs.microsoft.com/fr-FR/powershell/module/skype/export-csuserdata) pour exporter ces données.
