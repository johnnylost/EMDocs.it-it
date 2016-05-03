---
# required metadata

title: Esperienza utente finale di accesso condizionale in Windows Phone
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

# Windows Phone

Il processo di registrazione e le schermate visualizzate dall'utente saranno leggermente diverse a seconda della versione del sistema operativo in esecuzione sul dispositivo dell'utente finale.  In questo argomento viene descritta l'esperienza dell'utente finale per Windows Phone.

## Registrazione

1.  Se un utente è già registrato in Intune ed è conforme, non vedrà alcuna differenza nei dispositivi Windows e continuerà ad avere accesso alla posta elettronica. Gli utenti che non sono ancora registrati in Intune riceveranno un messaggio di posta elettronica di quarantena simile all'esempio seguente:

    ![](./media/ProtectEmail/EUX-Windows-quarantineEmail.png)

    L'utente fa clic su **Per iniziare** per iniziare a registrare il dispositivo.

2.  Nella schermata Configurazione dell'accesso aziendale, l'utente fa clic su **Inizia** per cominciare a configurare il dispositivo e verificarne la conformità.

    ![](./media/ProtectEmail/EUX-Windows1-company-Access-Setup.png)

3.  Nella schermata Registra il dispositivo, l'utente fa clic su **Conferma registrazione** per avviare la registrazione del dispositivo.

    ![](./media/ProtectEmail/EUX-Windows3-enroll-Device.png)

    Durante la registrazione, verrà installato il profilo di gestione dei dispositivi mobili per consentire all'amministratore IT di gestire in remoto il dispositivo. All'utente potrebbe essere richiesto di accettare un certificato di autorizzazione dell'Aggiunta all'area di lavoro.

    ![](./media/ProtectEmail/EUX-Windows4-workplaceJoin1.png)

4.  L'utente accede usando l'indirizzo di posta elettronica che usa con Office. Dopo che si sarà connesso, potrebbe dover fare clic su **Conferma registrazione** ancora una volta per continuare a registrare il dispositivo.

    ![](./media/ProtectEmail/EUX-Windows5-workplaceJoin2.png)

    Il dispositivo viene controllato per verificare che sia registrato.

    ![](./media/ProtectEmail/EUX-Windows6-checking-Enrollment.png)

5.  L'utente completa quindi il processo di registrazione selezionando il dispositivo e facendo clic su **Seleziona**. Se il suo dispositivo non è visualizzato, può selezionare **Il dispositivo non è visualizzato nell'elenco** per riprovare.

    ![](./media/ProtectEmail/EUX-Windows7-confirm-Device.png)

    Il dispositivo viene controllato per verificare che sia conforme ai criteri aziendali.

    ![](./media/ProtectEmail/EUX-Windows9-checking-Compliance.png)

6.  Se si verifica un problema di conformità, all'utente viene richiesto di risolvere il problema (ad esempio creando una password valida) e quindi di fare clic su **Controlla conformità** per continuare.

    ![](./media/ProtectEmail/EUX-Windows13-resolve-Compliance.png)

    Dopo aver verificato la conformità, l'utente verifica che la registrazione venga attivata.

    ![](./media/ProtectEmail/EUX-Windows10-activating-Enrollment.png)

7.  La registrazione viene attivata e l'utente fa clic su **Continua** per completare il processo. L'utente fa quindi clic su **Fine** per uscire dalla configurazione.

    ![](./media/ProtectEmail/EUX-Windows11-COMPLETE.png)

    Dopo che l'utente è stato registrato e la conformità è stata verificata, l'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

Se l'utente segue questi passaggi per registrarsi e diventare conforme e non riesce comunque ad accedere alla sua posta elettronica dal dispositivo mobile, potrà eseguire questi passaggi aggiuntivi per provare a risolvere il problema:

-   Verificare prima di tutto che il dispositivo sia registrato. In caso contrario, l'utente segue i passaggi precedenti.

-   Verificare che il dispositivo è conforme facendo clic su **Controlla conformità**. Se viene identificato un errore di conformità, l'utente può seguire le istruzioni specifiche per i dispositivi mobili su come risolvere il problema, ad esempio con la reimpostazione della password.

-   Chiamare l'help desk.

## Problemi e soluzioni
Ogni 8 ore per impostazione predefinita, i dispositivi vengono controllati per verificare che siano ancora conformi. Se un dispositivo che prima era conforme viene in seguito considerato come non conforme (ad esempio, se è stato aggiunto o modificato un criterio di conformità), l'utente può seguire questi passaggi per rendere il dispositivo nuovamente conforme:

1.  L'utente riceve una notifica nella posta elettronica o nel dispositivo che indica che il dispositivo non è conforme. A questo punto, il dispositivo viene messo in quarantena in Exchange.

2.  Se l'utente prova ad accedere alla posta elettronica, viene reindirizzato alla schermata Configurazione dell'accesso aziendale dal portale aziendale di Intune che indica che l'utente non è conforme.

    ![](./media/ProtectEmail/EUX-Windows14-OutOfCompliance.png)

3.  L'utente fa clic su **Continua** e visualizza il problema di conformità che gli impedisce di accedere alla posta elettronica.

4.  Dopo la correzione del problema, l'utente fa clic su **Controlla conformità** per verificare che il problema è risolto.

5.  Se il problema viene risolto, l'utente fa clic su **Continua** per completare il processo. L'accesso alla posta elettronica dovrebbe diventare disponibile entro pochi minuti.

### Come proseguire
L'esperienza dell'utente finale è leggermente diversa in altri dispositivi mobili. Altre informazioni sull'esperienza dell'utente finale per [Android](../Solutions/end-user-experience-conditional-access-android.md) e
[iOS](../Solutions/end-user-experience-conditional-access-ios.md).


<!--HONumber=Apr16_HO2-->


