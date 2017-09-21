---
title: Criteri di sicurezza consigliati per posta elettronica -Microsoft 365 Enterprise | Microsoft Docs
description: Descrive i criteri consigliati da Microsoft sull'applicazione di criteri e configurazioni che riguardano la posta elettronica.
author: jeffgilb
manager: femila
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/30/2017
ms.author: jeffgilb
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: a9155d50516e2597e319beea26884fafad0b2e0f
ms.sourcegitcommit: 0e0a15476e3bbd2d4ac6101c2cedd02e082ee25d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2017
---
# <a name="policy-recommendations-for-securing-email"></a>Criteri consigliati per la protezione della posta elettronica
 
In questo articolo vengono descritti i criteri di sicurezza per la posta elettronica dell'organizzazione e i client di posta elettronica che supportano l'autenticazione moderna e l'accesso condizionale. Queste indicazioni si aggiungono a quelle contenute in [Common identity and access policy recommendations](identity-access-policies.md) (Consigli sui criteri comuni di identità e accesso).

Questi consigli si basano su tre diversi livelli di sicurezza e protezione per la posta elettronica e possono essere applicati in base al livello di granularità necessario: **base**, **sensibile**e **maggiore regolamentazione**. Per altre informazioni su questi livelli di sicurezza e sui sistemi operativi client consigliati a cui fanno riferimento questi consigli, vedere [Recommended security policies and configurations](microsoft-365-policies-configurations.md) (Criteri di sicurezza e configurazioni consigliati).

>[!NOTE]
>Per creare tutti i gruppi di sicurezza di queste indicazioni, è necessario che le funzionalità di Office siano abilitate. È importante in particolare per la distribuzione di AIP durante la protezione dei documenti in SharePoint. 
>
>![Funzionalità di Office abilitate per i gruppi di sicurezza](./media/security-group.png)
>

## <a name="baseline"></a>Versione di base 
Per creare un nuovo criterio di accesso condizionale, accedere al portale di Microsoft Azure con le credenziali di amministratore. Selezionare **Azure Active Directory > Security > Accesso condizionale**. 

È possibile aggiungere un nuovo criterio (+ Aggiungi) come illustrato nella schermata seguente:

![Criterio di accesso condizionale di base](./media/secure-email/baseline-ca-policy.png)

Le tabelle seguenti descrivono le impostazioni appropriate necessarie per esprimere i criteri richiesti per ogni livello di protezione.

### <a name="medium-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio medio ed elevato

Nella tabella seguente vengono descritte le impostazioni relative ai criteri di accesso condizionale che devono essere implementate per questo criterio.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Assegnazioni**|Utenti e gruppi|Includi|Seleziona utenti e gruppi - Selezionare il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione|Iniziare con il gruppo di sicurezza che include utenti pilota.|
|||Exclude|Exception security group; service accounts (app identities) (Gruppo di sicurezza eccezione account del servizio (identità applicazione)|Appartenenza modificata su base temporanea a seconda delle necessità|
||App cloud|Includi|Selezionare le app: selezionare Office 365 Exchange Online||
||Condizioni|Configurata|Sì|Configurare in base all'ambiente e alle necessità specifici|
||Rischio di accesso|Livello di rischio|Alto, medio|Controllare entrambi|
|**Controlli di accesso**|Concessione|Concedi accesso|True|Opzione selezionata|
|||Richiedi MFA|True|Check|
|||Richiedi un dispositivo conforme|False||
|||Richiedi dispositivo aggiunto a un dominio|False||
|||Richiedi tutti i controlli selezionati|True|Opzione selezionata|
|**Abilitare i criteri**|||Attivato|Distribuisce i criteri di accesso condizionale|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio

Per creare un nuovo criterio di accesso condizionale di Intune per Exchange Online, accedere al [portale di Microsoft Management (http://manage.microsoft.com)](http://manage.microsoft.com/) con le credenziali di amministratore e passare a **Criteri > Accesso condizionale > Criteri di Exchange Online**.

![Criteri di Exchange Online](./media/secure-email/exchange-online-policy.png)

Per richiedere un dispositivo conforme o aggiunto al dominio, è necessario impostare un criterio di accesso condizionale specificatamente per Exchange Online nel portale di gestione di Intune.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Accesso all'applicazione**|Outlook e altre app che usano l'autenticazione moderna|Tutte le piattaforme|True|Opzione selezionata|
|||Windows deve soddisfare i requisiti seguenti|Il dispositivo deve essere aggiunto a un dominio/conforme|Selezionato (elenco)|
|||Selected platform (Piattaforma selezionata)|False||
||Outlook Web Access (OWA)|Blocca i dispositivi non conformi sulle stesse piattaforme in cui si trova Outlook|True|Check|
||App di Exchange ActiveSync che usano l'autenticazione di base|Blocca i dispositivi non conformi sulle piattaforme supportate da Microsoft Intune|True|Check|
|||Blocca tutti gli altri dispositivi sulle piattaforme non supportate da Microsoft Intune|True|Check|
|**Distribuzione dei criteri**|Gruppi di destinazione|Select the Active Directory groups to target with this policy (Seleziona i gruppi di sicurezza Active Directory da usare come destinazione per questi criteri)|||
|||Tutti gli utenti|False||
|||Gruppi di sicurezza selezionati|True|Opzione selezionata|
|||Modifica|Seleziona il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione||
||Gruppi esenti|Select the Active Directory groups to exempt from this policy (overrides members of the Targeted Groups list) (Seleziona i gruppi di Active Directory da esentare da questi criteri). Questa impostazione sostituisce i membri dell'elenco Gruppi di destinazione|||
|||Nessun utente esente|True|Opzione selezionata|
|||Gruppi di sicurezza selezionati|False|||

### <a name="mobile-application-management-conditional-access-for-exchange-online"></a>Accesso condizionale per la gestione di applicazioni per dispositivi mobili per Exchange Online

Per gestire le app per dispositivi mobili, è necessario impostare un criterio di accesso condizionale specificatamente per Exchange Online nel portale di gestione di Intune.

Per gestire le app per dispositivi mobili, accedere al portale di Microsoft Azure con le credenziali di amministratore e selezionare **Protezione app di Intune > Impostazioni > Accesso condizionale > Exchange Online**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Accesso app**|App consentite|Abilita accesso app|Consenti app che supportano i criteri app di Intune|Selezionato (elenco): il risultato è un elenco di combinazioni di app/piattaforme supportate dai criteri per le app di Intune|
|**Accesso utente**|App consentite|Gruppi di utenti limitati|Aggiungi utenti/gruppi -Selezionare il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione|Iniziare con il gruppo di sicurezza che include utenti pilota|
|||Gruppi di utenti esentati|Gruppi di sicurezza di eccezione|||

#### <a name="apply-to"></a>Applica a

Dopo aver completato il progetto pilota, questi criteri devono essere applicati a tutti gli utenti dell'organizzazione.

## <a name="sensitive"></a>Dati sensibili 

### <a name="low-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio basso ed elevato
Nella tabella seguente vengono descritte le impostazioni relative ai criteri di accesso condizionale che devono essere implementate per i criteri di rischio basso ed elevato.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Assegnazioni**|Utenti e gruppi|Includi|Seleziona utenti e gruppi - Selezionare il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione|Iniziare con il gruppo di sicurezza che include utenti pilota|
|||Exclude|Exception security group; service accounts (app identities) (Gruppo di sicurezza eccezione account del servizio (identità applicazione)|Appartenenza modificata su base temporanea a seconda delle necessità|
||App cloud|Includi|Selezionare le app: selezionare Office 365 Exchange Online||
||Condizioni|Configurata|Sì|Configurare in base all'ambiente e alle necessità specifici|
||Rischio di accesso|Configurata|Sì|Configurare in base all'ambiente e alle necessità specifici|
|||Livello di rischio|Basso, medio, elevato|Controllare tutti e tre|
|**Controlli di accesso**|Concessione|Concedi accesso|True|Opzione selezionata|
|||Richiedi MFA|True|Check|
|||Richiedi un dispositivo conforme|False||
|||Richiedi dispositivo aggiunto a un dominio|False||
|||Richiedi tutti i controlli selezionati|True|Opzione selezionata|
|**Abilitare i criteri**|||Attivato|Distribuisce i criteri di accesso condizionale|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio
(Vedere le istruzioni per la protezione di base)

### <a name="mobile-application-management-conditional-access-for-exchange-online"></a>Accesso condizionale per la gestione di applicazioni per dispositivi mobili per Exchange Online

(Vedere le istruzioni per la protezione di base)

#### <a name="apply-to"></a>Applica a

Dopo aver completato il progetto pilota, questi criteri devono essere applicati a tutti gli utenti dell'organizzazione che devono accedere a posta elettronica contenente dati sensibili.

## <a name="highly-regulated"></a>Riservatezza elevata 
### <a name="mfa-required"></a>Autenticazione MFA obbligatoria

Nella tabella seguente vengono descritte le impostazioni relative ai criteri di accesso condizionale che devono essere implementate per criteri con maggiore regolamentazione.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Assegnazioni**|Utenti e gruppi|Includi|Seleziona utenti e gruppi - Selezionare il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione|Iniziare con il gruppo di sicurezza che include utenti pilota|
|||Exclude|Exception security group; service accounts (app identities) (Gruppo di sicurezza eccezione account del servizio (identità applicazione)|Appartenenza modificata su base temporanea a seconda delle necessità|
||App cloud|Includi|Selezionare le app: selezionare Office 365 Exchange Online||
|**Controlli di accesso**|Concessione|Concedi accesso|True|Opzione selezionata|
|||Richiedi MFA|True|Check|
|||Richiedi un dispositivo conforme|False|Check|
|||Richiedi dispositivo aggiunto a un dominio|False||
|||Richiedi tutti i controlli selezionati|True|Opzione selezionata|
|**Abilitare i criteri**|||Attivato|Distribuisce i criteri di accesso condizionale|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio
(Vedere le istruzioni per la protezione di base)
### <a name="mobile-application-management-conditional-access-for-exchange-online"></a>Accesso condizionale per la gestione di applicazioni per dispositivi mobili per Exchange Online
(Vedere le istruzioni per la protezione di base)
#### <a name="apply-to"></a>Applica a
Dopo aver completato il progetto pilota, questi criteri devono essere applicati a tutti gli utenti dell'organizzazione che devono accedere a posta elettronica soggetta a maggiore regolamentazione.

### <a name="high-risk-users-policy"></a>Criteri per gli utenti a rischio elevato
Perché tutti gli account compromessi di utenti a rischio elevato siano obbligati a modificare la password durante l'accesso, è necessario applicare i criteri seguenti. 

Accedere al [portale di Microsoft Azure (http://portal.azure.com)](http://portal.azure.com/) con le credenziali di amministratore e selezionare **Azure AD Identity Protection > Criteri di rischio utente**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Assegnazioni**|Users|Includi|Tutti gli utenti|Opzione selezionata|
|||Exclude|Nessuno||
||Condizioni|Rischio utente|Alta|Opzione selezionata|
|**Controlli**|Accesso|Consenti l'accesso|True|Opzione selezionata|
||Accesso|Richiedi modifica password|True|Check|
|**Verifica**|N/D|N/D|N/D|N/D|
|**Imponi criteri**|||Attivato|Avvia l'applicazione dei criteri|


## <a name="additional-configurations"></a>Configurazioni aggiuntive
Oltre ai criteri descritti in precedenza, è necessario configurare le impostazioni per la gestione di applicazioni e dispositivi mobili illustrate in questa sezione. 

### <a name="intune-mobile-application-management"></a>Gestione di applicazioni mobili di Intune 

Per garantire che la posta elettronica sia protetta dai criteri consigliati in precedenza per ogni di livello di sicurezza e di protezione dati, è necessario creare i criteri di protezione delle app di Intune nel portale di Azure.

Per creare un nuovo criterio per la protezione delle app, accedere al portale di Microsoft Azure con le credenziali di amministratore e selezionare **Protezione app di Intune > Impostazioni > Accesso condizionale > Criteri per le app**.

Aggiungere un nuovo criterio (+ Aggiungi) come illustrato nella schermata seguente:

![Gestione di applicazioni mobili di Intune](./media/secure-email/intune-mobile-app-mgmt.png)

>[!NOTE]
>Le opzioni dei criteri per la protezione delle app sono leggermente diverse tra iOS e Android. Di seguito sono specificati i criteri per Android.
>

La tabella seguente descrive le impostazioni consigliate per i criteri per la protezione delle app di Intune:

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Generalee**|Posta elettronica|Nome|Secure email policy for Android (Criteri di sicurezza per posta elettronica per Android)|Immettere un nome per i criteri|
|||Descrizione||Immettere un testo che descrive il criterio|
|||Piattaforma|Android|Le opzioni dei criteri per la protezione delle app sono leggermente diverse tra iOS e Android. Di seguito sono specificati i criteri per Android|
|**App**|Applicazioni|App|Outlook|Selezionato (elenco)|
|**Impostazioni**|Rilocazione dati|Impedisci backup in Android|Sì|In iOS viene effettua una chiamata in iTunes e iCloud|
||||Consenti all'app di trasferire i dati ad altre app|App gestite da criteri||
|||Consenti all'app di ricevere i dati da altre app|App gestite da criteri||
|||Impedisci Salva con nome|Sì||
|||Limita le operazioni taglia, copia e incolla con le altre app|App gestite da criteri||
|||Limita il contenuto Web per la visualizzazione in Managed Browser|No||
|||Crittografa dati app|Sì|In iOS selezionare l'opzione Quando il dispositivo è bloccato|
|||Disabilita sincronizzazione contatti|No||
||Accesso|Richiedi PIN per l'accesso|Sì||
|||Numero di tentativi prima della reimpostazione del PIN|3||
|||Consenti PIN semplice|No||
|||Lunghezza PIN|6||
|||Consenti impronta digitale anziché PIN|Sì||
|||Richiedi credenziali aziendali per l'accesso|No||
|||Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted|Sì||
|||Controlla di nuovo i requisiti di accesso dopo (minuti)|30||
|||Periodo di prova offline|720||
|||Intervallo offline (giorni) prima della cancellazione dei dati dell'app|90||
|||Blocca acquisizione schermo e Assistente per Android|No|In iOS questa opzione non è disponibile|

Al termine, ricordarsi di fare clic su "Crea". Ripetere i passaggi precedenti e sostituire la piattaforma selezionata (menu a discesa) con iOS. In questo modo vengono creati due criteri per le app, quindi dopo aver creato i criteri, assegnare i gruppi ai criteri e distribuirli.

### <a name="intune-mobile-device-management"></a>Gestione dei dispositivi mobili di Intune
Per creare i criteri seguenti di configurazione e conformità, accedere al [portale di Microsoft Management (http://manage.microsoft.com)](https://manage.microsoft.com/) con le credenziali di amministratore.

#### <a name="ios-email-profile"></a>Profilo di posta elettronica iOS
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di configurazione > Aggiungi > iOS > Profilo di posta elettronica (iOS 8.0 e versioni successive)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Profilo di posta elettronica**|Exchange Active Sync|Host (#)|Outlook.office365.com||
|||Nome account (#)|SecureEmailAccount|Scelta amministratore|
|||Nome utente|Nome entità utente|Selezionato (menu a discesa)|
|||Indirizzo di posta elettronica|Indirizzo SMTP primario|Selezionato (menu a discesa)|
|||Metodo di autenticazione|Nome utente e password|Selezionato (menu a discesa)|
|||Usa S/MIME|False||
||Impostazioni di sincronizzazione|Numero di giorni di messaggi di posta elettronica da sincronizzare|Due settimane|Selezionato (menu a discesa)|
|||Usa SSL|True|Check|
|||Consenti di spostare i messaggi negli altri account di posta elettronica|False||
|||Consenti di inviare i messaggi di posta elettronica dalle applicazioni di terze parti|True||
|||Sincronizza gli indirizzi di posta elettronica utilizzati di recente|True|Check|

#### <a name="ios-app-sharing-profile"></a>Profilo di condivisione app iOS
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di configurazione > Aggiungi > iOS > Configurazione generale (iOS 8.0 e versioni successive)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Security**|Tutto|Tutto|Non configurata||
|**Cloud**|Tutto|Tutto|Non configurata||
|**Applicazioni**|Browser|Tutto|Non configurata||
||App|Consenti l'installazione di app|Non configurata||
|||Richiedi una password per accedere all'archivio applicazioni|Non configurata||
|||Acquisti in-app|Non configurata||
|||Consenti i documenti gestiti in altre app non gestite (iOS 8.0 e versione successiva)|No|Selezionato (menu a discesa)|
|||Consenti documenti non gestiti in altre app gestite|Non configurata||
|||Consenti videoconferenza|Non configurata||
|||Consenti all'utente di considerare attendibili nuovi autori di app aziendali|Non configurata||
||Giochi|Tutto|Non configurata||
||Contenuto multimediale|Tutto|Non configurata|||

#### <a name="android-email-profile"></a>Profilo di posta elettronica Android
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di configurazione > Aggiungi > iOS > Profilo di posta elettronica (Samsung KNOX Standard 4.0 e versioni successive)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Profilo di posta elettronica**|Exchange Active Sync|Host (#)| Outlook.office365.com|
|||Nome account (#)|SecureEmailAccount|Scelta amministratore|
|||Nome utente|Nome entità utente|Selezionato (menu a discesa)|
|||Indirizzo di posta elettronica|Indirizzo SMTP primario|Selezionato (menu a discesa)|
|||Metodo di autenticazione|Nome utente e password|Selezionato (menu a discesa)|
|||Usa S/MIME|False||
||Impostazioni di sincronizzazione|Numero di giorni di messaggi di posta elettronica da sincronizzare|Due settimane|Selezionato (menu a discesa)|
|||Pianificazione sincronizzazione|Non configurata|Selezionato (menu a discesa)|
|||Usa SSL|True|Check|
|||Tipo di contenuti da sincronizzare|||
|||Posta elettronica|True|Controllare (bloccato)|
|||Contatti|True|Check|
|||Calendario|True|Check|
|||Attività|True|Check|
|||Note|True|Check|

#### <a name="android-for-work-email-profile"></a>Profilo di posta elettronica per Android
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di configurazione > Aggiungi > iOS > Profilo di posta elettronica (Android for Work - Gmail)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Profilo di posta elettronica**|Exchange Active Sync|Host(#)| Outlook.office365.com|
|||Nome account (#)|SecureEmailAccount|Scelta amministratore|
|||Nome utente|Nome entità utente|Selezionato (menu a discesa)|
|||Indirizzo di posta elettronica|Indirizzo SMTP primario|Selezionato (menu a discesa)|
|||Metodo di autenticazione|Nome utente e password|Selezionato (menu a discesa)|
||Impostazioni di sincronizzazione|Numero di giorni di messaggi di posta elettronica da sincronizzare|Due settimane|Selezionato (menu a discesa)|
|||Usa SSL|True|Check|

#### <a name="android-for-work-app-sharing-profile"></a>Profilo di condivisione app iOS Android for Work
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di configurazione > Aggiungi > iOS > Configurazione generale ((Android for Work)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Security**|Password|Lunghezza minima password|Non configurata||
|||Numero di errori di accesso ripetuti consentiti prima della rimozione del profilo di lavoro|Non configurata||
|||Minuti di inattività prima che il dispositivo venga bloccato|Non configurata||
|||Scadenza password (giorni)|Non configurata||
|||Ricorda cronologia password|Non configurata||
|||Richiedi una password per sbloccare il dispositivo mobile|Non configurata||
|||Consenti sblocco tramite impronta digitale (Android 6.0+)|Non configurata||
|||Consenti Smart Lock e altri agenti di attendibilità (Android 6.0+)|Non configurata||
||Impostazioni del profilo di lavoro|Consenti la condivisione dei dati tra i profili di lavoro e personali|Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale|Selezionato (menu a discesa)|
|||Nascondi le notifiche del profilo di lavoro quando il dispositivo è bloccato (Android 6.0+)|Non configurata||
|||Imposta i criteri di autorizzazione predefiniti delle app (Android 6.0+)|Non configurata|||

#### <a name="device-compliance-policy"></a>Criteri di conformità dei dispositivi
Nel [portale di gestione di Intune (https://manage.microsoft.com)](https://manage.microsoft.com/) creare i criteri di configurazione seguenti in **Criteri > Criteri di conformità > Aggiungi**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Protezione del sistema**|Password|Richiedi una password per sbloccare i dispositivi mobili (...)|Sì|Selezionato (menu a discesa)|
|||Consenti le password semplici (...)|No|Selezionato (menu a discesa)|
|||Lunghezza minima password (...)|6|Selezionato (elenco)|
||Impostazioni avanzate password|Tutto|Non configurata||
||Crittografia|Richiedi crittografia sul dispositivo mobile (...)|Sì|Selezionato (menu a discesa)|
||Profili di posta elettronica|L'account di posta elettronica deve essere gestito da Intune (iOS 8.0+)|Sì| Selezionato (menu a discesa)|
|||Seleziona (#)||Selezionare i criteri di configurazione di posta elettronica per iOS: criteri di posta elettronica iOS (vedere i criteri di configurazione descritti in precedenza)|
|**Integrità del dispositivo**|Attestazione dell'integrità del dispositivo Windows|Richiedi che i dispositivi siano riportati come integri (Windows 10 Desktop e Mobile e versioni successive)|Sì||
||Impostazioni di sicurezza del dispositivo|Tutto|Non configurata||
||Protezione dalle minacce per il dispositivo|Tutto|Non configurata||
||Jailbreak|Il dispositivo non deve essere jailbroken o rooted (iOS 8.0+, Android 4.0+)|Sì||
|**Proprietà del dispositivo**|Versione del sistema operativo|Tutto|Non configurata|||

Tutti i criteri descritti in precedenza vengono considerati distribuiti se assegnati a gruppi di utenti. Creare quindi criteri (al momento del salvataggio) o successivamente selezionando Gestisci distribuzione nella sezione Criteri (stesso livello di Aggiungi).

## <a name="remediating-medium-or-high-risk-access-events"></a>Correzione degli eventi che hanno generato rischi di accesso medio ed elevato
Se un utente segnala che è ora richiesto eseguire l'autenticazione a più fattori, il supporto può rivedere lo stato dell'utente da una prospettiva di rischio.  

Gli utenti dell'organizzazione con un ruolo Amministratore globale o Amministratore della protezione possono usare Azure AD Identity Protection per analizzare gli eventi rischiosi che hanno contribuito al punteggio del rischio calcolato. Se si identificano eventi che sono stati contrassegnati come sospetti, ma che vengono ritenuti validi (ad esempio un accesso da posizione insolita quando un dipendente è in ferie), l'amministratore può risolvere l'evento in modo che non sia più considerato per calcolare il punteggio di rischio.

## <a name="next-steps"></a>Passaggi successivi

[Suggerimenti sui criteri per la protezione di siti e file di SharePoint](sharepoint-file-access-policies.md)
 
