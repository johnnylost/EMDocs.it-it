---
title: Uso dei criteri di gestione delle app mobili in Configuration Manager
description: Creare e distribuire un'app in Configuration Manager con i criteri di gestione delle app mobili (MAM).
keywords: 
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74288276-84d3-4d24-8307-7875491be9c9
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: d0bc5fb61b481256d816df7c898ade798379aa19
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="use-mobile-app-management-policies-in-configuration-manager"></a>Usare i criteri di gestione delle app mobili in Configuration Manager
A partire da System Center 2012 Configuration Manager SP2, i criteri di gestione delle applicazioni consentono di modificare la funzionalità delle app distribuite per adeguarle ai criteri aziendali di conformità e di sicurezza. Ad esempio, è possibile limitare le operazioni taglia, copia e incolla in un'app con restrizioni oppure configurare un'app per aprire tutti i collegamenti Web in un browser gestito. I criteri di gestione delle app supportano:

- Dispositivi che eseguono Android 4 e versioni successive
- Dispositivi che eseguono iOS 7 e versioni successive

> [!TIP]
> Oltre che per i dispositivi gestiti, è possibile usare i criteri di gestione delle app mobili (MAM) per proteggere le app nei dispositivi non gestiti da Intune. Mediante questa nuova funzionalità, è possibile applicare criteri di gestione delle app mobili ad app che si connettono ai servizi di Office 365. Questa funzionalità non è supportata per le app che si connettono ai servizi locali di Exchange o SharePoint.
Per usare questa nuova funzionalità, è necessario usare il portale di Azure. Per acquisire familiarità con tale funzionalità, usare gli argomenti seguenti:
- [Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)
- [Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

A differenza delle linee di base e degli elementi di configurazione in Configuration Manager, non si distribuisce un criterio di gestione delle applicazioni direttamente. Al contrario, è possibile associare i criteri al tipo di distribuzione delle app che si vuole limitare. Le impostazioni specificate diventeranno effettive quando il tipo di distribuzione delle app viene distribuito e installato nei dispositivi.

Per applicare restrizioni a un'app, questa deve includere Microsoft Intune App Software Development Kit (SDK). Esistono due metodi per ottenere questo tipo di app:

- **Usare un'app gestita con criteri** (Android e iOS): include App SDK. Per aggiungere questo tipo di applicazione, è possibile specificare un collegamento all'app da un archivio di app, ad esempio l'iTunes store o Google Play. Non sono richieste ulteriori elaborazioni per questo tipo di app. Per un elenco delle app gestite da criteri disponibili per dispositivi iOS e Android, vedere la [raccolta di applicazioni per dispositivi mobili di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
- **Usare un'app di cui è stato eseguito il wrapping** (Android e iOS): app riassemblate per includere App SDK usando lo strumento per la disposizione testo per app di Microsoft Intune. Questo strumento viene in genere usato per elaborare le app aziendali create internamente. Non può essere usato per elaborare le app state scaricate dall'App Store. Vedere [Preparare le app per iOS per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) e [Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## <a name="create-and-deploy-an-app-in-configuration-manager-with-a-mobile-app-management-policy"></a>Creare e distribuire un'app in Configuration Manager con i criteri di gestione delle app mobili

- Passaggio 1: Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stato eseguito il wrapping.
- Passaggio 2: Creare un'applicazione di Configuration Manager che contenga un'app.
- Passaggio 3:Creare i criteri di gestione delle app mobili.
- Passaggio 4: Associare i criteri di gestione delle app a un tipo di distribuzione.
- Passaggio 5: Monitorare la distribuzione dell'app

### <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>Passaggio 1: Ottenere il collegamento a un'app gestita da criteri o creare un'app di cui è stato eseguito il wrapping.
- **Per ottenere un collegamento a un'app gestita da criteri**: nell'App Store trovare e prendere nota dell'URL dell'app gestita da criteri che si vuole distribuire.
Ad esempio, l'URL dell'app Microsoft Word per iPad è [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- **Per creare un'app di cui è stato eseguito il wrapping:** usare le informazioni negli argomenti [Preparare le app iOS per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) e [Preparare le app Android per la gestione delle applicazioni mobili con lo strumento per la disposizione testo delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool). Lo strumento crea un'app elaborata e un file manifesto associato. Questi file verranno usati quando si crea un'applicazione di Configuration Manager contenente l'app.

### <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>Passaggio 2: Creare un'applicazione di Configuration Manager che contenga un'app.
La procedura per creare l'applicazione di Configuration Manager è diversa se si usa un'app gestita da criteri (collegamento esterno) o un'app creata con lo strumento per la disposizione testo delle app di Microsoft Intune per iOS (Pacchetto app per iOS).

Vedere [Come controllare le app usando i criteri di gestione delle applicazioni mobili in Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step2) per la procedura necessaria per creare un'applicazione di Configuration Manager che contenga un'app.

Al termine della procedura, la nuova applicazione viene visualizzata nel nodo **Applicazioni** dell'area di lavoro **Raccolta software**.

### <a name="step-3-create-a-mobile-application-management-policy"></a>Passaggio 3: Creare criteri di gestione delle applicazioni mobili.
Creare quindi un [criterio di gestione delle applicazioni](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#bkmk_step3) che verrà associato all'applicazione. È possibile creare criteri di Managed Browser o generali.

Al termine della procedura di creazione, il nuovo criterio viene visualizzato nel nodo **Criteri di gestione delle applicazioni** dell'area di lavoro **Raccolta software**.

### <a name="step-4-associate-the-app-management-policy-with-a-deployment-type"></a>Passaggio 4: Associare i criteri di gestione delle app a un tipo di distribuzione.
Quando viene creato un tipo di distribuzione per un'app che richiede un criterio di gestione delle applicazioni, Configuration Manager riconosce che è necessario collegare un criterio di gestione delle app a questo tipo di distribuzione se l'app associata viene distribuita e richiede l'associazione a un criterio di gestione delle app. Per il tipo Managed Browser, sarà necessario associare i criteri Managed Browser e Generale. Per altre informazioni , vedere [Come creare e distribuire applicazioni per dispositivi mobili in Configuration Manager](https://technet.microsoft.com/library/dn469410.aspx).

> [!TIP]
> Per i dispositivi che eseguono sistemi operativi precedenti a iOS 7.1, i criteri associati non verranno rimossi quando si disinstalla l'app.

> Se viene annullata la registrazione del dispositivo da Configuration Manager, i criteri non vengono rimossi dalle app. Nelle app con i criteri applicati verranno mantenute le impostazioni dei criteri anche dopo che l'applicazione viene disinstallata e reinstallata.


### <a name="step-5-monitor-the-app-deployment"></a>Passaggio 5: Monitorare la distribuzione dell'app
Dopo aver creato e distribuito un'app associata a criteri MAM, è possibile [monitorare l'app e risolvere eventuali conflitti di criteri](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step5).

Per informazioni generali sul monitoraggio delle applicazioni, vedere [Come monitorare le applicazioni in Configuration Manager](https://technet.microsoft.com/library/gg682201.aspx).

## <a name="where-to-go-from-here"></a>Come proseguire

Dopo aver creato e distribuito un'app associata a un criterio MAM, sarà possibile approfondire la conoscenza [dell'esperienza dell'utente finale con MAM](end-user-experience-mam.md). Questo consente di prepararsi ad affrontare eventuali problemi che potrebbero verificarsi.
