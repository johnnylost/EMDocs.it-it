---
title: Responsabilità di FastTrack
description: Responsabilità di FastTrack quando i clienti usano FastTrack Center Benefit per EMS
keywords: ''
author: andredm7
ms.author: andredm
manager: ''
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: b984f825ba2c799f7a6e5585e038e017df3ee417
ms.sourcegitcommit: 4401a878f88cc60b3cfd90a915747fe37e333014
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="fasttrack-responsibilities"></a>Responsabilità di FastTrack

Ecco le responsabilità di FastTrack durante il processo di onboarding.

## <a name="general"></a>Generale

-   Viene fornita assistenza remota per le attività di configurazione necessarie, come illustrato nelle descrizioni dettagliate delle fasi.

-   All'utente vengono forniti documentazione, strumenti software e console di amministrazione disponibili per ridurre o eliminare le attività di configurazione.

## <a name="initiate-phase"></a>Fase di avvio

-   Collaborare con l'utente per avviare l'onboarding.

-   Definire i servizi idonei per l'onboarding.

## <a name="assess-phase"></a>Fase di valutazione

-   Fornire una panoramica sull’amministrazione.

-   Fornire indicazioni su:

    -   Esigenze relative a DNS, rete e infrastruttura.

    -   Esigenze del client (browser Internet, sistema operativo client e servizi).

    -   Identità dell'utente e provisioning.

    -   Abilitazione dei servizi che sono stati acquistati e definiti come parte dell'onboarding.

-   Stabilire la sequenza temporale per le attività di correzione.

-   Fornire un elenco di controllo di correzione per Intune e Azure AD Premium.

## <a name="remediate-phase"></a>Fase di correzione

-   Effettuare conferenze telefoniche con l'utente in base alla programmazione già concordata per esaminare l'avanzamento delle attività di correzione, ad esempio offrire informazioni sui prerequisiti di installazione prima di eseguire l'onboarding di un servizio cloud Microsoft.

## <a name="enable-phase"></a>Fase di abilitazione
Fornire indicazioni su:

-   Attivazione del tenant o dell'abbonamento per i servizi online di Microsoft.

-   Configurazione di protocolli TCP/IP e porte del firewall.

-   Configurazione del DNS per i servizi idonei.

-   Convalida di connettività ai servizi online di Microsoft.

-   Per un ambiente a foresta singola:

    -   Installazione di un server di sincronizzazione delle directory tra Active Directory Domain Services (AD DS) e Microsoft Online Services (solo materiale sussidiario se necessario).

    -   Configurazione dell'autenticazione gestita (sincronizzazione degli hash delle password o autenticazione pass-through) con lo strumento Azure Active Directory Connect. (solo materiale sussidiario se necessario).

        > [!NOTE]
        > Sviluppo e implementazione per estensioni di regole personalizzate non rientrano nell'ambito.

-   Per una singola foresta se la destinazione sono le identità federate: installazione e configurazione di Active Directory Federation Services (AD FS) per l'autenticazione di domini locali con Intune in una configurazione a tolleranza di errore con singolo sito, se necessario.

    > [!NOTE]
    > Per tutte le configurazioni di più foreste le distribuzioni di AD FS non rientrano nell'ambito.

-   Test della funzionalità SSO (Single Sign-On), se distribuita.

### <a name="enable-phase---microsoft-azure-active-directory-premium"></a>Fase di abilitazione - Microsoft Azure Active Directory Premium

Fornire indicazioni su:

- Attivazione del tenant di Azure AD Premium.

- Configurazione delle porte del firewall.

- Configurazione di DNS per i servizi idonei.

- Convalida della connettività nei servizi di Azure AD Premium.

- Per un ambiente a foresta singola:

  -   Installazione di una sincronizzazione delle directory tra Active Directory Domain Services (AD DS) e Azure AD Connect, se richiesto.

  -   Configurazione di un metodo di autenticazione (sincronizzazione degli hash delle password o autenticazione pass-through) con lo strumento Azure AD Connect.

- Per un ambiente a più foreste:

  -   Installazione della sincronizzazione di Azure AD Connect, configurata per scenari a più foreste.
- Per ambienti a foresta singola e a più foreste:
  - Configurazione dell'autenticazione pass-through di Azure Active Directory, se necessario.
  - Configurazione dell'accesso Single Sign-On facile (SSO) di Azure Active Directory, se necessario.
    > [!NOTE]
    > L'autenticazione pass-through di Azure Active Directory per ambienti a più foreste è supportata se sono presenti trust tra foreste tra le foreste di Active Directory e se il routing dei suffissi nome è configurato correttamente. È possibile installare altri agenti su più server locali per offrire disponibilità elevata per le richieste di accesso.

  - Per altre informazioni, vedere [Autenticazione pass-through di Azure Active Directory: Avvio rapido](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start#step-1-check-prerequisites) e [Accesso Single Sign-On facile di Azure Active Directory: Avvio rapido](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start#step-1-check-prerequisites).
  - Per altre informazioni sui limiti dell'autenticazione pass-through, vedere [Autenticazione pass-through di Azure Active Directory: Limitazioni correnti](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-current-limitations).
  - Per altre informazioni sui problemi con l'accesso Single Sign-On facile, vedere [Risolvere i problemi relativi all'accesso Single Sign-On facile di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-sso).

      > [!NOTE]
      > La sincronizzazione hash e il writeback delle password supportano più foreste. Tuttavia, gli altri scenari di writeback non sono supportati.

  - Configurazione della sincronizzazione tra le foreste locali di Active Directory e la directory di Microsoft Azure Active Directory Premium (Azure Active Directory).

    > [!NOTE]
    > Sviluppo e implementazione per estensioni di regole personalizzate non rientrano nell'ambito.

- Per una singola foresta se la destinazione sono le identità federate:

  -   Installazione e configurazione di AD FS per l'autenticazione di domini locali con Azure AD Premium in una configurazione a tolleranza di errore con singolo sito, se necessario.

  > [!NOTE]
  > Per tutte le configurazioni di più foreste le distribuzioni di AD FS non rientrano nell'ambito.

- Test della funzionalità SSO (se distribuita).

### <a name="enable-phase---azure-ad-premium--with-azure-ad-connect-and-ad-fs"></a>Fase di abilitazione - Azure AD Premium con Azure AD Connect e AD FS

Fornire indicazioni sulla configurazione di:

- Provisioning utenti, incluse le licenze.

- Sincronizzazione delle directory Azure AD Connect (con sincronizzazione hash e writeback delle password ).

  - Reimpostazione della password self-service (SSPR).

  - Azure Multi-Factor Authentication.

  - Fino a 3 o più integrazioni di un'applicazione SaaS (Software as a Service) con SSO da [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

  - Schermata di accesso personalizzata, con logo, testo e immagini.

  - Self-service e gruppi dinamici (gruppi).

  - Proxy dell'applicazione Azure Active Directory.

  - Azure AD Connect Health.

  - Identity Protection.

  - Privileged Identity Management.

  - Accesso condizionale di Azure Active Directory.

### <a name="enable-phase---intune"></a>Fase di abilitazione - Intune

> [!IMPORTANT]
> FastTrack non supporta la gestione dei PC classica di Windows 10 con Intune. FastTrack supporta solo la gestione di Windows 10 tramite il software MDM (Mobile Device Management) di Intune.

Fornire indicazioni su:

-   Configurazione delle identità da usare con Intune, tramite Active Directory locale o le identità cloud (Azure Active Directory).

-   Concessione di licenze agli utenti finali.

-   Aggiunta di utenti alla sottoscrizione di Intune, definizione dei ruoli di amministratore IT e creazione di gruppi di utenti e di dispositivi.

-   Configurazione dell'autorità di gestione dei dispositivi mobili (MDM, Mobile Device Management) in base alle specifiche esigenze di gestione:

    -   Impostazione di Intune come autorità MDM quando Intune è l'unica soluzione MDM.

    -   Impostazione di System Center Configuration Manager come autorità MDM se è presente un'implementazione esistente di Configuration Manager e si vogliono espandere le funzionalità di gestione con Intune.

    -   Configurazione dei gruppi di test da usare per la convalida dei criteri di gestione MDM.

    -   Esplorazione del portale di amministrazione di Intune per individuare le informazioni su utenti e dispositivi.

    -   Configurazione dei ruoli di Intune (operatore di help desk, amministratori, ecc.)

    -   Configurazione dei servizi e dei criteri di gestione MDM quali:

        -   Distribuzione dell'app per ogni piattaforma supportata tramite collegamenti Web, MSI e/o collegamenti diretti.

        -   Distribuzione di Office ProPlus nei dispositivi Windows 10.

        -   Volume Purchase Program per la distribuzione di app, inclusi VPP di Apple, Windows Store per le aziende e Google Play for Work.

        -   Distribuzione di posta elettronica, reti wireless e profili VPN se si ha un'infrastruttura di Autorità di certificazione esistente, Wi-Fi o VPN nella propria organizzazione.

        -   Configurazione di Microsoft Intune Exchange Connector, quando applicabile.

        -   Profili di configurazione dispositivo per le piattaforme per dispositivi supportate.

    -   Configurazione dei criteri di accesso condizionale.

    -   Configurazione e distribuzione dei criteri di protezione delle app di Intune per ogni piattaforma supportata.

    -   Preparazione delle app line-of-business (LOB) per i criteri di protezione delle app di Intune, con materiale sussidiario per le opzioni disponibili.

    -   Registrazione dei dispositivi di ogni piattaforma supportata in Intune o in Configuration Manager con il servizio Microsoft Intune.

    -   Connessione al data warehouse di Intune.

    -   Integrazione di Intune con Team Viewer per l'assistenza remota, partner Mobile Threat Defense e partner Telecom Expense (licenza dei prodotti di terze parti non inclusa con l'abbonamento di Intune).

    -   Configurazione degli aggiornamenti software per le piattaforme supportate applicabili.

    -   Risorse per la pianificazione dell'adozione da parte degli utenti.

> [!NOTE]
> **Per altre informazioni** vedere [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility).

## <a name="next-steps"></a>Passaggi successivi

[FastTrack Benefit per EMS - Responsabilità dell'utente](fasttrack-center-benefit-process-for-ems-your-responsibilities.md)
