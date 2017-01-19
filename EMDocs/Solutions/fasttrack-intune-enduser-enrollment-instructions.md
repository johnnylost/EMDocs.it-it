---
title: Istruzioni di registrazione di Intune (versione utente finale) per gli amministratori IT
description: Istruzioni di registrazione di Intune (versione utente finale) per gli amministratori IT
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c13446e-aa31-47df-ad9d-373be7660197
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2342889a686db8a6496c97979cb222af8347241a
ms.openlocfilehash: 698af6701d756beac696648addbef11d709764fa


---

# <a name="end-user-intune-enrollment-instructions-for-it-administrators"></a>Istruzioni di registrazione di Intune (versione utente finale) per gli amministratori IT

Questo documento che contiene istruzioni per la registrazione può essere personalizzato e dato agli utenti per facilitare la registrazione di dispositivi mobili iOS e Android in Microsoft Intune™ (per i dispositivi Windows, vedere Uso del dispositivo Windows con Intune). Si consiglia di copiare le parti di questo documento considerate più appropriate per gli utenti. Ad esempio, si potrebbe voler creare un documento singolo per ogni piattaforma del dispositivo o aggiungere altre catture di schermata.

Oltre a queste istruzioni scritte, è possibile includere collegamenti ipertestuali ai video di Intune (versione utente finale) disponibili nella pagina Web [http://aka.ms/IntuneUserVideos](http://aka.ms/IntuneUserVideos).

> [!NOTE]
> Microsoft, Intune e Office 365 sono marchi registrati di Microsoft Corporation. iPhone, Apple e Mac sono marchi registrati di Apple, Inc. Android è un marchio registrato di Google Inc. Samsung KNOX è un marchio registrato di Samsung Electronics Co., Ltd.

## <a name="why-enroll-in-intune"></a>Perché registrarsi in Intune
Quando se esegue la registrazione, è possibile usare il dispositivo mobile per accedere a dati e file aziendali o dell'istituto di istruzione. Ciò consente al dipartimento IT di gestire e proteggere le risorse aziendali e dell'istituto di istruzione, offrendo allo stesso tempo la possibilità di usare il dispositivo preferito per accedere ai dati.

Per usare il dispositivo al lavoro, registrarlo in Intune tramite il Portale aziendale. È possibile trovare facilmente le app da installare, vedere le altre app aggiunte e trovare le informazioni di contatto dell'amministratore IT. Viene inoltre concessa l'autorizzazione all'amministratore IT di gestire il dispositivo per proteggere le informazioni aziendali usate sul dispositivo. Prima di avviare la registrazione, assicurarsi di avere una buona connessione Wi-Fi o rete cellulare a Internet.

## <a name="enroll-your-android-device-in-intune-using-the-intune-company-portal-app"></a>Registrare il dispositivo Android in Intune tramite l'app Portale aziendale

Queste passaggi sono validi per la registrazione di dispositivi Android Samsung Knox e Android nativi, esclusi i dispositivi Samsung Knox. Per determinare se il dispositivo è di tipo Samsung Knox, aprire **Impostazioni > Informazioni sul telefono**. Se non viene visualizzata la parola Knox qui riportata, significa che il dispositivo è un dispositivo Android nativo. Le schermate che appaiono sul dispositivo potrebbero essere leggermente diverse da quelle illustrate di seguito.

Se si verifica un errore durante la registrazione del dispositivo in Intune, vedere [Inviare gli errori di registrazione all'amministratore IT](https://technet.microsoft.com/en-US/library/mt502762(TechNet.10).aspx#BKMK_andr_send_enroll_errors).

Prima o dopo la registrazione potrebbe essere necessario scegliere la categoria che descrive meglio come viene usato il dispositivo. L'amministratore IT usa questa categoria per determinare a quali app ha accesso l'utente.
1.  Installare l'app gratuita Portale aziendale di Microsoft Intune nel dispositivo da [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Aprire l'app Portale aziendale di Microsoft Intune.
3.  Nella **schermata iniziale** del portale aziendale toccare **Accedi** e quindi accedere con l'account aziendale o dell'istituto di istruzione.

  ![Cattura di schermata che illustra la schermata di accesso al Portale aziendale di Intune in un dispositivo Android](./media/ft-userEnrollAndroid-1-signUp.png)

4.  Se l'amministratore IT ha impostato i termini e le condizioni aziendali, toccare **ACCETTO** per accettarli.

  ![Cattura di schermata nella quale si richiede all'utente di accettare i termini e le condizioni in un dispositivo Android](./media/ft-userEnrollAndroid-2-accept.png)
5.  Se si usa un dispositivo Android 6.0 o versioni successive, eseguire questo passaggio; altrimenti andare al passaggio successivo.

  Se l'amministratore IT ha configurato determinati criteri, è possibile che venga visualizzato uno dei due messaggi seguenti o entrambi:

  - Se viene visualizzato il messaggio **Allow Company Portal to access your contacts? (Consentire al Portale aziendale di accedere ai contatti)**, toccare **ALLOW (Consenti)**. Scegliere questa opzione perché Microsoft non accede mai ai contatti. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si concede l'accesso, l'app Portale aziendale può accedere ai registri dei dati per risolvere problemi riguardanti il dispositivo.

        ![Screenshot in cui viene chiesto all'utente di consentire al portale di accedere ai contatti in un dispositivo Android](./media/ft-userEnrollAndroid-3-accessContacts.png)
  - Se viene visualizzato il messaggio **Allow Company Portal to make and manage phone calls? (Consentire al portale aziendale di telefonare e gestire le chiamate)**, toccare **ALLOW (Consenti)**. Scegliere questa opzione perché Microsoft non effettua né gestisce le chiamate telefoniche. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si consente l'accesso, l'app Portale aziendale può solo visualizzare il numero di telefono e un ID IMEI.

        ![Screenshot in cui viene chiesto all'utente di consentire al portale di gestire le telefonate in un dispositivo Android](./media/ft-userEnrollAndroid-4-manageCalls.png)

  Se si tocca **DECLINE (Rifiuta)**, i messaggi vengono visualizzati di nuovo al prossimo accesso all'app Portale aziendale; è possibile disattivare la visualizzazione di messaggi toccando la casella di controllo **Never ask again (Non visualizzare più questo messaggio)**. Se successivamente si decide di consentire l'accesso, andare a **Impostazioni > App > Portale aziendale > Autorizzazioni > Telefono** e attivare l'autorizzazione.
6.  Accedere all'app Portale aziendale usando l'account e la password aziendale o dell'istituto di istruzione e quindi toccare **Accedi**.

  ![Cattura di schermata nella quale si richiede all'utente di accedere al Portale aziendale in un dispositivo Android](./media/ft-userEnrollAndroid-5-signIn.png)
7.  Nella pagina Configurazione dell'accesso aziendale toccare **INIZIA**.

  ![Cattura di schermata che illustra la pagina Configurazione dell'accesso aziendale in un dispositivo Android](./media/ft-userEnrollAndroid-6-beginSetup.png)
8.  Leggere le informazioni sulle operazioni che possono essere eseguite quando si registra un dispositivo, quindi toccare **CONTINUA**.

  ![Cattura di schermata che illustra informazioni sui motivi per i quali si dovrebbe registrare un Android](./media/ft-userEnrollAndroid-7-whyEnroll.png)
9.  Vedere l'elenco degli elementi che l'amministratore IT può o meno visualizzare nel dispositivo registrato e toccare **CONTINUA**.

  ![Cattura di schermata che illustra l'informativa sulla privacy in un dispositivo Android](./media/ft-userEnrollAndroid-8-privacy.png)
10. Rivedere alcuni degli elementi che potrebbero essere visualizzati quando si tocca Registra. Al termine, toccare **REGISTRA**.

  ![Cattura di schermata che illustra i passaggi di registrazione successivi in un dispositivo Android](./media/ft-userEnrollAndroid-9-whatNext.png)
11. Nella schermata relativa all'attivazione dell'amministratore del dispositivo toccare **ATTIVA**.

  ![Cattura di schermata nella quale si richiede all'utente di attivare l'amministratore del dispositivo in un dispositivo Android](./media/ft-userEnrollAndroid-10-activateAdmin.png)
12. Seguire le istruzioni per immettere un PIN o una password. Se sul dispositivo è già stato impostato un PIN o una password, questa schermata non verrà visualizzata o verrà richiesto di immettere un nuovo PIN o una nuova password.

  ![Cattura di schermata nella quale si richiede all'utente di immettere il PIN in un dispositivo Android](./media/ft-userEnrollAndroid-11-enterPIN.png)
13. Seguire le istruzioni seguenti relative al tipo di dispositivo in uso, ossia Android nativo o Samsung Knox. Se non si ha un dispositivo Samsung Knox, seguire le istruzioni per Android nativo. Per determinare se il dispositivo è di tipo Samsung Knox, aprire **Impostazioni > Informazioni sul telefono**. Se non viene visualizzata la parola Knox qui riportata, significa che il dispositivo è un dispositivo Android nativo.
 - Dispositivo nativo, non Samsung Knox: nella schermata **Name the certificate (Assegna nome al certificato)** toccare **OK** per accettare il certificato predefinito.

        ![Screenshot prompting the user to accept the default certificate on a native Android device](./media/ft-userEnrollAndroid-12-android.png)
 - Dispositivo Samsung KNOX: toccare **CONFERMA**

        ![Screenshot prompting the user to confirm the privacy policy for a Samsung Knox device](./media/ft-userEnrollAndroid-13-knox.png)

 Mentre Intune registra il dispositivo, viene visualizzato il messaggio seguente.

  ![Cattura di schermata che illustra la notifica che il dispositivo Android è registrato](./media/ft-userEnrollAndroid-14-enrollingDevice.png)
14.  Nella schermata **Configurazione dell'accesso aziendale** toccare **CONTINUA**. Se l'amministratore IT ha impostato altri requisiti di sicurezza, ad esempio la necessità di impostare una password, seguire le istruzioni visualizzate e toccare **CONTINUA** quando si è di nuovo nella schermata Configurazione dell'accesso aziendale.

  ![Cattura di schermata che illustra la notifica che il dispositivo Android è conforme e richiede all'utente di continuare](./media/ft-userEnrollAndroid-15-coAccessSetup.png)
15. Toccare **FINE**.

  ![Screenshot che illustra il completamento della configurazione dell'accesso aziendale in un dispositivo Android](./media/ft-userEnrollAndroid-16-SetupComplete.png)
16. Il dispositivo è ora registrato in Intune e si riapre l'app Portale aziendale.
17. Prima di installare app aziendali, andare in **Impostazioni > Sicurezza** e attivare **Origini sconosciute**. Se non si attiva questa opzione prima di installare le app, viene visualizzato un messaggio che indica che l'installazione è bloccata. per motivi di sicurezza che impediscono di installare nel telefono app ottenute da origini sconosciute. È possibile toccare **Impostazioni** nella finestra di dialogo di errore per visualizzare l'opzione **Origini sconosciute**.

## <a name="enroll-your-ios-device-in-intune"></a>Registrare il dispositivo iOS in Intune
Usare queste istruzioni per registrare il dispositivo iOS in Intune. Per altre informazioni, vedere [Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune?](https://technet.microsoft.com/library/mt598622(TechNet.10).aspx#BKMK_ios_what_happ_enroll) Se si verifica un errore durante la registrazione del dispositivo in Intune, vedere [Inviare gli errori di registrazione all'amministratore IT](https://technet.microsoft.com/library/mt598622(TechNet.10).aspx#BKMK_ios_error_enrolling_tbl).

Prima o dopo la registrazione potrebbe essere necessario scegliere la categoria che descrive meglio come viene usato il dispositivo. L'amministratore IT usa questa categoria per determinare a quali app ha accesso l'utente.
1.  Installare l'app gratuita Portale aziendale di Microsoft Intune nel dispositivo da App Store.
2.  Aprire l'app Portale aziendale di Microsoft Intune.
3.  Nella **schermata iniziale** del portale aziendale toccare **Accedi** e quindi accedere con l'account aziendale o dell'istituto di istruzione.

  ![Cattura di schermata che mostra la schermata di accesso al Portale aziendale di Intune su un dispositivo iOS](./media/ft-userEnrollIOS-1-signUp.png)
4.  Se l'amministratore IT ha impostato i termini e le condizioni aziendali, toccare **ACCETTO** per accettarli.
5.  Nella pagina Configurazione dell'accesso aziendale toccare **Inizia**.

  ![Cattura di schermata nella quale si richiede all'utente di avviare il processo di registrazione in un dispositivo iOS](./media/ft-userEnrollIOS-2-coAccessSetup.png)
6.  Leggere le informazioni sulle operazioni che possono essere eseguite quando si registra un dispositivo, quindi toccare **Continua**.

  ![Cattura di schermata che illustra informazioni sui motivi per i quali si dovrebbe registrare un dispositivo iOS](./media/ft-userEnrollIOS-3-whyEnroll.png)
7.  Vedere l'elenco degli elementi che l'amministratore IT può o meno visualizzare nel dispositivo registrato e toccare **Continua**.

  ![Cattura di schermata che illustra l'informativa sulla privacy in un dispositivo iOS](./media/ft-userEnrollIOS-4-privacy.png)
8.  Rivedere alcuni degli elementi che potrebbero essere visualizzati quando si tocca Registra. Al termine, toccare **Registra**.

  ![Cattura di schermata che illustra i passaggi di registrazione successivi in un dispositivo iOS](./media/ft-userEnrollIOS-5-whatNext.png)
9.  Nella schermata Installa profilo toccare **Installa** e, se richiesto, immettere il passcode.

  ![Cattura di schermata nella quale si richiede all'utente di installare il profilo di gestione di un dispositivo iOS](./media/ft-userEnrollIOS-6-installProfile.png)
10. Toccare **Installa**.

  ![Cattura di schermata nella quale si richiede all'utente di toccare il pulsante Installa per installare il profilo in un dispositivo iOS](./media/ft-userEnrollIOS-7-tapInstall.png)
11. Toccare **Installa** per indicare che il messaggio di avviso è stato letto.

  ![Cattura di schermata nella quale si richiede all'utente di indicare che ha letto l'avviso di gestione del profilo in un dispositivo iOS](./media/ft-userEnrollIOS-8-readWarning.png)
12. Toccare **Attendibilità**.

  ![Cattura di schermata nella quale si richiede all'utente di verificare l'origine del profilo in un dispositivo iOS](./media/ft-userEnrollIOS-9-tapTrust.png)
13. Quando la schermata indica che il profilo è stato installato, toccare **Fine**. Viene visualizzato un messaggio che indica la registrazione in corso del dispositivo.

  ![Cattura di schermata che illustra che il profilo è installato in un dispositivo iOS](./media/ft-userEnrollIOS-10-profileInstalled.png)
14. Quando viene visualizzato un messaggio che chiede se si vuole aprire la pagina nel Portale aziendale, toccare **Apri**.

  ![Cattura di schermata nella quale si richiede all'utente di aprire la pagina del Portale aziendale in un dispositivo iOS](./media/ft-userEnrollIOS-11-openPage.png)
- Nella schermata Configurazione accesso aziendale toccare **Continua**. Se l'amministratore IT ha impostato altri requisiti di sicurezza, ad esempio la necessità di impostare una password, seguire le istruzioni visualizzate fino a soddisfare tutti i requisiti di conformità e toccare **Continua** quando si è di nuovo nella schermata Configurazione dell'accesso aziendale.

  ![Cattura di schermata che illustra la notifica che il dispositivo iOS è conforme e richiede all'utente di continuare](./media/ft-userEnrollIOS-12-coAccessSetup.png)
15. Toccare **Fine**.

  ![Cattura di schermata che illustra il completamento della configurazione dell'accesso aziendale in un dispositivo iOS](./media/ft-userEnrollIOS-13-setupComplete.png)

Il dispositivo è ora registrato in Intune e si riapre l'app Portale aziendale.

## <a name="enroll-your-mac-os-x-device-in-intune"></a>Registrare il dispositivo Mac OS X in Intune
1.  Aprire il [sito Web del portale aziendale](https://portal.manage.microsoft.com/) con un browser Safari e toccare la barra di notifica.
2.  Toccare **Il dispositivo non è registrato oppure il Portale aziendale non riesce a identificarlo**.

  ![Cattura di schermata che illustra che il portale aziendale non può identificare un dispositivo Mac OS X](./media/ft-userEnrollMacOSx-1-enrollBegin.png)
3.  Toccare **Installa** per iniziare la registrazione del dispositivo.

  ![Cattura di schermata nella quale si richiede all'utente di registrare il dispositivo Mac OS X](./media/ft-userEnrollMacOSx-2-enrollDevice.png)
4.  Nella finestra di dialogo Install Management Profile (Installa profilo di gestione) toccare **Installa**. Se viene visualizzata una finestra di dialogo in cui viene richiesto di immettere le credenziali, digitare il nome utente e la password e toccare **Continua > Installa**.

  ![Schermata che richiede all'utente di installare il profilo di gestione in un dispositivo Mac OS X](./media/ft-userEnrollMacOSx-3-installProfile.png)

Al termine della registrazione, verrà visualizzata una pagina con il profilo di gestione che mostra che il profilo è stato verificato.

  ![Cattura di schermata che illustra che il profilo di gestione è verificato in un dispositivo di Mac OS X](./media/ft-userEnrollMacOSx-4-profileVerified.png)

### <a name="want-to-learn-more"></a>Altre informazioni
Vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).



<!--HONumber=Jan17_HO1-->


