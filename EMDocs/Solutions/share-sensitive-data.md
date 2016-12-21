---
title: Condividere i dati sensibili internamente ed esternamente | Azure Information Protection
description: "Scenario che descrive come usare Enterprise Mobility + Security per condividere i dati sensibili internamente ed esternamente usando le funzionalità di Microsoft Azure Information Protection."
author: yuridio
ms.author: yurid
manager: swadhwa
ms.date: 12/07/2016
ms.topic: solution
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a996fbf8-ece4-40bc-b866-d4606c230027
ms.reviewer: v-craic
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 02b0e611805ad2214b1b108b8c466590aad7999a
ms.openlocfilehash: d76fa5c4857b12e2eb91de9fb3217ba78ea6a11f


---

# <a name="share-sensitive-data-internally-and-externally"></a>Condividere i dati sensibili internamente ed esternamente

Anche se molte violazioni dei dati sono dovute agli attacchi informatici, gli esperti concordano sul fatto che molte altre sono il risultato di errori umani o di momenti di distrazione che si verificano quando i dipendenti divulgano inavvertitamente dati aziendali sensibili. Applicando i protocolli appropriati per la prevenzione della perdita dei dati e le informazioni di sicurezza, è possibile impedire quasi tutti questi tipi di violazioni.

Per utenti e aziende, la condivisione dei dati è inevitabile, ma, oltre a essere necessaria comporta anche una delle maggiori sfide del settore, ovvero come consentire la condivisione tra dispositivi diversi riducendo al contempo le perdite dei dati condivisi con altri utenti? Il panorama delle minacce è ancora più ampio quando è necessario condividere i dati sensibili all'esterno, ad esempio con i partner, i clienti e altre parti. 

![Diagramma](./media/share-sensitive-data/share-sensitive-data-fig1.png)

In questo contesto, le aziende devono spesso gestire progetti in cui è necessario consentire ai dipendenti di collaborare internamente in silo di dati ed esternamente con fornitori di terze parti, allineando i protocolli di sicurezza alle esigenze aziendali e influenzando il comportamento degli utenti finali per quanto riguarda i processi di classificazione e protezione dei dati. 

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?

Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS aiuta a rispondere a una delle esigenze principali degli ambienti incentrati su dispositivi mobili e cloud, ovvero fornire funzionalità di posta elettronica sicure ai dipendenti che lavorano fuori ufficio. Con EMS si offrirà ai propri dipendenti la possibilità di lavorare in modo sicuro all'interno e all'esterno dell'organizzazione. EMS consente agli amministratori IT di sfruttare il modello di criteri di [Azure Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms) per l'utilizzo della posta elettronica. I diritti di utilizzo sono collegati al messaggio stesso, in modo che la protezione venga applicata online e offline, nonché all'interno e all'esterno del firewall dell'organizzazione.

## <a name="recommended-solution"></a>Soluzione consigliata

Grazie all'integrazione di Azure Rights Management con Rights Management in Exchange Online, EMS consente alle organizzazioni di proteggere i dati che vengono inviati all'esterno dell'organizzazione tramite posta elettronica. È possibile implementare questa soluzione per le istanze locali di Exchange Server e per Exchange Online (Office 365). Sia Information Rights Management che [Office 365 Message Encryption](https://technet.microsoft.com/library/dn569285.aspx) sono basati su e criteri progettati per funzionare con il motore delle regole di trasporto di Exchange. Ciò significa che Microsoft Azure Rights Management consente di configurare facilmente restrizioni dei criteri complesse, con una singola operazione.

Alcune delle funzionalità disponibili con queste soluzioni sono descritte di seguito:

- Protezione della posta elettronica dall'accesso non autorizzato applicando opzioni IRM diverse ai messaggi di posta elettronica.
- Maggiore sicurezza delle informazioni, online o offline, perché i file vengono protetti indipendentemente dalla posizione in cui vengono visualizzati, usando Office Online oppure scaricandoli in un computer locale.
- Facile integrazione con tutti i documenti di Office, per salvaguardare la proprietà intellettuale dell'organizzazione.
- Applicazione di modelli personalizzati in base alle esigenze aziendali in aggiunta all'uso dei modelli predefiniti di Rights Management Services.


## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

Per configurare Exchange Online per supportare Azure RMS, è necessario configurare il servizio IRM (Information Rights Management) per Exchange Online. Per implementare la soluzione, seguire questi passaggi:

1. Integrazione con Exchange: 
    - Exchange Online: abilitare Exchange Online per l'uso di Azure RMS
    - Exchange locale: distribuire il connettore di Azure Rights Management
2. Inviare un documento di Office protetto con Exchange

## <a name="how-to-share-sensitive-data-internally-and-externally"></a>Come condividere i dati sensibili internamente ed esternamente

Le aziende devono consentire ai dipendenti di collaborare internamente in silo di dati ed esternamente con fornitori di terze parti, allineando i protocolli di sicurezza alle esigenze aziendali e influenzando il comportamento degli utenti finali per quanto riguarda i processi di classificazione e protezione dei dati. La condivisione dei dati diventa una parte essenziale del processo e le organizzazioni devono consentirla riducendo nel contempo le probabilità che l'integrità e la privacy dei dati vengano compromesse.

### <a name="step-1-integration-with-exchange"></a>Passaggio 1: Integrazione con Exchange

La protezione di Rights Management viene applicata alla posta elettronica applicando un modello di criteri di Azure Rights Management a un messaggio di posta elettronica. Il primo passaggio per abilitare questa integrazione dipende dalla posizione di Exchange: nel cloud (Exchange Online) o in locale. 

#### <a name="enable-rights-management-integration-with-exchange-online"></a>Abilitare l'integrazione di Rights Management con Exchange Online

Per configurare Exchange Online per supportare Azure RMS, è necessario configurare il servizio IRM (Information Rights Management) per Exchange Online. Nell'articolo [Office 365: configurazione di client e servizi online](https://docs.microsoft.com/rights-management/deploy-use/configure-office365) seguire i passaggi nella sezione [Exchange Online: configurazione di IRM](https://docs.microsoft.com/rights-management/deploy-use/configure-office365#exchange-online-irm-configuration) per configurare Exchange Online per IRM.

L'ultimo passaggio deve essere il test finale per la convalida della configurazione e il risultato dovrebbe essere simile a quello illustrato nella schermata seguente:

![PowerShell](./media/share-sensitive-data/share-sensitive-data-fig2.png)

#### <a name="enable-rights-management-integration-with-exchange-on-premises"></a>Abilitare l'integrazione di Rights Management con Exchange locale

Per configurare l'integrazione di Rights Management con Exchange locale, è necessario configurare il connettore di Microsoft Rights Management (RMS). Questo connettore consente di abilitare le istanze locali esistenti di Exchange Server in modo che usino la funzionalità Information Rights Management (IRM) con il servizio Microsoft Rights Management (Azure RMS) basato sul cloud. È possibile utilizzare questo connettore anche se alcuni utenti si connettono ai servizi online, in uno scenario ibrido.

Esaminare i [prerequisiti per installare il connettore RMS](https://docs.microsoft.com/rights-management/deploy-use/deploy-rms-connector#prerequisites-for-the-rms-connector) e seguire i cinque passaggi illustrati nell'articolo [Installazione e configurazione del connettore di Azure Rights Management](https://docs.microsoft.com/rights-management/deploy-use/install-configure-rms-connector).

### <a name="step-2-send-a-protected-document-using-exchange"></a>Passaggio 2: Inviare un documento protetto con Exchange

Seguire il passaggio 3 dello scenario [Proteggere i dati usando la classificazione, l'assegnazione di etichette e la protezione](infoprotect-secure-classify-scenario.md) per installare l'applicazione RMS sharing. Se è necessario supportare diversi tipi di client, vedere l'articolo [Applicazione Rights Management sharing: installazione e configurazione dei client](https://docs.microsoft.com/rights-management/deploy-use/configure-sharing-app) per altre informazioni su come installare l'applicazione RMS sharing.

Se si vuole condividere un documento di Office, ad esempio direttamente da Word, è sufficiente usare l'icona Condividi file protetto sulla barra multifunzione come illustrato nella figura seguente:

![Condividi file protetto](./media/share-sensitive-data/share-sensitive-data-fig3.png)

Dopo aver fatto clic su questa opzione, verrà visualizzata la finestra di dialogo Condividi file protetto con altri dettagli sulle opzioni per la condivisione del documento, come illustrato nella figura seguente:

![Condividi](./media/share-sensitive-data/share-sensitive-data-fig4.png)

Nella parte superiore di questa finestra è necessario digitare l'indirizzo di posta elettronica dell'utente di destinazione e selezionare il tipo di accesso che si vuole fornire a questo utente. Nella parte inferiore della finestra è anche possibile controllare la data di scadenza del documento e abilitare l'opzione per ricevere un messaggio di posta elettronica ogni volta che un utente tenta di aprire questo documento. Dopo aver effettuato le selezioni appropriate, fare clic su Invia e Outlook aprirà un nuovo messaggio come illustrato nella schermata seguente:

![E-mail](./media/share-sensitive-data/share-sensitive-data-fig5.png)

> [!IMPORTANT] 
> Guardare la presentazione [Collaborate securely using Azure Information Protection](https://myignite.microsoft.com/videos/49947) (Collaborare in modo sicuro usando Azure Information Protection) di Microsoft Ignite per altre informazioni su questo scenario.



<!--HONumber=Dec16_HO2-->


