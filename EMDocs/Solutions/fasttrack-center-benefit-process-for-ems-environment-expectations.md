---
title: Previsione per l&quot;ambiente di origine
description: Requisiti dell&quot;ambiente di origine per l&quot;uso di FastTrack Center Benefit
keywords: 
author: staciebarker
manager: angrobe
ms.date: 10/02/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b8c690844c5bae7898bfe908d4ce923a0edf41dd
ms.openlocfilehash: 387a260519fc812a63a35ad4984e6d88d3325d3a


---


# Previsione per l'ambiente di origine
Se si usa [FastTrack Center Benefit per Enterprise Mobility + Security (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Azure Active Directory Premium e/o Microsoft Intune per l'uso, è necessario che l'ambiente soddisfi i requisiti descritti nelle sezioni seguenti.

Se Microsoft Active Directory locale è già presente nell'ambiente corrente, è possibile integrarlo con EMS o qualsiasi altro suo singolo servizio per sfruttare le funzionalità complete di gestione delle identità da una singola console. FastTrack Center Benefit prevede assistenza durante il processo d'integrazione di Microsoft Azure Active Directory con l'implementazione locale esistente. Se l'integrazione è necessaria, l'ambiente di origine deve essere a un livello minimo per tale applicazione.

La tabella seguente illustra le previsioni nell'ambiente di origine esistente per l'onboarding.

|Attività|Previsione per l’ambiente di origine|
|------------|----------------------------------|
|Onboarding di base|Foreste di Active Directory con il livello di foresta funzionale impostato su Windows Server 2008 o versione successiva, con la configurazione di foresta seguente:<br /><br />-   Foresta singola di Active Directory<br />-   Più foreste di Active Directory </br></br>**Nota**: per tutte le configurazioni a più foreste, la distribuzione di AD FS è esterna all'ambito di FastTrack Center Benefit.|
|Caricamento di Microsoft Azure Active Directory Premium|Active Directory e l'ambiente locali sono stati preparati per Azure Active Directory Premium. Quest'ultimo include la correzione dei problemi identificati che impediscono l'integrazione con le funzionalità di Azure Active Directory e Azure Active Directory Premium.|
|Caricamento di Microsoft Intune, solo cloud o integrato con System Center Configuration Manager|Per la gestione di dispositivi con System Center Configuration Manager 2012 R2 o versioni successivi con connessione a Microsoft Intune, gli amministratori IT dovranno seguire l'[Elenco di controllo amministratore: Configurazione di Configuration Manager per la gestione di dispositivi mobili mediante Microsoft Intune](https://technet.microsoft.com/library/jj943763.aspx).</br></br> **Nota**: il service benefit non include l'assistenza per la configurazione o l'aggiornamento di System Center Configuration Manager in base ai requisiti minimi necessari per integrare Microsoft Intune con System Center Configuration Manager.|

**Altre informazioni**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)


<!--HONumber=Oct16_HO3-->


