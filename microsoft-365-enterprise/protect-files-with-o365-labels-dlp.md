---
title: Proteggere i file con le etichette di Office 365 e prevenzione della perdita di dati di SharePoint Online | Documenti di Microsoft
description: Office 365 dati ed etichette perdita criterio DLP criteri applicati ai siti dei team SharePoint Online con diversi livelli di protezione delle informazioni.
services: active-directory
keywords: Office 365, Windows 10, Enterprise Mobility and Security, Microsoft 365 Enterprise
documentationcenter: ''
author: JoeDavies-MSFT
manager: laurawi
ms.assetid: ''
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.workload: ''
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/15/2017
ms.author: josephd
ms.openlocfilehash: ec400ac466aeb5a20473c00f7a7df488e4b23725
ms.sourcegitcommit: a322bdd365c7d648c5241cf959dcd04b3815672d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-data-loss-prevention"></a>Proteggere i file di SharePoint Online con le etichette di Office 365 e la prevenzione della perdita dei dati

## <a name="introduction"></a>Introduzione
Seguire la procedura descritta in questo articolo per progettare e distribuire le etichette di Office 365 e i criteri di prevenzione della perdita dei dati ai siti di base, sensibili e con riservatezza elevata del team di SharePoint Online. Per altre informazioni su questi tre livelli di protezione, vedere [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Proteggere siti e file di SharePoint Online).

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Etichette di Office 365 per i siti di SharePoint Online
Durante la creazione e l'assegnazione delle etichette di Office 365 ai siti del team di SharePoint Online è necessario completare le tre fasi seguenti.

### <a name="phase-1-determine-the-office-365-label-names"></a>Fase 1: definire i nomi etichette di Office 365

In questa fase si definiscono i nomi etichette di Office 365 per i quattro livelli di protezione delle informazioni applicati ai siti del team di SharePoint Online. La tabella seguente elenca i nomi consigliati per ogni livello.
 
|**Livello di protezione del sito del team di SharePoint Online**|**Nome etichetta**|
|:-----|:-----|
|Pubblico di base|Pubblico interno|
|Privato di base|Private|
|Dati sensibili|Dati sensibili|
|Highly Confidential (Riservatezza elevata)|Highly Confidential (Riservatezza elevata)|

### <a name="phase-2-create-the-office-365-labels"></a>Fase 2: creare le etichette di Office 365
In questa fase si creano e poi pubblicano le etichette specificate per i diversi livelli di protezione delle informazioni.

Per creare le etichette, è possibile usare l'interfaccia di amministrazione di Office 365 oppure Microsoft PowerShell.

**Creare le etichette di Office 365 con l'interfaccia di amministrazione di Office 365**

1. Accedere al **portale di Office 365** con un account con il ruolo Amministratore della sicurezza o Amministratore società. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Dalla scheda **Microsoft Office Home** fare clic sul riquadro **Amministratore**.
3. Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Interfacce di amministrazione > Sicurezza e conformità**.
4. Dalla nuova scheda **Home: Sicurezza e conformità** del browser fare clic su **Classificazioni > Etichette**.
5. Dal riquadro **Home > Etichette** fare clic su **Create a label** (Crea un'etichetta).
6. Nel riquadro **Name your label** (Denomina l'etichetta) digitare il nome dell'etichetta e fare clic su **Avanti**.
7. Nel riquadro **Label settings** (Importazioni etichetta) fare clic su **Avanti**.
8. Nel riquadro **Verifica le impostazioni** fare clic su **Create this label** (Crea questa etichetta) e fare clic su **Chiudi**.
9. Ripetere i passaggi da 5 a 8 per etichette aggiuntive.

**Creare le etichette di Office 365 con PowerShell**

1. [Connettersi al Centro sicurezza e conformità di Office 365 tramite sessione remota di PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&clcid=0x409) e specificare le credenziali di un account con ruolo Amministratore della sicurezza o Amministratore società.
2. Compilare l'elenco dei nomi delle etichette ed eseguire questi comandi al prompt dei comandi di PowerShell:

```
$labelNames=@([list of label names, each enclosed in quotes and separated by commas])
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
```

Successivamente, seguire questa procedura per pubblicare le nuove etichette di Office 365.

1. Dal riquadro **Home > Etichette** nel Centro sicurezza e conformità fare clic su **Publish labels** (Pubblica etichette).
2. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Choose labels to publish** (Scegli etichette da pubblicare).
3. Nel riquadro **Choose labels** (Scegli etichette) fare clic su **Aggiungi** e selezionare le quattro etichette.
4. Fare clic su **Fine**.
5. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Avanti**.
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Avanti**.
7. Nel riquadro **Denomina il criterio** digitare un nome per il set di etichette in **Nome** e fare clic su **Avanti**.
8. Nel riquadro **Verifica le impostazioni** fare clic su **Publish labels** (Pubblica etichette) e fare clic su **Chiudi**.

### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Fase 3: applicare le etichette di Office 365 ai siti di SharePoint Online
Seguire questa procedura per applicare le etichette di Office 365 alle cartelle di documenti dei siti del team di SharePoint Online.

1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **SharePoint**.
2. Nella nuova scheda **SharePoint** del browser selezionare un sito per cui è necessario assegnare un'etichetta di Office 365.
3. Nella nuova scheda del sito di SharePoint del browser fare clic su **Documenti**.
4. Fare clic sull'icona delle impostazioni e selezionare **Impostazioni libreria**.
5. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
6. In **Impostazioni: Applica etichetta** selezionare l'etichetta appropriata e fare clic su **Salva**.
7. Chiudere la scheda per il sito di SharePoint Online.
8. Ripetere i passaggi da 3 a 8 per assegnare le etichette di Office 365 a siti di SharePoint Online aggiuntivi.

Questa è la configurazione risultante.

 ![Protezione di siti di base](./media/protect-files-with-o365-labels-dlp/site_labels.png)

### <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Criteri di prevenzione della perdita dei dati per siti di SharePoint Online
Seguire questa procedura per configurare un criterio della prevenzione della perdita dei dati che notifica agli utenti la condivisione di un documento in un sito sensibile del team di SharePoint Online all'esterno dell'organizzazione.

1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza e conformità**.
2. Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
4. Nel riquadro **Inizia da un modello o Crea criteri personalizzati** fare clic su **Personalizzato** e su **Avanti**.
5. Nel riquadro **Denomina il criterio** digitare il nome del criterio di prevenzione della perdita dei dati per il livello sensibile in Nome e fare clic su **Avanti**.
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
7. Nell'elenco delle posizioni disabilitare le opzioni **Exchange email** (Posta elettronica di Exchange) e **OneDrive accounts** (Account OneDrive) e fare clic su **Avanti**.
8. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
9. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Aggiungi** nella casella di riepilogo a discesa e fare clic su **Etichette**.
10. Nel riquadro **Etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Sensitive** (Sensibile), fare clic su **Aggiungi** e su **Fine**.
11. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
12. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
13. Nella **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, fare clic su * * Personalizza la descrizione e posta elettronica * *.
14. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
15. Nella casella di testo digitare o incollare quanto segue:
 * Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su File, Proteggi documento, Crittografa con password e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
 * Digitare o incollare il suggerimento per i criteri in cui si indica agli utenti come condividere un file all'esterno dell'organizzazione.
16. Fare clic su **OK** nella finestra di **Selezionare l'operazione da eseguire se si rileva informazioni riservate?** riquadro, deselezionare la casella di controllo **Blocca la condivisione degli utenti e limitare l'accesso al contenuto condiviso** e fare clic su **Avanti**.
17. Nel riquadro **Do you want to turn on the policy or test things out first?** (Attivare i criteri o prima verificare?) fare clic su **Sì** per attivare subito i criteri e scegliere **Avanti**.
18. Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e su **Chiudi**.

Di seguito è riportata la configurazione risultante per i siti sensibili del team di SharePoint Online.

 ![Protezione di siti sensibili](./media/protect-files-with-o365-labels-dlp/sensitive_w_dlp.png)

Seguire questa procedura per configurare un criterio della prevenzione della perdita dei dati che blocchi gli utenti in fase di condivisione di un documento in un sito con riservatezza elevata del team di SharePoint Online all'esterno dell'organizzazione.

1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza e conformità**.
2. Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
4. Nel riquadro **Inizia da un modello o Crea criteri personalizzati** fare clic su **Personalizzato** e su **Avanti**.
5. Nel riquadro **Denomina il criterio** digitare il nome del criterio di prevenzione della perdita dei dati per il livello con riservatezza elevata in **Nome** e fare clic su **Avanti**.
6. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
7. Nell'elenco delle posizioni disabilitare le opzioni **Exchange email** (Posta elettronica di Exchange) e **OneDrive accounts** (Account OneDrive) e fare clic su **Avanti**.
8. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
9. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Aggiungi** nella casella di riepilogo a discesa e fare clic su **Etichette**.
10. Nel riquadro **Etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Riservatezza elevata**, fare clic su **Aggiungi** e su **Fine**.
11. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
12. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
13. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
14. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
15. Nella casella di testo digitare o incollare quanto segue:
 * Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su **File**, **Proteggi documento**, **Crittografa con password** e specificare una password complessa. Inviare la password tramite un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
 * Digitare o incollare il suggerimento per i criteri in cui si indica agli utenti come condividere un file all'esterno dell'organizzazione.
16. Fare clic su **OK**.
17. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) selezionare **Require a business justification to override** (Richiedi una motivazione aziendale per la sostituzione) e fare clic su **Avanti**.
18. Nel riquadro **Do you want to turn on the policy or test things out first?** (Attivare i criteri o prima verificare?) fare clic su **Sì** per attivare subito i criteri e scegliere **Avanti**.
19. Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e su **Chiudi**.

Di seguito è riportata la configurazione risultante per i siti con riservatezza elevata del team di SharePoint Online.

 ![Protezione di siti con riservatezza elevata](./media/protect-files-with-o365-labels-dlp/hc_w_dlp.png)

## <a name="next-steps"></a>Passaggi successivi

[Proteggere i file di SharePoint Online con Azure Information Protection](protect-files-with-aip.md)






