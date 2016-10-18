---
title: "Scenari di produttività dei dispositivi mobili gestiti"
description: L'approccio moderno di Microsoft in ambito EMM assicura una gestione eccellente delle app di Office 365 e consente agli utenti di lavorare al meglio su qualsiasi dispositivo, senza compromettere la sicurezza dei dati aziendali.
keywords: 
author: jeffgilb
manager: swadhwa
ms.date: 09/16/2016
ms.topic: article
ms.prod: 
ms.service: ems
ms.technology: 
ms.assetid: 452d7991-fa90-4100-afc4-47c4e7b18949
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e90ab882127f59e73eb739f073b96d80f4c0e429
ms.openlocfilehash: 72bed249099bd40a15e06d0ef7250ac87364cf1b


---

# Scenari di produttività dei dispositivi mobili gestiti con EMS
Microsoft Enterprise Mobility + Security adotta un moderno approccio alla gestione della mobilità e assicura una gestione eccellente delle app di Office 365 per dispositivi mobili per aiutare gli utenti a lavorare al meglio su qualsiasi dispositivo, senza compromettere la sicurezza dei dati aziendali. Prima di procedere con le attività di implementazione, comunque, è necessario avere ben chiare le finalità. Per avviare l'implementazione di EMS per gli scenari di produttività su dispositivi mobili, occorre che siano stati definiti alcuni obiettivi aziendali precisi e conoscere i servizi e le funzionalità di EMS che consentono di raggiungerli. Questo è importante sia quando la mobilità aziendale rappresenta una novità, sia quando si esegue la migrazione da un altro prodotto.

Il modo migliore per allineare le attività di implementazione di EMS agli obiettivi aziendali è esprimere ciò che si vuole ottenere attraverso scenari da implementare per dipendenti, partner e personale IT.  Di seguito sono descritti brevemente gli scenari più comuni per la produttività con dispositivi mobili gestiti. Gli scenari sono basati su Intune e per ognuno di essi sono forniti collegamenti ad altre informazioni sull'effettiva implementazione.

>[!NOTE]
>Si vuole sapere come Microsoft IT usa Intune per consentire ai dipendenti Microsoft di accedere alle risorse aziendali sui propri dispositivi mobili proteggendo allo stesso tempo i dati della società? [Leggere questo case study tecnico](https://www.microsoft.com/itshowcase/Article/Content/588) per vedere in dettaglio in che modo Microsoft IT usa Intune e altri servizi per gestire identità, dispositivi, applicazioni e dati.

## Proteggere l'accesso e i dati aziendali in Office 365 su dispositivi gestiti con Microsoft Intune
Proteggere i dati aziendali archiviati in Office 365 (posta elettronica, documenti, messaggi immediati e così via) con Intune è estremamente semplice per gli amministratori e trasparente per gli utenti. Intune offre un'esclusiva soluzione di accesso condizionale integrata che garantisce che nessun utente possa accedere ai dati di Office 365 a meno che non soddisfi i requisiti di conformità dell'azienda (esecuzione dell'autenticazione a più fattori, registrazione del dispositivo con Intune, uso di app gestite, versione del sistema operativo supportata, PIN del dispositivo e così via). Le app di Office 365 per dispositivi mobili disponibili negli app store corrispondenti sono dotate di funzionalità di contenimento dei dati appositamente progettate per essere configurate da Intune. Queste funzionalità consentono di impedire la condivisione dei dati con app (ad esempio le app di posta elettronica) e posizioni di archiviazione (ad esempio Dropbox) che non sono gestite dal reparto IT. Tutte queste funzionalità sono integrate direttamente in Office 365, per cui non è necessario distribuire o gestire un'infrastruttura aggiuntiva per usufruire di questi vantaggi.

Per altre informazioni, vedere [Secure access and protect Office 365 company data with Intune](https://docs.microsoft.com/intune/understand/secure-office365-data-with-intune) (Proteggere l'accesso e i dati aziendali in Office 365 con Intune).


## Proteggere l'accesso e i dati aziendali in locale con Intune
La maggior parte delle strategie di mobilità aziendale inizia con un piano che consenta ai dipendenti di accedere in modo sicuro alla posta elettronica aziendale e ai dati locali archiviati in server applicazioni, come Microsoft Exchange, ospitati nella rete aziendale. Intune offre un'esclusiva soluzione di accesso condizionale integrata per Exchange Server che assicura che nessuna app per dispositivi mobili possa accedere alla posta elettronica finché il dispositivo non viene registrato con Intune e non è conforme ai criteri aziendali. Tutto questo senza la necessità di implementare un altro computer gateway al perimetro della rete aziendale.

Oltre alla posta elettronica, Intune supporta l'abilitazione dell'accesso alle app per dispositivi mobili che richiedono l'accesso protetto ai dati locali, ad esempio un server app line-of-business. Questa operazione viene in genere eseguita usando certificati gestiti da Intune per il controllo di accesso combinato con un gateway VPN standard o un proxy nel perimetro, ad esempio il Proxy di applicazione di Microsoft Azure AD. In questi casi, l'unico modo per accedere ai dati aziendali è registrare il dispositivo nel sistema di gestione. Eseguita la registrazione, Intune garantisce che i dispositivi che accedono ai dati aziendali siano conformi ai criteri specificati.  In Intune sono anche disponibili lo strumento di wrapping delle app e App SDK che consentono di contenere i dati a cui si accede all'interno dell'app line-of-business, in modo non sia possibile passare dati aziendali ad app o servizi consumer non gestiti.

<!-- Learn more -->


## Proteggere l'accesso e i dati aziendali in Office 365 su dispositivi non gestiti con Intune
Una procedura comune per la distribuzione di Office 365 consiste nell'obbligo di registrare i dispositivi nel sistema di gestione se richiedono il provisioning completo con configurazioni aziendali per app/certificati/Wi-Fi/VPN, come spesso accade per i dispositivi di proprietà dell'azienda. Se però l'utente ha solo l'esigenza di accedere alla posta elettronica e ai documenti aziendali, come spesso accade per i dispositivi personali, potrà semplicemente usare le app di Office 365 per dispositivi mobili senza registrare il dispositivo. In questo caso, è possibile usare Intune per consentire a dipendenti, fornitori e partner di accedere in modo facile e sicuro ai dati aziendali dai propri dispositivi non gestiti.

I criteri di restrizione dei dati di Intune per i dispositivi non gestiti consentono di mantenere il controllo sugli utenti e sulle app che possono accedere ai dati di Office 365 con potenti funzionalità di prevenzione della perdita dei dati, anche se il dispositivo è già gestito da una soluzione MDM non Microsoft. È infatti possibile continuare a usare la soluzione che si preferisce, aggiungendo comunque le funzionalità avanzate messe a disposizione da Intune per il controllo dell'accesso e la prevenzione della perdita dei dati nelle app di Office 365 per dispositivi mobili. In ogni caso, proteggendo i dati aziendali senza eseguire la registrazione si otterrà un risparmio sui costi, senza necessità di gestire server, e si incrementerà la percentuale di utenti conformi ai criteri aziendali senza l'intervento del reparto IT per la gestione dei loro dispositivi personali.

<!-- Learn more -->


## Abilitare un programma BYOD nell'organizzazione
L'approccio BYOD è sempre più popolare tra le organizzazioni come mezzo per ridurre i costi riferiti all'hardware e aumentare le opzioni di produttività su dispositivi mobili per i dipendenti. Oggi quasi tutti gli utenti hanno uno smartphone personale, quindi perché dovrebbero averne un altro? Il problema principale è da sempre convincere i dipendenti a registrare i dispositivi personali nel sistema di gestione, perché temono ciò che il reparto IT sarà in grado di vedere e fare nei loro dispositivi. Quando la registrazione del dispositivo non è fattibile, Intune offre un approccio BYOD alternativo che consiste nel limitare la gestione alle app che contengono dati aziendali. Intune protegge i dati aziendali anche se l'app in questione accede sia ai dati aziendali che ai dati personali, come avviene per le app Office per dispositivi mobili.  In qualità di amministratore, l'utente può richiedere agli utenti di accedere a Office 365 dalle app Office per dispositivi mobili e di configurare le app con i criteri che assicurano la protezione dei dati (crittografia, protezione con pin e così via).

<!-- Learn more -->


## Gestire i dispositivi di proprietà dell'azienda con Intune
La maggior parte degli information worker oggi opera fuori sede e ha bisogno di usare dispositivi mobili di proprietà dell'azienda in modo produttivo. Questi dipendenti devono poter accedere facilmente alle app e ai dati aziendali in qualsiasi momento, ovunque si trovino, mentre l'azienda deve assicurarsi che i dati siano protetti e che i costi amministrativi siano contenuti.

Per il reparto IT, affrontare la situazione tentando di registrare manualmente molti dispositivi mobili di proprietà dell'azienda, uno alla volta, può essere un compito difficile. Per risolvere questo problema, Intune offre soluzioni per il provisioning e la gestione in blocco integrate con le principali piattaforme di gestione dei dispositivi aziendali presenti sul mercato, come il programma di registrazione dispositivi di Apple e la piattaforma di sicurezza mobile Samsung KNOX.  La creazione centralizzata delle configurazioni dei dispositivi con Intune trasforma il provisioning dei dispositivi aziendali in un processo estremamente automatizzato che permette di risparmiare molto tempo.

Con Intune è infatti possibile fornire a un dipendente un nuovo dispositivo mobile aziendale che, all'accensione, presenta una procedura di configurazione guidata personalizzata per l'azienda che consente di configurare facilmente il dispositivo con criteri di sicurezza per proteggere le risorse aziendali (crittografia del disco rigido, PIN del dispositivo e così via), criteri di configurazione per la produttività (profili di posta elettronica/Wi-Fi/VPN/certificato) e un set di app di base. In seguito, il dipendente potrà usare l'app Portale aziendale di Intune per accedere alle app aziendali facoltative a sua disposizione. E soprattutto, tutto questo può avvenire senza alcun intervento dopo la consegna del dispositivo.

<!-- Learn more -->

## Allineare una strategia di distribuzione e gestione di Windows 10 con EMS alle esigenze aziendali
Grazie a processi sia moderni che tradizionali per il ciclo di vita della gestione, EMS offre la flessibilità di scegliere come meglio distribuire e gestire Windows 10 nell'organizzazione. È possibile continuare a usare System Center Configuration Manager per distribuire e gestire i dispositivi Windows 10 con controlli avanzati basati su criteri oppure gestirli dal cloud solo con Intune per una gestione moderna dei dispositivi. In effetti è possibile anche usarli entrambi con una soluzione MDM ibrida, in cui alcuni dispositivi usano la gestione basata su agente con Configuration Manager e altri sono gestiti da Intune tramite OMA-DM e MDM.

<!-- Learn more -->


## Abilitare una soluzione con dispositivi condivisi con limitazioni d'uso con Intune
Talvolta i dipendenti devono usare dispositivi, app o browser che non è possibile gestire, ad esempio i computer pubblici disponibili presso le fiere e gli hotel. In questi casi è opportuno consentire ai dipendenti di accedere alla posta elettronica aziendale? Anche i task worker usano sempre più le tecnologie mobili. Ad esempio, oggi è normale vedere gli addetti alla vendita di un negozio che usano tablet condivisi. La protezione dei dati aziendali e la semplicità dell'esperienza utente in questi casi sono essenziali. Per questo motivo, i tablet usati dai dipendenti in genere presentano delle limitazioni d'uso, ad esempio il dipendente può interagire solo con una singola app line-of-business. Intune consente di eseguire il provisioning in blocco e di proteggere e gestire centralmente questi tablet iOS e Android condivisi o di chiosco multimediale configurandoli per l'esecuzione con specifiche limitazioni d'uso.

<!-- Learn more -->

### Altre informazioni



<!--HONumber=Oct16_HO1-->


