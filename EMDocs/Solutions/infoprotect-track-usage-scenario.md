---
title: Tenere traccia dell'utilizzo dei dati condivisi e rispondere in caso di uso improprio dei dati | Microsoft Docs
description: "Uno scenario che descrive come sia possibile usare Enterprise Mobility + Security per tenere traccia dell'uso dei dati condivisi e rispondere in caso di uso improprio sfruttando le funzionalità di Azure Rights Management."
author: yuridio
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: solution
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c7e6e01a-5796-4bd7-a0c5-847ecfc08a1e
ms.reviewer: v-craic
ms.suite: ems
ms.openlocfilehash: 81e6b6479dcca1a82b37cfc4c832f36e33ac1b7b
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="track-usage-of-shared-data-and-respond-to-data-abuse"></a>Tenere traccia dell'utilizzo dei dati condivisi e rispondere in caso di uso improprio dei dati

Avere visibilità e controllo sui dati condivisi è di fondamentale importanza per tenera traccia dell'uso dei dati, ma anche per rilevare eventuali usi impropri. Al giorno d'oggi la condivisione dei dati è sempre più estesa e le organizzazioni hanno l'esigenza di condividere i dati all'esterno del loro dominio per soddisfare le esigenze aziendali.

In questo contesto è un'esigenza comune per gli utenti non solo condividere i documenti, ma anche monitorare gli accessi ai documenti e revocare l'accesso all'occorrenza. Gli amministratori IT desiderano avere un'esperienza simile a quella che hanno attualmente per la condivisione dei dati con un gruppo di utenti autorizzati, ovvero vogliono mantenere il controllo e poter intraprendere azioni appropriate in merito all'uso o all'uso improprio dei dati. Continuare la lettura per altre informazioni sull'utilità di Enterprise Mobility + Security in questo scenario.

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS offre la soluzione a una delle esigenze principali degli ambienti mobile-first e cloud-first, ovvero come riuscire a condividere i dati mantenendo comunque il controllo e con la possibilità di intraprendere le dovute azioni per reagire rapidamente in caso di problemi. Con EMS si offrirà ai propri dipendenti la possibilità di lavorare in modo sicuro all'interno e all'esterno dell'organizzazione. EMS consente ai proprietari dei documenti e agli amministratori di tenere traccia delle attività sui file confidenziali condivisi con altri utenti. Questi utenti possono visualizzare le attività, ad esempio i destinatari che aprono il file o gli utenti non autorizzati a cui viene negato l'accesso ai file, e possono anche vedere le posizioni geografiche da cui è stato eseguito l'accesso ai file. Basta un solo clic per revocare l'accesso a un file condiviso.

### <a name="recommended-solution"></a>Soluzione consigliata
Grazie all'integrazione di Azure Rights Management è possibile monitorare l'uso dei documenti protetti da parte degli utenti. Se necessario, è anche possibile revocare l'accesso a questi documenti quando si desidera interromperne la condivisione. Questa funzionalità è disponibile per le applicazioni di Office (Word, Excel, Outlook e PowerPoint), tramite il gruppo di RMS, l'opzione Condividi file protetto e Rileva utilizzo. Per i sistemi Windows, è anche possibile usare Esplora file e per tutti gli altri dispositivi supportati si può tenere traccia dell'utilizzo tramite il Web browser. Rilevamento e revoca fanno parte della fase di monitoraggio e risposta del ciclo di vita documento, come illustrato nel diagramma seguente:

![Figura che mostra il ciclo di vita del documento in Azure Rights Management.](./media/infoprotect-track-usage-scenario/infoprotect-track-usage-scenario-fig1.png)

Questo breve video offre una rapida introduzione su come Azure Information Protection consente di tenere traccia facilmente dell'utilizzo dei documenti.

<iframe width="675" height="480" src="https://sec.ch9.ms/ch9/76ac/35499c0a-859c-4a3e-9a5c-fa4e5d0e76ac/AzureRMSDocumentTrackingandRevocation_high.mp4 " frameborder="0" allowfullscreen></iframe>

#### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
Il rilevamento dell'utilizzo dei dati condivisi non è una funzionalità che è necessario configurare, se è già stata eseguita la procedura descritta nello scenario [Condividere i dati sensibili internamente ed esternamente](https://docs.microsoft.com/enterprise-mobility-security/solutions/share-sensitive-data) per configurare Azure Rights Management e l'applicazione client. A questo punto è sufficiente scegliere come tenere traccia dell'utilizzo dei documenti. Le opzioni disponibili sono:

1. Tenere traccia dell'utilizzo con Office
- Tenere traccia dell'utilizzo con il browser
- Revocare l'accesso al documento condiviso

### <a name="how-to-track-usage-of-shared-data-and-respond-to-data-abuse"></a>Come tenere traccia dell'utilizzo dei dati condivisi e rispondere in caso di uso improprio dei dati
Le sezioni seguenti descrivono le opzioni disponibili per tenere traccia dell'utilizzo dei dati condivisi in base a uno scenario specifico.

#### <a name="scenario-1-track-usage-using-microsoft-office"></a>Scenario 1: tenere traccia dell'utilizzo con Microsoft Office
Gli utenti che vogliono usare le applicazioni di Office (Word, Excel e PowerPoint) per ottenere ulteriori informazioni sull'utilizzo dei documenti protetti, possono usare il gruppo di RMS, selezionare l'opzione **Condividi file protetto** e quindi fare clic su **Rileva utilizzo**, come illustrato nella figura seguente:

![Figura che illustra come un utente può impostare l'opzione "Rileva utilizzo" nelle applicazioni di Office.](./media/infoprotect-track-usage-scenario/infoprotect-track-usage-scenario-fig2.png)

Per altre informazioni su questa funzionalità, vedere [Tenere traccia dei documenti e revocarli quando si usa l'applicazione di condivisione RMS](https://docs.microsoft.com/information-protection/rms-client/sharing-app-track-revoke).

#### <a name="scenario-2-track-usage-using-browser"></a>Scenario 2: tenere traccia dell'utilizzo con il browser
In alcuni casi, potrebbe essere necessario monitorare l'utilizzo dei documenti anche se nel dispositivo in uso non è installata un'applicazione di Office. Da un [browser supportato](https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke) visitare il [sito di rilevamento dei documenti](http://go.microsoft.com/fwlink/?LinkId=529562) e accedere con le credenziali personali. Quando si seleziona il documento da monitorare vengono visualizzate le statistiche di utilizzo illustrate nella schermata seguente:

![Figura che illustra le statistiche generali sull'utilizzo di un documento da un Web browser.](./media/infoprotect-track-usage-scenario/infoprotect-track-usage-scenario-fig3.png)

In questa schermata viene mostrato il numero di visualizzazioni e il numero di accessi negati per il numero di mesi durante i quali questo file è stato condiviso. Anche se ogni riquadro contiene un riepilogo che mostra gli utenti che hanno avuto accesso al file, è possibile ottenere altre informazioni facendo clic sul riquadro. Con riferimento all'esempio nella schermata precedente, viene visualizzato il risultato seguente quando si seleziona il riquadro dell'accesso negato:

![Figura che mostra le statistiche relative agli accessi negati per un documento da un Web browser.](./media/infoprotect-track-usage-scenario/infoprotect-track-usage-scenario-fig4.png)

#### <a name="scenario-3-revoke-access-to-shared-document"></a>Scenario 3: revocare l'accesso al documento condiviso

Durante il monitoraggio di un documento le informazioni sull'utilizzo sono un elemento importante per comprendere il comportamento di un utente, ma l'utilità principale deriva dalla possibilità di intraprendere un'azione in base a quanto rilevato grazie al monitoraggio. Si supponga, ad esempio, di scoprire grazie al report di utilizzo che l'accesso viene negato a un utente valido che tenta di accedere a questo documento. A questo punto si deve intraprendere un'azione correttiva per risolvere il problema.

In alcuni casi, potrebbe essere anche necessario affrontare un evento imprevisto relativo alla sicurezza. Ad esempio, si scopre che uno dei documenti con ampia condivisione contiene in effetti informazioni aziendali riservate e il reparto Risorse umane richiede al reparto IT di revocare l'accesso a questo documento. Quando si [revoca un documento](https://docs.microsoft.com/rights-management/rms-client/sharing-app-track-revoke), il documento condiviso non viene eliminato, ma gli utenti autorizzati non potranno più aprirlo. Per revocare l'accesso, è sufficiente fare clic sull'opzione **Revoca l'accesso** disponibile nella pagina di rilevamento dell'utilizzo. Verrà visualizzato un form simile a quello illustrato nella figura seguente:

![Figura che mostra il form Revoca l'accesso che consente di revocare l'accesso a un documento.](./media/infoprotect-track-usage-scenario/infoprotect-track-usage-scenario-fig5.png)

È possibile abilitare l'opzione per informare i destinatari che è stato revocato l'accesso a questo documentati ed è possibile includere un messaggio con la spiegazione del motivo per cui questo documento è stato revocato.
