---
# required metadata

title: Esperienza utente finale di accesso condizionale nei dispositivi Android
description:
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 3e186dd2-e17c-40d8-b160-48038b2c6593

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Android

Il processo di registrazione e le schermate visualizzate dall'utente saranno leggermente diverse a seconda della versione del sistema operativo in esecuzione sul dispositivo dell'utente finale. In questo argomento viene descritta l'esperienza dell'utente finale per i dispositivi Android.

## Registrazione

1.  Quando prova ad accedere alla posta elettronica, l'utente riceve un messaggio di posta elettronica di quarantena simile all'esempio seguente:

    ![](./media/ProtectEmail/EUX-Android-quarantine-Email.png)

    L'utente fa clic su **Per iniziare** per iniziare a registrare il dispositivo.

    > [!NOTE]
    > Se un utente non ha impostato un browser predefinito per il dispositivo, verrà richiesto durante la registrazione del dispositivo e durante l'attivazione della registrazione per consentire a un collegamento di aprire una finestra del browser. Quando richiesto, l'utente dovrà selezionare lo stesso browser ogni volta oppure il processo di registrazione non riuscirà.

2.  All'utente viene richiesto di installare l'app Portale aziendale di Intune dall'App Store corrispondente.

    ![](./media/ProtectEmail/EUX-Android-Portal.png)

    Dopo l'installazione, l'utente apre l'app ed esegue l'accesso con le credenziali della società.

3.  Nella schermata Configurazione dell'accesso aziendale, l'utente fa clic su **Inizia** per cominciare a configurare il dispositivo e verificarne la conformità.

    ![](./media/ProtectEmail/EUX-Android-company-Access-Setup.PNG)

4.  Nella schermata Registrazione del dispositivo, l'utente fa clic su **Registra** per iniziare a registrare il suo dispositivo.

    ![](./media/ProtectEmail/EUX-Android-device-Enroll.png)

5.  Gli utenti devono attivare l'amministratore del dispositivo facendo clic su **Attiva** quando richiesto oppure la procedura di registrazione del dispositivo verrà annullata.

    ![](./media/ProtectEmail/EUX-Android-activate-DeviceAdmin.PNG)

    Inizia la registrazione del dispositivo. A seconda del dispositivo, durante la registrazione potrebbe essere visualizzata una richiesta di installazione del certificato o un prompt con l'informativa sulla privacy di Samsung KNOX. Questi sono necessari per consentire all'amministratore IT di gestire in remoto il dispositivo. Il dispositivo è registrato in Intune e stabilisce un'identità del dispositivo con Azure Active Directory.

    ![](./media/ProtectEmail/EUX-Android-enrolling-Device.png)

6.  Dopo il corretto completamento della registrazione, l'utente fa clic su **Continua** per iniziare a verificare la conformità nel dispositivo.

    ![](./media/ProtectEmail/EUX-Android-enroll-Success.png)

    Se si verifica un problema di conformità, all'utente viene richiesto di risolvere il problema (ad esempio creando una password valida) e quindi di fare clic su **Controlla conformità** per continuare.

    ![](./media/ProtectEmail/EUX-Android-resolve-Compliance-Issues.png)

7.  Quando il dispositivo sarà completamente compatibile, l'utente fa clic su **Continua** per iniziare l'attivazione della registrazione. L'identità del dispositivo AAD verrà connessa all'ID EAS fornito da Exchange.

    > [!NOTE]
    > In Android, il browser predefinito verrà visualizzato per pochi secondi durante l'attivazione della registrazione. Se l'utente non ha già selezionato un browser predefinito, verrà richiesto di scegliere un browser. Durante il completamento della Configurazione dell'accesso aziendale, l'utente dovrà selezionare lo stesso browser dell'utente ogni volta che viene richiesto.

    ![](./media/ProtectEmail/EUX-Android-compliance-Successful.PNG)

8.  L'attivazione della registrazione verrà completata e l'utente fa clic **Fine** per uscire dal processo di verifica della registrazione e della conformità.

    ![](./media/ProtectEmail/EUX-Android-all-Successful2.PNG)

    Dopo che l'utente è stato registrato e la conformità è stata verificata, l'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

Se l'utente segue questi passaggi per registrarsi e diventare conforme e non riesce comunque ad accedere alla sua posta elettronica dal dispositivo mobile, potrà eseguire questi passaggi aggiuntivi per provare a risolvere il problema:

1.  Verificare prima di tutto che il dispositivo sia registrato. In caso contrario, l'utente segue i passaggi precedenti.

2.  Verificare che il dispositivo è conforme facendo clic su **Controlla conformità**. Se viene identificato un errore di conformità, l'utente può seguire le istruzioni specifiche per i dispositivi mobili su come risolvere il problema, ad esempio con la reimpostazione della password.

3.  Chiamare l'help desk.

## Problemi e soluzioni
Ogni 8 ore per impostazione predefinita, i dispositivi vengono controllati per verificare che siano ancora conformi. Se un dispositivo che prima era conforme viene in seguito considerato come non conforme (ad esempio, se è stato aggiunto o modificato un criterio di conformità), l'utente può seguire questi passaggi per rendere il dispositivo nuovamente conforme:

1.  L'utente riceve una notifica nella posta elettronica o nel dispositivo che indica che il dispositivo non è conforme. A questo punto, il dispositivo viene messo in quarantena in Exchange.

2.  Quando l'utente prova ad accedere alla posta elettronica, viene visualizzato un messaggio di posta elettronica di quarantena che lo informa della necessità di risolvere i problemi di conformità prima di ottenere l'accesso. Quando l'utente fa clic sul collegamento ipertestuale nel messaggio di posta elettronica di quarantena, viene reindirizzato alla schermata di Configurazione dell'accesso aziendale nel portale aziendale di Intune (tramite browser predefinito e Google Play), che indica che il dispositivo non è conforme.

    ![](./media/ProtectEmail/EUX-Android-outOfCompliance.png)

3.  L'utente fa clic su **Continua** e visualizza il problema di conformità che gli impedisce di accedere alla posta elettronica.

    ![](./media/ProtectEmail/EUX-Android-resolve-Compliance-Issues.png)

4.  Dopo la correzione del problema, l'utente fa clic su **Controlla conformità** per verificare che il problema è risolto.

5.  Se il problema viene risolto, l'utente fa clic su **Continua** per completare il processo. L'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

### Come proseguire
L'esperienza dell'utente finale è leggermente diversa in altri dispositivi mobili. Altre informazioni sull'esperienza dell'utente finale per [iOS](../Solutions/end-user-experience-conditional-access-ios.md) e [Windows Phone](../Solutions/end-user-experience-conditional-access-winphone.md).


<!--HONumber=Apr16_HO2-->


