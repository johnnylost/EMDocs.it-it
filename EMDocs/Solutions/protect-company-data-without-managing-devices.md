---
title: Proteggere i dati aziendali senza gestire i dispositivi | Microsoft Docs
description: "EMS offre funzionalità innovative per la protezione dalla perdita di dati con Microsoft Intune. Consente di proteggere i dati aziendali e mantenere l&quot;esperienza utente con le applicazioni di Office 365 al livello eccezionale a cui sono abituati i dipendenti senza gestire i loro dispositivi."
keywords: 
author: jeffgilb
manager: swadhwa
ms.date: 6/7/2017
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b46877f3-cf32-4919-ba63-4df55cd2af32
ms.reviewer: vlpetros
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 5d9a4bd18660a573b2dd76c0263b89ecf5ae4610
ms.openlocfilehash: 5a0eef972374efefff886ab9dbf7b6a7e4f7aab7
ms.contentlocale: it-it
ms.lasthandoff: 05/29/2017


---

# <a name="protect-company-data-without-managing-devices-with-intune"></a>Proteggere i dati aziendali senza gestire i dispositivi con Intune
Viviamo in un mondo caratterizzato dalla mobilità in cui i dipendenti hanno bisogno di accedere ovunque si trovino ai dati aziendali e agli strumenti di produttività sui propri dispositivi mobili. A causa della loro diffusione e importanza, per molte organizzazioni è essenziale proteggere ulteriormente i dati di Office 365 impedendone la perdita dalle app Office Mobile e assicurando allo stesso tempo esperienze utente di alta qualità. Il reparto IT deve proteggere l'accesso a Office 365 e impedire la perdita di dati aziendali da applicazioni e dispositivi mobili che l'organizzazione non possiede o gestisce. Il problema è che la necessità di proteggere i dati aziendali implica un controllo dei dispositivi personali da parte di IT e molti dipendenti temono per la propria privacy.

## <a name="how-can-enterprise-mobility--security-ems-help-you"></a>Come può essere utile Enterprise Mobility + Security (EMS)?

EMS offre funzionalità innovative per la protezione dalla perdita di dati con Microsoft Intune. Consente di proteggere i dati aziendali e mantenere l'esperienza utente con le applicazioni di Office 365 al livello eccezionale a cui sono abituati i dipendenti. È possibile farlo senza richiedere agli utenti di registrare i propri dispositivi per la gestione e questo aumenta notevolmente le probabilità di successo del programma BYOD e di conformità degli utenti ai criteri IT. Si ottiene il livello di controllo necessario e gli utenti usufruiscono dell'esperienza moderna che si aspettano.  Poiché Microsoft Intune funziona direttamente con Azure Active Directory e Office 365 per gestire l'accesso e proteggere i dati aziendali, non è necessario installare e gestire un'infrastruttura locale né indirizzare tutto il traffico attraverso di essa.

### <a name="recommended-solution"></a>Soluzione consigliata

Microsoft Intune consente alle organizzazioni di assicurare l'accesso alle applicazioni per dispositivi mobili e di proteggere i dati di Office 365 da eventuali perdite senza richiedere ai dipendenti di eseguire la registrazione per la gestione dei dispositivi. La gestione dei dispositivi (MDM) può ancora essere eseguita se necessario, ma ora è facoltativa. Le potenti funzionalità di protezione delle applicazioni di Intune consentono a IT di proteggere i dati aziendali a livello di applicazione senza dover gestire materialmente i dispositivi. Per i dati strettamente riservati, la protezione può essere ulteriormente estesa a livello di file con Azure Information Protection. Dipendenti, fornitori e partner possono usare i propri dispositivi mobili preferiti per accedere a strumenti di produttività e dati aziendali senza rischiare intrusioni nella propria privacy. E se IT sta già usando una soluzione MDM, Intune può aggiungere la protezione avanzata dalla perdita dei dati con controllo di accesso di Office 365 senza che sia necessario annullare la registrazione dei dispositivi dalla soluzione MDM corrente e rieseguirla in Intune MDM.

La demo riportata di seguito illustra come è possibile impedire la perdita di dati dalle applicazioni per dispositivi mobili, incluse le app di Office 365 e quelle interne line-of-business (LOB), usando le innovative funzionalità di protezione di Intune, che non richiedono la registrazione dei dispositivi degli utenti in Intune MDM:

<iframe width="675" height="480"  src="https://www.youtube.com/embed/BcwgKmsAy18?list=TLGGQ9qBhVYxOZIxMzEyMjAxNg" frameborder="0" allowfullscreen></iframe>

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

Il resto di questa soluzione è suddiviso nelle sezioni seguenti che illustrano come proteggere i dati aziendali di Office 365 con Intune:

- **Proteggere i dati delle app con i criteri di protezione delle app per dispositivi mobili di Intune**. In questa sezione viene descritto come creare e distribuire i criteri di protezione delle applicazioni di Microsoft Intune per mettere a disposizione degli utenti di dispositivi mobili non gestiti funzionalità per la prevenzione della perdita dei dati (ad esempio copia/incolla/salva con nome/PIN/crittografia/cancellazione selettiva e così via).

- **Consentire solo alle app per dispositivi mobili che supportano i criteri di protezione delle app di accedere ai servizi di Office 365**. Questa sezione illustra come creare un criterio che consenta solo alle app per dispositivi mobili che supportano i criteri di gestione delle app per dispositivi mobili di Intune di accedere a servizi di Office 365 come Exchange Online.

## <a name="protect-app-data-with-intune-mobile-app-protection-policies"></a>Proteggere i dati delle applicazioni con criteri di protezione delle app per dispositivi mobili di Intune

Quando si proteggono i dati delle applicazioni nei dispositivi non gestiti, non si distribuiscono le applicazioni come si farebbe con i dispositivi gestiti. Gli utenti scaricano le applicazioni di Office 365 da App Store sui dispositivi iOS o Android personali e quindi accedono con gli account aziendali come di consueto.

I criteri di protezione per tali applicazioni sono semplici da creare per i dispositivi iOS e Android nel portale di Azure. Questi tipi di criteri consentono di limitare le azioni utente come taglia, copia, incolla e salva con nome o di applicare un PIN, richiedere la crittografia e cancellare selettivamente i dati aziendali dalle app per dispositivi mobili. Quando vengono assegnati agli utenti, i criteri di protezione delle app vengono automaticamente applicati da Intune e attivati tra account e applicazioni personali e di lavoro. Poiché Intune è perfettamente integrato con Azure AD e Office 365, i dati di lavoro sono protetti mentre i dati personali nelle stesse app di Office rimangono inalterati.

>[!NOTE]
>I criteri di protezione delle app come questi sono disponibili per i computer Windows 10 gestiti da Intune come dispositivi mobili che usano [i criteri di Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

Dopo aver eseguito l'accesso al portale di Azure, le procedure di selezione delle app da proteggere, configurazione delle impostazioni dei criteri di protezione delle app e distribuzione dei criteri a gruppi e utenti finali sono molto semplici:

>[!TIP]
>Per trovare le impostazioni dei criteri di protezione delle app di Intune, accedere al [portale di Azure](https://portal.azure.com) con le credenziali di amministratore di Intune e cercare **Protezione delle app di Intune** nella casella *Cerca risorse* nella parte superiore del portale. Tutti i passaggi seguenti vengono completati da qui.

-   **Creare un criterio di protezione delle app per dispositivi mobili.** Oltre ad assegnare un nome e, se necessario, aggiungere una descrizione per i criteri, per [creare un criterio di protezione delle app](https://docs.microsoft.com/intune-azure/manage-apps/app-protection-policies#create-an-app-protection-policy) è sufficiente definire la piattaforma, selezionare le app da proteggere e configurare le impostazioni dei criteri da applicare:

> **Definire la piattaforma**: è possibile stabilire se usare le piattaforme Android o iOS quando si crea un nuovo criterio, ma qui non sarà possibile creare criteri di protezione delle app per i dispositivi Windows. Sarà necessario [usare i criteri di Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

> **Selezionare una o più app** dall'elenco delle app disponibili in grado di supportare la protezione nei dispositivi non gestiti. Eventuali app che diventano idonee per la protezione verranno aggiunte automaticamente all'elenco delle applicazioni disponibili. Per impostazione predefinita, non è selezionata alcuna app, ma è possibile usare CTRL+clic per selezionare tutte le app che si vuole proteggere con i criteri. In alternativa, è possibile [aggiungere una propria app line-of-business (LOB)](https://docs.microsoft.com/intune/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune) per iOS o Android.

> **Configurare le impostazioni dei criteri richieste** [in iOS o Android](https://docs.microsoft.com/en-us/intune-azure/manage-apps/app-protection-policies#policy-settings) per il trasferimento dei dati (taglia, copia, incolla, salva con nome, crittografia e così via) e l'accesso (richiesta di PIN, intervallo offline e così via).

- **Distribuire i criteri di protezione delle app ai gruppi di utenti** [selezionando i gruppi di utenti](https://docs.microsoft.com/intune-azure/manage-apps/app-protection-policies#deploy-a-policy-to-users) a cui verranno applicati i criteri. Può trattarsi degli stessi gruppi già gestiti in Office 365 o di qualsiasi gruppo disponibile in Azure Active Directory.

La prima volta che un utente apre un'app protetta da un criterio di protezione delle app riceve un messaggio che lo informa che il reparto IT ora protegge i dati aziendali nell'app. Se le impostazioni di accesso configurate nei criteri richiedono un PIN o una password, anche l'utente dovrà creare un PIN o una password per accedere all'app protetta, come illustrato di seguito per un dispositivo Android:

![Requisito del PIN nei criteri di protezione delle app](..\Solutions\media\protect-company-data-without-managing-devices\protect-company-data-without-managing-devices-fig1.png)

Poiché i criteri di protezione delle app funzionano a livello di applicazione anziché di dispositivo, Intune semplifica la protezione dei dati aziendali per IT limitando la condivisione dei dati aziendali tra le app gestite e quelle personali, tra gli account aziendali e quelli personali all'interno della stessa applicazione e consentendo il salvataggio dei dati aziendali solo in percorsi approvati. I dipendenti con dispositivi mobili non dovranno rinunciare al controllo dei propri dispositivi per avere accesso agli strumenti e ai dati aziendali più importanti mentre sono in viaggio.

>[!TIP]
>Per i dati strettamente riservati, la protezione può essere ulteriormente estesa a livello di file con la tecnologia di protezione usata da Azure Information Protection: [Azure Rights Management (Azure RMS).](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

## <a name="allow-only-mobile-apps-that-support-app-protection-policies-to-access-office-365-services"></a>Consentire l'accesso ai servizi di Office 365 solo alle app per dispositivi mobili che supportano i criteri di protezione delle app
Per impostazione predefinita, tutti gli utenti e tutte le applicazioni possono accedere alle informazioni aziendali ospitate da Exchange Online. Con Intune è possibile controllare facilmente a chi e a quali app viene consentito l'accesso configurando i criteri di accesso condizionale delle app che limitano l'accesso ai servizi di Office 365 solo alle applicazioni che supportano i criteri di protezione delle app di Intune. Ad esempio, dal [portale di Azure](https://portal.azure.com) è possibile creare un criterio che limita l'accesso a Exchange Online solo a determinati gruppi e applicazioni su Android e iOS indipendentemente dal fatto che il dispositivo sia gestito o meno.

- **Creare un criterio di accesso condizionale a Exchange Online per la protezione delle app.** [Questi criteri vengono creati](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-exchange-online) nello stesso posto dei criteri di protezione delle app descritti in precedenza. Oltre a definire le applicazioni a cui è consentito accedere a Exchange Online, è necessario definire i gruppi di accesso utenti per gestire le connessioni a Exchange Online.

- Gli utenti dovranno **configurare un'applicazione broker** la prima volta che tentano di usare un'app supportata dai criteri per accedere a Exchange Online. Per i dispositivi iOS l'applicazione è l'app Microsoft Authenticator e per i dispositivi Android è necessario installare l'app Portale aziendale di Microsoft Intune. [Le applicazioni broker](https://docs.microsoft.com/intune/deploy-use/use-apps-with-mam-ca) registrano il dispositivo con Azure AD per consentire la verifica dell'identità del dispositivo, ma non registrano il dispositivo nella gestione.

Con i criteri di accesso condizionale per Exchange Online definiti, gli utenti riceveranno un messaggio simile al seguente quando tentano di accedere alla posta elettronica azienda usando il client di posta elettronica nativo, come illustrato in un dispositivo Android:

![Requisito dell'app Outlook per i criteri di protezione delle app](..\Solutions\media\protect-company-data-without-managing-devices\protect-company-data-without-managing-devices-fig2.png)

Quando l'utente tocca il collegamento *Inizia ora* nel messaggio di posta elettronica, il Web browser predefinito per il dispositivo si apre e visualizza https://portal.manage.microsoft.com/OutlookRedirect.aspx. Viene quindi chiesto all'utente di installare l'app Microsoft Outlook gratuita dall'App Store nel dispositivo.

### <a name="learn-more"></a>Altre informazioni

[Iniziare a usare Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)

