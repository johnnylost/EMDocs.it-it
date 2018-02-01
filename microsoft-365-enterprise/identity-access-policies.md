---
title: "Panoramica sui criteri relativi alle identità e all'accesso ai dispositivi - Microsoft 365 Enterprise | Microsoft Docs"
description: "Descrive i criteri per i consigli di Microsoft su come applicare i criteri e le configurazioni relativi all'identità e all'accesso ai dispositivi."
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 12/10/2017
ms.author: barlan
ms.reviewer: martincoetzer
ms.custom: it-pro
ms.openlocfilehash: 54b3308b334f60e47e78bdf4bc194495fe348814
ms.sourcegitcommit: 8d42bd1ec3d7bf5f873a7b681b0fea73a748b413
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="general-identity-and-device-access-policy-recommendations"></a>Consigli generali sull'identità e sui criteri di accesso ai dispositivi
Questo articolo descrive i criteri consigliati comuni per contribuire a proteggere Microsoft 365 Enterprise. Vengono anche presentate le configurazioni client della piattaforma predefinite consigliate per offrire un'esperienza SSO ottimale agli utenti, oltre ai prerequisiti tecnici per l'accesso condizionale.

In questa guida viene descritto come distribuire i criteri consigliati in un ambiente di cui è appena stato eseguito il provisioning. L'impostazione di questi criteri in un ambiente lab distinto consente di comprendere e valutare i criteri consigliati prima di eseguire l'implementazione degli ambienti di pre-produzione e di produzione. L'ambiente di cui è stato eseguito il provisioning può essere solo cloud o ibrido.  

Per distribuire correttamente i criteri consigliati, è necessario accedere al portale di Azure e soddisfare i prerequisiti specificati in precedenza. In particolare, è necessario:
* Configurare le reti denominate per garantire che Azure Identity Protection generi un punteggio di rischio correttamente
* Richiedere a tutti gli utenti di registrarsi per l'autenticazione a più fattori (MFA)
* Configurare la sincronizzazione degli hash delle password e la reimpostazione della password self-service per consentire agli utenti di reimpostare le password in modo autonomo

È possibile usare i criteri di Azure AD e di Intune per gruppi di utenti specifici. È consigliabile implementare i criteri definiti in precedenza a fasi. In questo modo è possibile convalidare le prestazioni dei criteri e i team di supporto che si occupano dei criteri in modo graduale.


## <a name="prerequisites"></a>Prerequisiti

Prima di implementare i criteri descritti nella parte restante di questo documento, l'organizzazione deve soddisfare alcuni prerequisiti:
* [Configurare la sincronizzazione degli hash delle password](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization). Questa funzionalità deve essere abilitata per rilevare credenziali perse e intervenire per l'accesso condizionale basato sui rischi. **Nota:** questo requisito è obbligatorio, indipendentemente dal fatto che l'organizzazione usi l'autenticazione gestita, come l'autenticazione pass-through, o l'autenticazione federata.
* [Configurare le reti denominate](https://docs.microsoft.com/azure/active-directory/active-directory-known-networks-azure-portal). Azure AD Identity Protection raccoglie e analizza tutti i dati di sessione disponibili per generare un punteggio di rischio. Si consiglia di specificare gli intervalli IP pubblici dell'organizzazione per la propria rete nella configurazione di reti denominate di Azure AD. Al traffico proveniente da questi intervalli viene assegnato un punteggio di rischio ridotto, di conseguenza il traffico proveniente dall'esterno rispetto all'ambiente aziendale viene valutato con un punteggio di rischio più elevato.
* [Registrare tutti gli utenti con l'autenticazione a più fattori (MFA)](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-manage-users-and-devices). Azure AD Identity Protection usa Azure MFA per eseguire una verifica della sicurezza aggiuntiva. È consigliabile richiedere a tutti gli utenti di registrarsi per tempo con l'autenticazione a più fattori di Azure.
* [Abilitare la registrazione automatica dei dispositivi dei computer Windows con dominio associato](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). L'accesso condizionale può garantire che il dispositivo che si collega al servizio sia un dispositivo con dominio associato o un dispositivo conforme. A tale scopo, nei computer Windows, il dispositivo deve essere registrato con Azure AD.  In questo articolo viene illustrato come configurare la registrazione automatica dei dispositivi.
* **Preparare il team di supporto**. Predisporre un piano per gli utenti che non riescono a portare a termine l'autenticazione a più fattori. Tale piano potrebbe prevedere la loro aggiunta a un gruppo di esclusione di criteri o la registrazione di nuove informazioni di autenticazione a più fattori a loro riguardo. Prima di apportare una di queste modifiche relative alla sicurezza, è necessario verificare che l'utente effettivo presenti la richiesta. Un passaggio efficace consiste nel richiedere ai responsabili degli utenti di offrire assistenza nel processo di approvazione.
* [Configurare il writeback delle password nell'AD locale](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started). Il writeback delle password consente ad Azure AD di richiedere che gli utenti modifichino le loro password locali quando è stato rilevato un rischio elevato di compromissione di account. È possibile abilitare questa funzionalità con Azure AD Connect in due modi. È possibile abilitare il writeback delle password nella schermata delle funzionalità opzionali della procedura guidata di Azure AD Connect oppure è possibile abilitarlo tramite Windows PowerShell.  
* [Abilitare l'autenticazione moderna](https://support.office.com/article/Enable-or-disable-modern-authentication-in-Exchange-Online-58018196-f918-49cd-8238-56f57f38d662) e [proteggere gli endpoint legacy](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-supported-apps).  L'accesso condizionale funziona con le applicazioni sia desktop che portatili che usano l'autenticazione moderna. Se l'applicazione usa protocolli di autenticazione legacy, potrebbe ottenere l'accesso nonostante l'applicazione delle condizioni. È importante sapere quali applicazioni possono usare le regole di accesso condizionale e i passaggi da eseguire per proteggere altri punti di ingresso dell'applicazione.
* [Abilitare Azure Information Protection](https://docs.microsoft.com/information-protection/get-started/infoprotect-tutorial-step1) attivando Rights Management. Usare Azure Information Protection con la posta elettronica per avviare la classificazione dei messaggi di posta elettronica. Seguire l'esercitazione di avvio rapido per personalizzare e pubblicare i criteri.  

### <a name="recommended-email-clients"></a>Client di posta elettronica consigliati
I seguenti client di posta elettronica supportano l'autenticazione moderna e l'accesso condizionale. Azure Information Protection non è ancora disponibile per tutti i client.

|Piattaforma|Client|Versione/Note|Azure Information Protection|
|:-------|:-----|:------------|:--------------------|
|**Windows**|Outlook|2016, 2013 [Abilitare l'autenticazione moderna](https://support.office.com/article/Enable-Modern-Authentication-for-Office-2013-on-Windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910), [aggiornamenti obbligatori](https://support.office.com/en-us/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|Sì|
|**iOS**|Outlook|[Ultima versione](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|No|
|**Android**|Outlook|[Ultima versione](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|No|
|**macOS**|Outlook|2016|No|
|**Linux**|Non supportato||No|

Per accedere ai documenti protetti di Azure Information Protection potrebbe essere necessario un software aggiuntivo. Assicurarsi di usare [software e formati di documenti supportati](https://docs.microsoft.com/information-protection/get-started/requirements-applications) per creare e visualizzare i documenti protetti con Azure Information Protection.


### <a name="recommended-client-platforms-when-securing-documents"></a>Piattaforme client consigliate per la protezione di documenti
I client seguenti sono consigliati nei casi in cui è stato applicato un criterio di protezione dei documenti.

|Piattaforma|Word/Excel/PowerPoint|OneNote|App OneDrive|App SharePoint|Client di sincronizzazione di OneDrive|
|:-------|:-----|:------------|:-------|:-------------|:-----|
|Windows 7|Supportato|Supportato|N/D|N/D|Anteprima<sup>*</sup>|
|Windows 8.1|Supportato|Supportato|N/D|N/D|Anteprima<sup>*</sup>|
|Windows 10|Supportato|Supportato|N/D|N/D|Anteprima<sup>*</sup>|
|Windows Phone 10|Non supportato|Non supportato|Supportato|Supportato|N/D|
|Android|Supportato|Supportato|Supportato|Supportato|N/D|
|iOS|Supportato|Supportato|Supportato|Supportato|N/D|
|macOS|Anteprima pubblica|Anteprima pubblica|N/D|N/D|Non supportato|
|Linux|Non supportato|Non supportato|Non supportato|Non supportato|Non supportato|

<sup>*</sup>Altre informazioni sull'[anteprima del client di sincronizzazione di OneDrive](https://support.office.com/article/Azure-Active-Directory-conditional-access-with-the-OneDrive-sync-client-on-Windows-028d73d7-4b86-4ee0-8fb7-9a209434b04e).

> [!NOTE]
> Questi consigli si basano su tre diversi livelli di sicurezza e protezione per la posta elettronica e possono essere applicati in base al livello di granularità necessario: **versione di base**, **sensibile**e **maggiore regolamentazione**. Per altre informazioni su questi livelli di sicurezza e sui sistemi operativi client consigliati a cui fanno riferimento questi consigli, vedere [Recommended security policies and configurations](microsoft-365-policies-configurations.md) (Criteri di sicurezza e configurazioni consigliati).


## <a name="baseline"></a>Versione di base
Questa sezione descrive i consigli per il livello di base dei dati, l'identità e la protezione dei dispositivi. Questi consigli dovrebbero soddisfare le esigenze di protezione di base di molte organizzazioni.

>[!NOTE]
>I criteri riportati di seguito sono additivi e si sviluppano in sequenza. Ogni sezione descrive unicamente le aggiunte applicate a ogni livello.
>

### <a name="conditional-access-policy-settings"></a>Impostazioni dei criteri di accesso condizionale

#### <a name="identity-protection"></a>Protezione dell'identità
È possibile assegnare agli utenti l'accesso Single Sign-On (SSO), come descritto nelle sezioni precedenti. È necessario intervenire solo in caso di necessità in base agli [eventi di rischio](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events).  

* Richiedere l'autenticazione a più fattori in base a un rischio di accesso **medio o più elevato**
* Richiedere la modifica della password di protezione per utenti con rischio **elevato**

>[!IMPORTANT]
>Per questo consiglio sui criteri sono necessarie la [sincronizzazione password](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization) e la [reimpostazione della password self-service](https://docs.microsoft.com/azure/active-directory/active-directory-passwords).
>

#### <a name="data-loss-prevention"></a>Prevenzione della perdita di dati
L'obiettivo per i criteri di gestione dei dispositivi e delle applicazioni è proteggere dalla perdita di dati in caso di perdita o furto di un dispositivo. Ciò può essere realizzato garantendo che l'accesso ai dati sia protetto da un PIN, che i dati siano crittografati nel dispositivo e che il dispositivo non sia danneggiato.

|Consiglio in relazione ai criteri|Descrizione|
|:--------------------|:----------|
|**Richiedere la gestione del PC utente**|Richiedere agli utenti di aggiungere i loro PC Windows a un dominio di Active Directory o di registrare i loro PC nella gestione con Microsoft Intune o System Center Configuration Manager.|
|**Applicare le impostazioni di sicurezza tramite oggetti Criteri di gruppo (GPO) o criteri di Configuration Manager per i computer aggiunti a un dominio**|Distribuire i criteri che configurano i computer gestiti in modo da abilitare BitLocker, l'anti-virus e il firewall.|
|**Richiedere la gestione dei dispositivi mobili**|Richiedere che i dispositivi utente usati per accedere alla posta elettronica siano gestiti da Intune **o** che l'accesso alla posta elettronica aziendale venga eseguito unicamente mediante applicazioni mobili di posta elettronica protette dai criteri di protezione app di Intune, come Outlook per iOS o Android.|
|**Applicare un criterio di conformità del dispositivo Intune ai dispositivi gestiti**|Applicare un criterio di conformità del dispositivo Intune per dispositivi mobili aziendali gestiti e computer gestiti da Intune che richieda: un PIN di lunghezza minima 6, la crittografia del dispositivo, l'integrità del dispositivo (che non sia jailbroken, rooted e sia munito di attestazione dell'integrità) e, se disponibile, che richieda dispositivi a **basso** rischio, secondo quanto stabilito da un MTP di terze parti come Lookout o SkyCure.|
|**Applicare un criterio di protezione app di Intune alle applicazioni gestite in esecuzione su dispositivi non gestiti**|Applicare un criterio di protezione App di Intune per le applicazioni gestite in esecuzione su dispositivi mobili personali non gestiti in modo da richiedere: un PIN con lunghezza minima 6, la crittografia del dispositivo e l'integrità del dispositivo (che non sia jailbroken, rooted e sia munito di attestazione dell'integrità).|

### <a name="user-impact"></a>Impatto sugli utenti

Per la maggior parte delle organizzazioni, è importante poter impostare le esigenze degli utenti in relazione a quando e per quali condizioni dovranno usare Office 365 per accedere alla posta elettronica.  

Gli utenti hanno generalmente un beneficio nell'accesso Single Sign-On (SSO), tranne nelle situazioni seguenti:
* Per la richiesta di token di autenticazione per Exchange Online:
  * Agli utenti potrebbe essere richiesto di eseguire l'autenticazione a più fattori ogni volta che viene rilevato un rischio di accesso **medio o più elevato** e che non hanno ancora eseguito l'autenticazione a più fattori nella sessione corrente.  
  * Agli utenti verrà richiesto di usare le applicazioni di posta elettronica che supportano l'SDK della protezione app di Intune o di accedere alla posta elettronica da dispositivi conformi a Intune o appartenenti a un dominio AD.
* Quando gli utenti a rischio eseguono l'accesso e completano correttamente l'autenticazione a più fattori, viene chiesto loro di cambiare la password.

## <a name="sensitive"></a>Dati sensibili
Questa sezione descrive i consigli per il livello di protezione avanzata dei dati, dell'identità e dei dispositivi. Questi consigli sono rivolti ai clienti che hanno un subset di dati che devono essere protetti a livelli più elevati o che richiedono che tutti i dati siano protetti a livelli più elevati.

È possibile applicare una protezione maggiore per tutti i set di dati o solo per alcuni di essi nell'ambiente Office 365. Ad esempio, è possibile applicare i criteri per garantire che i dati sensibili siano condivisi solo tra app protette per impedire la perdita di dati. Si consiglia di proteggere le identità e i dispositivi che accedono ai dati sensibili con livelli di sicurezza analoghi.

### <a name="conditional-access-policy-settings"></a>Impostazioni dei criteri di accesso condizionale
#### <a name="identity-protection"></a>Protezione dell'identità

È possibile assegnare agli utenti l'accesso Single Sign-On (SSO), come descritto nelle sezioni precedenti. È necessario intervenire solo in caso di necessità in base agli [eventi di rischio](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events).   

* Richiedere l'autenticazione a più fattori in sessioni di rischio **basso o più elevato**
* Richiedere la modifica della password di protezione per utenti con rischio elevato

>[!IMPORTANT]
>Per questo consiglio sui criteri sono necessarie la [sincronizzazione password](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization) e la [reimpostazione della password self-service](https://docs.microsoft.com/azure/active-directory/active-directory-passwords).
>

#### <a name="data-loss-prevention"></a>Prevenzione della perdita di dati

L'obiettivo per questi criteri di gestione dei dispositivi e delle applicazioni è proteggere dalla perdita di dati in caso di perdita o furto di un dispositivo. Ciò può essere realizzato garantendo che l'accesso ai dati sia protetto da un PIN, che i dati siano crittografati nel dispositivo e che il dispositivo non sia danneggiato.

|Consiglio in relazione ai criteri|Descrizione|
|:--------------------|:----------|
|**Richiedere la gestione del PC utente**|Richiedere agli utenti di aggiungere i loro computer a un dominio di Active Directory o di registrare i computer nella gestione con Intune o Configuration Manager e di assicurarsi che tali dispositivi siano conformi ai criteri prima di consentire l'accesso alla posta elettronica.|
|**Applicare le impostazioni di sicurezza tramite oggetti Criteri di gruppo (GPO) o criteri di Configuration Manager per i computer aggiunti a un dominio**|Distribuire i criteri che configurano i computer gestiti in modo da abilitare BitLocker, l'anti-virus e il firewall.|
|**Richiedere la gestione dei dispositivi mobili**|Richiedere che i dispositivi utente usati per accedere alla posta elettronica siano gestiti da Intune **o** che l'accesso alla posta elettronica aziendale venga eseguito unicamente mediante applicazioni mobili di posta elettronica protette dai criteri di protezione app di Intune, come Outlook per iOS o Android.|
|**Applicare un criterio di conformità del dispositivo Intune ai dispositivi gestiti**|Applicare un criterio di conformità del dispositivo Intune per dispositivi mobili aziendali gestiti e computer gestiti da Intune che richieda: un PIN di lunghezza minima 6, la crittografia del dispositivo, l'integrità del dispositivo (che non sia jailbroken, rooted e sia munito di attestazione dell'integrità) e, se disponibile, che richieda dispositivi a **basso** rischio, secondo quanto stabilito da un MTP di terze parti come Lookout o SkyCure.|
|**Applicare un criterio di protezione app di Intune alle applicazioni gestite in esecuzione su dispositivi non gestiti**|Applicare un criterio di protezione App di Intune per le applicazioni gestite in esecuzione su dispositivi mobili personali non gestiti in modo da richiedere: un PIN con lunghezza minima 6, la crittografia del dispositivo e l'integrità del dispositivo (che non sia jailbroken, rooted e sia munito di attestazione dell'integrità).|

### <a name="user-impact"></a>Impatto sugli utenti
Per la maggior parte delle organizzazioni è importante poter impostare le aspettative per gli utenti in relazione a quando e in quali condizioni dovranno accedere alla posta elettronica di Office 365.

Gli utenti traggono generalmente vantaggio dell'accesso Single Sign-On (SSO), tranne nelle situazioni seguenti:
* Per la richiesta di token di autenticazione per Exchange Online:
  * Agli utenti verrà richiesto di eseguire l'autenticazione a più fattori ogni volta che viene rilevato un rischio di accesso **basso o più elevato** e qualora non abbiano ancora eseguito l'autenticazione a più fattori nella sessione corrente.  
  * Agli utenti verrà richiesto di usare le applicazioni di posta elettronica che supportano l'SDK della protezione app di Intune o di accedere alla posta elettronica da dispositivi conformi a Intune o appartenenti a un dominio AD.
* Quando gli utenti a rischio eseguono l'accesso e completano correttamente l'autenticazione a più fattori, viene chiesto loro di cambiare la password.

## <a name="highly-regulated"></a>Riservatezza elevata
Questa sezione descrive i consigli per il livello di protezione altamente regolamentata dei dati, dell'identità e dei dispositivi. Questi consigli sono destinati ai clienti che potrebbero avere una piccola quantità di dati altamente classificati, segreti commerciali o dati soggetti a regolamentazione. Microsoft offre funzionalità che consentono alle organizzazioni di soddisfare questi requisiti, inclusa la protezione aggiuntiva per identità e dispositivi.

### <a name="conditional-access-policy-settings"></a>Impostazioni dei criteri di accesso condizionale
#### <a name="identity-protection"></a>Protezione dell'identità

Per il livello altamente regolamentato Microsoft consiglia di applicare l'autenticazione a più fattori a tutte le nuove sessioni.
* Richiedere l'autenticazione a più fattori per tutte le nuove sessioni
* Richiedere la modifica della password di protezione per utenti con rischio **elevato**

>[!IMPORTANT]
>Per questo consiglio sui criteri sono necessarie la [sincronizzazione password](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization) e la [reimpostazione della password self-service](https://docs.microsoft.com/azure/active-directory/active-directory-passwords).
>

#### <a name="data-loss-prevention"></a>Prevenzione della perdita di dati
L'obiettivo per questi criteri di gestione dei dispositivi e delle applicazioni è prevenire la perdita di dati in caso di perdita o furto di un dispositivo. Ciò viene realizzato garantendo che l'accesso ai dati sia protetto da un PIN, che i dati siano crittografati nel dispositivo e che il dispositivo non sia danneggiato.

Per il livello altamente regolamentato è consigliabile richiedere le applicazioni che supportano i criteri di protezione app di Intune in esecuzione solo su dispositivi conformi a Intune o aggiunti a un dominio.

|Consiglio in relazione ai criteri|Descrizione|
|:--------------------|:----------|
|**Richiedere la gestione del PC utente**|Richiedere agli utenti di aggiungere i loro computer Windows a un dominio di Active Directory **o** di registrare i computer nella gestione con Intune o Configuration Manager e di assicurarsi che tali dispositivi siano conformi ai criteri prima di consentire l'accesso alla posta elettronica.|
|**Applicare le impostazioni di sicurezza tramite oggetti Criteri di gruppo (GPO) o criteri di Configuration Manager per i computer aggiunti a un dominio**|Distribuire i criteri che configurano i computer gestiti in modo da abilitare BitLocker, l'anti-virus e il firewall.|
|**Richiedere la gestione dei dispositivi mobili**|Richiedere che i dispositivi usati per accedere alla posta elettronica di Office 365 siano gestiti da Intune o che l'accesso alla posta elettronica aziendale sia eseguito unicamente mediante applicazioni mobili di posta elettronica protette dai criteri di protezione app di Intune, come Outlook per iOS o Android.|
|**Applicare un criterio di conformità del dispositivo Intune ai dispositivi gestiti**|Applicare un criterio di conformità del dispositivo Intune per dispositivi mobili aziendali gestiti e computer gestiti da Intune che richieda: un PIN di lunghezza minima 6, la crittografia del dispositivo, l'integrità del dispositivo (che non sia jailbroken, rooted e sia munito di attestazione dell'integrità) e, se disponibile, che richieda dispositivi a basso rischio, secondo quanto stabilito da un MTP di terze parti come Lookout o SkyCure.|

### <a name="user-impact"></a>Impatto sugli utenti
Per la maggior parte delle organizzazioni è importante poter impostare le aspettative per gli utenti in relazione a quando e in quali condizioni dovranno accedere ai file di Office 365.

* Una volta scadute le sessioni, gli utenti per i quali è stata configurata la protezione per ambienti altamente regolamentati dovranno accedere nuovamente con l'autenticazione a più fattori.
* Quando gli utenti a rischio eseguono l'accesso, viene chiesto loro di cambiare la password, dopo aver completato l'autenticazione a più fattori.
* Per la richiesta di token di autenticazione per Exchange Online:
  * Gli utenti dovranno eseguire l'autenticazione a più fattori ogni volta che avviano una nuova sessione.  
  * Gli utenti dovranno usare le app di posta elettronica che supportano l'SDK di protezione app di Intune
  * Gli utenti dovranno accedere a messaggi di posta elettronica da dispositivi conformi a Intune o aggiunti a un dominio AD.

## <a name="next-steps"></a>Passaggi successivi

[Learn about policy recommendations for securing email](secure-email-recommended-policies.md) (Informazioni sui criteri consigliati per la protezione della posta elettronica)
