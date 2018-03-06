---
title: "Responsabilità di Microsoft"
description: "Responsabilità di Microsoft quando i clienti usano FastTrack Center Benefit"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 102ff22c60aa58cddbc07ddd485a57e9e7340a92
ms.sourcegitcommit: 024fad70d2c4976f039e3e572c7334927375b17e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="microsoft-responsibilities"></a>Responsabilità di Microsoft

Ecco le responsabilità di Microsoft durante il processo di onboarding.

## <a name="general"></a>Generale

-   Viene fornita assistenza remota per le attività di configurazione necessarie, come illustrato nelle descrizioni dettagliate delle fasi.

-   All'utente vengono forniti documentazione, strumenti software, console di amministrazione e script disponibili per ridurre o eliminare le attività di configurazione.

## <a name="initiate-phase"></a>Fase di avvio

-   Contattare l'utente entro 30 giorni dall’acquisto di licenze idonee per un nuovo tenant.

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

-   Fornire un elenco di controllo della correzione.

## <a name="remediate-phase"></a>Fase di correzione

-   Effettuare conferenze telefoniche con l'utente in base a una pianificazione concordata per esaminare lo stato di avanzamento delle attività di correzione.

-   Fornire assistenza per l'esecuzione di strumenti allo scopo di identificare e risolvere problemi e per l'interpretazione dei risultati.

## <a name="enable-phase"></a>Fase di abilitazione
Fornire indicazioni su:

-   Attivazione del tenant dei servizi online di Microsoft.

-   Configurazione di protocolli TCP/IP e porte del firewall.

-   Configurazione del DNS per i servizi idonei.

-   Convalida di connettività ai servizi online di Microsoft.

-   Per un ambiente a foresta singola:

    -   Installazione di un server di sincronizzazione delle directory tra Servizi di dominio Active Directory (AD DS) e i Microsoft Online Services idonei, se necessario.

    -   Configurazione della sincronizzazione delle password (hash della password) in Microsoft Intune (Azure Active Directory) con lo strumento Azure Active Directory Connect.

        > [!NOTE]
        > Sviluppo e implementazione per estensioni di regole personalizzate non rientrano nell'ambito.

-   Per una singola foresta se la destinazione sono le identità federate: installazione e configurazione di Active Directory Federation Services (AD FS) per l'autenticazione di domini locali con Intune in una configurazione a tolleranza di errore con singolo sito, se necessario.

    > [!NOTE]
    > Per tutte le configurazioni di più foreste le distribuzioni di AD FS non rientrano nell'ambito.

-   Test della funzionalità SSO (Single Sign-On), se distribuita.

### <a name="enable-phase---microsoft-azure-active-directory-premium"></a>Fase di abilitazione - Microsoft Azure Active Directory Premium

Fornire indicazioni su:

-   Attivazione del tenant di Azure AD Premium.

-   Configurazione delle porte del firewall.

-   Configurazione di DNS per i servizi idonei.

-   Convalida della connettività nei servizi di Azure AD Premium.

-   Per un ambiente a foresta singola:

    -   Installazione di una sincronizzazione delle directory tra Active Directory Domain Services (AD DS) e Azure AD Connect, se richiesto.

    -   Configurazione di un metodo di autenticazione (sincronizzazione degli hash delle password o autenticazione pass-through) con lo strumento Azure AD Connect.

-   Per un ambiente a più foreste:

    -   Installazione della sincronizzazione di Azure AD Connect, configurata per scenari a più foreste.
-   Per ambienti a foresta singola e a più foreste:
    -   Configurazione dell'autenticazione pass-through di Azure Active Directory, se necessario.
    -   Configurazione dell'accesso Single Sign-On facile (SSO) di Azure Active Directory, se necessario. 
        > [!NOTE]
        > L'autenticazione pass-through di Azure Active Directory per ambienti a più foreste è supportata se sono presenti trust tra foreste tra le foreste di Active Directory e se il routing dei suffissi nome è configurato correttamente. È possibile installare altri agenti su più server locali per offrire disponibilità elevata per le richieste di accesso. 

    - Per altre informazioni, vedere [Autenticazione pass-through di Azure Active Directory - Avvio rapido] (https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start#step-1-check-prerequisites) e [Accesso Single Sign-On facile di Azure Active Directory: guida introduttiva] (https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start#step-1-check-prerequisites).
    - Per altre informazioni sui limiti dell'autenticazione pass-through, vedere [Autenticazione pass-through di Azure Active Directory - Limitazioni correnti] (https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-current-limitations).
    - Per altre informazioni sui problemi di Single Sign-On facile, vedere [Risolvere i problemi relativi all'accesso Single Sign-On facile di Azure Active Directory] (https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-sso).
  
        > [!NOTE]
        > La sincronizzazione hash e il writeback delle password supportano più foreste. Tuttavia, gli altri scenari di writeback non sono supportati.

    -   Configurazione della sincronizzazione tra le foreste locali di Active Directory e la directory di Microsoft Azure Active Directory Premium (Azure Active Directory).

        > [!NOTE]
        > Sviluppo e implementazione per estensioni di regole personalizzate non rientrano nell'ambito.

-   Per una singola foresta se la destinazione sono le identità federate:

    -   Installazione e configurazione di AD FS per l'autenticazione di domini locali con Azure AD Premium in una configurazione a tolleranza di errore con singolo sito, se necessario.

    > [!NOTE]
    > Per tutte le configurazioni di più foreste le distribuzioni di AD FS non rientrano nell'ambito.

-   Test della funzionalità SSO (se distribuita).

### <a name="enable-phase---azure-ad-premium--with-azure-ad-connect-and-ad-fs"></a>Fase di abilitazione - Azure AD Premium con Azure AD Connect e AD FS

Fornire indicazioni sulla configurazione di:

-   Provisioning utenti, incluse le licenze.

-   Sincronizzazione delle directory Azure AD Connect (con sincronizzazione hash e writeback delle password ).

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

  - Report sull'utilizzo e sulla sicurezza per gli amministratori.

  - Notifiche e avvisi amministrativi.

### <a name="enable-phase---intune"></a>Fase di abilitazione - Intune
Fornire indicazioni su:

-   Concessione di licenze agli utenti finali.

-   Configurazione delle identità da usare con Intune, tramite Active Directory locale o le identità cloud.

-   Aggiunta di utenti alla sottoscrizione di Intune, definizione dei ruoli di amministratore IT e creazione di gruppi di utenti e di dispositivi.

-   Configurazione dell'autorità di gestione dei dispositivi mobili (MDM, Mobile Device Management) in base alle specifiche esigenze di gestione:

    -   Impostazione di Intune come autorità MDM quando è l'unica soluzione MDM o è in combinazione con Gestione di dispositivi mobili per Office 365.

    -   Impostazione di System Center Configuration Manager come autorità MDM se è presente un'implementazione esistente di Configuration Manager e si vogliono espandere le funzionalità di gestione con Intune.

        > [!NOTE]
        > Se si vuole solo usare MDM nei dispositivi di proprietà degli utenti finali, nei dispositivi condivisi o nei dispositivi di tipo chiosco multimediale, la configurazione di un'autorità MDM non è necessaria.

    -   Configurazione dei gruppi di test da usare per la convalida dei criteri di gestione MDM.

    -   Configurazione dei servizi e dei criteri di gestione MDM quali:

        -   Distribuzione dell'applicazione per ogni piattaforma supportata tramite collegamenti Web o collegamenti diretti.

        -   Criteri di accesso condizionale.

        -   Distribuzione di posta elettronica, reti wireless e profili VPN se si ha un'infrastruttura di Autorità di certificazione esistente, Wi-Fi o VPN nella propria organizzazione.

        -   Configurazione di Microsoft Intune Exchange Connector, quando applicabile.

    -   Registrazione dei dispositivi di ogni piattaforma supportata in Intune o in Configuration Manager con il servizio Microsoft Intune.

    -   Uso dei report sull'inventario hardware e software.

    -   Configurazione dei criteri MAM per ogni piattaforma supportata.

    -   Configurazione dei criteri di accesso condizionale per le app gestite.

    -   Indirizzamento ai gruppi di utenti appropriati con i criteri MAM descritti in precedenza.

    -   Uso dei report sull'utilizzo delle applicazioni gestite.

    -   Installazione del software client di Intune, se necessario.

    -   Uso dei report sul software e l'hardware disponibili in Intune.

**Altre informazioni**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
