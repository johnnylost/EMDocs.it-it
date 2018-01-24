---
title: Criteri consigliati per la protezione dei documenti - Microsoft 365 Enterprise | Microsoft Docs
description: Descrive i criteri consigliati da Microsoft riguardo alla protezione dell'accesso ai file di SharePoint.
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 01/18/2018
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 3eabab5a19c99fe97d56ed3d802c026c0b0bc6ef
ms.sourcegitcommit: eb3521981c5dec164ce2a14b4d4d53830b5ba461
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Suggerimenti sui criteri per la protezione di siti e file di SharePoint
I seguenti consigli sono offerti *in aggiunta* ai [consigli sui criteri comuni di identità e accesso](identity-access-policies.md) e ai [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md). Per proteggere i file di SharePoint Online, è necessario creare nuovi criteri e modificare i criteri esistenti come descritto di seguito.

Queste indicazioni si basano su tre diversi livelli di sicurezza e protezione per la posta elettronica e possono essere applicati in base al livello di granularità necessario:

- **Baseline** (Livello base): Microsoft consiglia di definire uno standard minimo per la protezione dei dati, nonché le identità e i dispositivi che accedono ai dati. Microsoft offre come impostazione predefinita una protezione avanzata efficiente, che soddisfa le esigenze di molte organizzazioni. Alcune organizzazioni richiedono funzionalità aggiuntive per soddisfare i propri requisiti di base.
- **Sensitive** (Dati sensibili): alcuni clienti hanno un subset di dati che richiede un grado di protezione superiore. È possibile applicare una protezione superiore a set di dati specifici nell'ambiente Office 365. Microsoft consiglia di applicare livelli di protezione analoghi alle identità e ai dispositivi che accedono ai dati sensibili. 
- **Highly regulated** (Dati altamente sensibili): alcune organizzazioni possono avere una piccola quantità di dati della massima riservatezza, segreti commerciali o dati soggetti a regolamentazione. Microsoft offre funzionalità che consentono alle organizzazioni di soddisfare questi requisiti, inclusa la protezione aggiuntiva per identità e dispositivi.

Per altre informazioni, vedere l'introduzione dell'argomento [Configurazioni e criteri di sicurezza consigliati](microsoft-365-policies-configurations.md).

> [!IMPORTANT]
> Per creare tutti i gruppi di sicurezza di queste indicazioni, è necessario che le funzionalità di Office siano abilitate. Questa impostazione è particolarmente importante per la distribuzione di Azure Information Protection (AIP) quando si proteggono i documenti in SharePoint Online.
>
>![Funzionalità di Office abilitate per i gruppi di sicurezza](./media/security-group.png)
>

## <a name="baseline"></a>Versione di base

### <a name="medium-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio medio ed elevato
Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio

Per creare criteri di accesso condizionale per Exchange Online:

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali. Dopo l'accesso viene visualizzato il dashboard di Azure.

2. Scegliere **Azure Active Directory** dal menu a sinistra.

3. Nella sezione **Sicurezza** scegliere **Accesso condizionale**.

4. Scegliere **Nuovo criterio**.

5. Immettere un nome per i criteri, quindi in **Utenti e gruppi** scegliere gli utenti e i gruppi ai quali applicare i criteri.

6. Scegliere **App cloud**.

7. Scegliere **Seleziona le app**, selezionare **Office 365 SharePoint Online** nell'elenco **App cloud** e fare clic su **Seleziona**. Dopo aver selezionato l'app **Office 365 SharePoint Online** fare clic su **Chiudi**.

8. Scegliere **Concedi** nella sezione **Controlli di accesso**.

9. Scegliere **Concedi accesso**, selezionare sia **Richiedi che i dispositivi siano contrassegnati come conformi** sia **Require domain joined (Hybrid Azure AD)** (Richiedi dispositivo aggiunto a un dominio - Hybrid Azure AD), quindi scegliere **Seleziona**.

10. Fare clic su **Crea** per creare i criteri di accesso condizionale di Exchange Online.

    > [!NOTE]
    > A partire da Intune in Azure tutti i criteri di accesso condizionale devono essere creati nel carico di lavoro di Azure Active Directory. Per praticità, il portale di Intune dispone di un collegamento al carico di lavoro dei criteri di accesso condizionale di Azure AD.

    > [!IMPORTANT]
    > Per assistenza nella migrazione al portale di Intune in Azure dei criteri di accesso condizionale creati in precedenza nel portale di Intune classico, vedere l'argomento [Riassegnare i criteri di accesso condizionale dal portale di Intune classico al portale di Azure](https://docs.microsoft.com/intune/conditional-access-intune-reassign). 

### <a name="app-based-conditional-access-for-sharepoint-online"></a>Accesso condizionale basato su app per SharePoint Online

È possibile aggiungere un ulteriore livello di sicurezza impostando criteri di accesso condizionale basati su app per SharePoint Online nel portale di Intune su Azure. Quando si applica un accesso condizionale basato su app per SharePoint Online gli utenti potranno accedere alle risorse aziendali solo tramite tale app.

Per aggiungere criteri di accesso condizionale basato su app:

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune. Dopo l'accesso viene visualizzato il dashboard di Azure.

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare "**Intune**".

3. Scegliere **Protezione app di Intune**.

4. Nel pannello **Gestione di applicazioni mobili di Intune** scegliere **Tutte le impostazioni**.

5. Scegliere **Exchange Online** nella sezione **Accesso condizionale**.

6. Selezionare **Consenti app che supportano i criteri app di Intune** e quindi scegliere l'app (ad esempio Microsoft Outlook).

7. Scegliere **Gruppi di utenti limitati**, fare clic su **Seleziona gruppi**, selezionare l'utente o il gruppo al quale applicare i criteri e fare clic su **Seleziona**.

## <a name="sensitive"></a>Dati sensibili

### <a name="low-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio basso ed elevato

Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio

(Vedere le istruzioni per la protezione di base)

### <a name="app-based-conditional-access-for-sharepoint-online"></a>Accesso condizionale basato su app per SharePoint Online

(Vedere le istruzioni per la protezione di base)

## <a name="highly-regulated"></a>Riservatezza elevata

### <a name="mfa-required"></a>Autenticazione MFA obbligatoria

Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiedi un dispositivo conforme o aggiunto a un dominio
(Vedere le istruzioni per la protezione di base)

### <a name="app-based-conditional-access-for-sharepoint-online"></a>Accesso condizionale basato su app per SharePoint Online
(Vedere le istruzioni per la protezione di base)

## <a name="additional-configurations"></a>Configurazioni aggiuntive
Oltre ai criteri descritti in precedenza, è necessario bloccare i protocolli legacy che non supportano l'autenticazione moderna.

### <a name="lock-down-legacy-protocols"></a>Bloccare i protocolli legacy
I criteri di accesso condizionale proteggono l'accesso attraverso i flussi dei browser e le applicazioni usando l'autenticazione moderna, ad esempio Office 2016 e le applicazioni dell'elenco delle piattaforme supportate. Per le applicazioni desktop di Office meno recenti, ad esempio Office 2010, i criteri di accesso condizionale non vengono applicati.

Le applicazioni più datate che non usano l'autenticazione moderna possono essere bloccate [usando il portale di amministrazione di OneDrive](https://support.office.com/article/Control-access-based-on-network-location-or-app-59b83701-cefd-4bf8-b4d1-d4659b60da08). Per disabilitare i protocolli legacy di SharePoint, è anche possibile usare il cmdlet di amministrazione di SharePoint in PowerShell. Per usare PowerShell, è sufficiente eseguire il [cmdlet Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) e impostare **-LegacyAuthProtocolsEnabled** su **$false**.  Eseguita l'impostazione, il supporto del protocollo legacy viene disabilitato e l'accesso a SharePoint usando le applicazioni client meno recenti viene bloccato.

## <a name="next-steps"></a>Passaggi successivi
[Informazioni sui servizi di Microsoft 365](index.md)
