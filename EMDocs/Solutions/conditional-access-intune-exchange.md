---
title: Usare l'accesso condizionale con Intune ed Exchange Server locale
description: Distribuire Exchange locale con Intune.
keywords: 
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2a64e898-4c60-48bf-ae14-b05e091e0533
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 042bc3afbb5e0ce919b3a07dcbdba6ae27cacaa7
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="deploy-exchange-on-premises-with-intune"></a>Distribuire Exchange locale con Intune

Ora che si sono lette con attenzione le [indicazioni sull'architettura per la protezione di documenti e messaggi di posta elettronica aziendali](architecture-guidance-for-protecting-company-email-and-documents.md) è possibile procedere alla distribuzione di una soluzione.

Per consentire a Intune di gestire i dispositivi mobili, gli utenti devono registrare i dispositivi in Intune.

## <a name="deployment-steps"></a>Passaggi per la distribuzione
Per distribuire la soluzione Exchange locale con Intune, seguire questi passaggi:

### <a name="step-1-install-and-configure-the-microsoft-intune-on-premises-exchange-server-connector"></a>Passaggio 1: Installare e configurare il connettore Exchange Server locale di Microsoft Intune.

Per i dispositivi mobili che gli utenti non hanno registrato, è possibile abilitare la gestione Exchange ActiveSync usando Exchange Connector. Exchange Connector collega l'utente alla distribuzione di Exchange e consente di gestire i dispositivi mobili mediante la console di Intune.

Seguire i passaggi in [Install the Intune on-premises Exchange Connector](/intune/deploy-use/intune-on-premises-exchange-connector) (Installare Intune Exchange Connector locale) per scaricare, installare e configurare Windows Intune Exchange Connector.

> [!IMPORTANT]
> È possibile impostare solo una connessione di Exchange per account di Intune. Se si tenta di configurare una connessione aggiuntiva, la connessione originale sarà sostituita da quella nuova.

### <a name="step-2-create-compliance-policies-and-deploy-to-users"></a>Passaggio 2: Creare criteri di conformità e distribuirli agli utenti.
I criteri di conformità definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme ai criteri di accesso condizionale. Seguire i passaggi in [Creare criteri di conformità dei dispositivi in Microsoft Intune](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune) per creare e distribuire criteri di conformità.

Se si vuole avere la possibilità di rimuovere tutti i messaggi di posta elettronica aziendale da un dispositivo iOS quando non fa più parte dell'azienda, è necessario creare e distribuire un profilo di posta elettronica e quindi impostare i criteri di conformità che specificano che i profili di posta elettronica sono gestiti da Intune. È necessario distribuire il profilo di posta elettronica allo stesso set di utenti a cui sono destinati questi criteri di conformità.
![Screenshot che illustra la sezione "Profili di posta elettronica" della scheda Generale nella procedura guidata per la creazione di criteri in Intune, dove è possibile specificare che un profilo di posta elettronica deve essere gestito da Intune.](./media/ProtectEmail/intune-create-policy-email-profile.PNG)

Se si specificano questi criteri di conformità, un utente che ha già configurato il proprio account di posta elettronica dovrà rimuoverlo manualmente. Intune quindi lo aggiungerà nuovamente attraverso il processo di registrazione descritto in [Esperienza utente finale di accesso condizionale](end-user-experience-conditional-access.md).

> [!IMPORTANT]
> Se non sono stati distribuiti i criteri di conformità e abilitati i criteri di accesso condizionale di Exchange, a tutti i dispositivi di destinazione verrà consentito l’accesso.

### <a name="step-3-identify-users-who-will-be-impacted-by-conditional-access-policy"></a>Passaggio 3: Identificare gli utenti interessati dai criteri di accesso condizionale.
Dopo la configurazione, Exchange Connector inizia a creare l'inventario dei dispositivi non ancora registrati in Intune ma che si connettono a risorse di Exchange dell'organizzazione tramite Exchange Active Sync.  

Seguire le istruzioni in [Valutare l'effetto dei criteri di accesso condizionale](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access) per identificare gli utenti interessati dai criteri di accesso condizionale.


### <a name="step-4-configure-user-groups-for-the-conditional-access-policy"></a>Passaggio 4: Configurare i gruppi utenti per i criteri di accesso condizionale.
I criteri di accesso condizionale sono destinati a diversi gruppi di utenti in base ai tipi di criteri. Questi gruppi contengono gli utenti a cui saranno destinati i criteri o che ne saranno esenti. Quando a un utente viene destinato un criterio, ogni dispositivo in uso deve essere conforme per accedere alla posta elettronica.

Per altre informazioni, vedere [Configurare i gruppi utenti per i criteri di accesso condizionale](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access).

### <a name="step-5-configure-conditional-access-policy"></a>Passaggio 5: Configurare i criteri di accesso condizionale.
Il flusso seguente viene usato dai criteri di accesso condizionale perché un ambiente Exchange locale possa valutare se consentire o bloccare i dispositivi.

![Diagramma di flusso che illustra come i criteri di accesso condizionale per Exchange Server locale valutano se consentire o bloccare i dispositivi.](./media/ProtectEmail/conditional-access-8-2.png)

Per configurare i criteri di accesso condizionale, seguire le indicazioni in [Configurare l'accesso condizionale](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access).

## <a name="reporting"></a>Reporting

### <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorare i criteri di conformità e di accesso condizionale
Per visualizzare i dispositivi bloccati da Exchange:

Nel dashboard di Intune fare clic sul riquadro **Dispositivi bloccati da Exchange** per visualizzare il numero di dispositivi bloccati e i collegamenti ad altre informazioni.
![Screenshot che illustra il riquadro "Dispositivi bloccati da Exchange" nel dashboard di Intune](./media/ProtectEmail/intune-sa-6blocked-devices.PNG)

## <a name="where-to-go-from-here"></a>Come proseguire
Dopo aver distribuito una soluzione per la protezione della posta elettronica aziendale e dei dati di questa all'interno dei dispositivi mobili, è possibile scoprire di più sull'[esperienza dell'utente finale relativa all'accesso condizionale](end-user-experience-conditional-access.md). Ciò consente di prepararsi ad affrontare i problemi che potrebbero verificarsi quando gli utenti finali registrano dispositivi specifici.
