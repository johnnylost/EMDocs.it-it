---
title: Iniziare a usare Enterprise Mobility + Security | Documentazione Microsoft
description: 
keywords: 
author: jeffgilb
manager: swadhwa
ms.date: 6/7/2017
ms.topic: solution
ms.prod: 
ms.service: active-directory
ms.technology: 
ms.assetid: 1df56825-c0d1-48ac-a294-5ebd1667bc38
ms.reviewer: mhamerof
ms.suite: ems
ms.custom: advanced-threat-analytics,cloud-app-security,information-protection,microsoft-identity-manager,microsoft-intune,rights-management
experimental: true
experiment_id: jeffgilb-length-20161110
ms.translationtype: Human Translation
ms.sourcegitcommit: ed952bd866758978ed4348c70da826eb519b4733
ms.openlocfilehash: 78b0119b52ca1459fd644d093bf7f364b80e8ce1
ms.contentlocale: it-it
ms.lasthandoff: 12/08/2016


---
# <a name="start-using-enterprise-mobility--security"></a>Iniziare a usare Enterprise Mobility + Security

Le organizzazioni con processi di trasformazione digitale in corso hanno l'esigenza di proteggersi da nuove minacce e affrontare nuove sfide. Allo stesso tempo, i reparti IT sono sottoposti a pressioni continue per promuovere soluzioni di miglioramento dell'efficienza. Nel mondo attuale, nel quale il cloud e i dispositivi mobili hanno un ruolo di primo piano, gli utenti si aspettano anche di poter essere produttivi ovunque e su qualsiasi dispositivo. Con EMS è possibile ottenere soluzioni olistiche che consentono di:

- **Controllare identità e accessi nel cloud**. Gestione centralizzata delle identità e accessi Single Sign-On sicuri a dispositivi, data center e cloud.
- **Implementare sistemi di sicurezza basata sull'identità**. Protezione completa e intelligente dagli attacchi avanzati di oggi.
- **Gestire dispositivi mobili e app per i dispositivi mobili**. Gestione sicura di app e dati in ambiente iOS, Android e Windows da un'unica posizione.
- **Proteggere le informazioni**. Salvaguardia intelligente dei dati aziendali e abilitazione di soluzioni per la collaborazione protetta.

Nelle prossime sezioni sono disponibili informazioni sulle potenzialità messe a disposizione da EMS ai reparti IT per offrire con sicurezza le soluzioni di produttività protette e senza limiti così tanto apprezzate dagli utenti. Questi scenari di esempio saranno utili come introduzione a EMS nella fase di transizione da sistemi locali al cloud, per sfruttare i servizi di sicurezza e protezione basati sul cloud e infine per offrire servizi completi IT dal cloud.

## <a name="transition-from-on-premises-to-the-cloud"></a>Transizione da sistemi locali al cloud
EMS include molti servizi e funzionalità che è possibile usare a seconda delle specifiche esigenze aziendali e man mano che si acquisisce familiarità con le potenzialità offerte.

### <a name="establish-azure-ad-identity"></a>Stabilire l'identità di Azure AD
Tutto parte dall'identità nel cloud, quindi per iniziare occorre stabilire la presenza in [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) per l'organizzazione. Tutte queste operazioni possono essere gestite completamente dal cloud oppure è possibile [sincronizzare gli oggetti di Windows Server Active Directory correnti con Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) per sfruttare gli investimenti esistenti nella gestione delle identità in locale.

### <a name="protect-your-organization-at-the-front-door"></a>Proteggere l'organizzazione dalla porta di ingresso
Le soluzioni di sicurezza tradizionali erano sufficienti per proteggere il proprio lavoro. Ma questo avveniva prima che il settore della mobilità crescesse aumentando le possibilità di attacco e il passaggio al cloud rendesse più complesse le interazioni dei dipendenti con altri utenti, dispositivi, app e dati. Al giorno d'oggi, per proteggere il proprio lavoro è necessario un [approccio alla sicurezza più olistico e innovativo](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-front-door) in grado di proteggere, individuare e reagire a minacce di tutti i tipi in locale e nel cloud.

### <a name="start-managing-devices"></a>Iniziare a gestire i dispositivi
Garantire la protezione dei dati aziendali con costi amministrativi ridotti, gestendo al tempo stesso la complessità dei dispositivi usati nell'organizzazione, può essere complicato con un approccio IT tradizionale. Con EMS è facile supportare molti scenari di gestione dei dispositivi diversi, che vanno da quelli di proprietà dell'azienda (CYOD, Choose Your Own Device) a quelli personali (BYOD, Bring Your Own Device) usati per il lavoro.

- **Assegnare dispositivi di proprietà dell'azienda**. Intune offre soluzioni per il provisioning e la gestione in blocco per facilitare l'[assegnazione dei dispositivi di proprietà aziendali](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices) nell'organizzazione, integrate con le principali piattaforme di gestione dei dispositivi aziendali presenti sul mercato, come il programma di registrazione dispositivi di Apple (DEP, Device Entollment Program) e la piattaforma di sicurezza per dispositivi mobili Samsung KNOX.
- **Abilitare una soluzione con dispositivi condivisi con limitazioni d'uso**. I task worker usano sempre più le tecnologie mobili. Sia che vengano usati per l'elaborazione di una vendita o un controllo rapido dell'inventario, i tablet autorizzati a usare una singola app line-of-business vengono in genere forniti ai dipendenti con limitazioni d'uso. Intune consente di eseguire il provisioning in blocco e di proteggere e gestire centralmente i tablet iOS e Android condivisi, che possono essere configurati per il funzionamento con queste limitazioni d'uso.
- **Abilitare un programma BYOD nell'organizzazione**. L'approccio BYOD è sempre più popolare tra le organizzazioni come mezzo per ridurre le spese di hardware o aumentare la produttività dei dispositivi mobili dei dipendenti. Man mano che le aziende decidono di discostarsi dal modello tradizionale basato sull'uso dei dispositivi di proprietà dell'azienda, devono [decidere come implementare un programma BYOD](https://docs.microsoft.com/enterprise-mobility-security/solutions/byod-design-considerations-guide) per consentire ai dipendenti di usare i dispositivi personali per alcune delle attività lavorative.
- **Allineare la strategia di distribuzione e gestione di Windows 10 alle esigenze dell'azienda, degli utenti finali e del reparto IT**. Windows 10 offre nuove funzionalità, scenari e strumenti di distribuzione basati sulle tecnologie introdotte in Windows 7 e Windows 8.1, ma introduce allo stesso tempo i nuovi concetti di Windows as a Service per mantenere aggiornato il sistema operativo. Nel loro insieme, questi cambiamenti rendono necessaria una [ridefinizione del processo di distribuzione tradizionale](https://technet.microsoft.com/itpro/windows/plan/windows-10-deployment-considerations). Dopo aver distribuito Windows 10, è necessario anche [stabilire le modalità ottimali per gestire i PC Windows 10](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices) con Intune per soddisfare le esigenze aziendali e di produttività degli utenti finali. Sono disponibili due opzioni: registrare i PC Windows 10 come dispositivi mobili oppure installare il client del software Intune per gestire il dispositivo come un computer.

### <a name="manage-and-protect-company-data"></a>Gestire e proteggere i dati aziendali
La maggior parte degli information worker oggi usa dispositivi mobili, quindi la produttività sui dispositivi mobili è essenziale per essere competitivi. Questi dipendenti hanno l'esigenza di accedere con facilità a tutti i dati e le app aziendali in qualsiasi momento e ovunque ed EMS offre soluzioni semplici, sia in locale che nel cloud.
- **Proteggere i dati aziendali locali**. La maggior parte delle strategie di mobilità aziendale inizia con un piano per abilitare l'accesso sicuro alla posta elettronica per i dipendenti con i dispositivi mobili da Internet, ma è anche necessario essere in grado di [accedere in modo sicuro ai dati aziendali in locale](https://docs.microsoft.com/enterprise-mobility-security/solutions/conditional-access-intune-exchange) tramite i dispositivi mobili. Ad esempio, molte organizzazioni usano ancora server dati e applicazioni locali, come Microsoft Exchange, ospitati nella propria rete aziendale.
- **Proteggere i dati aziendali di Office 365**. [Proteggere i dati aziendali in Office 365 (posta elettronica, documenti, messaggi istantanei e così via)](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-office365-data-with-intune) non potrebbe essere più semplice né più trasparente per gli utenti. Office 365 e EMS offrono un'esclusiva soluzione di accesso condizionale integrata che garantisce che nessun utente, app o dispositivo possa accedere ai dati di Office 365 a meno che non soddisfi i requisiti di conformità dell'azienda (esecuzione dell'autenticazione a più fattori, registrazione in Intune, uso dell'app gestita, versione del sistema operativo supportata, PIN del dispositivo, basso profilo di rischio dell'utente e così via).
- **Proteggere l'accesso a Office 365 e proteggere i dati nei dispositivi non gestiti**. Una pratica di distribuzione di Office 365 comune consiste nel richiedere la registrazione dei dispositivi in una soluzione di gestione, ma non sempre è necessario. Se un utente deve semplicemente accedere alla posta elettronica e ai documenti aziendali, come spesso accade per i dispositivi personali, è possibile usare semplicemente le app di Office per dispositivi mobili, [dopo aver applicato criteri di restrizione](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) ed evitare del tutto la registrazione del dispositivo.

## <a name="leverage-cloud-security-and-protection"></a>Sfruttare i servizi di sicurezza e protezione del cloud
EMS offre una soluzione di sicurezza basata su identità che rende disponibile un approccio olistico ai problemi di sicurezza del mondo di oggi caratterizzato dal ruolo predominante di dispositivi mobili e cloud. Con EMS non è solo possibile proteggere i dati dell'organizzazione condivisi, ma anche identificare le violazioni della protezione prima che possano causare danni.

### <a name="securely-share-data"></a>Condividere i dati in modo sicuro
Al giorno d'oggi la condivisione delle informazioni viene eseguita da più dispositivi e all'esterno della società. Le aziende devono trovare il modo per distinguere i dati che devono essere protetti da quelli che non richiedono protezione. Per affrontare questa sfida, è possibile [classificare, etichettare e proteggere i dati sensibili](https://docs.microsoft.com/enterprise-mobility-security/solutions/infoprotect-secure-classify-scenario) con [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) per garantire che i dati aziendali critici non vengano compromessi consentendo allo stesso tempo agli utenti di condividere in modo sicuro le informazioni importanti per svolgere il loro lavoro.

### <a name="identify-and-protect-against-threats"></a>Identificare le minacce e attivare misure di protezione
<!-- Detect advanced threats on-premises and in the cloud (ATA, Azure AD, Cloud App Security) -->
Un numero sempre maggiore di organizzazioni sceglie un approccio basato sul presupposto che nessuno è al sicuro da violazioni della protezione e in questo scenario EMS è di grande aiuto per identificare gli attacchi grazie a strumenti di analisi comportamentale e tecnologie di rilevamento delle anomalie innovativi, in locale con [Microsoft Advanced Threat Analytics](http://www.microsoft.com/ata) e nel cloud con [Azure Active Directory](http://www.microsoft.com/identity) e [Cloud App Security](http://www.microsoft.com/cloudappsecurity). L'Intelligence per le minacce di Microsoft è supportata dal grafico della sicurezza intelligente di Microsoft basato su set di dati molto estesi e meccanismi di Machine Learning nel cloud.

## <a name="full-service-it-from-the-cloud"></a>Servizi IT completi dal cloud
Con il progressivo completamento della trasformazione digitale delle organizzazioni, la disponibilità di servizi IT completi dal cloud diventerà una consuetudine. Le aziende con implementazioni di cloud mature cercheranno di sfruttare al massimo le opportunità offerte da EMS per concretizzare scenari di protezione delle identità e dei dati completi e a lungo termine.

### <a name="identity-management-from-hire-to-retire"></a>Gestione delle identità per tutte le fasi del rapporto di lavoro con i dipendenti
Microsoft è impegnata nella protezione delle identità basate sul cloud da oltre un decennio e con Azure Active Directory sta rendendo questi stessi sistemi di protezione disponibili ai clienti aziendali, per garantire i processi di accountability di utenti e amministratori attraverso livelli migliori di sicurezza e governance.
- **Migliaia di app, una sola identità**. Azure AD è una soluzione cloud di gestione delle identità e degli accessi che consente alle organizzazioni di accedere a tutto il necessario da qualsiasi posizione. Azure Active Directory (Azure AD) rende gli utenti più produttivi [fornendo un'identità comune per gli utenti di applicazioni SaaS (Software as a Service) che accedono a risorse sia cloud che locali](https://docs.microsoft.com/enterprise-mobility-security/solutions/thousands-apps-one-identity).
- **Attività aziendali senza confini**. Le organizzazioni devono [consentire ai propri dipendenti di accedere a tutti i dati e a tutte le applicazioni da ogni dispositivo e da qualunque luogo](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-business-without-borders). Gli utenti devono poter collaborare tra loro e con i partner e comunicare con i clienti.
- **Gestire l'accesso su larga scala**. Azure AD offre un set di strumenti per automatizzare la [gestione avanzata del ciclo di vita dell'utente](https://docs.microsoft.com/enterprise-mobility-security/solutions/manage-access-at-scale) tramite regole di appartenenza ai gruppi dinamiche e funzionalità di gestione delle applicazioni.
- **Protezione basata sul cloud**. Azure AD Identity Protection è un servizio di sicurezza che offre una [visualizzazione consolidata degli eventi di rischio e delle potenziali vulnerabilità](https://docs.microsoft.com/enterprise-mobility-security/solutions/cloud-powered-protection) che possono colpire le identità dell'organizzazione.

### <a name="protect-shared-files-and-saas-apps-with-policies-and-tracking"></a>Proteggere i file condivisi e le app SaaS con criteri e rilevamento
EMS integra perfettamente funzionalità avanzate di protezione dei dati aziendali nei processi aziendali per rendere più semplice tutelare le informazioni della società da perdite di dati sia intenzionali che accidentali.
- **Condividere i dati sensibili internamente ed esternamente**. Anche se molte violazioni dei dati sono dovute agli attacchi informatici, gli esperti concordano sul fatto che molte altre sono il risultato di errori umani o di momenti di distrazione che si verificano quando i dipendenti divulgano inavvertitamente dati aziendali sensibili. [Applicando i protocolli appropriati per la prevenzione della perdita dei dati e le informazioni di sicurezza](https://docs.microsoft.com/enterprise-mobility-security/solutions/share-sensitive-data) è possibile impedire quasi tutti questi tipi di violazioni.
- **Tenere traccia dell'utilizzo dei dati condivisi e rispondere in caso di uso improprio dei dati**. [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) è una soluzione basata sul cloud che consente alle organizzazioni di classificare, etichettare e proteggere documenti e messaggi di posta elettronica. Queste operazioni possono essere eseguite automaticamente dagli amministratori, che definiscono regole e condizioni, manualmente dagli utenti oppure da entrambi, quando gli utenti ricevono raccomandazioni dagli amministratori.
- **Gestire i dati in modo personalizzato con opzioni flessibili per la distribuzione e la gestione delle chiavi**. Anziché affidare a Microsoft la gestione della chiave del tenant (impostazione predefinita), per rispettare specifici criteri dell'organizzazione può essere necessario [gestire autonomamente la propria chiave del tenant di Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/plan-design/plan-implement-tenant-key). in base alla modalità BYOK (Bring Your Own Key).
- **Approvare e gestire applicazioni SaaS per i dipendenti**. Usare [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) per approvare/annullare l'approvazione delle applicazioni, applicare misure di prevenzione della perdita dei dati (DLP) e controllare le autorizzazioni e la condivisione, oltre che per generare report e avvisi personalizzati.
- **Proteggere i dati da errori degli utenti**. Microsoft offre un'ampia visibilità sulle attività degli utenti e relative ai dati, quindi è possibile [proteggere l'azienda quando gli utenti effettuano scelte non appropriate](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake) mentre lavorano su dati aziendali critici. Microsoft Cloud App Security fornisce visibilità e controlli per le app cloud, incluso Office 365. Azure Information Protection riunisce funzionalità di classificazione ed assegnazione delle etichette a strumenti per la protezione dei dati persistenti per supportare la condivisione di file sicura, sia internamente che esternamente.


### <a name="learn-more"></a>Altre informazioni

[Visitare la pagina dedicata a Microsoft Enterprise Mobility + Security](http://go.microsoft.com/fwlink/?LinkId=816837)

[Informazioni su Enterprise Mobility + Security](learn-about-ems.md)

[Provare gratuitamente EMS](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-security-trial)

