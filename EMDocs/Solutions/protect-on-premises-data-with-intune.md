---
title: Proteggere i dati locali con Microsoft Intune | Microsoft Docs
description: "Con Enterprise Mobility + Security (EMS) è possibile garantire la produttività dei dipendenti con le app e i dispositivi preferiti, mantenendo allo stesso tempo protetti i dati aziendali locali."
keywords: 
author: jeffgilb
manager: angrobe
ms.date: 6/7/2017
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ebf7be63-4ac2-4158-9772-58f15416ccb7
ms.reviewer: vlpetros
ms.suite: ems
ms.custom: active-directory
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea7cc0c6c7b8286077c0bbc4251a22d138ed8e2
ms.openlocfilehash: 98acda761b353eacb2ce861dcef2f39385691021
ms.contentlocale: it-it
ms.lasthandoff: 05/29/2017


---
# <a name="protect-on-premises-company-data-with-intune"></a>Proteggere i dati aziendali locali con Intune
I firewall da soli non possono più offrire un limite di sicurezza aziendale adeguato. Oggi, i limiti di sicurezza devono includere gli utenti finali e tenere conto delle loro modalità di accesso, uso e condivisione dei dati aziendali. Indipendentemente dal fatto che usino smartphone, tablet o portatili, gli Information Worker si aspettano di poter accedere facilmente alle risorse da qualsiasi posizione, su qualsiasi dispositivo e quando necessario. L'implementazione di funzionalità di accesso e protezione adeguate per gli utenti può rappresentare una sfida per gli amministratori IT che devono anche assicurarsi di garantire la protezione dei dati aziendali. Con Enterprise Mobility + Security (EMS) è possibile garantire la produttività dei dipendenti con le app e i dispositivi preferiti, mantenendo allo stesso tempo protetti i dati aziendali locali. Le informazioni seguenti descrivono in che modo.

## <a name="how-can-enterprise-mobility--security-ems-help-you"></a>Come può essere utile Enterprise Mobility + Security (EMS)?
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. Con EMS, i dipendenti avranno accesso sicuro e trasparente alla posta elettronica e ai documenti aziendali e gli amministratori IT potranno contare sulla protezione dei dati aziendali.

## <a name="recommended-solution"></a>Soluzione consigliata
Con Microsoft Intune è possibile configurare in modalità remota criteri per profili di accesso alle risorse per eseguire il provisioning automatico degli account di posta elettronica, profili di accesso per le impostazioni Wi-Fi o VPN e fornire profili di certificato per assicurarsi che i dispositivi accettino e installino solo le configurazioni attendibili.

Oltre a fornire l'accesso, l'accesso condizionale di Intune a server locali Microsoft Exchange 2010, o versione successiva, garantisce che solo i dispositivi gestiti e conformi possano accedere alla posta elettronica aziendale. Estendendo la gestione oltre i dispositivi stessi, è anche possibile usare Cisco Identity Services Engine (ISE) di Intune, e presto soluzioni di altri partner, per limitare l'accesso alla rete aziendale solo ai dispositivi registrati per la gestione con Intune e conformi ai criteri aziendali. È anche possibile offrire l'accesso sicuro ad applicazioni locali senza VPN, reti perimetrali o proxy inversi locali, sfruttando il proxy per l'applicazione Azure Active Directory. L'aspetto migliore è la possibilità di ottenere tutto ciò senza installare o gestire un'infrastruttura locale aggiuntiva o aprire il firewall aziendale per instradare il traffico.

Il video che segue è un'introduzione rapida di come l'accesso condizionale con EMS possa offrire ai dipendenti un'esperienza facile di accesso sicuro ai dati aziendali da dispositivi iOS, Android e Windows:

<iframe width="675" height="480" src="https://youtube.com/embed/fvCT7Y3nlAY" frameborder="0" allowfullscreen></iframe>

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
Il resto di questa soluzione è suddiviso nelle sezioni seguenti che illustrano come proteggere i dati aziendali di Office 365 con Intune:
- **Registrare dispositivi mobili e PC Windows per la gestione**. Questa sezione descrive come registrare i dispositivi (iOS, Android, Android for Work e PC Windows) per la gestione con Intune, in modo da poter configurare l'accesso sicuro alle risorse locali con Intune.
- **Accedere alla posta elettronica aziendale e proteggerla**. Questa sezione illustra come è possibile usare Intune per configurare automaticamente le impostazioni di posta elettronica delle app native per gli utenti e come fornire l'accesso condizionale a Exchange Server locale.
- **Fornire l'accesso ad altre risorse aziendali locali**. Questa sezione descrive come fornire ai dipendenti l'accesso sicuro alle risorse di rete locali tramite Wi-Fi, VPN o il proxy per l'applicazione Azure Active Directory.
- **Usare i certificati per proteggere l'accesso alle risorse aziendali**. Le informazioni in questa sezione consentono di creare e distribuire un certificato PKCS #12 (PFX) o SCEP (Simple Certificate Enrollment Protocol) per proteggere l'accesso degli utenti alle risorse aziendali.

## <a name="enroll-mobile-devices-and-windows-pcs-into-management"></a>Registrare dispositivi mobili e PC Windows per la gestione
La registrazione dei dispositivi e dei PC per la gestione con Intune garantisce l'applicazione di tutti i criteri e i profili di accesso configurati per i dispositivi gestiti. Per poter registrare i dispositivi, è necessario innanzitutto [preparare il servizio Intune](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) assegnando le licenze agli utenti, impostando l'autorità di gestione dei dispositivi mobili e rispettando i requisiti di registrazione per i diversi tipi di dispositivo da gestire. Può essere necessario anche [personalizzare il portale aziendale](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) con informazioni di supporto e branding dell'azienda per offrire un'esperienza di registrazione e supporto attendibile agli utenti.

Dopo aver preparato il servizio Intune, il processo di registrazione dei dispositivi per la gestione è immediato, ma leggermente diverso per i vari tipi di dispositivo:

-   **Dispositivi iOS e Mac**. È necessario richiedere un certificato APNs (Apple Push Notification service) per registrare iPad, iPhone o dispositivi Mac OS X. Dopo aver [caricato il certificato APNs in Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) è possibile [registrare i dispositivi iOS](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) usando l'app Portale aziendale e usare il sito Web del portale aziendale per [registrare i dispositivi Mac OS X](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).
-   **Dispositivi Android**. Non è necessario eseguire alcuna operazione per preparare il servizio Intune per la registrazione dei dispositivi Android. Gli utenti possono [registrare i dispositivi Android](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) per la gestione usando l'app Portale aziendale disponibile in Google Play.
-   **Android for Work**. Per [configurare Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) per dispositivi con Android 5.0 Lollipop e successivi che supportano la gestione dei profili di lavoro con Intune, l'organizzazione deve iscriversi per Android for Work in Google e quindi configurare le impostazioni di Android for Work nel nodo Amministrazione della console di amministrazione di Intune.
-   **Windows Phone e PC Windows**. È consigliabile [impostare un alias DNS per il server di registrazione](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) per rendere più semplice la registrazione dei dispositivi Windows. In alternativa, è possibile [registrare i dispositivi Windows](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) aggiungendo un account aziendale o dell'istituto di istruzione.

> [!TIP]
> È possibile rendere ancora più semplice la registrazione dei dispositivi Windows per gli utenti [abilitando la funzionalità di registrazione automatica](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) in Azure AD (Premium). In questo caso, i dispositivi verranno registrati automaticamente per la gestione con Intune quando un utente aggiunge un account aziendale o dell'istituto di istruzione per registrare il dispositivo personale oppure quando un dispositivo di proprietà dell'azienda viene aggiunto ad Azure AD dell'organizzazione.

## <a name="access-and-protect-company-email"></a>Accedere alla posta elettronica e proteggerla
La prima cosa che la maggior parte dei dipendenti vuole sul proprio dispositivo mobile è l'accesso alla posta elettronica e ai documenti aziendali. E si aspettano di configurare l'accesso senza procedure complesse e senza doversi rivolgere al supporto tecnico. Con Microsoft Intune è semplice creare e distribuire le impostazioni di posta elettronica per le app di posta elettronica native preinstallate nei dispositivi mobili usati dall'organizzazione.

Usando i criteri di accesso condizionale di Intune per Exchange in locale è possibile assicurarsi che solo i dispositivi gestiti e conformi ai criteri registrati in Azure Active Directory possano accedere alle informazioni di Exchange Server locali dell'azienda.

### <a name="configure-exchange-email-settings-for-native-email-apps-on-managed-devices"></a>Configurare le impostazioni di posta elettronica di Exchange per le app di posta elettronica native nei dispositivi gestiti
È possibile [configurare le impostazioni delle app di posta elettronica native](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) in modo semplice nei dispositivi seguenti tramite la creazione di criteri di configurazione dei profili di posta elettronica e la loro distribuzione agli utenti:

-   Windows Phone (8 e versioni successive)
-   Windows 10 Desktop e Mobile
-   iOS 8.0 (e versioni successive)
-   Android (Samsung KNOX Standard 4.0 e versioni successive o Android for Work)

> [!NOTE]
> Intune supporta la configurazione di profili di posta elettronica Android for Work per le app di posta elettronica Gmail e Nine Work disponibili in Google Play Store.

### <a name="protect-access-to-your-on-premises-exchange-server"></a>Proteggere l'accesso a Exchange Server locale
Oltre a usare Intune per fornire le impostazioni di configurazione della posta elettronica per connettersi a server Exchange locali, è anche possibile usare Intune per [controllare l'accesso alla posta elettronica per un server Exchange locale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune) (2010 o versione successiva) tramite [On-Premises Exchange Connector](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector) di Intune.

Se un dispositivo non è registrato o non è conforme ai criteri aziendali, all'utente vengono presentate informazioni su come registrare il dispositivo per la gestione e come risolvere i problemi di conformità che impediscono l'accesso alla posta elettronica.

> [!TIP]
> Questi [scenari di esempio](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios#all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune) possono essere utili per trovare altre idee sui possibili usi dell'accesso condizionale di Intune per proteggere la posta elettronica di Exchange aziendale.

È possibile [configurare criteri di accesso condizionale per Exchange locale](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune#configure-a-conditional-access-policy) per i tipi di dispositivi seguenti usati dall'organizzazione:

-   Windows Phone (8.1 e versioni successive)
-   iOS 8.0 (e versioni successive)
-   Android (4.0 o versioni successive e Samsung KNOX Standard 4.0)
-   Android for Work (supportato attualmente solo per i profili di posta elettronica per le app Gmail e Nine Work)
-   Applicazione Posta nei PC Windows gestiti

> [!NOTE]
> I criteri di accesso condizionale di Intune funzionano solo con le applicazioni di posta elettronica native nei dispositivi, ad eccezione delle app di posta elettronica Gmail e Nine Work nel profilo di lavoro per Android for Work. L'app Microsoft Outlook per Android e iOS non è attualmente supportata, ma è previsto che lo sarà in futuro.

## <a name="provide-access-to-other-on-premises-company-resources"></a>Fornire accesso alle altre risorse aziendali locali
Oltre alla posta elettronica, EMS consente di controllare l'accesso e proteggere i dati aziendali locali a cui si accede dall'esterno dei limiti di sicurezza aziendali tradizionali. I profili Microsoft Intune Wi-Fi, VPN e di posta elettronica interagiscono per consentire agli utenti di accedere ai file e alle risorse necessari, mettendoli in grado di svolgere le loro attività ovunque si trovino. È anche possibile accedere in modo sicuro alle applicazioni Web e ai servizi dell'azienda ospitati in locale e proteggerli usando il proxy per l'applicazione Azure Active Directory e l'accesso condizionale.

### <a name="deploy-wi-fi-settings-to-managed-devices"></a>Distribuire le impostazioni Wi-Fi ai dispositivi gestiti
Con i criteri di configurazione Wi-Fi di Intune è semplice [distribuire le impostazioni per la rete wireless agli utenti](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune). Grazie a queste impostazioni, gli utenti possono connettersi facilmente alla rete aziendale senza configurare manualmente le impostazioni Wi-Fi in uno dei seguenti dispositivi supportati:

-   Android (4.0 e versioni successive, Samsung KNOX Standard e Android for Work)<sup>1</sup>
-   iOS (8.0 e versioni successive)<sup>1</sup>
-   Mac OS X (10.9 e versioni successive)<sup>1</sup>
-   Dispositivi Windows (PC Windows 8.1 e versioni successive, Windows Phone 8.1 o Windows 10 Mobile e versioni successive)<sup>2</sup>

> <sup>1</sup>È possibile usare un criterio di configurazione Wi-Fi di Intune predefinito.

> <sup>2</sup>È possibile [importare un profilo di configurazione XML di impostazioni Wi-Fi esportato in precedenza](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

### <a name="deploy-vpn-settings-to-managed-devices"></a>Distribuire le impostazioni VPN ai dispositivi gestiti
Le connessioni VPN vengono usate quando gli utenti devono connettersi in modalità remota alle risorse aziendali con i dispositivi mobili. Con Intune, è possibile [creare e distribuire profili di configurazione VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile) che consentono agli utenti di accedere alle risorse della rete aziendale in modo facile e sicuro, senza dover configurare manualmente le informazioni sul server VPN o il metodo di autenticazione.

È possibile configurare le impostazioni VPN per i molti [tipi di connessione VPN supportati da Intune](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#vpn-connection-types) nei seguenti tipi di dispositivi:

-   Android (4.0 e versioni successive, Samsung KNOX Standard e versioni successive e Android for Work)
-   iOS 8.0 (e versioni successive)
-   Mac OS X (10.9 e versioni successive)
-   Dispositivi Windows (PC Windows 8.1 e versioni successive, Windows Phone 8.1 e Windows 10 Mobile e versioni successive)

### <a name="protect-network-access"></a>Proteggere l'accesso alla rete
Così come è possibile consentire l'accesso alle informazioni di Exchange dell'azienda solo ai dispositivi gestiti e conformi, è possibile usare i criteri di rete [Cisco Identity Services Engine (ISE)](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_00.html) per proteggere l'accesso all'ambiente di rete. Cisco ISE è un sistema di controllo dell'accesso alla rete basato su criteri che può essere distribuito in infrastrutture aziendali che supportano reti 802.1X cablate, wireless e VPN.

Anziché configurare le impostazioni nella console di amministrazione di Intune, l'accesso dei dispositivi alle reti gestite con Cisco ISE viene configurato nel server Cisco ISE. È sufficiente [concedere al server Cisco ISE le autorizzazioni per l'accesso al tenant Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-networks) e quindi usare i criteri Cisco ISE per consentire l'accesso all'ambiente di rete solo ai dispositivi gestiti e conformi.

> [!IMPORTANT]
> Per usare questo sistema di protezione sono necessarie [licenze di Cisco ISE](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_0110.html), non incluse in EMS.

È anche possibile abilitare l'accesso Single Sign-On (SSO) e l'accesso condizionale per proteggere l'accesso remoto per le applicazioni Web ospitate in locale con il proxy per l'applicazione Azure AD. Grazie al proxy per l'applicazione Azure AD, gli utenti possono accedere in modo semplice alle applicazioni Web ospitate in locale, come siti di SharePoint, Outlook Web Access o altre applicazioni Web LOB senza dover ricorrere a una VPN. È anche possibile proteggere le connessioni alle API Web per supportare dispositivi e app diversi ospitati dietro un Gateway Desktop remoto.

La [configurazione del proxy per l'applicazione Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-enable) è un'operazione semplice. È sufficiente abilitare la funzionalità in Azure AD (Basic o Premium), installare un piccolo servizio di Windows Server chiamato connettore all'interno della rete e quindi pubblicare le applicazioni. Non è necessario aprire le porte del firewall in entrata o inserire altro in una rete perimetrale. Dopo aver completato la configurazione, l'accesso alle applicazioni Web locali avviene tramite Single Sign-On ad Azure AD. Le [regole di accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-conditional-access), come ad esempio richiedere l'autenticazione a più fattori o bloccare l'accesso quando i dipendenti non sono al lavoro, offrono misure di sicurezza aggiuntive.

## <a name="use-certificates-to-secure-company-resource-access"></a>Usare i certificati per proteggere l'accesso alle risorse aziendali
Quando si concede agli utenti l'accesso alle risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica, è possibile [proteggere tale accesso con un certificato](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles) installato in ogni dispositivo utente, invece di dipendere dalla semplice coppia nome utente/password per l'autenticazione.

È possibile creare e distribuire un profilo certificato **PKCS #12 (PFX)** o **SCEP (Simple Certificate Enrollment Protocol)** che può essere usato dai dispositivi che richiedono certificati di autenticazione su queste piattaforme per dispositivi:

-   iOS 8.0 (e versioni successive)
-   Mac OS X (10.9 e versioni successive)
-   Android (4.0 e versioni successive e Android for Work)
-   Windows (8.1 e versioni successive)
-   Windows Phone (8.1 e versioni successive)
-   Windows 10 (per dispositivi desktop e mobili) e versioni successive

Anche se è necessaria un'autorità di certificazione globale (enterprise) per gestire l'autenticazione basata su certificati per l'azienda, esistono altri prerequisiti che devono essere soddisfatti prima di poter usare certificati SCEP o PFX per proteggere l'accesso alle risorse aziendali.

-   Prima di poter usare Intune per creare e distribuire profili certificato SCEP, è necessario [configurare l'infrastruttura dei certificati per SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep). Questo passaggio richiede la configurazione di alcuni server locali, inclusi un server autorità di certificazione globale (enterprise), un server Registrazione dispositivi di rete (NDES) e il server Connettore di certificati di Microsoft Intune.
-   Per usare i [profili certificato PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx) (certificati attendibili per i dispositivi mobili), oltre all'autorità di certificazione globale (enterprise) è necessario il Connettore di certificati di Intune (installabile nella CA). Il server NDES non è richiesto.

> [!NOTE]
> L'uso di un server proxy applicazione Web (WAP) è facoltativo sia per i certificati SCEP che PFX per consentire ai dispositivi ricevere e rinnovare i certificati tramite una connessione Internet.

Quando si [distribuiscono i profili certificato](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles) agli utenti, il certificato CA attendibile viene installato nel dispositivo degli utenti. Il dispositivo usa quindi il profilo certificato SCEP o PFX per creare una richiesta di certificato per se stesso. Quando viene completata la richiesta di certificato, è possibile usare i certificati per autenticare i criteri di configurazione dei profili Wi-Fi, VPN e di posta elettronica selezionando l'opzione per il metodo di autenticazione dei criteri basato sui certificati (anziché nome utente e password).

### <a name="learn-more"></a>Altre informazioni

[Iniziare a usare Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)

