---
title: Sviluppare i requisiti di risposta agli eventi imprevisti
description: Requisiti comuni per lo sviluppo di un processo di risposta agli eventi imprevisti per uno scenario di gestione di dispositivi mobili.
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 10/18/2016
ms.topic: solution
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 6f9fd9b3-492b-48e1-871c-e5abefe1293a
ms.reviewer: 
ms.suite: ems
ms.custom: microsoft-intune
translationtype: Human Translation
ms.sourcegitcommit: cc449bca094772759983cc924b3294a4f6b44d83
ms.openlocfilehash: 91aee40cd8ec7aa38142da3a5617e3c7cb64b7d0


---

# Sviluppare i requisiti di risposta agli eventi imprevisti

>[!NOTE]
>Questo argomento fa parte di una guida più ampia dedicata alle considerazioni di progettazione. Per leggere la guida dall'inizio, vedere l'[argomento principale](mdm-design-considerations-guide.md). Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Sebbene molte organizzazioni abbiano già adottato un piano di risposta agli eventi imprevisti, è importante comprendere se il piano attuale include i dispositivi mobili e quali sono le operazioni da eseguire in caso di evento imprevisto su tali dispositivi. Se la società sta appena iniziando ad adottare una soluzione di mobilità, probabilmente il piano di risposta agli eventi imprevisti in uso non copre gli aspetti specifici relativi ai dispositivi mobili. Se l'organizzazione non ha ancora un piano di risposta agli eventi imprevisti, è importante collaborare strettamente con il team addetto alla sicurezza per comprendere i requisiti mentre si elabora il piano, in modo da sapere quali sono le domande da porre per scegliere la soluzione MDM più adatta alle proprie esigenze. 
 
>[!TIP] 
> [Leggere l'articolo relativo alla risposta agli eventi che riguardano la sicurezza IT](https://technet.microsoft.com/library/cc700825.aspx) per comprendere meglio quali sono i requisiti minimi per lo sviluppo di un piano di risposta.

Quando si progetta la soluzione MDM, assicurarsi di porre le domande seguenti per verificare di poter gestire i dispositivi mobili in caso di evento imprevisto.

- L'organizzazione dispone di un piano di risposta esistente agli eventi imprevisti?
    - In caso affermativo, il piano esistente include i processi e le procedure per la gestione dei dispositivi mobili compromessi?
- La politica di risposta agli eventi imprevisti copre i casi in cui un utente finale segnala di aver smarrito il dispositivo mobile?
    - È possibile cancellare l'intero dispositivo per evitare la perdita di dati? 
        - In caso affermativo, la società dispone di criteri di backup per i dati presenti nei dispositivi mobili?
- L'organizzazione dispone di procedure diverse in caso di smarrimento dei dispositivi aziendali e dei dispositivi personali?
    - In caso affermativo, quali sono tali procedure?
    - Tali procedure influiranno sulla scelta della soluzione MDM?
- Se un utente smarrisce il dispositivo mobile personale ma non autorizza la società a cancellare l'intero contenuto del dispositivo, la soluzione MDM consente la cancellazione selettiva?
- Se un dispositivo mobile è compromesso e si desidera impedire la diffusione di app dannose da tale dispositivo alla rete aziendale, la soluzione MDM consente l'applicazione di criteri che possano rapidamente limitare il dispositivo compromesso?
- La soluzione MDM consente di prevedere potenziali attacchi per intraprendere azioni proattive per la risoluzione dei problemi?
- La soluzione MDM consente di identificare se un file è stato infettato da un malware tramite una console di gestione?




<!--HONumber=Oct16_HO3-->


