---
title: Criteri consigliati per la protezione dei documenti - Microsoft 365 Enterprise | Microsoft Docs
description: Descrive i criteri consigliati da Microsoft riguardo alla protezione dell'accesso ai file di SharePoint.
author: jeffgilb
manager: femila
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/30/2017
ms.author: jeffgilb
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 8d38b1f9f899bcf61b1d35c8962a6829ce3d9a56
ms.sourcegitcommit: 0e0a15476e3bbd2d4ac6101c2cedd02e082ee25d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2017
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Suggerimenti sui criteri per la protezione di siti e file di SharePoint
I seguenti consigli sono offerti *in aggiunta* ai [consigli sui criteri comuni di identità e accesso](identity-access-policies.md) e ai [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md). Per proteggere i file di SharePoint Online, è necessario creare nuovi criteri e modificare i criteri esistenti come descritto di seguito. 

Questi consigli si basano su tre diversi livelli di sicurezza e protezione per i file di SharePoint e possono essere applicati in base al livello di granularità necessario: **protezione di base**, **dati sensibili** e **riservatezza elevata**. Per altre informazioni su questi livelli di sicurezza e sui sistemi operativi client consigliati, a cui fanno riferimento questi consigli, vedere [l'introduzione ai criteri e alle configurazioni di sicurezza consigliati](microsoft-365-policies-configurations.md).

>[!NOTE]
>Per creare tutti i gruppi di sicurezza di queste indicazioni, è necessario che le funzionalità di Office siano abilitate. È importante in particolare per la distribuzione di AIP quando si proteggono i documenti in SharePoint. 
>
>![Funzionalità di Office abilitate per i gruppi di sicurezza](./media/security-group.png)
>

## <a name="baseline"></a>Versione di base 

### <a name="medium-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio medio ed elevato
Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiede un dispositivo conforme o aggiunto a un dominio
Per creare un nuovo criterio di accesso condizionale di Intune per SharePoint Online, accedere al [portale di Microsoft Management (http://manage.microsoft.com)](http://manage.microsoft.com) con le credenziali di amministratore e passare a **Criteri** > **Accesso condizionale** > **Criteri di SharePoint Online**.

![Criteri di SharePoint Online](./media/secure-docs/sharepoint-online-policy.png)

Per richiedere un dispositivo conforme o aggiunto al dominio, è necessario impostare un criterio di accesso condizionale specifico per SharePoint Online nel portale di gestione di Intune.
| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|**Accesso all'applicazione**|OneDrive for Business e altre app che usano l'autenticazione moderna|Tutte le piattaforme|True|Opzione selezionata|
|     |     |Windows deve soddisfare i requisiti seguenti|I dispositivi devono essere aggiunti a un dominio o conformi|Selezionato (elenco)|
|     |     |Piattaforme specifiche|False||
|     |Accesso browser a SharePoint e OneDrive for Business |Blocca i dispositivi non conformi sulla stessa piattaforma in cui si trova OneDrive for Business|True|Check|
|**Distribuzione dei criteri**|Gruppi di destinazione|Seleziona i gruppi di Active Directory da usare come destinazione per questi criteri|     |     |
|     |     |Tutti gli utenti|False|     |
|     |     |Gruppi di sicurezza selezionati|True|Opzione selezionata|
|     |     |Modifica|Seleziona il gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione.|     |
|     |Gruppi esenti|Seleziona i gruppi di Active Directory da esentare da questi criteri. Questa impostazione sostituisce i membri dell'elenco Gruppi di destinazione.|     |     |    
|     |     |Nessun utente esente|True|Opzione selezionata|
|     |     |Gruppi di sicurezza selezionati|False|     |

### <a name="mobile-application-management-conditional-access-for-sharepoint-online"></a>Accesso condizionale per la gestione di applicazioni mobili per SharePoint Online

Per gestire le app per dispositivi mobili, è necessario impostare un criterio di accesso condizionale specifico per SharePoint Online nel portale di gestione di Intune.

Per gestire le app per dispositivi mobili, accedere al portale di Microsoft Azure con le credenziali di amministratore e quindi passare a **Protezione app di Intune** > **Impostazioni** > **Accesso condizionale** > **SharePoint Online**.

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|**Accesso app**|App consentite|Abilita accesso app|Consenti app che supportano i criteri app di Intune|Selezionato (elenco): il risultato è un elenco delle combinazioni di app/piattaforme supportate dai criteri app di Intune.|
|**Accesso utente**|     |Gruppi di utenti limitati|Aggiunta di gruppi di utenti: seleziona un gruppo di sicurezza specifico in cui sono contenuti gli utenti di destinazione.|Iniziare con il gruppo di sicurezza che include utenti pilota.|
|     |     |Gruppi di utenti esentati|Gruppi di sicurezza di eccezione|     |

### <a name="apply-to"></a>Applica a

Dopo aver completato il progetto pilota, questi criteri devono essere applicati a tutti gli utenti dell'organizzazione.

## <a name="sensitive"></a>Dati sensibili 

### <a name="low-and-above-risk-requires-mfa"></a>Autenticazione a più fattori richiesta per rischio basso ed elevato

Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiede un dispositivo conforme o aggiunto a un dominio

(Vedere le istruzioni per la protezione di base)

### <a name="mobile-application-management-conditional-access-for-sharepoint-online"></a>Accesso condizionale per la gestione di applicazioni mobili per SharePoint Online

(Vedere le istruzioni per la protezione di base)

## <a name="highly-regulated"></a>Riservatezza elevata 

### <a name="mfa-required"></a>Autenticazione MFA obbligatoria

Apportare le modifiche seguenti al criterio di accesso condizionale esistente creato durante l'applicazione dei [criteri di sicurezza consigliati per la posta elettronica](secure-email-recommended-policies.md):

| Category|Tipo|Proprietà|Valori|Note|
|:-----|:-----|:-----|:-----|:-----|
|Assignments|App cloud|Includi|Selezionare le app:<br></br>  Office 365 Exchange Online<br></br>  Office 365 SharePoint Online|Selezionare entrambe|

### <a name="require-a-compliant-or-domain-joined-device"></a>Richiede un dispositivo conforme o aggiunto a un dominio
(Vedere le istruzioni per la protezione di base)

### <a name="mobile-application-management-conditional-access-for-sharepoint-online"></a>Accesso condizionale per la gestione di applicazioni mobili per SharePoint Online
(Vedere le istruzioni per la protezione di base)

## <a name="additional-configurations"></a>Configurazioni aggiuntive
Oltre ai criteri descritti in precedenza, è necessario bloccare i protocolli legacy che non supportano l'autenticazione moderna.

### <a name="lock-down-legacy-protocols"></a>Bloccare i protocolli legacy
I criteri di accesso condizionale proteggono l'accesso attraverso i flussi dei browser e le applicazioni usando l'autenticazione moderna, ad esempio Office 2016 e le applicazioni dell'elenco delle piattaforme supportate. Per le applicazioni desktop di Office meno recenti, ad esempio Office 2010, i criteri di accesso condizionale non vengono applicati. 

Le applicazioni più datate che non usano l'autenticazione moderna possono essere bloccate [usando il portale di amministrazione di OneDrive](https://support.office.com/article/Control-access-based-on-network-location-or-app-59b83701-cefd-4bf8-b4d1-d4659b60da08). Per disabilitare i protocolli legacy di SharePoint, è anche possibile usare il cmdlet di amministrazione di SharePoint in PowerShell. Per usare PowerShell, è sufficiente eseguire il [cmdlet Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) e impostare **-LegacyAuthProtocolsEnabled** su **$false**.  Eseguita l'impostazione, il supporto del protocollo legacy viene disabilitato e l'accesso a SharePoint usando le applicazioni client meno recenti viene bloccato.
                                                     
## <a name="next-steps"></a>Passaggi successivi
[Informazioni sui servizi di Microsoft 365](index.md)
