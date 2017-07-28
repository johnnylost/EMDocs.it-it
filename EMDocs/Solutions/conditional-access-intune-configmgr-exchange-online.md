---
title: Accesso condizionale - Exchange Online, Intune, Configuration Manager
description: Usare Configuration Manager, Exchange Online e Intune per gestire l'accesso alla posta elettronica e proteggere i dati di posta elettronica nei dispositivi mobili.
keywords: 
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06921361-9475-46e6-9368-3cc44c84b22f
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 47f4298d833bcc910f769046ec018f270e75d246
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="deploy-exchange-online-with-microsoft-intune-and-configuration-manager"></a>Distribuire Exchange Online con Microsoft Intune e Configuration Manager
Ora che si sono lette con attenzione le [indicazioni sull'architettura per la protezione di documenti e messaggi di posta elettronica aziendali](architecture-guidance-for-protecting-company-email-and-documents.md) è possibile procedere alla distribuzione di una soluzione.

Se si usano già System Center Configuration Manager ed Exchange Online, è possibile incorporare Intune in modo da gestire l'accesso alla posta elettronica e proteggere i dati di posta elettronica nei dispositivi mobili. Il processo di alto livello per l'implementazione di questa soluzione è il seguente:

-   Creare i criteri di conformità che definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme ai criteri di accesso condizionale.

-   Avviare l'applicazione dell'accesso condizionale.

-   Facoltativamente, configurare il connettore Exchange Server per Exchange Online. Questo connettore è necessario solo a scopo di report. Non è necessario per applicare l'accesso condizionale.

## <a name="conditional-access-control-flow-for-exchange-online"></a>Flusso di controllo accesso condizionale per Exchange Online
Questo diagramma mostra il flusso di controllo per i client che provano ad accedere alla posta elettronica di Exchange Online. A e B possono essere eseguiti prima dell'applicazione dell'accesso condizionale.

![Diagramma di flusso di controllo dell'accesso condizionale in Configuration Manager con Intune ed Exchange Online](./media/ProtectEmail/Hybrid-Exchange-Online-CA-architecture.png)

-   Microsoft Intune: gestisce i criteri di conformità e di accesso condizionale per il dispositivo

-   Microsoft Azure Active Directory: autentica l'utente e fornisce lo stato di conformità del dispositivo

-   Configuration Manager: gestisce la registrazione del dispositivo e fornisce i report, se abilitati

-   Exchange Online: applica l'accesso alla posta elettronica in base allo stato del dispositivo

## <a name="before-you-begin"></a>Prima di iniziare
Assicurarsi che l'ambiente presenti questi requisiti per l'implementazione di questa soluzione.

-   Installare e assegnare i servizi di Exchange a un [certificato digitale valido ](https://technet.microsoft.com/library/dd351044.aspx) acquistato da un'autorità di certificazione pubblica attendibile.

-   Verificare che sia in esecuzione System Center 2012 R2 Configuration Manager SP1 con aggiornamento cumulativo 1 o versione successiva.

-   Configurare un account (amministratore locale o di dominio) con le autorizzazioni per eseguire i cmdlet di Exchange Server seguenti:

    Clear-ActiveSyncDevice

    Get-ActiveSyncDevice

    Get-ActiveSyncDeviceAccessRule

    Get-ActiveSyncDeviceStatistics

    Get-ActiveSyncMailboxPolicy

    Get-ActiveSyncOrganizationSettings

    Get-ExchangeServer

    Get-Recipient

    Set-ADServerSettings

    Set-ActiveSyncDeviceAccessRule

    Set-ActiveSyncMailboxPolicy

    Set-CASMailbox

    New-ActiveSyncDeviceAccessRule

    New-ActiveSyncMailboxPolicy

    Remove-ActiveSyncDevice

## <a name="deployment-steps"></a>Passaggi per la distribuzione
Seguire questi passaggi per distribuire la soluzione Exchange Online:

### <a name="step-1-create-compliance-policies-and-deploy-to-users"></a>Passaggio 1: Creare criteri di conformità e distribuirli agli utenti.
I criteri di conformità definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme ai criteri di accesso condizionale. Per creare i criteri di conformità, seguire i passaggi in [Criteri di conformità in Configuration Manager](https://technet.microsoft.com/library/mt131417.aspx) .

Se si vuole avere la possibilità di rimuovere tutti i messaggi di posta elettronica aziendale da un dispositivo iOS quando non fa più parte dell'azienda, è necessario creare e distribuire un profilo di posta elettronica e quindi impostare i criteri di conformità che specificano che i profili di posta elettronica sono gestiti da Intune. È necessario distribuire il profilo di posta elettronica allo stesso set di utenti a cui sono destinati questi criteri di conformità.

![Screenshot che illustra la pagina "Regole" della Creazione guidata criteri di conformità in cui è possibile specificare che un profilo di posta elettronica deve essere gestito da Intune](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

Se si specificano questi criteri di conformità, un utente che ha già configurato il proprio account di posta elettronica dovrà rimuoverlo manualmente. Intune quindi lo aggiungerà nuovamente attraverso il processo di registrazione descritto in [Esperienza utente finale di accesso condizionale](end-user-experience-conditional-access.md).

Dopo aver creato i criteri di conformità, selezionare il nome del criterio di conformità nell'elenco e fare clic su **Distribuisci**.

### <a name="step-2-configure-conditional-access-policy"></a>Passaggio 2: Configurare i criteri di accesso condizionale.
Prima di tutto, decidere come e quando si vuole applicare l'accesso condizionale e quali dipendenti ne saranno interessati. Seguire quindi i passaggi elencati in [Accesso condizionale per la posta elettronica di Exchange in Configuration Manager](https://technet.microsoft.com/library/mt131421.aspx) per abilitare i criteri di accesso condizionale per Exchange Online.

> [!NOTE]
> I criteri di accesso condizionale devono essere configurati nella console di Intune. I passaggi seguenti iniziano con l'accesso alla console di Intune tramite Configuration Manager. Se richiesto, accedere con le stesse credenziali usate per configurare il connettore tra Configuration Manager e Intune.

### <a name="step-3-optional-install-and-configure-an-exchange-server-connector"></a>Passaggio 3: (*facoltativo*) Installare e configurare un connettore Exchange Server.
Configuration Manager supporta un solo connettore in un'organizzazione Exchange.

> [!IMPORTANT]
> Prima di installare il connettore Exchange Server, confermare il supporto della versione di Microsoft Exchange usata da parte di Configuration Manager. Per altre informazioni, vedere [Configurazioni supportate per Configuration Manager](https://technet.microsoft.com/library/gg682077.aspx).

Per installare e configurare il connettore Exchange Server, seguire i passaggi illustrati nell'argomento [Come gestire i dispositivi mobili utilizzando Configuration Manager e Exchange](https://technet.microsoft.com/library/gg682001.aspx) .

## <a name="verification-steps"></a>Passaggi di verifica
Se è stato configurato il connettore Exchange Server facoltativo per questa soluzione, è possibile usare lo strumento di registro traccia di Configuration Manager per aprire il file EasDisc.log (nella cartella Microsoft Configuration Manager/Logs in cui è installato Configuration Manager). Cercare il file di log "Exchange Connector" per trovare informazioni sull'eventuale esecuzione dei Exchange Connector e sul numero di dispositivi connessi.

![Screenshot che illustra il file EasDisc.log aperto nello strumento per il log di traccia di Configuration Manager](./media/ProtectEmail/Hybrid-Onprem-Eas-DiscLog-Sample.PNG)

Lo strumento per il log di traccia di Configuration Manager è incluso in [System Center 2012 R2 Configuration Manager Toolkit](https://www.microsoft.com/download/details.aspx?id=50012).

## <a name="reporting"></a>Reporting
Se è stato configurato il connettore Exchange Server facoltativo, è possibile usare la console di Configuration Manager per visualizzare informazioni specifiche sui dispositivi che sono stati individuati da Exchange Connector. Per i dispositivi a cui viene applicato l'accesso condizionale, è possibile visualizzare lo stato corrente di ogni dispositivo, l'ultima volta che il dispositivo si è connesso al server Exchange e così via.

Nella console di Configuration Manager fare clic su **Asset e conformità** e quindi fare clic su **Dispositivi**. È possibile visualizzare lo stato corrente di ogni dispositivo (In quarantena o Consentito) nella colonna **Stato di accesso di Exchange** . Aggiungere questa colonna se non è già visualizzata facendo clic con il pulsante destro del mouse sull'area della barra del titolo della colonna. È anche possibile visualizzare l'ora dell'ultima sincronizzazione riuscita per ogni dispositivo come riportato da Exchange aggiungendo la colonna **Ultima sincronizzazione riuscita in Exchange Server** .

![Screenshot che illustra un elenco di dispositivi nella console di Configuration Manager](./media/ProtectEmail/Hybrid-Onprem-Verify-Devices-State.png)

Se si esegue SQL Server Reporting Services (SSRS), è possibile visualizzare un report di accesso condizionale che mostra lo stato di conformità dei dispositivi, se è stato installato e in esecuzione Exchange Connector e lo stato di accesso EAS. Fornirà anche  informazioni sulla registrazione di Active Directory, l'attivazione EAS, nonché il proprietario del dispositivo.

![Screenshot che illustra un esempio di report di SQL Server Reporting Services](./media/ProtectEmail/Hybrid-Reports-CA.png)

Per visualizzare i report SSRS, è necessario aver installato un ruolo report nel server primario:

1.  In Configuration Manager fare clic su **Amministrazione &gt; Configurazione della gerarchia &gt; Configurazione del sito &gt; Server e ruoli del sistema del sito**.

2.  Selezionare un server e fare clic su **Aggiungi ruoli del sistema del sito** per aprire l'aggiunta guidata ruoli del sistema del sito.

3.  Nella pagina Selezione ruolo del sistema selezionare la casella di controllo **Punto di Reporting Services** . Il punto di Reporting Services mostra i report relativi alla gestione dei client.

4.  Fare clic su **Avanti**.

Di seguito viene illustrato lo stato della distribuzione dei criteri di configurazione:

![Screenshot che illustra lo stato della distribuzione dei criteri di configurazione](./media/ProtectEmail/Hybrid-Reports-Deployment-Status.png)

### <a name="latency"></a>Latenza
Ai dispositivi che usano l'autenticazione moderna l'accesso condizionale viene applicato immediatamente. Per i dispositivi connessi tramite il protocollo EAS, può verificarsi un ritardo massimo di sei ore prima che venga applicata l'accesso condizionale, in base all'impostazione predefinita. Durante questo periodo, un dispositivo può essere considerato conforme.

## <a name="where-to-go-from-here"></a>Come proseguire
Dopo aver distribuito una soluzione per la protezione della posta elettronica aziendale e dei dati di questa all'interno dei dispositivi mobili, è possibile scoprire di più sull'[esperienza dell'utente finale relativa all'accesso condizionale](end-user-experience-conditional-access.md). Ciò consente di prepararsi ad affrontare i problemi che potrebbero verificarsi quando gli utenti finali registrano dispositivi specifici.
