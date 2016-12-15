---
title: "Migliaia di app, una sola identità"
description: "Questo articolo descrive come usare Enterprise Mobility + Security per fornire una singola identità da usare in qualsiasi app basata sul Web nel settore, sfruttando gli strumenti di Azure Active Directory."
keywords: 
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 12/07/2016
ms.topic: solution
ms.prod: 
ms.service: active-directory
ms.technology: 
ms.assetid: dd879a14-919e-431b-89b9-c035c83a6899
ROBOTS: 
ms.reviewer: atkladak, jsnow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fdb0852611551daaa2aad7d3839a3431abd8b445
ms.openlocfilehash: 27f71a706990997908a13b34477a1aa87ba698ab


---

# <a name="thousands-of-apps-one-identity"></a>Migliaia di app, una sola identità
Azure Active Directory (Azure AD) rende gli utenti più produttivi fornendo un'identità comune per gli utenti di applicazioni SaaS (Software as a Service, software come un servizio) che accedono a risorse sia cloud che locali.

Azure AD si integra con molte delle applicazioni SaaS attualmente più diffuse, come Box, Twitter, ServiceNow, DocuSign, Workday e molte altre. Supporta l'autenticazione Single Sign-On (SSO) e le identità e protegge la gestione degli accessi alle applicazioni da qualsiasi dispositivo in modo sicuro e affidabile.

## <a name="how-can-enterprise-mobility-security-help-you"></a>Come può essere utile Enterprise Mobility + Security?
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS aiuta a rispondere a una delle esigenze principali degli ambienti incentrati su dispositivi mobili e cloud, ovvero fornire una singola identità che funzioni in qualsiasi app basata sul Web nel settore:
- Esperienza di autenticazione facile con connessione al cloud
- Accesso Single Sign-On a 1000 app pre-integrate o alle app personalizzate
- Accesso remoto sicuro alle app locali
- Supporto per potenziamento e spostamento nel cloud


## <a name="recommended-solution"></a>Soluzione consigliata
Azure AD è una soluzione cloud di gestione delle identità e degli accessi che consente alle organizzazioni di accedere a tutto il necessario da qualsiasi posizione, in modo sicuro e produttivo, sfruttando anche gli investimenti esistenti negli strumenti tradizionali.
### <a name="access-to-single-sign-on-applications"></a>Accesso alle applicazioni Single Sign-On

Quando la funzionalità Single Sign-On non era ancora disponibile, gli amministratori IT dovevano gestire diversi utenti e password per tutte le varie applicazioni supportate dalle organizzazioni:

- Gli utenti immettono un nome utente e una password in ogni app usata
- Gli utenti devono gestire troppe password
- Spesso le password vengono riutilizzate
- La revoca dell'accesso è molto complessa

In base a una ricerca recente, nel 63% dei casi le violazioni dei dati sono correlate a password vulnerabili, predefinite o rubate.

La funzionalità Single Sign-On consente agli utenti di accedere a tutte le applicazioni e le risorse necessarie per lavorare effettuando l'accesso una sola volta con un singolo account utente. Una volta effettuato l'accesso, gli utenti possono accedere a tutte le applicazioni necessarie senza dover eseguire l'autenticazione (ad esempio digitare una password) una seconda volta.

Azure AD supporta tre tipi di autenticazione Single Sign-On:

- **Single Sign-On di Microsoft Azure AD:** questa opzione usa l'accesso federato per consentire agli utenti di accedere automaticamente alle applicazioni di terze parti, come Salesforce, usando le informazioni dell'account utente di Azure AD.
- **Password Single Sign-On:** questa opzione consente agli utenti di accedere automaticamente a un'applicazione SaaS di terze parti tramite l'uso in Azure AD delle informazioni dell'account utente di terze parti.
- **Accesso Single Sign-On esistente:** questa opzione supporta l'accesso Single Sign-On alle società SaaS di terze parti usando Active Directory Federation Services (ADFS) o un altro provider di servizi Single Sign-On di terze parti.

### <a name="how-single-sign-on-works"></a>Funzionamento dell'accesso Single Sign-On
Azure AD supporta l'accesso Single Sign-On con le app che supportano uno di questi protocolli standard:
- SAML 2.0
- OAuth 2.0/OpenID Connect
- WS-Federation

Un'applicazione viene configurata per usare Azure AD come provider di identità. Dopo la configurazione, l'app non richiede più l'input diretto di nome utente e password, ma esegue il reindirizzamento al provider di identità per l'autenticazione:

![Grafico che mostra le relazioni di trust configurate tra Azure AD e diverse applicazioni.](./media/thousands-apps-one-identity/thousands-apps-one-identity-fig1.png)


### <a name="do-i-still-need-azure-active-directory-federation-services-adfs"></a>È comunque necessario disporre di Azure Active Directory Federation Services (ADFS)?
Sì. Una connessione ADFS ad Azure AD fornisce consente un semplice accesso Single Sign-On da computer aggiunti al dominio:
- Gli utenti non vedono alcuna pagina di accesso basata sul Web
- I trust delle singole applicazioni vengono gestiti in Azure AD

![Grafico che mostra la modalità di connessione di Azure Active Directory Federation Services ad Azure AD allo scopo di fornire semplice accesso Single Sign-On per molte applicazioni.](./media/thousands-apps-one-identity/thousands-apps-one-identity-fig2.png)

### <a name="what-if-an-app-doesnt-support-federated-single-sign-on"></a>Cosa succede se un'app non supporta l'accesso Single Sign-On federato?
L'accesso SSO basato su password è la soluzione migliore per le app che non supportano SAML/OpenID e supportano solo l'immissione di nomi utente e password in un Web Form.
- È possibile definire set di credenziali specifici dell'applicazione e archiviarli in Azure AD
- Le credenziali possono essere assegnate a utenti o gruppi per l'accesso condiviso

### <a name="user-account-provisioning"></a>Provisioning degli account utente
Il provisioning degli account utente è l'operazione di creazione, aggiornamento e/o disabilitazione dei record degli account utente nell'archivio dei profili utente locale di un'applicazione. La maggior parte delle app SaaS archivia il ruolo e le autorizzazioni dell'utente nel proprio archivio dei profili utente locale.

Il servizio di provisioning di Azure AD si connette a un'API di gestione utenti SOAP/REST fornita per ogni singola app, per aggiungere, aggiornare e disabilitare gli account utente. È supportata la sincronizzazione dei gruppi e i profili/ruoli possono anche essere importati dall'app in Azure AD.

![Grafico che mostra la modalità di connessione del servizio di provisioning di Azure AD all'API di gestione utenti SOAP/REST.](./media/thousands-apps-one-identity/thousands-apps-one-identity-fig3.png)

### <a name="the-end-user-experience"></a>Esperienza dell'utente finale
Il pannello di accesso delle applicazioni è un portale compatibile con più dispositivi e più browser, accessibile usando iOS, Android, Mac e Windows. Per visualizzare il pannello di accesso, gli utenti eseguono una volta l'autenticazione in Azure AD, quindi visualizzano l'elenco di applicazioni a cui hanno accesso e possono avviare l'app da questa posizione con un semplice clic. Se l'applicazione è stata configurata per l'accesso SSO dall'amministratore, gli utenti non devono eseguire nuovamente l'autenticazione per accedere all'applicazione: la funzionalità Single Sign-On eseguirà automaticamente l'autenticazione.

### <a name="bring-your-own-apps"></a>Uso di app personalizzate
La raccolta di applicazioni di Azure AD contiene migliaia di applicazioni che è possibile aggiungere alla propria organizzazione, ma se non si riesce a trovare un'applicazione di terze parti, è possibile aggiungerla come app personalizzata per l'uso nell'organizzazione.

È possibile caricare praticamente qualsiasi applicazione basata sul Web che abbia un meccanismo di autenticazione basato su nome utente e password, indipendentemente dal fatto che sia presente o meno nella raccolta di applicazioni Azure.

![Schermata che mostra come usare la raccolta di applicazioni di Azure AD per aggiungere un'applicazione per l'organizzazione.](./media/thousands-apps-one-identity/thousands-apps-one-identity-fig4.png)

### <a name="secure-remote-access-to-on-premises-apps"></a>Accesso remoto sicuro alle app locali
Il [proxy di applicazione di Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-enable/) offre accesso Single Sign-On (SSO) e accesso remoto sicuro per le applicazioni Web ospitate in locale. Tali applicazioni includono siti di SharePoint, Outlook Web Access o altre applicazioni Web line-of-business in uso. Le applicazioni Web locali vengono integrate con Azure AD, la stessa piattaforma di controllo e identità usata da Office 365.

Gli utenti finali possono quindi accedere alle applicazioni locali nello stesso modo in cui accedono a Office 365 e ad altre applicazioni SaaS integrate con Azure AD, senza la necessità di una rete VPN o di modificare l'infrastruttura di rete.

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
I passaggi seguenti descrivono come implementare ogni funzionalità di Azure AD illustrata in precedenza. Ogni collegamento rappresenta un set diverso di articoli con un set specifico di istruzioni o passaggi da implementare nell'organizzazione:
1. [Abilitare l'accesso Single Sign-On con il proxy di applicazione.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-sso-using-kcd/)
- [Fornire accesso remoto sicuro alle applicazioni locali.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-get-started/)
  - [Uso di domini personalizzati nel proxy di applicazione di Azure AD.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-custom-domains/)
  - [Uso di app in grado di riconoscere le attestazioni nel proxy di applicazione.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-claims-aware-apps/)
  - [Uso dell'accesso condizionale per le app pubblicate usando il proxy di applicazione.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-conditional-access/)
- [Usare app personalizzate in Azure AD.](https://blogs.technet.microsoft.com/enterprisemobility/2015/06/17/bring-your-own-app-with-azure-ad-self-service-saml-configuration-now-in-preview/)

## <a name="additional-resources"></a>Risorse aggiuntive
- **Raccolta di app in Azure.com**
  - https://azure.microsoft.com/marketplace/active-directory/
- **Elenco di applicazioni SaaS** (con funzionalità di integrazione)
  - https://aadappgallery.azurewebsites.net/M
- **Esercitazioni sulle applicazioni SaaS**
  - https://azure.microsoft.com/documentation/articles/active-directory-saas-tutorial-list/



<!--HONumber=Dec16_HO2-->


