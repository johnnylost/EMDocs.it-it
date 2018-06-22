---
title: Descrizione del servizio Enterprise Mobility + Security per il governo degli Stati Uniti
description: I piani EMS GCC High sono sottoscrizioni mensili e vengono concessi in licenza per singoli utenti.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: ems
ms.technology: ''
ms.assetid: de61a788-f45d-47bb-a047-e92b64b1ee03
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: da6b79835b9891b15fcb97d90f6d6263f231b356
ms.sourcegitcommit: 6399d25da998e54605082faff5f8b2304a851e4e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
ms.locfileid: "29721445"
---
# <a name="enterprise-mobility--security-for-us-government-service-description"></a>Descrizione del servizio Enterprise Mobility + Security per il governo degli Stati Uniti 
In risposta ai requisiti unici e in continua evoluzione del settore pubblico degli Stati Uniti d'America, Microsoft ha creato i piani EMS (Enterprise Mobility + Security) per i clienti del governo degli Stati Uniti. Questo documento offre una panoramica delle funzionalità specifiche dei piani EMS.  

## <a name="how-to-use-this-service-description"></a>Come usare la descrizione del servizio 
La descrizione del servizio EMS per il governo degli Stati Uniti va usata come panoramica dell'offerta di Microsoft e riguarda (1) i servizi e le funzionalità incluse nell'offerta, (2) le differenze tra le offerte commerciali esistenti e le offerte per enti pubblici e (3) gli impegni di conformità attualmente assunti da Microsoft. Questo documento definisce gli impegni unici e le differenze di questa offerta rispetto alle offerte EMS commerciali.  

## <a name="ems-offers-for-us-government-and-office-365-interoperability"></a>Interoperabilità tra le offerte EMS per il governo degli Stati Uniti e Office 365 
Office 365 è attualmente disponibile sia ambienti GCC sia negli ambienti GCC High. Per altre informazioni su queste offerte, vedere la descrizione del servizio Office 365 Government. Il prodotto commerciale EMS è totalmente compatibile con Office 365 GCC ed è in corso la definizione della conformità alla certificazione FedRAMP-Moderate per questo prodotto. EMS GCC High è basato su Microsoft Azure Government Cloud e creato per l'interoperabilità con Office 365 GCC High e Office 365 DoD. È previsto l'ottenimento della certificazione FedRAMP-High per EMS GCC High.  

|Offerta EMS|Prodotto Office 365 Government corrispondente|Impegno di conformità|
|-----------|-----------|-----------|
|EMS (commerciale)</br>Disponibile sia in E3 sia in E5|Office 365 GCC|FedRAMP-Moderate|
|EMS GCC High</br>Disponibile sia in E3 sia in E5|Office 365 GCC High|FedRAMP-High| 

> [!Note]    
> La conformità con FedRAMP è prevista entro l'anno di calendario 2018. 

## <a name="about-ems-for-us-government"></a>Informazioni su EMS per il governo degli Stati Uniti 
I piani EMS GCC High sono sottoscrizioni mensili e vengono concessi in licenza per singoli utenti. Le organizzazioni che usano EMS GCC High dispongono delle seguenti funzionalità uniche:  

- I contenuti dell'organizzazione sono separati a livello logico dai contenuti dei servizi EMS commerciali di Microsoft. 

- Il contenuto dell'organizzazione viene archiviato negli Stati Uniti. 

- L'accesso ai sistemi Microsoft che ospitano il contenuto è riservato a personale Microsoft sottoposto a screening. 

- EMS GCC High è conforme alle certificazioni e alle accreditazioni comuni richieste per i clienti del settore pubblico statunitense. 

## <a name="customer-eligibility"></a>Idoneità dei clienti 
Le offerte EMS per gli enti pubblici sono disponibili per (1) enti federali, statali, locali, tribali e territoriali del governo degli Stati Uniti e (2) altri enti che gestiscono dati soggetti a normative e requisiti governativi e nei quali l'uso di EMS consente di soddisfare tali requisiti, previa convalida dell'idoneità. La convalida dell'idoneità da parte di Microsoft includerà una conferma della gestione dei dati regolati o controllati da enti governativi. La convalida può richiedere una prova di registrazione presso il Dipartimento di Stato americano o di sponsorizzazione da parte di un ente governativo, con requisiti specifici per la gestione dei dati. Questa offerta è limitata ai clienti che dispongono di almeno 500 postazioni. Al momento del rinnovo del contratto di un cliente per EMS viene richiesta nuovamente la convalida dell'idoneità. Le entità con domande sull'idoneità per EMS sono invitate a rivolgersi ai team interni responsabili degli account.  

## <a name="location-of-customer-data"></a>Posizione dei dati del cliente 
I servizi EMS GCC High sono offerti da data center situati fisicamente negli Stati Uniti. Tutti il contenuti vengono archiviati in data center situati fisicamente solo negli Stati Uniti.  

## <a name="ems-gcc-high-and-third-party-services"></a>EMS GCC High e servizi di terze parti 
Vari servizi EMS consentono di interagire in modo integrato con applicazioni e servizi di terze parti. Tali applicazioni e servizi di terze parti possono includere l'archiviazione, la trasmissione e l'elaborazione dei contenuti dei clienti dell'organizzazione su sistemi di terze parti esterni all'infrastruttura di EMS e pertanto non inclusi negli accordi di conformità e protezione dei dati di EMS. Per valutare se l'uso di questi servizi è appropriato per l'organizzazione, è consigliabile verificare le informative sulla privacy e la conformità messe a disposizione dalle organizzazioni terze.  

## <a name="parity-with-ems-commercial-offerings"></a>Parità con le offerte commerciali di EMS 
Microsoft si propone di offrire ai clienti degli enti pubblici tutte le funzioni e le funzionalità disponibili nelle versioni commerciali. Tuttavia in EMS GCC High non sono attualmente disponibili le funzionalità elencate di seguito.  
    
Di seguito sono elencate le differenze di disponibilità tra EMS GCC High e i prodotti commerciali in data febbraio 2018:  

- Microsoft Cloud App Security non è attualmente incluso nei piani EMS E5 per GCC High.   

- Azure Active Directory B2B. 

- La raccolta di Azure Active Directory con app preconfigurate non è disponibile. 

- Il controllo FedRAMP MFA è separato rispetto al controllo FedRAMP Azure AD e viene eseguito in ritardo. All'avvio di MFA la certificazione FedRAMP non è implementata e i clienti devono comunicare il consenso esplicito per questo servizio. 

- Licenze basate sui gruppi. Questa funzionalità è attualmente in anteprima nel cloud commerciale. Quando sarà disponibile al pubblico generico nel cloud commerciale, la funzionalità verrà gradualmente resa disponibile anche in Azure Active Directory Premium GCC High. 

- Le app per dispositivi mobili Office 365 non sono ancora incluse nell'offerta Office 365 GCC High e pertanto non sono abilitate le funzionalità di Gestione per applicazioni mobili di Intune. 

- Aggiornamenti di Azure Information Protection (AIP)  