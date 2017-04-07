---
title: Abilitare una soluzione con dispositivi condivisi con limitazioni d&quot;uso | Documentazione Microsoft
description: 
keywords: 
author: jeffgilb
manager: angrobe
ms.date: 3/24/2017
ms.topic: solution
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d78e2b94-8ad3-4703-b7f0-db070288a20b
ms.reviewer: vlpetros
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d4362764cad9264c513ca745c45b96590b18928f
ms.openlocfilehash: 98efafde6981fa8cb0c49c4b22729c64c8386754
ms.lasthandoff: 03/24/2017


---
# <a name="enable-a-limited-use-shared-device-solution-with-intune"></a>Abilitare una soluzione con dispositivi condivisi con limitazioni d'uso con Intune
In alcuni casi, i dipendenti hanno la necessità di condividere i dispositivi per accedere ad app e dati aziendali in modo da poter eseguire attività specifiche che richiedono impostazioni e app particolari. Si tratta di un'esigenza comune in negozi, fabbriche e nel settore dei trasporti. In altri casi, non sono i dipendenti ma i clienti ad avere l'esigenza di accedere in modo interattivo alle risorse usando dispositivi accessibili pubblicamente in luoghi come sale conferenze, hall di alberghi, scuole o biblioteche. A volte potrebbe essere sufficiente visualizzare una presentazione con esecuzione automatica o fornire informazioni statiche al pubblico.

L'esecuzione di un'app a schermo intero, senza altre opzioni, può essere utile per offrire un'esperienza utente sicura e interattiva, mantenendo comunque protetti gli asset aziendali da attività utente sospette. Questa opportunità consente al personale IT di offrire una maggiore sicurezza insieme a un'esperienza personalizzabile che consente ai dipendenti di restare produttivi e di soddisfare le esigenze dei clienti.

## <a name="how-can-enterprise-mobility--security-help-you"></a>Come può essere utile Enterprise Mobility + Security?
EMS consente di offrire funzionalità ed esperienze per realizzare un ambiente di lavoro produttivo e soddisfare le esigenze dei clienti, ovunque. Indipendentemente dal fatto che vengano usati dispositivi aziendali iOS, Mac OS, Android o Windows Mobile , Microsoft Intune può aiutare a fornire una soluzione di produttività ai dipendenti e informazioni ai clienti, garantendo al tempo stesso la sicurezza dei dati aziendali.

### <a name="recommended-solution"></a>Soluzione consigliata
Con Intune, è possibile usare le impostazioni dei criteri di configurazione della modalità tutto schermo per i dispositivi mobili Android o iOS e l'accesso assegnato per i telefoni Windows Mobile, per bloccare un dispositivo in modo che funzionino solo determinate app o funzionalità. I criteri di configurazione di Intune sono gruppi di impostazioni che controllano le funzionalità nei dispositivi mobili e nei computer. È possibile creare criteri usando modelli che contengono le impostazioni consigliate o personalizzate, quindi distribuire i criteri a gruppi di dispositivi o utenti. Ad esempio, è possibile distribuire i criteri di configurazione della modalità tutto schermo nei dispositivi per consentire l'esecuzione solo di un'app gestita specificata o per disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

### <a name="how-to-implement-this-solution"></a>Come implementare questa soluzione
La parte restante di questa soluzione è suddivisa nelle sezioni seguenti che illustrano come eseguire la configurazione:
- **Modalità tutto schermo per dispositivi iOS**. Questa sezione illustra come bloccare i dispositivi iOS con le impostazioni dei criteri di configurazione della modalità tutto schermo di Intune.
- **Modalità tutto schermo per Android**. Questa sezione illustra come bloccare i dispositivi Android con le impostazioni dei criteri di configurazione della modalità tutto schermo di Intune per i dispositivi Samsung KNOX.
- **Criteri di accesso assegnato per Windows**. Questa sezione descrive come usare il provider di servizi di configurazione (CSP) EnterpriseAssignedAccess per bloccare i dispositivi Windows 10 Mobile per offrire un'esperienza di accesso assegnato.

## <a name="kiosk-mode-for-ios"></a>Modalità schermo intero per iOS
Intune offre una gamma di impostazioni predefinite generali che è possibile configurare nei dispositivi iOS, incluse le impostazioni di configurazione della modalità tutto schermo che consentono di bloccare i dispositivi gestiti iOS.  

Prima di poter configurare un dispositivo iOS (8.0 e versioni successive) per la modalità tutto schermo, è necessario usare lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) in un dispositivo Mac oppure distribuire un profilo di registrazione per [registrare i dispositivi iOS acquistati tramite il programma DEP (Device Enrollment Program) di Apple](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) per attivare la modalità con supervisore nel dispositivo. Dopo questa operazione, è possibile distribuire le impostazioni di configurazione della modalità tutto schermo per controllare le impostazioni delle app e dei dispositivi tramite i criteri di configurazione di Intune.

Nella console di amministrazione di Intune passare semplicemente al nodo CRITERI, iOS, creare un nuovo criterio **Configurazione generale (iOS 8.0 e versione successiva)** e quindi definire le impostazioni della modalità tutto schermo. La più importante di queste impostazioni consente di definire l'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo.

![Impostazioni dei criteri della modalità tutto schermo per iOS](..\Solutions\media\limited-use-devices\kiosk-mode-policy.png)

È possibile specificare un'app gestita o un'app dall'App Store di Apple, ma nessun'altra app potrà essere eseguita nel dispositivo dopo l'applicazione dei criteri della modalità tutto schermo. Ricordarsi, inoltre, che dopo la distribuzione i criteri saranno attivi solo nei dispositivi iOS in modalità di supervisione.

> [!NOTE]
> Se l'app specificata viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

## <a name="kiosk-mode-for-android"></a>Modalità tutto schermo per Android
Il blocco dei dispositivi Android KNOX Standard (4.0 e versioni successive) viene eseguito in modo simile all'attivazione della modalità tutto schermo per i dispositivi iOS. Nella console di amministrazione di Intune passare semplicemente al nodo CRITERI, Android, creare un nuovo criterio **Configurazione generale (Android 4 e versioni successive, Samsung KNOX Standard 4.0 e versioni successive)** e quindi definire le impostazioni della modalità tutto schermo.

Sono disponibili meno impostazioni per la configurazione con i dispositivi Android KNOX, ma comunque la più importante è l'app gestita che potrà essere eseguita in modalità tutto schermo. Le app dello store non sono supportate per questi dispositivi e i criteri distribuiti verranno eseguiti su qualsiasi dispositivo Samsung KNOX che li riceve, inclusi i dispositivi personali BYOD se non si presta attenzione. Per questo motivo, è consigliabile distribuire solo le impostazioni della modalità tutto schermo per i dispositivi Android alla persona che gestisce la registrazione in blocco dei dispositivi di proprietà aziendale che devono essere gestiti come dispositivi per la modalità tutto schermo.

> [!NOTE]
> Se l'app specificata viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

## <a name="assigned-access-policies-for-windows"></a>Criteri di accesso assegnato per Windows
Anche i dispositivi Windows 10 Mobile (versione 1511 e versioni successive) possono essere configurati come dispositivi per la modalità tutto schermo, ma viene usato un criterio di configurazione di Windows personalizzato invece di un criterio di configurazione generale. Questi tipi di criteri consentono di sfruttare le [impostazioni URI OMA di Windows 10](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) per gestire le impostazioni di configurazione dei dispositivi con Intune.

> [!TIP]
> I [provider di servizi di configurazione (CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) espongono le impostazioni di configurazione dei dispositivi URI OMR in Windows 10.

Il provider [CSP EnterpriseAssignedAccess](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/enterpriseassignedaccess-csp) viene usato per bloccare i dispositivi Windows 10 per offrire un'esperienza di accesso assegnato. È anche possibile usare tale CSP per configurare altre impostazioni come lingua e temi o per configurare layout personalizzati in un dispositivo.

Per creare i criteri per i dispositivi Windows, è necessario passare al nodo CRITERI della console di amministrazione di Intune, poi a Windows e quindi creare un nuovo criterio **Configurazione personalizzata (Windows 10 Desktop e Mobile e versioni successive)**. Da qui, è necessario fornire le informazioni sul CSP e importare un file XML valido che definisce le impostazioni da applicare ai dispositivi Windows destinatari della distribuzione di questo criterio.  

![Impostazioni URI OMA](..\Solutions\media\limited-use-devices\settings.png)

Per creare un criterio di accesso assegnato semplice, fornire i metadati di base per nome e descrizione, impostare il tipo di dati su **Stringa (XML)** e immettere **./Vendor/MSFT/EnterpriseAssignedAccess/AssignedAccess/AssignedAccessXml** per il valore URI OMA *con distinzione tra maiuscole e minuscole*. Nel codice XML di esempio seguente il dispositivo verrà bloccato in modo che siano disponibili per l'uso nel dispositivo solo le applicazioni specificate in un elenco delle applicazioni consentite (Microsoft Edge in questo caso). Le app non identificate dai rispettivi [ID di prodotto per app Windows 10 Mobile](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/customize/mdm/enterpriseassignedaccess-csp#productid) nell'elenco delle applicazioni consentite rimangono installate nel dispositivo, ma sono nascoste e ne viene impedito l'avvio. Per immettere i dati XML necessari, è sufficiente importare un nuovo file XML contenente le informazioni di esempio seguenti oppure copiare e incollare tali informazioni come codice XML con formattazione a riga singola nell'area di testo **Valore**:


> [!IMPORTANT]
> Quando si incolla l'esempio XML formattato nella casella Valore, assicurarsi che tutto il codice XML sia formattato in una singola riga.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<HandheldLockdown version="1.0">
   <Default>
      <ActionCenter enabled="false" />
      <Apps>
         <!-- Microsoft Edge -->
         <Application productId="{395589FB-5884-4709-B9DF-F7D558663FFD}" autoRun="true">
            <PinToStart>
               <Size>Medium</Size>
               <Location>
                  <LocationX>0</LocationX>
                  <LocationY>0</LocationY>
               </Location>
            </PinToStart>
         </Application>
      </Apps>
      <Buttons>
         <ButtonLockdownList>
            <!-- Lockdown all buttons -->
            <Button name="Search">
               <ButtonEvent name="Press" />
               <ButtonEvent name="PressAndHold" />
            </Button>
            <Button name="Camera">
               <ButtonEvent name="Press" />
               <ButtonEvent name="PressAndHold" />
            </Button>
         </ButtonLockdownList>
         <ButtonRemapList />
      </Buttons>
      <MenuItems>
         <DisableMenuItems />
      </MenuItems>
      <Settings>
         <System name="Microsoft.WiFi" />
         <System name="Microsoft.About" />
         <System name="Microsoft.Feedback" />
         <System name="Microsoft.CompanyAccount" />
         <System name="Microsoft.VPN" />
      </Settings>
      <StartScreenSize>Small</StartScreenSize>
   </Default>
</HandheldLockdown>

```
Dopo aver creato il criterio, distribuirlo a un gruppo di dispositivi Windows che si vuole configurare per la modalità tutto schermo.

> [!IMPORTANT]
> Assicurarsi che il criterio di accesso assegnato venga distribuito al gruppo corretto. L'unico modo per annullare un criterio di accesso assegnato consiste nel ripristinare le impostazioni predefinite del dispositivo.

### <a name="learn-more"></a>Altre informazioni
[Iniziare a usare Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)

