---
title: Proteggere i dati aziendali di Office 365 con Microsoft Intune | Documentazione Microsoft
description: "EMS e Office 365 offrono insieme una soluzione completa per la produttività mobile gestita che rende disponibile agli utenti lo standard di produttività migliore e al personale IT controlli dei dati completamente integrati."
keywords: 
author: jeffgilb
manager: swadhwa
ms.date: 10/18/2016
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cc0d2e1f-9c34-4dcb-ac1f-2f355e9ebb7e
ms.reviewer: vlpetros
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 168d6d559aa17bbe0b8e912a53cbd384a3dc48a3
ms.openlocfilehash: 59bbc2cd3476c8632f8a72c9144eeedcdb141c42


---

# <a name="protect-office-365-company-data-with-intune"></a>Proteggere i dati aziendali di Office 365 con Intune
La prima cosa che la maggior parte dei dipendenti vuole sul proprio dispositivo mobile è l'accesso alla posta elettronica e ai documenti aziendali. E si aspettano di configurare l'accesso senza procedure complesse e senza doversi rivolgere al supporto tecnico. I responsabili IT d'altro canto vogliono mantenere la sicurezza dei dati aziendali dovunque senza dover gestire un'infrastruttura locale di grandi dimensioni. Con Enterprise Mobility + Security (EMS) è possibile garantire la produttività dei dipendenti con le app e i dispositivi preferiti e la protezione dei dati aziendali. Le informazioni seguenti descrivono in che modo.

## <a name="how-can-enterprise-mobility--security-ems-help-you"></a>Come può essere utile Enterprise Mobility + Security (EMS)?
EMS è l'unica soluzione progettata per proteggere in modo nativo i messaggi di posta elettronica, i file e le app di Microsoft Office su tutti i dispositivi che gli utenti portano al lavoro. Con EMS è possibile offrire in modo semplice ai dipendenti fuori sede posta elettronica sicura con quattro livelli di protezione in identità, dispositivi, app e dati. Con EMS i dipendenti avranno accesso sicuro alla posta elettronica e ai documenti aziendali, alla posta elettronica personale e a esperienze di produttività con le app di Office Mobile, ad esempio Outlook, Word, Excel, PowerPoint e OneDrive.

Office 365 è progettato per i dipendenti che desiderano la flessibilità di portare il proprio lavoro ovunque senza limiti di utilizzo. EMS e Office 365 offrono insieme una soluzione completa per la produttività mobile gestita che rende disponibile agli utenti lo standard di produttività migliore e al personale IT controlli dei dati completamente integrati.

### <a name="recommended-solution"></a>Soluzione consigliata
Con Intune, lo *"strumento di gestione"* di EMS, è possibile offrire ai dipendenti accesso ad applicazioni, dati e risorse aziendali dovunque su qualsiasi dispositivo e contemporaneamente proteggere le informazioni aziendali. Oltre a una maggior facilità d'uso, Intune offre anche un metodo più moderno ed economico di proteggere i dati aziendali rispetto alle soluzioni locali più tradizionali. Se Intune protegge i dati di Office 365, non sarà più necessario installare e gestire un infrastruttura locale o aprire il firewall aziendale per instradare il traffico.

Il video che segue è un'introduzione rapida all'uso di Intune e Office 365 per offrire ai dipendenti un'esperienza di accesso sicuro ai dati aziendali da dispositivi iOS, Android e Windows:

<iframe width="675" height="480" src="https://www.youtube.com/embed/To9zfl6-Z6Y" frameborder="0" allowfullscreen></iframe>

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
Il resto di questa soluzione è suddiviso nelle sezioni seguenti che illustrano come proteggere i dati aziendali di Office 365 con Intune:
- **Registrare dispositivi mobili e PC Windows per la gestione**. Questa sezione descrive come registrare i dispositivi (iOS, Android, Android for Work e PC Windows) per la gestione con Intune, in modo da poter distribuire i criteri in tali dispositivi per la protezione dei dati aziendali di Office 365.
- **Proteggere l'accesso ai servizi di Office 365**. Questa sezione presenta informazioni sui criteri di conformità di Intune e illustra come gestire l'accesso condizionale ai servizi di Office 365 Exchange Online e SharePoint Online.
- **Proteggere i dati aziendali**. Questa sezione illustra come usare i criteri di protezione delle app per dispositivi Android e iOS, nonché come sfruttare i criteri WIP (Windows Information Protection) per proteggere i dati delle app aziendali nei PC Windows 10 gestiti come dispositivi da Intune.
- **Cancellare i dati aziendali in modo selettivo**. Questa sezione offre informazioni utili su come rimuovere le app e i dati aziendali dai dispositivi quando non sono più necessari per il lavoro oppure in caso di furto o smarrimento.


## <a name="enroll-mobile-devices-and-windows-pcs-into-management"></a>Registrare dispositivi mobili e PC Windows per la gestione
La registrazione dei dispositivi e dei PC per la gestione in Intune garantisce l'applicazione di tutti i criteri e i profili di accesso configurati per i dispositivi gestiti. Per poter registrare i dispositivi, è necessario innanzitutto [preparare il servizio Intune](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) assegnando le licenze agli utenti, impostando l'autorità di gestione dei dispositivi mobili e rispettando i requisiti di registrazione per i diversi tipi di dispositivo da gestire. Può essere necessario anche [personalizzare il portale aziendale](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) con informazioni di supporto e branding dell'azienda per offrire un'esperienza di registrazione e supporto attendibile agli utenti.

Dopo aver preparato il servizio Intune, il processo di registrazione dei dispositivi per la gestione è immediato ma leggermente diverso per i vari tipi di dispositivo:
- **Dispositivi iOS e Mac**. È necessario richiedere un certificato APNs (Apple Push Notification service) per registrare iPad, iPhone o dispositivi Mac OS X. Dopo aver [caricato il certificato APNs in Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) è possibile [registrare i dispositivi iOS](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) usando l'app Portale aziendale e usare il sito Web del portale aziendale per [registrare i dispositivi Mac OS X](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).
- **Dispositivi Android**. Non è necessario eseguire alcuna operazione per preparare il servizio Intune per la registrazione dei dispositivi Android. Gli utenti possono [registrare i dispositivi Android](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) per la gestione usando l'app Portale aziendale disponibile in Google Play.
-   **Android for Work**. Per [configurare Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) per dispositivi con Android 5.0 Lollipop e successivi che supportano la gestione dei profili di lavoro con Intune, l'organizzazione deve iscriversi per Android for Work in Google e quindi configurare le impostazioni di Android for Work nel nodo Amministrazione della console di amministrazione di Intune.
- **Windows Phone e PC Windows**. È consigliabile [impostare un alias DNS per il server di registrazione](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) per rendere più semplice la registrazione dei dispositivi Windows. In alternativa, è possibile [registrare i dispositivi Windows](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) aggiungendo un account aziendale o dell'istituto di istruzione.

> [!TIP]
> È possibile rendere ancora più semplice la registrazione dei dispositivi Windows per gli utenti [abilitando la funzionalità di registrazione automatica](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) in Azure AD (Premium). In questo caso, i dispositivi verranno registrati automaticamente per la gestione con Intune quando un utente aggiunge un account aziendale o dell'istituto di istruzione per registrare il dispositivo personale oppure quando un dispositivo di proprietà dell'azienda viene aggiunto ad Azure AD dell'organizzazione.

## <a name="secure-access-to-office-365-services"></a>Proteggere l'accesso ai servizi di Office 365
Sebbene gli utenti si aspettino di poter accedere alla posta elettronica e a tutti i file aziendali quando usano le app per dispositivi mobili di Office 365, è anche necessario assicurarsi che soltanto i dispositivi attendibili si connettano alle risorse aziendali. A tale scopo è possibile usare i criteri di accesso condizionale di Intune per assicurarsi che i dipendenti accedano ai servizi cloud di Office 365 soltanto da dispositivi gestiti e conformi ai criteri.

Per poter usare i criteri di accesso condizionale è necessario definire i [criteri di conformità del dispositivo di Intune](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Questi tipi di criteri di Intune controllano i dispositivi, alla prima registrazione e successivamente a intervalli regolari, per verificare che siano specificate le impostazioni desiderate. In questo modo è più semplice assicurarsi che soltanto i dispositivi che soddisfano i requisiti di sicurezza possano accedere alla risorsa aziendale. Definire ciò che rende conforme un dispositivo (ad esempio, la richiesta di una password per lo sblocco, la possibilità o il divieto di usare password semplici, la lunghezza minima delle password, non essere un dispositivo jailbroken, ecc.) creando criteri di conformità del dispositivo di Intune e quindi distribuirli agli utenti.

> [!IMPORTANT]
> I criteri di accesso condizionale non possono essere usati se non vengono applicati criteri di conformità per la convalida della conformità.

I [criteri di accesso condizionale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) possono essere usati per proteggere l'accesso ai servizi di Office 365, ad esempio a Dynamics CRM Online<sup>1</sup>, Exchange Online<sup>2</sup>, SharePoint Online<sup>2</sup> e Skype for Business Online<sup>1</sup>. Negli esempi seguenti vengono configurati i criteri di accesso condizionale per Exchange Online e SharePoint Online.  

> <sup>1</sup> Solo iOS e Android.

> <sup>2</sup> Dispositivi iOS, Android e Windows.

### <a name="secure-access-to-exchange-online"></a>Proteggere l'accesso a Exchange Online
Con Intune la posta elettronica di Exchange Online dell'azienda è protetta in base ai criteri di accesso condizionale e di conformità impostati. È possibile ad esempio [limitare l'accesso alla posta elettronica di Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) ai dispositivi che non usano una password complessa, non sono jailbroken e non sono crittografati.

Ecco cosa accade quando un utente tenta di controllare la posta elettronica usando un dispositivo che non è gestito da Intune quando sono stati configurati criteri di accesso condizionale per accedere a Exchange Online:
1. L'utente tenta di leggere la posta elettronica aziendale di Exchange Online usando l'app di posta elettronica nativa del dispositivo Android non gestito. L'accesso alla posta elettronica viene negato perché il dispositivo non è gestito da Intune e pertanto non è conforme ai criteri di conformità.
2. L'unico messaggio di posta elettronica visibile all'utente è il messaggio inviato dal servizio Intune che comunica che il dispositivo non è conforme ai criteri aziendali e che è necessario registrarlo per poter accedere alla posta elettronica.
3. Dopo la registrazione del dispositivo e la verifica della conformità ai criteri aziendali, viene ripristinato l'accesso completo alla posta elettronica aziendale.

![Immagini che illustrano l'uso dell'accesso condizionale per Exchange Online](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig1.png)

### <a name="secure-access-to-sharepoint-online"></a>Proteggere l'accesso a SharePoint Online
Intune consente anche di [proteggere l'accesso ai file di SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) usando l'accesso condizionale. Come nella protezione dell'accesso alla posta elettronica, sarà necessario impostare due criteri che dovranno essere soddisfatti per abilitare l'accesso: un criterio di conformità del dispositivo per assicurarsi che i criteri aziendali vengano soddisfatti nel dispositivo e un criterio di accesso condizionale che specifica le condizioni necessarie per accedere al servizio.

Quando un utente tenta di usare un dispositivo non gestito per connettersi al servizio SharePoint Online protetto dai criteri di accesso condizionale di Intune si verifica quanto segue:
1.  All'utente viene negato l'accesso alle risorse di SharePoint Online e viene visualizzato un messaggio che richiede di rafforzare la sicurezza e include collegamenti per registrare il dispositivo per la gestione in Intune.
2.  L'utente esegue la registrazione del dispositivo seguendo i collegamenti inclusi nel messaggio di accesso negato.
3.  Dopo la registrazione del dispositivo e la verifica della conformità ai criteri aziendali, viene ripristinato l'accesso completo ai dati di SharePoint Online aziendali.

![Immagini che illustrano l'uso dell'accesso condizionale per SharePoint Online](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig2.png)

## <a name="protect-company-data"></a>Proteggere i dati aziendali
È noto che la maggior parte dei dipendenti usa i propri dispositivi mobili per motivi di lavoro e personali. Con l'aumento dei dispositivi di proprietà del dipendente usati per lavoro, aumenta anche il rischio di perdita accidentale dei dati tramite app e servizi, ad esempio posta elettronica, social media e cloud pubblico non controllati dall'organizzazione. Ad esempio, quando un dipendente invia le immagini di progettazione più recenti dal proprio account di posta elettronica personale, copia e incolla le informazioni su un prodotto in un tweet o salva il report delle vendite in corso nella propria area di archiviazione nel cloud pubblico. Di conseguenza, pur volendo garantire la produttività dei dipendenti, è necessario anche impedire perdite dei dati aziendali intenzionali o accidentali.

Mentre i criteri di accesso condizionale fanno in modo che soltanto i dispositivi e gli utenti conformi possano accedere alla posta elettronica, rimane il problema di proteggere i messaggi di posta elettronica ed eventuali file allegati. Come impedire che il contenuto venga copiato, spostato, salvato in un'altra posizione o condiviso con altri? Per risolvere questo problema, Intune usa i criteri di gestione di applicazioni mobili (MAM) per i dispositivi iOS e Android e i criteri di Windows Information Protection (WIP) per i PC e i dispositivi mobili Windows 10.  

### <a name="mam-for-managed-ios-and-android-mobile-devices"></a>Gestione di applicazioni mobili per dispositivi mobili iOS e Android gestiti
È possibile usare i criteri di gestione di applicazioni mobili (MAM) di Intune per proteggere i dati aziendali a cui accedono i dispositivi iOS e Android degli utenti. Implementando questi criteri a livello di app è possibile controllare il modo in cui i dati aziendali vengono usati e condivisi dai dipendenti.

> [!TIP]
> I criteri MAM di Intune possono essere usati indipendentemente dalla soluzione di gestione dei dispositivi mobili (MDM) a condizione che all'utente sia stata assegnata una licenza Intune. Ciò significa che è possibile proteggere i dati dell'azienda registrando o senza registrare i dispositivi per la gestione in Intune o anche nel caso in cui il dispositivo sia gestito da un servizio MDM non Microsoft.

L'amministratore [configura le impostazioni dei criteri delle app MAM di Intune dal portale di amministrazione di Azure](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune). I due tipi di impostazioni inclusi nei criteri MAM sono *Rilocazione dati* e *Accesso*. I criteri di rilocazione dati definiscono in che modo possono essere usati i dati di un'app protetta. È possibile ad esempio impedire il comando "Salva con nome" o le funzioni taglia, copia o incolla. Le impostazioni dei criteri di accesso determinano il livello di sicurezza del dispositivo che si ritiene sia necessario per consentire ai dipendenti di usare l'app. Con queste impostazioni è possibile richiedere un PIN dell'app aggiuntivo o impedire l'esecuzione dell'app su dispositivi jailbroken o rooted.

Le schermate seguenti illustrano alcuni metodi per proteggere un'app con i criteri MAM di Intune. Nell'esempio viene richiesto un PIN per accedere all'app (impostazione di accesso) e i dati aziendali vengono protetti impedendo di incollare le informazioni aziendali in app non gestite (impostazione di rilocazione dati):

1.  Al primo avvio dell'app gestita (Yammer per iOS in questo esempio), all'utente viene richiesto di creare un PIN per accedere all'app. Successivamente, sarà necessario immettere il PIN ogni volta che l'app viene avviata.
2.  L'utente può copiare dati aziendali come le conversazioni di Yammer e incollarli in altre app gestite.
3.  Tuttavia, quando l'utente tenta di incollare tale contenuto in un messaggio di testo o in qualsiasi altra app non gestita, la funzione Incolla non sarà disponibile.  

![Immagini che illustrano il funzionamento dei criteri MAM](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig3.png)

### <a name="windows-information-protection-wip-for-managed-windows-10-pcs-and-mobile-devices"></a>Windows Information Protection (WIP) per PC e dispositivi mobili Windows 10 gestiti
I criteri WIP di Intune proteggono da potenziali perdite di dati da dispositivi Windows 10 gestiti. Questi criteri funzionano senza interferire con l'esperienza del dipendente o richiedere modifiche all'ambiente di rete o ad altre app.

I criteri funzionano nel modo seguente: i dati aziendali vengono crittografati automaticamente dopo essere stati caricati in un dispositivo Windows gestito da un'origine aziendale o se un dipendente contrassegna i dati come dati di lavoro (non personali). Quando i dati aziendali vengono scritti su disco, WIP usa la tecnologia Encrypting File System (EFS) inclusa in Windows per proteggerli e associarli all'identità dell'azienda. Durante la creazione dei criteri WIP di Intune, viene specificato un elenco delle app attendibili che possono accedere e modificare i dati aziendali. Successivamente, la funzionalità AppLocker lavora in background con il sistema operativo per controllare quali app possono essere eseguite e come è possibile accedere e condividere i dati aziendali. Le app autorizzate non devono essere modificate per aprire i dati aziendali poiché sono incluse nell'elenco che consente a Windows di concedere loro l'accesso ai dati aziendali.

> [!TIP]
> Se le app e i dati aziendali sono protetti dai criteri WIP, nel menu Start dei dispositivi degli utenti finali viene visualizzata l'indicazione "Gestita" accanto al nome dell'app autorizzata. Per i tasti di scelta rapida e i file salvati dell'app viene visualizzata anche l'icona di valigetta WIP in aggiunta alle icone delle app standard.
<img src="..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig4.png" alt="Image showing how WIP policies affect the Start Menu and files" style="width:376px;height:112x;">

Le [impostazioni dei criteri di configurazione WIP](https://docs.microsoft.com/intune/deploy-use/microsoft-intune-policy-reference#windows-configuration-policies) consentono di impostare diversi livelli di controllo dalla console di amministrazione di Intune. I livelli di protezione dei dati includono impostazioni da **Installazione automatica** (registra solo l'attività WIP) a **Blocca** che impedisce agli utenti di condividere qualsiasi contenuto dalle app protette. **Sostituisci** è un'impostazione intermedia che consente agli utenti di condividere i dati aziendali in app non protette con un avviso ma registra tutte le azioni per una revisione successiva.

Di seguito viene descritto come i criteri WIP di Intune possono essere usati per proteggere i dati aziendali su dispositivi Windows 10 gestiti:
1.  Viene creato un nuovo criterio WIP che viene distribuito agli utenti dalla console di amministrazione di Intune.
2.  In questo esempio le informazioni di AppLocker per Microsoft Word vengono usate per aggiungere Word 2016 all'elenco delle app autorizzate, il livello di restrizione dei criteri è impostato su Sostituisci e i criteri sono distribuiti agli utenti.
3.  Un utente tenta di incollare i dati aziendali copiati da un documento di Word 2016 protetto in una nuova istanza di Blocco note non protetta. Viene immediatamente richiesto all'utente di verificare che la modifica sia pianificata dalla classificazione lavoro a personale e che l'azione venga registrata.

![Immagini che illustrano il funzionamento dei criteri WIP](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig5.png)

## <a name="selectively-wipe-company-data"></a>Cancellare i dati aziendali in modo selettivo
Quando un dispositivo non viene più usato per lavoro, viene reimpiegato o risulta mancante, è necessario poter rimuovere le app e i dati aziendali dal dispositivo. A tale scopo è possibile usare le funzionalità di cancellazione selettiva e completa di Intune. Gli utenti possono anche cancellare in remoto i dati dai dispositivi personali registrati per la gestione dal portale aziendale di Intune.

Anziché eseguire una [cancellazione completa](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#full-wipe) che ripristina le impostazioni predefinite del dispositivo e rimuove i dati e le impostazioni dell'utente, è possibile usare la funzionalità di [cancellazione selettiva](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#selective-wipe) per rimuovere soltanto i dati aziendali dal dispositivo lasciando inalterati i dati personali dell'utente.

Per eseguire la cancellazione selettiva di un dispositivo è sufficiente fare clic con il pulsante destro del mouse sul nome del dispositivo, selezionare **Disattiva/Cancella** e quindi **Cancellare il dispositivo in modo selettivo**:

![Immagine delle opzioni di cancellazione selettiva nella console di Intune](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig6.png)

Una volta avviata, il dispositivo inizia immediatamente il processo di cancellazione selettiva per essere rimosso dalla gestione. Al termine del processo, tutti i dati aziendali vengono eliminati e il nome del dispositivo viene rimosso dalla console di amministrazione di Intune terminando il ciclo di vita di gestione del dispositivo.

### <a name="learn-more"></a>Altre informazioni
[Iniziare a usare Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)



<!--HONumber=Dec16_HO2-->


