---
# required metadata

title: Requisiti di utenti e dispositivi
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 69020f79-4ce2-4984-b127-4520503fb729

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Requisiti di utenti e dispositivi

Prima di consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi, rispondere alle domande nelle sezioni seguenti in collaborazione con gli utilizzatori di queste risorse nell'ambiente usato e con il reparto IT. La figura 2 mostra le interazioni tra utenti e dispositivi, con l'obiettivo finale di accedere ai dati e di utilizzarli. Si noti che il diagramma non valuta la posizione geografica. Sebbene la posizione geografica sia un aspetto importante, che verrà trattato più avanti in questo documento, lo scopo della figura 2 è illustrare i componenti principali di utenti e dispositivi. Fare le dovute considerazioni di progettazione per consentire questa comunicazione.

![Utenti, dispositivi e dati](./media/BYOD_Figure2.png)

Il risultato di questo processo è una definizione chiara delle funzionalità da fornire. La sezione seguente contiene le domande su utenti e dispositivi a cui è necessario rispondere per formulare i requisiti per la progettazione della soluzione.

## Domande da chiedere

I requisiti di utenti e dispositivi sono suddivisi in tre aree:

- Profilo
- Dispositivo
- Rete

### Profilo

- Quali sono i tipi di profili utente disponibili nell'organizzazione (ad esempio utenti remoti, utenti che viaggiano occasionalmente e utenti che lavorano a tempo pieno tra casa e ufficio)?
- Gli utenti hanno tutti le stesse esigenze per svolgere il proprio incarico?
- Si ha una matrice che definisce le esigenze degli utenti in base agli incarichi/ruoli?


### Dispositivi

- Quali tipi di dispositivi porteranno gli utenti, ad esempio smartphone, tablet e portatili?
- Si intende fornire la funzionalità di cancellazione remota per tutti i tipi di dispositivi?
- Si intende gestire i dispositivi degli utenti?
- Si hanno degli scenari in cui non è necessario gestire il dispositivo, ma è necessario comunque tenere traccia di chi possiede il dispositivo?
- Si intende eseguire l'autenticazione dei dispositivi in base agli utenti che portano i dispositivi nell'azienda?
- L'azienda rispetta dei requisiti di conformità che devono essere applicati a tutti i dispositivi che potenzialmente avranno accesso ai dati dell'azienda?
- L'azienda prevede dei criteri per gestire i dispositivi rubati?

### Rete

- L'azienda ha delle risorse nel cloud che saranno accessibili tramite Internet dai dispositivi degli utenti?
- L'azienda ha delle restrizioni dei criteri per gli utenti che accedono ai dati aziendali da diverse posizioni geografiche?
- Si intende fornire la crittografia di rete per consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi?
    - In tal caso, l'elenco esistente dei dispositivi supportati supporta il protocollo di crittografia che verrà usato?
- È prevista la segmentazione della rete?
    - In tal caso, tutti i dispositivi degli utenti verranno connessi a una rete separata per isolarli dalla rete di produzione?


<!--HONumber=Apr16_HO2-->


