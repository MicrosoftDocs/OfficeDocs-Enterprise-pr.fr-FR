---
title: Enregistrements DNS externes pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 'Résumé : liste de référence des enregistrements DNS à utiliser lorsque vous planifiez un déploiement Office 365.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996538"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Enregistrements DNS externes pour Office 365

|||
|:-----|:-----|
|![Domaine](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Retournez sur **[ planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Enregistrements DNS externes requis pour Office 365 (services principaux) :
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|**CNAME** <br/> **(Suite)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Remarque :** cette CNAME s’applique uniquement à Office 365 géré par 21Vianet.   |**Alias :** msoID  <br/> **Cible :** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Vérification du domaine)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Hôte :** @ (ou de certains fournisseurs d’hébergement DNS, votre nom de domaine)  <br/> **Valeur TXT :** _une chaîne de texte fournie par_ Office 365  <br/> L’Assistant de **configuration de domaine** Office 365 fournit les valeurs à utiliser pour créer cet enregistrement.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Enregistrements DNS externes requis pour la messagerie électronique dans Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **L’enregistrement de découverte automatique **permet aux ordinateurs clients de rechercher automatiquement Exchange et de configurer correctement le client.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
Voulez-vous simplement faire passer quelques adresses de messagerie dans Office 365 ? Vous pouvez [piloter Office 365 avec un petit nombre d’adresses e-mail sur votre domaine personnalisé](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **L’enregistrement TXT pour SPF** permet aux systèmes de messagerie de destination de confirmer que vous approuvez le serveur d’envoi de votre courrier électronique. Cela évite des problèmes tels que l’usurpation d’adresse e-mail et le hameçonnage. Consultez [Enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords) dans cet article pour comprendre ce que vous devez inclure dans votre enregistrement.

Les clients email qui utilisent la fédération Exchange auront un enregistrement CNAME et TXT supplémentaire en bas de tableau.
  
||||
|:-----|:-----|:-----|
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Alias :** autodiscover  <br/> **Cible :** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Envoie le courrier entrant pour votre domaine vers le service Exchange Online dans Office 365.  <br/> [!NOTE] Une fois le courrier électronique envoyé vers Exchange Online, vous devez supprimer les enregistrements MX qui pointent vers votre ancien système.   |**Domaine :** par exemple, contoso.com  <br/> **Serveur de messagerie cible :** \<MX token\> . mail.protection.outlook.com  <br/> **Préférence/priorité :** inférieur à d’autres enregistrements MX (cela garantit que le courrier est remis à Exchange Online) : par exemple, 1 ou 'faible'  <br/>  Recherchez votre en procédant comme \<MX token\> suit :  <br/>  Connectez-vous à Office 365, accédez à administrateur Office 365 \> domaines.  <br/>  Dans la colonne Action pour votre domaine, sélectionnez Corriger les problèmes.  <br/>  Dans la section Enregistrements MX, sélectionnez Que faut-il corriger ?  <br/>  Suivez les instructions de cette page pour mettre à jour votre enregistrement MX.  <br/> [Quelle est la priorité MX ?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Fédération Exchange)** <br/> |Utilisé pour la fédération Exchange en cas de déploiement hybride.  <br/> |**Enregistrement TXT 1 :** par exemple, contoso.com et texte associé personnalisé, texte de hachage de vérification de domaine associé généré de façon personnalisée (par exemple, Y96nu89138789315669824)  <br/> **Enregistrement TXT 2 :** par exemple, exchangedelegation.contoso.com et le texte de hachage de vérification de domaine associé personnalisé (par exemple, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Fédération Exchange)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Alias :** par exemple, Autodiscover.service.contoso.com  <br/> **Cible :** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Enregistrements DNS externes requis pour Skype Entreprise Online
<a name="BKMK_ReqdCore"> </a>

Il existe des étapes spécifiques à suivre lorsque vous utilisez des [plages d’adresses IP et URL Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) pour vous assurer que votre réseau est correctement configuré.

> [!NOTE]
> Ces enregistrements DNS s’appliquent également à Teams, en particulier dans un scénario hybride Teams et Skype Entreprise Online, lorsque certains problèmes de fédération peuvent se produire.
  
||||
|:-----|:-----|:-----|
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|**SRV** <br/> **(Skype Entreprise Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Service** : sipfederationtls  <br/> **Protocole :** TCP  <br/> **Priorité :** 100  <br/> **Poids :** 1  <br/> **Port :** 5061  <br/> **Cible** : sipfed.online.lync.com  <br/> **Remarque :** si le pare-feu ou le serveur proxy bloque les recherches SRV sur un DNS externe, vous devez ajouter cet enregistrement à l'enregistrement DNS interne.   |
|**SRV** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par Skype Entreprise Online pour coordonner le flux d’informations entre des clients Lync.  <br/> |**Service :** sip  <br/> **Protocole :** TLS  <br/> **Priorité :** 100  <br/> **Poids :** 1  <br/> **Port :**  443  <br/> **Cible :** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par le client Lync pour trouver le service Skype Entreprise Online et se connecter.  <br/> |**Alias :** sip  <br/> **Cible :** sipdir.online.lync.com  <br/> Pour plus d’informations, voir [URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par le client Lync mobile pour trouver le service Skype Entreprise Online et se connecter.  <br/> |**Alias :** lyncdiscover  <br/> **Cible :** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Enregistrements DNS externes requis pour authentification unique Office 365
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|**Hôte (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Cible :** par exemple, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Enregistrements DNS externes requis pour SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Structure d'un enregistrement SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Un système de messagerie recevant un message électronique via votre domaine examine l’enregistrement SPF, et, si le serveur de messagerie qui a émis le message était un serveur Office 365, le message est accepté. Si le serveur qui a envoyé le message était votre ancien système de messagerie ou un système de messagerie malveillant sur Internet, par exemple, la vérification SPF échouerait et le message ne serait pas remis. Ces vérifications contribuent à éviter l’usurpation d’identité et à détecter les messages de hameçonnage.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Choisir la structure d’enregistrement SPF dont vous avez besoin

Pour les scénarios où vous n’utilisez pas seulement les emails Exchange Online pour Office 365 (par exemple, lorsque vous utilisez le courrier électronique en provenance de SharePoint Online), utilisez le tableau suivant pour déterminer les éléments à inclure dans la valeur de l’enregistrement.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Si vous utilisez...  <br/> |Objectif  <br/> |Ajoutez ceci  <br/> |
|1   <br/> |Tous les systèmes de messagerie (obligatoire)  <br/> |Tous les enregistrements SPF commencent par cette valeur  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (courant)  <br/> |Utilisez uniquement avec Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Un système de messagerie tiers (moins courant)  <br/> ||Incluez : \<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Le système de messagerie du site (moins courant)  <br/> |À utiliser si vous avez recours à Exchange Online Protection ou Exchange Online et un autre système de messagerie  <br/> |IP4 : \<0.0.0.0\>  <br/> ip6 : \< : : \>  <br/> Incluez : \<mail.contoso.com\>  <br/> La valeur entre crochets (\<\>) doit être les autres systèmes de messagerie chargés d’envoyer les emails pour votre domaine.  <br/> |
|5   <br/> |Tous les systèmes de courrier (obligatoire)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Exemple : Ajout à un enregistrement SPF existant
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Vous mettez à jour votre enregistrement SPF pour Office 365. Vous allez modifier votre enregistrement actif afin d’avoir un enregistrement SPF qui inclut les valeurs dont vous avez besoin. Pour Office 365, « spf.protection.outlook.com ».
  
Correct :
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Incorrect :
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Autres exemples de valeurs SPF standard
<a name="bkmk_addtospf"> </a>

Si vous utilisez la suite Office 365 complète et que vous utilisez MailChimp pour envoyer des e-mails de marketing en votre nom, votre enregistrement SPF sur contoso.com peut ressembler à ce qui suit, qui utilise les lignes 1, 3 et 5 de la table ci-dessus. N’oubliez pas que les lignes 1 et 5 sont obligatoires.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Sinon, si vous avez une configuration Exchange hybride où le courrier électronique a été envoyé à la fois à partir d’Office 365 et du système de messagerie du site, votre enregistrement SPF sur contoso.com peut se présenter comme ceci :
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365edns](https://aka.ms/o365edns)
