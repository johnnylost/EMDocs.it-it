---
title: Come usare app con supporto di più identità
description: Come usare app con supporto di più identità
keywords: ''
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586ecd93-b097-42a0-9229-bcf3b781021c
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: ddde711116ad95e878612ad9115ea4b96d66dc55
ms.sourcegitcommit: 4401a878f88cc60b3cfd90a915747fe37e333014
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
ms.locfileid: "30848020"
---
# <a name="how-to-use-apps-with-multi-identity-support"></a>Come usare app con supporto di più identità

In questo scenario, viene usato Microsoft Word come esempio. È possibile seguire gli stessi passaggi nelle altre applicazioni incluse in Office 365.
1. Aprire l'app **Word** nel proprio dispositivo. In questo esempio viene usato un dispositivo iOS.
2. Toccare **Nuovo** per creare un nuovo documento di Word.

   ![Schermata che illustra che l'utente seleziona "Nuovo" per iniziare a creare un documento di Word.](./media/ft-multiID-1-createDoc.png)

3. Digitare una frase a scelta e toccare **Salva**. Verranno presentate due opzioni per il percorso di salvataggio del documento: personale o aziendale. I criteri delle app non sono attive poiché non è stato ancora stabilito se il documento è per uso personale o aziendale.

   ![Schermata che illustra che l'utente ha digitato una frase nel nuovo documento di Word.](./media/ft-multiID-2-saveDoc.png)

4. Salvare il documento in un **percorso aziendale**, ad esempio OneDrive for Business. Poiché OneDrive for Business viene riconosciuto come percorso aziendale, il documento è ora contrassegnato come documento aziendale e vengono applicate le restrizioni dei criteri.
5. A questo punto, aprire il documento salvato nel percorso aziendale e copiare il testo. Aprire l'account personale in **Facebook** e provare a incollare il testo copiato. Si noterà che non è possibile incollare il contenuto nel nuovo post di Facebook. L'opzione Incolla non è disattivata, ma non accade nulla quando si preme **Incolla**. Ciò avviene perché le restrizioni dei criteri impediscono che i dati aziendali vengano condivisi in app personali.

   ![Schermata che illustra che l'utente ha copiato il testo dal documento di Word. ](./media/ft-multiID-3-copyText.png)

   ![Schermata che illustra che l'utente non è in grado di incollare il testo in Facebook.](./media/ft-multiID-4-pasteInFB.png)
6. Successivamente, creare un altro documento nuovo di Word ripetendo i passaggi 2 e 3. Digitare una frase a scelta e, questa volta, salvare il documento nel percorso personale, ad esempio **OneDrive - Personale**. Il documento viene contrassegnato come personale e non vengono applicate le restrizioni imposte dai criteri aziendali.

   ![Schermata che illustra che l'utente ha digitato una frase in un nuovo documento di Word.](./media/ft-multiID-5-createDoc.png)

7. Aprire il documento salvato nel percorso personale e copiare il testo. Aprire di nuovo **Facebook** e incollare il testo copiato. Poiché questo documento è stato contrassegnato come personale, sarà possibile incollarne il contenuto in un post di Facebook.

   ![Schermata che illustra che l'utente è in grado di incollare il testo in Facebook.](./media/ft-multiID-6-copyText.png)

### <a name="want-to-learn-more"></a>Altre informazioni
Vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).
