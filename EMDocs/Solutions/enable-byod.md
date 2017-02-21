---
title: Abilitare BYOD con Intune | Documentazione Microsoft
description: 
keywords: 
author: jeffgilb
manager: angrobe
ms.date: 2/10/2017
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d31eebe-81d2-4c6b-bfec-fbd536096dda
ms.reviewer: vlpetros
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4edb16e4ef00b7376af800ab542f42c0e530197
ms.openlocfilehash: 9defe28a74bc3e53f6ae5dc33b33396e47247265


---
# <a name="enable-byod-with-intune"></a>Abilitare BYOD con Intune
Il supporto per le trasformazioni digitali rappresenta una nuova sfida per il personale IT, impegnato a proteggere i dati aziendali e al tempo stesso garantire la produttività dei dipendenti nel sempre più complesso panorama attuale della tecnologia mobile. Con la progressiva evoluzione delle organizzazioni verso il cloud, i dipendenti si aspettano di mantenere alti livelli di produttività sui dispositivi mobili, in linea con le loro esperienze consumer su più dispositivi.

![Possibilità di scelta in un panorama complesso di dispositivi](..\Solutions\media\enable-byod\management-choices-with-intune.png)

> <sup>È possibile scaricare questa infografica all'indirizzo https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup>

Alcuni di questi dispositivi sono gestiti a livello aziendale e possono essere destinati a un utente specifico oppure condivisi tra più dipendenti. I dipendenti possono inoltre usare dispositivi che gestiscono personalmente, ad esempio un iPhone o un PC per le attività lavorative giornaliere o un dispositivo complementare per accedere saltuariamente a Internet, ad esempio un iPad o un computer della famiglia.

Oltre ai dispositivi, anche il luogo di lavoro sta vivendo profonde trasformazioni. Le persone non lavorano più esclusivamente in un ufficio o in un'area di lavoro tradizionale. Oggi si lavora da casa, nei bar, presso la sede del cliente, mentre si è in viaggio e anche in aereo. Per questo motivo i programmi BYOD (Bring Your Own Device) si sono diffusi negli ambienti di lavoro attuali. È compito del personale IT sfruttare le opportunità e i vantaggi offerti per aumentare la soddisfazione dei dipendenti e ridurre i costi mantenendo al tempo stesso il controllo dei dati aziendali.

I programmi BYOD di successo prevedono controlli più rigorosi e livelli di sicurezza più elevanti senza imporre processi complessi o cambiare il modo di lavorare delle persone. Un'esperienza efficace per gli utenti finali si concretizza in una maggiore probabilità che vengano usate le soluzioni sicure offerte e in una minore probabilità che gli utenti facciano ricorso a espedienti totalmente fuori controllo per completare il lavoro.

## <a name="how-can-enterprise-mobility--security-ems-help-you"></a>Come può essere utile Enterprise Mobility + Security (EMS)?

Con EMS è possibile offrire funzionalità ed esperienze per realizzare un ambiente produttivo, in grado di accogliere diversi stili di lavoro, in qualsiasi luogo. Indipendentemente dai dispositivi usati dai dipendenti, iOS, Mac OS, Android o Windows, Microsoft Intune, incluso in EMS, può aiutare a fornire loro una soluzione di produttività su più dispositivi, garantendo al tempo stesso la sicurezza dei dati aziendali. Intune offre funzionalità MDM e MAM che permettono di proteggere i dati aziendali con o senza la gestione dei dispositivi. Oltre a offrire la gestione completa dei dispositivi mobili e del ciclo di vita delle app, Intune consente l'integrazione diretta con Office 365 e con le app di Office Mobile.

### <a name="recommended-solution"></a>Soluzione consigliata

Con Intune è possibile offrire ai dipendenti l'accesso ad applicazioni, dati e risorse aziendali praticamente ovunque e su qualsiasi dispositivo, mantenendo allo stesso tempo protette le informazioni aziendali. Grazie all'integrazione diretta con Office 365, gli utenti finali potranno usufruire di esperienze efficaci e funzionalità complete per la prevenzione della perdita di dati per le app di Office Mobile e il controllo di accesso a Office 365. Quando un dispositivo viene perso, rubato o semplicemente non è più necessario per il lavoro, Intune consente di cancellare in modo selettivo solo i dati aziendali dai dispositivi BYOD.

Ecco un breve video in cui professionisti IT e utenti reali parlano delle proprie esigenze e delle sfide da affrontare per trovare il giusto equilibrio tra produttività e protezione in un mondo incentrato sui dispositivi mobili e sul cloud:
<iframe width="675" height="480" src="https://www.youtube.com/embed/pgAmKnluwVw" frameborder="0" allowfullscreen></iframe>

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

La parte restante di questa soluzione è suddivisa nelle sezioni seguenti che illustrano come eseguire queste operazioni:

-   **Registrare i dispositivi e verificare la conformità**. Questa sezione descrive come consentire agli utenti di registrare i dispositivi (iOS, Mac OS, Android, Android for Work e Windows) per la gestione con Intune, distribuire loro dei criteri e verificare che siano conformi ai requisiti di sicurezza di base.

-   **Fornire l'accesso alle risorse aziendali**. Questa sezione illustra come il personale IT può consentire agli utenti di accedere in modo facile e sicuro alle risorse aziendali della società distribuendo profili di accesso ai dispositivi gestiti e mostra come usare Intune per gestire le distribuzioni di app acquistate con Volume Purchase Program.  

-   **Proteggere i dati aziendali**. Questa sezione offre informazioni utili su come fornire l'accesso condizionale alle risorse aziendali, evitare la perdita di dati e rimuovere le app e i dati aziendali dai dispositivi quando non sono più necessari per il lavoro oppure in caso di furto o smarrimento.

## <a name="enroll-devices-and-check-for-compliance"></a>**Registrare i dispositivi e verificare la conformità**

Questa sezione descrive come consentire agli utenti di registrare i dispositivi per la gestione con Intune e verificare che i dispositivi siano conformi ai requisiti di sicurezza di base.

### <a name="enable-users-to-enroll-their-personal-devices-into-management"></a>Consentire agli utenti di registrare i dispositivi personali per la gestione

La registrazione dei dispositivi e dei PC per la gestione con Intune garantisce l'applicazione di tutti i criteri e i profili di accesso configurati per i dispositivi gestiti. Per poter registrare i dispositivi, è necessario innanzitutto [preparare il servizio Intune](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) assegnando le licenze agli utenti, impostando l'autorità di gestione dei dispositivi mobili e rispettando i requisiti di registrazione per i diversi tipi di dispositivo da gestire. Può essere necessario anche [personalizzare il portale aziendale](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) con informazioni di supporto e branding dell'azienda per offrire un'esperienza di registrazione e supporto attendibile agli utenti.

Dopo aver preparato il servizio Intune, il processo di registrazione dei dispositivi per la gestione è immediato, ma leggermente diverso per i vari tipi di dispositivo:

-   **Dispositivi iOS e Mac**. Per registrare iPad, iPhone o dispositivi Mac OS è necessario richiedere un certificato APNs (Apple Push Notification service). Dopo aver [caricato il certificato APNs in Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) è possibile [registrare i dispositivi iOS](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) usando l'app Portale aziendale e usare il sito Web del portale aziendale per [registrare i dispositivi Mac OS](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).

-   **Dispositivi Android**. Non è necessario eseguire alcuna operazione per preparare il servizio Intune per la registrazione dei dispositivi Android. Gli utenti possono [registrare i dispositivi Android](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) per la gestione usando l'app Portale aziendale disponibile in Google Play.

-   **Android for Work**. Per [configurare Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) per dispositivi con Android 5.0 Lollipop e successivi che supportano la gestione dei profili di lavoro con Intune, l'organizzazione deve iscriversi per Android for Work in Google e quindi configurare le impostazioni di Android for Work nel nodo Amministrazione della console di amministrazione di Intune.

-   **Windows Phone e PC Windows**. È consigliabile [impostare un alias DNS per il server di registrazione](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) per rendere più semplice la registrazione dei dispositivi Windows. In alternativa, è possibile [registrare i dispositivi Windows](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) aggiungendo un account aziendale o dell'istituto di istruzione.

> [!TIP]
> È possibile rendere ancora più semplice la registrazione dei dispositivi Windows per gli utenti [abilitando la funzionalità di registrazione automatica](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) in Azure AD (Premium). In questo caso, i dispositivi verranno registrati automaticamente per la gestione con Intune quando un utente aggiunge un account aziendale o dell'istituto di istruzione per registrare il dispositivo personale oppure quando un dispositivo di proprietà dell'azienda viene aggiunto ad Azure AD dell'organizzazione.

### <a name="make-sure-that-managed-devices-comply-with-basic-security-requirements"></a>Verificare che i dispositivi gestiti siano conformi ai requisiti di sicurezza di base

Dopo che gli utenti hanno registrato i dispositivi per la gestione, il personale IT deve assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali siano conformi ai requisiti di sicurezza di base, come l'uso di un PIN per l'accesso ai dispositivi e la crittografia dei dati archiviati nei dispositivi. Un set di regole di questo tipo è definito [criteri di conformità](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

Quando [si creano e si distribuiscono criteri di conformità](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune) a un utente, tutti i dispositivi gestiti da Intune vengono controllati per vedere se sono conformi ai requisiti di sicurezza di base definiti come parte dei criteri BYOD. Dopo che un dispositivo è stato valutato per determinarne la conformità ai criteri, il relativo stato viene comunicato al servizio Intune. In alcuni casi è possibile che agli utenti venga chiesto di correggere le impostazioni non conformi, ad esempio usando un PIN o la crittografia dei dispositivi, ma in altri casi l'app Portale aziendale segnalerà all'utente eventuali problemi di conformità rilevati.

## <a name="provide-access-to-company-resources"></a>Fornire l'accesso alle risorse aziendali

Questa sezione illustra come il personale IT può consentire agli utenti di accedere in modo facile e sicuro alle risorse aziendali della società distribuendo profili di accesso ai dispositivi gestiti e gestendo le app acquistate con Volume Purchase Program.

### <a name="provide-access-to-company-data"></a>Fornire l'accesso ai dati aziendali
La prima cosa che la maggior parte dei dipendenti vuole sul proprio dispositivo mobile è l'accesso alla posta elettronica e ai documenti aziendali. E si aspettano di configurare l'accesso senza procedure complesse e senza doversi rivolgere al supporto tecnico. Con Microsoft Intune è semplice [creare e distribuire le impostazioni di posta elettronica](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) per le app di posta elettronica native preinstallate nei dispositivi mobili usati dall'organizzazione.

> [!NOTE]
> Intune supporta la configurazione di profili di posta elettronica Android for Work per le app di posta elettronica Gmail e Nine Work disponibili in Google Play Store.

Oltre alla posta elettronica, EMS consente di controllare l'accesso e proteggere i dati aziendali locali a cui si accede dall'esterno dei limiti di sicurezza aziendali tradizionali. I profili Microsoft Intune [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune), [VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile) e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari per svolgere le loro attività ovunque si trovino. È anche possibile accedere in modo sicuro alle applicazioni Web e ai servizi dell'azienda ospitati in locale e proteggerli usando il proxy per l'applicazione Azure Active Directory e l'accesso condizionale.

### <a name="manage-volume-purchased-apps"></a>Gestire le app acquistate con Volume Purchase Program
È possibile [distribuire con facilità app degli Store ai dispositivi gestiti](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune) e anche app di destinazione ai dispositivi non gestiti usando il sito Web del portale aziendale, ma Intune consente anche di gestire e distribuire le app acquistate con Volume Purchase Program dall'App Store di iOS e da Windows Store per le aziende. In questo modo, è possibile ridurre il carico amministrativo associato al monitoraggio delle app acquistate con Volume Purchase Program.

> [!TIP]
> È possibile [configurare facilmente Single Sign On (SSO) con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) per consentire agli utenti di accedere ad app con il nome utente di dominio e la password usati in locale. È inoltre possibile [fornire l'accesso basato su Internet alle app Web ospitate in locale](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) usando il proxy per l'applicazione Azure Active Directory.

Con Intune è facile importare le informazioni sui contratti multilicenza da uno dei due App Store, tenere traccia del numero di licenze usate e impedire agli utenti di installare più copie dell'app rispetto a quelle possedute.

-   [Gestire le app acquistate tramite Volume Purchase Program per dispositivi iOS](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune). Per acquistare più licenze per app iOS, è necessario usare [Volume Purchase Program di Apple per le aziende](http://www.apple.com/business/vpp/). A questo scopo, configurare un account VPP di Apple dal sito Web Apple e caricare il token VPP di Apple in Intune. È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

-   [Windows Store per le aziende](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune). In [Windows Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Intune le app acquistate con Volume Purchase Program.

## <a name="protect-company-data"></a>Proteggere i dati aziendali

Intune protegge i dati aziendali tra più livelli di tecnologia. A livello di identità, l'accesso condizionale protegge l'accesso ai servizi consentendo solo l'accesso da dispositivi conformi e gestiti. A livello di applicazione client, la gestione di applicazioni per dispositivi mobili (MAM) consente di evitare la perdita dei dati impedendo lo spostamento dei dati in app o percorsi di archiviazione di dati non protetti e cancellando i dati quando un dispositivo viene smarrito o rubato.

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



<!--HONumber=Feb17_HO2-->


