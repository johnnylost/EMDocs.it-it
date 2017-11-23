---
title: Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test | Microsoft Docs
description: Creare siti pubblici, privati, sensibili ed estremamente riservati per il team di SharePoint Online in un ambiente di sviluppo e test.
services: active-directory
keywords: Office 365, Windows 10, Enterprise Mobility and Security, Microsoft 365 Enterprise
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
ms.date: 11/15/2017
ms.author: josephd
ms.openlocfilehash: 6e7050dca9c0f66f481fe6ee37fb88bf4617f982
ms.sourcegitcommit: 684c942047754e93378e271f5b1a659a9752f0ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test

## <a name="introduction"></a>Introduzione

Questo articolo contiene istruzioni dettagliate per la creazione di un ambiente di sviluppo e test che includa i quattro tipi diversi di sito del team di SharePoint Online per la [soluzione di protezione di siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md).

Usare questo ambiente di sviluppo e test per sperimentare i comportamenti della protezione delle informazioni e ottimizzare le impostazioni in base alle esigenze specifiche prima di distribuire siti del team di SharePoint Online nell'ambiente di produzione.

## <a name="phase-1-create-your-devtest-environment"></a>Fase 1: Creare l'ambiente di sviluppo/test
In questa fase si ottengono le sottoscrizioni di valutazione per Office 365 ed Enterprise Mobility + Security per un'organizzazione fittizia.

Per prima cosa, seguire le istruzioni della **fase 2** nell'articolo relativo all'[ambiente di sviluppo e test di Office 365](https://technet.microsoft.com/library/mt736406.aspx).

Successivamente, iscriversi alla **sottoscrizione di valutazione di EMS** e aggiungerla alla stessa organizzazione della sottoscrizione di valutazione di Office 365, quindi seguire questi passaggi:

1. Se necessario, accedere al **portale di Office 365** con le credenziali dell'account amministratore globale della sottoscrizione di valutazione. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Scegliere il riquadro **Amministrazione**.
3. Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.
4. Individuare la voce **Enterprise Mobility + Security E5** nella pagina **Servizi di acquisto**, quindi posizionare il puntatore del mouse sulla voce e scegliere **Avvia versione di valutazione gratuita**.
5. Nella pagina di **conferma dell'ordine** fare clic su **Prova subito**.
6. Nella pagina **Ricevuta ordine** fare clic su **Continua**.

Abilitare quindi la licenza Enterprise Mobility + Security E5 per l'account amministratore globale.

1. Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.
2. Fare clic sull'account amministratore globale e quindi su **Modifica** per le licenze del prodotto.
3. Nel riquadro delle **licenze del prodotto** **attivare** la licenza del prodotto per **Enterprise Mobility + Security E5**, fare clic su **Salva** e fare clic due volte su **Chiudi**.


## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Fase 2: Creare e configurare gruppi e utenti di Azure Active Directory (AD)
In questa fase vengono creati e configurati i gruppi e gli utenti di Azure AD per l'organizzazione fittizia.

Innanzitutto, creare un set di gruppi per un'organizzazione tipica con il portale di Azure.

1. Creare una scheda separata nel browser e passare al **portale di Azure** all'indirizzo [https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale della sottoscrizione di valutazione di Office 365 E5.
2. Nel portale di Azure fare clic su **Azure Active Directory > Utenti e gruppi > Tutti i gruppi**.
3. Nel pannello **Tutti i gruppi** fare clic su **+ Nuovo gruppo**.
4. Nel pannello **Gruppo**:
 * Digitare **C-Suite** in **Nome**.
 * Selezionare **Assegnato** in **Appartenenza**.
 * Selezionare **Sì** per **Abilitare le funzionalità di Office**.
5. Fare clic su **Crea** e quindi chiudere il pannello **Gruppo**.
6. Ripetere i passaggi da 3 a 5 per i nomi dei gruppi seguenti:
 * IT staff
 * Research staff
 * Regular staff
 * Marketing staff
 * Sales staff
7. Tenere aperta la scheda del portale di Azure nel browser.

Successivamente, configurare la gestione automatica delle licenze in modo che ai membri dei gruppi vengano automaticamente assegnate le licenze per le sottoscrizioni di Office 365 ed EMS, quindi attenersi alla procedura seguente:

1. Nel portale di Azure fare clic su **Azure Active Directory > Licenze > Tutti i prodotti**.
2. Selezionare dall'elenco **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** e fare clic su **Assegna**.
3. Nel pannello **Assegnare licenza** fare clic su **Utenti e gruppi**.
4. Nell'elenco dei gruppi selezionare gli elementi seguenti:
 * C-Suite
 * IT staff
 * Research staff
 * Regular staff
 * Marketing staff
 * Sales staff
5. Fare clic su **Seleziona** e quindi su **Assegna**.
6. Chiudere la scheda del portale di Azure nel browser.

È quindi necessario [connettersi al modulo PowerShell di Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).

Inserire il nome dell'organizzazione, il percorso e una password comune. Eseguire i comandi indicati di seguito dal prompt dei comandi di PowerShell o da Integrated Script Environment (ISE) per creare gli account utente e aggiungerli ai gruppi corrispondenti.

```
$orgName="[organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name]"
$location="[the ISO ALPHA2 country code, such as US for the United States]"
$commonPassword="[common password for all the new accounts]"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

>[!Note]
>L'uso di una password comune qui consente l'automazione e agevola la configurazione per un ambiente di sviluppo e test. Non è consigliato per le sottoscrizioni di produzione.
>

Successivamente, eseguire i passaggi seguenti per verificare che l'assegnazione delle licenze basata sui gruppi funzioni correttamente.

1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Amministratore**.
2. Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Utenti**.
3. Fare clic su **CEO** nell'elenco degli utenti.
4. Nel riquadro in cui sono elencate le proprietà dell'account utente **CEO** verificare che all'account siano state assegnate le licenze **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** (nell'elenco delle **licenze del prodotto**).

## <a name="phase-3-create-office-365-labels"></a>Fase 3: Creare le etichette di Office 365

In questa fase vengono create le etichette per i diversi livelli di sicurezza per le cartelle dei documenti del sito del team di SharePoint Online.

1. Se necessario, usare un'istanza privata del browser Internet e accedere al **portale di Office 365** con l'account amministratore globale della sottoscrizione di valutazione di Office 365 E5. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Dalla scheda **Microsoft Office Home** fare clic sul riquadro **Amministratore**.
3. Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Interfacce di amministrazione > Sicurezza e conformità**.
4. Dalla nuova scheda **Home: Sicurezza e conformità** del browser fare clic su **Classificazioni > Etichette**.
5. Dal riquadro **Home > Etichette** fare clic su **Crea un'etichetta**.
6. Nel riquadro **Name your label** (Denomina l'etichetta) digitare **Internal Public** e fare clic su **Avanti**.
7. Nel riquadro delle **impostazioni dell'etichetta** fare clic su **Avanti**.
8. Nel riquadro **Verifica le impostazioni** fare clic su **Create this label** (Crea questa etichetta) e fare clic su **Chiudi**.
9. Ripetere i passaggi da 5 a 8 per queste etichette aggiuntive:
 * Private
 * Dati sensibili
 * Highly Confidential (Riservatezza elevata)
10. Dal riquadro **Home > Etichette** fare clic su **Publish labels** (Pubblica etichette).
11. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Choose labels to publish** (Scegli etichette da pubblicare).
12. Nel riquadro **Choose labels** (Scegli etichette) fare clic su **Aggiungi**, selezionare le quattro etichette e fare clic su **Chiudi**.
13. Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Avanti**.
14. Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Avanti**.
15. Nel riquadro **Denomina il criterio** digitare **Example organization** in **Nome** e fare clic su **Avanti**.
16. Nel riquadro **Verifica le impostazioni** fare clic su **Publish labels** (Pubblica etichette) e fare clic su **Chiudi**.

## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Fase 4: Creare i siti del team di SharePoint Online
In questa fase vengono creati e configurati i quattro tipi di siti del team di SharePoint Online per l'organizzazione di esempio.

### <a name="organization-wide-team-site"></a>Sito del team per l'intera organizzazione
Per creare un sito pubblico iniziale per il team di SharePoint Online, eseguire queste operazioni:

1. Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
5. In **Nome sito** digitare **Organization wide**.
6. Come **descrizione del sito del team** digitare **SharePoint site for the entire organization** (Sito SharePoint per l'intera organizzazione).
7. In **Impostazioni privacy** selezionare **Public – anyone in the organization can access this site** (Pubblico: qualsiasi persona dell'organizzazione può accedere a questo sito) e quindi fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.

Configurare quindi la cartella dei documenti del sito del team dell'intera organizzazione per l'etichetta Internal Public.

1. Nella scheda **Organization wide - Home** (A livello di organizzazione - Home) del browser fare clic su **Documenti**.
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
4. In **Impostazioni: Applica etichetta** selezionare **Internal Public** e fare clic su **Salva**.

Questa è la configurazione risultante.

 ![Protezione del sito del team pubblico](./media/secure-sharepoint-online-sites-dev-test/pubsite.png)

### <a name="project-1-team-site"></a>Sito del team Project 1
Per creare un sito del team SharePoint Online privato iniziale per un progetto all'interno dell'organizzazione, eseguire queste operazioni:

1. Se necessario, usare un browser sul computer locale e accedere al **portale di Office 365** con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
5. In **Nome del sito** digitare **Project 1**.
6. Come **descrizione del sito del team** digitare **SharePoint site for Project 1** (Sito SharePoint per Project 1).
7. In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.

Configurare quindi la cartella dei documenti del sito del team Project 1 per l'etichetta Private.

1. Nella scheda **Project 1: Home** del browser fare clic su **Documenti**.
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
4. In **Impostazioni: Applica etichetta** selezionare **Private** e fare clic su **Salva**.

Questa è la configurazione risultante.

 ![Protezione del sito del team privato](./media/secure-sharepoint-online-sites-dev-test/privsite.png)

### <a name="marketing-campaigns-team-site"></a>Sito del team delle campagne di marketing

Per creare un sito del team di SharePoint Online isolato per i dati sensibili delle risorse della campagna di marketing, eseguire le operazioni seguenti:

1. Usando un browser sul computer locale, accedere al **portale di Office 365** con il proprio account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
5. Come **nome del sito del team** digitare **Marketing campaigns**.
6. Come **descrizione del sito del team** digitare **SharePoint site for marketing campaign resources (sensitive)** (Sito SharePoint per le risorse delle campagne marketing - dati sensibili).
7. In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
9. Nella barra degli strumenti della nuova scheda **Marketing campaigns** (Campagne di marketing) del browser fare clic sull'icona delle impostazioni e scegliere **Autorizzazioni sito**.
10. Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).
11. Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.
12. Nella finestra di dialogo **Impostazioni richieste di accesso**:
13. Deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e singoli file e cartelle** e **Consenti ai membri di invitare altre persone nel gruppo di membri del sito**.
14. Digitare **ITAdmin1@**[nome organizzazione]**.onmicrosoft.com** in **Invia tutte le richieste di accesso** e quindi fare clic su **OK**.
15. Fare clic su **Marketing campaigns - Members** (Campagne di marketing - Membri) nell'elenco.
16. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
17. Nella finestra di dialogo **Condividi** digitare **Marketing staff**, selezionarlo e fare clic su **Condividi**.
18. Ripetere i passaggi precedenti per l'account utente **Researcher1**.
19. Fare clic sul pulsante Indietro del browser e su **Marketing campaigns - Owners** (Campagne di marketing - Proprietari) nell'elenco.
20. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
21. Nella finestra di dialogo **Condividi** digitare **IT staff**, selezionarlo e fare clic su **Condividi**.
22. Fare clic sul pulsante Indietro del browser e chiudere la scheda **Utenti e gruppi** nel browser, fare clic sulla scheda **Marketing campaigns - Home** (Campagne di marketing - Home) nel browser e chiudere il riquadro **Autorizzazioni sito**.

Di seguito sono riportati i risultati della configurazione delle autorizzazioni:

* Il gruppo **Marketing campaigns - Members** (Campagne di marketing - Membri) di SharePoint contiene solo il gruppo **Marketing campaigns**, che contiene l'account utente amministratore globale, il gruppo **Marketing staff**, che contiene gli account utente Marketing1 e Marketing2, e l'account utente **Researcher1**.
* Il gruppo **Marketing campaigns - Owners** (Campagne di marketing - Proprietari) di SharePoint contiene solo il gruppo **IT staff**, che a sua volta contiene solo gli account utente ITAdmin1 e ITAdmin2.
* Il gruppo **Marketing campaigns - Visitors** (Campagne di marketing - Visitatori) di SharePoint non contiene gruppi né account utente.
* I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Marketing campaigns - Owners**.
* Gli altri account utente non possono accedere al sito o alle relative risorse, ma possono richiedere l'accesso al sito e in questo modo viene inviato un messaggio di posta elettronica alla cassetta postale dell'account utente _ITAdmin1_.

Configurare quindi la cartella dei documenti del sito del team Marketing campaigns per l'etichetta Sensitive.

1. Nella scheda **Marketing campaigns - Home** (Campagne di marketing - Home) del browser fare clic su **Documenti**.
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
4. In **Impostazioni: Applica etichetta** selezionare **Sensitive** e fare clic su **Salva**.

Configurare quindi un criterio di prevenzione della perdita di dati che informa gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Sensitive, incluso il sito Marketing campaigns, all'esterno dell'organizzazione.

1. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza e conformità**.
2. Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.
3. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
4. Nel riquadro **Inizia da un modello o Crea criteri personalizzati** fare clic su **Personalizzato** e su **Avanti**.
5. Nel riquadro **Denomina il criterio** digitare **Sensitive label SharePoint Online team sites** (Siti del team di SharePoint Online con etichetta Sensitive) in **Nome** e fare clic su **Avanti**.
6. Nel riquadro **Choose locations** (Scegliere le posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
7. Nell'elenco delle posizioni disabilitare le opzioni **Exchange email** (Posta elettronica di Exchange) e **OneDrive accounts** (Account OneDrive) e fare clic su **Avanti**.
8. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
9. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Aggiungi** nella casella di riepilogo a discesa e fare clic su **Etichette**.
10. Nel riquadro **Etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Sensitive** (Sensibile), fare clic su **Aggiungi** e su **Fine**.
11. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
12. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
13. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
14. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
15. Nella casella di testo digitare o incollare quanto segue:
 * Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su File, Proteggi documento, Crittografa con password e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
16. Fare clic su **OK**.
17. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) deselezionare la casella di controllo **Block people from sharing and restrict access to shared content** (Blocca la condivisione e limita l'accesso al contenuto condiviso) e fare clic su **Avanti**.
18. Nel riquadro **Do you want to turn on the policy or test things out first?** (Attivare i criteri o prima verificare?) fare clic su **Sì** per attivare subito i criteri e scegliere **Avanti**.
19. Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e su **Chiudi**.

Questa è la configurazione risultante.

 ![Protezione di siti sensibili](./media/secure-sharepoint-online-sites-dev-test/senssite.png)

### <a name="company-strategy-team-site"></a>Sito del team di strategia aziendale
Per creare un sito del team di SharePoint Online isolato per i dati altamente riservati delle risorse aziendali strategiche dei dirigenti dell'organizzazione, eseguire le operazioni seguenti:

1. Se necessario, usare un browser sul computer locale e accedere al **portale di Office 365** con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Nell'elenco dei riquadri fare clic su **SharePoint**.
3. Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.
4. Nella pagina **Crea un sito** fare clic su **Sito del team**.
5. Come **nome del sito del team** digitare **Company strategy** (Strategia aziendale).
6. Come **descrizione del sito del team** digitare **SharePoint site for company strategy (highly confidential)** (Sito di SharePoint per la strategia aziendale - Informazioni altamente riservate).
7. In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e fare clic su **Avanti**.
8. Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.
9. Nella barra degli strumenti della nuova scheda **Company strategy** (Strategia aziendale) del browser fare clic sull'icona delle impostazioni e scegliere **Autorizzazioni sito**.
10. Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).
11. Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.
12. Nella finestra di dialogo **Impostazioni richieste di accesso** deselezionare **Consenti ai membri di condividere il sito e singoli file e cartelle** e **Consenti ai membri di invitare altre persone nel gruppo di membri del sito**, in modo che tutte e tre le caselle di controllo siano deselezionate e fare clic su **OK**.
13. Fare clic su **Company strategy - Members** (Strategia aziendale - Membri) nell'elenco e fare clic su **Nuovo** nella pagina **Utenti e gruppi**.
14. Nella finestra di dialogo **Condividi** digitare **C-Suite**, selezionarlo e fare clic su **Condividi**.
15. Fare clic su **Company strategy - Owners** (Strategia aziendale - Proprietari) nell'elenco e fare clic su **Nuovo** nella pagina **Utenti e gruppi**.
16. Nella finestra di dialogo **Condividi** digitare **IT staff**, selezionarlo e fare clic su **Condividi**.
17. Fare clic sul pulsante Indietro del browser e chiudere la scheda **Utenti e gruppi**.
18. Fare clic sulla scheda **Company strategy - Home** (Strategia aziendale - Home) nel browser e quindi chiudere il riquadro **Autorizzazioni sito**.

Di seguito sono riportati i risultati della configurazione delle autorizzazioni:

* Il gruppo **Company strategy - Members** (Strategia aziendale - Membri) di SharePoint contiene solo il gruppo **C-Suite**, che contiene solo gli account utente CEO, CFO e CIO, e il gruppo **Company strategy**, che contiene solo l'account utente amministratore globale.
* Il gruppo **Company strategy - Owners** (Strategia aziendale - Proprietari) di SharePoint contiene solo il gruppo **IT staff**, che a sua volta contiene solo gli account utente _ITAdmin1_ e _ITAdmin2_.
* Il gruppo **Company strategy - Visitors** (Strategia aziendale - Visitatori) di SharePoint non contiene gruppi né account utente.
* I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Company strategy - Owners**.
* Gli altri account utente non possono accedere al sito o alle relative risorse né richiedere l'accesso al sito. Le autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Company strategy - Owners**.

Configurare quindi la cartella dei documenti del sito del team di strategia aziendale per l'etichetta Highly Confidential.

1. Nella scheda **Company strategy - Home** (Strategia aziendale - Home) del browser fare clic su **Documenti**.
2. Fare clic sull'icona delle impostazioni e quindi su **Impostazioni libreria**.
3. In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).
4. In **Impostazioni: Applica etichetta** selezionare **Highly Confidential** e fare clic su **Salva**.

Configurare un criterio di prevenzione della perdita di dati che blocchi gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Highly Confidential, incluso il sito Company strategy, all'esterno dell'organizzazione.

1. Se necessario, usare un browser nel computer locale e accedere al **portale di Office 365** con un account con il ruolo Amministratore della sicurezza o Amministratore società. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza e conformità**.
3. Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.
4. Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.
5. Nel riquadro **Inizia da un modello o Crea criteri personalizzati** fare clic su **Personalizzato** e su **Avanti**.
6. Nel riquadro **Denomina il criterio** digitare **Highly Confidential label SharePoint Online team sites** (Siti del team di SharePoint Online con etichetta Highly Confidential) in **Nome** e fare clic su **Avanti**.
7. Nel riquadro **Choose locations** (Scegliere le posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.
8. Nell'elenco delle posizioni disabilitare le opzioni **Exchange email** (Posta elettronica di Exchange) e **OneDrive accounts** (Account OneDrive) e fare clic su **Avanti**.
9. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.
10. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Aggiungi** nella casella di riepilogo a discesa e fare clic su **Etichette**.
11. Nel riquadro **Etichette** fare clic su **+ Aggiungi**, selezionare l'etichetta **Highly Confidential**, fare clic su **Aggiungi** e su **Fine**.
12. Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.
13. Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.
14. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).
15. Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).
16. Nella casella di testo digitare o incollare quanto segue:
 * Per condividere un file con un utente all'esterno dell'organizzazione, scaricare il file e aprirlo. Fare clic su **File** e quindi su **Proteggi documento** e **Crittografa con password** e specificare una password complessa. Inviare la password in un messaggio di posta elettronica separato o un altro mezzo di comunicazione.
17. Fare clic su **OK**.
18. Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) selezionare **Require a business justification to override** (Richiedi una motivazione aziendale per la sostituzione) e fare clic su **Avanti**.
19. Nel riquadro **Do you want to turn on the policy or test things out first?** (Attivare i criteri o prima verificare?) fare clic su **Sì** per attivare subito i criteri e scegliere **Avanti**.
20. Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e su **Chiudi**.

Seguire quindi le istruzioni in [Attivare Azure RMS dall'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).

Successivamente, configurare Azure Information Protection con nuovi criteri con ambito e un'etichetta secondaria per la protezione e le autorizzazioni con la procedura seguente:

1. In una scheda separata del browser in cui è stato eseguito l'accesso con l'account amministratore globale accedere al **portale di Azure** ([http://portal.azure.com](http://portal.azure.com/)).
3. Se è la prima volta che si configura Azure Information Protection, vedere [queste istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
4. Nel riquadro elenco fare clic su **Altri servizi**, digitare **informazioni** e fare clic su **Azure Information Protection**.
5. Nel pannello **Azure Information Protection** fare clic su **Criteri con ambito > + Aggiungi un nuovo criterio**.
6. Digitare **CompanyStrategy** in **Nome criterio** ed **Etichetta per i documenti nel sito del team di strategia aziendale** in **Descrizione**.
7. Fare clic su **Selezionare gli utenti o i gruppi a cui viene applicato il criterio > Utenti/Gruppi**, quindi selezionare **C-Suite**.
8. Fare clic su **Seleziona > OK**.
9. Per l'etichetta **Highly Confidential (Riservatezza elevata)**, fare clic sui puntini di sospensione (...) e quindi fare clic su **Aggiungi un'etichetta secondaria**.
10. Digitare **CompStrat-HC** in **Nome** e **Proteggere i documenti nel sito del team di strategia aziendale** in **Descrizione**.
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
12. Nella sezione **Protezione** fare clic su **Azure (chiave cloud)**.
13. Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.
14. Nel pannello **Aggiungi autorizzazioni** fare clic su **+ Sfoglia la directory** in **Specificare utenti e gruppi**.
15. Nel riquadro **Utenti e gruppi di AAD** selezionare **C-Suite** e fare clic su **Seleziona**.
16. In **Scegliere le autorizzazioni dai valori preimpostati** deselezionare le caselle di controllo **Stampa, copia ed estrai il contenuto** e **Inoltra**.
17. Fare due volte clic su **OK** .
18. Nel pannello **Etichetta secondaria** fare clic su **Salva**.
19. Chiudere il pannello dei nuovi criteri con ambito.
20. Nel pannello **Azure Information Protection - Criteri con ambito** fare clic su **Pubblica** e quindi su **Sì**.

Per proteggere un documento con Azure Information Protection e l'etichetta Highly Confidential, è necessario [installare il client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) in un computer di test, installare Office dal portale di Office 365 e quindi accedere da Microsoft Word con un account del gruppo C-Suite della sottoscrizione di valutazione.

Questa è la configurazione risultante.

 ![Protezione di siti con riservatezza elevata](./media/secure-sharepoint-online-sites-dev-test/hcsite.png)

### <a name="create-documents-and-test-access"></a>Creare documenti e testare l'accesso

A questo punto si è pronti a creare documenti in questi quattro siti e a testare l'accesso ai siti usando diversi account utente della sottoscrizione di valutazione.

Di seguito è riportata la configurazione completa per tutti i quattro siti del team di SharePoint Online.

 ![Configurazione finale](./media/secure-sharepoint-online-sites-dev-test/finalconfig.png)

## <a name="next-steps"></a>Passaggi successivi

Quando si è pronti per la distribuzione di produzione dei siti di SharePoint Online protetti, vedere [Proteggere siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md) per informazioni dettagliate e collegamenti ad articoli relativi alle procedure di distribuzione.

