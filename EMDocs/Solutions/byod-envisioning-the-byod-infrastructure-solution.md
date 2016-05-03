---
# required metadata

title: Progettazione della soluzione di infrastruttura BYOD
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 9596531a-2eef-4c91-af11-091088c52929

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

#Progettazione della soluzione di infrastruttura BYOD

Dopo aver definito chiaramente il problema BYOD che si sta provando a risolvere, è possibile definire una soluzione al problema e i requisiti dettagliati per la soluzione.

## Definizione della soluzione

Per risolvere i problemi identificati in precedenza e aiutare le organizzazioni a incoraggiare gli utenti a portare i propri dispositivi nel posto di lavoro per accedere ai dati aziendali, l'azienda deve passare da un approccio IT incentrato sui dispositivi a un approccio IT incentrato sugli utenti. Per definire una soluzione di infrastruttura BYOD personalizzata, usare le considerazioni di progettazione illustrate nel presente documento per: 

- Fornire agli utenti la flessibilità necessaria per usare i propri dispositivi per accedere alle app e ai dati aziendali.
- Gestire i dispositivi che accedono alle risorse aziendali in locale e dal cloud.
- Consentire a un reparto IT di proteggere i dati aziendali archiviati nei dispositivi dall'accesso locale non autorizzato e dalla cancellazione in remoto via Internet mediante crittografia e Rights Management quando un dispositivo viene perso o ritirato oppure durante la cessazione del rapporto di lavoro.
- Fornire agli utenti un'identità comune quando accedono alle risorse in locale e dal cloud.
- Consentire al reparto IT di gestire più identità e mantenere le informazioni sincronizzate tra ambienti diversi.
- Abilitare i servizi di autenticazione aziendali come l'autenticazione a più fattori e Single Sign-On.
- Fornire supporto per attività di conformità e sicurezza delle informazioni come l'attestazione di conformità.

## Requisiti della soluzione

Prima di consentire agli utenti di portare i propri dispositivi e accedere alle risorse dell'azienda, è necessario rivedere le funzionalità tecniche dell'infrastruttura esistente. L'obiettivo di questa revisione consiste nel comprendere se i requisiti della soluzione sono già implementati per questo nuovo modello o se devono essere introdotte nuove tecnologie per risolvere il problema. A tale scopo, è necessario definire una serie di requisiti, nonché i vincoli per l'ambiente. Alcuni dei requisiti e vincoli vengono definiti dagli utilizzatori delle funzionalità; altri vengono definiti dall'ambiente esistente, in termini di funzionalità tecniche esistenti, servizi, criteri e processi.

Determinare i requisiti, i vincoli e la progettazione per consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi gestiti è un processo fondamentale. I requisiti iniziali, insieme ai vincoli dell'ambiente, possono portare a una progettazione iniziale che non è in grado di soddisfare tutti i requisiti iniziali rendendo necessarie modifiche ai requisiti iniziali e una successiva progettazione. Prima di finalizzare i requisiti e la progettazione, sono necessarie più iterazioni per giungere alla definizione dei requisiti e alla progettazione della soluzione. Pertanto, non bisogna aspettarsi che il primo tentativo di progettazione realizzato tramite questo documento sia l'ultimo. Si potrà notare che alcune decisioni prese all'inizio del processo escludano altre opzioni preferibili rese disponibili in una fase successiva del processo.

Le risposte alle domande nelle sezioni successive creano un elenco completo di requisiti per consentire agli utenti di accedere alle risorse aziendali dai propri dispositivi, con la gestione da parte del reparto IT che provvede a mantenere i dati protetti. Tali domande non sono specifiche del fornitore e possono essere applicate a qualsiasi soluzione di infrastruttura BYOD.

Le considerazioni relative il dominio del problema BYOD illustrate in questa guida verranno suddivise in sottodomini. Ogni sottodominio conterrà un insieme di componenti. Per ogni sottodominio descritto in questa guida è previsto un set di requisiti:

- Requisiti di utenti e dispositivi
- Requisiti di protezione e accesso ai dati
- Requisiti di gestione
- Requisiti delle app



<!--HONumber=Apr16_HO2-->


