---
title: Requisiti di gestione
description: Questo articolo include una serie di requisiti comuni di progettazione della gestione da usare in uno scenario Bring Your Own Device (BYOD).
keywords: 
author: YuriDio
ms.author: yurid
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bf0d4210-5edc-4ad7-bcb5-372099049630
ms.reviewer: 
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 5adb7f68efacdfa20d78c3cf5853fa374793140a
ms.openlocfilehash: 9347d0ff642a3ea4a337962b5ec10a0c4c6cdc66
ms.contentlocale: it-it
ms.lasthandoff: 11/28/2016


---

# <a name="management-requirements"></a>Requisiti di gestione

La gestione dei dispositivi è una funzionalità alla base di qualsiasi strategia incentrata sugli utenti e deve essere valutata rispetto ai requisiti aziendali. A seconda del livello di maturità dell'azienda, è probabile che sia già implementato un sistema di gestione che dovrà essere esteso per coprire gli scenari BYOD adottati dall'azienda. La figura sottostante illustra le interazioni per la gestione di utenti, dispositivi e dati. Fare le dovute considerazioni per ogni componente del sottodominio Gestione.

![Requisiti di gestione](./media/BYOD_Figure4.png)

Quando si considerano i requisiti delle funzionalità di gestione, è consigliabile iniziare ponendo le domande riportate nella sezione seguente.

## <a name="questions-to-ask"></a>Domande da chiedere

Le domande sui requisiti di gestione sono suddivise in sette aree:

- Monitoraggio
- Reporting
- Configurazione
- Calcolo
- Archiviazione
- Automazione
- Distribuzione e provisioning


### <a name="monitoring"></a>Monitoraggio

- L'azienda deve monitorare le impostazioni di conformità come password, fotocamera e crittografia nei dispositivi degli utenti?
- L'azienda vuole distinguere la proprietà dei dispositivi, ovvero i dispositivi di proprietà dell'azienda da quelli di proprietà dell'utente?
- L'azienda vuole consentire agli utenti di reimpostare le password dai propri dispositivi?
- L'azienda deve avere le funzionalità di registrazione incorporate nel sistema di gestione?
- L'azienda deve avere le funzionalità di controllo incorporate nel sistema di gestione?
- L'azienda aggrega questo tipo di registrazione in un unico archivio?

### <a name="reporting"></a>Reporting

- L'azienda necessita di funzionalità per la creazione di rapporti per il modello BYOD?
    - In tal caso, quali tipi di rapporti (ad esempio aggiornamenti, software installati e inventario) sono necessari?
- Il sistema di gestione prevede i requisiti per la creazione di rapporti?
    - In tal caso, è possibile personalizzarli?
- Esiste una differenziazione nei requisiti per la creazione di rapporti tra i dispositivi appartenenti a un dominio e quelli non appartenenti a un dominio?
    - In tal caso, quali sono i requisiti per ogni scenario?

### <a name="configuration"></a>Configurazione

- L'azienda necessita di un sistema di gestione in cui i dispositivi degli utenti devono appartenere a un dominio per poter essere gestiti?
- L'azienda necessita di un sistema di gestione che si integra con la directory esistente?
- L'azienda necessita di un sistema di gestione che gestisce solo le app o deve gestire anche il sistema operativo in esecuzione su dispositivi degli utenti?
- L'azienda necessita di un sistema di gestione che consente di applicare i criteri sui dispositivi degli utenti?
- L'azienda necessita di un sistema di gestione che può essere integrato con i servizi cloud?
- L'azienda intende eseguire una cancellazione selettiva nel caso in cui un utente non necessita più dell'accesso alle app installate?
    - In tal caso, il sistema di gestione prevede il supporto della funzionalità di cancellazione selettiva?

### <a name="compute"></a>Calcolo

- Quali sono le funzionalità di calcolo necessarie per eseguire il sistema di gestione nei server back-end?
- Quali sono le funzionalità di calcolo necessarie per eseguire il sistema di gestione nei dispositivi degli utenti?
- Il sistema di gestione supporta l'uso delle funzionalità cloud per espandere le risorse di calcolo locali?

### <a name="storage"></a>Archiviazione

- Quali sono i requisiti di archiviazione per eseguire il sistema di gestione nei server back-end?
- Quali sono i requisiti di archiviazione per eseguire il sistema di gestione nei dispositivi degli utenti?
- Il sistema di gestione supporta l'uso delle funzionalità cloud per espandere le risorse di archiviazione locali?
- L'azienda deve gestire le unità di archiviazione esterne che vengono aggiunte ai dispositivi degli utenti?
- L'azienda necessita di un sistema di gestione che sia in grado anche di integrarsi con l'archiviazione cloud?

### <a name="automation"></a>Automazione

- Quali operazioni l'azienda intende automatizzare per gli scenari BYOD?
- Quali sono i requisiti di automazione per il sistema di gestione che l'azienda intende adottare?
- Il sistema di gestione esistente supporta la riga di comando incorporata o l'automazione degli script?
- L'azienda ha un sistema di gestione che si integra con i servizi cloud e fornisce le funzionalità di automazione?

### <a name="deployment-and-provisioning"></a>Distribuzione e provisioning

- Quali sono i requisiti per la distribuzione dell'agente di gestione per il sistema di gestione esistente?
- Verranno offerti dei servizi agli utenti remoti di cui sia possibile eseguire immediatamente il provisioning tramite un portale?
- I dispositivi personali vengono registrati con la società dal reparto IT o vengono registrati personalmente?
- È previsto un piano per consentire agli utenti di eseguire il provisioning dei servizi con i propri dispositivi?
    - In tal caso, il sistema di gestione consente agli utenti di eseguire questa operazione dai propri dispositivi in modalità nativa?

