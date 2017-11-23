---
title: Distribuire siti per tre livelli di protezione | Microsoft Docs
description: Creare e configurare siti del team di SharePoint Online in Office 365 per vari livelli di protezione delle informazioni.
services: active-directory
keywords: Office 365, Windows 10, Enterprise Mobility + Security, Microsoft 365 Enterprise
documentationcenter: 
author: JoeDavies-MSFT
manager: laurawi
ms.assetid: 
ms.prod: microsoft-365-enterprise
ms.service: 
ms.workload: 
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 09/11/2017
ms.author: josephd
ms.openlocfilehash: 0c4e7eaf6449b551a0a6222d475b2c42f49550f9
ms.sourcegitcommit: 684c942047754e93378e271f5b1a659a9752f0ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="deploy-sites-for-three-tiers-of-protection"></a>Distribuire siti per tre livelli di protezione

## <a name="introduction"></a>Introduzione

Usare i passaggi descritti in questo articolo per progettare e distribuire siti del team di SharePoint Online di base, sensibili e con riservatezza elevata. Per altre informazioni su questi tre livelli di protezione, vedere [Proteggere siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md).

## <a name="baseline-sharepoint-online-team-sites"></a>Siti del team di SharePoint Online di base
La protezione di siti di base include siti del team pubblici e privati. I siti del team pubblici possono essere individuati e usati da qualsiasi persona dell'organizzazione. I siti privati possono essere individuati e usati solo dai membri del gruppo di Office 365 associato al sito del team. Entrambi questi tipi di siti del team consentono ai membri di condividere il sito con altri utenti.

### <a name="public"></a>Pubblico
Per creare un sito del team di SharePoint Online di base con accesso pubblico e autorizzazioni, seguire questa procedura:

1. Accedere al **portale di Office 365** con un account che verrà usato anche per gestire il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea sito** fare clic su **Sito del team**.
5. In **Nome sito** digitare il nome del sito del team pubblico. 
6. In **Team site description** (Descrizione sito del team) digitare una descrizione dello scopo del sito.
7. In **Impostazioni privacy** selezionare **Public – anyone in the organization can access this site** (Pubblico: qualsiasi persona dell'organizzazione può accedere a questo sito) e quindi fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.

Di seguito è riportata la configurazione risultante.

 ![SharePoint di base pubblico](./media/deploy-sites-for-three-tiers-of-protection/pub_site.png)

### <a name="private"></a>Private
Per creare un sito del team di SharePoint Online di base con accesso privato e autorizzazioni, seguire questa procedura:

1. Se necessario, accedere al **portale di Office 365** con un account che verrà usato anche per gestire il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea sito** fare clic su **Sito del team**.
5. In **Nome sito** digitare il nome del sito del team privato. 
6. In **Team site description** (Descrizione sito del team) digitare una descrizione dello scopo del sito.
7. In **Impostazioni privacy** selezionare **Private – only members can access this site** (Privato: solo i membri possono accedere a questo sito) e quindi fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) in **Aggiungi membri** digitare i nomi degli account utente che hanno accesso a questo sito del team privato.
9. Quando il set iniziale di membri è stato aggiunto al sito, fare clic su **Fine**.

Di seguito è riportata la configurazione risultante.

 ![SharePoint di base privato](./media/deploy-sites-for-three-tiers-of-protection/priv_site.png)

## <a name="sensitive-sharepoint-online-team-sites"></a>Siti del team di SharePoint Online sensibili
Un sito del team di SharePoint Online sensibile è un sito del team isolato in cui le autorizzazioni sono controllate tramite l'appartenenza ai gruppi di SharePoint anziché l'appartenenza al gruppo di Office 365 associato al sito del team.

Per creare un sito del team isolato, seguire questi due passaggi principali.

### <a name="step-1-design-your-isolated-site"></a>Passaggio 1: Progettare un sito isolato
Per progettare un sito del team isolato è necessario stabilire:

* I gruppi di SharePoint e i livelli di autorizzazione.
* Il set di gruppi di accesso che saranno membri dei gruppi di SharePoint.
 Il set di gruppi di accesso consigliato è uno per i membri del sito, uno per i visualizzatori del sito e uno per gli amministratori del sito.
* Se verranno usati gruppi nidificati all'interno dei gruppi di accesso.

Ad esempio, la struttura dei gruppi di SharePoint e i livelli di autorizzazione consigliati sono simili ai seguenti:

|**Gruppo di SharePoint**|**Livello di autorizzazione**|**Gruppo di accesso (esempi)**|
|:-----|:-----|:-----|
|Membri di [nome sito]|Modifica|Membri di [nome sito]|
|Visitatori di [nome sito]|Lettura|Visualizzatori di [nome sito]|
|Proprietari di [nome sito]|Controllo completo|Amministratori di [nome sito]|

Per un sito del team, i gruppi e i livelli di autorizzazione di SharePoint vengono creati per impostazione predefinita. È necessario stabilire i nomi dei gruppi di accesso.

Per i dettagli del processo di progettazione, vedere [Progettare un sito del team SharePoint Online isolato](https://technet.microsoft.com/library/mt784687.aspx).

### <a name="step-2-deploy-your-isolated-site"></a>Passaggio 2: Distribuire un sito isolato
Per distribuire un sito isolato è innanzitutto necessario:

* Stabilire gli account utente e i gruppi da aggiungere a ogni gruppo di accesso.
* Creare i gruppi di accesso e aggiungere i membri di tipo utente e gruppo.

Per istruzioni dettagliate, vedere la **Fase 1** di [Distribuire un sito del team di SharePoint Online isolato](https://technet.microsoft.com/library/mt784693.aspx).

Creare quindi il sito del team di SharePoint Online seguendo questa procedura.

1. Se necessario, accedere al **portale di Office 365** con un account che verrà usato anche per gestire il sito del team di SharePoint Online (un amministratore di SharePoint Online). Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova **scheda SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea sito** fare clic su **Sito del team**.
5. In **Nome sito** digitare il nome del sito del team privato.
6. Nella descrizione **Sito del team** digitare una descrizione facoltativa.
7. In **Impostazioni privacy** selezionare **Private – only members can access this site** (Privato: solo i membri possono accedere a questo sito) e quindi fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.

Dal nuovo sito del team di SharePoint Online configurare quindi le autorizzazioni seguendo questa procedura.

1. Stabilire il nome dell'entità utente dell'amministratore IT o di un'altra persona che avrà la responsabilità di rispondere e occuparsi delle richieste di accesso al sito (belindan@contoso.com è un esempio di nome dell'entità utente). Prendere nota di questo nome.
2. Nella barra degli strumenti fare clic sull'icona delle impostazioni e quindi su **Autorizzazioni sito**.
3. Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).
4. Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.
5. Nella finestra di dialogo **Impostazioni richieste di accesso**:
  1. Deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e singoli file e cartelle** e **Consenti ai membri di invitare altre persone nel gruppo di membri del sito**.
  2. Digitare il nome dell'entità utente dell'amministratore IT al passaggio 1 in **Invia tutte le richieste di accesso**.
  3. Fare clic su **OK**.
6. Nella scheda **Autorizzazioni** del browser fare clic su **Membri di [nome sito]** nell'elenco.
7. In **Utenti e gruppi** fare clic su **Nuovo**. Nella finestra di dialogo **Condividi** digitare il nome del gruppo di accesso dei membri del sito per questo sito, selezionarlo e quindi fare clic su **Condividi**.
8. Fare clic sul pulsante Indietro del browser e su **Proprietari di [nome sito]** nell'elenco.
9. In **Utenti e gruppi** fare clic su **Nuovo**. Nella finestra di dialogo **Condividi** digitare il nome del gruppo di accesso degli amministratori del sito per questo sito, selezionarlo e quindi fare clic su **Condividi**.
10. Fare clic sul pulsante Indietro del browser e su **Visitatori di [nome sito]** nell'elenco.
11. In **Utenti e gruppi** fare clic su **Nuovo**. Nella finestra di dialogo **Condividi** digitare il nome del gruppo di accesso dei visualizzatori del sito per questo sito, selezionarlo e quindi fare clic su **Condividi**.
12. Chiudere la scheda **Autorizzazioni** del browser.

Di seguito sono riportati i risultati di queste impostazioni di autorizzazione:

* Il gruppo di SharePoint **Proprietari di [nome sito]** contiene il gruppo di accesso degli amministratori del sito in cui tutti i membri hanno il livello di autorizzazione **Controllo completo**.
* Il gruppo di SharePoint **Membri di [nome sito]** contiene il gruppo di accesso dei membri del sito in cui tutti i membri hanno il livello di autorizzazione **Modifica**.
* Il gruppo di SharePoint **Visitatori di [nome sito]** contiene il gruppo di accesso dei visualizzatori del sito in cui tutti i membri hanno il livello di autorizzazione **Lettura**.
* La possibilità per i membri di invitare altri membri è disabilitata. 
* La possibilità per gli utenti non membri di richiedere l'accesso è abilitata. 

Di seguito è riportata la configurazione risultante.

 ![Protezione di siti sensibili](./media/deploy-sites-for-three-tiers-of-protection/sens_site.png)

I membri del sito, attraverso l'appartenenza a uno dei gruppi di accesso, possono ora collaborare in modo sicuro alle risorse del sito.

## <a name="highly-confidential-sharepoint-online-team-sites"></a>Siti del team di SharePoint Online con riservatezza elevata
Un sito del team di SharePoint Online con riservatezza elevata è un sito del team isolato in cui le autorizzazioni sono controllate tramite l'appartenenza ai gruppi di SharePoint anziché l'appartenenza al gruppo di Office 365 associato al sito del team.

La creazione di un sito del team isolato per le informazioni e la collaborazione con riservatezza elevata richiede due passaggi principali.

### <a name="step-1-design-your-isolated-site"></a>Passaggio 1: Progettare un sito isolato
Per progettare un sito del team isolato è necessario stabilire:

* I gruppi di SharePoint e i livelli di autorizzazione.
* Il set di gruppi di accesso che saranno membri dei gruppi di SharePoint.
 Il set di gruppi di accesso consigliato è uno per i membri del sito, uno per i visualizzatori del sito e uno per gli amministratori del sito.
* Se verranno usati gruppi nidificati all'interno dei gruppi di accesso.

Ad esempio, la struttura dei gruppi e i livelli di autorizzazione consigliati sono simili ai seguenti:
 
|**Gruppo di SharePoint**|**Livello di autorizzazione**|**Gruppo di accesso (esempi)**|
|:-----|:-----|:-----|
|Membri di [nome sito]|Modifica|Membri di [nome sito]|
|Visitatori di [nome sito]|Lettura|Visualizzatori di [nome sito]|
|Proprietari di [nome sito]|Controllo completo|Amministratori di [nome sito]|

Per un sito del team, i gruppi e i livelli di autorizzazione di SharePoint vengono creati per impostazione predefinita. È necessario stabilire i nomi dei gruppi di accesso.

Per i dettagli del processo di progettazione, vedere [Progettare un sito del team SharePoint Online isolato](https://technet.microsoft.com/library/mt784687.aspx).

### <a name="step-2-deploy-your-isolated-site"></a>Passaggio 2: Distribuire un sito isolato
Per distribuire un sito isolato è innanzitutto necessario:

* Stabilire i membri di tipo utente e gruppo di ogni gruppo di accesso.
* Creare i gruppi di accesso e aggiungere i membri di tipo utente e gruppo.
* Creare un sito del team isolato che usa i gruppi di accesso.

Per istruzioni dettagliate, vedere [Distribuire un sito del team di SharePoint Online isolato](https://technet.microsoft.com/library/mt784693.aspx).

Di seguito sono riportati i risultati delle impostazioni di autorizzazione:

* Il gruppo di SharePoint **Proprietari di [nome sito]** contiene il gruppo di accesso degli amministratori del sito in cui tutti i membri hanno il livello di autorizzazione **Controllo completo**.
* Il gruppo di SharePoint **Membri di [nome sito]** contiene il gruppo di accesso dei membri del sito in cui tutti i membri hanno il livello di autorizzazione **Modifica**.
* Il gruppo di SharePoint **Visitatori di [nome sito]** contiene il gruppo di accesso dei visualizzatori del sito in cui tutti i membri hanno il livello di autorizzazione **Lettura**.
* La possibilità per i membri di invitare altri membri è disabilitata. 
* La possibilità per gli utenti non membri di richiedere l'accesso è disabilitata. 

Questa è la configurazione risultante.

 ![Protezione di siti con riservatezza elevata](./media/deploy-sites-for-three-tiers-of-protection/hc_site.png)

I membri del sito, attraverso l'appartenenza a uno dei gruppi di accesso, possono ora collaborare in modo sicuro alle risorse del sito. 

## <a name="next-steps"></a>Passaggi successivi

[Proteggere file con le etichette di Office 365 e DLP](protect-files-with-o365-labels-dlp.md)







