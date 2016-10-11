---
title: Come usare applicazioni per dispositivi mobili gestite dall'organizzazione
description: Come usare app per dispositivi mobili gestite dall'organizzazione
keywords: 
author: craigcaseyMSFT
manager: jeffgilb
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 174348f0-dbc6-4204-8626-3c6f38b7bbde
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c704180f9c607e39c27d75676eec30afa1a1730c
ms.openlocfilehash: 5e9bfffa88ba1375f3c0e0ea61d16677af87d137


---

# Come usare app per dispositivi mobili gestite dall'organizzazione

## Accesso a OneDrive in un dispositivo iOS

In questa sezione viene usato OneDrive for Business come esempio per dimostrare che l'esperienza dell'utente può essere leggermente diversa in un'applicazione gestita da Intune.

1.  Avviare l'app **OneDrive for Business** per aprire la pagina di accesso.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-1-launchOnedrive.png)
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2.  Digitare il nome utente dell'account aziendale. Si viene reindirizzati alla pagina di **autenticazione di O365** in cui immettere le credenziali aziendali.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-2-enterName.png)
3.  Dopo la corretta autenticazione delle credenziali in Azure AD, verranno applicati i criteri MAM e verrà richiesto di riavviare l'app **OneDrive for Business**.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-3-restart.png)
> [!NOTE]
> La finestra di dialogo Riavvio richiesto viene visualizzata solo per i dispositivi non registrati in Intune.

4.  Riavviare l'app **OneDrive for Business**. L'applicazione viene avviata con i criteri MAM attivati. A questo punto viene richiesto di impostare un **PIN** per l'applicazione. (se il criterio è configurato per questo).

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-4-enterPIN.png)
5.  Dopo aver impostato e confermato il PIN, sarà possibile accedere ai file in **OneDrive for Business**.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-5-accessFiles.png)
> [!NOTE]
> Quando si modifica un criterio distribuito, le modifiche verranno applicate alla successiva apertura dell'applicazione.

## Accesso a OneDrive in un dispositivo Android
In questa sezione viene usato OneDrive for Business come esempio per dimostrare che l'esperienza dell'utente può essere leggermente diversa in un'applicazione gestita da Intune.
1.  Avviare l'app **OneDrive for Business** per aprire la pagina di accesso.
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2.  Digitare il nome utente dell'account aziendale. Si verrà reindirizzati alla pagina di autenticazione di O365 in cui immettere le credenziali aziendali.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-6-enterCreds.png)
3.  Dopo che le credenziali saranno state autenticate da Azure AD, verrà visualizzato un messaggio con le istruzioni per installare l'app Portale aziendale, se non è già installata nel dispositivo. Toccare **Scarica l'app** per procedere.
> [!NOTE]
> L'app Portale aziendale è necessaria per tutte le app associate a criteri MAM in dispositivi Android. Per i dispositivi non registrati in Intune, è necessario che l'app sia installata nel dispositivo, ma avvio o accesso all'app non sono necessari.

4.  A questo punto si viene reindirizzati allo store **Google Play** , da cui è possibile scaricare e installare l'app **Portale aziendale** .

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-7-installPortal.png)

 L'app Portale aziendale consente di mantenere i dati sicuri e protetti.
![TESTO DESCRITTIVO](./media/ft-useMngdApps-8-intunePortal.png)
5.  Dopo aver completato l'installazione, scegliere **Accetta** per accettare le condizioni.
6.  L'app **OneDrive for Business** viene avviata automaticamente.
7.  All'apertura successiva di OneDrive for Business, verrà visualizzato il prompt dei comandi per impostare un **PIN**, purché i criteri siano impostati in modo da richiedere un PIN per accedere all'app **OneDrive for Business**.

  ![TESTO DESCRITTIVO](./media/ft-useMngdApps-9-setNewPIN.png)
8.  Dopo aver impostato e confermato il PIN, è possibile continuare a usare **OneDrive for Business**, gestito adesso con i criteri delle app.

### Altre informazioni
Vedere [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).



<!--HONumber=Sep16_HO4-->


