---
title: Separazione dei dati
description: Questo articolo include una serie di considerazioni sulla progettazione per la separazione dei dati da usare in uno scenario di gestione di dispositivi mobili (MDM).
keywords: 
author: YuriDio
ms.author: yurid
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 50bd37fe-30b5-4a45-9c36-0b907dd13cc2
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: ffed65ca17663ac0e2ff758318bbf6f0e1540b57
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="data-segregation"></a>Separazione dei dati

>[!NOTE]
>Questo argomento fa parte di una guida più ampia dedicata alle considerazioni di progettazione. Per leggere la guida dall'inizio, vedere l'[argomento principale](mdm-design-considerations-guide.md). Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

La separazione dei dati non solo è importante per l'organizzazione, ma anche per proteggere i dati personali dell'utente. La separazione dei dati consente di rimuovere tutte le app e i dati aziendali da un dispositivo appartenente a un utente senza alcun effetto sui dati personali dell'utente (vedere la figura che segue).

![Separazione dei dati](./media/MDM_Figure_10.png)

## <a name="users-personal-data-is-isolated-from-companys-data"></a>I dati personali dell'utente vengono separati dai dati dell'azienda

Mantenendo separate tutte le app, i dati aziendali e i criteri distribuiti dalla soluzione MDM, è possibile se necessario rimuoverli dal dispositivo tramite la cancellazione selettiva, senza alcun effetto sui contenuti e sulle app personali dell'utente.

>[!TIP]
> Per informazioni sul funzionamento della cancellazione remota in altre piattaforme, ad esempio iOS e Android, vedere [Proteggere i dati con la cancellazione selettiva o completa tramite Microsoft Intune](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune).

La cancellazione selettiva per la gestione dei dati dei dispositivi mobili è inclusa in Windows Server 2012 R2 e in Windows 8.1. Può essere usata collegando le risorse che consentono agli amministratori di Exchange Server e Microsoft Intune di gestire i dati aziendali nei dispositivi e di sviluppare app in grado di usare le funzionalità della [cancellazione selettiva di Windows](https://technet.microsoft.com/library/dn486874.aspx).  Windows Phone 8 e versioni successive supporta la separazione dei dati nell'archiviazione interna.

![Separazione dei dati](./media/MDM_Figure_11.png)

Per altre informazioni sulle funzionalità di sicurezza di Windows Phone 8.1, scaricare la [Panoramica sulla protezione di Windows Phone 8.1](http://www.microsoft.com/download/details.aspx?id=42509).

La separazione dei dati può risultare difficile se gli utenti passano dagli account personali agli account aziendali sui dispositivi mobili. In uno scenario di dispositivi mobili personali (BYOD) in genere gli utenti usano più credenziali per eseguire attività diverse sul dispositivo.

La funzionalità Protezione dei dati aziendali (EDP, Enterprise Data Protection) esegue la separazione dei dati, ma non usa i contenitori né richiede una versione speciale di un'app per accedere ai dati aziendali e successivamente una seconda istanza per accedere ai dati personali. Non esistono contenitori, partizioni o cartelle speciali per separare fisicamente i dati personali da quelli aziendali. Windows 10 Mobile è invece il gestore del controllo di accesso e identifica i dati aziendali perché sono crittografati per l'azienda.

EDP esegue la separazione dei dati crittografando i dati aziendali. Per altre informazioni, vedere l'[introduzione a Protezione dei dati aziendali (EDP)](https://technet.microsoft.com/library/dn985838.aspx). I criteri EDP di Intune gestiscono l'elenco di app protette da EDP, i percorsi di rete aziendali, il livello di protezione e le impostazioni di crittografia.

Quando un utente installa e accede a un'app che supporta più identità (multi-identità) su un dispositivo gestito da Intune, ad esempio Outlook, Intune verifica se l'account in uso corrisponde all'account gestito sul dispositivo. Se l'account è gestito ed è disponibile un criterio per l'app e per l'utente, le impostazioni del criterio proteggono i dati in tale account. Quando l'utente aggiunge account personali all'app, tali account non rientrano nella gestione e nella protezione di Intune. Ciò consente l'uso personale dell'applicazione senza compromettere la protezione aziendale. Per altre informazioni sulle funzionalità multi-identità in Intune, vedere [Proteggere i dati delle app usando i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console).

Nella tabella che segue vengono confrontate le funzionalità di cancellazione selettiva disponibili con diverse soluzioni MDM in modo da poter scegliere la soluzione più adatta ai requisiti di separazione dei dati dell'organizzazione.

## <a name="intune-standalone"></a>Intune (autonomo)

**Vantaggi**

- Consente di eseguire cancellazioni selettive per rimuovere solo i dati aziendali presenti nei dispositivi mobili
- Consente di eseguire il ripristino delle impostazioni predefinite e di cancellare completamente i dispositivi mobili
- Supporto per le app multi-identità

**Svantaggi**

- Non include la crittografia nativa per l'archiviazione dei dispositivi mobili
- La mancanza dell'integrazione con la piattaforma MDM locale corrente indica che sarà disponibile un'interfaccia di gestione aggiuntiva

## <a name="office-365-with-mdm"></a>Office 365 con MDM

**Vantaggi**

- Consente di eseguire il ripristino delle impostazioni predefinite e di cancellare completamente i dispositivi Android, Windows Phone e iOS
- Consente di eseguire cancellazioni selettive sui dispositivi Android, Windows Phone e iOS per rimuovere dai dispositivi mobili solo i dati aziendali

**Svantaggi**

- La mancanza dell'integrazione con la piattaforma MDM locale corrente indica che sarà disponibile un'interfaccia di gestione aggiuntiva

## <a name="hybrid-intune-with-configmgr"></a>Ibrida (Intune con Configuration Manager)

**Vantaggi**

- Consente di eseguire cancellazioni selettive per rimuovere dai dispositivi mobili solo i dati aziendali
- Consente di eseguire il ripristino delle impostazioni predefinite e di cancellare completamente i dispositivi mobili
- Supporto per le app multi-identità
- Unica console di gestione per gestire i dispositivi mobili basati su cloud e locali

**Svantaggi**

- Se l'organizzazione attualmente non usa un'infrastruttura locale di Configuration Manager, è necessario pianificare, installare e configurare questa piattaforma prima dell'integrazione

Leggere l'articolo [Proteggere i dati con la cancellazione selettiva o completa tramite Microsoft Intune](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune) per sapere in che modo i dati vengono rimossi e mantenuti dopo una cancellazione selettiva per ogni piattaforma per dispositivi mobili. Se si usa un ambiente ibrido, vedere l'articolo [Proteggere i dati con Cancellazione remota, Blocco remoto o Reimpostazione passcode usando Configuration Manager](https://technet.microsoft.com/library/dn956981.aspx) per capire come si usa Configuration Manager per eseguire questa operazione.
