---
title: Proteggere i file con Azure Information Protection | Microsoft Docs
description: Applicare Azure Information Protection per proteggere i file in un sito del team di SharePoint Online classificato come sito con riservatezza elevata.
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
ms.date: 08/28/2017
ms.author: josephd
ms.openlocfilehash: 34758e152a483a2bada03aeb4c4b5ee3327fb469
ms.sourcegitcommit: 5b34af60e3aac19d618f1c6297da91e2c050a374
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="protect-files-with--azure-information-protection"></a>Proteggere i file con Azure Information Protection

## <a name="introduction"></a>Introduzione

Seguire la procedura descritta in questo articolo per configurare Azure Information Protection (AIP) e offrire la crittografia e le autorizzazioni per i file in un sito con riservatezza elevata del team di SharePoint Online. 

La protezione tramite crittografia e autorizzazioni è veicolata da un file quando viene scaricato dal sito. Per altre informazioni sui siti con riservatezza elevata del team di SharePoint Online, vedere [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Proteggere siti e file di SharePoint Online).

## <a name="configure-azure-information-protection"></a>Configurare Azure Information Protection

Iniziare la configurazione seguendo le istruzioni in [Attivare Azure RMS dall'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).

A questo punto, configurare l'etichetta **AIP Highly Confidential** (Riservatezza elevata AIP) con la protezione e le autorizzazioni per il sito con riservatezza elevata del team di SharePoint Online attenendosi alla procedura seguente:

1. Accedere al **portale di Office 365** con un account con il ruolo Amministratore della sicurezza o Amministratore società. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Creare una scheda separata nel browser e accedere al portale ([https://portal.azure.com](https://portal.azure.com/)).
3. Nel riquadro elenco fare clic su **Altri servizi**, digitare **informazioni** e fare clic su **Azure Information Protection**.
4. Nel pannello **Azure Information Protection - Criteri globali**, sotto l'elenco di etichette, fare clic su **Riservatezza elevata**.
5. Nel pannello **Etichetta: Riservatezza elevata** fare clic su **Proteggi** in **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta**.
6. Nella sezione **Protezione** fare clic su **Azure RMS**.
7. Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.
8. Nel pannello **Aggiungi autorizzazioni** fare clic su **+ Sfoglia la directory** in **Specificare utenti e gruppi**.
9. Nel riquadro **Utenti e gruppi di AAD** selezionare il gruppo di membri di accesso al sito con riservatezza elevata del team di SharePoint Online e fare clic su **Seleziona**.
10. In **Scegliere le autorizzazioni dai valori preimpostati** deselezionare le caselle di controllo **Stampa, copia ed estrai il contenuto** e **Inoltra**.
11. Fare due volte clic su **OK** .
12. Nel pannello **Etichetta: Riservatezza elevata** fare clic su **Salva**.
13. Nel pannello **Azure Information Protection - Criteri globali** fare clic su **Pubblica**.

Di seguito è riportata la configurazione risultante per i siti con riservatezza elevata del team di SharePoint Online.

 ![Highly Confidential (Riservatezza elevata)](./media/protect-files-with-aip/hc_w_aip.png)

A questo punto è possibile iniziare a creare i documenti e proteggerli con Azure Information Protection e l'etichetta Riservatezza elevata.

[Installare il client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) nel dispositivo o in un computer con sistema operativo Windows. È possibile creare lo script e automatizzare l'installazione oppure installare il client manualmente. 

Per altre informazioni, vedere le risorse seguenti:

* [Lato client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
* [Installazione del client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
* [Pagina di download per l'installazione manuale](https://www.microsoft.com/download/details.aspx?id=53018)

Dopo aver installato il client, eseguirlo e accedere da un'applicazione Office (ad esempio Microsoft Word) usando il proprio account di Office 365. Da una nuova barra degli strumenti **Riservatezza** è possibile selezionare l'etichetta **Riservatezza elevata**. 

Verificare che gli utenti siano a conoscenza del sito del team di SharePoint Online in cui archiviare i file con riservatezza elevata.

>[!Note]
>In presenza di più siti con riservatezza elevata del team di SharePoint Online, è necessario creare più etichette di Azure Information Protection con le impostazioni sopra riportate, con le autorizzazioni per ogni etichetta impostate sul gruppo di membri di accesso al sito specifico di un team di SharePoint Online.
>

## <a name="next-steps"></a>Passaggi successivi
[Guida alla sicurezza Microsoft per campagne politiche, organizzazioni no profit e altre organizzazioni Agile](https://technet.microsoft.com/library/mt493213.aspx)

[Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Proteggere siti e file di SharePoint Online)

[Create team sites in a political campaign dev/test environment](secure-sharepoint-online-sites-dev-test.md) (Creare siti di team in un ambiente di sviluppo/ test di una campagna politica)

[Adozione del cloud e soluzioni ibride](https://technet.microsoft.com/library/dn262744.aspx)






