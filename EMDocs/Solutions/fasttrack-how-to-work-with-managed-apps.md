---
title: Come usare applicazioni per dispositivi mobili gestite dall'organizzazione
description: Come usare app per dispositivi mobili gestite dall'organizzazione
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 174348f0-dbc6-4204-8626-3c6f38b7bbde
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 187f733bf091fc337440c245fa95fb58ddfc1196
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="how-to-use-mobile-apps-managed-by-your-organization"></a>Come usare app per dispositivi mobili gestite dall'organizzazione

## <a name="accessing-onedrive-on-an-ios-device"></a>Accesso a OneDrive in un dispositivo iOS

In questa sezione viene usato OneDrive for Business come esempio per dimostrare che l'esperienza dell'utente può essere leggermente diversa in un'applicazione gestita da Intune.

1.  Avviare l'app **OneDrive for Business** per aprire la pagina di accesso.

  ![Schermata che illustra la pagina di accesso a OneDrive for Business per iOS.](./media/ft-useMngdApps-1-launchOnedrive.png)
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2.  Digitare il nome utente dell'account aziendale. Si verrà reindirizzati alla pagina di **autenticazione di O365** in cui immettere le credenziali di lavoro.

  ![Schermata che illustra un utente iOS che immette le credenziali nella pagina di accesso di Office 365.](./media/ft-useMngdApps-2-enterName.png)
3.  Dopo la corretta autenticazione delle credenziali in Azure AD, verranno applicati i criteri MAM e verrà richiesto di riavviare l'app **OneDrive for Business**.

  ![Schermata che illustra che OneDrive deve essere riavviato.](./media/ft-useMngdApps-3-restart.png)
> [!NOTE]
> La finestra di dialogo Riavvio richiesto viene visualizzata solo per i dispositivi non registrati in Intune.

4.  Riavviare l'app **OneDrive for Business**. L'applicazione viene avviata con i criteri MAM attivati. A questo punto viene richiesto di impostare un **PIN** per l'applicazione. (se il criterio è configurato per questo).

  ![Schermata in cui viene richiesto all'utente iOS di impostare un PIN per l'app.](./media/ft-useMngdApps-4-enterPIN.png)
5.  Dopo aver impostato e confermato il PIN, sarà possibile accedere ai file in **OneDrive for Business**.

  ![Schermata che illustra vari file che sono accessibili in OneDrive for Business in iOS.](./media/ft-useMngdApps-5-accessFiles.png)
> [!NOTE]
> Quando si modifica un criterio distribuito, le modifiche verranno applicate alla successiva apertura dell'applicazione.

## <a name="accessing-onedrive-on-an-android-device"></a>Accesso a OneDrive in un dispositivo Android
In questa sezione viene usato OneDrive for Business come esempio per dimostrare che l'esperienza dell'utente può essere leggermente diversa in un'applicazione gestita da Intune.
1.  Avviare l'app **OneDrive for Business** per aprire la pagina di accesso.
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2.  Digitare il nome utente dell'account aziendale. Si verrà reindirizzati alla pagina di autenticazione di O365 in cui immettere le credenziali aziendali.

  ![Schermata che illustra l'utente di un dispositivo Android che immette le credenziali nella pagina di accesso di Office 365.](./media/ft-useMngdApps-6-enterCreds.png)
3.  Dopo che le credenziali saranno state autenticate da Azure AD, verrà visualizzato un messaggio con le istruzioni per installare l'app Portale aziendale, se non è già installata nel dispositivo. Toccare **Scarica l'app** per procedere.
> [!NOTE]
> L'app Portale aziendale è necessaria per tutte le app associate a criteri MAM in dispositivi Android. Per i dispositivi non registrati in Intune, è necessario che l'app sia installata nel dispositivo, ma avvio o accesso all'app non sono necessari.

4.  A questo punto si viene reindirizzati allo store **Google Play** , da cui è possibile scaricare e installare l'app **Portale aziendale** .

  ![Schermata in cui viene richiesto all'utente del dispositivo Android di aprire Google Play Store per scaricare l'app Portale aziendale di Intune.](./media/ft-useMngdApps-7-installPortal.png)

 L'app Portale aziendale consente di mantenere i dati sicuri e protetti.
![Screenshot in cui viene richiesto all'utente di Android di installare l'app Portale aziendale di Intune.](./media/ft-useMngdApps-8-intunePortal.png)
5.  Dopo aver completato l'installazione, scegliere **Accetta** per accettare le condizioni.
6.  L'app **OneDrive for Business** viene avviata automaticamente.
7.  All'apertura successiva di OneDrive for Business, verrà visualizzato il prompt dei comandi per impostare un **PIN**, purché i criteri siano impostati in modo da richiedere un PIN per accedere all'app **OneDrive for Business**.

  ![Schermata in cui viene richiesto all'utente di un dispositivo Android di impostare un PIN per l'app](./media/ft-useMngdApps-9-setNewPIN.png)
8.  Dopo aver impostato e confermato il PIN, è possibile continuare a usare **OneDrive for Business**, gestito adesso con i criteri delle app.

### <a name="want-to-learn-more"></a>Altre informazioni
Vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).
