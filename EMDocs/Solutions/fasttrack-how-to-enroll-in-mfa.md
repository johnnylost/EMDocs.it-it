---
title: "Come registrarsi con autenticazione a più fattori"
description: Come configurare il metodo preferito per la verifica aggiuntiva di sicurezza
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06e21ca9-ed6a-4f6e-a7e2-5445aaeb3552
ms.reviewer: 
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 66be84d00e73f98217abfb2537bb52ebac94727a
ms.openlocfilehash: 7120b4ce41e0f9560bdecb3a98da0bd02171fabb
ms.contentlocale: it-it
ms.lasthandoff: 05/29/2017


---

# <a name="how-to-set-up-your-preferred-method-for-additional-security-verification"></a>Come configurare il metodo preferito per la verifica aggiuntiva di sicurezza



È possibile definire le impostazioni per la verifica aggiuntiva di sicurezza quando l'amministratore ha configurato l'account in modo da richiedere sia una password sia una risposta dal telefono dell'utente per verificarne l'identità. Se un amministratore ha configurato l'account in modo da richiedere una verifica aggiuntiva di sicurezza, non è possibile accedere fino al completamento del processo di autoregistrazione.

La prima volta che si accede dopo la configurazione dell'account, viene richiesto di avviare il processo di autoregistrazione. È possibile iniziare questo processo facendo clic su Set it up now.

![Cattura di schermata nella quale si richiede all'utente di registrarsi con verifica aggiuntiva di sicurezza per l'account](./media/ft-enrollMFA-1-beginProcess.png)

Tramite il processo di registrazione è possibile specificare il metodo preferito di verifica dell'identità. È possibile scegliere tra uno dei metodi elencati nella tabella di seguito. Per altre informazioni, inclusa una procedura dettagliata, è sufficiente fare clic sul metodo.


|Metodo|Descrizione|
|------------|----------------------------------|
|[Chiamata al telefono cellulare](#mobile-phone)|Invia una chiamata vocale automatizzata al numero di telefono di autenticazione. L'utente risponde e preme # sul tastierino telefonico per l'autenticazione. Questo numero di telefono non verrà sincronizzato con l'istanza locale di Active Directory.|
|[SMS al cellulare](#mobile-phone)|Invia all'utente un SMS che include un codice di verifica. All'utente viene richiesto di rispondere all'SMS con il codice di verifica oppure di digitare il codice di verifica nell'interfaccia di accesso.|
|[Chiamata al telefono dell'ufficio](#office-phone-call)|avvia una chiamata vocale automatizzata all'utente. L'utente risponde e preme # sul tastierino telefonico per l'autenticazione.|
|[App per dispositivi mobili](#mobile-application)|Invia una notifica all'app Azure Authenticator per dispositivi mobili sullo smartphone o sul tablet dell'utente. L'utente tocca Verifica nell'app per l'autenticazione. In alternativa, l'app può essere usata anche come token OTP per l'autenticazione offline. L'utente immette il token nella schermata di accesso per l'autenticazione.|

_L'app Azure Authenticator può funzionare in due modi diversi per offrire la sicurezza aggiuntiva di un servizio di autenticazione a più fattori. Sono disponibili le seguenti modalità:_

- **Notifica**: in questa modalità l'app Azure Authenticator impedisce l'accesso non autorizzato agli account e nega le transazioni illecite. Questa operazione viene eseguita inviando una notifica push al telefono o al dispositivo registrato. È sufficiente visualizzare la notifica e, se legittima, scegliere **Esegui autenticazione**. In alternativa, è possibile scegliere **Nega** oppure Nega e segnala illecito. Per informazioni sulle notifiche per la segnalazione di illeciti, vedere la pagina relativa all'uso della funzionalità Nega e segnala illecito per Multi-Factor Authentication.
- **Password monouso**: in questa modalità l'app Azure Authenticator può essere usata come un token di software per generare un codice di verifica OATH. È quindi possibile digitare il codice di verifica con il nome utente e la password per specificare la seconda forma di autenticazione.

L'app Azure Authenticator è disponibile per [Windows Phone](http://www.windowsphone.com/en-us/store/app/azure-authenticator/03a5b2bf-6066-418f-b569-e8aecbc06e50), [Android](https://play.google.com/store/apps/details?id=com.azure.authenticator) e [IOS](https://itunes.apple.com/us/app/azure-authenticator/id983156458).

## <a name="mobile-phone"></a>Cellulare
Se si vuole usare il telefono cellulare (per testo o chiamata) come metodo di contatto principale, seguire i passaggi descritti di seguito. Vengono offerte informazioni dettagliate su come impostare un'autenticazione a più fattori per usare il telefono cellulare come metodo di contatto tramite una telefonata o un SMS .

1. In **Passaggio 1: How should we contact you? (Metodo di contatto)** selezionare **Telefono per l'autenticazione**.

  ![Cattura di schermata che illustra un utente che vuole essere contattato tramite telefono](./media/ft-enrollMFA-2-securityVerification.png)
2.    Nella casella **Paese o regione** selezionare un valore dall'elenco a discesa. Un valore predefinito potrebbe già essere visualizzato.
3.    Nella casella accanto alla casella **Paese o regione** digitare il numero di telefono cellulare. Includere il prefisso.
Gli spazi sono consentiti, ma non i caratteri di punteggiatura. Ad esempio, numeri di telefono quali 5554445555 e 555 444 5555 sono consentiti, ma 555-444-5555 e (555) 444 5555 non sono consentiti.
4.    Selezionare la modalità d'uso preferita per il telefono cellulare: SMS o chiamata.
5.    Fare clic su **Avanti**.
6.    Fare clic sul pulsante **Verifica ora**. Verrà avviata una chiamata oppure verrà inviato un SMS al telefono cellulare. Assicurarsi che il telefono sia acceso. A seconda della modalità selezionata, SMS o telefonata, la risposta sarà diversa.
 - Se è stata selezionata la modalità SMS, verrà inviato un codice di 6 cifre via SMS. Immettere questo codice nella casella visualizzata nel browser.

        ![Screenshot asking user to enter the code that was texted to them](./media/ft-enrollMFA-3-textCode.png)
 - Se è stata seleziona la modalità Telefonata, si riceverà una telefonata. Rispondere usando il simbolo # sul telefono.

        ![Screenshot prompting user to answer their phone to continue enrollment process](./media/ft-enrollMFA-4-phoneCode.png)
7. Fare clic su **Avanti**.
8.    A questo punto è stato impostato il metodo di contatto ed è necessario impostare le password per le app non basate su browser, ad esempio Outlook 2010 o versione precedente. Se non si usano queste app, fare clic su **Operazione completata**. In caso contrario, **continuare** con il passaggio successivo.
9. Se si usano queste app **copiare** la password dell'app specificata.

  ![Cattura di schermata nella quale si richiede all'utente di digitare la password dell'app](./media/ft-enrollMFA-5-copyPW.png)
10.    Incollare nell'applicazione non basata su browser la password che è stata copiata negli Appunti.
11.    Fare clic su **Fine**.

## <a name="office-phone-call"></a>Chiamata al telefono dell'ufficio
Questa sezione illustra come impostare Azure Multi-Factor Authentication per usare il telefono dell'ufficio come metodo di contatto principale.
1. Selezionare Telefono ufficio dall'elenco a discesa.

  ![Cattura di schermata che illustra un utente che vuole essere contattato tramite il telefono dell'ufficio](./media/ft-enrollMFA-6-officePhone.png)
2.    Specificare il paese dall'elenco a discesa e digitare il numero di telefono dell'ufficio.
3.    Fare clic su **Contact Me**. Verrà avviata una chiamata al telefono dell'ufficio. Assicurarsi di essere vicino al telefono.
4.    Fare clic su **Avanti**.
5.    A questo punto è stato impostato il metodo di contatto ed è necessario impostare le password per le app non basate su browser, ad esempio Outlook 2010 o versione precedente. Se non si usano queste app, fare clic su **Operazione completata**. In caso contrario, **continuare** con il passaggio successivo.
7.    Se si usano queste app, copiare la password dell'app specificata.
8.    Incollare nell'applicazione non basata su browser la password che è stata copiata negli Appunti.

  ![Cattura di schermata nella quale si richiede all'utente di digitare la password dell'app](./media/ft-enrollMFA-7-pastePW.png)
9.    Fare clic su **Fine**.

## <a name="mobile-application"></a>Applicazione per dispositivi mobili
Questa sezione illustra come impostare Azure Multi-Factor Authentication per usare l'app per dispositivi mobili come metodo di contatto principale.

L'app Azure Authenticator è disponibile per Windows Phone, Android e IOS.

1. Selezionare **App per dispositivi mobili** dall'elenco a discesa.

  ![Cattura di schermata che illustra un utente che vuole essere contattato tramite un'app per dispositivi mobili](./media/ft-enrollMFA-8-mobileApp.png)
2.    Selezionare Notifica o Password monouso e fare clic su **Imposta**.
3.    Sul telefono in cui è installata l'app Azure Authenticator, avviare l'applicazione e fare clic su **Acquisizione del codice a barre**.

  ![Cattura di schermata nella quale si richiede all'utente di selezionare l'opzione di acquisizione del codice a barre](./media/ft-enrollMFA-9-scanBarcode.png)
4.    Effettuare la scansione dell'immagine del codice a barre visualizzata nella schermata di configurazione dell'app. Fare clic su **Operazione completata** per chiudere la schermata del codice a barre. Se non si è in grado di analizzare il codice a barre, è possibile digitare manualmente le informazioni.

  ![Cattura di schermata nella quale si richiede all'utente di analizzare il codice a barre visualizzato nell'app per dispositivi mobili](./media/ft-enrollMFA-9-scanBarcode2.png)
5.    Sul telefono, inizierà l'attivazione e quando sarà completata, fare clic su **Contact me**. Questa operazione invia una notifica o un codice di verifica al telefono cellulare. Fare clic su **Verifica**.

  ![Cattura di schermata nella quale si richiede all'utente di verificare il codice inviato al telefono](./media/ft-enrollMFA-10-verifyActivation.png)
6.    Fare clic su **Chiudi**. A questo punto, la verifica dovrebbe essere completata.
7.    È necessario adesso specificare il numero di cellulare, nel caso in cui l'app per dispositivi mobili non sia accessibile.
8.    Specificare il paese dall'elenco a discesa e digitare il numero di cellulare nella casella a fianco al Paese. Fare clic su **Avanti**.
9.    A questo punto è stato impostato il metodo di contatto ed è necessario impostare le password per le app non basate su browser, ad esempio Outlook 2010 o versione precedente. Se non si usano queste app, fare clic su **Operazione completata**. In caso contrario, **continuare** con il passaggio successivo.
10.    Se si usano queste app, copiare la password dell'app specificata.
11.    Incollare nell'applicazione non basata su browser la password che è stata copiata negli Appunti.

  ![Cattura di schermata nella quale si richiede all'utente di digitare la password dell'app](./media/ft-enrollMFA-11-securityVerification.png)
12.    Fare clic su **Fine**.

### <a name="want-to-learn-more"></a>Altre informazioni
Vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).

