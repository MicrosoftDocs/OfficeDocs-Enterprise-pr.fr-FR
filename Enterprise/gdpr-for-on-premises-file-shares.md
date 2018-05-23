---
title: RGPD pour les partages de fichiers en local
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment satisfaire aux exigences du RGPD dans le cadre des partages de fichier Windows Server en local.
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a>RGPD pour les partages de fichiers Windows Server en local

L’approche principale recommandée pour les partages de fichiers est la suivante :

-   Vous pouvez attribuer des étiquettes aux données sensibles à l’aide d’Azure Information Protection.

-   Vous pouvez rechercher des données à l’aide du scanneur Azure Information Protection

L’approche recommandée pour les partages de fichiers est la suivante :

1.  **Installez et configurez le scanneur Azure Information Protection.**

    -   Déterminez les types de données sensibles à utiliser.

    -   Indiquez les dossiers locaux et les partages réseau à utiliser.

2.  **Effectuez un cycle de détection.**

    -   Exécutez le scanneur en mode de détection et validez les résultats.

    -   Si nécessaire, optimisez les conditions et les types d’informations sensibles.

    -   Évaluez l’incidence que pourra avoir l’application automatiques d’étiquettes.

3.  **Exécutez le scanneur Azure Information Protection pour appliquer des étiquettes aux documents correspondants**.

4.  **Pour une meilleure protection :**

    -   Configurez des règles de protection contre la perte de données Exchange pour protéger les documents avec l’étiquette souhaitée.

    -   Veillez à déterminer des autorisations pour restreindre les personnes pouvant accéder aux fichiers.

5.  **Pour la surveillance, intégrez un outil SIEM aux journaux Windows Server.**

    -   Pour rechercher des données personnelles dans le cadre de demandes de personnes concernées, utilisez le scanneur Azure Information Protection. Vous pouvez également configurer la recherche SharePoint Server pour analyser les partages de fichiers.

Pour plus d’informations sur l’utilisation du scanneur Azure Information Protection pour la recherche et l’étiquetage des données personnelles, reportez-vous au Kit de détection de données du RGPD Microsoft à l’adresse [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>).

Pour plus d’informations sur la configuration du scanneur pour diverses conditions et sur l’utilisation des types d’informations sensibles Office 365 dans le cadre de la protection contre la perte de données, reportez-vous à l’article [Comment configurer des conditions pour la classification automatique et recommandée pour Azure Information Protection](https://docs.microsoft.com/fr-FR/information-protection/deploy-use/configure-policy-classification). Notez que les nouveaux types d’informations sensibles Office 365 ne pourront pas immédiatement être utilisés avec le scanneur et que les types d’informations sensibles personnalisés ne peuvent pas être utilisés avec le scanneur.
