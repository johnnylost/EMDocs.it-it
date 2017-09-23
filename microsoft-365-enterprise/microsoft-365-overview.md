---
title: Microsoft 365 Enterprise | Microsoft docs
description: Panoramica e descrizione dei servizi Microsoft 365 Enterprise.
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/15/2017
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 14f22a558e2e437f1491033eb33858b377eeca9d
ms.sourcegitcommit: d8588b191a4f9daea73698426dd632e7997140dc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2017
---
# <a name="microsoft-365-enterprise-overview"></a>Panoramica di Microsoft 365 Enterprise
Microsoft 365 Enterprise è progettato per le organizzazioni di grandi dimensioni e integra Office 365 Enterprise, Windows 10 Enterprise ed Enterprise Mobility + Security per offrire a tutti gli utenti le funzionalità fondamentali per esprimere la propria creatività e collaborare in tutta sicurezza. Microsoft Enterprise 365 include un'edizione enterprise delle applicazioni di Windows 10 e Office tramite Office 365 ProPlus.

Sia Windows 10 che Office 365 ProPlus offrono nuovi aggiornamenti delle funzionalità per le aziende rilasciati in marzo e settembre tramite il canale semestrale. Un rilascio di funzionalità del canale semestrale è supportato per 18 mesi. Sia Microsoft Intune che System Center Configuration Manager includono funzionalità per distribuire e aggiornare Windows 10 e Office 365 ProPlus.

Questa sezione offre una panoramica dei servizi EMS e Office 365 inclusi in Microsoft 365 Enterprise, oltre a un'introduzione ai concetti di base necessari per comprendere come usarli al meglio per le specifiche esigenze di ogni organizzazione. Le funzionalità offerte da questi servizi consentono agli amministratori aziendali del cloud Microsoft non solo di proteggere le identità e i dispositivi dei dipendenti della società, ma anche di controllare l'accesso ai dati aziendali, sia in transito che inattivi.

|Servizio|Descrizione|
|-------|-----------|
|[Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)|Azure AD offre una gamma completa di funzionalità per la gestione delle identità, tra cui autenticazione a più fattori, registrazione dei dispositivi, gestione delle password self-service, gestione dei gruppi self-service, controllo degli accessi in base al ruolo, monitoraggio dell'utilizzo delle applicazioni, controllo avanzato e monitoraggio e avvisi per la sicurezza.|
|[Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection)|Questo servizio consente di rilevare potenziali vulnerabilità che interessano le identità dell'organizzazione e di configurare risposte automatizzate tramite criteri di accesso condizionale per rischi di accesso e rischi utente di livello basso, medio e alto.|
|[Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)|Questo servizio consente alle organizzazioni di ridurre al minimo il numero di persone con accesso permanente a operazioni privilegiate. Azure AD Privileged Identity Management introduce il concetto di amministratore idoneo. Gli amministratori idonei devono essere utenti che necessitano dell'accesso con privilegi occasionalmente, ma non ogni giorno. Il ruolo è inattivo fino a quando l'utente deve accedere con questi requisiti, quindi occorre completare un processo di attivazione per diventare amministratore attivo per un periodo di tempo prestabilito.|
|[Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection)| Azure Information Protection è una soluzione basata sul cloud, inclusa nell'offerta EMS E5, che consente alle organizzazioni di classificare, etichettare e proteggere documenti e messaggi di posta elettronica. Queste operazioni possono essere eseguite automaticamente dagli amministratori, che definiscono regole e condizioni, manualmente dagli utenti oppure da entrambi, quando gli utenti ricevono raccomandazioni dagli amministratori. Le etichette di Azure Information Protection consentono di applicare la classificazione a documenti e messaggi di posta elettronica. In questo modo, la classificazione è identificabile in qualsiasi momento, indipendentemente dalla posizione di archiviazione dei dati o dagli utenti con cui è condivisa. <br><br>Le impostazioni dei criteri di Azure Information Protection sono protette da [Azure Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms). Analogamente alle etichette, la protezione applicata tramite Rights Management rimane associata ai documenti e ai messaggi di posta elettronica indipendentemente dalla posizione: all'interno o all'esterno dell'organizzazione, in reti, file server o applicazioni.|
|[Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/introduction-to-microsoft-intune)|Intune è un servizio di gestione della mobilità aziendale (EMM) basato su cloud che consente alla forza lavoro di essere produttiva, garantendo al tempo stesso la protezione dei dati aziendali. Intune è integrato con Azure AD per il controllo delle identità e degli accessi e viene usato per la gestione di dispositivi e applicazioni. Le funzionalità di [gestione dei dispositivi di Intune](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) vengono usate per configurare e proteggere i dispositivi dell'utente, inclusi i PC Windows. <br><br>Le funzionalità di gestione dei dispositivi di Intune supportano sia la registrazione [BYOD (Bring Your Own Device)](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod) che consente agli utenti di registrare telefoni, tablet o PC personali, sia la registrazione di [dispositivi di proprietà dell'azienda (COD, Corporate-Owned Device)](https://docs.microsoft.com/enterprise-mobility-security/solutions/issue-corp-devices) che rende possibili scenari di gestione come la registrazione automatica, i dispositivi condivisi o configurazioni con requisiti di registrazione pre-autorizzati. Per maggiore sicurezza, è anche possibile richiedere l'autenticazione a più fattori (MFA) per registrare un dispositivo. Dopo averli registrati nel sistema di gestione, Intune può configurare le funzionalità e le impostazioni dei dispositivi per abilitare l'accesso protetto alle risorse aziendali.|


Queste sono le versioni più aggiornate di Windows 10, Office 365 ProPlus, Microsoft Intune e System Center Configuration Manager:

|     |**Canale semestrale (mirato)**|**Canale semestrale**|
|:-----|:-----|:-----|
|**Windows 10**|Windows 10 Fall Creators Update (presto disponibile)|Versione 1703|
|**Office 365 ProPlus**|Versione 1708|Versione 1705|
|**Intune**|N/D|Versione 1708|
|**System Center Configuration Manager**|Technical Preview versione 1708|Versione1706<sup>*</sup>|

<sup>*</sup> L'aggiornamento 1706 per System Center Configuration Manager (Current Branch) è disponibile come aggiornamento nella console per siti installati in precedenza che eseguono la versione 1606, 1610 o 1702.

> [!NOTE]
> Anche i servizi di Microsoft Azure vengono aggiornati a intervalli regolari, ma non sono contraddistinti da un numero di versione. Per controllare gli aggiornamenti più recenti e quelli previsti per il futuro per i servizi di Azure, vedere la [Guida di orientamento a Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap).

Per altre informazioni sulle funzionalità disponibili in queste versioni, vedere gli articoli seguenti:
- [Novità in Windows 10](https://docs.microsoft.com/windows/whats-new/)
- [Informazioni sulla versione di Windows 10](https://technet.microsoft.com/windows/release-info)
- [Cronologia degli aggiornamenti per Windows 10](https://support.microsoft.com/help/4018124/windows-10-update-history)
- [Versioni canale aggiornamento client Office 365](https://technet.microsoft.com/office/mt465751)
- [Novità di Microsoft Intune](https://docs.microsoft.com/intune/whats-new)
- [What's new in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-incremental-versions) (Novità di System Center Configuration Manager)
- [Funzionalità di Technical Preview 1708 per System Center Configuration Manager](https://docs.microsoft.com/sccm/core/get-started/capabilities-in-technical-preview-1708)

## <a name="security-best-practices-and-recommendations"></a>Procedure consigliate e raccomandazioni per la sicurezza
Non esiste una sola procedura consigliata per tutti gli ambienti dei clienti, ma l'articolo [Configurazioni e criteri di sicurezza consigliati](microsoft-365-policies-configurations.md) presenta alcuni concetti su procedure consigliate che è importante comprendere. L'articolo descrive anche i consigli generali di Microsoft su come applicare i criteri e la configurazione nell'ambito del cloud di Microsoft per garantire la protezione e la produttività dei dipendenti.


## <a name="deploy-windows-10-and-office-365-proplus"></a>Distribuire Windows 10 e Office 365 ProPlus
Informazioni su come distribuire Windows 10 e Office 365 ProPlus con integrazione in Microsoft Azure Active Directory (Azure AD) o in Active Directory Domain Services in locale. Distribuire Windows 10, Office 365 ProPlus e le altre app line-of-business nei nuovi dispositivi o aggiornare i dispositivi esistenti a Windows 10 usando Intune, System Center Configuration Manager e Criteri di gruppo per gestire i dispositivi.

Per ulteriori informazioni, vedere gli articoli seguenti:
- [Considerazioni sulla distribuzione di Windows 10](https://docs.microsoft.com/windows/deployment/planning/windows-10-deployment-considerations)
- [Guida alla distribuzione di Office 365 ProPlus](https://support.office.com/article/f99f8cd0-e648-4834-8f45-f5637351899d)
- [Guida alle procedure consigliate per la distribuzione di Office 365 ProPlus nell'azienda](https://support.office.com/article/31a384ca-650c-4265-b76c-a87b414fd8b8)
- [Installare le app di Office 365 ProPlus nei dispositivi Windows 10 con Intune](https://docs.microsoft.com/intune/apps-add-office365)

Per assistenza per la distribuzione con Microsoft 365, [contattare FastTrack](https://fasttrack.microsoft.com/microsoft365).

## <a name="manage-updates-to-windows-10-and-office-365-proplus"></a>Gestire gli aggiornamenti per Windows 10 e Office 365 ProPlus
I collegamenti seguenti mostrano come ottenere il massimo controllo sugli aggiornamenti della qualità e delle funzionalità per Windows 10 e Office 365 ProPlus. Informazioni su come controllare in modo efficace l'utilizzo della larghezza di banda e mantenere aggiornati Windows e Office con le funzionalità, le caratteristiche e gli aggiornamenti della sicurezza più recenti.

Per ulteriori informazioni, vedere gli articoli seguenti:
- [Panoramica di Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-overview)
- [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://support.office.com/article/9ccf0f13-28ff-4975-9bd2-7e4ea2fefef4)
- [Gestire gli aggiornamenti software con Intune](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [Distribuire gli aggiornamenti di Windows 10 con System Center Configuration Manager](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager)<sup>*</sup>
- [Gestire Office 365 ProPlus con Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates)

<sup>*</sup> Microsoft invita le organizzazioni che attualmente usano Configuration Manager per la gestione degli aggiornamenti di Windows a continuare a farlo per i computer client Windows 10.

## <a name="next-steps"></a>Passaggi successivi
[Altre informazioni sui servizi Microsoft 365 Enterprise](services-overview.md)

[Pagina del prodotto Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)

[Guida di orientamento a Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap)

