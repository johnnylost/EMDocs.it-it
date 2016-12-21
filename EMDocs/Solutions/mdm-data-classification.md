---
title: Classificazione dei dati
description: Questo articolo include una serie di considerazioni sulla progettazione per la classificazione dei dati da usare in uno scenario di gestione di dispositivi mobili (MDM).
keywords: 
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 11/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f3486381-66d5-469a-93a3-013eaaa17c07
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5adb7f68efacdfa20d78c3cf5853fa374793140a
ms.openlocfilehash: 94c02152e553bdeba1bd1568c409d816ac078e9a


---

# <a name="data-classification"></a>Classificazione dei dati

>[!NOTE]
>Questo argomento fa parte di una guida più ampia dedicata alle considerazioni di progettazione. Per leggere la guida dall'inizio, vedere l'[argomento principale](mdm-design-considerations-guide.md). Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

La maggior parte delle aziende ha già adottato un criterio di [classificazione dei dati](http://blogs.microsoft.com/cybertrust/2014/01/28/the-importance-of-data-classification/), quindi è necessario capire in che modo la distribuzione di una soluzione di gestione dei dispositivi mobili influisce su tale criterio. Se la società non dispone di un criterio di classificazione dei dati corrente, è consigliabile introdurre questa funzionalità insieme alla pianificazione della soluzione di gestione dei dispositivi mobili. Alcune organizzazioni eseguono la classificazione dei dati in locale al livello del file server usando [Active Directory Rights Management Services (ADRMS)](https://technet.microsoft.com/windowsserver/dd448611.aspx). Un altro strumento che alcune aziende usano per identificare, classificare e proteggere i dati nei file server è [Microsoft Data Classification Toolkit](http://www.microsoft.com/download/details.aspx?id=27123).

Office 365 offre alcune funzionalità di classificazione automatica dei dati delle e-mail che consentono di rendere visibili informazioni riservate che devono essere protette. Office 365 usa regole di trasporto incorporate nell'elaborazione del flusso di posta per rilevare le informazioni riservate. La [funzionalità di prevenzione della perdita dei dati](http://blogs.office.com/2013/10/28/office-365-compliance-controls-data-loss-prevention/) esegue l'analisi approfondita del contenuto tramite le corrispondenze di parole chiave, le corrispondenze del dizionario, la valutazione dell'espressione regolare, funzioni interne come la convalida del checksum nei numeri di carta di credito e l'analisi di altri contenuti per individuare tipi di contenuti specifici all'interno del corpo del messaggio o degli allegati.

La classificazione dei dati non è integrata in Intune e Configuration Manager, che quindi si affidano alla classificazione basata su cloud con Azure RMS o alla classificazione locale con ADRMS. Un'altra opzione consiste nell'uso di [Enterprise Mobility + Security (EMS)](http://www.microsoft.com/server-cloud/enterprise-mobility/overview.aspx) come soluzione MDM. Con EMS sarà possibile accedere ad [Azure AD Premium](https://msdn.microsoft.com/library/azure/dn532272.aspx) e [Azure RMS](https://technet.microsoft.com/library/jj585026.aspx), che possono essere usati per la classificazione dei dati. La classificazione dei dati con Azure RMS può essere integrata con una soluzione di gestione locale in un ambiente ibrido.

Intune consente al reparto IT di assicurare la conformità usando criteri costituiti da regole e impostazioni che un dispositivo deve soddisfare per essere considerato conforme ai criteri di accesso condizionale. È inoltre possibile usare tali criteri per monitorare e correggere i problemi di conformità con i dispositivi, indipendentemente dall'accesso condizionale. Per altre informazioni, vedere [Gestire i criteri di conformità del dispositivo per Microsoft Intune](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

Usare la tabella seguente come riferimento per la scelta dell'opzione MDM più adatta ai requisiti aziendali relativi alla *classificazione dei dati*.

## <a name="intune-standalone"></a>Intune (autonomo)

**Vantaggi**

- Non disponibile

**Svantaggi**

- Non disponibile

## <a name="mdm-for-office-365"></a>Gestione dei dispositivi mobili per Office 365

**Vantaggi**

- È possibile usare le regole di trasporto di Exchange per rilevare le informazioni riservate
- Usa i criteri di [prevenzione della perdita dei dati (DLP)](https://technet.microsoft.com/library/ms.o365.cc.DLPLandingPage.aspx) del Centro conformità per identificare le informazioni riservate in numerose posizioni

**Svantaggi**

- La classificazione dei dati non è contenuta all'interno del file. Una volta che il file si trova nel dispositivo mobile, può essere usato senza restrizioni

## <a name="hybrid-intune-with-configmgr"></a>Ibrida (Intune con Configuration Manager)

**Vantaggi**

- Non disponibile

**Svantaggi**

- Non disponibile

## <a name="enterprise-mobility--security"></a>Enterprise Mobility + Security

**Vantaggi**

- Sfrutta Azure RMS per eseguire la classificazione dei dati
- La sottoscrizione di Azure RMS è inclusa in EMS
- Non richiede un'infrastruttura locale per la classificazione di dati
- Può essere integrata con le soluzioni di AD RMS locali esistenti
- La protezione si trova all'interno del file, pertanto il file manterrà la classificazione anche se è stato salvato in un percorso diverso

**Svantaggi**

- Non è disponibile per i clienti che non adottano una soluzione basata su cloud



<!--HONumber=Nov16_HO4-->


