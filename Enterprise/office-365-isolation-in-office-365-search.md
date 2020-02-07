---
title: Isolation du client Office 365 dans Office 365 Search
ms.author: robmazz
author: robmazz
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
description: 'Résumé : explication de l’isolation du client dans Office 365 Search.'
ms.openlocfilehash: 9583b923abdb87140863fad8cfc7ad606df6e979
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844415"
---
# <a name="tenant-isolation-in-office-365-search"></a>Isolation du client dans Office 365 Search

La recherche SharePoint Online utilise un modèle de séparation des clients qui équilibre l’efficacité des structures de données partagées avec une protection contre la fuite d’informations entre les locataires. Ce modèle empêche les fonctionnalités de recherche de :

- Renvoi de résultats de requête qui contiennent des documents provenant d’autres locataires
- Exposition de suffisamment d’informations dans les résultats de requête pour qu’un utilisateur compétent puisse déduire des informations sur d’autres clients
- Affichage du schéma ou des paramètres d’un autre client
- Le mélange des informations de traitement d’analyse entre les locataires ou les résultats du stockage dans le mauvais client
- Utilisation d’entrées de dictionnaire provenant d’un autre client

Pour chaque type de données client, nous utilisons une ou plusieurs couches de protection dans le code pour éviter la fuite accidentelle d’informations. Les données les plus critiques possèdent le plus de couches de protection pour s’assurer qu’un seul défaut ne résulte pas d’une fuite d’informations effective ou perçue.

## <a name="tenant-separation-for-the-search-index"></a>Séparation des clients pour l’index de recherche

L’index de recherche est stocké sur le disque dans les serveurs hébergeant les composants d’index et les clients partagent les fichiers d’index. Les documents indexés d’un client ne sont visibles que pour les requêtes de ce client. Trois mécanismes indépendants empêchent la fuite d’informations :

- Filtrage des ID de locataire
- Préfixe du terme ID client
- Vérifications de liste de contrôle d’accès

Les trois mécanismes doivent échouer pour que la recherche renvoie des documents au mauvais client.

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>Filtrage d’ID de client et préfixe de termes d’ID de client

Les préfixes de recherche sont indexés dans l’index de recherche en texte intégral avec l’ID de client. Par exemple, lorsque le terme «*foo*» est indexé pour un client dont l’ID est «*123*», l’entrée dans l’index de texte intégral est «*123foo ».*

Chaque requête est convertie pour inclure l’ID client à l’aide d’un processus appelé filtrage des ID de locataire. Par exemple, la requête «*foo*» est convertie en «<*GUID*>. *foo* ET *tenantID*: <*GUID*>», où <*GUID*> représente le client qui exécute la requête. Cette conversion de requête se produit au sein de chaque nœud d’index, et ni le traitement des requêtes, ni le traitement du contenu ne peuvent l’influencer. Étant donné que l’ID de locataire est ajouté à chaque requête, la fréquence d’un terme dans d’autres clients ne peut pas être déduite en examinant le meilleur classement par correspondance dans un seul client.

L’expression de préfixe d’ID de client ne se produit que dans l’index de texte intégral. Les recherches à l’aide de champs, telles que «*title : foo*», permettent d’accéder à un index de recherche synthétique où les termes ne sont pas préfixés par ID de client. Au lieu de cela, les recherches dans les champs sont précédées du nom du champ. Par exemple, la requête «*title : foo*» est convertie en «*Fields. title : foo et Fields. tenantID*: <*GUID*> ». Étant donné que la fréquence d’un terme n’influe pas sur le classement des correspondances dans l’index de recherche synthétique, il n’est pas nécessaire de séparer les clients par le préfixe des termes. Pour une recherche*nommée « title : foo*», la séparation de contenu du client dépend du filtrage de l’ID de client par conversion de requête.

## <a name="document-access-control-list-checks"></a>Vérification de la liste de contrôle d’accès des documents

La recherche contrôle l’accès aux documents via des ACL qui sont enregistrés dans l’index de recherche. Chaque élément est indexé avec un ensemble de termes dans un champ de liste de contrôle d’accès spécial. Le champ ACL contient un terme par groupe ou utilisateur qui peut afficher le document. Chaque requête est complétée par une liste de termes d’entrée de contrôle d’accès (ACE), un pour chaque groupe auquel l’utilisateur authentifié appartient.

Par exemple, une requête comme «<*guid*>. *foo et tenantID*: <*GUID*> « devient : » <*GUID*>. *foo et tenantID*: <*GUID*> *et* (*docACL :*<*ace1*> *ou docACL*: <*Ace2*> *ou docACL*: <*ACE3*> *...*) "

Étant donné que les identificateurs d’utilisateurs et de groupes, ainsi que les ACE, sont uniques, ce qui offre un niveau de sécurité supplémentaire entre les clients pour les documents qui ne sont visibles que par certains utilisateurs. Il en est de même pour l’ACE spéciale « tout le monde sauf les utilisateurs externes » qui accorde l’accès aux utilisateurs réguliers dans le client. Toutefois, étant donné que les ACE pour « tout le monde » sont les mêmes pour tous les clients, la séparation des clients pour les documents publics dépend du filtrage de l’ID de client. Les entrées ACE refusées sont également prises en charge. L’augmentation de requête ajoute une clause qui supprime un document du résultat lorsqu’il existe une correspondance avec une ACE Deny.

Dans Exchange Online Search, l’index est partitionné sur l’ID de la boîte aux lettres de l’utilisateur individuel au lieu de l’ID de client (ID d’abonnement) comme dans SharePoint Online. Le mécanisme de partitionnement est identique à SharePoint Online, mais il n’y a pas de filtrage ACL.
