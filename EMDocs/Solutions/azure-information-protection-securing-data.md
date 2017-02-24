---
title: Ruolo di Azure Information Protection nella protezione dei dati | Microsoft Docs
description: In questo articolo viene descritto il ruolo di Azure Information Protection nella protezione dei dati aziendali.
author: yuridio
ms.author: yurid
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: solution
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2f906e2e-3d99-40e6-b5cc-8d903fcda444
ms.reviewer: v-craic
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bf2418b68e40b60508447fc5400f4acfc5c6b1b3
ms.openlocfilehash: 17f2a0b6991d05af2a6f000af48e9fc085221a4d


---

# <a name="the-role-of-azure-information-protection-in-securing-data"></a>Il ruolo di Azure Information Protection nella protezione dei dati

[Azure Information Protection (AIP)](/information-protection/understand-explore/what-is-information-protection) consente di classificare, assegnare etichette e proteggere i dati tramite la crittografia. Con Azure Information Protection gli amministratori IT possono eseguire le operazioni seguenti:

- Classificare automaticamente messaggi di posta elettronica e documenti in base a regole preimpostate
- Aggiungere indicatori a contenuto, ad esempio intestazioni, piè di pagina e filigrane personalizzate
- Proteggere i file aziendali riservati con Rights Management, che consente le operazioni seguenti:
    - Usare chiavi RSA di 2048 bit per la crittografia a chiave pubblica e l'algoritmo SHA-256 per operazioni di firma
    - Crittografare i file per un gruppo specifico di destinatari sia interni che esterni all'organizzazione
    - Applicare un insieme di diritti per limitare l'usabilità del file    
    - Decrittografare il contenuto in base a identità e autorizzazione utente nei criteri per i diritti di utilizzo

Queste funzionalità consentono alle aziende di avere un maggiore controllo end-to-end sui dati. In questo contesto Azure Information Protection svolge un ruolo importante nella protezione dei dati aziendali.

> [!IMPORTANT]
> Per altre informazioni sul funzionamento di Azure Information Protection, leggere [Funzionamento di Azure RMS: dietro le quinte](/information-protection/understand-explore/how-does-it-work).

## <a name="the-state-of-enterprise-protection-today"></a>Lo stato di protezione aziendale di oggi

Molte aziende moderne non usano tecnologie di protezione, nonostante la condivisione di documenti e messaggi di posta elettronica in testo non crittografato e responsabili dei dati che non sanno con certezza quali utenti hanno accesso a contenuto con privilegi. Molte tecnologie di protezione, ad esempio SMIME, sono complicate e gli ACL (Access Control List, Elenco di controllo di accesso) non sono necessariamente applicabili a messaggi di posta elettronica e documenti.

![Nessuna protezione documenti](./media/azure-information-protection-securing-data/aip-securing-data-fig1.png)

In un ambiente sempre meno protetto Azure Information Protection garantisce un nuovo sistema di protezione. Inoltre, in un momento in cui il tema della protezione diventa sempre più d'interesse e alle organizzazioni non è possibile garantire una protezione del 100% sempre e ovunque, Azure Information Protection, se distribuito correttamente, può aumentare il livello di protezione di un'organizzazione.

## <a name="security-principles-for-sharing-content"></a>Principi di protezione per la condivisione del contenuto

Quando un'organizzazione usa Azure Information Protection, gli amministratori IT hanno pieno controllo del dispositivo client e della gestione delle identità utente. In questo modo si crea la giusta piattaforma di attendibilità per la condivisione delle informazioni all'interno dell'organizzazione. L'invio di informazioni all'esterno dell'organizzazione è invece di natura meno attendibile. Esistono alcuni principi che è necessario considerare nella scelta del tipo di protezione delle informazioni. Durante la valutazione dei rischi, considerare i punti seguenti:

- Il destinatario ha accesso fisico a un dispositivo non gestito e ha pertanto il controllo di tutto ciò che accade nel dispositivo.
- Il destinatario è autenticato con un grado di attendibilità correlato alla non-rappresentazione.

Se l'amministratore IT non ha il controllo del dispositivo o dell'identità, non può monitorare quel che accade alle informazioni protette. Nel momento in cui un utente esegue l'autenticazione e apre le informazioni protette, le informazioni non sono più sotto controllo. A questo punto, i destinatari che rispettano i criteri di contenuto vengono considerati attendibili.

È impossibile bloccare completamente un destinatario esterno malintenzionato con accesso autorizzato al contenuto protetto. Azure Information Protection consente tuttavia di stabilire dei limiti etici e di usare applicazioni abilitate per permettere agli utenti non malintenzionati di accedere al documento. Azure Information Protection interviene nel caso di attendibilità implicita entro il limite di accesso definito in base all'identità.

Rilevare e limitare l'accesso futuro è invece più semplice. Il rilevamento dei documenti è una funzionalità di Azure Information Protection che consente di tenere traccia dell'accesso. Grazie a questa funzionalità l'organizzazione può revocare l'accesso a un documento specifico o revocare l'accesso a un utente.

Se il contenuto è molto sensibile e l'organizzazione non considera attendibile il destinatario, è estremamente importante aumentare la protezione del contenuto. È consigliabile concentrarsi sulla protezione e definire controlli di accesso nel documento.

## <a name="identity-based-security"></a>Protezione basata sulle identità

Nelle sezioni seguenti vengono illustrati tre scenari principali di attacchi a contenuto protetto e viene spiegato come la combinazione di controlli dell'ambiente e Azure Information Protection può limitare l'accesso al contenuto di utenti malintenzionati.

### <a name="attacks-by-unauthorized-users"></a>Attacchi da parte di utenti non autorizzati

Azure Information Protection si fonda sul presupposto che l'accesso al contenuto protetto è basato su identità autenticata e autorizzazione. Ciò significa che *senza autenticazione* o *autorizzazione* Azure Information Protection *non concede accesso*. Questo è il primo motivo per distribuire Azure Information Protection. Consente infatti alle aziende di passare da uno stato di accesso illimitato a uno stato in cui l'accesso alle informazioni si basa su un'autenticazione e autorizzazione utente.

Grazie a questa funzione di Azure Information Protection, le aziende possono creare raggruppamenti di informazioni. Possono ad esempio isolare le informazioni riservate al reparto delle risorse umane all'interno del reparto stesso e mantenere riservate al reparto finanziario le informazioni di carattere prettamente finanziario. Azure Information Protection assicura così *almeno un accesso basato sull'identità*.

Il diagramma sotto illustra un esempio, in cui l'utente Bob invia un documento a Tom. In questo caso Bob lavora nel reparto finanziario mentre Tom è nel reparto vendite. Tom non può accedere al documento se non sono stati concessi i diritti.

![Nessun accesso](./media/azure-information-protection-securing-data/aip-securing-data-fig2.png)

In questo scenario il risultato è che Azure Information Protection può bloccare gli attacchi provenienti da utenti non autorizzati. Per altre informazioni sui controlli crittografici in Azure Information Protection, vedere [Controlli crittografici usati in Azure RMS: algoritmi e lunghezze delle chiavi](/information-protection/understand-explore/how-does-it-work).

### <a name="access-by-malicious-programs-on-behalf-of-users"></a>Accesso da parte di programmi dannosi per conto di utenti

L'accesso di programmi dannosi per conto di un utente è qualcosa che solitamente accade a insaputa dell'utente. Trojan horse, virus e altri malware sono esempi classici di programmi dannosi che possono agire per conto dell'utente. Se uno di questi programmi riesce a rappresentare l'identità dell'utente o a sfruttare i sui privilegi per eseguire un'azione, può usare l'[SDK di Azure Information Protection ](/information-protection/develop/developers-guide) per decrittografare il contenuto per conto di un utente ignaro. Poiché questa operazione avviene nel contesto dell'utente, non esiste un modo semplice per impedire questo tipo di attacco.

![Programmi dannosi](./media/azure-information-protection-securing-data/aip-securing-data-fig3.png)

In questo caso è necessario migliorare la protezione dell'identità dell'utente per ridurre la possibilità che applicazioni non autorizzate assumano il controllo dell'identità di un utente. Azure Active Directory offre diverse soluzioni che consentono di proteggere l'identità dell'utente, una tra queste l'autenticazione a due fattori. Per proteggere l'identità dell'utente, è consigliabile analizzare anche le altre funzionalità di Azure AD Identity Protection.

La protezione delle identità non rientra nell'ambito di Azure Information Protection, ma è nell'area di autenticazione di responsabilità dell'amministratore.

> [!IMPORTANT]
> Per rimuovere la presenza di programmi dannosi è anche importante concentrarsi su un ambiente "gestito". Questo argomento sarà trattato nel prossimo scenario.

### <a name="malicious-users-with-authorization"></a>Utenti malintenzionati con autorizzazione

L'accesso da parte di un utente malintenzionato è essenzialmente una violazione dell'attendibilità. In questo scenario il protagonista è un programma creato per eseguire un'escalation dei privilegi utente in quanto, a differenza dello scenario precedente, questo utente volontariamente indica le credenziali per violare l'attendibilità.

![Utenti malintenzionati](./media/azure-information-protection-securing-data/aip-securing-data-fig4.png)

Azure Information Protection è stato progettato perché le applicazioni nel dispositivo client applichino i diritti associati al documento. Senza ombra di dubbio, l'anello debole nella sicurezza di un contenuto protetto va oggi cercato nel dispositivo client, dove il contenuto è visibile all'utente finale in testo non crittografato. Le applicazioni client come Microsoft Office rispettano i diritti in modo corretto e pertanto un utente malintenzionato non può usare queste applicazioni per l'escalation dei privilegi. Con l'SDK di Azure Information Protection, un utente malintenzionato motivato può comunque creare applicazioni che non rispettano i diritti. È questa l'essenza di un *programma dannoso*.

Questo scenario si concentra sulla protezione di dispositivi e applicazioni client in modo da escludere l'uso di applicazioni non autorizzate. Di seguito sono elencanti alcuni dei passi che l'amministratore IT può seguire:

- Usare [Windows AppLocker](https://technet.microsoft.com/library/dd759117(v=ws.11).aspx) per impedire che siano eseguiti programmi indesiderati
- Usare [Intune](https://docs.microsoft.com/intune/) e [System Center Configuration Manager](https://docs.microsoft.com/sccm/) per garantire l'integrità del dispositivo
- Controllare che l'antivirus nel dispositivo sia aggiornato
- Usare applicazioni che supportano [broker Microsoft per il controllo dell'identità ](https://technet.microsoft.com/library/ms166045(v=sql.105).aspx) per l'autenticazione e [SSO](https://azure.microsoft.com/resources/videos/overview-of-single-sign-on/)

Da questo scenario emerge quindi l'importanza di proteggere i computer e le applicazioni client, un concetto essenziale che riguarda l'attendibilità sostenuta da Azure Information Protection.

## <a name="summary"></a>Riepilogo

Per garantire massima protezione, non è possibile limitarsi all'uso di una sola tecnologia. Grazie a una serie di strumenti interdipendenti, un amministratore IT può ridurre la superficie di attacco nel contenuto protetto nel mondo reale.

- **Azure Information Protection**: impedisce a utenti non autorizzati l'accesso al contenuto
- **Microsoft Intune, System Center Configuration Manager e altri prodotti di gestione dei dispositivi**: garantiscono un ambiente gestito e controllato, privo di app dannose
- **Windows AppLocker**: garantisce un ambiente gestito e controllato privo di app dannose
- **Azure AD Identity Protection**: migliora l'attendibilità nell'identità utente
- **Accesso condizionale EMS**: migliora l'attendibilità nel dispositivo e nell'identità

## <a name="additional-resources"></a>Risorse aggiuntive

Gli scenari seguenti illustrano nel dettaglio come Azure Information Protection può aiutare a proteggere i dati:

- [Proteggere i dati usando la classificazione, l'assegnazione di etichette e la protezione](infoprotect-secure-classify-scenario.md)
- [Condividere i dati sensibili internamente ed esternamente](share-sensitive-data.md)
- [Tenere traccia dell'uso dei dati condivisi e rispondere in caso di uso improprio dei dati](infoprotect-track-usage-scenario.md)



<!--HONumber=Feb17_HO2-->


