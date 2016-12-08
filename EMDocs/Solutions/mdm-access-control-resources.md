---
title: Controllo di accesso alle risorse
description: Questo articolo include una serie di considerazioni sulla progettazione per il controllo di accesso da usare in uno scenario di gestione di dispositivi mobili (MDM).
keywords: 
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 11/28/2016
ms.topic: solution
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 5967876b-3c08-4498-a0a6-0225b562d35f
ms.reviewer: 
ms.suite: ems
ms.custom: microsoft-intune
translationtype: Human Translation
ms.sourcegitcommit: 5adb7f68efacdfa20d78c3cf5853fa374793140a
ms.openlocfilehash: 782f6dac4a366312ce0a6d04735262908df6fe72


---

# <a name="access-control-to-resources"></a>Controllo di accesso alle risorse

>[!NOTE]
>Questo argomento fa parte di una guida più ampia dedicata alle considerazioni di progettazione. Per leggere la guida dall'inizio, vedere l'[argomento principale](mdm-design-considerations-guide.md). Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Le organizzazioni che usano Active Directory per autenticare e autorizzare gli utenti gestiscono già il controllo di accesso a risorse specifiche, usando i gruppi in Active Directory per segmentare e controllare l'accesso alle risorse.  

Per gestire il controllo di accesso a risorse specifiche, è necessario innanzitutto autenticare e autorizzare l'accesso per l'utente e quindi convalidare il tipo di controllo di cui l'utente dispone sulla risorsa di destinazione. La figura che segue illustra l'accesso a una cartella da parte dell'utente Bob.

![Flusso di autenticazione](./media/MDM_Figure_13.png)

## <a name="basic-authentication-and-authorization-flow"></a>Flusso di autenticazione e autorizzazione di base

L'elenco di controllo di accesso (ACL) tradizionale è molto limitato e non prende in considerazione altri aspetti dello stato dell'utente, ad esempio la relativa posizione durante il tentativo di accedere alla risorsa. Se è necessario che l'organizzazione includa altre variabili prima di consentire l'accesso a una risorsa, è possibile usare il [Controllo dinamico degli accessi](https://technet.microsoft.com/library/dn408191.aspx), disponibile in modo nativo in Windows Server 2012. Windows 10 supporta l'attestazione dell'integrità, che aiuta il reparto IT a verificare le condizioni del dispositivo prima di consentire l'accesso ai dati. Il servizio di attestazione dell'integrità esegue in modalità remota una serie di controlli sulle misurazioni. Convalida i punti dati relativi alla sicurezza, inclusi lo stato dell'avvio (avvio protetto, modalità di debug e così via) e lo stato dei componenti che gestiscono la sicurezza (BitLocker, Controllo dispositivo e così via). Comunica quindi lo stato di integrità inviando al dispositivo un BLOB crittografato sull'integrità. Per altre informazioni, vedere [Controllare l'integrità dei dispositivi basati su Windows 10](https://technet.microsoft.com/library/mt592023.aspx).

Gli amministratori di Intune ora possono visualizzare lo stato di attestazione dell'integrità dei dispositivi Windows 10 nella [console di amministrazione di Intune](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). L'attestazione dell'integrità dei dispositivi consente all'amministratore di assicurare che i computer client dispongano di configurazioni attendibili di BIOS, TPM e software di avvio. Per supportare l'attestazione dell'integrità dei dispositivi, i dispositivi client devono eseguire Windows 10 con TPM 2 abilitato. 

Poiché molte società agiscono da provider di cloud mediante tecnologie che consentono di disporre di un cloud privato, un'altra opzione consiste nell'uso del controllo di accesso basato sui ruoli. [AD Azure consente al reparto IT di usare RBAC](http://azure.microsoft.com/documentation/articles/role-based-access-control-configure/) per controllare l'accesso alle risorse. E poiché Azure AD può essere integrato con Active Directory a livello locale, è possibile usarli insieme per determinare in che modo gli utenti accedono alle risorse.

Una risorsa può anche essere un'app, pertanto per implementare il controllo di accesso alle risorse, la soluzione MDM deve anche essere in grado di controllare la modalità di installazione e accesso alle app. I [criteri di gestione delle applicazioni mobili in Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) consentono di modificare la funzionalità delle app distribuite per garantire che siano conformi ai criteri aziendali di conformità e sicurezza. 

Usare la tabella che segue come riferimento per la scelta dell'opzione MDM più adatta ai requisiti di controllo di accesso della propria azienda.

## <a name="intune-standalone"></a>Intune (autonomo)

**Vantaggi**

- Controllo di accesso (installazione e gestione) per le app
- Accesso condizionale con servizio di attestazione dell'integrità

**Svantaggi**

- La mancanza di integrazione con la piattaforma MDM locale corrente introdurrà un'interfaccia di gestione aggiuntiva
- Alcuni criteri potrebbero non essere disponibili per alcune piattaforme mobili
 
## <a name="mdm-for-office-365"></a>Gestione dei dispositivi mobili per Office 365

**Vantaggi**

- Controllo di accesso a posta elettronica, Office Mobile, app Office e OneDrive for Business

**Svantaggi**

- Consente solo un subset ridotto di controllo di accesso alle risorse
- La mancanza di integrazione con la piattaforma MDM locale corrente introdurrà un'interfaccia di gestione aggiuntiva
- Alcuni criteri potrebbero non essere disponibili per alcune piattaforme mobili

## <a name="hybrid-intune-with-configmgr"></a>Ibrida (Intune con Configuration Manager)

**Vantaggi**

- Controllo di accesso (installazione e gestione) per le app
- Accesso condizionale con servizio di attestazione dell'integrità

**Svantaggi**

- Il servizio cloud di Azure AD non è incluso quando si acquista la sottoscrizione di Intune

## <a name="enterprise-mobility-security"></a>Enterprise Mobility + Security

**Vantaggi**

- Controllo di accesso (installazione e gestione) per le app
- Sfrutta Azure AD Premium per consentire il controllo degli accessi in base al ruolo
- Accesso condizionale con servizio di attestazione dell'integrità

**Svantaggi**

- Se l'organizzazione attualmente non usa un'infrastruttura locale di Configuration Manager, è necessario pianificare, installare e configurare questa piattaforma prima dell'integrazione



<!--HONumber=Nov16_HO4-->


