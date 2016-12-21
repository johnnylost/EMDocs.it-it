---
title: Uso dei criteri di gestione delle app mobili in Intune
description: Creare e distribuire un&quot;app in Intune con i criteri di gestione delle app mobili.
keywords: 
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d7c4104-b85f-407e-8832-0e6bbac934f5
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0eacdea52150bc8282df618ae73c96724cec26c5
ms.openlocfilehash: 2efaf8b6298cabd640f141675b5cefe3f77aaae7


---

# Usare i criteri di gestione delle app mobili in Intune
Uno dei motivi principali per cui molte aziende usano Microsoft Intune è la possibilità di distribuire le app che servono agli utenti per completare il proprio lavoro. Prima di distribuire le app, sarà necessario [gestire i dispositivi](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

Se, ad esempio, la società usa Microsoft Word, sono disponibili versioni per Windows, iOS, Android e altri sistemi ancora. La sfida che gli amministratori IT devono affrontare è riuscire a gestire la grande varietà di app disponibili per le diverse piattaforme di dispositivi e computer, per consentire agli utenti di lavorare garantendo al tempo stesso la sicurezza dei dati aziendali.

Se si usa Intune con Configuration Manager, vedere [Come controllare le app usando i criteri di gestione delle applicazioni mobili in Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396).

I criteri di gestione delle app mobili (MAM) supportano:
- Dispositivi che eseguono Android 4 e versioni successive
- Dispositivi che eseguono iOS 7 e versioni successive

> [!NOTE]
> I criteri MAM supportano i dispositivi registrati con Intune. Per informazioni su come creare criteri di gestione delle app per i dispositivi non gestiti da Intune, vedere [Proteggere i dati delle app usando i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).

A differenza di altri criteri di Intune, i criteri MAM non vengono distribuiti direttamente. ma, al contrario, è possibile associare i criteri all'app che si vuole limitare. Le impostazioni specificate diventeranno effettive quando l'app viene distribuita e installata nei dispositivi.

Per applicare restrizioni a un'app, questa deve includere Microsoft Intune App Software Development Kit (SDK). Esistono due metodi per ottenere questo tipo di app:

- **Usare un'app gestita da criteri**: include App SDK. Per aggiungere questo tipo di applicazione, è possibile specificare un collegamento all'app da un archivio di app, ad esempio l'iTunes store o Google Play. Non sono richieste ulteriori elaborazioni per questo tipo di app. Per visualizzare l'elenco completo delle app Microsoft supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella pagina dei [partner di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners). Fare clic sull'app per visualizzare gli scenari e le piattaforme supportate e per verificare se l'app supporta identità multiple.
- **Usare un'app di cui è stato eseguito il wrapping**: app che sono state riassemblate per includere App SDK usando lo strumento di wrapping delle app di Microsoft Intune. Questo strumento viene in genere usato per elaborare le app aziendali create internamente. Non può essere usato per elaborare le app state scaricate dall'App Store. Per altre informazioni, vedere gli argomenti indicati di seguito.
  - [Preparare le app per iOS per la gestione delle applicazioni mobili con lo strumento di wrapping delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
  - [Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

Alcune app gestite, come l'app Outlook per iOS e Android, supportano **più identità**. Ciò significa che Intune si applica solo le impostazioni di gestione di account aziendali o dati nell'applicazione.

Ad esempio, utilizzando Outlook app:
- Se l'utente configura un account di posta elettronica aziendale e uno personale, Intune applica le impostazioni di gestione solo all'account aziendale e non gestisce l'account personale.
- Se il dispositivo viene ritirato o unenrolled, solo i dati aziendali di Outlook viene rimosso dal dispositivo.
- L'account aziendale usato deve essere lo stesso account specificato durante la registrazione del dispositivo con Intune.

Anche Word, Excel e PowerPoint supportano più identità, ma le restrizioni per i criteri vengono applicate solo in caso di gestione e modifica dei dati aziendali riservati da parte di un servizio, ad esempio OneDrive o SharePoint.

## Creare e distribuire un'app in Intune con i criteri di gestione delle app mobili

- Passaggio 1: Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stato eseguito il wrapping.
- Passaggio 2: Pubblicare l'app nello spazio di archiviazione cloud.
- Passaggio 3:Creare i criteri di gestione delle app mobili.
- Passaggio 4: Distribuire l'app selezionando l'opzione per associarla ai criteri di gestione delle app mobili.
- Passaggio 5: Monitorare la distribuzione dell'app

### Passaggio 1: Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stato eseguito il wrapping
- **Per ottenere un collegamento a un'app gestita da criteri**: nell'App Store trovare e prendere nota dell'URL dell'app gestita da criteri che si vuole distribuire.
Ad esempio, l'URL dell'app Microsoft Word per iPad è [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- **Per creare un'app di cui è stato eseguito il wrapping:** usare le informazioni negli argomenti [Preparare le app iOS per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) e [Preparare le app Android per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool). Lo strumento crea un'app elaborata che verrà usata quando si pubblica l'app nello spazio di archiviazione cloud.

### Passaggio 2: Caricare l'app nello spazio di archiviazione cloud
Quando si pubblica un'app gestita, le procedure possono essere diverse a seconda che l'app sia gestita tramite criteri o elaborata con lo strumento di wrapping delle app di Microsoft Intune per iOS.

Vedere [Aggiungere app per dispositivi mobili in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune#add-the-app) per la procedura necessaria per caricare un'app nello spazio di archiviazione cloud.

### Passaggio 3: Creare i criteri di gestione delle app mobili
Il portale di Azure è la console di amministrazione consigliata per la creazione dei criteri MAM. Il portale di Azure supporta gli scenari MAM seguenti:
- Dispositivi registrati in Intune
- Dispositivi gestiti da una soluzione MDM di terze parti
- Dispositivi non gestiti da nessuna soluzione MDM (BYOD).

Per altre informazioni sull'uso del portale di Azure per creare un criterio MAM, vedere [Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

Se si sta usando la console di amministrazione di Intune per la gestione dei dispositivi, è possibile creare un criterio MAM che supporta le app per i dispositivi registrati in Intune mediante la [console di amministrazione di Intune](https://docs.microsoft.com/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console#-step-3-create-a-mobile-application-management-policy) stessa.


### Passaggio 4: Distribuire l'app, selezionando l'opzione per associarla con i criteri di gestione delle applicazioni mobili
Se si sta usando il portale di Azure, [distribuire il criterio MAM agli utenti](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune#deploy-a-policy-to-users).

Se si sta usando il portale di Intune, [distribuire l'app](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune#deploy-an-app) assicurandosi di selezionare i criteri di gestione delle app per dispositivi mobili nella pagina Gestione delle app mobili per associare i criteri all'app.

Se viene annullata la registrazione del dispositivo da Intune, i criteri non verranno rimossi dalle app. Tutte le app a cui erano stati applicati i criteri conserveranno le impostazioni dei criteri anche dopo la disinstallazione e reinstallazione dell'app.

#### Cosa fare quando un'app è già stata distribuita nei dispositivi

Potrebbero esserci situazioni in cui si distribuisce un'app e un utente o un dispositivo ha già una versione non gestita di quell'app, ad esempio se un utente ha installato Microsoft Word dall'app store.

In questo caso, è necessario chiedere all'utente di disinstallare manualmente la versione non gestita in modo da poter installare la versione gestita che è stata configurata.

Tuttavia, per i dispositivi che eseguono iOS 9 e versioni successive, Intune chiederà automaticamente all'utente l'autorizzazione ad assumere la gestione dell'app esistente. Se l'utente accetta, l'app verrà gestita da Intune e verranno applicati anche tutti i criteri MAM associati all'app.


### Passaggio 5: Monitorare la distribuzione dell'app con i criteri MAM
Usare le procedure seguenti per monitorare la distribuzione dell'app dalla console di Intune e risolvere eventuali conflitti di criteri.

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Gruppi**.
2. Eseguire uno dei passaggi seguenti:
  -  Fare clic su **Tutti gli utenti**, quindi fare doppio clic sull'utente di cui si vuole esaminare i dispositivi. Nella pagina Proprietà utente fare clic su **Dispositivi**, quindi fare doppio clic sul dispositivo da esaminare.
  -  Fare clic su **Tutti i dispositivi > Tutti i dispositivi mobili**. Nella pagina Proprietà gruppo dispositivi fare clic su **Dispositivi**, quindi fare doppio clic sul dispositivo da esaminare.
3. Nella pagina Proprietà del dispositivo mobile fare clic su **Criteri** per visualizzare un elenco dei criteri MAM che sono stati distribuiti nel dispositivo.
4. Selezionare i criteri MAM di cui si vuole visualizzare lo stato. È possibile visualizzare i dettagli dei criteri nel riquadro inferiore ed espandere il relativo nodo per visualizzarne le impostazioni.
5.  Nella colonna Stato dei criteri MAM viene visualizzato lo stato Conforme, È conforme (in sospeso) o Errore. Se una o più impostazioni dei criteri selezionati sono in conflitto, in questo campo verrà visualizzato Errore.
6.  Dopo aver identificato un conflitto, è possibile modificare le impostazioni dei criteri in conflitto per usare la stessa impostazione o distribuire un solo criterio per l'app e l'utente.

> [!NOTE]
> Altre informazioni generali sul monitoraggio delle app sono disponibili dal [portale di Azure](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) o dalla [console di Intune](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune).

## Come proseguire

Dopo aver creato e distribuito un'app associata a un criterio MAM, sarà possibile approfondire la conoscenza [dell'esperienza dell'utente finale con MAM](end-user-experience-mam.md). Questo consente di prepararsi ad affrontare eventuali problemi che potrebbero verificarsi.



<!--HONumber=Nov16_HO2-->


