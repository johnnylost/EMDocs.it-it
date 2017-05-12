---
title: Gestire i dispositivi aziendali con Intune | Microsoft Docs
description: 
keywords: 
author: jeffgilb
manager: angrobe
ms.date: 3/08/2017
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9e695ec-5608-43bb-bbfb-808b869b1567
ms.reviewer: vlpetros
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: b5be7105266a7f455e1482a814929f65a130db82
ms.openlocfilehash: 6b220f4992651b5f3c107b5b958c47900515b77f
ms.contentlocale: it-it
ms.lasthandoff: 03/08/2017


---

# <a name="manage-company-owned-devices-with-intune"></a>Gestire i dispositivi di proprietà dell'azienda con Intune

Esistono varie opzioni per soddisfare le aspettative di mobilità dei dipendenti nell'ambiente di lavoro moderno, ad esempio i programmi Bring Your Own Device (BYOD). Molte organizzazioni vogliono comunque avere maggiore controllo sui dispositivi che vengono usati per accedere ai dati aziendali. In questi scenari, possono scegliere di implementare le strategie Choose Your Own Device (CYOD), in base alle quali ai dipendenti vengono proposti dispositivi mobili gestiti.

Perché le strategie CYOD siano efficaci, le aziende devono poter offrire agli utenti una gamma diversificata di dispositivi tra cui scegliere. Si tratta di un aspetto molto importante soprattutto se l'organizzazione ha deciso di implementare un strategia CYOD in alternativa a BYOD. Infatti, se gli utenti non sceglieranno un dispositivo tra quelli proposti, troveranno comunque un modo per usare i propri dispositivi non gestiti. Con CYOD, è possibile registrare nella gestione solo tipi di dispositivi specifici, ridurre i costi di assistenza e proteggere i dati aziendali immediatamente dal momento in cui un dispositivo viene assegnato a un dipendente.  I dipendenti possono usare le opzioni del dispositivo mobile a cui sono normalmente abituati senza seguire passaggi aggiuntivi o richiedere l'intervento dell'help desk affinché il dispositivo sia gestito e l'accesso ai dati aziendali sia configurato.  

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?

In base al tipo di dispositivo, alla modalità di acquisto del dispositivo e alle necessità aziendali, è possibile registrare i dispositivi di proprietà dell’azienda o i dispositivi aziendali in molti modi per essere gestiti con Microsoft Intune. È anche possibile installare l'app Portale aziendale per registrare e gestire i dispositivi aziendali come in [uno scenario BYOD](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod). I dispositivi iOS di proprietà dell'azienda possono essere registrati direttamente nella gestione con Intune tramite gli strumenti di configurazione di Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

Con EMS è possibile offrire funzionalità ed esperienze per realizzare un ambiente produttivo, in grado di accogliere diversi stili di lavoro, in qualsiasi luogo. Indipendentemente dai dispositivi usati dai dipendenti, iOS, Mac OS, Android o Windows, Intune può offrire loro una soluzione di produttività su più dispositivi, garantendo al tempo stesso la sicurezza dei dati aziendali. Oltre a offrire la gestione completa dei dispositivi mobili e del ciclo di vita delle app, Intune consente l'integrazione diretta con Office 365 e con le app di Office Mobile, che consentono di proteggere semplicemente i dati aziendali.

### <a name="recommended-solution"></a>Soluzione consigliata

Con Intune è possibile offrire ai dipendenti l'accesso ad applicazioni, dati e risorse aziendali praticamente ovunque e su qualsiasi dispositivo, mantenendo allo stesso tempo protette le informazioni aziendali. Grazie all'integrazione diretta con Office 365, gli utenti finali potranno usufruire di esperienze efficaci e funzionalità complete per la prevenzione della perdita di dati per le app di Office Mobile e il controllo di accesso a Office 365. Quando un dispositivo viene perso, rubato o semplicemente non è più necessario per il lavoro, Intune consente di cancellare in modo selettivo solo i dati aziendali dai dispositivi gestiti.

>[!Note]
>Intune riconosce un dispositivo come *di proprietà dell'azienda* se, per registrarlo, viene usato uno dei metodi descritti in questa soluzione. Se un dispositivo viene definito aziendale dal servizio Intune, verrà visualizzato **Aziendale** nella colonna Proprietà corrispondente al record dispositivo nella console di amministrazione.

![Possibilità di scelta in un panorama complesso di dispositivi](..\Solutions\media\enable-byod\management-choices-with-intune.png)

> <sup>È possibile scaricare questa infografica all'indirizzo https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup>

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
La parte restante di questa soluzione è suddivisa nelle sezioni seguenti che illustrano come eseguire queste operazioni:
- **Registrare i dispositivi iOS di proprietà dell'azienda**. Questa sezione descrive come usare l'integrazione di Apple Configurator (su un dispositivo Mac) e di DEP Apple per registrare i dispositivi di proprietà dell'azienda.
- **Registrare i dispositivi Windows 10 di proprietà dell'azienda**. Questa sezione descrive come registrare automaticamente nella gestione i dispositivi Windows 10 quando vengono aggiunti al servizio aziendale Azure Active Directory.
- **Registrare i dispositivi usando un account del manager di registrazione dispositivi**. Questa sezione contiene informazioni su come i manager di registrazione dispositivi autorizzino una sola persona dal reparto IT a registrare nella gestione un numero di dispositivi superiore a quello predefinito.
- **Contrassegnare i dispositivi di proprietà dell’azienda con i numeri IMEI (International Mobile Equipment Identity)**. Questa sezione descrive un'altra opzione per iniziare a gestire i dispositivi di proprietà dell'azienda al momento della registrazione importando i numeri IMEI che identificano i dispositivi di proprietà dell'azienda.
- **Verificare che i dispositivi gestiti siano conformi ai requisiti di sicurezza di base**. Questa sezione descrive come verificare che i dispositivi usati per accedere alle app e ai dati aziendali siano conformi ai requisiti di sicurezza di base.
- **Fornire l'accesso alle risorse aziendali**. Questa sezione illustra come il personale IT può consentire agli utenti di accedere in modo facile e sicuro alle risorse aziendali della società distribuendo profili di accesso ai dispositivi gestiti e mostra come usare Intune per gestire le distribuzioni di app acquistate con Volume Purchase Program.
- **Proteggere i dati aziendali**. Questa sezione offre informazioni utili su come fornire l'accesso condizionale alle risorse aziendali, evitare la perdita di dati e rimuovere le app e i dati aziendali dai dispositivi quando non sono più necessari per il lavoro oppure in caso di furto o smarrimento.

## <a name="enroll-corporate-owned-ios-devices"></a>Registrare i dispositivi iOS di proprietà dell'azienda
Se agli utenti viene offerta la possibilità di scegliere tra una serie di dispositivi iOS come parte di una strategia CYOD aziendale, è possibile preconfigurare la registrazione in modo che il dispositivo venga gestito con Intune sin dalla prima accensione. Intune supporta la registrazione tramite il [programma di registrazione dispositivi (DEP)](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) o tramite lo strumento Apple Configurator in esecuzione in un computer Mac per la registrazione con [Assistente configurazione](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) o [registrazione diretta](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune). È anche possibile distribuire *in modalità wireless* un profilo di registrazione ai dispositivi acquistati tramite il programma di registrazione dispositivi.

### <a name="setup-assistant-enrollment"></a>Registrazione con Assistente configurazione
Quando si usa [l'opzione Assistente configurazione per la registrazione dei dispositivi iOS](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune), il dispositivo viene reimpostato sulle impostazioni di fabbrica e preparato per l'installazione finale dal nuovo utente del dispositivo. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per preconfigurare la registrazione. I dispositivi vengono quindi distribuiti agli utenti che eseguono il processo di Assistente configurazione. Questo processo consente di configurare il dispositivo con le proprie credenziali aziendali o dell'istituto di istruzione e di completare la registrazione.

### <a name="direct-enrollment"></a>Registrazione diretta
La [registrazione diretta dei dispositivi iOS](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) crea un file compatibile con Apple Configurator da usare durante la preparazione del dispositivo. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) per registrare il dispositivo.

### <a name="dep-enrollment"></a>Registrazione tramite DEP
Microsoft Intune può distribuire un profilo di registrazione con il quale registrare i dispositivi iOS acquistati tramite il [programma di registrazione dispositivi (DEP)](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) *in modalità wireless*. Il pacchetto di registrazione può includere le opzioni di Assistente configurazione per il dispositivo. In questo modo, quando un utente esegue l'Assistente configurazione nel dispositivo, il dispositivo viene registrato in Intune specificando nella gestione il *giorno 0*.

>[!Important]

>[La registrazione dei dispositivi registrati tramite DEP](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) non può essere annullata dagli utenti.

## <a name="enroll-corporate-owned-windows-10-devices"></a>Registrare i dispositivi Windows 10 di proprietà dell'azienda
È possibile semplificare agli utenti il processo di registrazione dei dispositivi Windows nella gestione abilitando la funzionalità di registrazione automatica in Azure AD Premium. In questo caso, i dispositivi vengono registrati automaticamente per la gestione con Intune quando un utente aggiunge un account aziendale o dell'istituto di istruzione per registrare il dispositivo aziendale quando questo viene aggiunto al servizio Azure AD dell'organizzazione.

L'[aggiunta ad Azure Active Directory per Windows 10 ](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-overview) consente agli utenti di connettersi al cloud aziendale con più facilità usando Azure AD. Da qui gli utenti possono accedere ad app e risorse aziendali direttamente con i propri dispositivi Windows. Grazie all'integrazione della registrazione automatica, tali dispositivi vengono anche gestiti automaticamente da Microsoft Intune.

>[!Tip]

>Per abilitare la registrazione MDM automatica nella directory di Azure AD Premium dal [portale di Microsoft Azure](https://portal.azure.com), selezionare **Azure Active Directory**  >  **Servizi Mobility (MDM e MAM)**  >  **Microsoft Intune**.

L'aggiunta ad AD Azure è destinata alle aziende cloud-first/cloud-only. Si tratta solitamente di aziende di piccole e medie dimensioni che non usano un'infrastruttura Windows Server Active Directory Domain Services (AD DS) locale. Detto questo, l'aggiunta ad AD Azure può e sarà adottata anche da organizzazioni di grandi dimensioni su dispositivi che non possono eseguire una tradizionale aggiunta a un dominio (ad esempio i dispositivi mobili) o dagli utenti che devono necessariamente accedere a Office 365 o ad altre app SaaS di Azure AD. Quando un dispositivo viene gestito con Intune, gli amministratori IT possono gestire i dispositivi aggiunti ad AD Azure insieme ai dispositivi aggiunti a un dominio AD DS nella console di gestione di Configuration Manager tramite la [gestione di dispositivi mobili ibrida](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management#what-is-hybrid-mdm-with-configuration-manager).
Quando un utente aggiunge un account aziendale o dell'istituto di istruzione in un dispositivo Windows 10, il dispositivo viene automaticamente contrassegnato come "di proprietà dell'azienda".

## <a name="enroll-devices-with-a-device-enrollment-manager-dem-account"></a>Registrare i dispositivi usando un account del manager di registrazione dispositivi
Per registrare un numero elevato di dispositivi mobili per l'organizzazione, è possibile usare un unico [account del manager di registrazione dispositivi](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) Intune. Dopo aver creato un account del manager di registrazione dispositivi, è possibile registrare fino a 1.000 dispositivi.

È possibile usare un account del manager di registrazione dispositivi per registrare solo i dispositivi che non sono usati da un singolo utente specifico. Questi tipi di dispositivi sono ideali per app POS o di utilità, ad esempio, ma non sono adatti per gli utenti che devono accedere alla posta elettronica o alle risorse aziendali.
- Gli utenti non possono usare le app Volume Purchase Program di Apple poiché è necessario un ID Apple per utente per la gestione delle app.
- Se si usa un manager di registrazione dispositivi per la registrazione dei dispositivi iOS, non è possibile usare Apple Configurator o il programma di registrazione dispositivi di Apple per la registrazione dei dispositivi.

## <a name="tag-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Contrassegnare i dispositivi di proprietà dell’azienda con i numeri IMEI (International Mobile Equipment Identity)
Microsoft Intune consente agli amministratori di identificare i dispositivi mobili aziendali tramite l'[importazione dei numeri IMEI](https://docs.microsoft.com/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) per le piattaforme per dispositivi mobili.

È possibile importare fino a 5.000 numeri IMEI usando un file con formato speciale e con estensione csv oppure immettere manualmente fino a 15 numeri IMEI dispositivo per volta dalla console di amministrazione di Intune. Quando un dispositivo con un numero IMEI viene registrato in Intune, in genere quando un utente installa l'app Portale aziendale e completa il processo di registrazione, il dispositivo viene contrassegnato come di proprietà dell'azienda e viene visualizzato come registrato nel gruppo dei dispositivi IMEI.

## <a name="make-sure-that-managed-devices-comply-with-basic-security-requirements"></a>Verificare che i dispositivi gestiti siano conformi ai requisiti di sicurezza di base
Dopo aver registrato un dispositivo iOS, Android o Windows 10 , il personale IT deve assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali siano conformi ai requisiti di sicurezza di base, come l'uso di un PIN per l'accesso ai dispositivi e la crittografia dei dati archiviati nei dispositivi. Un set di regole di questo tipo è definito [criteri di conformità](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

Quando [si creano e si distribuiscono criteri di conformità](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune) a un utente, tutti i dispositivi gestiti da Intune vengono controllati per vedere se sono conformi ai requisiti di sicurezza di base definiti come parte dei criteri CYOD o BYOD. Dopo che un dispositivo è stato valutato per determinarne la conformità ai criteri, il relativo stato viene comunicato al servizio Intune. In alcuni casi è possibile che agli utenti venga chiesto di correggere le impostazioni non conformi, ad esempio usando un PIN o la crittografia dei dispositivi, ma in altri casi l'app Portale aziendale segnalerà all'utente eventuali problemi di conformità rilevati.

## <a name="provide-access-to-company-resources"></a>Fornire l'accesso alle risorse aziendali

Questa sezione illustra come il personale IT può consentire agli utenti di accedere in modo facile e sicuro alle risorse aziendali della società distribuendo profili di accesso ai dispositivi gestiti e gestendo le app acquistate con Volume Purchase Program.

### <a name="provide-access-to-company-data"></a>Fornire l'accesso ai dati aziendali
La prima cosa che la maggior parte dei dipendenti vuole sul proprio dispositivo mobile è l'accesso alla posta elettronica e ai documenti aziendali. E si aspettano di configurare l'accesso senza procedure complesse e senza doversi rivolgere al supporto tecnico. Con Microsoft Intune è semplice [creare e distribuire le impostazioni di posta elettronica](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) per le app di posta elettronica native preinstallate nei dispositivi mobili usati dall'organizzazione.

> [!NOTE]
> Intune supporta la configurazione di profili di posta elettronica Android for Work per le app di posta elettronica Gmail e Nine Work disponibili in Google Play Store.

Oltre alla posta elettronica, EMS consente di controllare l'accesso e proteggere i dati aziendali locali a cui si accede dall'esterno dei limiti di sicurezza aziendali tradizionali. I profili Microsoft Intune [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune), [VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile) e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari per svolgere le loro attività ovunque si trovino. È anche possibile accedere in modo sicuro alle applicazioni Web e ai servizi dell'azienda ospitati in locale e proteggerli usando il proxy per l'applicazione Azure Active Directory e l'accesso condizionale.

### <a name="add-apps-for-enrolled-devices"></a>Aggiungere app per dispositivi registrati
Aggiungere app per dispositivi registrati con Intune è facile, ma per poter distribuire o gestire un'app, è prima necessario [aggiungerla a Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) usando l'autore del software Intune. È possibile usare l'autore del software Intune per configurare le proprietà dell'app e, se opportuno, caricarla nello spazio di archiviazione cloud.

Con Intune, è possibile [distribuire o gestire i tipi seguenti di app](https://docs.microsoft.com/intune/deploy-use/add-apps) per i dispositivi registrati:
- **Programma di installazione software**. Questi tipi di app includono il programma di installazione software Windows (con estensione exe o msi), il pacchetto per Android (con estensione apk), il pacchetto app per iOS (con estensione ipa), il pacchetto app per Windows Phone (con estensione xap, appx e appxbundle), il pacchetto app Windows (con estensione appx, appxbundle) e Windows Installer tramite file MDM (con estensione msi). Tutti i tipi di app del programma di installazione software vengono caricati nello [spazio di archiviazione cloud](https://docs.microsoft.com/intune/deploy-use/add-apps#cloud-storage-space).
- **Collegamento esterno**. Questo tipo di distribuzione dell'app usa un collegamento esterno (URL) che consente agli utenti di scaricare un'app da un App Store o un collegamento a un'applicazione basata sul Web che viene eseguita dal Web browser. Le app basate su collegamenti esterni non sono archiviate nello spazio di archiviazione nel cloud Intune.
- **App iOS gestita dall'App Store**. È possibile usare app iOS gestite per gestire e distribuire app iOS gratuite dall'App Store. È anche possibile usare app iOS gestite per associare i criteri di gestione delle applicazioni mobili ad app compatibili e controllarne lo stato nella console di amministrazione. Le app iOS gestite non vengono archiviate nello spazio di memorizzazione cloud di Intune.

### <a name="manage-volume-purchased-apps"></a>Gestire le app acquistate con Volume Purchase Program
È possibile [distribuire con facilità app degli Store ai dispositivi gestiti](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune) e anche app di destinazione ai dispositivi non gestiti usando il sito Web del portale aziendale, ma Intune consente anche di gestire e distribuire le app acquistate con Volume Purchase Program dall'App Store di iOS e da Windows Store per le aziende. In questo modo, è possibile ridurre il carico amministrativo associato al monitoraggio delle app acquistate con Volume Purchase Program.

> [!TIP]
> È possibile [configurare facilmente Single Sign On (SSO) con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) per consentire agli utenti di accedere ad app con il nome utente di dominio e la password usati in locale. È inoltre possibile [fornire l'accesso basato su Internet alle app Web ospitate in locale](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) usando il proxy per l'applicazione Azure Active Directory.

Con Intune è facile importare le informazioni sui contratti multilicenza da uno dei due App Store, tenere traccia del numero di licenze usate e impedire agli utenti di installare più copie dell'app rispetto a quelle possedute.

-   [Gestire le app acquistate tramite Volume Purchase Program per dispositivi iOS](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune). Per acquistare più licenze per app iOS, è necessario usare [Volume Purchase Program di Apple per le aziende](http://www.apple.com/business/vpp/). A questo scopo, configurare un account VPP di Apple dal sito Web Apple e caricare il token VPP di Apple in Intune. È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

-   [Windows Store per le aziende](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune). In [Windows Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Intune le app acquistate con Volume Purchase Program.

## <a name="protect-company-data"></a>Proteggere i dati aziendali

Intune protegge i dati aziendali tra più livelli di tecnologia. A livello di identità, l'accesso condizionale protegge l'accesso ai servizi consentendo solo l'accesso da dispositivi conformi e gestiti. A livello di applicazione client, i criteri di protezione delle app consentono di evitare la perdita dei dati impedendo lo spostamento dei dati in app o percorsi di archiviazione di dati non protetti e cancellando i dati quando un dispositivo viene smarrito o rubato.

### <a name="enforce-conditional-access-to-company-resources"></a>Imporre l'accesso condizionale alle risorse aziendali

È possibile usare criteri di conformità in combinazione con [criteri di accesso condizionale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) per verificare se i dispositivi sono conformi ai requisiti di sicurezza di base definiti dai criteri BYOD. Se un dispositivo non è conforme ai criteri, vengono applicate le regole di accesso condizionale e l'accesso viene negato finché il dispositivo non è configurato per soddisfare i requisiti dei criteri. In questo modo si ha la certezza che i dispositivi solo gestiti e conformi possono accedere ai dati aziendali da servizi come Exchange ([Exchange locale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune) o [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)), SharePoint Online, Skype for Business Online e altri ancora.

> [!IMPORTANT]
> I criteri di accesso condizionale non possono essere usati se non vengono applicati criteri di conformità per la convalida della conformità.

### <a name="prevent-data-loss-of-company-data-with-application-protection-policies"></a>Evitare la perdita dei dati aziendali con criteri di protezione delle applicazioni

I criteri di protezione delle applicazioni di Intune consentono di gestire in modo versatile la modalità di accesso ai dati, con o senza registrazione dei dispositivi. La possibilità di proteggere i dati aziendali con o senza la registrazione dei dispositivi permette di abilitare scenari di protezione in grado di rendere accessibili in modo sicuro i dati aziendali, anche quando un utente è restio a registrare il proprio dispositivo per la gestione.

È possibile usare i [criteri di protezione delle app di Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) per proteggere i dati aziendali a cui accedono i dispositivi iOS e Android degli utenti. Implementando questi criteri a livello di app è possibile controllare il modo in cui i dati aziendali vengono usati e condivisi dai dipendenti, anche se il dispositivo stesso non è gestito da Intune.

Usare i [criteri di Windows Information Protection (WIP)](https://docs.microsoft.com/intune/deploy-use/microsoft-intune-policy-reference#windows-configuration-policies) per eseguire la stessa operazione per i dispositivi Windows 10 gestiti. Questi criteri funzionano senza interferire con l'esperienza dei dipendenti o richiedere modifiche all'ambiente di rete o ad altre app.

### <a name="wipe-company-data-while-leaving-personal-data-intact"></a>Cancellare i dati aziendali mantenendo intatti i dati personali

Quando un dispositivo non viene più usato per lavoro, viene reimpiegato o risulta mancante, è necessario poter rimuovere le app e i dati aziendali dal dispositivo. A tale scopo è possibile usare le funzionalità di cancellazione selettiva e completa di Intune. Gli utenti possono anche cancellare in remoto i dati dai dispositivi personali registrati per la gestione dal portale aziendale di Intune.

Anziché eseguire una [cancellazione completa](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#full-wipe) che ripristina le impostazioni predefinite del dispositivo e rimuove i dati e le impostazioni dell'utente, è possibile usare la funzionalità di [cancellazione selettiva](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#selective-wipe) per rimuovere soltanto i dati aziendali dal dispositivo lasciando inalterati i dati personali dell'utente.

Una volta avviata, il dispositivo inizia immediatamente il processo di cancellazione selettiva per essere rimosso dalla gestione. Al termine del processo, tutti i dati aziendali vengono eliminati e il nome del dispositivo viene rimosso dalla console di amministrazione di Intune terminando il ciclo di vita di gestione del dispositivo.

### <a name="learn-more"></a>Altre informazioni
[Iniziare a usare Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)

