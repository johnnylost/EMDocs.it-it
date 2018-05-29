---
title: Rilevare attacchi prima che possano provocare danni | Microsoft Docs
description: Uno scenario che descrive come Enterprise Mobility + Security può essere usato per proteggere i dati aziendali da attacchi prima che possano provocare danni tramite Advanced Threat Analytics, Cloud App Security e Azure Active Directory Premium.
author: yuridio
ms.author: yurid
manager: swadhwa
ms.date: 01/23/2017
ms.topic: solution
ms.prod: ''
ms.service: active-directory
ms.technology: ''
ms.assetid: de0a7e70-008b-45c1-bba8-f033b1f62194
ms.reviewer: v-craic
ms.suite: ems
ms.custom: advanced-threat-analytics, cloud-app-security
ms.openlocfilehash: c8d94bb0ff5fdbb45670d93c31a3da0f5b1a859d
ms.sourcegitcommit: 573bba4fa70ce651971ec5bafd9967ebdd6bd6c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
# <a name="detect-attacks-before-they-cause-damage"></a>Rilevare attacchi prima che possano provocare danni
Un ambiente di lavoro sicuro richiede un sistema di rilevamento avanzato in grado di identificare minacce prima che possano causare danni importanti. Le organizzazioni possono usufruire facilmente delle funzionalità di sicurezza Microsoft per rilevare attività sospette nel cloud o localmente.

Un sistema di rilevamento efficace deve individuare attività sospette e bloccare le minacce tramite una visibilità approfondita e un'analisi comportamentale continua. Ciò consente ai responsabili IT di intraprendere azioni immediate contro attacchi rilevati e semplificare il ripristino con un supporto efficiente.


## <a name="how-can-enterprise-mobility--security-help-you"></a>Vantaggi di Enterprise Mobility + Security
Microsoft Enterprise Mobility + Security consente ai responsabili IT di identificare gli utenti malintenzionati nell'organizzazione tramite un'analisi innovativa comportamentale e tecnologie di rilevamento anomalie nel cloud e localmente.  Supporta i responsabili IT nel rilevare attacchi dannosi noti e vulnerabilità di sicurezza note nei sistemi.

## <a name="recommended-solution"></a>Soluzione consigliata
Per soddisfare i requisiti di questo scenario, EMS usa [Advanced Threats Analytics](https://docs.microsoft.com/advanced-threat-analytics/), [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) e [Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium). Con l'implementazione di queste tecnologie, le organizzazioni saranno in grado di:

- Rilevare o identificare un comportamento anomalo tramite analisi comportamentali innovative e tecnologie di rilevamento anomalie sfruttando le funzionalità di Machine Learning
- Rilevare attacchi dannosi noti, ad esempio Pass the Hash, Pass the Ticket, e le vulnerabilità di sicurezza note
- Concentrarsi solo sulle informazioni rilevanti sugli attacchi
- Identificare anomalie e violazioni dei criteri che potrebbero essere indicativi di problemi di sicurezza

La figura seguente riepiloga le funzionalità usate nello scenario e descrive come vengono usate per proteggere le risorse:

![Grafico che illustra le funzionalità di ogni soluzione di prodotto e il relativo funzionamento per proteggere da attacchi.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig1.png)

# <a name="how-to-detect-attacks-before-they-cause-damage"></a>Come rilevare attacchi prima che possano provocare danni
Tradizionalmente, gli investimenti nella sicurezza erano incentrati solo sulla protezione. Oggi è invece fondamentale avere un efficace sistema di rilevamento e risposta. Le organizzazioni IT dovrebbero concentrarsi su un approccio che mira alla protezione, al rilevamento e alla risposta alle minacce.

![Grafico che illustra il processo continuo di protezione, rilevamento e risposta alle minacce.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig2.png)

Gli esperti IT devono esaminare come proteggere in modo appropriato identità, dati, applicazioni, dispositivi e infrastruttura, nel cloud o localmente.  Ciò richiede un approccio alla sicurezza che prende in considerazione tutti gli aspetti, dai sensori al datacenter. In passato, gli amministratori IT si fidavano delle firme di malware per riconoscere le minacce.

Gli strumenti IT di sicurezza tradizionali offrono una protezione limitata contro gli attacchi sofisticati alla sicurezza informatica se un utente malintenzionato si appropria delle credenziali degli utenti. L'impostazione iniziale, la creazione di regole e l'ottimizzazione sono attività complesse che richiedono molto tempo di implementazione. Ogni giorno, si ricevono molti report pieni di falsi positivi. Nella maggior parte dei casi, non si dispone di sufficienti risorse per esaminare tutte le informazioni e, se questo fosse possibile, le informazioni non hanno sempre le risposte appropriate, poiché gli strumenti sono progettati per proteggere il perimetro, ovvero per impedire agli utenti malintenzionati di accedere a sistemi e dati. Oggi gli attacchi alla sicurezza informatica sono molto complessi e richiedono un approccio diverso.

Per mitigare le minacce correnti in questo nuovo panorama di attacchi alla sicurezza informatica, gli esperti IT hanno bisogno di soluzioni innovative di rilevamento delle minacce che usano analisi comportamentali e sistemi di Machine Learning in modo che possano riconoscere rapidamente e completamente le nuove minacce.  Con l'uso di Advanced Threats Analytics e Cloud App Security per rilevare attacchi locali e nel cloud, gli esperti IT possono rispondere rapidamente agli eventi imprevisti prima che possano causare danni importanti nell'ambiente.

Leggere [Pianificazione della capacità di ATA](https://docs.microsoft.com/advanced-threat-analytics/plan-design/ata-capacity-planning) prima di implementare Advanced Threats Analytics localmente e [Prerequisiti di ATA](https://docs.microsoft.com/advanced-threat-analytics/plan-design/ata-prerequisites) per considerazioni generali prima di installare Advanced Threats Analytics. Usare l'[elenco di controllo della preinstallazione](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/preinstall-ata) per verificare se l'infrastruttura è pronta per ricevere ATA. Dopo aver completato questa fase di pianificazione e convalida, è possibile [distribuire Advanced Threat Analytics](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step1). Dopo aver distribuito Advanced Threat Analytics nell'ambiente, la configurazione è minima e ATA inizierà immediatamente a raccogliere informazioni relative all'ambiente e attivare gli avvisi se rileva attacchi dannosi noti. Eseguire il passaggio 1 per usare [Advanced Threat Analytics](https://docs.microsoft.com/advanced-threat-analytics/understand-explore/what-is-ata) per identificare attività sospette localmente.

Per rilevare minacce per le applicazioni cloud, questo scenario usa [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security). Assicurarsi di seguire le [istruzioni generali di installazione](https://docs.microsoft.com/cloud-app-security/general-setup) per configurare Cloud App Security e usare l'opzione [Individuazione cloud](https://docs.microsoft.com/cloud-app-security/set-up-cloud-discovery) per analizzare i log di traffico in relazione al catalogo di app cloud di Cloud App Security. Eseguire il passaggio 2 per usare Cloud App Security per rilevare minacce e violazioni alla conformità.

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
Eseguire questi passaggi per implementare [Advanced Threats Analytics](https://docs.microsoft.com/advanced-threat-analytics/) e [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security):

- Passaggio 1: usare Advanced Threat Analytics (ATA) per rilevare attività sospette localmente
- Passaggio 2: usare Cloud App Security per rilevare minacce e violazioni di conformità per le app cloud  

### <a name="step-1-using-ata-to-detect-suspicious-activity"></a>Passaggio 1: uso di Advanced Threat Analytics per rilevare attività sospette
La ricezione costante di report dagli strumenti di sicurezza tradizionali e la valutazione delle informazioni per individuare gli avvisi importanti e rilevanti può essere un'operazione molto impegnativa. Advanced Threat Analytics offre invece report semplici da leggere, approfonditi e arricchiti di commenti dai social media che consentono agli esperti IT di concentrarsi rapidamente su ciò che è più importante. La presentazione di questa quantità di dati come sequenza temporale offre una prospettiva e una visione più dettagliata su chi, cosa, quando e come è stato eseguito l'accesso ai dati.

Quando si apre la [sequenza temporale dell'attacco](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/working-with-suspicious-activities) in Advanced Threat Analytics, viene visualizzato un report completo sulle attività sospette che indica le [entità](https://docs.microsoft.com/advanced-threat-analytics/plan-design/ata-architecture) coinvolte e offre consigli appropriati:

![Schermata della sequenza temporale degli attacchi con un report su attività sospette.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig3.png)

In questo esempio è incluso un evento che indica un'appropriazione sospetta di identità tramite un attacco Pass-the-ticket. È incluso anche un elenco di consigli che possono essere usati per operazioni di correzione iniziale. In questo esempio, Advanced Threat Analytics ha inviato un avviso perché qualcuno si è impadronito del ticket Kerberos dell'amministratore dal server SHAREDADMIN-SRV per EXTVENDOR-TS e lo ha usato per accedere a DC01. È possibile approfondire il processo di analisi facendo clic su qualsiasi oggetto di questo evento. Ad esempio, facendo clic sul server terminal dei fornitori esterni (EXTVENDOR-TS) si avrà accesso a tutte le [attività sospette](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/working-with-suspicious-activities) nelle quali è stato coinvolto il server.

Advanced Threat Analytics usa Machine Learning con il motore deterministico e il motore di rilevamento per stabilire una comprensione dei modelli di comportamento normale per gli utenti e le entità; tale capacità univoca consente di creare avvisi tempestivi e accurati su una grande varietà di vettori di attacco.


### <a name="step-2-using-cloud-app-security-to-detect-threats-and-policy-violations-for-cloud-apps"></a>Passaggio 2: uso di Cloud App Security per rilevare minacce e violazioni dei criteri per le app cloud

Sempre più organizzazioni stanno adottando app SaaS, non solo per ridurre i costi ma anche per sfruttare vantaggi competitivi, ad esempio un time-to-market più rapido e una migliore collaborazione. Anche se l'azienda non usa applicazioni cloud, è possibile che i dipendenti lo facciano. In base ad alcune ricerche, oltre l'80 percento dei dipendenti ammette di usare app SaaS non approvati nelle loro attività lavorative.

In questa transizione rapida alle applicazioni cloud, è nota la preoccupazione di molte aziende sull'archiviazione di dati aziendali nel cloud e come renderli accessibili ovunque agli utenti senza visibilità completa o controlli. Le soluzioni di sicurezza legacy non sono progettate per proteggere i dati in applicazioni SaaS. Le soluzioni di sicurezza di rete tradizionali, ad esempio i firewall e i sistemi di prevenzione intrusioni, non offrono visibilità nelle transazioni che sono univoche per ogni applicazione e per il traffico fuori sede, inclusa la modalità in cui i dati vengono usati e archiviati. I controlli classici non riescono a offrire una protezione per le app cloud perché monitorano solo un piccolo subset di traffico cloud e hanno una limitata visione sulle attività a livello app.

In che modo è possibile mantenere visibilità, controllo e protezione delle app cloud? Soluzione:

Microsoft Cloud App Security è un servizio completo che offre una visibilità più ampia, controlli più sicuri e una protezione migliorata per le applicazioni cloud. Cloud App Security è progettato per aumentare la visibilità e i controlli locali per le applicazioni cloud.

Cloud App Security non offre solo visibilità e controllo ma anche una protezione da minacce efficace per le applicazioni cloud, migliorata con una estesa ricerca e analisi delle minacce da parte di Microsoft. È possibile identificare eventi imprevisti ad alto rischio di utilizzo e sicurezza e rilevare comportamenti utenti anomali per prevenire minacce.

Quando si accede al dashboard di Cloud App Security, si ha una visione completa dello stato protetto delle app cloud con una sezione dedicata agli avvisi:

![Schermata del dashboard di Cloud App Security con avvisi aperti.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig6.png)

È possibile fare clic sul menu Avvisi per accedere al [centro avvisi](https://docs.microsoft.com/cloud-app-security/monitor-alerts). Il centro avvisi raccoglie gli avvisi di un'ampia gamma di categorie, tra cui l'individuazione delle minacce, gli account con privilegi e le violazioni di conformità.

![Schermata del centro avvisi che visualizza un elenco di tutti gli avvisi.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig5.png)

Il centro avvisi raccoglie tutti i flag rossi identificati da Cloud App Security inclusi anomalie, rilevamento di minacce, violazioni di conformità e account con privilegi. L'euristica avanzata di Machine Learning di Cloud App Security memorizza informazioni su come ogni utente interagisce con un'app cloud e, attraverso l'analisi comportamentale, valuta il rischio in ogni transazione.

Quando si analizza un avviso, è possibile fare clic sul nome dell'avviso per ottenere altre informazioni. Nell'esempio seguente, l'avviso si riferisce a una corrispondenza in [file dei criteri](https://docs.microsoft.com/cloud-app-security/data-protection-policies)*file riservati condivisi pubblicamente*, che viene considerato come priorità alta perché può causare perdite di dati.   

![Schermata di dettagli specifici per uno degli avvisi.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig7.png)

Anche se l'esempio precedente si basava su una violazione dei criteri, Cloud App Security è anche in grado di [rilevare anomalie](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy#anomaly-detection-policy-reference). Cloud App Security ha un periodo di apprendimento iniziale di 7 giorni durante il quale non segnala nuovi utenti, attività, dispositivi o percorsi come anomali. In seguito, ogni sessione viene confrontata con le attività (ad esempio quando gli utenti erano attivi, indirizzi IP, dispositivi e cosi via) rilevate durante il mese precedente e un valore di rischio viene assegnato a queste attività. La descrizione di questo tipo di avviso viene definito "rilevamento di anomalie generale" e se si fa clic su di essa, viene visualizzata una schermata simile alla seguente:

![Schermata che illustra le anomalie rilevate da Cloud App Security.](./media/detect-attacks-before-damage/detect-attacks-before-damage-fig8.png)

In questa pagina, è possibile notare quale utente ha attivato l'avviso, l'indirizzo IP, l'appartenenza al gruppo dell'utente e altre informazioni sui comportamenti sospetti. È possibile visualizzare altri dettagli su questa attività, ad esempio i tentativi di accesso non riusciti, il percorso da cui ha origine l'accesso e l'app usata per eseguire il tentativo di accesso.
