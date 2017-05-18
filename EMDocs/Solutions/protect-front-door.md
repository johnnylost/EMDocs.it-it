---
title: Proteggere l&quot;ingresso principale | Microsoft Docs
description: "Uno scenario che descrive come Enterprise Mobility + Security può essere usato per proteggere l&quot;identità e garantire un accesso sicuro alle risorse aziendali tramite le funzionalità di Microsoft Azure Active Directory Identity Protection e Azure Active Directory Privileged Identity Management."
author: yuridio
ms.author: yurid
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: solution
ms.prod: 
ms.service: active-directory
ms.technology: techgroup-identity
ms.assetid: c9aeabcf-db9b-4a35-b1bc-61331c464165
ms.reviewer: v-craic
ms.suite: ems
ms.custom: microsoft-identity-manager
ms.translationtype: Human Translation
ms.sourcegitcommit: 5d9a4bd18660a573b2dd76c0263b89ecf5ae4610
ms.openlocfilehash: 7912b13666c9b08af0c6d962fe1ea592335ca73d
ms.contentlocale: it-it
ms.lasthandoff: 01/24/2017


---

# <a name="protect-at-the-front-door"></a>Proteggere l'ingresso principale

Le soluzioni di sicurezza tradizionali erano sufficienti per proteggere il proprio lavoro. Ma questo avveniva prima che il settore della mobilità crescesse aumentando le possibilità di attacco e il passaggio al cloud rendesse più complesse le interazioni dei dipendenti con altri utenti, dispositivi, app e dati. Al giorno d'oggi per proteggere il proprio lavoro è necessario un approccio alla sicurezza più olistico e innovativo in grado di proteggere, individuare e reagire a minacce di tutti i tipi in locale e sul cloud.

In oltre il 63% delle violazioni dei dati, gli utenti malintenzionati riescono ad accedere alla rete aziendale usando credenziali utente deboli, predefinite o rubate.  La sicurezza basata sull'identità di Microsoft è imperniata sulle credenziali utente, impedendo il furto delle credenziali tramite la gestione e la protezione delle identità, incluse le identità con e senza privilegi.


## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?

L'approccio alla sicurezza di Enterprise Mobility + Security (EMS) inizia con un'identità comune protetta per un accesso sicuro a tutte le risorse aziendali in locale e sul cloud con un [accesso condizionale](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access/) basato sul rischio. Con questo approccio, i responsabili IT possono proteggere le risorse aziendali all'ingresso principale con accessi condizionali basati sul rischio innovativi e avanzati. EMS offre un'unica identità comune protetta per l'accesso a migliaia di app rendendo più semplice per i responsabili IT la gestione e la protezione delle identità con privilegi.

## <a name="recommended-solution"></a>Soluzione consigliata

Per soddisfare le esigenze di questo scenario, EMS usa [Azure AD Identity Protection](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/) e [Azure AD Privileged Identity Management](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-configure/). Con l'implementazione di queste tecnologie, le organizzazioni saranno in grado di:

- Ottenere informazioni da una visualizzazione consolidata del rilevamento delle minacce basato su Machine Learning
- Correggere gli elementi consigliati
- Eseguire il calcolo di gravità del rischio
- Eseguire automaticamente l'accesso condizionale basato sul rischio per la protezione contro accessi sospetti e credenziali compromesse
- Applicare l'accesso amministrativo su richiesta JIT (Just-In-Time) quando necessario
- Usare avvisi, report di controllo e verifiche di accesso

La figura seguente riepiloga le funzionalità usate nello scenario e descrive come vengono usate per proteggere le risorse:

![Protezione delle risorse](./media/protect-front-door/protect-front-door-fig1.png)

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione

Seguire questa procedura per implementare Azure AD Identity Protection e Azure AD Privileged Identity Management:

- Passaggio 1: Abilitare Azure AD Identity Protection
- Passaggio 2: Configurare Azure AD Identity Protection
- Passaggio 3: Monitorare l'accesso alle risorse
- Passaggio 4: Abilitare Azure AD Privileged Identity Management
- Passaggio 5: Configurare Azure AD Privileged Identity Management
- Passaggio 6: Operazioni di Privileged Identity Management


## <a name="how-to-protect-your-resources-at-the-front-door"></a>Come proteggere le risorse all'ingresso principale

Organizzazioni diverse avranno posizioni differenti relativamente alla priorità degli eventi imprevisti. Ciò che è critico per una line-of-business potrebbe non esserlo per un'altra. Per questa ragione è necessario innanzitutto scoprire come Azure AD Identity Protection classifica il [livello di rischio](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#detection-and-risk) (alto, medio o basso) che è un'indicazione della gravità dell'evento di rischio. Azure AD Identity Protection valuta anche la probabilità che l'identità dell'utente sia stata compromessa e assegna un proprio livello di rischio denominato [livello di rischio dell'utente](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#what-is-a-user-risk-level). Azure AD Identity Protection identifica una [vulnerabilità](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection-vulnerabilities/) alla quale assegna un livello di rischio. Esistono diversi [tipi di rischio](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection-risk-events-types/), ognuno classificato in base alla criticità. Eseguire i passaggi da 1 a 3 per abilitare, implementare e monitorare le risorse usando Azure AD Identity Protection.

La seconda fase di questa soluzione (passaggi da 4 a 6) implementerà Azure Active Directory (AD) Privileged Identity Management per individuare, limitare e monitorare le identità con privilegi. Le organizzazioni che usano Azure possono [assegnare ruoli in Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/). Azure AD Privileged Identity Management è in grado di gestire [alcuni di questi ruoli](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-roles/).

### <a name="step-1-enable-azure-ad-identity-protection"></a>Passaggio 1: Abilitare Azure AD Identity Protection

Prima di procedere all'implementazione di questa soluzione, verificare che una [licenza Azure AD Premium](https://azure.microsoft.com/documentation/articles/active-directory-get-started-premium/) sia assegnata all'utente finale. Se si usa un dominio federato e si vuole imporre la modifica delle password nel cloud per eseguirne il writeback in locale, è necessario abilitare il [writeback delle password](https://azure.microsoft.com/documentation/articles/active-directory-passwords-getting-started/). Dopo aver rivisto questi requisiti, [abilitare Azure AD Identity Protection](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection-enable/) installandolo da Marketplace. Al termine dell'installazione, sarà possibile accedere al dashboard di Azure AD Identity Protection che potrebbe essere vuoto come mostra l'immagine seguente.

![Azure AD Identity Protection](./media/protect-front-door/protect-front-door-fig2.png)

### <a name="step-2-configure-azure-ad-identity-protection"></a>Passaggio 2: Configurare Azure AD Identity Protection

Se si prevede di implementare Azure AD Identity Protection, è necessario iniziare definendo i criteri seguenti:

- [Criteri di registrazione per l'autenticazione a più fattori](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#multi-factor-authentication-registration-policy): consente ai responsabili IT di applicare l'autenticazione a più fattori per gli utenti.
- [Criteri di rischio utente](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#user-risk-security-policy): consente ai responsabili IT di impostare i criteri di rischio di un utente per bloccare gli utenti all'accesso a seconda del livello di rischio.
- [Criteri di rischio di accesso](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#sign-in-risk-security-policy): consente ai responsabili IT di valutare il rischio di un accesso specifico e, in base al risultato, applicare attenuazioni usando condizioni e regole predefinite.

Questi criteri sono disponibili nel dashboard di Azure AD Identity Protection nella sezione **Configura** come illustrato nella schermata seguente:

![Criteri](./media/protect-front-door/protect-front-door-fig3.png)

Oltre a configurare i criteri di sicurezza, è anche possibile specificare gli utenti che riceveranno gli avvisi. Usare l'opzione **Avvisi** nella sezione Impostazioni del dashboard di Azure AD Identity Protection come illustrato nell'immagine seguente:

![Avvisi](./media/protect-front-door/protect-front-door-fig4.png)

Si noti che in questa configurazione gli utenti ricevono gli avvisi solo se il livello di rischio dell'utente è **alto**.

### <a name="step-3-monitor-and-remediation"></a>Passaggio 3: Monitorare e correggere

Un monitoraggio continuo è parte integrante di qualsiasi operazione di sicurezza. Usando le funzionalità di [ricerca della causa](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#investigation) di Azure AD Identity Protection, i responsabili IT potranno visualizzare informazioni sul rilevamento delle minacce basato su Machine Learning con notifiche e consigli per la correzione. È possibile usare il dashboard di Azure AD Identity Protection per valutare rapidamente l'ambiente corrente e identificare con facilità i problemi da risolvere in base alla loro criticità. In alternativa, è possibile limitare l'indagine alle aree seguenti indicate nella sezione Ricerca causa nel dashboard di Azure AD Identity Protection:

![Ricerca della causa](./media/protect-front-door/protect-front-door-fig5.png)

Dopo aver ricercato la causa in ciascuna delle aree, gli amministratori possono intervenire per mitigare gli [utenti a rischio](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#mitigating-user-risk-events) o gli [eventi di accesso](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#mitigating-sign-in-risk-events). Ad esempio, se si identifica un evento di sicurezza come il secondo evento della schermata seguente [Trasferimento impossibile a posizioni atipiche](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection-risk-events-types/#impossible-travel-to-atypical-locations), è possibile intervenire per [correggere](https://azure.microsoft.com/documentation/articles/active-directory-identityprotection/#remediating-user-risk-events) la minaccia imponendo ad esempio la reimpostazione della password.

![Eventi di rischio](./media/protect-front-door/protect-front-door-fig6.png)

È anche possibile usare i [report di accesso e di utilizzo di Azure AD Premium](https://azure.microsoft.com/documentation/articles/active-directory-view-access-usage-reports/) per ottenere altre informazioni sul comportamento di un utente e su minacce potenziali.

### <a name="step-4-enable-azure-ad-privileged-identity-management"></a>Passaggio 4: Abilitare Azure AD Privileged Identity Management

Per accedere a Azure AD Privileged Identity Management è necessario innanzitutto [installarlo da Marketplace](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-getting-started/). Azure AD Privileged Identity Management e Azure Multi-Factor Authentication (MFA) vengono usati insieme per consentire ai responsabili IT di gestire l'accesso per proteggere applicazioni e servizi. Dopo aver installato Azure AD Privileged Identity Management verrà eseguito un test per verificare se si è in grado di usare MFA. Quando si fa clic sull'opzione per la verifica del proprio account, si viene reindirizzati a una pagina Web in cui è necessario immettere le proprie credenziali. Se il proprio account non è ancora abilitato per MFA, verrà visualizzato un messaggio simile a quello illustrato nella schermata seguente:

![Schermata di accesso](./media/protect-front-door/protect-front-door-fig7.png)

Fare clic su **Imposta ora** e seguire le istruzioni della procedura guidata. È necessario immettere il numero di cellulare o di telefono per la verifica. Dopo aver completato la procedura guidata, verrà visualizzato il messaggio di verifica completata:

![Verifica](./media/protect-front-door/protect-front-door-fig8.png)

### <a name="step-5-configure-azure-ad-privileged-identity-management"></a>Passaggio 5: Configurare Azure AD Privileged Identity Management

La configurazione iniziale viene eseguita usando una [procedura guidata relativa alla sicurezza](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-security-wizard/) che prevede tre fasi come illustrato nel pannello **Protezione dell'organizzazione**:

![Procedura guidata relativa alla sicurezza](./media/protect-front-door/protect-front-door-fig9.png)

Nella prima fase si esamineranno i [ruoli con privilegi](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-roles/) che sono stati individuati da Azure AD Privileged Identity Management. La seconda fase ha lo scopo di limitare il numero di utenti dell'organizzazione con assegnazioni di ruolo con privilegi permanenti riducendo al minimo la vulnerabilità alle violazioni della protezione. L'ultima fase consente di rivedere le modifiche ai ruoli con privilegi degli utenti.

Se durante questo processo è stato concesso a un altro utente un ruolo amministrativo, l'utente è stato reso idoneo a eseguire operazioni con tale ruolo e sarà possibile [attivare il ruolo](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-how-to-activate-role/) nel caso in cui sia necessario eseguire un'attività che richiede tale ruolo.

### <a name="step-6-privileged-identity-management-operations"></a>Passaggio 6: Operazioni di Privileged Identity Management

Dopo aver installato e configurato Azure AD Privileged Identity Management, è possibile eseguire la valutazione iniziale per verificare lo schema del ruolo corrente e gli avvisi. Nel pannello **Privilege Identity Management** fare clic su **Gestione dei ruoli con privilegi** per visualizzare un dashboard simile a quello illustrato nell'immagine seguente:

![Ruoli con privilegi](./media/protect-front-door/protect-front-door-fig10.png)

Nel dashboard è possibile visualizzare l'attività corrente, ad esempio gli [avvisi di sicurezza](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-how-to-configure-security-alerts/) e la [verifica di accesso](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-how-to-start-security-review/). È anche possibile usare il dashboard per [aggiungere](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-how-to-give-access-to-pim/) o [rimuovere](https://azure.microsoft.com/documentation/articles/active-directory-privileged-identity-management-how-to-give-access-to-pim/#remove-another-users-access-rights-for-managing-pim) l'accesso di uno o più utenti ad Azure AD Privileged Identity Management.

