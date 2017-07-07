---
title: Proteggere i dati aziendali usando MAM con MDM
description: Creare e distribuire le app con i criteri di gestione delle app per dispositivi mobili (MAM) per proteggere meglio i dati aziendali.
keywords: 
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6c7088a9-ca88-4ff2-97a6-f842691fd3c7
ms.reviewer: 
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 0be1ad609016303572b67676c03f544d88fb5576
ms.openlocfilehash: 88625a3bc5ac5f1a877650f73185721674e0f28d
ms.contentlocale: it-it
ms.lasthandoff: 07/07/2017


---

# <a name="protect-company-data-on-mobile-devices-through-app-management-policies"></a>Proteggere i dati aziendali nei dispositivi mobili usando i criteri di gestione delle app
La protezione dei dati aziendali è di vitale importanza e rappresenta un compito sempre più complesso man mano che aumenta il numero di dipendenti che usano i dispositivi mobili personali per accedere alle risorse aziendali, inclusi i messaggi e gli allegati di posta elettronica. Per gli amministratori IT è importante assicurarsi che i dati aziendali siano protetti anche quando quei dispositivi mobili non si trovano all'interno della sede fisica dell'azienda.

Questa guida è incentrata sull'abilitazione delle applicazioni gestite in relazione a due distribuzioni di Intune MDM:

- Come soluzione di gestione del cloud con Intune
- Come servizio integrato con Configuration Manager

In questo modo è possibile creare e distribuire le app con i criteri di gestione delle app per dispositivi mobili (MAM) per proteggere meglio i dati aziendali.

Questo documento illustra la creazione dei criteri basati su MAM quando il dispositivo dell'utente finale viene registrato in Intune per MDM. Vedere [Proteggere app e dati line-of-business su dispositivi non registrati](https://docs.microsoft.com/intune/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune) per informazioni sulla configurazione dei criteri MAM quando il dispositivo non è registrato in Intune per MDM.

> [!TIP]
> È possibile scaricare una copia dell'intero argomento nella [Raccolta TechNet](https://gallery.technet.microsoft.com/Protect-Company-Data-on-d972f4f4/file/154240/1/Protect%20Company%20Data%20on%20Mobile%20Devices%20through%20Application%20Management%20Policies.pdf).

## <a name="introduction"></a>Introduzione
Le app gestite sono app a cui sono applicati criteri MAM per renderle conformi ai requisiti di sicurezza aziendali. Sono disponibili due opzioni per la gestione delle app per dispositivi mobili:
- **La funzionalità predefinita**, ad esempio Apple Managed Open In, che protegge i dati aziendali controllando le app autorizzate ad aprire determinati documenti e allegati di posta elettronica
- **Intune App SDK**, che consente di limitare la funzionalità e la condivisione dei dati per le app con Intune App SDK abilitato. Alcune delle funzionalità principali di Intune App SDK consentono di:
  - Gestire la funzione di salvataggio con nome
  - Impedire operazioni di taglia, copia e incolla
  - Richiedere l'autenticazione quando si accede a un'app
  - Cancellare i dati aziendali da un'app gestita da Intune

  Vedere [Panoramica di Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk) per una descrizione di tutte le funzionalità dell'SDK.

## <a name="before-you-begin"></a>Prima di iniziare
- **Informazioni sulla distribuzione di app con Microsoft Intune:**  [nozioni di base](https://docs.microsoft.com/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) sulla distribuzione delle app di Intune.

- **Valutare l'implementazione da eseguire:** tra tutte le opzioni di progettazione e configurazione per la gestione dei dispositivi mobili, è difficile determinare quale combinazione soddisfi meglio le esigenze dell'azienda. L'articolo [Guida alle considerazioni sulla progettazione per la gestione dei dispositivi mobili](https://docs.microsoft.com/enterprise-mobility/Solutions/mdm-design-considerations-guide) consente di comprendere i requisiti per la progettazione di una soluzione di gestione dei dispositivi mobili e indica in dettaglio i passaggi e le attività che è possibile eseguire per progettare una soluzione adatta alle esigenze tecnologiche e di business dell'azienda.
- **Comprendere l'esperienza dell'utente finale di alto livello:** dopo aver implementato la soluzione, si sarà in grado di proteggere i dati sui dispositivi anche se l'azienda non li gestisce. È sufficiente implementare criteri a livello di app per limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

   > [!NOTE]
   > L'esperienza dell'utente finale di questa soluzione è descritta in dettaglio nell'articolo [Esperienza dell'utente finale](end-user-experience-mam.md).

- **Conoscere il ciclo di vita dell'app:** come nel caso della gestione dei dispositivi, anche le app hanno un ciclo di vita che va dalla preparazione alla distribuzione, al monitoraggio, all'aggiornamento, fino al ritiro. Intune può risultare utile in tutte le fasi di questo ciclo di vita. Per informazioni dettagliate sul ciclo di vita delle app, vedere [Panoramica del ciclo di vita dell'app](https://docs.microsoft.com/intune/deploy-use/overview-of-app-lifecycle-in-microsoft-intune).
- **Conoscere le app Microsoft che si possono usare con i criteri MAM:** la pagina dei [partner delle applicazioni di Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) contiene le informazioni più recenti sulle app Microsoft e di altre società che è possibile usare con i criteri di gestione delle app mobili.

  È possibile usare lo strumento di wrapping delle app di Microsoft Intune per Android per modificare il comportamento delle app interne in modo da configurare le funzionalità dell'app senza modificare il codice dell'app stessa. Per informazioni più specifiche, vedere gli argomenti seguenti:
 - [Preparare le app per iOS per la gestione delle applicazioni mobili con lo strumento di wrapping delle app di Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
 - [Preparare le app per Android per la gestione delle app mobili con lo strumento di wrapping delle app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

- **Sapere come vengono risolti i conflitti di criteri:** in caso di conflitto di criteri di gestione delle app mobili nella prima distribuzione all'utente o al dispositivo, il valore di impostazione specifico in conflitto verrà rimosso dai criteri distribuiti all'app e l'app userà un valore predefinito. Il valore predefinito è quello **più restrittivo**.

  Quando si verifica un conflitto dei criteri di gestione delle applicazione mobili nelle successive distribuzioni all'utente o al dispositivo, il valore di impostazione specifico in conflitto non verrà aggiornato nei criteri distribuiti all'app e l'app userà il valore esistente per tale impostazione.

  Nei casi in cui il dispositivo o l'utente riceva due criteri in conflitto, si applica il comportamento seguente:
  - Se un criterio è già stato distribuito al dispositivo, le impostazioni di criteri esistenti non vengono sovrascritte.
  - Se al dispositivo non è stato ancora distribuito alcun criterio e vengono distribuite due impostazioni in conflitto, viene usata l'impostazione predefinita del dispositivo.

## <a name="where-to-go-from-here"></a>Come proseguire
Dopo aver acquisito una certa familiarità con il processo generale di MAM, è possibile [usare i criteri di gestione delle app mobili in Intune](mam-intune.md) o [i criteri di gestione delle app mobili in Configuration Manager](mam-configmgr.md). È anche possibile vedere altre informazioni [sull'esperienza dell'utente finale con MAM](end-user-experience-mam.md).

