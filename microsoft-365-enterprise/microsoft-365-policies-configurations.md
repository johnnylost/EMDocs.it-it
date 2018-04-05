---
title: Configurazioni e criteri di sicurezza consigliati per Microsoft 365 Enterprise | Microsoft docs
description: Descrive i consigli Microsoft e i concetti di base per la distribuzione di configurazioni e criteri di protezione per posta elettronica, documenti e app.
author: dougeby
manager: dougeby
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/30/2017
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: a7f6ab6765be5462c652feb006839f0839b1136e
ms.sourcegitcommit: 8d42bd1ec3d7bf5f873a7b681b0fea73a748b413
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="recommended-security-policies-and-configurations"></a>Configurazioni e criteri di sicurezza consigliati

## <a name="introduction"></a>Introduzione
Sebbene non esista un'unica indicazione ottimale per tutti gli ambienti dei clienti, le procedure consigliate nel documento descrivono le indicazioni generali di Microsoft su come applicare le impostazioni di configurazione e i criteri nel cloud Microsoft per garantire la sicurezza e la produttività dei dipendenti.  

**Destinatari** I consigli illustrati qui sono concepiti per architetti dell'infrastruttura aziendale e professionisti dell'IT che hanno familiarità con [Office 365](https://technet.microsoft.com/library/dn127064(v=office.14).aspx) e [Microsoft Enterprise Mobility + Security](http://microsoft.com/ems) che include Azure Active Directory (identità), Microsoft Intune (gestione dei dispositivi) e Azure Information Protection (protezione dei dati).

**Ambiente del cliente** I criteri consigliati sono applicabili a organizzazioni aziendali che operano interamente nell'ambito del cloud Microsoft e per clienti con un'infrastruttura distribuita in locale e nel cloud Microsoft.

**Presupposti** Molti dei consigli offerti si basano su servizi disponibili solo con sottoscrizioni di Enterprise Mobility + Security (EMS) E5 sottoscrizioni. I consigli illustrati presuppongono funzionalità complete della sottoscrizione a EMS E5.

**Avvertenze importanti** È possibile che l'organizzazione sia soggetta a requisiti normativi o altri requisiti di conformità, incluse indicazioni specifiche per le quali potrebbe essere necessario applicare criteri diversi dalle configurazioni consigliate in questo articolo.  Tali configurazioni consigliano controlli dell'utilizzo non disponibili in precedenza.  Tali controlli sono consigliabili perché rappresentano una soluzione equilibrata tra sicurezza e produttività.  

Nonostante il massimo impegno profuso per tenere in considerazione una vasta gamma di requisiti di protezione aziendale, non è possibile prendere in considerazione tutti i requisiti possibili o tutti gli aspetti unici di ogni organizzazione. Usare i consigli offerti nel documento come guida sul modo considerato corretto da Microsoft e dal team aziendale della produttività e della sicurezza di applicare i criteri.  

>[!NOTE]
>Per una panoramica dei concetti principali necessari per comprendere le funzionalità di protezione descritte in queste indicazioni, vedere [Panoramica di Microsoft 365 Enterprise](index.md).
>

## <a name="core-concepts"></a>Concetti base
Tutte le misure di sicurezza del mondo non bastano se gli utenti ignorano i criteri di sicurezza aziendali perché costituiscono un inutile ostacolo all'esecuzione del lavoro. Single Sign-On (SSO) di Azure AD cerca di ridurre al minimo la pressione sugli utenti. Questo consente agli utenti di rimanere produttivi pur conformandosi ai criteri di controllo di accesso dell'organizzazione.

### <a name="single-sign-on-authentication"></a>Autenticazione Single Sign-On

Il diagramma seguente illustra un flusso di autenticazione SSO tipico:

![Autenticazione Single Sign-On utente finale](./media/policies-configurations/authentication-flow.png)

Per avviare l'autenticazione, il client invia le credenziali, ad esempio nome utente e password, e/o gli elementi SSO ottenuti in precedenza, a Azure AD. Un elemento SSO può essere un token di sessione per un browser o un token di aggiornamento per applicazioni complesse.

Dopo che le credenziali e/o l'elemento SSO sono stati verificati in Azure AD e che sono stati valutati tutti i criteri applicabili, viene generato un token di accesso per il provider di risorse, Office 365 nel diagramma qui sopra. Azure AD rilascia anche un elemento SSO come parte della risposta per consentire ai client di ottenere l'autenticazione SSO nelle richieste successive. Il client archivia l'elemento SSO e invia il token di accesso come identificazione per il provider di risorse. Dopo che Office 365 ha verificato il token di accesso e ha eseguito i controlli necessari, concede l'accesso client ai documenti.

#### <a name="single-sign-on-sso-refresh-tokens"></a>Token di aggiornamento Single Sign-On (SSO)
È possibile ottenere l'autenticazione SSO in diversi modi. Ad esempio, è possibile usare i cookie provenienti da un provider di identità come l'elemento SSO per archiviare lo stato di accesso per un utente all'interno di un browser. In questo modo saranno possibili tentativi futuri di accesso automatico alle applicazioni, ovvero senza alcuna richiesta di credenziali, tramite lo stesso provider di identità.

Quando un utente esegue l'autenticazione con Azure AD, viene stabilita una sessione SSO con Azure AD e il browser dell'utente. Il token SSO, sotto forma di cookie, rappresenta la sessione. Azure AD usa due tipi di token di sessione SSO: permanente e non permanente. I token di sessione permanenti vengono archiviati come cookie permanenti dai browser quando durante l'accesso è stata selezionata la casella di controllo **Mantieni l'accesso**. I token di sessione non permanenti vengono archiviati come cookie di sessione e vengono eliminati quando il browser viene chiuso.

Per applicazioni affidabili che possono usare protocolli di autenticazione moderna, ad esempio [OpenId Connect](http://openid.net/specs/openid-connect-core-1_0.html) e [OAuth 2.0](https://tools.ietf.org/html/rfc6749), l'autenticazione SSO viene abilitata con i token di aggiornamento come elementi SSO, oltre ai cookie SSO descritti in precedenza. I token di aggiornamento vengono presentati a un server di autorizzazione quando un'applicazione richiede un nuovo token di accesso. Il token di aggiornamento contiene le attestazioni e gli attributi sul tipo di metodi di autenticazione usata per autenticare gli utenti. Ad esempio, se un utente ha eseguito l'autenticazione usando diversi metodi, nome utente e password e autenticazione via telefono, nel token di aggiornamento è presente un'attestazione di autenticazione a più fattori (MFA, Multi-Factor Authentication). Potrebbero esserci anche attestazioni aggiuntive che contengono dati, ad esempio la durata della validità dell'autenticazione a più fattori.

I token di aggiornamento consentono al client di ottenere un nuovo token di accesso, senza la necessità di eseguire un'altra autenticazione interattiva. I token di aggiornamento hanno una durata molto più lunga rispetto ai token di accesso e possono essere riscattati per ottenere una nuova coppia di token di accesso e di aggiornamento. In seguito, i token di aggiornamento appena ottenuti possono essere usati per recuperare un altro set di token di accesso e di aggiornamento. Il client continuerà il processo SSO fino a quando non scadrà l'impostazione del tempo di inattività massimo del token di aggiornamento, non verrà raggiunta l'età massima del token di aggiornamento, o non verranno modificati i requisiti dei criteri di autenticazione e autorizzazione. Tale modifica si verifica quando viene generato il token di aggiornamento originale. Modifiche degli attributi utente significative, ad esempio la reimpostazione della password, richiedono anche la generazione di un nuovo token di autenticazione. Per continuare, è necessario che il client esegua una nuova autenticazione interattiva. Ciò significa essenzialmente un'interruzione del processo di SSO che il client non ha riscontrato fino ad ora.

#### <a name="conditional-access"></a>Accesso condizionale
Azure AD agisce come un servizio di autorizzazione per le applicazioni determinando se rilasciare token di accesso in base alla valutazione di tutti i criteri di accesso condizionale applicati alla risorsa cui si sta tentando di accedere. Se vengono soddisfatti i requisiti dei criteri, vengono rilasciati un token di accesso e un token di aggiornamento aggiornato. Se il criterio non viene soddisfatto, l'utente riceve istruzioni su come soddisfare i criteri e/o deve completare passaggi aggiuntivi tra cui l'autenticazione a più fattori (MFA). Una volta completata l'autenticazione a più fattori, l'attestazione di autenticazione a più fattori viene aggiunta al token di aggiornamento risultante.  

Le attestazioni nel token di aggiornamento vengono accumulate nel tempo. Alcune delle attestazioni hanno sequenze temporali di scadenza, dopo le quali non sono più considerate durante i controlli di autorizzazione. In alcuni casi ciò può causare risultati imprevisti. Ad esempio, se i criteri di accesso condizionale sono configurati in modo che sia necessaria l'autenticazione a più fattori per i tentativi di autenticazione provenienti da percorsi Extranet. In questo caso, è possibile che gli utenti non ricevano la richiesta di autenticazione a più fattori prevista quando accedono a una risorsa dalla Extranet. Un possibile motivo è che l'utente potrebbe aver precedentemente eseguito l'autenticazione a più fattori poco prima di lasciare la Intranet. Pertanto, ha un'attestazione di autenticazione a più fattori valida nel relativo token di accesso. La richiesta di autenticazione a più fattori soddisfa i requisiti dei criteri e pertanto Azure AD non richiede all'utente un'altra autenticazione a più fattori.

#### <a name="token-lifetime-policy"></a>Durata dei token
Oltre la scadenza delle attestazioni singole in un token, i token stessi hanno una scadenza. Come illustrato in precedenza, i token scaduti sono uno dei motivi per cui il servizio SSO può essere interrotto. È possibile impostare la durata di un token emesso da Azure AD tramite i [criteri di durata del token](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes). Come si può dedurre da quanto illustrato finora, non è facile definire i contorni di una sessione SSO. Ad esempio, quando le app complesse costituite da vari fattori apparentemente disconnessi influiscono sulla durata di una sessione SSO.

>[!NOTE]
>Gli amministratori globali di Azure AD possono controllare i periodi di inattività e di validità dei token di aggiornamento. Per informazioni sui token di accesso e le attestazioni vedere l'articolo [Durata dei token configurabili in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes).
>

#### <a name="primary-refresh-tokens"></a>Token di aggiornamento primari
Finora è stato illustrato il funzionamento di SSO nel contesto di un client singolo, ma questo non è sufficiente per descrivere l'esperienza di SSO in una sola app. Oggi gli utenti usano flussi di lavoro interattivi su più applicazioni all'interno della stessa suite di applicazioni, come ad esempio Microsoft Office. Agli utenti serve anche l'accesso ad applicazioni non correlate, tra cui le applicazioni LOB sviluppate internamente.

In genere, i dispositivi Windows aggiunti a un dominio, tramite l'autenticazione integrata di Windows (Kerberos), ottengono un livello del servizio SSO elevato in diverse applicazioni e risorse. Queste applicazioni includono i browser supportati, come ad esempio Internet Explorer o Edge. Esiste qualcosa di analogo per Azure AD, sotto forma di un token di aggiornamento principale. Tale token con privilegi è disponibile solo per un insieme di entità client selezionato, ad esempio per componenti di sistema della piattaforma. Le entità possono quindi consentire l'accesso di autenticazione negoziata ad altre applicazioni client, in modo che possano offrire anch'esse un'esperienza SSO facile. Per gli utenti di Office 365 di dispositivi [iOS](https://docs.microsoft.com/azure/active-directory/develop/active-directory-sso-ios) e [Android](https://docs.microsoft.com/azure/active-directory/develop/active-directory-sso-android), è stato possibile ridurre il numero di autenticazioni richieste applicando la funzionalità di broker di autenticazione. La funzionalità è incorporata nelle app Microsoft Authenticator e Portale aziendale Intune.

>[!NOTE]
>I consigli illustrati in questo documento presuppongono che una di queste app, Microsoft Authenticator o Portale aziendale Intune, sia stata distribuita agli utenti dei dispositivi IOS o Android.

### <a name="multi-factor-authentication"></a>Multi-Factor Authentication
L'autenticazione a più fattori (MFA, Multi-Factor Authentication) garantisce un livello di attendibilità elevato sull'oggetto dell'autenticazione, poiché l'oggetto offre più prove o evidenze sulla propria identità. Le prove possono essere segreti prestabiliti conosciuti solo dall'oggetto e dall'autorità oppure un'entità fisica che solo l'oggetto possiede. L'autenticazione a più fattori in genere viene eseguita in diverse fasi. Per prima cosa stabilisce l'identità usando le password e quindi richiede un metodo di autenticazione diverso, meno soggetto ad attacchi dannosi, come secondo fattore, o viceversa.

Diverse autorità possono avere un'interpretazione dell'autenticazione a più fattori leggermente diversa oppure possono usare l'autenticazione avanzata. Ad esempio, alcune autorità, o più precisamente gli amministratori dei criteri di configurazione, possono scegliere di interpretare l'autenticazione basata su smart card fisica come MFA. Questa situazione può verificarsi anche se in senso stretto l'autenticazione tramite smart card è un'autenticazione a fase singola.

La combinazione di smart card e PIN, il segreto, obbligatori per poter usare la smart card può essere interpretata come MFA. Tuttavia, le organizzazioni potrebbero scegliere di essere più flessibili sulla frequenza con cui vengono richiesti metodi di autenticazione più gravosi. In questi casi le autenticazioni normali, che si verificano tra le autenticazioni più avanzate, possono essere considerate valide per risorse che in genere richiedono l'autenticazione avanzata. Ad esempio, in alcune organizzazioni può essere accettabile richiedere all'utente di eseguire l'autenticazione a più fattori dopo un certo numero di ore o di giorni. Il tempo dipende dalla riservatezza delle risorse protette e dal fatto che la posizione fisica dell'utente che tenta di accedere a una risorsa non cambia.

Azure Active Directory e AD FS usano l'attestazione MFA per indicare se l'autenticazione viene eseguita con l'autenticazione a più fattori. Per impostazione predefinita, Azure AD rilascia token con attestazione MFA quando l'autenticazione viene eseguita con [Azure MFA](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud) o [Windows Hello for Business](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification). Negli scenari federativi Azure AD esegue l'attestazione MFA dai provider di identità federative, come ad esempio AD FS, e riporta l'attestazione MFA nei token.

## <a name="recommended-client-configurations"></a>Configurazioni client consigliate
In questa sezione vengono descritte le configurazioni client della piattaforma predefinite consigliate per offrire un'esperienza SSO ottimale agli utenti, oltre ai prerequisiti tecnici per l'accesso condizionale.

### <a name="windows-devices"></a>Dispositivi Windows
È consigliabile usare Windows 10, versione 1703 o successive, poiché Azure è progettato per offrire un'esperienza di uso ottimale di SSO sia in locale che in Azure AD. I dispositivi aziendali o dell'istituto di istruzione devono essere configurati per unirsi ad Azure AD direttamente o, se l'organizzazione usa l'aggiunta a un dominio AD in locale, devono essere [configurati per la registrazione automatica e invisibile con Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Per i dispositivi Windows BYOD, gli utenti possono usare "Aggiungi account aziendale o dell'istituto di istruzione". Si noti che gli utenti del browser Chrome in Windows 10 devono [installare un'estensione](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) per poter ottenere la stessa esperienza di accesso ottimale degli utenti di Edge o Internet Explorer. Se l'organizzazione ha dispositivi Windows 7 aggiunti a un dominio, è possibile installare il pacchetto [Microsoft Workplace Join per i computer non Windows 10](https://www.microsoft.com/download/details.aspx?id=53554) per registrare i dispositivi con Azure AD.

### <a name="ios-devices"></a>Dispositivi iOS
È consigliabile installare l'[app Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sui dispositivi degli utenti prima di distribuire i criteri MFA o dell'accesso condizionale. Come minimo, l'app deve essere installata nel momento in cui agli utenti [viene richiesto di registrare i dispositivi](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/multi-factor-authentication-end-user-first-time) in Azure AD tramite l'aggiunta di un account aziendale o dell'istituto di istruzione o quando installano l'app Portale aziendale Intune per registrare i dispositivi per la gestione. Ciò dipende dai criteri di accesso condizionale configurati.

### <a name="android-devices"></a>Dispositivi Android
È consigliabile che gli utenti installino l'[app Portale aziendale Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en
) e l'[app Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) prima che vengano distribuiti i criteri di accesso condizionale o quando richiesto durante determinati tentativi di autenticazione. Dopo l'installazione delle app, è possibile che venga richiesto agli utenti di registrarsi con Azure AD o di registrare il dispositivo con Intune. Ciò dipende dai criteri di accesso condizionale configurati.

È consigliabile anche che i dispositivi di proprietà dell'azienda vengano normalizzati in OEM e che le versioni che supportano Android for Work o Samsung Knox consentano che gli account di posta elettronica siano gestiti e protetti dai criteri MDM Intune.

## <a name="security-guidelines"></a>Linee guida per la sicurezza
In questa sezione vengono illustrate le linee guida per la sicurezza generali da seguire quando si implementa uno dei consigli descritti nelle sezioni successive.

### <a name="security-and-productivity-trade-offs"></a>Compromesso tra sicurezza e produttività
È necessario arrivare a un compromesso tra sicurezza e produttività. Per illustrare questo concetto, si usa spesso il triangolo Sicurezza-Funzionalità-Usabilità/Facilità di utilizzo:

![Compromesso tra sicurezza e produttività](./media/policies-configurations/security-triad.png)

I consigli illustrati si basano sui principi del triangolo Sicurezza-Funzionalità-Facilità di utilizzo seguenti:

* Conoscere il gruppo di destinatari: flessibilità in base a mansione lavorativa/barra della sicurezza
* Applicare i criteri di sicurezza Just-In-Time e assicurarsi che siano efficaci

### <a name="administrators-versus-users"></a>Amministratori e utenti
È consigliabile creare gruppi di sicurezza che contengano tutti gli utenti che hanno account amministrativi o idonei per ricevere temporaneamente privilegi di account amministrativo. Tali gruppi di sicurezza devono quindi essere usati per definire criteri di accesso condizionale specifici per gli amministratori di Azure AD e di Office 365.  

I consigli relativi ai criteri specificati tengono in considerazione i privilegi associati agli account. I ruoli di [amministratore di Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) hanno molti più privilegi per i servizi di Office 365. Pertanto, i suggerimenti sui criteri per tali account sono più rigorosi rispetto a quelli per gli account utente normali. Tutti i criteri che fanno riferimento agli amministratori indicano i criteri consigliati per gli account di amministratore di Office 365.

### <a name="reduce-the-number-of-accounts-with-persistent-admin-access"></a>Ridurre il numero di account con accesso amministratore permanente
Usare Azure AD Privileged Identity Management per ridurre il numero di account amministrativi permanenti. È consigliabile anche che gli amministratori di Office 365 abbiano un account utente separato, senza privilegi di amministratore, per l'uso normale, e usino l'account di amministratore solo quando è necessario per completare un'attività associata alla loro mansione lavorativa.

## <a name="tiers-of-security-and-protection"></a>Livelli di sicurezza e protezione
La maggior parte delle organizzazioni hanno requisiti specifici relativi a sicurezza e protezione dei dati. Tali requisiti variano in base al settore e alle mansioni lavorative all'interno delle organizzazioni. Ad esempio, l'ufficio legale e gli amministratori di Office 365 potrebbero richiedere maggiore sicurezza e controlli di protezione sulle informazioni della corrispondenza tramite posta elettronica che non sono richiesti per gli utenti di altre business unit.

Ogni settore ha anche il proprio set di normative specializzate. Anziché specificare un elenco di tutte le opzioni di sicurezza o un'indicazione per ogni settore o mansione lavorativa, sono stati specificati consigli per tre diversi livelli di sicurezza e protezione dati che possono essere applicati in base alle proprie esigenze di granularità: [protezione di base, protezione avanzata e protezione per ambienti altamente regolamentati](https://go.microsoft.com/fwlink/p/?linkid=841656).  

**Protezione di base**. È consigliabile stabilire uno standard minimo per la protezione dei dati, nonché le identità e i dispositivi che accedono ai dati. I consigli basilari possono essere seguiti per garantire una solida protezione predefinita che soddisfi le esigenze di molte organizzazioni.

**Protezione avanzata**. Alcuni clienti hanno un subset di dati che devono essere protetti a livelli superiori o richiedono che tutti i dati siano protetti a livelli superiori. È possibile applicare una protezione maggiore per tutti i set di dati o solo per alcuni di essi nell'ambiente Office 365. È consigliabile proteggere le identità e i dispositivi che accedono ai dati sensibili con livelli di sicurezza analoghi.

**Protezione per ambienti altamente regolamentati**. Alcune organizzazioni potrebbero avere una piccola quantità di dati altamente classificati, segreti commerciali o dati soggetti a regolamentazione. Microsoft offre funzionalità che consentono alle organizzazioni di soddisfare questi requisiti, inclusa la protezione aggiuntiva per identità e dispositivi.

### <a name="default-protection-mechanism-recommendations"></a>Consigli per i meccanismi di protezione predefiniti
Nella tabella seguente sono elencati i consigli sui meccanismi di protezione predefiniti per ognuno dei livelli di protezione e sicurezza definiti in precedenza:

|Meccanismo di protezione|Versione di base|Dati sensibili|Protezione per ambienti altamente regolamentati|
|:-------------------|:-------|:--------|:---------------|
|**Applicare l'autenticazione a più fattori**|A partire da rischio di accesso medio|A partire da rischio di accesso basso|Per tutte le nuove sessioni|
|**Applicare modifica password**|Per gli utenti ad alto rischio|Per gli utenti ad alto rischio|Per gli utenti ad alto rischio|
|**Applicare la protezione delle applicazioni di Intune**|Sì|Sì|Sì|
|**Applicare la registrazione di Intune**|Richiede un dispositivo conforme o aggiunto a un dominio|Richiedi un dispositivo conforme o aggiunto a un dominio|Richiedi un dispositivo conforme o aggiunto a un dominio|

### <a name="device-ownership"></a>Proprietà del dispositivo
La tabella sopra riportata riflette la tendenza di molte organizzazioni a supportare una combinazione di dispositivi aziendali e dispositivi personali o BYOD per abilitare la produttività mobile tra i dipendenti. I criteri di Protezione app di Intune garantiscono che la posta elettronica sia protetta da divulgazioni non consentite al di fuori dell'app Outlook Mobile e di altre app di Office Mobile, sia aziendali che BYOD.  

I dispositivi di proprietà dell'azienda devono essere gestiti da Intune o aggiunti a un dominio per applicare altri tipi di protezione e controllo.  A seconda della riservatezza dei dati, l'organizzazione potrebbe scegliere di non consentire l'uso di dispositivi BYOD per app o utenti specifici.

## <a name="next-steps"></a>Passaggi successivi

 [Deploy common identity and device access policies](identity-access-policies.md) (Distribuire criteri comuni di identità e accesso ai dispositivi)
