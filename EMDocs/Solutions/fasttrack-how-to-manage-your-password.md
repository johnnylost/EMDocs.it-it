---
title: Gestire la password
description: Come gestire la password
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 162e59f3-33a2-44b5-a59f-24612dc743f3
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 1bf552e92104a7872099e555df12993dd4258293
ms.sourcegitcommit: 0541e4aa400a818551469fe9df8929c25c2dd918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2017
---
# <a name="how-to-manage-your-own-password"></a>Come gestire la password

Agli utenti che non sono amministratori in un'organizzazione che usa Office 365 o Accounts Microsoft per accedere alle risorse aziendali, si consiglia di leggere le sezioni seguenti per informazioni su come risolvere i problemi comuni con la password.

## <a name="how-to-register-for-password-reset"></a>Come eseguire la registrazione per la reimpostazione della password
Il modo più rapido di registrazione per la reimpostazione della password consiste nel visitare il sito [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).

1.  Passare a [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).
2.  Immettere il nome utente e la password.
3.  Scegliere un'opzione di registrazione facendo clic su **Set it up now**. In questo caso, verrà illustrata la registrazione del **telefono per l'autenticazione**.
![Screenshot con blahblah](./media/ft-mngPW-1-setup.png)
4.  Selezionare il prefisso internazionale del paese/area geografica dall'elenco a discesa e digitare il numero di telefono completo con prefisso.
![Screenshot che illustra come selezionare un codice paese. ](./media/ft-mngPW-2-enterNumber.png)![Screenshot che indica dove immettere un numero di telefono.](./media/ft-mngPW-3-enterNumber2.png)
5.  Selezionare una delle opzioni: **Text me (SMS)** o**Call me (Telefonata)**. In questo esempio, viene selezionata l'opzione **Text me (SMS)**, che invierà un codice di 6 cifre al telefono. Attendere alcuni secondi affinché il codice arrivi al telefono.
![Screenshot che illustra un codice a 6 cifre che è stato inviato a un telefono.](./media/ft-mngPW-4-textCode.png)
6.  Quando arriva il codice, digitarlo nella casella di input e fare clic su "Verifica".
7.  Se viene visualizzato il testo **Thanks (Grazie)** vuol dire che l'operazione è stata completata correttamente. Ora è possibile usare ciò che è stato registrato per reimpostare la password in qualsiasi momento dal sito [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com).
![Screenshot che illustra il messaggio di ringraziamento ricevuto quando la registrazione viene completata.](./media/ft-mngPW-5-thanks.png)

> [!IMPORTANT]
> Se l'amministratore consente più opzioni di registrazione, è consigliabile usare un'opzione di backup nel caso in cui venga perso il telefono oppure non si possa accedere alla posta elettronica.

## <a name="how-to-reset-your-password"></a>Come reimpostare la password
Seguire la procedura illustrata di seguito per reimpostare la password dell'account aziendale o dell'istituto di istruzione da qualsiasi schermata di accesso all'account.

> [!IMPORTANT]
> Questa funzionalità è disponibile solo se è stata attivata dall'amministratore. Se non è attivata, verrà visualizzato un messaggio che indica che l'account non è abilitato per questa funzionalità. È possibile usare il collegamento "Contattare l'amministratore" per chiedere di sbloccare l'account.
>
Se questa funzionalità è stata attivata, è necessario innanzitutto registrarsi prima di poterla usare. La registrazione può essere fatta in questo sito: [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).

1.  In qualsiasi pagina di accesso all'account aziendale o dell'istituto di istruzione, fare clic sul collegamento "can't access your account? (impossibile accedere all'account?)" O "forgot your password? (password dimenticata?)" Oppure aprire direttamente il sito [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com).
![Screenshot che illustra il primo messaggio che un utente riceve se l'ID utente o la password non sono stati riconosciuti.](./media/ft-mngPW-6-resetPWbegin.png)
2.  Nella pagina "who are you? (Identificarsi)" immettere l'ID dell'account aziendale o dell'istituto di istruzione e dimostrare di non essere un robot inserendo il captcha.
![Screenshot in cui viene richiesto all'utente di immettere l'ID utente e il codice captcha visualizzato.](./media/ft-mngPW-7-enterID.png)
3.  Fare clic su **Avanti**.
4.  Scegliere un'opzione per reimpostare la password. A seconda di come l'amministratore ha configurato il sistema, è possibile visualizzare uno o più delle opzioni seguenti:
 - **Invia messaggio di posta elettronica all'indirizzo di posta elettronica alternativo dell'utente**: invia un messaggio di posta elettronica con un codice di 6 cifre all'indirizzo di posta elettronica alternativo o all'indirizzo di posta elettronica di autenticazione (in base alla scelta dell'utente).
  - **Invia SMS sul telefono cellulare**: invia un SMS con un codice di 6 cifre al telefono cellulare o all'indirizzo di posta elettronica di autenticazione (in base alla scelta dell'utente).
  - **Chiama telefono cellulare**: chiama il telefono cellulare o il telefono di autenticazione (in base alla scelta dell'utente); premere il tasto # per verificare la chiamata.
 - **Chiama telefono ufficio**: chiama il telefono dell'ufficio; premere il tasto # per verificare la chiamata.
 - **Rispondi alle domande di sicurezza**: visualizza le domande di sicurezza, precedentemente definite, alle quali rispondere.
 ![Screenshot in cui viene richiesto all'utente di scegliere il metodo con cui vuole essere contattato per la verifica.](./media/ft-mngPW-8-answerQuestions.png)
5.  In questo esempio viene usata l'opzione **Invia SMS sul telefono cellulare**. Se si sceglie un'opzione basata su telefono, è necessario verificare il numero di telefono prima di ricevere un SMS. Digitare il numero di telefono completo e fare clic su **Avanti** per verificare che sia corretto e inviare un SMS.
![Screenshot che indica che l'utente deve immettere il numero di telefono su cui riceverà un SMS di verifica.](./media/ft-mngPW-9-textNumber.png)
6.  Quando si riceve l'SMS, assicurarsi di usare il codice di verifica incluso nel corpo del messaggio e non il numero di codice del mittente. Potrebbero passare alcuni minuti tra l'invio e la ricezione dell'SMS.
![Screenshot che illustra il codice di verifica ricevuto.](./media/ft-mngPW-10-verificationCode.png)
7.  Dopo la ricezione dell'SMS, digitare il codice appena ricevuto nella casella di input della pagina.
![Screenshot che indica che l'utente deve immettere il codice di verifica appena ricevuto.](./media/ft-mngPW-11-enterCode.png)
8.  È possibile che l'amministratore richieda un secondo passaggio di verifica; nel qual caso ripetere il passaggio 4 con un'altra opzione.
9.  Nella schermata "Scegliere una nuova password", digitare una nuova password, confermarla e fare clic su **Fine**.
![Screenshot che indica che l'utente deve immettere e confermare una nuova password.](./media/ft-mngPW-12-clickFinish.png)
10. Viene visualizzata una pagina in cui viene specificato che la procedura è stata completata con esito positivo. È ora possibile accedere con la nuova password.
![Screenshot che indica che il processo di reimpostazione della password è stato completato.](./media/ft-mngPW-13-success.png)
Problemi durante l'impostazione della password? Leggere le informazioni sui [problemi comuni e relative soluzioni](https://azure.microsoft.com/en-us/documentation/articles/active-directory-passwords-update-your-own-password/#common-problems-and-their-solutions).

### <a name="want-to-learn-more"></a>Altre informazioni
Vedere [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).
