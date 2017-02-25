---
title: Proteggere i dati usando la classificazione, l&quot;assegnazione di etichette e la protezione | Microsoft Docs
description: "Uno scenario che descrive come usare Enterprise Mobility + Security per classificare, assegnare un&quot;etichetta e proteggere i dati usando le funzionalità di Microsoft Azure Information Protection."
author: yuridio
ms.author: yurid
manager: swadhwa
ms.date: 02/21/17
ms.topic: solution
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 65409d5c-4f1b-4026-86e9-e65e1c4fe2b4
ms.reviewer: v-craic
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 34d04195000f7cdb5a9efdfa31788a12cc8d8d5b
ms.openlocfilehash: a2fc2e045c413707ad9d53e738b1eec6457c3a95


---

# <a name="secure-data-using-classification-labeling-and-protection"></a>Proteggere i dati usando la classificazione, l'assegnazione di etichette e la protezione

Al giorno d'oggi la condivisione delle informazioni viene eseguita da più dispositivi e all'esterno della società.  Diventa fondamentale garantire che i dati aziendali critici non vengano compromessi in questo processo e contemporaneamente consentire agli utenti di condividere in modo sicuro i dati necessari per svolgere il lavoro. Con pratiche come l'outsourcing sempre più diffuse può essere necessario condividere dati aziendali riservati con appaltatori e fornitori. Poiché non tutti i contenuti necessitano della stessa protezione, alle società viene richiesto di identificare i dati da proteggere.

Continuare la lettura per altre informazioni sull'utilità di Enterprise Mobility + Security in questo scenario.

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?

Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS offre la soluzione a una delle esigenze principali degli ambienti che usano dispositivi mobili e cloud, ovvero inviare dati sicuri ai dipendenti fuori sede. Con EMS si offrirà ai propri dipendenti la possibilità di lavorare in modo sicuro all'interno e all'esterno dell'organizzazione. EMS consente agli amministratori IT di usare Azure Information Protection per proteggere i dati aziendali a livello di file. L'uso di questa funzionalità garantisce la protezione dei dati indipendentemente dalla posizione di archiviazione, dalla condivisione e dall'uso permanente o temporaneo.

## <a name="recommended-solution"></a>Soluzione consigliata

Azure Information Protection consente alle organizzazioni di classificare, assegnare un'etichetta e proteggere i dati al momento della creazione o della modifica. Con Azure Information Protection gli utenti possono:

- Classificare i dati in base alla sensibilità e aggiungere etichette manualmente o automaticamente
- Proteggere i dati mediante crittografia, autenticazione e diritti di utilizzo
- Abilitare un'esperienza intuitiva e non intrusiva per gli utenti finali

L'organizzazione ha anche accesso a funzionalità di rilevamento e reporting dettagliato che consentono di verificare cosa accade ai dati condivisi per poterli gestire in modo migliore. La figura seguente riassume il ciclo di vita della protezione delle informazioni:

![Ciclo di vita della protezione delle informazioni](./media/infoprotect-secure-classify-scenario/infoprotect-secure-classify-scenario-fig1.png)

Questo breve video offre una rapida introduzione su come Azure Information Protection semplifica la classificazione, l'assegnazione di etichette e la protezione delle informazioni anche quando viene usato all'esterno dell'organizzazione.

<iframe src="https://channel9.msdn.com/Shows/Mechanics/An-Introduction-to-Microsoft-Azure-Information-Protection/player" width="560" height="315" allowFullScreen frameBorder="0"></iframe>

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

Seguire questi passaggi per implementare la classificazione, l'assegnazione di etichette e la protezione dei dati usando Azure Information Protection:

- Passaggio 1: Preparazione per la classificazione e la protezione dei dati
- Passaggio 2: Configurare i criteri di protezione delle informazioni e le etichette
- Passaggio 3: Implementare la classificazione automatica basata sul contenuto
- Passaggio 4: Configurare le condizioni per la classificazione automatica e consigliata

## <a name="how-to-secure-data-using-classification-labeling-and-protection-with-azure-information-protection"></a>Come proteggere i dati usando la classificazione, l'assegnazione di etichette e la protezione con Azure Information Protection

Le aziende devono identificare i dati che necessitano di protezione e i dati per i quali non è necessario lo stesso livello di protezione. I passaggi che seguono descrivono le attività principali che è necessario eseguire per consentire ai responsabili IT di implementare Azure Information Protection.

### <a name="step-1-preparing-for-document-protection-and-content-classification"></a>Passaggio 1: Preparazione per la protezione dei documenti e la classificazione dei contenuti

Prima di implementare questa soluzione, rivedere i [requisiti di Azure Information Protection](/information-protection/get-started/requirements) e assicurarsi che Azure Rights Management sia attivato. Se è attivato, verrà visualizzata la schermata seguente nel portale di Azure:

![Portale di Azure](./media/infoprotect-secure-classify-scenario/infoprotect-secure-classify-scenario-fig2.png)

Quando si attiva Azure Rights Management è possibile proteggere i dati importanti usando le applicazioni e i servizi supportati da questa soluzione di protezione delle informazioni. È anche possibile gestire e monitorare i file e i messaggi di posta elettronica protetti di proprietà dell'azienda. È necessario attivare Azure Rights Management per poter usare le funzionalità di Rights Management in Office, SharePoint ed Exchange per proteggere i file sensibili o riservati.

### <a name="step-2-configure-information-protection-policies-and-labels"></a>Passaggio 2: Configurare i criteri di protezione delle informazioni e le etichette

Se si prevede di implementare criteri di protezione delle informazioni ed etichette, attenersi alle seguenti linee guida:

- Classificare i dati in base alla sensibilità
- Iniziare con i dati più sensibili
- I responsabili IT possono impostare regole automatiche che gli utenti possono integrare
- Associare azioni, ad esempio indicazioni visive e protezione

Nella figura seguente è riportato un esempio di implementazione:

![Classificazione](./media/infoprotect-secure-classify-scenario/infoprotect-secure-classify-scenario-fig3.png)

Sebbene Azure Information Protection includa etichette predefinite, è possibile [personalizzarle](/information-protection/deploy-use/configure-policy-new-label) e creare etichette ed etichette secondarie visibili agli utenti sulla barra di Information Protection.

> [!IMPORTANT]
> Le etichette sono metadati scritti nei documenti. Il testo delle etichette non è crittografato in modo che altri sistemi, ad esempio un motore DLP, possano leggerle.

Nell'esempio seguente sono visibili etichette secondarie personalizzate create nell'etichetta **Secret**:

![Label](./media/infoprotect-secure-classify-scenario/infoprotect-secure-classify-scenario-fig4.png)

Dopo aver definito l'uso delle etichette (predefinite o personalizzate), [configurare un'etichetta per applicare la protezione di Rights Management](/information-protection/deploy-use/configure-policy-new-label).

### <a name="step-3-implement-content-based-automatic-classification"></a>Passaggio 3: Implementare la classificazione automatica basata sul contenuto

Con Azure Information Protection, i controlli di classificazione e protezione dei dati sono integrati in Office e in altre applicazioni comuni. Questa integrazione offre opzioni semplici di un solo clic per proteggere i dati usati dagli utenti. Nel portale di Azure è possibile applicare motivi predefiniti, ad esempio numeri di carta di credito o codici fiscali, come condizione della classificazione automatica. In alternativa, è possibile usare motivi di testo ed espressioni regolari per definire una stringa o un motivo personalizzato.

Quando si configurano le condizioni per un'etichetta, è possibile assegnare automaticamente un'etichetta a un documento o messaggio di posta elettronica oppure è possibile richiedere agli utenti di selezionare l'etichetta consigliata. Leggere [Come configurare le condizioni per la classificazione automatica e consigliata per Azure Information Protection](/information-protection/deploy-use/configure-policy-classification) per altre informazioni su come eseguire questa configurazione.


### <a name="step-4-configure-conditions-for-automatic-and-recommended-classification"></a>Passaggio 4: Configurare le condizioni per la classificazione automatica e consigliata

Gli amministratori IT possono impostare criteri per l'applicazione automatica della classificazione e della protezione ai dati. I criteri possono essere basati anche sul contenuto su cui si sta lavorando e possono essere configurati per richiedere agli utenti la classificazione suggerita. Le condizioni predefinite sono le seguenti:

- Codice SWIFT
- Numero di carta di credito
- ABA Routing Number (Codice ABA)
- USA Social Security Number (SSN) (Numero di previdenza sociale USA - SSN)
- International Banking Account Number (IBAN)

Leggere le [informazioni sulle condizioni predefinite](/information-protection/deploy-use/configure-policy-classification#information-about-the-built-in-conditions) per altri dettagli su questo tipo di configurazione.



<!--HONumber=Feb17_HO4-->


