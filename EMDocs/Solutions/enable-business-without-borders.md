---
title: Consentire un business senza confini
description: Questo articolo descrive come usare Enterprise Mobility + Security per fornire una singola identità da usare con asset cloud e locali per garantire agli utenti la massima produttività, sfruttando gli strumenti di Azure Active Directory.
keywords: ''
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 12/07/2016
ms.topic: solution
ms.prod: ''
ms.service: active-directory
ms.technology: ''
ms.assetid: 38e9802b-d8c0-4f5c-b89d-8ce1e04f7387
ROBOTS: ''
ms.reviewer: atkladak, jsnow
ms.suite: ems
ms.openlocfilehash: 756df8b2432788ba1152c5ef5a195d84cd6cf82b
ms.sourcegitcommit: 573bba4fa70ce651971ec5bafd9967ebdd6bd6c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
ms.locfileid: "34474004"
---
# <a name="enable-business-without-borders"></a>Consentire un business senza confini
L'identità non è un'opzione, ma un elemento fondamentale per una forza lavoro efficiente. Le organizzazioni devono consentire ai propri dipendenti di accedere a tutti i dati e a tutte le applicazioni da ogni dispositivo e da qualunque luogo. Gli utenti devono poter collaborare tra loro e con i partner e comunicare con i clienti. Gli strumenti usati non si trovano più in un ambiente protetto e controllato, ma in un cloud pubblico.

Questo nuovo assetto introduce sfide e minacce avanzate che non possono essere attenuate con gli strumenti tradizionali. È inutile proteggere solo la rete, quando il nuovo confine è rappresentato dall'utente. Il segreto per essere produttivi e protetti in un ambiente di questo tipo è rappresentato da una soluzione avanzata di gestione delle identità.

## <a name="how-can-enterprise-mobility--security-help-you"></a>Vantaggi di Enterprise Mobility + Security
Enterprise Mobility + Security (EMS) è l'unica soluzione cloud completa che protegge in modo nativo i dati aziendali nel dispositivo stesso e con quattro livelli di protezione per identità, dispositivi, app e dati. EMS aiuta a rispondere a una delle esigenze principali degli ambienti incentrati su dispositivi mobili e cloud, ovvero fornire una singola identità che funzioni con qualsiasi asset cloud e locale, consentendo agli utenti di lavorare nel modo più produttivo possibile.

### <a name="access-to-single-sign-on-applications"></a>Accesso alle applicazioni Single Sign-On
Con la federazione delle identità e l'accesso Single Sign-On, gli utenti hanno un set di credenziali di accesso e password e il personale IT può gestire in modo più efficiente le identità degli utenti.
### <a name="multi-factor-authentication"></a>Multi-Factor Authentication
Gli utenti possono anche introdurre nuovi dispositivi nell'azienda, ma il reparto IT può verificare che i dispositivi che si connettono alla rete siano di proprietà e controllati da utenti con le credenziali appropriate. Multi-Factor Authentication (MFA) offre un livello di protezione aggiuntivo.
### <a name="self-service-group-management"></a>Gestione dei gruppi in modalità self-service
Quando gli utenti dimenticano le password, possono reimpostarle autonomamente, riducendo così il carico di lavoro del reparto IT e ottenendo una maggiore efficienza grazie alla possibilità di risolvere rapidamente il problema.
### <a name="cross-organization-collaboration"></a>Collaborazione tra organizzazioni
La collaborazione tra aziende è importante per il 97% dei clienti Microsoft, che la considerano un requisito essenziale per lavorare con i partner. La collaborazione B2B (Business to Business) di Azure Active Directory supporta le relazioni tra società, consentendo ai partner di accedere in modo selettivo alle applicazioni e ai dati aziendali usando identità gestite autonomamente.

## <a name="recommended-solution"></a>Soluzione consigliata
La [collaborazione B2B (Business to Business) di Azure Active Directory ](https://azure.microsoft.com/documentation/articles/active-directory-b2b-what-is-azure-ad-b2b/) è la soluzione consigliata che consente alle organizzazioni di accedere a tutto il necessario da qualsiasi posizione, in modo sicuro e produttivo, sfruttando anche gli investimenti esistenti negli strumenti tradizionali.
- I professionisti IT forniscono a organizzazioni partner e collaboratori l'accesso ai dati e alle applicazioni della propria organizzazione.
- Gli utenti partner operano "per conto di", come rappresentanti o dipendenti dell'organizzazione.
- Verifiche di accesso, verifica della posta elettronica, elenchi di operazioni consentite e non consentite e così via regolano l'accesso alle risorse e alle applicazioni host.
- Gli utenti partner sono individuabili e possono vedere gli altri utenti della propria organizzazione (in base ai criteri).

### <a name="how-azure-ad-b2b-collaboration-works"></a>Come funziona la collaborazione B2B di Azure AD

La collaborazione B2B di Azure AD si basa su un modello di invito e riscatto, che utilizza gli indirizzi di posta elettronica dei partner con cui si vuole lavorare e le rispettive applicazioni che si vuole usare.

1. L'amministratore accede al portale di Azure e invita gli utenti partner importando un file CSV contenente le informazioni su di essi.
2. Il portale di Azure invia messaggi di posta elettronica ai partner.
3. I partner fanno clic sul collegamento nel messaggio di posta elettronica ricevuto dal portale di Azure. Se l'utente partner è già in Azure AD, gli viene chiesto di immettere le credenziali aziendali, in caso contrario, l'utente partner dovrà effettuare l'accesso come utente di Collaborazione B2B di Azure AD.
4. L'utente partner viene automaticamente reindirizzato all'applicazione in cui è stato invitato a collaborare.

![Grafico che mostra il processo tramite cui un utente partner viene invitato a collaborare con B2B di Azure AD.](./media/enable-business-without-borders/enable-business-without-borders-fig1.png)

## <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
I passaggi seguenti descrivono come implementare ogni aspetto della collaborazione B2B di Azure AD illustrato in precedenza. Ogni collegamento rappresenta un set diverso di articoli con un set specifico di istruzioni o passaggi da implementare nell'organizzazione:
- Informazioni su [come usare la collaborazione B2B di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-b2b-detailed-walkthrough/).
- Informazioni su [come usare un file CSV per specificare le informazioni degli utenti partner](https://azure.microsoft.com/documentation/articles/active-directory-b2b-references-csv-file-format/).
