---
title: Simulazione di attacchi con Advanced Threat Analytics
description: "Questa guida aiuterà i clienti a comprendere gli attacchi finalizzati al furto di credenziali contro un sistema operativo Windows, come usare gli strumenti di ricerca disponibili pubblicamente per eseguire azioni di questo tipo e in che modo Microsoft ATA può rilevare queste minacce."
author: yuridio
ms.author: yurid
manager: mbaldwin
ms.date: 06/06/2017
ms.topic: solution
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: techgroup-identity
ms.assetid: da5eda7c-29bb-429f-9366-72495667c010
ms.reviewer: v-craic
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: b14dcbddb611dc49da2f92cf3f1aca1593af11c0
ms.openlocfilehash: 923f827a8c122af393b1909ba55bb73c650d62fc
ms.contentlocale: it-it
ms.lasthandoff: 07/07/2017


---

<a id="advanced-threat-analytics-attack-simulation-playbook" class="xliff"></a>
# Simulazione di attacchi con Advanced Threat Analytics

Questa guida consentirà di capire il furto di credenziali, ad esempio Pass-the-Hash, Pass-the-Ticket, Over-Pass-the-Hash, e come usare gli strumenti di ricerca disponibili pubblicamente per eseguire azioni di questo tipo. Questa simulazione si basa su uno scenario costruito con strumenti Internet validi utilizzati dagli autori degli attacchi. Lo scopo è spiegare come pensano gli autori degli attacchi (nei grafici), come muoversi all'interno di un ambiente con credenziali rubate e come usare Microsoft Advanced Threat Analytics (ATA) per rilevare attività di questo tipo nell'ambiente in uso.

Questa guida illustra i seguenti scenari di attacco:

- Esplorazione DNS
- Enumerazione dei servizi di directory
- Enumerazione delle sessioni SMB
- Raccolta delle credenziali (lsass.exe)
- Overpass-the-Hash
- Pass-the-Ticket
- Esecuzione di codice da remoto
- Skeleton Key
- DC Sync

> [!IMPORTANT]
> I passaggi indicati in questa guida devono essere completati in ambiente lab e non in ambiente di produzione.

<a id="configuring-your-lab-environment" class="xliff"></a>
## Configurazione dell'ambiente lab

Si consiglia di seguire fedelmente queste istruzioni, inclusi gli esperimenti alla fine.  È necessario completare alcuni passaggi di preparazione, in particolare avere quattro computer, tre utenti e disporre di programmi di ricerca in grado di cercare su Internet.

Per informazioni aggiuntive su come installare ATA e per ottenere una copia di valutazione di 90 giorni, visitare [Advanced Threat Analytics Valutazioni](http://aka.ms/ataeval). 

> [!IMPORTANT]
> Questa guida si basa su ATA versione 1.7.


<a id="scenario" class="xliff"></a>
### Scenario

Nell'esempio di questa esercitazione JeffV è amministratore della propria workstation.  In molti reparti IT gli utenti possiedono privilegi amministrativi.  In questi scenari gli attacchi di escalation dei privilegi locali non sono necessari, in quanto il malintenzionato ha già l'accesso di amministratore nell'ambiente da cui eseguire le operazioni di post-infiltrazione. 
 
Tuttavia, anche quando i reparti IT limitano i privilegi e usano account senza privilegi amministrativi, vengono eseguite altre forme di attacchi (note come vulnerabilità delle applicazioni, 0 giorni e così via) per ottenere l'escalation dei privilegi locali. In questo caso la guida presuppone che il malintenzionato abbia ottenuto l'escalation dei privilegi locali nel computer vittima.  In questa esercitazione la si è ottenuta tramite un messaggio di posta elettronica di spear phishing inviato a JeffV, come illustrato nei dettagli più avanti in questa guida.


<a id="servers-and-workstations" class="xliff"></a>
### Server e workstation

Di seguito sono elencati i computer che saranno necessari e le configurazioni utilizzate in questo esercizio.  Sono tutte macchine virtuali (VM) guest in Windows 10 Hyper-V.  Se si effettua questa scelta, che è quella consigliata, assicurarsi che le VM siano inserite nello stesso commutatore virtuale.

| Nome di dominio completo (FQDN) | Sistema operativo | IP | Scopo |
| --- | --- | --- | --- |
| DC1.contoso.local | Windows Server 2012 R2 | 192.168.10.10 | Controller di dominio con ATA e Lightweight Gateway (LWGW) installato |
| ATACenter.contoso.local | Windows Server 2012 R2 | 192.168.10.20 | Centro ATA |
| Admin-PC.contoso.local | Windows 7 Enterprise | 192.168.10.30 | PC dell'amministratore |
| Victim-PC.contoso.local | Windows 7 Enterprise | 192.168.10.31 | PC della vittima |

Il dominio per questa esercitazione è denominato "CONTOSO. LOCAL". Creare il dominio e quindi aggiungervi questi computer. Quando tutti e quattro i computer sono attivi e appartenenti al dominio, passare alla sezione successiva per aggiungere alcuni utenti fittizi all'ambiente.


<a id="users-configuration" class="xliff"></a>
### Configurazione degli utenti

Si creeranno ora ruoli diversi per "Helpdesk" e "Domain Admin".  Lo scopo della creazione di tali ruoli è separare i compiti, ma si apprenderà più avanti in questa guida che ciò non è sufficiente a impedire il furto di credenziali, lo spostamento trasversale o l'escalation del dominio, perché è difficile comprendere le dipendenze di sicurezza oltre questi due gruppi all'interno di un ambiente. 

Creare innanzitutto i seguenti utenti nel dominio: 

| Nome | Membri | Scopo |
| --- | --- | --- |
| Supporto tecnico | RonHD | Gestisce i client di contoso.local. |

Creare ora il seguente gruppo di sicurezza con un solo membro specifico:

| Nome completo | SAMAccount | Scopo |
| --- | --- | --- |
| Jeff vittima | JeffV | La vittima di un altro attacco di spear phishing straordinariamente efficace |
| Ron HD | RonHD | Ron è l'utente "preso di mira" del reparto IT di Contoso.  RonHD è membro del gruppo di sicurezza "Helpdesk". |
| Nuck Chorris | NuckC | Prima d'ora si credeva che non esistesse.  In Contoso risulta essere il *Domain Admin*. |

> [!IMPORTANT]
> Prima di procedere assicurarsi che *RonHD* sia stato aggiunto come membro al gruppo di sicurezza *Helpdesk*.


Nuck Chorris, amministratore di dominio di Contoso, usa la workstation *Admin-PC*. Il gruppo di sicurezza *Helpdesk* (di cui *RonHD* è membro) gestisce anche il computer di *NuckC*.  È possibile eseguire questa configurazione mediante [gruppi con restrizioni](https://support.microsoft.com/kb/279301). Le proprietà del gruppo dell'amministratore dovrebbero essere simili alla schermata seguente:

![Proprietà di amministrazione](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig1.png)

Inoltre, come in molti reparti IT, *JeffV* è stato aggiunto come amministratore nel proprio dispositivo (*Victim-PC*).  L'operazione è stata eseguita di proposito e sarà spiegata più avanti in questo articolo. Le proprietà del gruppo dell'amministratore locale saranno simili alla schermata seguente:

![Proprietà degli amministratori 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig2.png)


<a id="security-research-tools" class="xliff"></a>
### Strumenti di ricerca di sicurezza

Per configurare questa esercitazione è necessario scaricare e installare gli strumenti indicati di seguito in *C:\tools* nel computer *Victim-PC*:

- [Mimikatz](https://github.com/gentilkiwi/mimikatz)
- [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)
- [PsExec](https://technet.microsoft.com/en-us/sysinternals/bb897553.aspx) 
- [NetSess.exe](http://www.joeware.net/freetools)

La cartella degli strumenti sarà simile a quella illustrata nella figura seguente:

![Proprietà di amministrazione](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig3.png)


> [!IMPORTANT]
> Questi strumenti sono finalizzati esclusivamente alla ricerca.  Microsoft non possiede questi strumenti e non può garantire sul loro funzionamento.  Questi strumenti devono essere eseguiti solo in un ambiente di testing.

Ai fini di questa esercitazione, disattivare tutti i programmi antivirus nel computer *Victim-PC*. Nonostante si possa credere che la disattivazione dei programmi antivirus influisca sui risultati, è importante notare che il codice sorgente per questi strumenti è disponibile gratuitamente, perciò gli autori degli attacchi possono modificarlo per eludere il rilevamento basato su firma del software antivirus. È importante notare anche che, non appena un malintenzionato ottiene l'amministrazione locale su un computer, nulla gli impedisce di eludere l'antivirus.  L'obiettivo a quel punto è proteggere il resto dell'organizzazione. La compromissione di un solo computer non deve portare all'escalation fino al dominio e certamente non alla violazione del dominio.

<a id="environment-topology" class="xliff"></a>
### Topologia dell'ambiente

A questo punto il codice sarà simile al seguente:

![Topologia](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig4.png)

Come accennato in precedenza in questa guida, abbiamo ruoli diversi per *Domain Admins* e *Helpdesk* tuttavia, durante la dimostrazione, si vedrà che a un utente malintenzionato basta un solo collegamento di dipendenza di sicurezza (in questo caso l'utente *RonHD*) per impadronirsi dell'intero ambiente con strumenti di ricerca pubblicamente disponibili.

<a id="helpdesk-simulation" class="xliff"></a>
### Simulazione con il ruolo Helpdesk

Per simulare uno scenario comune del supporto tecnico, in cui il personale si registra in computer diversi, accedere come *RonHD* a *Victim-PC* e quindi eseguire nuovamente l'accesso come *JeffV*.  Usare il meccanismo di "cambio utente" per simulare la gestione delle credenziali con privilegi nella workstation.

![Cambia utente](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig5.png)


Esistono altri modi per simulare il flusso di lavoro di gestione in questa esercitazione, ad esempio creare account di servizio con script batch, attività pianificate e sessione RDP o "runas" nella riga di comando.  Nelle operazioni sicure qualcosa (non sempre qualcuno) deve gestire queste risorse e per gestirle deve possedere privilegi di amministratore locale. Per gli scopi di questa esercitazione e per risparmiare tempo, è stata scelta la strada più veloce per simulare questo flusso di lavoro.

> [!IMPORTANT]
> Non disconnettersi o riavviare *Victim-PC* ora, poiché ciò comporterà la cancellazione delle credenziali di *RonHD* dalla memoria e occorrerà ripetere lo scenario *helpdesk*. 

La tabella seguente riepiloga le credenziali salvate in ogni computer:

| Computer | Credenziali salvate nel computer |
| --- | --- |
| Admin-PC | - NuckC |
| Victim-PC | -JeffV e RonHD (come conseguenza dello scenario helpdesk) |

A questo punto l'ambiente lab è pronto. L'esercitazione ha raggiunto attualmente uno stato tale che per la violazione del dominio basta un solo exploit (la violazione del dominio è "one-exploit-away" o #1ea).  Successivamente si vedrà che la singola violazione in genere proviene dalle risorse del dominio con i minimi privilegi verso le applicazioni più esposte a Internet da parte di un malintenzionato altamente motivato e che non si fermerà.  Qui entra in gioco la metodologia di [presupporre una violazione](https://blogs.msdn.microsoft.com/azuresecurity/2015/10/19/an-insiders-look-at-the-security-of-microsoft-azure-assume-the-breach/).

<a id="executing-the-attack" class="xliff"></a>
## Eseguire l'attacco

In questa sezione della guida si useranno strumenti reali e si simuleranno attività di post-infiltrazione di un malintenzionato.

<a id="beachhead-via-spearphish" class="xliff"></a>
### Creazione di teste di ponte mediante spear phish

Per questa simulazione di attacco il presupposto è che il malintenzionato abbia ottenuto privilegi di amministratore locale in un solo computer nell'ambiente.  Sebbene questo si possa ottenere tramite metodi diversi, il mezzo più frequente sono le campagne di spear phshing contro l'organizzazione. 

Nel [Microsoft Security Intelligence Report Volume 21](https://www.microsoft.com/security/sir/default.aspx) sono trattati due diversi gruppi di attività, PROMETHIUM e NEODYNIUM. Entrambi i gruppi di attività partecipano all'attacco di spear phishing per entrare negli ambienti presi di mira.  Perché?  La posta elettronica è un modo rapido per gli autori degli attacchi di eludere le difese di rete di un'organizzazione. Nell'immagine seguente è riportato un esempio di un reale messaggio di posta elettronica di spear phishing a cui Microsoft Threat Intelligence Center ha risposto.

![Messaggio di posta elettronica di spear phising](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig6.png)


In un ambiente protetto la perdita di un singolo host non deve comportare la compromissione di un intero dominio o foresta.  Individuare la mossa successiva del malintenzionato è fondamentale nel "post-violazione".

<a id="reconnaissance" class="xliff"></a>
### Esplorazione

Quando un malintenzionato umano entra in un ambiente, inizia l'esplorazione (o riconoscimento).  In questa fase il malintenzionato dedice tempo a eseguire ricerche nell'ambiente: individuare le impostazioni, i computer di interesse, enumerare i gruppi di sicurezza e altri oggetti di Active Directory di interesse e così via, per disegnare un'immagine utile dell'ambiente.

<a id="dns-reconnaissance" class="xliff"></a>
#### Esplorazione DNS

Una delle prime cose che molti malintenzionati faranno sarà tentare di ricevere tutti i contenuti dal DNS, e Microsoft ATA può rilevare questa azione.

Nel computer Victim-PC si avvierà DNS Recon eseguendo l'accesso con le credenziali di JeffV, ovvero il PC e l'utente compromessi dal malintenzionato, ed eseguendo i comandi seguenti: 
    
    nslookup
    ls -d contoso.local

I risultanti saranno simili alla schermata seguente:

![Nslookup](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig7.png)

In questa esercitazione il DNS è configurato in modo da bloccare l'operazione di dump DNS verso il dominio. Purtroppo però questo evento viene spesso ignorato o si perde nel rumore nella rete, impedendo ai difensori della rete di rendersi conto che un utente malintenzionato ha raggiunto un certo livello di accesso nel proprio ambiente e sta avviando un attacco più mirato.

Microsoft ATA consente di rilevare questo tipo di attacco individuando le attività DNS sospette, come illustrato di seguito:

![Nslookup](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig8.png)

Poiché ATA analizza continuamente il traffico DNS, può vedere la richiesta di dump, che riesca o meno.  Offre anche la possibilità di imparare dall'evento per il futuro, nel caso l'attività sospetta sia legittima e provenga da una periferica di scansione DNS approvata.

In questo caso al malintenzionato sarà impedito di realizzare la conquista a cui mirava, ovvero eseguire un dump DNS, e dovrà ripiegare su altre tecniche di esplorazione.

> [!IMPORTANT]
> Il rilevamento degli attacchi non riusciti contro un ambiente può essere altrettanto utile del rilevamento di quelli riusciti.
 
Nell'avviso ATA illustrato sopra è possibile notare la bolla blu per le attività sospette che indica che ATA impara continuamente sia dai dati utilizzati sia dall'analista.  Il commento dell'analista consente di eliminare i positivi benigni e di ridurre il rumore nel tempo, personalizzando ATA e il suo rilevamento delle attività sospette nell'ambiente.

<a id="directory-services-enumeration" class="xliff"></a>
#### Enumerazione dei servizi di directory

[Security Account Manager Remote Protocol (SAMR)](https://msdn.microsoft.com/library/cc245477.aspx) offre funzionalità di gestione per gli utenti e i gruppi in tutto il dominio.  Conoscere la relazione tra utenti, gruppi e privilegi può essere estremamente importante per un malintenzionato.  Qualsiasi utente autenticato può eseguire questi comandi. Per altre informazioni sulle impostazioni SAMR e la limitazione di tale riconoscimento solo agli utenti che sono membri del gruppo Local Administrators, vedere [questo white paper](https://gallery.technet.microsoft.com/SAMRi10-Hardening-Remote-48d94b5b#content).

<a id="enumerate-all-users-and-groups" class="xliff"></a>
#### Enumerare tutti gli utenti e gruppi

L'enumerazione di utenti e gruppi è molto utile per un malintenzionato.  Conoscere i nomi degli utenti e dei gruppi può rivelarsi utile.  Nei panni dell'autore di un attacco, si desidera ottenere più informazioni possibile durante la fase di esplorazione.

Per simulare l'enumerazione degli utenti e dei gruppi è necessario usare l'account *JeffV* compromesso, per accedere al computer *Victim-PC*. Dopo aver eseguito l'accesso si tenterà di ottenere tutti gli utenti e i gruppi del dominio tramite i comandi seguenti:

    net user /domain
    net group /domain

Nella figura seguente è riportato un esempio del risultato del primo comando:

![Net user](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig9.png)

Nella figura seguente è riportato un esempio del risultato del secondo comando:

![Net group](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig10.png)

Queste operazioni riescono senza problemi perché vengono eseguite usando credenziali legittime. Il problema è che l'autore dell'attacco ora conosce tutti gli utenti e i gruppi dell'ambiente. Senza uno strumento come Microsoft ATA, questa azione passerebbe probabilmente inosservata.

Per questa operazione Microsoft ATA mostra un avviso che notifica l'attacco e visualizza anche i dati che l'autore dell'attacco è riuscito a ottenere.

![Riconoscimento](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig11.png)

<a id="enumerate-high-privileged-accounts" class="xliff"></a>
#### Enumerazione degli account con privilegi elevati

Ora l'autore dell'attacco possiede sia l'elenco degli utenti che l'elenco dei gruppi.  Ma è importante anche sapere chi fa parte di ciascun gruppo, in particolare per i gruppi con privilegi elevati, ad esempio *Enterprise Admins* e *Domain Admins*. Per ottenere queste informazioni nell'ambiente lab eseguire l'accesso come *JeffV* nel computer *Victim-PC* ed eseguire il comando seguente:

    net group “domain admins” /domain

Nella figura seguente è riportato un esempio del risultato di questo comando:

![Net group 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig12.png)

L'autore dell'attacco ora conosce tutti gli utenti e i gruppi e sa quali utenti possiedono gli elevati privilegi del gruppo *Domain Admins*. In uno scenario reale la probabilità che l'autore dell'attacco continuerà con un'escalation nel tentativo di impadronirsi anche dei privilegi di Enterprise Admins è molto elevata, poiché non esiste alcuna barriera nel sistema di sicurezza tra *Enterprise Admins* e *Domain Admins*.

> [!IMPORTANT]
> Per altre informazioni sulle barriere di sicurezza tra foreste e domini, Enterprise Admins e Domain Admins, e altri privilegi "di livello 0", vedere [Materiale di riferimento per la protezione dell'accesso con privilegi](http://www.aka.ms/tier0).

Per ottenere l'elenco dei membri del gruppo *Enterprise Admins* nell'ambiente lab, eseguire il comando seguente su *Victim-PC*:

    net group “enterprise admins” /domain

Nella figura seguente è riportato un esempio del risultato di questo comando:

![Net group 3](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig13.png)

Nell'esempio illustrato sopra esiste un solo account nel gruppo *Enterprise Admins*. In questo caso non si tratta di un'informazione molto utile, in quanto è l'impostazione predefinita, ma l'autore dell'attacco sa qualcosa di più sugli account e ha identificato l'utente che desidera maggiormente compromettere.

<a id="smb-session-enumeration" class="xliff"></a>
### Enumerazione delle sessioni SMB

A questo punto l'autore dell'attacco sa di chi vuole violare le credenziali, ma con le informazioni attuali non sa esattamente come violarle. Tramite l'enumerazione SMB può ottenere il percorso preciso in cui questi account molto interessanti sono esposti.

Tutti gli utenti autenticati devono connettersi al controller di dominio per elaborare i criteri di gruppo (in SYSVOL) rendendo l'enumerazione SMB uno strumento prezioso per gli autori degli attacchi. Questo fa dei controller di dominio (DC) gli obiettivi principali su cui eseguire l'enumerazione SMB.

In questa parte dell'esercitazione si userà *NetSess*, il primo strumento di ricerca scaricato da Internet.  *NetSess* è uno strumento della riga di comando che consente di enumerare le sessioni NetBIOS in un determinato computer locale o remoto.  

Per enumerare gli utenti connessi a un computer specifico, in questo caso il controller di dominio, in *Victim-PC*, passare al percorso in cui NetSess è salvato localmente ed eseguire il comando seguente:

    NetSess.exe dc1.contoso.local

Nella figura seguente è riportato un esempio del risultato di questo comando:

![NetSess](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig14.png)

Questo tipo di esplorazione è difficile da rilevare con i controlli di sicurezza tradizionali, ad esempio un firewall. Ciò che aumenta la probabilità che questo tipo di attacco abbia esito positivo è il fatto che il protocollo SMB è ampiamente usato nei reparti IT ed è un protocollo che fa affidamento su Active Directory per molte operazioni. Microsoft ATA è in grado di rilevare l'attività di enumerazione delle sessioni SMB e di attivare un avviso che informa su quali account sono stati esposti.

Microsoft ATA consente di ottenere gli stessi dati rilevanti che ha ottenuto l'autore dell'attacco, identifica l'account di origine, il computer di origine e anche gli account esposti e gli indirizzi IP al momento dell'enumerazione del malintenzionato. È possibile vedere un esempio nella schermata seguente:

![SMB](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig15.png)

I dati che Microsoft ATA offre all'utente sono fondamentali per migliorare la consapevolezza della sicurezza ed essere più preparati a rispondere agli attacchi.

<a id="lateral-movement" class="xliff"></a>
### Movimento laterale

L'obiettivo di questa fase è accedere all'indirizzo IP che è stato individuato in precedenza (192.168.10.30), dove sono esposte le credenziali del computer di *NuckC*. Per eseguire questa azione si enumereranno le credenziali in memoria che si trovano in *Victim-PC*. Tenere presente che *Victim-PC* non è esposto alle credenziali di *JeffV* ed esistono molti altri account che potrebbe essere utile individuare per l'autore di un attacco. 


Per estrarre le credenziali da *Victim-PC* si userà mimikatz, un altro strumento di ricerca scaricato da Internet. Da un prompt dei comandi con privilegi elevati in *Victim-PC* passare alla cartella degli strumenti in cui *Mimikatz* è stato salvato ed eseguire il comando seguente:

    mimikatz.exe “privilege::debug” “sekurlsa::logonpasswords” “exit” >> c:\temp\victim-pc.txt

Nella figura seguente è riportato un esempio del risultato di questo comando:

![mimikatz](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig16.png)

Il comando precedente esegue mimikatz che raccoglierà le credenziali in memoria.  Lo strumento scriverà le informazioni in un file di testo denominato "victim-pc.txt". Aprire il file "victim-pc.txt" per vedere cosa contiene.

Il passaggio successivo è analizzare l'output del dump delle credenziali di *mimikatz* e a tale scopo è necessario aprire il file "victim-pc.txt" nel Blocco note.  Il file avrà un aspetto diverso in quanto sono state usate password diverse, sistemi operativi potenzialmente differenti con attivate altre impostazioni predefinite, perciò non bisogna preoccuparsi se il proprio file non è esattamente uguale all'esempio seguente.

![Output](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig17.png)

Da questo esempio di output si nota che l'autore dell'attacco ha trovato le credenziali di JeffV, il che gli consentirà di rappresentare JeffV. L'autore dell'attacco ha trovato anche l'account del computer che, come un account utente, può essere aggiunto al gruppo *Local Admin* e ad altri gruppi di sicurezza con privilegi elevati di altri computer.  Ciò non sarebbe utile in questo scenario, ma bisogna sempre tenere presente che gli *account computer* possono anche essere collegati a privilegi altrove.

Nell'esempio seguente si noterà che l'autore dell'attacco ha rilevato anche un account potenzialmente interessante, *RonHD*. Bisogna tenere presente che *RonHD* aveva eseguito l'accesso a *Victim-PC* durante la fase di configurazione. Le sue credenziale sono state esposte al [processo LSA](https://msdn.microsoft.com/library/windows/desktop/aa378327%28v=vs.85%29.aspx) in memoria in quel momento, cosa che mimikatz aveva reso visibile all'autore dell'attacco. L'utente *RonHD* non è stato elencato quando è stata eseguita l'enumerazione degli utenti in *Domain Admins* o *Enterprise Admins*, ma ora si ha accesso alle sue credenziali.

![Nslookup](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig18.png)

È anche importante notare che in alcuni casi il dump di mimikatz potrebbe rivelare password in testo normale, quando l'ambiente non è aggiornato o non configurato per bloccare [WDigest](https://blogs.technet.microsoft.com/kfalde/2014/11/01/kb2871997-and-wdigest-part-1/). Un ambiente aggiornato, seguendo le procedure consigliate, restituirà un campo *Password* vuoto.   

Come autore dell'attacco, il passaggio naturale successivo consiste nel verificare se l'account di *RonHD* ha un valore e per farlo l'autore dell'attacco eseguirà operazioni di riconoscimento sull'account. Per simulare questo nell'ambiente lab eseguire il comando seguente in *Victim-PC*:

    net user ronhd /domain

Nella figura seguente è riportato un esempio del risultato di questo comando:

![net user domain](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig19.png)

Sulla base di questo risultato l'autore dell'attacco apprenderà che *RonHD* è membro di *Helpdesk*. L'account di *RonHD* è diventato interessante per l'autore dell'attacco.  Tuttavia è necessaria un'ulteriore analisi per verificare se l'account dispone di privilegi amministrativi in altri computer. Dopo tutto avrebbe poco senso usarlo per spostarsi lateralmente in un altro computer e scoprire che possiede privilegi inferiori rispetto alle credenziali di cui l'autore dell'attacco è già in possesso.

In base a ciò, il passaggio successivo consiste nell'enumerare i membri del computer remoto. In questo passaggio si userà *PowerSploit*, una serie di moduli di PowerShell utilizzati dai tester di penetrazione. Aprire una sessione di PowerShell e passare al percorso in cui *PowerSploit* è salvato localmente in *Victim-PC*.  Nella console di PowerShell eseguire il comando seguente:

    Import-Module .\PowerSploit.psm1
    Get-NetLocalGroup 192.168.10.30

Il primo comando viene usato per importare il modulo di *PowerSploit* in memoria e il secondo comando esegue una delle funzioni fornite da tale modulo, in questo caso *Get-NetLocalGroup*.

Nella figura seguente è riportato un esempio del risultato di questo comando:

![PowerShell](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig20.png)

L'indirizzo IP 192.168.10.30 è l'indirizzo IP individuato dalla fase di enumerazione SMB, come già indicato in precedenza in questa guida. L'autore dell'attacco ha trovato le informazioni seguenti: 

- L'indirizzo IP 192.168.10.30 è connesso ad *Admin-PC* (anche la risoluzione dei nomi è stata eseguita tramite PowerSploit)
- "Contoso.local/Domain Admins" e "Contoso.local/Helpdesk" sono membri del *gruppo Administrators*

*RonHD* è membro del gruppo *Helpdesk*, pertanto *RonHD* può concedere all'autore dell'attacco privilegi *Admin* in *Admin-PC* (dove l'autore dell'attacco sa che si trova *NuckC*, grazie all'esplorazione precedente).  
L'autore dell'attacco ha usato questo [modo di pensare simile a un grafico](https://blogs.technet.microsoft.com/johnla/2015/04/26/defenders-think-in-lists-attackers-think-in-graphs-as-long-as-this-is-true-attackers-win/) per individuare le relazioni nella rete. I difensori devono adottare questo tipo di mentalità per gestire le nuove minacce alle reti aziendali. 

A questo punto è possibile usare *RonHD* per eseguire lo spostamento laterale mediante un attacco [Overpass-the-Hash](). Se l'autore dell'attacco si trova in un ambiente in cui non è disattivato WDigest, la partita è già terminata, in quanto dispone della password in testo normale.  Tuttavia, ai fini di questa esercitazione si presuppone di non conoscere/avere accesso alla password in testo normale.

Usando una tecnica denominata Overpass-the-Hash è possibile prendere l'hash NTLM e usarlo per ottenere un Ticket Granting Ticket (TGT) tramite Kerberos\Active Directory.  Con un TGT è possibile mascherarsi da Ron**HD e accedere a qualsiasi risorsa del dominio a cui ha accesso *RonHD*.  

Copiare l'hash NTLM di *RonHD* da victim-pc.txt, raccolto in precedenza (da "Azione: Eseguire il dump delle credenziali da Victim-PC"). Successivamente accedere a *Victim-PC*, accedere al percorso in cui *mimikatz* è stato salvato nel file system ed eseguire i comandi seguenti:

    Mimikatz.exe “privilege::debug” “sekurlsa::pth /user:RonHD /ntlm:[ntlm hash] /domain:contoso.local” “exit”

Assicurarsi di sostituire *[ntlm hash]* con il valore NTLM contenuto in victim-pc.txt.

Nella figura seguente è riportato un esempio del risultato di questo comando:

![mimikatz 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig21.png)

Si apre una nuova sessione del prompt dei comandi e vengono inserite le credenziali di *del RonHD*. Per verificare se è possibile leggere il contenuto di C$ del computer *Admin-PC* (qualcosa che *JeffV* non deve essere in grado di fare), eseguire il comando seguente dalla nuova sessione della riga di comando:

    dir \\admin-pc\c$
   
Nella figura seguente è riportato un esempio del risultato di questo comando:

![Dir](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig22.png)

Il risultato del comando dimostra che a questo punto si dispone dell'accesso all'unità C del computer *Admin-PC*. Ora si verificherà che il nuovo prompt dei comandi aperto ha inserito il ticket di *RonHD* e non è semplicemente stato configurato in modo errato *JeffV* con diritti di lettura.

Successivamente si analizzeranno i ticket nel prompt dei comandi overpass-the-hash. Dal nuovo prompt dei comandi che si è aperto in seguito all'attacco overpass-the-hash, eseguire il comando seguente:

    klist

Nella figura seguente è riportato un esempio del risultato di questo comando:

![klist](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig23.png)

Come si può vedere, ora si rappresenta *RonHD* in questo prompt dei comandi il che testimonia che sono state usate le sue credenziali legittime per accedere al suo *Admin-PC*.

Si sarà probabilmente notato che Microsoft ATA ha generato un avviso relativo a un'implementazione insolita del protocollo, come illustrato di seguito. Ciò accade perché overpass-the-hash usa NTLM e di conseguenza RC4. Dal punto di vista del difensore, si apprenderà che sul computer *Victim-PC*, l'account di RonHD si è autenticato con il controller di dominio.  È quindi possibile iniziare l'analisi.

![Protocollo insolito](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig24.png) 

<a id="domain-escalation" class="xliff"></a>
### Escalation al dominio

L'autore dell'attacco dispone ora dell'accesso ad *Admin-PC*, un computer che dall'esplorazione precedente è stato identificato come efficace vettore dell'attacco per compromettere l'account con privilegi elevati *NuckC*. L'autore dell'attacco adesso desidera spostarsi in *Admin-PC*, realizzando un'escalation dei propri privilegi all'interno del dominio.

A tale scopo l'autore dell'attacco raccoglierà le credenziali eseguendo un attacco [Pass-the-Hash](https://www.microsoft.com/security/sir/strategy/default.aspx#!pass_the_hash_defenses) che ci consentirà di spostarci in *Admin-PC*.   

Dal nuovo prompt dei comandi, in esecuzione nel contesto di *RonHD*, passare alla sezione del file system in cui si trova mimikatz da quella libreria ed eseguire il comando seguente:

    xcopy mimikatz \\admin-pc\c$\temp

Successivamente eseguire mimiKatz da remoto per esportare tutti i ticket Kerberos da *Admin-PC*, con il comando seguente:

    psexec.exe \\admin-pc -accepteula cmd /c (cd c:\temp ^& mimikatz.exe “privilege::debug” “sekurlsa::tickets /export” ^& “exit”)

Copiare di nuovo i ticket in *Victim-PC* con il comando seguente:

    xcopy \\admin-pc\c$\temp c:\temp\tickets

Nella figura seguente è riportato un esempio del risultato di questo comando:

![XCopy](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig25.png) 

Questa operazione ha dimostrato che l'autore dell'attacco è riuscito a copiare lo strumento *mimikatz* in *Admin-PC*. L'autore dell'attacco è riuscito a eseguire mimikatz da remoto esportando tutti i ticket Kerberos da *Admin-PC*.  Infine, l'autore dell'attacco ha copiato i risultati in *Victim-PC* e ora ha le credenziali di *NuckC* senza la necessità di violare il suo computer.

Il passaggio successivo consiste nel trovare il TGT di *NuckC*. Per farlo è necessario individuare i file kirbi che non sono di *NuckC* (vale a dire "ADMIN-PC$"), eliminarli e mantenere i ticket di *NuckC*.

Nella figura seguente è riportato un esempio del risultato di questo comando:

![Explorer](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig26.png) 

A questo punto l'autore dell'attacco può passare i ticket in memoria e usarli per accedere alle risorse come se fosse *NuckC*. L'autore dell'attacco è pronto a importarli nella memoria di *Victim-PC* per ottenere le credenziali con cui accedere alle risorse sensibili. Questa operazione viene eseguita tramite un attacco [Pass-the-Ticket](https://blogs.technet.microsoft.com/windowsserver/tag/pass-the-ticket/).

Da un prompt dei comandi con privilegi elevati, in cui *mimikatz* si trova nel file system, eseguire il comando seguente:

    mimikatz.exe “privilege::debug” “kerberos::ptt c:\temp\tickets” “exit”

Nella figura seguente è riportato un esempio del risultato di questo comando:

![mimikatz privilege](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig27.png) 

Assicurarsi che i ticket  *NuckC@krbtgt-CONTOSO.LOCAL*  siano stati importati correttamente come illustrato nell'esempio precedente.

Quindi è necessario verificare che nella sessione del prompt dei comandi ci siano i ticket giusti. Per farlo, eseguire il comando seguente dallo stesso prompt dei comandi con privilegi elevati:

    klist

Nella figura seguente è riportato un esempio del risultato di questo comando:

![klist 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig28.png) 

L'autore dell'attacco è riuscito a importare il ticket raccolto nella sessione e a questo punto sfrutterà i suoi nuovi privilegi e l'accesso per accedere all'unità C del controller di dominio. Eseguire il comando seguente nello stesso prompt dei comandi in cui i ticket sono stati appena importati:

    dir \\dc1\c$

Nella figura seguente è riportato un esempio del risultato di questo comando:

![dir 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig29.png) 

A questo punto l'autore dell'attacco è a tutti gli effetti *NuckC*. Solo gli amministratori devono poter accedere alla radice del controller di dominio.  L'autore dell'attacco usa credenziali legittime, può accedere a risorse legittime e avviare eseguibili legittimi. 

La maggior parte dei reparti IT non si accorgerebbe di questa attività di post-infiltrazione nel proprio ambiente.  Microsoft ATA può rilevare questa attività come illustrato nell'immagine seguente:

![Infiltrazione](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig30.png) 

Come si può notare, Microsoft ATA ha rilevato che i ticket di Nuck Chorris sono stati rubati da *ADMIN-PC* e spostati in *VICTIM-PC*.  ATA mostra anche quali sono le risorse a cui l'autore dell'attacco è riuscito ad accedere usando i ticket rubati.  Non solo si viene a conoscenza dell'attacco ma si ottengono anche informazioni su dove iniziare la ricerca. La figura seguente mostra anche che ATA è in grado di vedere a quali risorse il Pass-the-Ticket associato è riuscito ad accedere:

![Risorse](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig31.png) 

Queste informazioni sono estremamente importanti per difendere la rete. L'autore dell'attacco è riuscito ad accedere a CIFS tramite il comando "dir \\dc1\c$".  L'autore dell'attacco ha inviato una richiesta LDAP a DC1 locale ai fini di CIFS.  Il [KRBTGT](https://technet.microsoft.com/library/dn745899%28v=ws.11%29.aspx) è stato usato per comunicare direttamente con DC1 e autenticarsi (un processo necessario per l'accesso all'unità c$ del controller di dominio).  Da questo, come difensori, possiamo verificare che l'attività di Pass-the-Ticket ha consentito di accedere direttamente al computer DC1.

A questo punto la maggior parte dei malintenzionati tenterà di eseguire codice da remoto verso un controller di dominio. Ciò è fondamentale perché apportare modifiche al livello di identità stesso può rendere estremamente difficile il rilevamento della presenza. Per simulare ciò, eseguire comandi remoti per aggiungere un utente al dominio e aggiungerlo al gruppo di sicurezza *Administrators*, usando le credenziali legittime di NuckC.  È possibile fare tutto questo mediante gli strumenti integrati, senza bisogno di software dannoso o strumenti di ricerca.

Dal percorso in cui si trova PsExec in *Victim-PC*, eseguire i comandi seguenti:

    psexec \\dc1 -accepteula net user /add InsertedUser pa$$w0rd1
    psexec \\dc1 -accepteula net localgroup “Administrators” InsertedUser /add

Nella figura seguente è riportato un esempio del risultato di questo comando:

![psexec](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig32.png) 

L'autore dell'attacco ha appena creato un account utente come account *Administrator*. Sono stati usati chiaramente i privilegi *Doman Admin* che ora si possiedono, mediante l'esecuzione di codice da remoto.  Non solo, è possibile creare altri *Domain Admins* e rimuovere amministratori di dominio.  

Microsoft ATA ha rilevato l'esecuzione in modalità remota su DC1 da *Victim-PC*.  Nella schermata di esempio riportata di seguito, ATA sta rilevando i tentativi riusciti e non riusciti effettuati dal malintenzionato.

![Esecuzione remota](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig33.png) 

<a id="domain-dominance" class="xliff"></a>
### Dominanza del dominio

L'autore dell'attacco ha ottenuto il controllo del dominio e può eseguire qualsiasi codice, come amministratore, e accedere alle risorse del dominio.
 
Tuttavia, per mantenere il controllo del dominio, vengono attivate backdoor e altri meccanismi, come criteri assicurativi, nel caso venga scoperto il metodo di attacco originale o siano reimpostate le credenziali in modo casuale. A questo punto si presume che l'autore dell'attacco voglia creare un'efficace backdoor verso il controller di dominio, un modo per creare rapidamente utenti con previlegi *Admin*, metodo noto come Skeleton Key. 

Il passaggio successivo è sferrare l'attacco Skeleton Key a DC1. In primo luogo è necessario copiare *mimikatz* nel controller di dominio. Si noti che in questa fase è importante sapere se il controller di dominio è un computer a 32 bit o a 64 bit.  Nell'esempio usa un computer a 64 bit: modificarlo in base alle esigenze dell'ambiente specifico.

    xcopy x64\mimikatz.exe \\dc1\c$\temp\

Successivamente si userà *PsExec* per eseguirlo in modalità remota e distribuire lo Skeleton Key con il comando seguente:

    PsExec \\dc1 -accepteula cmd /c (cd c:\temp ^& mimikatz.exe “privilege::debug” “misc::skeleton” ^& “exit”)

Nella figura seguente è riportato un esempio del risultato di questo comando:

![PSExec2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig34.png) 

L'autore dell'attacco ha "corretto" il file binario LSASS.exe con la "patch" Skeleton Key.  A questo punto l'autore dell'attacco può sfruttare lo Skeleton Key. Per simulare questo, aprire un prompt dei comandi come *JeffV*.  Innanzitutto si controllerà che non ci sono ticket di altri utenti. Questa procedura ha il solo scopo di verificare esattamente ciò che accade. Da *Victim-PC* eseguire il comando seguente come *JeffV*:

    klist

Nella figura seguente è riportato un esempio del risultato di questo comando:

![klist nucko](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig35.png) 

Come illustrato nell'esempio precedente, non ci sono ticket con privilegi elevati.  Questo significa che tutti i comandi che l'autore dell'attacco eseguirà devono avere solo i privilegi di *JeffV*. Ora si tenterà di autenticarsi in DC1 provando a eseguire il mapping di C$ del DC1.  Si userà una password errata, di proposito, per illustrare che non tutte le password funzioneranno. Dalla stesso prompt dei comandi eseguire il comando seguente:

    net use k: \\dc1\c$ wrongpassword /user:Administrator@contoso.local

Nella figura seguente è riportato un esempio del risultato di questo comando:

![net use](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig36.png) 

Come illustrato nell'esempio, il comando non riesce, esattamente come ci si aspetta.  Qui è dove entra in gioco lo Skeleton Key. Si proverà a eseguire lo stesso comando di nuovo, ma ora con la chiave master che è appena stata aggiunta a tutti gli account autenticati su DC1, in cui è stato inserito lo Skeleton Key. Dal prompt dei comandi eseguire il comando seguente, ma questa volta con la chiave master "mimikatz":

    net use k: \\dc1\c$ mimikatz /user:Administrator@contoso.local

Nella figura seguente è riportato un esempio del risultato di questo comando:

![net use 2](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig37.png) 

Con la chiave master "mimikatz" (specificata nel codice), l'autore dell'attacco potrebbe ottenere privilegi di amministratore.  Tale chiave non è la password per l'account, un modo per raggiungere DC1, usando il processo con patch, e autenticare qualsiasi utente come amministratore (o qualsiasi altro gruppo di sicurezza). Si noti che ora sono presenti 2 password attive per ogni account:

- La password originale creata dall'utente o amministratore.
- La chiave master Skeleton Key  

Microsoft ATA sarà in grado di rilevare questa attività, come illustrato nell'esempio riportato di seguito:

![Skeleton Key](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig38.png) 

Finora tutto ciò che l'autore dell'attacco ha fatto sul controller di dominio ha richiesto l'esecuzione di codice arbitrario nel controller di dominio.  ATA ha rilevato queste azioni attivando la rispettiva notifica di un'attività sospetta nonché fornendo al difensore della rete le informazioni per rimediare. Tuttavia, l'autore dell'attacco potrebbe voler continuare la suo intrusione eseguendo un attacco più nascosto, che non coinvolga l'uso di codice nel controller di dominio (senza *PsExec* o inserendo lo Skeleton Key direttamente nel processo LSASS).
*Mimikatz*, lo strumento di ricerca preferito in quest'area, offre una funzionalità denominata "DC Sync".  Questa consente all'autore dell'attacco, con le credenziali di amministratore di dominio, di replicare le credenziali come se fosse un controller di dominio.

Aprire il prompt dei comandi che ha le credenziali di *NuckC*, passare al prompt dei comandi e assicurarsi che il ticket del NuckC sia ancora inserito nella sessione, come illustrato nell'esempio seguente:

![ticket](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig39.png) 

Ora che si ha la certezza di lavorare dalla console corretta, è possibile emulare l'autore dell'attacco e tentare di ottenere le credenziali più importanti del dominio: il [KRBTGT](https://technet.microsoft.com/library/dn745899.aspx#Sec_KRBTGT).  Il motivo per cui è necessario usare questo account è il fatto che con questo account è possibile firmare i propri ticket.

Dal prompt dei comandi *NuckC* ora convalidato in *Victim-PC* passare alla posizione in cui si trova mimikatz nel file system ed eseguire il comando seguente:

    mimikatz.exe “lsadump::dcsync /domain:contoso.local /user:krbtgt “exit” >> krbtgt-export.txt

Nella figura seguente è riportato un esempio del risultato di questo comando:

![lsadump](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig40.png) 

Una volta che l'autore dell'attacco aprirà "krbtgt-export.txt" conoscerà i dettagli di KRBTGT necessari.  Aprire il file "krbtgt export.txt" in cui si è appena esportato l'hash, come illustrato nell'esempio riportato di seguito:

![KRBTGT](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig41.png) 

Ora l'autore dell'attacco dispone di tutto ciò che serve per firmare qualsiasi TGT per qualsiasi risorsa usando l'hash NTLM rubato senza neppure tornare al controller di dominio.  In questo modo l'autore dell'attacco può diventare chiunque in qualsiasi momento (fino a quando l'account KRBTGT stesso non viene reimpostato due volte).

Microsoft ATA può identificare questo tipo di attacco, come illustrato nell'esempio riportato di seguito:

![Attacco](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig42.png) 

Microsoft ATA non solo ha rilevato l'attacco ma ha anche fornito le informazioni necessarie per intraprendere azioni correttive.

Sfruttare il KRBTGT per firmare ticket fittizi è noto come attacco Golden Ticket, anche questo rilevato da ATA.  Tuttavia, per questioni di ambito e rilevamento basato su firma, esula dagli argomenti di questa guida.

<a id="conclusion" class="xliff"></a>
## Conclusione

Microsoft ATA fornisce informazioni e approfondimenti per la difesa della rete che non sono disponibili altrove.  Microsoft ATA trasforma il piano di identità in un potente strumento di rilevamento che scopre le attività di post-infiltrazione nell'ambiente.  Microsoft ATA consente di raccogliere informazioni sui macroeventi e trasformarle rapidamente in un quadro che descrive in modo coerente un attacco in corso.

![Conclusione](./media/ata-attack-simulation-playbook/ata-attack-simulation-playbook-fig43.png) 

Microsoft ATA fornisce le informazioni e l'intelligence necessari nei casi in cui si presume che si sia verificata una violazione ed è indispensabile individuare le attività di post-infiltrazione.  Firewall, motori antivirus, servizi di rilevamento delle intrusioni e servizi di prevenzione delle intrusioni tentano tutti di tenere fuori il nemico, ma non riescono a vedere quasi nulla dopo che l'autore dell'attacco ha violato il sistema, quando strumenti legittimi e credenziali legittime vengono usati da utenti malintenzionati.  Nel mondo della sicurezza informatica è essenziale conoscere a fondo queste attività dannose. 

Per altre informazioni su Microsoft ATA, visitare la pagina [Microsoft ATA](https://www.microsoft.com/cloud-platform/advanced-threat-analytics) o inviare un messaggio di posta elettronica a ataeval@microsoft.com.




