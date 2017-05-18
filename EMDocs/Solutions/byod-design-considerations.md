---
title: Considerazioni sulla progettazione
description: Questo articolo include una serie di considerazioni sulla progettazione per prodotti e tecnologie in uno scenario Bring Your Own Device (BYOD).
keywords: 
author: YuriDio
ms.author: yurid
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 639dfd46-33ea-4cfd-918d-f3d8e57645ed
ms.reviewer: 
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 5adb7f68efacdfa20d78c3cf5853fa374793140a
ms.openlocfilehash: 3dbf7072bbc3baf6a97072f1cbbd15bd236349d3
ms.contentlocale: it-it
ms.lasthandoff: 11/28/2016


---

# <a name="design-considerations"></a>Considerazioni sulla progettazione

Con un'analisi dei requisiti descritti in dettaglio nella sezione Progettazione della soluzione di infrastruttura BYOD di questo documento, è possibile selezionare i prodotti e le tecnologie appropriati per implementare i requisiti per il progetto di infrastruttura BYOD. La tabella seguente elenca i prodotti, le tecnologie e i servizi Microsoft che consentono di implementare una soluzione di infrastruttura BYOD.

I prodotti, le tecnologie e i servizi Microsoft per una soluzione di infrastruttura BYOD menzionati in questa guida sono:

## <a name="user-and-device"></a>Utenti e dispositivi

- Windows Server 2012 R2
- Windows 10
- Aggiunta all'area di lavoro
- Servizio registrazione dispositivi
- Registrazione del dispositivo
- Profilo Wi-Fi
- Portale aziendale
- Protocollo HTTPS

## <a name="data-access-and-protection"></a>Protezione e accesso ai dati

- Windows Server 2012 R2
- Servizi di dominio Active Directory (AD DS)
- Active Directory di Azure (Azure AD)
- Azure Multi-Factor Authentication (Azure MFA)
- Active Directory Federation Services (ADFS)
- Controllo dinamico degli accessi
- Servizio Microsoft Rights Management
- Azure Information Protection
- Crittografia SMB
- Single Sign-On (SSO)
- Cartelle di lavoro
- Proxy applicazione Web (WAP)

## <a name="management"></a>Management

- Microsoft Intune
- Criteri di gestione dispositivi
- Infrastruttura di gestione unificata
- Cancellazione selettiva
- Distribuzione del software
- Gestione e rapporti sull'utilizzo dei punti di distribuzione
- System Center 2012 R2 Configuration Manager

## <a name="apps"></a>App

- Proxy applicazione Web
- VPN ad attivazione automatica
- RemoteApp
- Rapporto utilizzo copie shadow di sessione
- Riconnessione rapida
- Archiviazione di deduplicazione
- Security Development Lifecycle (SDL)
- Active Directory Federations Services (AD FS)
- Protocollo HTTPS

Le sezioni seguenti delineano il processo di progettazione ma, come indicato nella sezione Progettazione della soluzione di infrastruttura BYOD di questo documento, il processo di progettazione e di definizione dei requisiti è iterativo finché non viene completato.
Il resto della documentazione prende in esame le considerazioni di progettazione e i prodotti, le tecnologie e i servizi elencati nella tabella precedente. Quando è possibile usare più prodotti, tecnologie e servizi Microsoft per affrontare le diverse considerazioni di progettazione, ne verranno illustrati i compromessi.

Il progetto di infrastruttura per il supporto di BYOD riunisce le risposte alle domande riportate in precedenza in questo articolo, nonché le funzionalità della tecnologia e le opzioni disponibili. Il progetto illustrato in questo documento usa una tecnologia basata su Microsoft. Le considerazioni e le opzioni di progettazione possono tuttavia essere applicate a qualsiasi infrastruttura usata per adottare il modello BYOD.

