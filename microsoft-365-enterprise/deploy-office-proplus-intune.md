---
title: Distribuire Office 365 ProPlus con Microsoft Intune - Microsoft 365 Enterprise | Microsoft Docs
description: Illustra come distribuire Microsoft Office 365 ProPlus con Microsoft Intune.
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/10/2017
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: da8fb9ee62b458a3580abadb2a65a84110ac51a9
ms.sourcegitcommit: a322bdd365c7d648c5241cf959dcd04b3815672d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="deploy-office-365-proplus-with-microsoft-intune"></a>Distribuire Office 365 ProPlus con Microsoft Intune
Microsoft 365 Enterprise è una moderna soluzione aziendale che consente a tutti di essere creativi e di collaborare in modo sicuro. Le soluzioni Microsoft 365 Enterprise sono il risultato della stretta collaborazione tra i team di Enterprise Mobility + Security (EMS), Office 365 e Windows 10. Da questa collaborazione nascono soluzioni innovative, ad esempio la possibilità di distribuire le applicazioni di Office 365 ProPlus nei dispositivi Windows 10 con Intune.

Selezionare app di Office 365 ProPlus specifiche (usando la tecnologia a portata di clic), distribuirle ai dispositivi registrati che eseguono Windows 10 Creators Update e visualizzare le metriche di distribuzione è ora più facile che mai grazie al nuovo portale di Intune in Azure. Il portale funziona perfettamente con Windows AutoPilot per preparare i dispositivi dei dipendenti per le attività lavorative tramite la semplice immissione delle credenziali aziendali durante la Configurazione guidata mentre Azure AD e Intune vengono eseguiti in background per registrare il dispositivo, distribuire le configurazioni necessarie e ora anche per installare le app di Office 365 ProPlus.

![Semplificare la gestione di Windows 10 e ridurre il TCO con EMS](./media/deploy-office-proplus-intune/windows-10-management-ems.png)

È possibile [scaricare qui questa infografica](https://gallery.technet.microsoft.com/Infographic-Simplify-37e77674).

## <a name="deploy-office-365-proplus-with-intune"></a>Distribuire Office 365 ProPlus con Intune
In questa sezione viene illustrato come configurare una distribuzione di Office 365 ProPlus con Intune.

È possibile aggiungere e personalizzare facilmente le distribuzioni di Office 365 ProPlus tramite il nuovo portale di Intune. Dopo aver scelto il tipo di app di **Office 365 ProPlus Suite (Windows 10)** è possibile personalizzare la distribuzione delle app di Office in tre semplici passaggi.

In primo luogo, scegliere le applicazioni da installare nei dispositivi degli utenti finali:

![Scegliere le applicazioni da distribuire](./media/deploy-office-proplus-intune/Configure-App-Suite.png)

Successivamente, configurare le informazioni della famiglia di prodotti. Si può, ad esempio, aggiungere una breve descrizione di quali app sono incluse in questa famiglia di prodotti da visualizzare nel Portale aziendale Intune:

![Configurare le informazioni della famiglia di prodotti](./media/deploy-office-proplus-intune/App-Suite-Information.png)

Configurare infine alcune impostazioni di installazione, ad esempio l'architettura di sistema o il canale di aggiornamento:

![Configurare le impostazioni di installazione](./media/deploy-office-proplus-intune/App-Suite-Settings.png)

Gli utenti finali possono installare le app di Office tramite il Portale aziendale Intune se sono state rese disponibili. Altrimenti verrà semplicemente eseguita un'installazione invisibile all'utente. Dopo che Office è stato installato nei dispositivi, gli utenti potranno accedere, attivare il prodotto e usare le funzionalità più recenti poiché [Office viene automaticamente aggiornato dal servizio](https://support.office.com/article/Overview-of-update-channels-for-Office-365-ProPlus-9ccf0f13-28ff-4975-9bd2-7e4ea2fefef4).

> [!NOTE]
> Questa forma di distribuzione di Office 365 ProPlus è attualmente supportata solo per i dispositivi in cui non è installata alcuna versione di Office. Per i dispositivi con versioni esistenti di Office, è consigliabile rimuovere tutte le versioni di Office prima della registrazione. Stiamo lavorando con i team di Windows e Office ai futuri miglioramenti per supportare i dispositivi con distribuzioni di Office esistenti.

## <a name="learn-more"></a>Altre informazioni
Per istruzioni dettagliate, vedere [Distribuire le app di Office 365 per Windows 10 con Intune](https://docs.microsoft.com/intune/apps-add-office365).
