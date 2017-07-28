---
title: Gestire l'accesso su larga scala
description: "Questo articolo descrive come usare Enterprise Mobility + Security per permettere all'organizzazione la gestione dell'accesso alle identità tramite gli strumenti inclusi in Azure Active Directory."
keywords: 
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 12/07/2016
ms.topic: solution
ms.prod: 
ms.service: active-directory
ms.technology: 
ms.assetid: 0292919a-af10-4a25-8916-c704aed643f6
ROBOTS: 
ms.reviewer: atkladak, jsnow
ms.suite: ems
ms.openlocfilehash: fa2795fb578c0d278d55cbff9f44c19ca2e13309
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="manage-access-at-scale"></a>Gestire l'accesso su larga scala
Microsoft offre da sempre gli strumenti necessari alle organizzazioni. Oltre a un'identità che permette di accedere dovunque, Microsoft offre anche un insieme di strumenti per automatizzare, proteggere e gestire le attività IT all'interno dell'organizzazione. Anche dopo l'avvento del cloud computing, esiste tuttora una domanda di gestione e controllo di attività IT come le chiamate del supporto tecnico per la reimpostazione delle password utente, la gestione dei gruppi di utenti e le richieste di applicazioni.

## <a name="how-enterprise-mobility--security-can-help-you"></a>Come può essere utile Enterprise Mobility + Security
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS offre la soluzione a una delle esigenze principali degli ambienti mobile-first e cloud-first, ovvero rendere disponibile un insieme completo di strumenti all'interno di Azure Active Directory (Azure AD) che consentono di:
- Gestire il ciclo di vita dell'utente
- Ridurre overhead e costo dell'IT
- Monitorare il bridge di identità

## <a name="recommended-solution"></a>Soluzione consigliata
Azure AD Premium è la soluzione ideale per migliorare la propria organizzazione con la gestione delle identità e degli accessi.

### <a name="advanced-user-lifecycle-management"></a>Gestire il ciclo di vita dell'utente
Azure AD offre una gestione avanzata del ciclo di vita dell'utente automatizzata tramite regole di appartenenza ai gruppi dinamiche e funzionalità di gestione delle applicazioni. Ecco ulteriori dettagli:

- Per le organizzazioni con un sistema di gestione delle risorse umane locale, Microsoft Identity Manager definisce le identità utente in Windows Server Active Directory.
- Per le organizzazioni con un sistema di gestione delle risorse umane SaaS (Software as a Service), Azure AD si integra attualmente con Workday.
- Azure AD Connect sincronizza utenti e gruppi tra Windows Server Active Directory e Azure AD.
- Azure AD offre licenze automatizzate basate sui gruppi per Office 365 e altri Microsoft Online Services.

![Figura che illustra come Azure AD Connect sincronizza utenti e gruppi tra Windows Server Active Directory e Azure Active Directory](./media/manage-access-at-scale/manage-access-at-scale-fig1.png)

### <a name="application-management"></a>Gestione delle applicazioni
A quanti utenti piace ricordare le password delle singole applicazioni che usano ogni giorno? Il servizio [Single Sign-On](https://azure.microsoft.com/en-us/documentation/articles/active-directory-appssoaccess-whatis/) risolve questo problema comune. È possibile accedere a diverse applicazioni SaaS con un singolo account utente e una sola password. Il provisioning dell'accesso Single Sign-On per tutte le applicazioni all'interno dell'organizzazione può essere eseguito automaticamente. Questa funzionalità è disponibile per le applicazioni cloud Microsoft, come Office 365, e per le applicazioni di terze parti, come Salesforce, ServiceNow e Workday.

Ecco ulteriori dettagli su Single Sign-On:

 - Il servizio funziona nel cloud consentendo di risparmiare tempo e denaro. Le soluzioni locali richiedono la configurazione e la gestione di reti perimetrali, server perimetrali o altre infrastrutture complesse.
 - È più semplice da impostare e proteggere rispetto alle soluzioni locali poiché non è necessario aprire connessioni in entrata attraverso il firewall.
 - Offre un'ottima protezione. Quando si pubblicano le app usando il proxy per l'applicazione Azure AD, è possibile usare i controlli di autorizzazione e l'analisi della sicurezza in Azure. Ciò significa che sono disponibili funzionalità di sicurezza avanzate per tutte le app esistenti senza dover modificare alcuna app.
 - Viene offerta agli utenti un'esperienza di autenticazione coerente. Il servizio Single Sign-On consente agli utenti di accedere a tutte le app necessarie per la loro produttività con un'unica password.

### <a name="low-it-overhead-and-cost"></a>Ridurre overhead e costo dell'IT
Azure AD Premium offre funzionalità self-service per la reimpostazione delle password e la gestione dei gruppi e delle app per migliorare la produttività IT e degli utenti nell'organizzazione. Gli utenti non dovranno chiamare il supporto tecnico e fornire numerose informazioni per ottenere una password temporanea che viene inviata per posta elettronica o comunicata durante la chiamata in modo non sicuro.

Ecco ulteriori dettagli sulla reimpostazione della password:

- Funziona con account utente di federazione, di sincronizzazione delle password o solo cloud. Vengono anche applicati tutti i criteri delle password locali.
- Tutto il traffico viene crittografato con una chiave specifica del tenant e tramite HTTPS.
- Gli utenti possono aggiornare le loro password AD o sbloccare i loro account AD in tempo reale.
- Notifiche in tempo reale vengono inviate agli utenti e agli amministratori.

![Figura che illustra come funziona Azure Active Directory in locale e nel cloud per offrire funzionalità self-service di reimpostazione delle password agli utenti finali](./media/manage-access-at-scale/manage-access-at-scale-fig2.png)

### <a name="monitor-your-identity-bridge"></a>Monitorare il bridge di identità
Azure AD Connect Health consente alle organizzazioni di ottenere informazioni approfondite sull'infrastruttura locale delle identità e i servizi di sincronizzazione, nonché di monitorarli. Offre anche la possibilità alle organizzazione di mantenere una connessione affidabile a Office 365 e Microsoft Online Services, fornendo funzionalità di monitoraggio per i componenti chiave correlati alle identità. Questi componenti includono server Active Directory Federation Services (AD FS), server Azure AD Connect e controller di dominio Active Directory.

Ecco ulteriori dettagli su Azure AD Health:

- Controllo e conformità con un solo clic tramite il portale di Azure
- Analisi scientifiche e indagini: consentono agli amministratori IT di rispondere alle domande "chi, dove e quando"
- Report attività: offrono informazioni su controlli, accessi, reimpostazione delle password self-service, attività dei gruppi, attività delle app, provisioning delle app e altro
- Report sulla sicurezza: supportano mitigazione e risoluzione per le anomalie relative alla sicurezza attraverso la protezione dell'identità

![Figura che illustra come Azure AD Connect Health consente alle organizzazioni di monitorare i componenti chiave per le identità, come i server AD FS, i server Azure AD Connect e i controller di dominio Active Directory](./media/manage-access-at-scale/manage-access-at-scale-fig3.png)

## <a name="how-to-implement-an-advanced-user-lifecycle-management"></a>Come implementare una gestione avanzata del ciclo di vita dell'utente
Di seguito sono descritti alcuni esempi e i passaggi da eseguire per implementare questa soluzione:

1. In uno scenario reale, l'organizzazione assume un professionista e aggiunge l'utente al sistema di gestione delle risorse umane come membro del team Marketing.
2.  Presupponendo che l'istanza di Active Directory locale sia già stata integrata con Azure AD tramite la sincronizzazione delle directory, Azure AD Connect in locale sincronizza l'account utente con Azure AD.
3.  Quando l'account utente compare in Azure AD, è possibile creare regole di appartenenza ai gruppi dinamiche che assegnano automaticamente gli utenti del team Marketing al gruppo appropriato.
4.  Dopo il popolamento automatico degli utenti nel gruppo Marketing, è possibile usare l'assegnazione delle licenze selettiva basata sui gruppi. Questo tipo di gestione delle licenze offre la possibilità di aggiungere utenti a un gruppo di licenze specifico, ad esempio Azure AD Premium o Office 365 Enterprise E5.
    Nell'esempio viene concesso agli utenti l'accesso a tutte le app di Office 365 necessarie per svolgere il loro lavoro e gli accessi ad Azure AD Premium per eseguire le altre attività automatizzate.

Se un dipendente lascia l'azienda, è possibile rimuoverlo dal sistema di gestione delle risorse umane, rimuovendo così automaticamente l'accesso da tutte le applicazioni e le risorse di cui era stato eseguito il provisioning in precedenza per l'utente in questione. Se il dipendente deve semplicemente passare a un altro reparto, le regole di appartenenza ai gruppi dinamiche rimuoveranno automaticamente l'accesso dalle applicazioni del gruppo Marketing e aggiungeranno l'accesso alle applicazioni dell'altro reparto non appena l'utente viene rimosso dal team Marketing e aggiunto al gruppo dinamico del nuovo reparto.

## <a name="how-to-manage-cloud-and-on-premises-applications"></a>Come gestire le applicazioni cloud e locali
Di seguito sono descritti i passaggi che è possibile eseguire per aggiungere, distribuire e gestire le applicazioni SaaS Microsoft e di terze parti con Azure AD:
- Altre informazioni sull'[integrazione di Azure AD con le applicazioni](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications-getting-started/).
- Altre informazioni sull'[abilitazione del servizio Single Sign-On per le app SaaS](https://azure.microsoft.com/documentation/articles/active-directory-sso-integrate-saas-apps/).
- Altre informazioni sulla [gestione dell'accesso alle app](https://azure.microsoft.com/documentation/articles/active-directory-managing-access-to-apps/).

## <a name="how-to-implement-password-reset-self-service-portal"></a>Come implementare il portale self-service di reimpostazione delle password
Per impostazione predefinita, Azure AD include una funzionalità gratuita che consente a ogni amministratore di eseguire la reimpostazione della password self-service.

Quando si usa Azure AD Premium, è possibile evitare l'intervento degli amministratori IT offrendo agli utenti le funzionalità del portale self-service di reimpostazione delle password. È possibile abilitare rapidamente i criteri di reimpostazione delle password utente che estenderanno le stesse funzionalità per gli amministratori a ogni utente all'interno della directory.

Altre informazioni sui [prerequisiti, l'abilitazione e la configurazione del portale self-service di reimpostazione delle password](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/) sono disponibili nel tenant di Azure AD.

## <a name="how-to-use-azure-ad-connect-health"></a>Come usare Azure AD Connect Health
Fare riferimento alla [documentazione di Azure AD Connect Health](https://azure.microsoft.com/en-in/documentation/articles/active-directory-aadconnect-health/) per altre informazioni sullo strumento, le funzionalità e i passaggi da eseguire per iniziare a usarlo nell'organizzazione.

Azure AD Connect Health è disponibile nel [portale di Azure](https://ms.portal.azure.com) e richiede l'installazione di un agente per l'integrità nei controller di dominio locali da monitorare. Altre informazioni su [come installare l'agente per l'integrità](https://azure.microsoft.com/en-in/documentation/articles/active-directory-aadconnect-health-agent-install/).

Il dashboard dei **controller di dominio** offre una singola visualizzazione per lo stato di integrità e operativo dell'ambiente. Con questo strumento, l'amministratore può individuare facilmente i controller di dominio con il ruolo FSMO (Flexible Single Master Operations), quelli con avvisi attivi e quelli che operano come cataloghi globali. Altre colonne di informazioni disponibili sono **PDC raggiungibile**, **GC raggiungibile** e **Stato SYSVOL**.

![Screenshot che illustra il dashboard dei controller di dominio con informazioni sul controller di dominio selezionato](./media/manage-access-at-scale/manage-access-at-scale-fig4.png)

I controller di dominio possono essere anche raggruppati in base al dominio corrispondente oppure l'amministratore può raggrupparli in base al sito.

![Screenshot che illustra i controller di dominio raggruppati in base al sito](./media/manage-access-at-scale/manage-access-at-scale-fig5.png)

Il dashboard **Stato replica** visualizza la topologia di replica all'interno dell'ambiente e informazioni sull'ultimo tentativo di replica per ogni contesto di denominazione.

![Screenshot che illustra il dashboard Stato replica con informazioni sull'ultimo tentativo di replica](./media/manage-access-at-scale/manage-access-at-scale-fig6.png)

I dettagli di un avviso includono altre informazioni sul problema che causa l'avviso, la correzione necessaria e un collegamento ad altre risorse per la risoluzione dei problemi.

![Screenshot che illustra i dettagli di un avviso specificato](./media/manage-access-at-scale/manage-access-at-scale-fig7.png)

Il monitoraggio delle prestazioni di AD Connect Health offre un metodo semplice per confrontare le prestazioni dei controller di dominio monitorati e le diverse metriche di interesse.

![Screenshot che illustra il monitoraggio delle prestazioni dei controller di dominio selezionati](./media/manage-access-at-scale/manage-access-at-scale-fig8.png)
