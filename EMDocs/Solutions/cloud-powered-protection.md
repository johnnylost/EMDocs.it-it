---
title: Protezione basata sul cloud
description: Questo articolo descrive come usare Enterprise Mobility + Security per offrire un set completo di strumenti per la sicurezza in modo da identificare le minacce per la sicurezza in modo proattivo e rispondervi correttamente nell'organizzazione tramite gli strumenti inclusi in Azure Active Directory.
keywords: 
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/24/2016
ms.topic: solution
ms.prod: 
ms.service: active-directory
ms.technology: 
ms.assetid: 46654ab0-0d0a-47ad-8715-b149a1092a37
ROBOTS: 
ms.reviewer: atkladak, jsnow
ms.suite: ems
ms.openlocfilehash: 0ed7704a832f3567f14c6eec5ae7da9ea5e9f22a
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="cloud-powered-protection"></a>Protezione basata sul cloud
Microsoft è impegnata nella protezione delle identità basate sul cloud da oltre un decennio e con Azure Active Directory sta rendendo questi stessi sistemi di protezione disponibili ai clienti aziendali, per garantire la responsabilità di utenti e amministratori attraverso livelli migliori di sicurezza e governance.

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS permette di affrontare una delle principali sfide degli scenari incentrati su mobilità e cloud, per offrire un set completo di strumenti per la sicurezza che aiutano a identificare in modo proattivo le minacce per la sicurezza e a rispondervi in modo adeguato nell'organizzazione:
- Controllare l'accesso alle risorse
- Proteggere l'autenticazione utente
- Rispondere a minacce avanzate con monitoraggio e criteri basati sui rischi
- Ridurre i rischi amministrativi
- Governance delle identità locali e cloud

Azure Active Directory Identity Protection è unico. Usando Machine Learning per analizzare oltre 10 TB di dati comportamentali e contestuali ogni giorno, offre visibilità delle attività sospette e permette di intervenire immediatamente se necessario.

Inoltre, le regole di accesso condizionale di Azure AD permettono ai clienti di controllare l'accesso ai servizi online in base ad attributi come la conformità del dispositivo o il percorso di rete. È possibile distinguere tra i tipi seguenti:
- Accesso condizionale basato su MFA di Azure AD
- Accesso condizionale basato sul percorso di Azure AD
- Accesso condizionale basato sul dispositivo di Azure AD


## <a name="recommended-solution"></a>Soluzione consigliata
### <a name="azure-active-directory-identity-protection"></a>Azure Active Directory Identity Protection

Azure AD Identity Protection è un servizio di sicurezza che offre una visualizzazione consolidata degli eventi di rischio e delle potenziali vulnerabilità che possono colpire le identità dell'organizzazione:
- Rispondere a minacce avanzate con monitoraggio e criteri basati sui rischi (Azure AD Identity Protection)
- Ridurre i rischi amministrativi (Privileged Identity Manager)
- Governance dell'identità

In un mondo in cui aumentano continuamente eventi imprevisti di furto delle identità, utenti malintenzionati insistenti e frequenti violazioni della sicurezza, Azure AD Identity Protection è uno strumento indispensabile.

Il dashboard di Azure AD Identity Protection offre accesso a report relativi, ad esempio, a utenti contrassegnati per il rischio, eventi di rischio e vulnerabilità. Offre inoltre impostazioni come la configurazione di criteri di sicurezza, notifiche e registrazione con autenticazione a più fattori.
### <a name="azure-ad-conditional-access"></a>Accesso condizionale di Azure AD
Il passaggio a servizi cloud e una sempre più pressante esigenza di mobilità impongono alle organizzazioni di trovare soluzioni per la protezione dei dati in grado di migliorare allo stesso tempo la produttività degli utenti e la flessibilità dei dispositivi. I clienti vogliono poter controllare l'accesso a Office 365 in base a diversi attributi, come percorsi di rete o applicazione di MFA. Questo è un aspetto particolarmente importante per i clienti soggetti a normative, come i clienti appartenenti al settore pubblico o a quello finanziario.

Poiché la protezione dei dati all'interno della rete perimetrale non è più sufficiente, le organizzazioni hanno bisogno di poter controllare l'accesso utente anche in base ad altri fattori, come la conformità dei dispositivi.

Le regole di accesso condizionale di Azure AD vengono applicate per ogni applicazione e sono disponibili ai clienti per controllare l'accesso in base a condizioni diverse. Usando la gestione dei dispositivi mobili (MDM) per Office 365 o Intune, i clienti devono poter limitare l'accesso a Office 365 ai soli utenti che usano un dispositivo aziendale o che hanno registrato il proprio dispositivo personale per la gestione.

Ad esempio, i clienti possono configurare regole di accesso condizionale per applicare controlli come i seguenti:
- Permettere l'accesso solo da dispositivi aggiunti a un dominio o conformi
- Applicare MFA per tutto l'accesso ai servizi di Exchange Online
- Impedire l'accesso a SharePoint Online ai client esterni alla rete aziendale.

## <a name="how-to-implement-these-solutions"></a>Come implementare questa soluzione?

Di seguito vengono descritti i passaggi necessari per iniziare a usare Azure AD Identity Protection e l'accesso condizionale. Questa sezione contiene inoltre alcuni articoli sulle procedure che offrono altri dettagli per i passaggi specifici.

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection
Azure AD Identity Protection è disponibile con l'offerta Azure AD Premium 2, in combinazione con Azure AD Privileged Identity Management per offrire funzionalità di criteri di accesso condizionale uniformi.

Per abilitare Azure AD Identity Protection, è possibile accedere ad Azure Marketplace e cercare "Identity Protection", quindi fare clic sul riquadro Azure AD Identity Protection, che apre il dashboard con una visualizzazione consolidata dei dati a rischio per il tenant. Di seguito vengono evidenziati alcuni esempi del modo in cui Identity Protection può aiutare l'organizzazione ad affrontare le minacce per la sicurezza degli account.

#### <a name="risk-events"></a>Eventi di rischio
Gli eventi di rischio sono eventi contrassegnati come sospetti da Identity Protection e indicano che un'identità può essere stata compromessa.

Microsoft sta continuando a investire in questa area e prevede di migliorare continuamente l'accuratezza del rilevamento degli eventi di rischio esistenti e di aggiungere nuovi tipi di evento di rischio regolarmente. Ad esempio, si supponga di poter indagare sull'evento di rischio Comunicazione impossibile.

Per altri dettagli, vedere la [guida ad Azure AD Identity Protection](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-playbook/).

Ecco un esempio di alcuni eventi di rischio nel dashboard di Identity Protection:

![Screenshot che mostra alcuni eventi di rischio elencati nel dashboard di Azure AD Identity Protection.](./media/cloud-powered-protection/cloud-powered-protection-fig1.png)

#### <a name="impossible-travels-risk"></a>Rischio Comunicazione impossibile
Nel pannello Comunicazione impossibile tutti gli eventi imprevisti contrassegnati sono visualizzati in base alle posizioni del primo e secondo accesso e all'ora di ogni accesso.

![Screenshot del dashboard di Azure AD Identity Protection che mostra le posizioni degli eventi di rischio "Comunicazione impossibile".](./media/cloud-powered-protection/cloud-powered-protection-fig2.png)

Sono disponibili altri dettagli sui [tipi di eventi di rischio rilevati da Azure AD Identity Protection](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-risk-events-types/).

#### <a name="remediation"></a>Soluzione
Oltre alla gestione degli eventi imprevisti su base individuale, Azure AD Identity Protection permette di risolvere i possibili problemi tramite un approccio proattivo configurando criteri di correzione del rischio utente. All'interno delle impostazioni dei criteri è possibile scegliere come destinazione singoli utenti, gruppi o tutti gli utenti. È anche possibile impostare le condizioni specifiche che attiveranno i criteri.

![Screenshot che mostra come prevenire gli eventi di rischio direttamente dal dashboard di Azure AD Identity Protection.](./media/cloud-powered-protection/cloud-powered-protection-fig3.png)

Infine, è possibile scegliere se bloccare l'accesso interamente o se consentire l'accesso, ma con i requisiti di:
- Multi-Factor Authentication
- Registrazione di Azure MFA
- Modifica delle password

Altri dettagli sono disponibili in [Azure AD Identity Protection](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection/) e in questo [post di blog su Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/07/azuread-identity-protection-azure-ad-privileged-identity-management-and-azure-ad-premium-p2-will-be-generally-available-sept-15th/).

### <a name="azure-ad-conditional-access"></a>Accesso condizionale di Azure AD
I collegamenti seguenti offrono informazioni sull'uso dell'accesso condizionale di Azure AD in base a Multi-Factor Authentication (MFA), percorso e criteri dei dispositivi.
- Informazioni su [come implementare l'accesso condizionale di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access/).
- Informazioni su [MFA e criteri percorso](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-azuread-connected-apps/).
- Informazioni su [Criteri basati sul dispositivo](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).
