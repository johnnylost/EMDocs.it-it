---
title: Requisiti per l'ambiente di origine
description: Requisiti dell'ambiente di origine per l'uso di FastTrack Center Benefit per EMS
keywords: ''
author: andredm7
ms.author: andredm
manager: ''
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: beee0fe5a4b0907b6584f22d9c2a9967f83e5161
ms.sourcegitcommit: ffa46a69834de317e99a58146492e06c6aa4901a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="source-environment-expectations"></a>Requisiti per l'ambiente di origine

Se si usa [FastTrack Center Benefit per Enterprise Mobility + Security (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) per preparare Microsoft Azure Active Directory Premium e Microsoft Intune per l'uso, è necessario che l'ambiente soddisfi i requisiti descritti nelle sezioni seguenti.

Se Active Directory locale è già presente nell'organizzazione, è possibile integrarlo con EMS o uno dei singoli servizi per sfruttare le funzionalità avanzate di gestione delle identità da una singola console. FastTrack Center Benefit per EMS offre assistenza per l'integrazione di Azure Active Directory con l'ambiente Active Directory locale.

La tabella seguente illustra le previsioni nell'ambiente di origine esistente per l'onboarding.

|Attività|Previsione per l’ambiente di origine|
|------------|----------------------------------|
|Onboarding di base|Foreste di Active Directory con il livello di foresta funzionale impostato su Windows Server 2008 o versione successiva, con la configurazione di foresta seguente:<br /><br />-   Foresta singola di Active Directory<br />-   Più foreste di Active Directory </br></br>**Nota**: per tutte le configurazioni a più foreste, la distribuzione di Active Directory Federation Services (AD FS) esula dall'ambito di FastTrack Center Benefit.|
|Caricamento di Azure AD Premium|Il servizio Active Directory locale e il relativo ambiente sono stati preparati per Azure AD Premium. Quest'ultimo include la correzione dei problemi identificati che impediscono l'integrazione con le funzionalità di Azure AD e Azure AD Premium.|
|Caricamento di Intune, solo cloud o integrato con System Center Configuration Manager|Per la gestione di dispositivi con Configuration Manager 2012 R2 o versioni successive con connessione a Intune, gli amministratori IT dovranno seguire l'[Elenco di controllo amministratore: Configurazione di Configuration Manager per la gestione di dispositivi mobili mediante Microsoft Intune](https://technet.microsoft.com/library/jj943763.aspx).</br></br> **Nota**: il service benefit non include l'assistenza per la configurazione o l'aggiornamento di Configuration Manager in base ai requisiti minimi necessari per integrare Microsoft Intune con Configuration Manager.</br></br>Per la distribuzione di profili Wi-Fi e VPN, gli esperti IT hanno bisogno di un'Autorità di certificazione esistente e di infrastrutture Wi-Fi e VPN già funzionanti negli ambienti di produzione.</br></br> **Nota**: il servizio non include l'assistenza per l'installazione o la configurazione di infrastrutture dell'Autorità di certificazione, Wi-Fi o VPN. |

> [!NOTE]
> **Per altre informazioni**
> [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility)

## <a name="next-steps"></a>Passaggi successivi

[Fasi di onboarding e migrazione di FastTrack Center Benefit per EMS](fasttrack-center-benefit-process-for-ems-phases.md)
