---
# required metadata

title: Esperienza utente finale di accesso condizionale nei dispositivi iOS
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

# iOS

Il processo di registrazione e le schermate visualizzate dall'utente saranno leggermente diverse a seconda della versione del sistema operativo in esecuzione sul dispositivo dell'utente finale. In questo argomento viene descritta l'esperienza dell'utente finale per i dispositivi iOS.

## Registrazione

1.  Se un utente è già registrato in Intune ed è conforme, non vedrà alcuna differenza nei dispositivi iOS e continuerà ad avere accesso alla posta elettronica. Se l'utente non è ancora registrato, visualizzerà un messaggio di quarantena simile al seguente quando avvia la sua applicazione di posta elettronica:

    ![](./media/EUX-iOS-Get-Started.PNG)

    L'utente fa clic su **Per iniziare** per iniziare a registrare il dispositivo.

2.  All'utente viene richiesto di installare l'app Portale aziendale di Intune dall'App Store corrispondente.

    ![](./media/ProtectEmail/EUX-iOS-intune-Company-Portal.png)

    Dopo l'installazione, l'utente apre l'app ed esegue l'accesso con le credenziali della società.

3.  Nella schermata Configurazione dell'accesso aziendale, l'utente fa clic su **Inizia** per cominciare a configurare il dispositivo e verificarne la conformità.

    ![](./media/ProtectEmail/EUX-iOS-company-AccessSetup.png)

4.  Nella schermata Registrazione del dispositivo, l'utente fa clic su **Registra** per iniziare a registrare il suo dispositivo.

    ![](./media/ProtectEmail/EUX-iOS-device-Enrollment.png)

    Durante la registrazione, verrà installato il profilo di gestione dei dispositivi mobili per consentire all'amministratore IT di gestire in remoto il dispositivo. L'utente immette la sua password, se richiesta.

5.  Nella schermata Configurazione dell'accesso aziendale, l'utente fa clic su **Continua** per iniziare a verificare la conformità nel dispositivo.

    ![](./media/ProtectEmail/EUX-iOS-device-Compliance-Check.png)

    Se si verifica un problema di conformità, all'utente viene richiesto di risolvere il problema (ad esempio creando una password valida) e quindi di fare clic su **Controlla conformità** per continuare.

    ![](./media/ProtectEmail/EUX-iOS-device-Compliance-Check.png)

6.  Quando il dispositivo sarà completamente compatibile, l'utente fa clic su **Continua** per continuare.

    ![](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    Dopo che l'utente è stato registrato e la conformità è stata verificata, l'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

Se l'utente segue questi passaggi per registrarsi e diventare conforme e non riesce comunque ad accedere alla sua posta elettronica dal dispositivo mobile, potrà eseguire questi passaggi aggiuntivi per provare a risolvere il problema:

-   Verificare prima di tutto che il dispositivo sia registrato. In caso contrario, l'utente segue i passaggi precedenti.

-   Verificare che il dispositivo è conforme facendo clic su **Controlla conformità**. Se viene identificato un errore di conformità, l'utente può seguire le istruzioni specifiche per i dispositivi mobili su come risolvere il problema, ad esempio con la reimpostazione della password.

-   Chiamare l'help desk.

## Problemi e soluzioni
Ogni 8 ore per impostazione predefinita, i dispositivi vengono controllati per verificare che siano ancora conformi. Se un dispositivo che prima era conforme viene in seguito considerato come non conforme (ad esempio, se è stato aggiunto o modificato un criterio di conformità), l'utente può seguire questi passaggi per rendere il dispositivo nuovamente conforme:

1.  L'utente riceve una notifica nella posta elettronica o nel dispositivo che indica che il dispositivo non è conforme. A questo punto, il dispositivo viene messo in quarantena in Exchange.

2.  Se l'utente prova ad accedere alla posta elettronica, viene reindirizzato alla schermata Configurazione dell'accesso aziendale dal portale aziendale di Intune che indica che l'utente non è conforme.

    ![](./media/ProtectEmail/EUX-iOS-fallOut-Compliance.png)

3.  L'utente fa clic su **Continua** e visualizza il problema di conformità che gli impedisce di accedere alla posta elettronica.

    ![](./media/ProtectEmail/EUX-iOS-check-Compliance.png)

4.  Dopo la correzione del problema, l'utente fa clic su **Controlla conformità** per verificare che il problema è risolto.

5.  Se il problema viene risolto, l'utente fa clic su **Continua** per completare il processo.

    ![](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    L'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

### Come proseguire
L'esperienza dell'utente finale è leggermente diversa in altri dispositivi mobili. Altre informazioni sull'esperienza dell'utente finale per [Android](../Solutions/end-user-experience-conditional-access-android.md) e [Windows Phone](../Solutions/end-user-experience-conditional-access-winphone.md).


<!--HONumber=Apr16_HO2-->


