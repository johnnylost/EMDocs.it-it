---
title: "Opzioni di gestione della connettività di rete"
description: "Questo articolo include materiale sussidiario sulle opzioni di gestione della connettività della rete per la pianificazione e la progettazione di una soluzione di gestione di dispositivi mobili Microsoft tramite Enterprise Mobility + Security."
keywords: 
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc7cdb8f-3485-45ae-9493-f840ad9ed3ea
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7d9c38008b5b47ea41ff331f1de763de5c119c5e
ms.openlocfilehash: 856d2d2ba9968aa0f4a0da4f4afcbf452260e548


---

# <a name="network-connectivity-management-options"></a>Opzioni di gestione della connettività di rete

>[!NOTE]
>Questo argomento fa parte di una guida più ampia dedicata alle considerazioni di progettazione. Per leggere la guida dall'inizio, vedere l'[argomento principale](mdm-design-considerations-guide.md). Per scaricare una copia della versione integrale della guida, visitare la raccolta [TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

A seconda dell'infrastruttura, i dispositivi mobili potrebbero essere in grado di connettersi alle risorse aziendali da una varietà di servizi di connettività Internet, la cui sicurezza è spesso garantita da endpoint protetti tramite VPN.

Usando [Intune](/Intune/deploy-use/wi-fi-connections-in-microsoft-intune) o una [distribuzione ibrida](https://technet.microsoft.com/library/dn261221.aspx) con Configuration Manager, è possibile distribuire profili Wi-Fi per il provisioning di reti Wi-Fi, in modo che un dispositivo possa connettersi automaticamente alla rete quando si trova nel campo. Ad esempio, i dispositivi mobili possono essere configurati per connettersi a una rete Wi-Fi segmentata in una sala conferenze, ma connettersi a un altro segmento della rete Wi-Fi in caso di roaming in una posizione diversa. Gli utenti non devono immettere le password o scegliere una rete, la connessione avviene automaticamente.

[Intune](/Intune/deploy-use/vpn-connections-in-microsoft-intune) e [Configuration Manager](https://technet.microsoft.com/library/dn261217.aspx) sono anche in grado di distribuire profili VPN direttamente ai dispositivi mobili, per consentire agli utenti di accedere alle risorse aziendali interne senza ulteriori operazioni di configurazione o interventi manuali. Intune è anche in grado di configurare i dispositivi mobili per avviare automaticamente una connessione VPN in base al tipo di risorsa o al metodo di accesso. Tenere presente, tuttavia, che i requisiti di configurazione sono diversi per l'esecuzione di questa operazione per diversi tipi di sistemi operativi per dispositivi mobili.

Le risposte alle domande nell'attività 3 aiutano a decidere in che modo si desidera gestire i dispositivi da connettere alle risorse aziendali. Tenere presente che attualmente <token>MDM per Office 365</token> non supporta la gestione delle risorse di rete wireless e VPN per i dispositivi mobili.

Gli elenchi che seguono descrivono i vantaggi e gli svantaggi della gestione delle reti wireless e VPN usando Intune autonomo e Intune ibrido con Configuration Manager.

## <a name="intune-standalone"></a>Intune (autonomo)

**Vantaggi**

- Supporta i profili wireless e VPN per tutti i principali sistemi operativi per dispositivi mobili (Android, iOS, Windows 10, Windows 8.x e Windows Phone)
- Supporta i tipi di connessione VPN leader del settore, tra cui Cisco, Juniper, Dell SonicWall, Checkpoint e altri ancora
- I profili VPN e wireless possono essere integrati con i profili del certificato SCEP, per una maggiore sicurezza
- Supporta la configurazione di profili wireless e VPN personalizzati per diversi tipi di utenti, dispositivi, sistemi operativi dei dispositivi o gruppi e ruoli degli utenti
- Supporto per l'avvio DNS basato su nome per Windows 10, Windows 8.1, Windows Phone 8.1 e iOS
- Supporto per l'avvio dell'applicazione basato su ID per Windows 10 e Windows 8.1
- È possibile selezionare app che si connettono automaticamente alla rete aziendale con VPN nei profili VPN

**Svantaggi**

- Per supportare i profili VPN, è necessario distribuire e gestire un'infrastruttura VPN locale

## <a name="mdm-for-office-365"></a>Gestione dei dispositivi mobili per Office 365

Il supporto per i criteri per Wi-Fi e VPN non è previsto in MDM per Office 365.

## <a name="hybrid-intune-with-configmgr"></a>Ibrida (Intune con Configuration Manager)

**Vantaggi**

- Tutti i vantaggi di Intune autonomo, oltre alle funzionalità seguenti:
    - I profili VPN sono supportati dall'infrastruttura VPN aziendale locale esistente

**Svantaggi**

- Per supportare i profili VPN, è necessario distribuire e gestire un'infrastruttura VPN locale
- È necessario concedere autorizzazioni di sicurezza specifiche per gestire i [profili Wi-Fi](https://technet.microsoft.com/library/dn408646.aspx) e i [profili VPN](https://technet.microsoft.com/library/dn408643.aspx) in Configuration Manager

Esaminare i dettagli sulle opzioni di gestione della configurazione della posta elettronica per dispositivi mobili prendendo in considerazione gli elementi seguenti:

- Intune: abilitare i profili [wireless](/Intune/deploy-use/wi-fi-connections-in-microsoft-intune) e [VPN](/Intune/deploy-use/vpn-connections-in-microsoft-intune)
- Configuration Manager: abilitare i profili [wireless](https://technet.microsoft.com/library/dn261221.aspx) e [VPN](https://technet.microsoft.com/library/dn261217.aspx)



<!--HONumber=Nov16_HO4-->


