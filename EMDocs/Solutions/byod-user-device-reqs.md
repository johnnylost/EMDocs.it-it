---
title: Requisiti di utenti e dispositivi
description: Questo articolo include una serie di requisiti comuni che devono essere adottati da utenti e relativi dispositivi in uno scenario Bring Your Own Device (BYOD).
keywords: 
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6319952-e9cd-4308-b9b9-b2e6005e6506
ms.reviewer: 
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 5adb7f68efacdfa20d78c3cf5853fa374793140a
ms.openlocfilehash: e8052d7c45b1b0a579dab9c17112907ade027f8f
ms.contentlocale: it-it
ms.lasthandoff: 11/28/2016


---

# <a name="user-and-device-requirements"></a>Requisiti di utenti e dispositivi

Prima di consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi, rispondere alle domande nelle sezioni seguenti in collaborazione con gli utilizzatori di queste risorse nell'ambiente usato e con il reparto IT. La figura sottostante illustra le interazioni tra utenti e dispositivi, con l'obiettivo finale di accedere ai dati e di usarli. Si noti che il diagramma non valuta la posizione geografica. Sebbene la posizione geografica sia un aspetto importante, che verrà trattato più avanti in questa guida, lo scopo di questa figura è illustrare i componenti principali di utenti e dispositivi. Fare le dovute considerazioni di progettazione per consentire questa comunicazione.

![Utenti, dispositivi e dati](./media/BYOD_Figure2.png)

Il risultato di questo processo è una definizione chiara delle funzionalità da fornire. La sezione seguente contiene le domande su utenti e dispositivi a cui è necessario rispondere per formulare i requisiti per la progettazione della soluzione.

## <a name="questions-to-ask"></a>Domande da chiedere

I requisiti di utenti e dispositivi sono suddivisi in tre aree:

- Profilo
- Dispositivo
- Rete

### <a name="profile"></a>Profilo

- Quali sono i tipi di profili utente disponibili nell'organizzazione (ad esempio utenti remoti, utenti che viaggiano occasionalmente e utenti che lavorano a tempo pieno tra casa e ufficio)?
- Gli utenti hanno tutti le stesse esigenze per svolgere il proprio incarico?
- Si ha una matrice che definisce le esigenze degli utenti in base agli incarichi/ruoli?


### <a name="devices"></a>Dispositivi

- Quali tipi di dispositivi porteranno gli utenti, ad esempio smartphone, tablet e portatili?
- Si intende fornire la funzionalità di cancellazione remota per tutti i tipi di dispositivi?
- Si intende gestire i dispositivi degli utenti?
- Si hanno degli scenari in cui non è necessario gestire il dispositivo, ma è necessario comunque tenere traccia di chi possiede il dispositivo?
- Si intende eseguire l'autenticazione dei dispositivi in base agli utenti che portano i dispositivi nell'azienda?
- L'azienda rispetta dei requisiti di conformità che devono essere applicati a tutti i dispositivi che potenzialmente avranno accesso ai dati dell'azienda?
- L'azienda prevede dei criteri per gestire i dispositivi rubati?

### <a name="network"></a>Rete

- L'azienda ha delle risorse nel cloud che saranno accessibili tramite Internet dai dispositivi degli utenti?
- L'azienda ha delle restrizioni dei criteri per gli utenti che accedono ai dati aziendali da diverse posizioni geografiche?
- Si intende fornire la crittografia di rete per consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi?
    - In tal caso, l'elenco esistente dei dispositivi supportati supporta il protocollo di crittografia che verrà usato?
- È prevista la segmentazione della rete?
    - In tal caso, tutti i dispositivi degli utenti verranno connessi a una rete separata per isolarli dalla rete di produzione?
- Chi lavora sia da casa che in ufficio come deve connettersi alla rete? Con una connessione cablata, wireless o di entrambi i tipi?
    - Nel caso della connessione wireless, come si intende gestire l'autenticazione, l'autorizzazione e l'accounting (AAA) dei dispositivi in modo che i dispositivi non registrati o non autorizzati non siano in grado di usare risorse di rete senza autorizzazioni appropriate?

### <a name="technical-support"></a>Supporto tecnico
- Il team responsabile della rete e della sicurezza è pronto a inserire tra le proprie mansioni lo svolgimento a intervalli regolari di controlli di conformità sui dispositivi?
- Sono in vigore criteri e procedure di gestione delle modifiche a supporto dell'implementazione di BYOD?

