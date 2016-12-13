---
title: Requisiti per l&quot;ambiente di origine
description: Requisiti dell&quot;ambiente di origine per l&quot;uso di FastTrack Center Benefit
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 999947648cdf98b94312dfd2e700cc8d74011a99
ms.openlocfilehash: ac5783c0343f1e92dbf6d5f0352ae22591fb7def


---


# <a name="source-environment-expectations"></a>Requisiti per l'ambiente di origine
Se si usa [FastTrack Center Benefit per Enterprise Mobility + Security (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Microsoft Azure Active Directory Premium e Microsoft Intune per l'uso, è necessario che l'ambiente soddisfi i requisiti descritti nelle sezioni seguenti.

Se Microsoft Active Directory locale è già presente nell'ambiente corrente, è possibile integrarlo con EMS o qualsiasi altro suo singolo servizio per sfruttare le funzionalità avanzate di gestione delle identità da una singola console. FastTrack Center Benefit include l'assistenza durante l'integrazione di Azure AD con l'implementazione locale esistente. Se l'integrazione è necessaria, l'ambiente di origine deve soddisfare il livello minimo per tale applicazione.

La tabella seguente illustra le previsioni nell'ambiente di origine esistente per l'onboarding.

|Attività|Previsione per l’ambiente di origine|
|------------|----------------------------------|
|Onboarding di base|Foreste di Active Directory con il livello di foresta funzionale impostato su Windows Server 2008 o versione successiva, con la configurazione di foresta seguente:<br /><br />-   Foresta singola di Active Directory<br />-   Più foreste di Active Directory </br></br>**Nota**: per tutte le configurazioni a più foreste, la distribuzione di Active Directory Federation Services (AD FS) esula dall'ambito di FastTrack Center Benefit.|
|Caricamento di Azure AD Premium|Il servizio Active Directory locale e il relativo ambiente sono stati preparati per Azure AD Premium. Quest'ultimo include la correzione dei problemi identificati che impediscono l'integrazione con le funzionalità di Azure AD e Azure AD Premium.|
|Caricamento di Intune, solo cloud o integrato con System Center Configuration Manager|Per la gestione di dispositivi con Configuration Manager 2012 R2 o versioni successive con connessione a Intune, gli amministratori IT dovranno seguire l'[Elenco di controllo amministratore: Configurazione di Configuration Manager per la gestione di dispositivi mobili mediante Microsoft Intune](https://technet.microsoft.com/library/jj943763.aspx).</br></br> **Nota**: il service benefit non include l'assistenza per la configurazione o l'aggiornamento di Configuration Manager in base ai requisiti minimi necessari per integrare Microsoft Intune con Configuration Manager.</br></br>Per la distribuzione di profili Wi-Fi e VPN, gli esperti IT hanno bisogno di un'Autorità di certificazione esistente e di infrastrutture Wi-Fi e VPN già funzionanti negli ambienti di produzione.</br></br> **Nota**: il servizio non include l'assistenza per l'installazione o la configurazione di infrastrutture dell'Autorità di certificazione, Wi-Fi o VPN. |

**Altre informazioni**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)



<!--HONumber=Nov16_HO4-->


