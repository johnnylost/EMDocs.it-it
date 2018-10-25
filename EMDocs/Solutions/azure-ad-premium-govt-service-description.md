---
title: Descrizione del servizio Azure Active Directory Premium per enti pubblici
description: I piani Azure Active Directory Premium per enti pubblici sono sottoscrizioni mensili e vengono concessi in licenza per singoli utenti.
keywords: autenticazione
author: arob98
ms.author: mtillman
manager: mtillman
ms.date: 12/21/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: active-directory
ms.technology: ''
ms.assetid: 112289b0-0336-4cc0-b471-42fc2c015c64
ms.reviewer: ''
ms.suite: ''
ms.custom: ''
ms.openlocfilehash: 7eb4740e44a5b4104de7d39667e9653e29213315
ms.sourcegitcommit: 4401a878f88cc60b3cfd90a915747fe37e333014
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
ms.locfileid: "30848173"
---
# <a name="azure-active-directory-premium-government-service-description"></a>Descrizione del servizio Azure Active Directory Premium per enti pubblici

In risposta ai requisiti unici e in continua evoluzione del settore pubblico degli Stati Uniti d'America, Microsoft ha creato i piani Azure Active Directory Premium per enti pubblici (o "Azure Active Directory Premium Government"). Questo documento offre una panoramica delle funzionalità specifiche di Azure Active Directory Premium per enti pubblici. 

## <a name="how-to-use-this-service-description"></a>Come usare la descrizione del servizio

La descrizione del servizio Azure Active Directory Premium per enti pubblici va usata come panoramica dell'offerta di Microsoft e riguarda (1) i servizi e le funzionalità incluse nell'offerta, (2) le differenze tra le offerte commerciali esistenti e le offerte per enti pubblici e (3) gli impegni di conformità attualmente assunti da Microsoft. Questo documento definisce gli impegni unici e le differenze di questa offerta rispetto alle offerte Azure Active Directory Premium commerciali.

## <a name="about-azure-active-directory-premium-government-environments"></a>Informazioni sugli ambienti Azure Active Directory Premium per enti pubblici

I piani Azure Active Directory Premium per enti pubblici sono sottoscrizioni mensili e vengono concessi in licenza per singoli utenti. Le organizzazioni che usano Azure Active Directory Premium per enti pubblici traggono vantaggio dalle funzionalità specifiche seguenti:

* I contenuti dell'organizzazione sono separati a livello logico dai contenuti dei servizi Azure Active Directory Premium commerciali di Microsoft.
* Il contenuto dell'organizzazione viene archiviato negli Stati Uniti.
* L'accesso ai sistemi Microsoft che ospitano il contenuto è riservato a personale Microsoft sottoposto a screening.
* Azure Active Directory Premium per gli enti pubblici è conforme alle certificazioni e alle accreditazioni comuni richieste per i clienti del settore pubblico statunitense.

## <a name="customer-eligibility"></a>Idoneità dei clienti 

Azure Active Directory Premium per gli enti pubblici è disponibile per (1) enti federali, statali, locali, tribali e territoriali del governo degli Stati Uniti e (2) altri enti che gestiscono dati soggetti a normative e requisiti governativi e nei quali l'uso di Azure Active Directory Premium per enti pubblici consente di soddisfare tali requisiti, previa convalida dell'idoneità. La convalida dell'idoneità da parte di Microsoft includerà una conferma della gestione dei dati regolati o controllati da enti governativi. La convalida può richiedere una prova di registrazione presso il Dipartimento di Stato americano o di sponsorizzazione da parte di un ente governativo, con requisiti specifici per la gestione dei dati. Questa offerta è limitata ai clienti che dispongono di almeno 500 postazioni. Al momento del rinnovo del contratto di un cliente per Azure Active Directory Premium per enti pubblici, viene di nuovo richiesta la convalida dell'idoneità. Le entità con domande sull'idoneità per Azure Active Directory Premium per enti pubblici sono invitate a rivolgersi ai team interni responsabili degli account.

## <a name="location-of-customer-data"></a>Posizione dei dati del cliente

I servizi Azure Active Directory Premium per enti pubblici sono offerti da data center situati fisicamente negli Stati Uniti. Tutti i contenuti vengono archiviati in data center situati fisicamente solo negli Stati Uniti.

## <a name="azure-active-directory-premium-government-and-third-party-services"></a>Azure Active Directory Premium per enti pubblici e servizi di terzi

Vari servizi di Azure Active Directory Premium offrono la possibilità di interagire in modo integrato con applicazioni e servizi di terze parti. Tali applicazioni e servizi di terze parti possono includere l'archiviazione, la trasmissione e l'elaborazione dei contenuti dei clienti dell'organizzazione su sistemi di terze parti esterni all'infrastruttura di Azure Active Directory Premium e pertanto non sono inclusi negli accordi di conformità e protezione dei dati di Azure Active Directory Premium. Per valutare se l'uso di questi servizi è appropriato per l'organizzazione, è consigliabile verificare le informative sulla privacy e la conformità messe a disposizione dalle organizzazioni terze.

## <a name="azure-active-directory-premium-government-offers-and-office-365-interoperability"></a>Prodotti Azure Active Directory Premium per enti pubblici e interoperabilità con Office 365

Office 365 è attualmente disponibile sia negli ambienti GCC sia negli ambienti GCC High. Per altre informazioni su queste offerte, vedere la [descrizione del servizio](https://technet.microsoft.com/library/mt774581.aspx) Office 365 Government. Il prodotto commerciale Azure Active Directory Premium è totalmente compatibile con Office 365 GCC e attualmente è in corso la definizione della conformità alla certificazione FedRAMP-Moderate per questo prodotto. Azure Active Directory Premium GCC High è basato su [Microsoft Azure Government Cloud](https://docs.microsoft.com/azure/azure-government/documentation-government-welcome) e creato per l'interoperabilità con Office 365 GCC High e Office 365 DoD. È previsto l'ottenimento della certificazione FedRAMP-High per Azure Active Directory Premium GCC High.

|Prodotto Azure Active Directory Premium per enti pubblici|Prodotto Office 365 Government corrispondente|Impegno di conformità|
|-----------|-----------|-----------|
|Azure Active Directory Premium P1/P2 (commerciale)|Office 365 <br/> GCC|FedRAMP-Moderate|
|Azure Active Directory Premium P1/P2 GCC High|Office 365 <br/> GCC High|FedRAMP-High|

> [!NOTE]
> La conformità con FedRAMP è prevista entro l'anno di calendario 2018

## <a name="parity-with-azure-active-directory-premium-commercial-offerings"></a>Parità con le offerte commerciali Azure Active Directory Premium

Microsoft si propone di offrire ai clienti degli enti pubblici tutte le funzioni e le funzionalità commerciali con Azure Active Directory Premium GCC High, tuttavia nel prodotto non sono disponibili le funzionalità elencate di seguito. 

Di seguito sono elencate le differenze di disponibilità tra Azure Active Directory Premium GCC High e i prodotti commerciali in data dicembre 2017: 
* Azure Active Directory B2B.
* La raccolta di Azure Active Directory con app preconfigurate non è disponibile.
* Il controllo FedRAMP MFA è separato rispetto al controllo FedRAMP Azure AD e viene eseguito in ritardo. All'avvio di MFA la certificazione FedRAMP non è implementata e i clienti devono comunicare il consenso esplicito per questo servizio.
* Licenze basate sui gruppi. Questa funzionalità è attualmente in anteprima nel cloud commerciale. Quando sarà disponibile al pubblico generico nel cloud commerciale, la funzionalità verrà gradualmente resa disponibile anche in Azure Active Directory Premium GCC High.

