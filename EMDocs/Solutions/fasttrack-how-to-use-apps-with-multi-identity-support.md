---
title: "Come usare app con supporto di più identità"
description: "Come usare app con supporto di più identità"
keywords: 
author: craigcaseyMSFT
manager: jeffgilb
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 586ecd93-b097-42a0-9229-bcf3b781021c
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c704180f9c607e39c27d75676eec30afa1a1730c
ms.openlocfilehash: a45bf5fe6c58c89d386f95cd26a1d2dac68b6c05


---

# Come usare app con supporto di più identità

In questo scenario, viene usato Microsoft Word come esempio. È possibile seguire gli stessi passaggi nelle altre applicazioni incluse in Office 365.
1.  Aprire l'app **Word** nel proprio dispositivo. In questo esempio viene usato un dispositivo iOS.
2.  Toccare **Nuovo** per creare un nuovo documento di Word.

  ![TESTO DESCRITTIVO](./media/ft-multiID-1-createDoc.png)

3.  Digitare una frase a scelta e toccare **Salva**. Verranno presentate due opzioni per il percorso di salvataggio del documento: personale o aziendale. I criteri delle app non sono attive poiché non è stato ancora stabilito se il documento è per uso personale o aziendale.
4.  Salvare il documento in un **percorso aziendale**, ad esempio OneDrive for Business. Poiché OneDrive for Business viene riconosciuto come percorso aziendale, il documento è ora contrassegnato come documento aziendale e vengono applicate le restrizioni dei criteri.

  ![TESTO DESCRITTIVO](./media/ft-multiID-2-saveDoc.png)

5.  A questo punto, aprire il documento salvato nel percorso aziendale e copiare il testo. Aprire l'account personale in **Facebook** e provare a incollare il testo copiato. Si noterà che non è possibile incollare il contenuto nel nuovo post di Facebook. L'opzione Incolla non è disattivata, ma non accade nulla quando si preme **Incolla**. Ciò avviene perché le restrizioni dei criteri impediscono che i dati aziendali vengano condivisi in app personali.

  ![TESTO DESCRITTIVO](./media/ft-multiID-3-copyText.png)

  ![TESTO DESCRITTIVO](./media/ft-multiID-4-pasteInFB.png)
6.  Successivamente, creare un altro documento nuovo di Word ripetendo i passaggi 2 e 3. Digitare una frase a scelta e, questa volta, salvare il documento nel percorso personale, ad esempio **OneDrive - Personale**. Il documento viene contrassegnato come personale e non vengono applicate le restrizioni imposte dai criteri aziendali.

  ![TESTO DESCRITTIVO](./media/ft-multiID-5-createDoc.png)

7.  Aprire il documento salvato nel percorso personale e copiare il testo. Aprire di nuovo **Facebook** e incollare il testo copiato. Poiché questo documento è stato contrassegnato come personale, sarà possibile incollarne il contenuto in un post di Facebook.

  ![TESTO DESCRITTIVO](./media/ft-multiID-6-copyText.png)

### Altre informazioni
Vedere [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).



<!--HONumber=Sep16_HO4-->


