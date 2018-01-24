---
title: Criteri di sicurezza consigliati per posta elettronica -Microsoft 365 Enterprise | Microsoft Docs
description: Descrive i criteri consigliati da Microsoft sull'applicazione di criteri e configurazioni che riguardano la posta elettronica.
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 01/18/2018
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: c86f8f86d134d77e45ab7a59564b9f0d4821ed38
ms.sourcegitcommit: eb3521981c5dec164ce2a14b4d4d53830b5ba461
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="policy-recommendations-for-securing-email"></a>Criteri consigliati per la protezione della posta elettronica

In questo articolo vengono descritti i criteri di sicurezza per la posta elettronica dell'organizzazione e i client di posta elettronica che supportano l'autenticazione moderna e l'accesso condizionale. Queste indicazioni si aggiungono a quelle contenute in [Common identity and access policy recommendations](identity-access-policies.md) (Consigli sui criteri comuni di identità e accesso).

Queste indicazioni si basano su tre diversi livelli di sicurezza e protezione per la posta elettronica e possono essere applicati in base al livello di granularità necessario:

- **Baseline** (Livello base): Microsoft consiglia di definire uno standard minimo per la protezione dei dati, nonché le identità e i dispositivi che accedono ai dati. Microsoft offre come impostazione predefinita una protezione avanzata efficiente, che soddisfa le esigenze di molte organizzazioni. Alcune organizzazioni richiedono funzionalità aggiuntive per soddisfare i propri requisiti di base.
- **Sensitive** (Dati sensibili): alcuni clienti hanno un subset di dati che richiede un grado di protezione superiore. È possibile applicare una protezione superiore a set di dati specifici nell'ambiente Office 365. Microsoft consiglia di applicare livelli di protezione analoghi alle identità e ai dispositivi che accedono ai dati sensibili. 
- **Highly regulated** (Dati altamente sensibili): alcune organizzazioni possono avere una piccola quantità di dati della massima riservatezza, segreti commerciali o dati soggetti a regolamentazione. Microsoft offre funzionalità che consentono alle organizzazioni di soddisfare questi requisiti, inclusa la protezione aggiuntiva per identità e dispositivi.

Per altre informazioni, vedere l'introduzione dell'argomento [Configurazioni e criteri di sicurezza consigliati](microsoft-365-policies-configurations.md).

> [!IMPORTANT]
> Per creare tutti i gruppi di sicurezza di queste indicazioni, è necessario che le funzionalità di Office siano abilitate. Questa impostazione è particolarmente importante per la distribuzione di Azure Information Protection (AIP) quando si proteggono i documenti in SharePoint Online.
>
>![Funzionalità di Office abilitate per i gruppi di sicurezza](./media/security-group.png)
>

## <a name="baseline"></a>Versione di base
Per creare nuovi criteri di accesso condizionale: 

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali. Dopo l'accesso viene visualizzato il dashboard di Azure.

2. Scegliere **Azure Active Directory** dal menu a sinistra.

3. Nella sezione **Sicurezza** scegliere **Accesso condizionale**.

4. Scegliere **Nuovi criteri** come illustrato nella schermata seguente:

![Criterio di accesso condizionale di base](./media/secure-email/CA-EXO-policy-1.png)

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

Per creare criteri di accesso condizionale per Exchange Online:

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali. Dopo l'accesso viene visualizzato il dashboard di Azure.

2. Scegliere **Azure Active Directory** dal menu a sinistra.

3. Nella sezione **Sicurezza** scegliere **Accesso condizionale**.

4. Scegliere **Nuovo criterio**.

5. Immettere un nome per i criteri, quindi in **Utenti e gruppi** scegliere gli utenti e i gruppi ai quali applicare i criteri.

6. Scegliere **App cloud**.

7. Scegliere **Seleziona le app**, selezionare **Office 365 Exchange Online** nell'elenco **App cloud** e fare clic su **Seleziona**. Dopo aver selezionato l'app **Office 365 Exchange Online** fare clic su **Chiudi**.

8. Scegliere **Concedi** nella sezione **Controlli di accesso**.

9. Scegliere **Concedi accesso**, selezionare sia **Richiedi che i dispositivi siano contrassegnati come conformi** sia **Require domain joined (Hybrid Azure AD)** (Richiedi dispositivo aggiunto a un dominio - Hybrid Azure AD), quindi scegliere **Seleziona**.

10. Fare clic su **Crea** per creare i criteri di accesso condizionale di Exchange Online.

    > [!NOTE]
    > A partire da Intune in Azure tutti i criteri di accesso condizionale devono essere creati nel carico di lavoro di Azure Active Directory. Per praticità, il portale di Intune dispone di un collegamento al carico di lavoro dei criteri di accesso condizionale di Azure AD.

    > [!IMPORTANT]
    > Per assistenza nella migrazione al portale di Intune in Azure dei criteri di accesso condizionale creati in precedenza nel portale di Intune classico, vedere l'argomento [Riassegnare i criteri di accesso condizionale dal portale di Intune classico al portale di Azure](https://docs.microsoft.com/intune/conditional-access-intune-reassign). 

### <a name="app-based-conditional-access-for-exchange-online"></a>Accesso condizionale basato su app per Exchange Online

È possibile aggiungere un ulteriore livello di sicurezza impostando criteri di accesso condizionale basati su app per Exchange Online nel portale di Intune in Azure. Quando si applica l'accesso condizionale basato sulle app per Exchange Online è necessario richiedere agli utenti di usare un'app specifica (ad esempio Microsoft Outlook) per l'accesso alla posta elettronica aziendale.

Per aggiungere criteri di accesso condizionale basato su app:

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune. Dopo l'accesso viene visualizzato il dashboard di Azure.

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare "**Intune**".

3. Scegliere **Protezione app di Intune**.

4. Nel pannello **Gestione di applicazioni mobili di Intune** scegliere **Tutte le impostazioni**.

5. Scegliere **Exchange Online** nella sezione **Accesso condizionale**.

6. Selezionare **Consenti app che supportano i criteri app di Intune** e quindi scegliere l'app (ad esempio Microsoft Outlook).

7. Scegliere **Gruppi di utenti limitati**, fare clic su **Seleziona gruppi**, selezionare l'utente o il gruppo al quale applicare i criteri e fare clic su **Seleziona**.

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

### <a name="app-based-conditional-access-for-exchange-online"></a>Accesso condizionale basato su app per Exchange Online

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
### <a name="app-based-conditional-access-for-exchange-online"></a>Accesso condizionale basato su app per Exchange Online
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

Per creare un nuovo criterio per la protezione delle app, accedere al portale di Microsoft Azure con le credenziali di amministratore e selezionare **Protezione app di Intune > Criteri per le app**.

Aggiungere un nuovo criterio (+ Aggiungi) come illustrato nella schermata seguente:

![Gestione di applicazioni mobili di Intune](./media/secure-email/CA-EXO-policy-2.png)

>[!NOTE]
>Le opzioni dei criteri per la protezione delle app sono leggermente diverse tra iOS e Android. Di seguito sono specificati i criteri per Android.
>

La tabella seguente descrive le impostazioni consigliate per i criteri per la protezione delle app di Intune:

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Generalee**|Posta elettronica|Name|Secure email policy for Android (Criteri di sicurezza per posta elettronica per Android)|Immettere un nome per i criteri|
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

- Per informazioni dettagliate, vedere [Come creare e assegnare criteri di protezione delle app](https://docs.microsoft.com/intune/app-protection-policies).

### <a name="intune-mobile-device-management"></a>Gestione dei dispositivi mobili di Intune
È possibile creare i seguenti profili di configurazione dei dispositivi e criteri di conformità del dispositivo accedendo al [portale di Intune in Azure](https://portal.azure.com) con le credenziali di Intune.

#### <a name="ios-email-profile"></a>Profilo di posta elettronica iOS
Nel [portale di Intune in Azure](https://portal.azure.com) è possibile creare i seguenti profili di configurazione dei dispositivi in **Configurazione del dispositivo > Profili > Crea profilo > Piattaforma (iOS) > Tipo di profilo (Posta elettronica)**.

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

#### <a name="android-email-profile"></a>Profilo di posta elettronica Android
Nel [portale di Intune in Azure](https://portal.azure.com) è possibile creare i seguenti profili di configurazione dei dispositivi in **Configurazione del dispositivo > Profili > Crea profilo > Piattaforma (Android) > Tipo di profilo (Posta elettronica)**.

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
Nel [portale di Intune in Azure](https://portal.azure.com) è possibile creare i seguenti profili di configurazione dei dispositivi in **Configurazione del dispositivo > Profili > Crea profilo > Piattaforma (Android for Work) > Tipo di profilo (Posta elettronica)**.

|Categories|Tipo|Proprietà|Valori|Note|
|:---------|:---|:---------|:-----|:----|
|**Profilo di posta elettronica**|Exchange Active Sync|Host(#)| Outlook.office365.com|
|||Nome account (#)|SecureEmailAccount|Scelta amministratore|
|||Nome utente|Nome entità utente|Selezionato (menu a discesa)|
|||Indirizzo di posta elettronica|Indirizzo SMTP primario|Selezionato (menu a discesa)|
|||Metodo di autenticazione|Nome utente e password|Selezionato (menu a discesa)|
||Impostazioni di sincronizzazione|Numero di giorni di messaggi di posta elettronica da sincronizzare|Due settimane|Selezionato (menu a discesa)|
|||Usa SSL|True|Check|

#### <a name="device-compliance-policy"></a>Criteri di conformità dei dispositivi
Nel [portale di Intune in Azure](https://portal.azure.com) è possibile creare i seguenti criteri di conformità del dispositivo in **Conformità del dispositivo > Criteri > Crea criterio > Piattaforma (iOS, Android o altre) > Impostazioni**.

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
