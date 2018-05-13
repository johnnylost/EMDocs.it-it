---
title: Fasi di caricamento e migrazione
description: Fasi per FastTrack Center Benefit
keywords: ''
author: andredm7
ms.author: andredm
manager: ''
ms.date: 04/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e51f030b-8b08-4fea-96c9-d4ded435a264
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: e63644b2e8db81f6293dbad4ca4de14dbe40ecac
ms.sourcegitcommit: 0863dce817862f00068614f2c62698784eb76d84
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="onboarding-phases"></a>Fasi di onboarding

Quando si usano i [Piani e servizi idonei per FastTrack Center Benefit](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Microsoft Azure Active Directory Premium e Microsoft Intune per l'uso, il processo prevede varie fasi. Le sezioni seguenti descrivono ogni fase del processo di onboarding.

Il processo di onboarding prevede quattro fasi principali:

![Le quattro fasi del processo di caricamento di FastTrack](./media/ft-onboarding-benefit.png)


## <a name="initiate-phase"></a>Fase di avvio

Dopo aver acquistato il numero appropriato di licenze, attenersi alle istruzioni nel messaggio di conferma dell'acquisto per associare le licenze al tenant esistente o a un tenant nuovo. Microsoft verifica l'idoneità per FastTrack Center Benefit e tenta di contattare l'utente per offrire assistenza durante il processo di caricamento.

> [!NOTE]
> È anche possibile richiedere assistenza da parte di [FastTrack Center](http://fasttrack.microsoft.com/) se si è pronti per distribuire questi servizi per l'organizzazione.

### <a name="to-request-assistance"></a>Per richiedere assistenza

1. Passare a [FastTrack Center](http://fasttrack.microsoft.com/) e accedere con l'account aziendale o dell'istituto di istruzione.

2. Nel dashboard clienti scegliere **Vai a FastTrack** nella parte inferiore destra della pagina.

3. Nel dashboard FastTrack espandere **Richiesta di assistenza** nella parte inferiore destra della pagina e seguire le istruzioni visualizzate per completare la richiesta.

Dopo aver avviato l'assistenza per l'onboarding, FastTrack programma le riunioni online con l'utente per discutere del processo di onboarding, verificare i dati e definire una riunione di inizio della collaborazione.

![Fase di avvio del caricamento](./media/ft-initiate-phase.png)

## <a name="assess-phase"></a>Fase di valutazione

Dopo l'avvio del processo di caricamento, FastTrack Center offre all'utente l'assistenza necessaria per valutare l'ambiente di origine e i requisiti. Vengono eseguiti strumenti per valutare l'ambiente e gli specialisti FastTrack guidano l'utente nella valutazione di Active Directory locale, browser Internet, sistemi operativi dei dispositivi client, DNS (Domain Name System), rete, infrastruttura e sistema di identità, con lo scopo di determinare se sono necessarie modifiche per l'onboarding.

FastTrack Center offre anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

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
> [!NOTE]
> WAP è l'acronimo di Web Application Proxy (proxy applicazione Web). SSL è l'acronimo di Secure Sockets Layer. SDS è l'acronimo di School Data Sync. Per altre informazioni su SDS, vedere [Introduzione a Microsoft School Data Sync](https://go.microsoft.com/fwlink/?linkid=871480).

> [!NOTE]
> Un metodo di autenticazione gestita include, senza limitazioni, la sincronizzazione degli hash delle password. Identity Integration è un'attività da svolgere una sola volta e non include la migrazione o la disattivazione di metodi di autenticazione esistenti, quali l'autenticazione gestita o federata.

### <a name="enable-phase---azure-ad-premium"></a>Fase di abilitazione – Azure AD Premium

L'ambiente di Azure AD Premium può essere configurato usando la sincronizzazione delle directory di Azure Active Directory Connect e Active Directory Federation Services (AD FS), se necessario.

Per gli scenari di Azure AD Premium che includono la sincronizzazione delle identità locali nel cloud, Microsoft supporterà l'utente aggiungendo gli amministratori IT e gli utenti alla sottoscrizione, configurando i prerequisiti di gestione, configurando Azure AD Premium, impostando la sincronizzazione delle directory con l'autenticazione gestita e AD FS mediante lo strumento Azure AD Connect, configurando gli utenti di test e convalidando i casi d'uso di base per il servizio.

La configurazione di Azure AD Premium include l'abilitazione delle funzionalità seguenti:

-   Reimpostazione della password self-service (SSPR).

-   Azure Multi-Factor Authentication (Azure MFA).

-   Fino a 3 o più integrazioni di un'applicazione SaaS (Software as a Service) con Single Sign On (SSO) da [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

-   Schermata di accesso personalizzata, con logo, testo e immagini.

-   Self-service e gruppi dinamici (gruppi).

-   Proxy dell'applicazione Azure Active Directory.

-   Azure Active Directory Connect Health.

-   Identity Protection.

-   Privileged Identity Management.

-   Accesso condizionale di Azure Active Directory.

![Fase di abilitazione del caricamento - Azure AD Premium](./media/ft-enable-phase_aad-premium_adconnect_adfed.png)

### <a name="enable-phase---intune"></a>Fase di abilitazione - Intune

Per Intune, l'utente viene guidato nei preparativi per l'uso di Microsoft Intune per gestire i dispositivi. La procedura esatta dipende dall'ambiente di origine ed è basata sul dispositivo mobile in uso e sulle esigenze di gestione delle app mobili. Le operazioni necessarie possono includere:

-   Concessione di licenze agli utenti finali. Verrà fornita anche assistenza su come attivare i contratti multilicenza per il tenant del servizio cloud Microsoft, se necessario.

-   Configurazione delle identità da usare con Intune, tramite Active Directory locale o le identità cloud.

-   Aggiunta di utenti alla sottoscrizione di Intune, definizione dei ruoli di amministratore IT e creazione di gruppi di utenti e di dispositivi.

-   Configurazione dell'autorità di gestione dei dispositivi mobili (MDM, Mobile Device Management) in base alle specifiche esigenze di gestione:

    -   Impostazione di Intune come autorità MDM quando è l'unica soluzione MDM o è in combinazione con Gestione di dispositivi mobili per Office 365.

    -   Impostazione di System Center Configuration Manager come autorità MDM se è presente un'implementazione esistente di Configuration Manager e si vogliono espandere le funzionalità di gestione con Intune.

-   Distribuzione di indicazioni relative a MDM per le attività seguenti:

    -   Configurazione dei gruppi di test da usare per la convalida dei criteri di gestione MDM.

    -   Configurazione dei servizi e dei criteri di gestione MDM quali:

        -   Distribuzione dell'applicazione per ogni piattaforma supportata tramite collegamenti Web o collegamenti diretti.

        -   Criteri di accesso condizionale.

        -   Distribuzione di posta elettronica, reti wireless e profili VPN se si ha un'infrastruttura di Autorità di certificazione esistente, Wi-Fi o VPN nella propria organizzazione.

        -   Configurazione di Microsoft Intune Exchange Connector, quando applicabile.

        -   Connessione al data warehouse di Intune

        -   Integrazione di Intune con:
            -   Team Viewer per l'assistenza remota. La sottoscrizione di Team Viewer è obbligatoria.

            -   Soluzioni partner Mobile Threat Defense (MTD). La sottoscrizione di Mobile Threat Defense è obbligatoria.

            -   Soluzione di gestione delle spese per telecomunicazioni. La sottoscrizione della soluzione di gestione delle spese per telecomunicazioni è obbligatoria.

            -   Windows Defender Advanced Threat Protection. Le licenze di Windows E5 o Microsoft 365 E5 sono obbligatorie.

    -   Registrazione dei dispositivi di ogni [piattaforma supportata](https://technet.microsoft.com/library/dn600287.aspx) in Microsoft Intune o in Configuration Manager con il servizio Intune.

-   Materiale sussidiario per Protezione app di Intune (gestione app) su:

    -   Configurazione dei criteri di protezione delle app per ogni piattaforma supportata.

    -   Configurazione dei criteri di accesso condizionale per le app gestite.

    -   Indirizzamento ai gruppi di utenti appropriati con i criteri MAM descritti in precedenza.

    -   Uso dei report sull'utilizzo delle applicazioni gestite.

-   Distribuzione di indicazioni relative alla gestione dei PC per:

    -   Installazione del software client di Intune, se necessario.

    -   Uso dei report sul software e l'hardware disponibili in Intune.

    > [!IMPORTANT]
    > FastTrack non supporta la gestione dei PC classica di Windows 10 con Intune. FastTrack supporta solo la gestione dei dispositivi Windows 10 tramite il software MDM (Mobile Device Management) di Intune.

Microsoft offre anche informazioni aggiuntive su come adottare correttamente i servizi idonei.

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mam.png)

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase_intune_mdm-mam_cloudonly.png)

![Fase di abilitazione del caricamento: Intune](./media/ft-enable-phase-intune-mdm-mam-sccm.png)

> [!NOTE]
> **Per altre informazioni** vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility).

## <a name="next-steps"></a>Passaggi successivi

[FastTrack Benefit per EMS - Responsabilità di Microsoft](fasttrack-center-benefit-process-for-ems-fasttrack-responsibilities.md)
