---
title: Fasi di onboarding e migrazione
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 10/02/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e51f030b-8b08-4fea-96c9-d4ded435a264
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4edfa04ab1ecf371e207497d74aa4c1e2366d7a9
ms.openlocfilehash: 9a41384fc4c7706c715b7c79d2dfd8e42f1d0a5d


---

# Fasi di onboarding e migrazione
Quando si usano i [Piani e servizi idonei per FastTrack Center Benefit](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Azure Active Directory Premium e/o Microsoft Intune per l'uso, il processo prevede varie fasi. Le sezioni seguenti descrivono ogni fase del processo di onboarding.

L'onboarding presenta le seguenti fasi principali:

![Le quattro fasi del processo di caricamento di FastTrack](./media/ft-onboarding-benefit.png)


## Fase di avvio

Dopo aver acquistato il numero appropriato di licenze, attenersi alle istruzioni nel messaggio di conferma dell'acquisto per associare le licenze al tenant esistente o a un tenant nuovo. Microsoft verificherà l'idoneità per FastTrack Center Benefit e contatterà l'utente per offrire assistenza durante il processo di caricamento. È anche possibile richiedere assistenza da parte di [FastTrack Center](http://fasttrack.microsoft.com/) se si è pronti per distribuire questi servizi per l'organizzazione.

Per richiedere assistenza, accedere a [FastTrack Center](http://fasttrack.microsoft.com/) (http://fasttrack.microsoft.com) con il proprio account aziendale o dell'istituto di istruzione, fare clic sull'azienda (o aggiungerla, se necessario), fare clic sulla scheda dei servizi e scegliere l'opzione per richiedere assistenza per Microsoft Intune o Azure Active Directory Premium. Una volta contattato il supporto tecnico di onboarding, verrà impostata la pianificazione di riunioni online.

Durante questa fase verrà illustrato il processo di onboarding, verranno verificati i dati e verrà impostata la riunione iniziale.

![Fase di avvio del caricamento](./media/ft-initiate-phase.png)

## Fase di valutazione

Una volta avviato il processo di onboarding, Microsoft assisterà l'utente nel valutare l'ambiente di origine e i requisiti. Verranno eseguiti strumenti per valutare l'ambiente e Microsoft guiderà l'utente nella valutazione di Active Directory locale, browser Internet, sistemi operativi dei dispositivi client, DNS, rete, infrastruttura e sistema di identità, qualora fossero necessarie modifiche per l'onboarding.

Microsoft offrirà anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

In base all'installazione corrente, verrà suggerito un piano di correzione in modo che l'ambiente di origine sia conforme ai requisiti minimi per garantire il caricamento di EMS o dei sui singoli servizi cloud. Verranno inoltre stabilite delle chiamate di controllo appropriate per la fase di correzione.

![Fase di valutazione del caricamento](./media/ft-assess-phase.png)

## Fase di correzione
Se necessario, l'utente eseguirà le attività previste nel piano di correzione nell'ambiente di origine, in modo da soddisfare i requisiti per il caricamento e l'adozione di ogni servizio.

![Fase di correzione del caricamento](./media/ft-remediate-phase.png)

Prima di iniziare la fase di abilitazione, verranno verificati i risultati delle attività di correzione per essere certi che l'utente sia pronto a procedere.

## Fase di abilitazione
Dopo aver completato tutte le attività di correzione, il progetto passa alla configurazione dell'infrastruttura principale, richiesta per l'uso del servizio e il provisioning di ogni servizio cloud EMS idoneo.

**Fase di abilitazione - Funzionalità di base**

L'onboarding di base prevede il provisioning di servizi e l'integrazione di identità e tenant. Include anche la procedura per definire una base per l'onboarding di servizi online come Azure Active Directory Premium e Microsoft Intune.

![Fase di abilitazione del caricamento: funzionalità di base](./media/ft-enable-phase-core-01.png)

![Fase di abilitazione del caricamento: funzionalità di base](./media/ft-enable-phase-core-02.png)

### Fase di abilitazione: Azure Active Directory Premium

L'ambiente di Azure Active Directory Premium può essere configurato usando la sincronizzazione delle directory di Azure Active Directory Connect e Active Directory Federation Services (AD FS), se necessario.

Per gli scenari di Azure Active Directory Premium che includono la sincronizzazione delle identità locali nel cloud, Microsoft supporterà l'utente aggiungendo amministratori IT e utenti alla sottoscrizione, configurando i prerequisiti di gestione, configurando Azure Active Directory Premium, impostando la sincronizzazione delle directory e Active Directory Federation Services (AD FS), usando lo strumento Azure Active Directory Connect, configurando utenti di test e convalidando i principali casi d'uso del servizio.

L'installazione di Azure Active Directory Premium include l'abilitazione delle funzionalità seguenti:

-   Reimpostazione della password self-service (SSPR).

-   Azure Multi-Factor Authentication (Azure MFA).

-   Integrazione di un'applicazione software come servizio (SaaS) con Single Sign On (SSO) da [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

-   Schermata di accesso personalizzata, con logo, testo e immagini.

-   Self-service e gruppo dinamico (gruppi).

-   Proxy dell'applicazione Azure Active Directory.

-   Azure Active Directory Connect Health.

-   Identity Protection.

-   Privileged Identity Management.

-   Report sull'utilizzo e sulla sicurezza per gli amministratori.

-   Notifiche e avvisi amministrativi.

![Fase di abilitazione del caricamento: AADP](./media/ft-enable-phase_aad-premium_adconnect_adfed.png)

### Fase di abilitazione – Microsoft Intune

In base alle esigenze di gestione dei dispositivi mobili e delle applicazioni mobili, verranno fornite informazioni su come usare Microsoft Intune per gestire i dispositivi. La procedura esatta dipende dall'ambiente di origine e può includere:

-   Concessione di licenze agli utenti finali. Se necessario, verrà fornita anche assistenza su come attivare i contratti multilicenza per il tenant del servizio cloud Microsoft.

-   Configurazione delle identità da usare con Microsoft Intune, tramite Active Directory locale o le identità cloud.

-   Aggiunta di utenti alla sottoscrizione di Microsoft Intune, definizione dei ruoli di amministratore IT e creazione di gruppi di utenti e di dispositivi.

-   Configurazione dell'autorità di gestione dei dispositivi mobili in base alle specifiche esigenze di gestione:

    -   Impostare Microsoft Intune come autorità MDM quando è l'unica soluzione MDM o è in combinazione con Gestione di dispositivi mobili per Office 365.

    -   Se è presente un'implementazione esistente di System Center Configuration Manager e si vogliono espandere le funzionalità di gestione con Microsoft Intune, impostare Configuration Manager come autorità MDM.

        > [!NOTE]
        > Se si vuole solo usare Gestione di applicazioni mobili nei dispositivi di proprietà degli utenti finali, nei dispositivi condivisi o nei dispositivi di tipo chiosco multimediale, la configurazione di un'autorità MDM non è necessaria.

-   Se Gestione di dispositivi mobili rientra nel proprio ambito, verranno fornite istruzioni su:

    -   Configurazione dei gruppi di test da usare per la convalida dei criteri di gestione MDM.

    -   Configurazione dei servizi e dei criteri di gestione MDM quali:

        -   Distribuzione dell'applicazione per ogni piattaforma supportata tramite collegamenti Web o collegamenti diretti.

        -   Criteri di accesso condizionale.

        -   Distribuzione di profili di posta elettronica, Wi-Fi e VPN.

        -   Configurazione di Microsoft Intune Exchange Connector, quando applicabile.

    -   Registrazione dei dispositivi di ogni [piattaforma supportata](https://technet.microsoft.com/library/dn600287.aspx) in Microsoft Intune o in Configuration Manager con il servizio Microsoft Intune.

-   Se Gestione di applicazioni mobili (MAM) rientra nel proprio ambito o se si vuole integrare la soluzione MDM Microsoft o di terze parti esistente con i criteri MAM, verranno fornite istruzioni su:

    -   Configurazione dei criteri MAM per ogni piattaforma supportata.

    -   Configurazione dei criteri di accesso condizionale per le app gestite.

    -   Indirizzamento ai gruppi di utenti appropriati con i criteri MAM descritti in precedenza.

    -   Uso dei report sull'utilizzo delle applicazioni gestite.

-   Se la gestione del PC rientra nel proprio ambito, verranno fornite istruzioni su:

    -   Installazione del software client di Intune, se necessario.

    -   Uso dei report sul software e l'hardware disponibili in Intune.

Microsoft offrirà anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mam.png)

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mdm-mam_cloudonly.png)

**Altre informazioni**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)


<!--HONumber=Oct16_HO1-->


