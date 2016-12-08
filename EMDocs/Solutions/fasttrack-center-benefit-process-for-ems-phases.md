---
title: Fasi di caricamento e migrazione
description: Fasi per FastTrack Center Benefit
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: ems
ms.technology: 
ms.assetid: e51f030b-8b08-4fea-96c9-d4ded435a264
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 61241368440bea9a12bbac136466250da91da997
ms.openlocfilehash: 50389fcdfc8f8dd9d2c565b60990449b442d90aa


---

# <a name="onboarding-and-migration-phases"></a>Fasi di onboarding e migrazione
Quando si usano i [Piani e servizi idonei per FastTrack Center Benefit](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Microsoft Azure Active Directory Premium e Microsoft Intune per l'uso, il processo prevede varie fasi. Le sezioni seguenti descrivono ogni fase del processo di onboarding.

Il processo di onboarding prevede quattro fasi principali:

![Le quattro fasi del processo di caricamento di FastTrack](./media/ft-onboarding-benefit.png)


## <a name="initiate-phase"></a>Fase di avvio

Dopo aver acquistato il numero appropriato di licenze, attenersi alle istruzioni nel messaggio di conferma dell'acquisto per associare le licenze al tenant esistente o a un tenant nuovo. Microsoft verifica l'idoneità per FastTrack Center Benefit e tenta di contattare l'utente per offrire assistenza durante il processo di caricamento. È anche possibile richiedere assistenza da parte di [FastTrack Center](http://fasttrack.microsoft.com/) se si è pronti per distribuire questi servizi per l'organizzazione.

Per richiedere assistenza, accedere a [FastTrack Center](http://fasttrack.microsoft.com/) con l'account aziendale o dell'istituto di istruzione, andare al dashboard, espandere **Richiesta di assistenza** a sinistra dello schermo, quindi seguire le istruzioni visualizzate per completare la richiesta. Una volta contattata l'assistenza per il processo di caricamento, verrà definita una programmazione di riunioni online.

Durante questa fase viene illustrato il processo di caricamento, vengono verificati i dati e viene organizzata la riunione iniziale.

![Fase di avvio del caricamento](./media/ft-initiate-phase.png)

## <a name="assess-phase"></a>Fase di valutazione

Una volta avviato il processo di caricamento, Microsoft offre assistenza all'utente per valutare l'ambiente di origine e i requisiti. Vengono eseguiti strumenti per valutare l'ambiente e Microsoft guida l'utente nella valutazione di Active Directory locale, browser Internet, sistemi operativi dei dispositivi client, DNS (Domain Name System), rete, infrastruttura e sistema di identità, qualora fossero necessarie modifiche per il caricamento.

Microsoft offre anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

In base all'installazione corrente, viene suggerito un piano di correzione in modo che l'ambiente di origine sia conforme ai requisiti minimi per garantire il caricamento corretto di EMS o dei sui singoli servizi cloud. Vengono inoltre concordate delle chiamate di controllo appropriate per la fase di correzione.

![Fase di valutazione del caricamento](./media/ft-assess-phase.png)

## <a name="remediate-phase"></a>Fase di correzione
L'utente esegue le attività previste nel piano di correzione nell'ambiente di origine, in modo da soddisfare i requisiti per il caricamento e l'adozione di ogni servizio, come necessario.

![Fase di correzione del caricamento](./media/ft-remediate-phase.png)

Prima di iniziare la fase di abilitazione, vengono verificati i risultati delle attività di correzione per essere certi che l'utente sia pronto a procedere.

## <a name="enable-phase"></a>Fase di abilitazione
Dopo aver completato tutte le attività di correzione, il progetto passa alla configurazione dell'infrastruttura principale, richiesta per l'uso del servizio e il provisioning di ogni servizio cloud EMS idoneo.

**Fase di abilitazione - Funzionalità di base**

L'onboarding di base prevede il provisioning di servizi e l'integrazione di identità e tenant. Include anche la procedura per definire una base per il caricamento di servizi online come Azure AD Premium e Intune.

![Fase di abilitazione del caricamento: funzionalità di base](./media/ft-enable-phase-core-01.png)

![Fase di abilitazione del caricamento: funzionalità di base](./media/ft-enable-phase-core-02.png)

### <a name="enable-phase---azure-ad-premium"></a>Fase di abilitazione – Azure AD Premium

L'ambiente di Azure AD Premium può essere configurato usando la sincronizzazione delle directory di Azure Active Directory Connect e Active Directory Federation Services (AD FS), se necessario.

Per gli scenari di Azure AD Premium che includono la sincronizzazione delle identità locali nel cloud, Microsoft supporterà l'utente aggiungendo gli amministratori IT e gli utenti alla sottoscrizione, configurando i prerequisiti di gestione, configurando Azure AD Premium, impostando la sincronizzazione delle directory e AD FS con lo strumento Azure AD Connect, configurando gli utenti di test e convalidando i casi di utilizzo di base per il servizio.

La configurazione di Azure AD Premium include l'abilitazione delle funzionalità seguenti:

-   Reimpostazione della password self-service (SSPR).

-   Azure Multi-Factor Authentication (Azure MFA).

-   Integrazione di un'applicazione SaaS (Software as a Service) con Single Sign On (SSO) da [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

-   Schermata di accesso personalizzata, con logo, testo e immagini.

-   Self-service e gruppi dinamici (gruppi).

-   Proxy dell'applicazione Azure Active Directory.

-   Azure Active Directory Connect Health.

-   Identity Protection.

-   Privileged Identity Management.

-   Report sull'utilizzo e sulla sicurezza per gli amministratori.

-   Notifiche e avvisi amministrativi.

![Fase di abilitazione del caricamento - Azure AD Premium](./media/ft-enable-phase_aad-premium_adconnect_adfed.png)

### <a name="enable-phase---intune"></a>Fase di abilitazione - Intune

Per Intune, l'utente viene guidato nei preparativi per l'uso di Microsoft Intune per gestire i dispositivi. La procedura esatta dipende dall'ambiente di origine ed è basata sul dispositivo mobile in uso e sulle esigenze di gestione delle app mobili. Le operazioni necessarie possono includere:

-   Concessione di licenze agli utenti finali. Verrà fornita anche assistenza su come attivare i contratti multilicenza per il tenant del servizio cloud Microsoft, se necessario.

-   Configurazione delle identità da usare con Intune, tramite Active Directory locale o le identità cloud.

-   Aggiunta di utenti alla sottoscrizione di Intune, definizione dei ruoli di amministratore IT e creazione di gruppi di utenti e di dispositivi.

-   Configurazione dell'autorità di gestione dei dispositivi mobili (MDM, Mobile Device Management) in base alle specifiche esigenze di gestione:

    -   Impostazione di Intune come autorità MDM quando è l'unica soluzione MDM o è in combinazione con Gestione di dispositivi mobili per Office 365.

    -   Impostazione di System Center Configuration Manager come autorità MDM se è presente un'implementazione esistente di Configuration Manager e si vogliono espandere le funzionalità di gestione con Intune.

        > [!NOTE]
        > Se si vuole solo usare MDM per i dispositivi di proprietà degli utenti finali, i dispositivi condivisi o i dispositivi di tipo chiosco multimediale, la configurazione di un'autorità MDM non è necessaria.

-   Distribuzione di indicazioni relative a MDM per le attività seguenti:

    -   Configurazione dei gruppi di test da usare per la convalida dei criteri di gestione MDM.

    -   Configurazione dei servizi e dei criteri di gestione MDM quali:

        -   Distribuzione dell'applicazione per ogni piattaforma supportata tramite collegamenti Web o collegamenti diretti.

        -   Criteri di accesso condizionale.

        -   Distribuzione di posta elettronica, reti wireless e profili VPN se si ha un'infrastruttura di Autorità di certificazione esistente, Wi-Fi o VPN nella propria organizzazione.

        -   Configurazione di Microsoft Intune Exchange Connector, quando applicabile.

    -   Registrazione dei dispositivi di ogni [piattaforma supportata](https://technet.microsoft.com/library/dn600287.aspx) in Microsoft Intune o in Configuration Manager con il servizio Intune.

-   Distribuzione di indicazioni relative alla gestione delle app mobili (MAM) per:

    -   Configurazione dei criteri MAM per ogni piattaforma supportata.

    -   Configurazione dei criteri di accesso condizionale per le app gestite.

    -   Indirizzamento ai gruppi di utenti appropriati con i criteri MAM descritti in precedenza.

    -   Uso dei report sull'utilizzo delle applicazioni gestite.

-   Distribuzione di indicazioni relative alla gestione dei PC per:

    -   Installazione del software client di Intune, se necessario.

    -   Uso dei report sul software e l'hardware disponibili in Intune.

Microsoft offre anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mam.png)

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mdm-mam_cloudonly.png)

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase-intune-mdm-mam-sccm.png)

**Altre informazioni**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)



<!--HONumber=Nov16_HO4-->


