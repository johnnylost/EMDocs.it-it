---
title: Proteggere i file di SharePoint Online con Azure Information Protection | Documenti di Microsoft
description: Applicare la protezione delle informazioni di Azure per proteggere i file in un sito del team di SharePoint Online altamente riservato.
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
ms.openlocfilehash: ec88a40392e8bc530a40c35a1d8dadd1be8eb4f3
ms.sourcegitcommit: a322bdd365c7d648c5241cf959dcd04b3815672d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="protect-files-with--azure-information-protection"></a>Proteggere i file con Azure Information Protection

## <a name="introduction"></a>Introduzione

Seguire la procedura descritta in questo articolo per configurare Azure Information Protection (AIP) e offrire la crittografia e le autorizzazioni per i file in un sito con riservatezza elevata del team di SharePoint Online. 

La protezione tramite crittografia e autorizzazioni è veicolata da un file quando viene scaricato dal sito. Per altre informazioni sui siti con riservatezza elevata del team di SharePoint Online, vedere [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) (Proteggere siti e file di SharePoint Online).

> [!NOTE]
> Quando si applica la crittografia di Azure Information Protection ai file archiviati in Office 365, il servizio non è in grado di elaborare il contenuto di questi file. La creazione condivisa, eDiscovery, la ricerca, Delve e altre funzionalità di collaborazione non funzionano. I criteri di prevenzione della perdita dei dati (DLP) funzionano solo con i metadati, incluse le etichette di Office 365, ma non con il contenuto dei file, ad esempio i numeri di carta di credito all'interno dei file.

## <a name="configure-azure-information-protection"></a>Configurare Azure Information Protection

Iniziare la configurazione seguendo le istruzioni in [Attivare Azure RMS dall'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).

A questo punto, configurare Azure Information Protection con nuovi criteri con ambito e un'etichetta secondaria per la protezione e le autorizzazioni per il sito con riservatezza elevata del team di SharePoint Online attenendosi alla procedura seguente:

1. Accedere al **portale di Office 365** con un account con il ruolo Amministratore della sicurezza o Amministratore società. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
2. Creare una scheda separata nel browser e accedere al portale ([https://portal.azure.com](https://portal.azure.com/)).
3. Se è la prima volta che si configura Azure Information Protection, vedere [queste istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
4. Nel riquadro elenco fare clic su **Altri servizi**, digitare **informazioni** e fare clic su **Azure Information Protection**.
5. Nel pannello **Azure Information Protection** fare clic su **Criteri con ambito > + Aggiungi un nuovo criterio**.
6. Digitare un nome per il nuovo criterio in **Nome criterio** e una descrizione in **Descrizione**.
7. Fare clic su **Selezionare gli utenti o i gruppi a cui viene applicato il criterio > Utenti/Gruppi** e quindi selezionare il gruppo di accesso dei membri del sito con riservatezza elevata del team di SharePoint Online.
8. Fare clic su **Seleziona > OK**.
9. Per l'etichetta **Highly Confidential (Riservatezza elevata)**, fare clic sui puntini di sospensione (...) e quindi fare clic su **Aggiungi un'etichetta secondaria**.
10. Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.
11. In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.
12. Nella sezione **Protezione** fare clic su **Azure (chiave cloud)**.
13. Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.
14. Nel pannello **Aggiungi autorizzazioni** fare clic su **+ Sfoglia la directory** in **Specificare utenti e gruppi**.
15. Nel riquadro **Utenti e gruppi di AAD** selezionare il gruppo di membri di accesso al sito con riservatezza elevata del team di SharePoint Online e fare clic su **Seleziona**.
16. In **Scegliere le autorizzazioni dai valori preimpostati** deselezionare le caselle di controllo **Stampa, copia ed estrai il contenuto** e **Inoltra**.
17. Fare due volte clic su **OK** .
18. Nel pannello **Etichetta secondaria** configurare i contrassegni visivi in base alle esigenze e quindi fare clic su **Salva**.
19. Chiudere il pannello dei nuovi criteri con ambito.
20. Nel pannello **Azure Information Protection - Criteri con ambito** fare clic su **Pubblica** e quindi su **Sì**.

Questa è la configurazione risultante per i siti con riservatezza elevata del team di SharePoint Online.

 ![Highly Confidential (Riservatezza elevata)](./media/protect-files-with-aip/hc_w_aip.png)

A questo punto è possibile iniziare a creare i documenti e proteggerli con Azure Information Protection e la nuova etichetta.

[Installare il client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) nel dispositivo o in un computer con sistema operativo Windows. È possibile creare lo script e automatizzare l'installazione oppure installare il client manualmente. 

Per altre informazioni, vedere le risorse seguenti:

* [Lato client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
* [Installazione del client di Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
* [Pagina di download per l'installazione manuale](https://www.microsoft.com/download/details.aspx?id=53018)

Dopo aver installato il client, eseguirlo e accedere da un'applicazione Office (ad esempio Microsoft Word) usando il proprio account di Office 365. Una nuova barra **Information Protection** consente di selezionare l'etichetta. 

Verificare che gli utenti siano a conoscenza del sito del team di SharePoint Online e dell'etichetta usata per proteggere i file con riservatezza elevata.

>[!Note]
>In presenza di più siti con riservatezza elevata del team di SharePoint Online, è necessario creare più criteri con ambito di Azure Information Protection con etichette secondarie con le impostazioni sopra riportate, con le autorizzazioni per ogni etichetta secondaria impostate sul gruppo di accesso dei membri del sito di uno specifico sito del team di SharePoint Online.
>

## <a name="next-steps"></a>Passaggi successivi

[Adozione del cloud e soluzioni ibride](https://technet.microsoft.com/library/dn262744.aspx)
