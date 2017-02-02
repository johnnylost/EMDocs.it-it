---
title: Esperienza dell&quot;utente finale con MAM
description: Esperienza dell&quot;utente finale con i criteri di gestione delle app mobili.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc9f6ea-fc92-468d-bb5b-60c67949ca28
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2342889a686db8a6496c97979cb222af8347241a
ms.openlocfilehash: 0367aea637810515742a344ac707f4e5272d29b1


---

# <a name="end-user-experience-of-mobile-app-management-policies"></a>Esperienza dell'utente finale con i criteri di gestione delle app mobili
I criteri MAM si applicano solo quando le app vengono usate in un contesto professionale. Leggere gli scenari di esempio seguenti che consentono di informare gli utenti in modo che comprendano il funzionamento delle app gestite.

In questa sezione vengono illustrati gli esempi seguenti di esperienza degli utenti finali:

- Scenario: Accesso a OneDrive in un dispositivo iOS
- Scenario: Accesso a OneDrive in un dispositivo Android

Per informazioni su altre esperienze specifiche dell'utente finale, vedere gli articoli seguenti:

- [Uso di app con supporto di più identità](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support)
- [Gestione degli account utente](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts)
- [Visualizzazione di file multimediali con l'app di condivisione file Rights Management](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)

## <a name="scenario-accessing-onedrive-on-an-ios-device"></a>Scenario: Accesso a OneDrive in un dispositivo iOS

1. L'utente avvia l'app **OneDrive** per aprire la pagina di accesso.
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2. L'utente digita il nome utente dell'account aziendale e viene reindirizzato alla pagina di **autenticazione di O365** perché immetta le credenziali aziendali.

  Dopo l'autenticazione delle credenziali da parte di Azure AD, i criteri MAM vengono applicati.
3. Se i criteri sono configurati per l'uso di un PIN, all'utente viene richiesto di impostare un **PIN** per l'app.

4.  Dopo aver impostato e confermato il PIN, l'utente può accedere ai file all'interno di **OneDrive for Business**.
> [!NOTE]
> Quando si modifica un criterio distribuito, le modifiche vengono applicate alla successiva apertura dell'app.

## <a name="scenario-accessing-onedrive-on-an-android-device"></a>Scenario: Accesso a OneDrive in un dispositivo Android
1. L'utente avvia l'app **OneDrive** per aprire la pagina di accesso.
> [!NOTE]
> In un dispositivo personale l'utente deve solitamente scaricare l'app. Se il dispositivo è gestito da una soluzione MDM, è possibile distribuire l'app nel dispositivo.

2.  L'utente digita il nome utente dell'account aziendale e viene reindirizzato alla pagina di **autenticazione di O365** perché immetta le credenziali aziendali.

  Dopo l'autenticazione delle credenziali da parte di Azure AD, i criteri MAM vengono applicati.

3.  L'app **OneDrive** si avvia automaticamente e all'utente viene richiesto di impostare un **PIN**, purché i criteri siano impostati in modo da richiedere un **PIN** per accedere all'app **OneDrive**.

4.  Dopo aver impostato e verificato il PIN, l'utente può continuare a usare **OneDrive**, che è ora gestito da criteri di app.

## <a name="where-to-go-from-here"></a>Come proseguire
Sono disponibili ulteriori informazioni su altre esperienze dell'utente finale, ad esempio in [Uso di app con supporto di più identità](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support), [Gestione degli account utente](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts) e [Visualizzazione di file multimediali con l'app di condivisione file Rights Management](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).



<!--HONumber=Jan17_HO1-->


