---
title: Proteggere i dati dagli errori degli utenti | Information Protection di Azure Active Directory
description: "Scenario che descrive come usare Enterprise Mobility + Security proteggere i dati aziendali dagli errori degli utenti e impedire la perdita dei dati usando le funzionalità di Cloud App Security e di Azure Information Protection."
author: yuridio
ms.author: yurid
manager: swadhwa
ms.date: 10/24/2016
ms.topic: solution
ms.prod: 
ms.service: cloud-app-security
ms.technology: techgroup-identity
ms.assetid: 0af3894c-7b0e-4c0c-8874-31e041d81300
ms.reviewer: v-craic
ms.suite: ems
ms.custom: information-protection
translationtype: Human Translation
ms.sourcegitcommit: 02b0e611805ad2214b1b108b8c466590aad7999a
ms.openlocfilehash: 669042461511939695717de1d5d22c14c071923c


---

# <a name="protect-data-against-user-mistakes"></a>Proteggere i dati dagli errori degli utenti

Benché la transizione alla mobilità e al cloud abbia incrementato sostanzialmente la produttività dei dipendenti, la complessa interazione tra utenti, dispositivi, app e dati, in locale come nel cloud, ha prodotto nuovi punti ciechi per i team IT. Anche se le organizzazioni possono scegliere di non adottare questa transizione, i dipendenti lo hanno già fatto. Con l'aumentare delle interazioni tra questi componenti e la sofisticatezza dei vettori di attacco, la sicurezza resta una tra le prime sfide per le organizzazioni. Il personale IT deve lottare per mantenere visibilità, controllo e protezione dei dati aziendali.

Le risorse di controllo dei dati che proteggono i dati aziendali dagli errori degli utenti sono un fattore importante per la sicurezza delle risorse e favoriscono la produttività degli utenti.

## <a name="how-can-enterprise-mobility-security-help-you"></a>Vantaggi di Enterprise Mobility + Security

Enterprise Mobility + Security (EMS) offre al personale IT maggiore visibilità delle attività di utenti, dispositivi e dati, in locale e nel cloud.  Con EMS il personale IT può proteggere i dati aziendali dagli errori degli utenti con controlli e applicazione più severi.  Sarà possibile monitorare il rilevamento dei rischi tramite potenti report e analisi di utenti, traffico di caricamento/download, modelli di utilizzo e transazioni per le applicazioni rilevate.

## <a name="recommended-solution"></a>Soluzione consigliata

Per soddisfare i requisiti di questo scenario, EMS usa [Cloud App Security](https://technet.microsoft.com/library/mt489024.aspx) e [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection). Implementando queste tecnologie, le organizzazioni otterranno:

- Visibilità completa di shadow IT e utilizzo delle app cloud da parte degli utenti
- Criteri dati e di controllo di livello granulare per la protezione dati continua nelle app cloud
- Classificazione e protezione persistenti dei dati, che garantiscono la protezione continua dei dati, indipendentemente dalla loro posizione di archiviazione o dagli utenti con cui vengono condivisi
- Possibilità di condividere i dati in tutta sicurezza con persone all'interno e all'esterno dell'organizzazione
- Controlli intuitivi per la classificazione e la protezione dei dati
- Visibilità e controllo dei dati condivisi per utenti e IT

La figura seguente riepiloga le funzionalità usate nello scenario e descrive come vengono usate per proteggere le risorse:

![Grafica che mostra l'integrazione di Cloud App Security e Azure Information Protection per proteggere i dati in locale e nel cloud.](./media/protect-data-user-mistake/protect-data-user-mistake-fig1-1.png)

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

Seguire questi passaggi per implementare [Cloud App Security](https://technet.microsoft.com/library/mt668458.aspx) e [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection):

- Passaggio 1: Individuare le app cloud in uso e controllarle con criteri
- Passaggio 2: Proteggere i dati in locale o nel cloud

## <a name="how-to-protect-data-against-user-mistakes"></a>Come proteggere i dati dagli errori degli utenti

Le applicazioni cloud vengono usate oggi dalla maggior parte delle organizzazioni e presto arriverà il momento in cui nel cloud verrà archiviata una quantità di dati aziendali maggiore rispetto agli ambienti locali. Spesso gli utenti useranno app SaaS dai propri dispositivi senza che la società ne sia al corrente o abbia dato il proprio consenso, provocando un aumento dell'utilizzo dello shadow IT nel cloud. Questa conclusione proviene da alcuni studi, che mostrano che l'80% dei dipendenti ha ammesso di usare app SaaS non approvate per attività aziendali. [Cloud App Security](https://technet.microsoft.com/library/mt657567.aspx) offre una panoramica dettagliata di tutte le app cloud usate nell'organizzazione. Identifica tutti gli utenti e gli indirizzi IP che accedono a un'applicazione. Esegue inoltre una valutazione dei rischi per oltre 13.000 app cloud e offre un punteggio di rischio automatico per ogni app in base a più di 60 parametri.

Seguire il passaggio 1 per rilevare le app cloud nell'ambiente e implementare criteri per il controllo di queste app. La seconda fase di questa soluzione implementa [Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/get-started/requirements) per proteggere e classificare i dati, in modo da prevenire gli errori degli utenti e l'utilizzo non corretto dei dati.

### <a name="step-1-discover-cloud-apps-in-use-and-control-them-with-policy"></a>Passaggio 1: Individuare le app cloud in uso e controllarle con criteri

Il primo passaggio per usare Cloud App Security consiste nell'[individuare le app](https://technet.microsoft.com/en-us/library/mt657567.aspx). Se si ignora questo passaggio, non ci saranno app da analizzare e da limitare tramite criteri. Se il processo di individuazione non è stato avviato, l'opzione di individuazione nel dashboard di Cloud App Security visualizzerà il messaggio seguente:

![Screenshot che mostra il messaggio indicante che l'utente non ha ancora caricato un log di Cloud Discovery.](./media/protect-data-user-mistake/protect-data-user-mistake-fig2-1.png)

L'individuazione delle app in uso nell'intera organizzazione è il primo passaggio per garantire la protezione dei dati aziendali sensibili. Al termine del processo di individuazione, sarà possibile visualizzare un elenco delle app individuate nel [dashboard di Cloud Discovery](https://technet.microsoft.com/en-us/library/mt727946.aspx).

![Screenshot che mostra il dashboard di Cloud Discovery e un elenco delle app individuate.](./media/protect-data-user-mistake/protect-data-user-mistake-fig3.png)

Ogni app ha un punteggio che rappresenta la credibilità e l'affidabilità delle app cloud. Quando si accede alla classificazione dell'app, si può notare che per la creazione di questa classificazione sono state usate tre categorie: Generale, Sicurezza e Conformità. Ogni categoria ha determinati attributi che vengono testati durante il processo di individuazione. Se un attributo non è completamente conforme, viene mostrato come parziale ed è possibile accedere ai dettagli dell'attributo per capire perché viene indicato in questo modo.

![Screenshot che mostra i dettagli dell'attributo "Intestazioni di sicurezza HTTP".](./media/protect-data-user-mistake/protect-data-user-mistake-fig4.png)

Il passaggio successivo consiste nel controllare tramite criteri il comportamento delle applicazioni individuate. Questa funzionalità permette al personale IT di ottimizzare le applicazioni individuate e il livello di rischio associato per l'organizzazione. Esistono diversi tipi di criteri. I criteri da creare per primi dipendono dai requisiti aziendali dell'organizzazione. Poiché i criteri di rilevamento delle anomalie sono attivati per impostazione predefinita, non è necessario configurare un nuovo criterio per farli funzionare. È tuttavia possibile ottimizzare i tipi di anomalie riguardo ai quali si vuole essere avvisati nei criteri predefiniti.

![Screenshot che mostra come selezionare un tipo di criterio da creare.](./media/protect-data-user-mistake/protect-data-user-mistake-fig5.png)

Dopo aver configurati i criteri, è possibile indagare sulle potenziali violazioni ai criteri attualmente definiti. In questo scenario specifico, si vuole verificare se nel cloud vengono condivise informazioni personali. Le informazioni su questo tipo di attività sono disponibili tramite Criteri file. I criteri a livello di file che verranno esaminati sono i criteri di conformità delle informazioni personali. Lo scopo di questi criteri è identificare i file contenenti informazioni personali condivisi pubblicamente, nonché fornire opzioni per l'indagine e la prevenzione.

![Screenshot che mostra come esaminare il tipo Criteri file per individuare possibili violazioni.](./media/protect-data-user-mistake/protect-data-user-mistake-fig6.png)

In questo caso specifico, esistono tre corrispondenze per questi criteri, ovvero tre file che corrispondono ai criteri. È possibile fare clic su uno dei file per esaminarne nome e percorso.

### <a name="step-2-protect-data-on-premises-or-in-the-cloud"></a>Passaggio 2: Proteggere i dati in locale o nel cloud

Prima di implementare questa soluzione, esaminare i requisiti di Azure Information Protection e assicurarsi che Azure Rights Management sia attivato.

Microsoft Azure Information Protection aiuta a classificare i dati e ad applicarvi etichette al momento della creazione. È quindi possibile applicare la protezione (crittografia più autenticazione più diritti utente) ai dati sensibili. Le etichette di classificazione e la protezione sono persistenti e seguono sempre i dati perché questi siano identificabili e protetti in ogni momento, indipendentemente dalla posizione di archiviazione e dagli utenti con cui vengono condivisi. Se si prevede di implementare criteri di protezione delle informazioni ed etichette, attenersi alle seguenti linee guida:



- Classificare i dati in base alla sensibilità
- Iniziare con i dati più sensibili
- Il personale IT può impostare regole automatiche, che gli utenti possono integrare
- Associare azioni, ad esempio indicazioni visive e protezione

Benché Azure Information Protection includa etichette predefinite, è possibile personalizzarle e creare etichette o etichette secondarie visibili agli utenti sulla barra di Information Protection.

> [!NOTE]
> Le etichette sono metadati scritti nei documenti. Il testo delle etichette non è crittografato in modo che altri sistemi, ad esempio un motore DLP, possano leggerle.

Nell'esempio seguente è possibile osservare etichette secondarie personalizzate create nell'etichetta Secret:

![Screenshot che mostra etichette secondarie personalizzate create nell'etichetta Secret. ](./media/protect-data-user-mistake/protect-data-user-mistake-fig7.png)


Dopo aver definito l'uso delle etichette (predefinite o personalizzate), [configurare un'etichetta per applicare la protezione di Rights Management](https://docs.microsoft.com/en-us/rights-management/information-protection/configure-policy-protection#to-configure-a-label-to-apply-rights-management-protection).

Con Azure Information Protection, i controlli di classificazione e protezione dei dati sono integrati in Office e in altre applicazioni comuni. Questa integrazione offre opzioni semplici di un solo clic per proteggere i dati usati dagli utenti. Nel portale di Azure un amministratore può applicare modelli predefiniti, come numeri di carta di credito o codici fiscali, come condizione per la classificazione automatica. In alternativa, è possibile usare motivi di testo ed espressioni regolari per definire una stringa o un motivo personalizzato.

Quando si configurano le condizioni per un'etichetta, è possibile assegnare automaticamente un'etichetta a un documento o messaggio di posta elettronica oppure è possibile richiedere agli utenti di selezionare l'etichetta consigliata. Leggere [Come configurare le condizioni per la classificazione automatica e consigliata per Azure Information Protection](https://docs.microsoft.com/en-us/rights-management/information-protection/configure-policy-classification) per altre informazioni su come eseguire questa configurazione.

> [!NOTE]
> Per altre informazioni su classificazione e protezione dei dati, vedere [Proteggere i dati usando la classificazione, l'assegnazione di etichette e la protezione](https://docs.microsoft.com/en-us/enterprise-mobility-security/solutions/infoprotect-secure-classify-scenario).



<!--HONumber=Dec16_HO2-->


