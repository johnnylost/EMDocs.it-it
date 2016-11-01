---
title: Gestire l&quot;accesso su larga scala
description: Gestire l&quot;accesso su larga scala
keywords: 
author: andredm7
manager: swadhwa
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 0292919a-af10-4a25-8916-c704aed643f6
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c20f69b821a2acfbf2fa399b960b60fc31dbf502
ms.openlocfilehash: 28b83995ab2689cffa048cbf2ccdd53a3d9b1421


---

# Gestire l'accesso su larga scala
Microsoft offre da sempre gli strumenti necessari alle organizzazioni. Oltre a un'identità che permette di accedere dovunque, Microsoft offre anche un insieme di strumenti per automatizzare, proteggere e gestire l'IT all'interno dell'organizzazione. Anche dopo l'avvento del cloud computing, esiste tuttora una domanda di gestione e controllo di operazioni IT come le chiamate del supporto tecnico per la reimpostazione delle password utente, la gestione dei gruppi di utenti e le richieste di applicazioni.

## Come può essere utile Enterprise Mobility + Security?
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS offre la soluzione a una delle esigenze principali degli ambienti che usano dispositivi mobili e cloud, ovvero rendere disponibile un insieme completo di strumenti all'interno di Azure Active Directory (Azure AD) che consentono di:
- Gestire il ciclo di vita dell'utente
- Ridurre overhead e costo dell'IT
- Monitorare il bridge di identità


### Soluzione consigliata
Azure AD Premium è la soluzione ideale per migliorare la propria organizzazione con la gestione delle identità e degli accessi.
#### Gestione del ciclo di vita dell'utente
Azure AD offre una gestione avanzata del ciclo di vita dell'utente automatizzata tramite regole di appartenenza ai gruppi dinamiche e funzionalità di gestione delle applicazioni.

- Per le organizzazioni con un sistema di gestione delle risorse umane locale, Microsoft identity Manager definisce le identità utente in Windows Server Active Directory.
- Per le organizzazioni con un sistema di gestione delle risorse umane SaaS (Software as a Service), Azure AD si integra attualmente con Workday e si integrerà con altre app in futuro.
- Azure AD Connect sincronizza utenti e gruppi tra Windows Server Active Directory e Azure AD.
- Azure AD offre licenze automatizzate basate sui gruppi per Office 365 e altri Microsoft Online Services.

![Immagine che illustra come Azure AD Connect sincronizza utenti e gruppi tra Windows Server Active Directory e Azure Active Directory](./media/ManageAccessAtScale/fig1.png)
#### Gestione delle applicazioni
A quanti utenti piace ricordare le password delle singole applicazioni che usano ogni giorno? Il servizio [Single Sign-On](https://azure.microsoft.com/en-us/documentation/articles/active-directory-appssoaccess-whatis/) risolve questo problema comune: è possibile accedere a più applicazioni SaaS usando un unico account utente e una password di cui viene eseguito automaticamente il provisioning per tutte le applicazioni all'interno dell'organizzazione. Questa funzionalità è disponibile per le applicazioni cloud Microsoft, ad esempio Office 365, e per le applicazioni di terze parti, ad esempio Salesforce, ServiceNow e Workday.

 La funzionalità è disponibile anche per le applicazioni locali attraverso il [proxy di applicazione di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) che offre un accesso remoto semplice, sicuro ed economico come soluzione distribuita come servizio a tutte le applicazioni locali. I dipendenti remoti possono accedere alle risorse locali senza limitarsi alla rete aziendale e senza che i responsabili IT implementino VPN, ambienti di reti perimetrali o proxy inversi.

 - Il servizio funziona nel cloud consentendo di risparmiare tempo e denaro. Le soluzioni locali richiedono l'impostazione e la gestione di reti perimetrali, server perimetrali o altre infrastrutture complesse.
 - È più semplice da impostare e proteggere rispetto alle soluzioni locali poiché non è necessario aprire connessioni in entrata attraverso il firewall.
 - Offre un'ottima protezione. Quando si pubblicano le app usando Azure AD Application Proxy, è possibile usare i controlli di autorizzazione avanzati e le analisi sicure in Azure. Ciò significa che sono disponibili funzionalità di sicurezza avanzate per tutte le app esistenti senza dover modificare alcuna app.
 - Viene offerta agli utenti un'esperienza di autenticazione coerente. Il servizio Single Sign-On consente agli utenti finali di accedere in modo semplice a tutte le app necessarie per la loro produttività con un'unica password.

#### Ridurre overhead e costo dell'IT
Azure AD Premium offre anche funzionalità self-service per la reimpostazione delle password e la gestione dei gruppi e delle app per migliorare la produttività IT e degli utenti finali nell'organizzazione. Gli utenti non dovranno chiamare il supporto tecnico e passare al telefono diversi minuti e fornire numerose informazioni per ottenere una password temporanea che viene inviata per posta elettronica o comunicata durante la chiamata in modo non sicuro.
- Funziona con account utente di federazione, di sincronizzazione delle password o solo cloud. Vengono anche applicati tutti i criteri delle password locali.
- Il traffico viene crittografato con una chiave specifica del tenant e su HTTPS.
- Gli utenti possono aggiornare le loro password AD o sbloccare i loro account AD in tempo reale.
- Notifiche in tempo reale vengono inviate agli utenti e agli amministratori.

![Immagine che illustra come Azure Active Directory funziona in modo sicuro in locale e nel cloud per offrire funzionalità self-service di reimpostazione delle password agli utenti finali.  ](./media/ManageAccessAtScale/fig2.png)

#### Monitorare il bridge di identità
Azure AD Connect Health consente alle organizzazioni di monitorare e ottenere informazioni sull'infrastruttura delle identità locale e sui servizi di sincronizzazione e di mantenere una connessione affidabile a Office 365 e Microsoft Online Services offrendo funzionalità di monitoraggio per i componenti delle identità principali, ad esempio i server AD FS, i server Azure AD Connect e i controller di dominio Active Directory.

- Controllo e conformità con un solo clic tramite il portale di Azure.
- Analisi scientifiche e indagini: consentono agli amministratori IT di rispondere alle domande "chi, dove e quando".
- Report attività: offrono controlli, accessi, SSPR, attività dei gruppi, attività delle app, provisioning delle app, ecc.
- Report sulla sicurezza: offrono mitigazione e risoluzione per le anomalie di sicurezza attraverso la protezione dell'identità.

![Immagine che illustra come Azure AD Connect Health consente alle organizzazioni di monitorare i componenti delle identità principali, ad esempio i server AD FS, i server Azure AD Connect e i controller di dominio Active Directory. ](./media/ManageAccessAtScale/fig3.png)

## Come implementare una gestione avanzata del ciclo di vita dell'utente
Di seguito sono descritti alcuni esempi e i passaggi da eseguire per implementare questa soluzione:
1. In uno scenario reale, l'organizzazione assume un professionista e aggiunge l'utente al sistema di gestione delle risorse umane come membro del team Marketing.
2.  Presupponendo che Active Directory locale sia già stato integrato con Azure AD tramite la sincronizzazione delle directory, Azure AD Connect locale sincronizza l'account utente con Azure AD.
3.  Quando l'account utente è visibile in Azure AD, è possibile creare una regola di appartenenza ai gruppi dinamica che assegna automaticamente gli utenti Marketing all'account.
4.  Dopo aver inserito automaticamente gli utenti nel gruppo Marketing, è possibile usare licenze selettive basate sui gruppi che offrono la possibilità di aggiungere gli utenti in un gruppo di licenze specifico, ad esempio Azure AD Premium o Office 365 Enterprise E5.
  - Nell'esempio viene concesso agli utenti l'accesso a tutte le app di Office 365 necessarie per svolgere il loro lavoro e gli accessi ad Azure AD Premium per eseguire le altre attività automatizzate.

Se per qualche motivo un dipendente lascia l'azienda, è possibile rimuoverlo dal sistema di gestione delle risorse umane per rimuovere automaticamente l'accesso da tutte le applicazioni e le risorse di cui è stato precedentemente eseguito il provisioning. Se il dipendente deve semplicemente passare a un altro reparto, le regole di appartenenza ai gruppi dinamiche rimuoveranno automaticamente l'accesso dalle applicazioni di Marketing e aggiungeranno l'accesso alle applicazioni dell'altro reparto non appena l'utente viene rimosso dal team Marketing e aggiunto al gruppo dinamico del nuovo reparto.

### Come gestire le applicazioni cloud e locali
Di seguito sono descritti i passaggi che è possibile eseguire per aggiungere, distribuire e gestire le applicazioni SaaS Microsoft e di terze parti con Azure AD.
- Altre informazioni sull'[integrazione di Azure AD con le applicazioni](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications-getting-started/).
- Altre informazioni sull'[abilitazione del servizio Single Sign-On nelle app SaaS](https://azure.microsoft.com/documentation/articles/active-directory-sso-integrate-saas-apps/).
- Altre informazioni sulla [gestione dell'accesso alle app](https://azure.microsoft.com/documentation/articles/active-directory-managing-access-to-apps/).

## Come implementare il portale self-service di reimpostazione delle password
Per impostazione predefinita, Azure AD include una funzionalità gratuita che consente a ogni amministratore di eseguire la reimpostazione della password self-service.

Quando si usa Azure AD Premium, è possibile superare gli amministratori IT offrendo le funzionalità del portale self-service di reimpostazione delle password agli utenti. È possibile abilitare rapidamente i criteri di reimpostazione delle password utente che estenderanno le stesse funzionalità di amministrazione avanzate a ogni utente all'interno della directory.

Altre informazioni sui [prerequisiti e l'abilitazione e la configurazione del portale self-service di reimpostazione delle password](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/) sono disponibili nel tenant di Azure AD.

## Come implementare Azure AD Connect Health
Fare riferimento alla [documentazione di Azure AD Connect Health](https://azure.microsoft.com/en-in/documentation/articles/active-directory-aadconnect-health/) per altre informazioni sullo strumento, le funzionalità e i passaggi da eseguire per iniziare a usarlo nell'organizzazione.

Azure AD Connect Health è disponibile nel [portale di Azure](https://ms.portal.azure.com) e richiede l'installazione di un agente per l'integrità nei controller di dominio locali da monitorare. Altre informazioni su [come installare l'agente per l'integrità](https://azure.microsoft.com/en-in/documentation/articles/active-directory-aadconnect-health-agent-install/).

Il dashboard dei controller di dominio offre un unico punto di osservazione dello stato di integrità e operativo dell'ambiente in cui l'amministratore può individuare facilmente i controller di dominio che sono proprietari dei ruoli FSMO, hanno avvisi attivi e sono cataloghi globali e visualizzare altre colonne come "PDC raggiungibile", "GC raggiungibile", "Stato Sysvol" e altre ancora:

![Schermata che illustra il dashboard dei controller di dominio con informazioni sul controller di dominio selezionato. ](./media/ManageAccessAtScale/fig4.png)

I controller di dominio possono essere anche raggruppati per dominio corrispondente o per sito dall'amministratore:

![Schermata che illustra i controller di dominio raggruppati per sito. ](./media/ManageAccessAtScale/fig5.png)

Il dashboard Stato replica visualizza la topologia di replica all'interno dell'ambiente e informazioni sull'ultimo tentativo di replica per ogni contesto di denominazione:

![Schermata che illustra il dashboard Stato replica con informazioni sull'ultimo tentativo di replica. ](./media/ManageAccessAtScale/fig6.png)

I dettagli di un avviso includono altre informazioni sul problema che causa l'avviso, la correzione necessaria e un collegamento a risorse di risoluzione dei problemi aggiuntive:

![Schermata che illustra i dettagli di un avviso specificato. ](./media/ManageAccessAtScale/fig7.png)

Il monitoraggio delle prestazioni di AD Connect Health offre un metodo semplice per confrontare le prestazioni dei controller di dominio monitorati e le diverse metriche di interesse:

![Schermata che illustra il monitoraggio delle prestazioni dei controller di dominio selezionati. ](./media/ManageAccessAtScale/fig8.png)



<!--HONumber=Oct16_HO3-->


