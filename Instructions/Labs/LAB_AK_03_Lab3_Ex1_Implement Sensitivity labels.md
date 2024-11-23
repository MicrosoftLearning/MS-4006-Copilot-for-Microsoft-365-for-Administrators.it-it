# Percorso di apprendimento 3 - Lab 3 - Esercizio 1: Implementare le etichette di riservatezza con Microsoft Entra ID Protection

Nel ruolo di Holly Dickson, il nuovo amministratore di Microsoft 365 di Adatum, è stato distribuito Microsoft 365 in un ambiente lab virtualizzato. Proseguendo con il progetto pilota di Microsoft 365, i passaggi successivi prevedono l'implementazione delle etichette di riservatezza con Microsoft Entra ID Protection in Adatum. In questo lab verrà creata e pubblicata un'etichetta e si effettuerà il test di un'etichetta pubblicata. È bene precisare che non verrà testata l'etichetta creata in questo lab. Verrà invece testata un'etichetta differente.

**Importante:** quando si pubblica una nuova etichetta di riservatezza e i relativi criteri, sono necessarie fino a 24 ore per la propagazione in Microsoft 365. Di conseguenza, non sarà possibile testare l'etichetta creata in questo lab. Verrà invece testata un'etichetta di riservatezza preesistente denominata **Progetto - Falcon**. Questa etichetta preesistente è quasi identica all'etichetta che verrà creata, quindi in pratica sarà possibile visualizzare gli stessi risultati ottenibili dal test dell'etichetta appena creata nel lab. 


### Attività 1: installare il client di etichettatura unificata di Microsoft Entra ID Protection

Per implementare le etichette di riservatezza come parte del progetto pilota in Adatum, è necessario prima installare il client Microsoft Entra ID Protection dall'Area download Microsoft.

**Nota:** anche se il rebranding di Azure AD in Microsoft Entra ID è ancora in corso, il client Azure Information Protection non è stato rinominato alla data di questo articolo. Verrrà in seguito rinominato in client Microsoft Entra ID Protection.

1. La connessione a LON-CL1 dovrebbe essere ancora attiva con l'account locale **adatum\administrator**, mentre nel browser Edge la connessione a Microsoft 365 dovrebbe essere ancora a nome di **Holly Dickson**. 

2. In **Microsoft Edge**, aprire una nuova scheda e immettere (oppure copiare e incollare) il seguente URL nella barra degli indirizzi: **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

    Verrà avviato il download per il **client Microsoft Purview Information Protection**.

3. Nella finestra **Download** mostrata in alto a destra della pagina verrà visualizzato il file **PurviewInfoProtection.exe** in fase di download. Al termine del download del file, selezionare il collegamento **Apri file** visualizzato sotto il nome del file.

4. Verrà aperta la procedura guidata di **Microsoft Azure Information Protection**. Se la procedura guidata non viene aperta sul desktop, selezionare la relativa icona dalla barra delle applicazioni per visualizzarla.

5. Durante la procedura guidata, nella finestra **Installa il **client Microsoft Purview Information Protection****, che viene visualizzata, selezionare la casella di controllo **Confermo che venga disinstallato il componento aggiuntivo AIP per Office (obbligatorio)** e deselezionare la casella di controllo **Contribuire a migliorare Microsoft Purview Information Protection inviando statistiche di utilizzo a Microsoft**. Selezionare quindi il pulsante **Accetto**.

6. Al termine dell'installazione, fare clic su **Chiudi**.

Il client Azure per l'etichettatura unificata di Azure Information Protection è stato installato correttamente nella macchina virtuale LON-CL1.

### Attività 2: abilitare le etichette di riservatezza per i file in SharePoint e OneDrive

In questo esercizio verranno abilitate le etichette di riservatezza per i file di Office e i file PDF supportati in SharePoint e OneDrive. Quando questa funzionalità è abilitata, gli utenti visualizzano il pulsante **Riservatezza** sulla barra multifunzione per consentire l'applicazione delle etichette. La barra di stato visualizza anche tutti i nomi di etichetta applicati. Per SharePoint, gli utenti possono inoltre visualizzare e applicare le etichette di riservatezza dal riquadro dei dettagli.

L'abilitazione di questa funzionalità offre a SharePoint e OneDrive la possibilità di elaborare il contenuto dei file di Office e, facoltativamente, i documenti PDF crittografati usando un'etichetta di riservatezza. L'etichetta può essere applicata in Office per il Web o nelle app desktop di Office e caricata o salvata in SharePoint e OneDrive Finché non si abilita la funzionalità, questi servizi non possono elaborare i file crittografati, il che significa che la creazione condivisa, eDiscovery, la prevenzione della perdita dei dati, la ricerca e altre funzionalità di collaborazione non saranno attive per questi file.

Prima di tutto verranno abilitate le etichette di riservatezza per i file online di Office archiviati in SharePoint e OneDrive. In seguito verrà abilitato il supporto per i file PDF.

**Nota:** come per tutte le modifiche di configurazione a livello di tenant per SharePoint e OneDrive, l'applicazione della modifica potrebbe richiedere circa 15 minuti.

1. In LON-CL1, nel browser Edge dovrebbe essere ancora attiva la connessione a Microsoft 365 come **Holly Dickson**.

2. Nel browser Edge dovrebbe essere aperta una scheda per l'**interfaccia di amministrazione di Microsoft 365**. In caso contrario, aprire una nuova scheda e immettere l'URL seguente: **https://admin.microsoft.com**.

3. Nell'**interfaccia di amministrazione di Microsoft 365**, se necessario, selezionare **... Mostra tutto**. Selezionare **Conformità** nel gruppo **Interfacce di amministrazione**. Il portale di Microsoft Purview viene aperto in una nuova scheda.

4. Per iniziare, abilitare le etichette di riservatezza per i file online di Office archiviati in SharePoint e OneDrive. <br/>

    Nel portale di **Microsoft Purview**, nella sezione **Soluzioni** del riquadro di spostamento, selezionare **Protezione delle informazioni** e quindi selezionare **Etichette**.

5. Nella pagina **Etichette** verrà visualizzato il messaggio seguente al centro della pagina: **L'organizzazione non ha attivato la possibilità di elaborare il contenuto nei file online di Office con le etichette di riservatezza crittografate applicate e archiviate in OneDrive e SharePoint. È possibile l'attivazione da qui, ma tenere presente che è necessaria una configurazione aggiuntiva per gli ambienti Multi-Geo.** <br/>

    Sotto questo messaggio è riportato il pulsante **Attiva ora**. Selezionare il pulsante.  <br/>

    **Nota:** il comando viene eseguito immediatamente e al successivo aggiornamento della pagina, il messaggio o il pulsante non saranno più visibili.

6. A questo punto verrà abilitata la protezione PDF per i file in SharePoint e OneDrive. <br/>

    Nel portale di **Microsoft Purview**, in **Protezione delle informazioni** nel riquadro di spostamento, selezionare **Etichettatura automatica**.

7. Nella pagina **Etichettatura automatica** viene visualizzato il banner **Proteggi PDF con etichettatura automatica** al centro della pagina. Selezionare l'intestazione **Proteggi PDF con etichettatura automatica** per attivare la protezione PDF per i file in SharePoint e OneDrive. 

8. Nella finestra di dialogo **Etichettatura automatica** visualizzata, selezionare **Conferma** per confermare l'attivazione della protezione PDF per i file in SharePoint e OneDrive. 

    **Nota:** il comando viene eseguito immediatamente e al successivo aggiornamento della pagina, il banner **Proteggi PDF con etichettatura automatica** non sarà più visibile.

9. Lasciare aperto il browser Edge insieme a tutte le schede. 

### Attività 3: creare un'etichetta di riservatezza

In questo esercizio verrà creata un'etichetta di riservatezza che verrà aggiunta ai criteri predefiniti, in modo che sia valida per tutti gli utenti del tenant Adatum.

1. In LON-CL1, nel browser Edge dovrebbe essere ancora attiva la connessione a Microsoft 365 come **Holly Dickson**.

2. Nel browser Edge dovrebbe essere aperta una scheda per l'**interfaccia di amministrazione di Microsoft 365**. In caso contrario, aprire una nuova scheda e immettere l'URL seguente: **https://admin.microsoft.com**.

3. Nell'**interfaccia di amministrazione di Microsoft 365** selezionare, se necessario, **... Mostra tutte** nel riquadro di spostamento. Selezionare **Conformità** nel gruppo **Interfacce di amministrazione**.

4. Nel portale di conformità di **Microsoft Purview** selezionare **Protezione delle informazioni** nel riquadro di spostamento e quindi selezionare **Etichette**. 

5. Nella pagina **Etichette** verrà visualizzato un messaggio di avviso in una casella ombreggiata in giallo chiaro al centro della pagina che indica: **L'organizzazione non ha attivato la possibilità di elaborare il contenuto nei file online di Office con le etichette di riservatezza crittografate applicate e archiviate in OneDrive e SharePoint. È possibile l'attivazione da qui, ma tenere presente che è necessaria una configurazione aggiuntiva per gli ambienti Multi-Geo.** <br/>

    Selezionare il pulsante **Attiva ora** visualizzato sul lato destro di questo messaggio. Ciò consentirà ad Adatum di applicare le etichette di riservatezza all'interno dell'ambiente Microsoft 365. <br/>

    Notare che ora il messaggio è stato modificato: **È ora possibile creare le etichette di riservatezza con le impostazioni di privacy e controllo di accesso per Teams, i siti di SharePoint e i Gruppi di Microsoft 365.** 

6. Nella pagina **Etichette** selezionare l'opzione **+Crea un'etichetta** visualizzata nella barra dei menu al centro della schermata, sotto al messaggio precedente. Verrà avviata la procedura guidata **Nuova etichetta di riservatezza**.

7. Nella procedura guidata **Nuova etichetta di riservatezza**, immettere le informazioni seguenti nella pagina **Specificare i dettagli di base per questa etichetta**:

    - Nome: **informazioni personali**
    
    - Nome visualizzato: **informazioni personali**

    - Descrizione per gli utenti: **documenti, file e messaggi e-mail con informazioni personali**

    - Descrizione per gli amministratori: **documenti, file e messaggi e-mail con informazioni personali**

    - Colore etichetta: selezionare uno dei colori che si desidera assegnare alle etichette di riservatezza

8. Selezionare **Avanti**.

9. Nella pagina **Definisci l'ambito per questa etichetta** verificare che la casella di controllo **Elementi** sia selezionata (se necessario, selezionarla ora) e quindi scegliere **Avanti**.

10. Nella pagina **Scegli le impostazioni di protezione per gli elementi etichettati**, selezionare entrambe le caselle di controllo **Applica o rimuovi crittografia** e **Applica contrassegno del contenuto**, quindi selezionare **Avanti**.

11. Nella pagina **Crittografia** verrà definito chi può accedere agli elementi a cui è applicata questa etichetta. Selezionare l'opzione **Rimuovi crittografia se il file o il messaggio e-mail, oppure l'evento del calendario è crittografato**, quindi selezionare **Avanti**.

12. Nella pagina **Contrassegno del contenuto** impostare l'interruttore **Contrassegno del contenuto** su **On**. Vengono quindi visualizzate tre opzioni che consentono di personalizzare la modalità di contrassegno di file e messaggi e-mail. <br/>

    Selezionare tutte e tre le caselle di controllo. In ogni impostazione selezionare **Personalizza testo**. Verrà aperto un riquadro per personalizzare la specifica impostazione. Immettere le informazioni seguenti nel riquadro **Personalizza** per ogni opzione (selezionare **Salva** dopo aver completato le impostazioni per ogni opzione): <br/>

    - **Aggiungere una filigrana** 
        - Testo della filigrana: **Sensibile - Non condividere** (Suggerimento: dopo aver immesso questo valore, copiarlo (CTRL+C) in modo da poterlo incollare (CTRL+V) nelle altre due impostazioni di testo)
        - Dimensioni del carattere: **25**
        - Colore carattere: **blu**
        - Layout del testo: **diagonale**
            
    - **Aggiungi intestazione** 
        - Testo intestazione: **Sensibile - Non condividere**
        - Dimensioni del carattere: **25**
        - Colore carattere: **rosso**
        - Allinea testo: **centrato**
            
    - **Aggiungi un piè di pagina**
        - Testo del piè di pagina: **Sensibile - Non condividere**
        - Dimensioni del carattere: **25**
        - Colore carattere: **rosso**
        - Allinea testo: **centrato**

13. Nella pagina **Contrassegno del contenuto** selezionare **Avanti**. 

14. Nella pagina **Etichettatura automatica per file e messaggi e-mail** impostare su **Sì** l'interruttore **Etichettatura automatica per file e messaggi e-mail**. Ciò consente una serie di opzioni che verranno aggiornate nei passaggi successivi.

15. In **Rileva contenuto corrispondente a queste condizioni**, selezionare **+Aggiungi condizione** e quindi selezionare **Contenuto incluso**.

16. Nella finestra **Contenuto incluso**, selezionare la freccia a discesa **Aggiungi** e quindi selezionare **Tipi di informazioni sensibili**.

17. Nella finestra **Tipi di informazioni sensibili** passare il mouse a sinistra dell'intestazione di colonna **Nome**. Selezionare la casella di controllo visualizzata, che consente di selezionare automaticamente tutti i tipi di informazioni sensibili. Selezionare **Aggiungi** per aggiungere tutti questi tipi di informazioni sensibili alla propria etichetta.

18. Nella pagina **Etichettatura automatica per file e messaggi e-mail** verranno visualizzati tutti i tipi di informazioni sensibili selezionati. Scorrere fino alla fine della finestra e aggiornare le impostazioni seguenti:

    - Quando il contenuto corrisponde a queste condizioni: selezionare **Applica automaticamente l'etichetta**

    - Visualizzare questo messaggio agli utenti quando viene applicata l'etichetta: immettere **È stato rilevato contenuto sensibile che verrà crittografato**.
        
19. Selezionare **Avanti**.

20. Nella pagina **Definire le impostazioni di protezione per gruppi e siti** lasciare vuote entrambe le caselle di controllo e selezionare **Avanti**.

21. Nella pagina **Etichettatura automatica per gli asset di dati schematizzati (anteprima)** non abilitare l'etichettatura automatica per gli asset di dati schematizzati (anteprima). Selezionare **Avanti**. 

22. Nella pagina **Esaminare le impostazioni e completare**, rivedere le informazioni immesse. Se è necessario correggere alcune impostazioni, selezionare l'opzione **Modifica** corrispondente e apportare le modifiche necessarie. Quando tutte le informazioni risultano corrette, selezionare **Crea etichetta**.

23. Verrà visualizzata la finestra di dialogo **Errore client** che indica che il BLOB di regole generato per l'etichetta che si sta tentando di creare è troppo lungo. La dimensione massima delle selezioni dei tipi di informazioni sensibili che è possibile effettuare contemporaneamente per ogni regola è **49152**. La selezione di tutti i tipi di informazioni sensibili, come avvenuto nei passaggi precedenti nella finestra **Tipi di informazioni sensibili**, ha causato il superamento di questo limite. <br/>

    **NOTA: è stato richiesto appositamente di selezionare tutti i tipi di informazioni sensibili per consentire di ricevere questo errore.** Abbiamo intenzionalmente creato le condizioni per questo errore in modo da mettere l'utente nelle condizioni di comprendere il perché è stato ricevuto e come correggerlo nel caso si verifichi negli ambienti di produzione.  <br/>

    Per risolvere il problema, selezionare **OK** nella finestra di dialogo **Errore client**, quindi nella pagina **Esaminare le impostazioni e completare**, scorrere verso il basso fino alla sezione **Etichettatura automatica per file e messaggi e-mail** e infine selezionare **Modifica**.
    
24. In questo modo si ritorna alla pagina **Scegliere le impostazioni di protezione per gli elementi etichettati** della procedura guidata. Selezionare **Avanti** in questa pagina, nuovamente **Avanti** nella pagina **Crittografia** e infine selezionare **Avanti** nella pagina **Contrassegno del contenuto**. In questo modo si torna alla pagina **Etichettatura automatica per file e messaggi e-mail**. 

25. Nella pagina **Etichettatura automatica per file e messaggi e-mail**, a destra della condizione **Contenuto incluso**, selezionare l'**icona del Cestino**. In questo modo verrà rimossa la condizione esistente **Contenuto incluso**per l'etichetta **informazioni personali** creata. <br/>

    Nei passaggi rimanenti verrà aggiunta una nuova condizione contenente solo due tipi di informazioni sensibili, anziché tutti i tipi come effettuato precedentemente.

26. Nella pagina **Etichettatura automatica per file e messaggi e-mail**, in **Rileva contenuto corrispondente a queste condizioni** selezionare **+Aggiungi condizione** e quindi selezionare **Contenuto incluso**.

27. Nella finestra **Contenuto incluso**, selezionare la freccia a discesa **Aggiungi** e quindi selezionare **Tipi di informazioni sensibili**.

28. Nella finestra **Tipi di informazioni sensibili**, nell'elenco dei tipi di informazioni sensibili, selezionare solo il **numero di registrazione ABA** e le caselle di controllo relative al **codice fiscale statunitense (SSN)** e quindi selezionare **Aggiungi**. Tornando alla pagina **Etichettatura automatica per file e messaggi e-mail**, si potranno ora visualizzare entrambi i tipi di informazioni sensibili. Selezionare **Avanti**.

29. Nella pagina **Definire le impostazioni di protezione per gruppi e siti**, lasciare vuote le due caselle di controllo e selezionare **Avanti**.

30. Nella pagina **Etichettatura automatica per gli asset di dati schematizzati (anteprima)** non abilitare l'etichettatura automatica per le colonne del database. Selezionare **Avanti**.

31. Nella pagina **Esaminare le impostazioni e completare**, selezionare **Crea etichetta**.

32. Nella pagina **L'etichetta di riservatezza è stata creata** selezionare l'opzione **Non creare ancora un criterio** e quindi selezionare **Fine**. Questo consente di ritornare alla pagina **Etichette**.

33. È ora possibile pubblicare l'etichetta **PII**. Nella pagina **Etichette**, se l'etichetta **PII** non viene visualizzata nel relativo elenco, selezionare **Aggiorna** sulla barra dei menu. Quando viene visualizzata l'etichetta **PII**, selezionare la casella di controllo visualizzata a sinistra. 

34. Selezionare l'opzione **Pubblica etichetta** visualizzata nella barra dei menu sopra l'elenco delle etichette. Verrà avviata una procedura guidata **Crea criterio** .

35. Nella procedura guidata **Crea criterio**, nella pagina **Scegliere le etichette di riservatezza da pubblicare**, l'etichetta **PII** è già elencata, quindi selezionare **Avanti**. 

36. Nella pagina **Assegnare le unità di amministrazione** di amministrazione, selezionare **Avanti** poiché il criterio PII verrà assegnato all'intera directory di Adatum invece che a un gruppo specifico di unità di amministrazione.

37. Nella pagina **Pubblica per utenti e gruppi** è possibile scegliere se rendere i criteri disponibili per tutti gli utenti e i gruppi oppure limitare i criteri a utenti e gruppi selezionati. Per questo lab si vogliono rendere disponibili a tutti i criteri. L'opzione **Utenti e gruppi** è già selezionata per impostazione predefinita (in caso contrario, selezionarla ora). In questo modo i criteri saranno disponibili per tutti gli utenti e i gruppi. Selezionare **Avanti**.  <br/>

    **Nota:** quando si esegue questa operazione nella distribuzione reale, se si desidera limitare i criteri a un numero selezionato di utenti o gruppi, selezionare **Modifica** ed effettuare tali selezioni. 

38. Nella pagina **Impostazioni criteri** selezionare la casella di controllo **Gli utenti devono fornire una giustificazione per rimuovere un'etichetta o ridurne la classificazione**, quindi selezionare **Avanti**. 

39. Nella pagina **Applicare un'etichetta predefinita ai documenti** selezionare **PII** nel menu a discesa visualizzato, quindi selezionare **Avanti**.

40. Nella pagina **Applicare un'etichetta predefinita ai messaggi di posta elettronica** selezionare **PII** nel menu a discesa visualizzato, quindi selezionare **Avanti**.

41. Nella pagina **Applicare un'etichetta predefinita alle riunioni e agli eventi del calendario**, selezionare **PII** nel menu a discesa visualizzato, quindi selezionare **Avanti**.

42. Nella pagina **Applicare un'etichetta predefinita al contenuto di Power BI** selezionare **PII** nel menu a discesa visualizzato, quindi selezionare **Avanti**.

43. Nella pagina **Assegnare un nome ai criteri** immettere i **Criteri PII** nel campo **Nome**, quindi immettere (o copiare e incollare) la descrizione seguente per questo criterio di etichetta di riservatezza: **lo scopo di questo criterio è rilevare informazioni riservate, ad esempio numeri di registrazione della banca ABA e codici fiscali statunitensi nei messaggi di posta elettronica e nei documenti, e crittografare queste informazioni quando vengono individuate. L'utente deve fornire una spiegazione per la rimozione dell'etichetta di classificazione.** Selezionare **Avanti**.

44. Nella pagina **Verifica e completamento**, rivedere le informazioni immesse. Se è necessario correggere qualcosa, selezionare l'opzione **Modifica** corrispondente e apportare le correzioni necessarie. Quando tutte le informazioni sono corrette, selezionare **Invia**.

45. Nella pagina **Il nuovo criterio è stato creato** selezionare **Fine**.


### Attività 4. Assegnare un'etichetta di riservatezza preesistente a un documento

Come descritto nelle istruzioni all'inizio di questo lab, non è possibile testare immediatamente l'etichetta di riservatezza e i criteri dell'etichetta creati nell'attività precedente. Ciò è dovuto al fatto che sono necessarie 24 ore per la propagazione di un nuovo criterio di etichetta in Microsoft 365 e perché l'etichetta diventi visibile in applicazioni come Microsoft Word e Outlook.

Si procederà invece a verificare una delle etichette di riservatezza preesistenti di Microsoft 365. Per questo lab si userà l'etichetta di riservatezza **Progetto - Falcon**, corrispondente a un livello estremamente riservato. Questa etichetta è simile all'etichetta creata nell'attività precedente, con l'unica eccezione che non include un'intestazione o un piè di pagina. L'uso di questa etichetta preesistente offrirà una buona idea del funzionamento dell'etichetta creata in Adatum.

1. In LON-CL1, nel browser Edge dovrebbe essere ancora attiva la connessione a Microsoft 365 come **Holly Dickson**.

2. Si esaminerà prima di tutto l'etichetta di riservatezza **Progetto-Falcon** che verrà applicata a un documento in questa attività.  Nel browser Edge dovrebbe essere ancora aperta dall'attività precedente una scheda per il portale di **Microsoft Purview**. Nel portale di **Microsoft Purview**, nel gruppo **Protezione delle informazioni**, nel riquadro di spostamento, selezionare **Etichette**. 

3. Nell'elenco delle etichette della pagina **Etichette** selezionare la freccia destra (**>**) accanto a **Estremamente riservato** per visualizzare le etichette secondarie di questa etichetta. In questo modo viene visualizzata l'etichetta **Progetto - Falcon** preesistente.

4. Selezionare l'etichetta **Progetto - Falcon** (non la casella di controllo; selezionare il nome dell'etichetta). In questo modo si apre il riquadro dei dettagli del **Progetto - Falcon** . Esaminare le informazioni definite per questa etichetta, quindi chiudere il riquadro al termine.  

5. L'etichetta di riservatezza **Progetto-Falcon** verrà assegnata ora a un documento. Selezionare la scheda **Home | Microsoft 365** nel browser per tornare alla home page di Microsoft 365. Nel lato sinistro della schermata, selezionare l'icona **App**. Nella pagina **App** visualizzata, fare clic con il pulsante destro del mouse sul riquadro di **Word** e selezionare **Apri in una nuova scheda**. 

6. Nella scheda **Word | Microsoft 365**, nella sezione **Crea nuovo** nella parte superiore della pagina selezionare **Documento vuoto**.

7. Se viene visualizzata la finestra **Opzione Privacy**, selezionare **Chiudi**.

8. Se la barra multifunzione di Word visualizza icone per ogni funzionalità ma non suddivide le icone per gruppo, selezionare la freccia rivolta verso il basso all'estrema destra della barra multifunzione, quindi in **Layout barra multifunzione** selezionare **Barra multifunzione classica**. In questo modo la barra multifunzione passerà allo stile tradizionale, suddiviso per gruppi di funzionalità (ad esempio Annulla, Appunti, Carattere, Paragrafo, Stili e altro ancora).

9. Nel documento di **Word** digitare il testo seguente: **Test di un'etichetta di riservatezza su un documento con informazioni personali (PII), in questo caso un codice fiscale statunitense: 111-11-1111.**

10. Poiché all'inizio di questo esercizio sono state abilitate le etichette di riservatezza, **Word** dovrebbe visualizzare il gruppo **Riservatezza** sulla barra multifunzione nella parte superiore della pagina. Selezionare la freccia giù nel gruppo **Riservatezza**. Nel menu a discesa corrispondente dovrebbe essere visualizzato l'elenco dei tipi di etichetta di riservatezza. Selezionare **Estremamente riservato**, quindi nel sottomenu visualizzato selezionare **Progetto - Falcon**. <br/>

    **Nota:** dopo 24 ore, l'etichetta creata nell'attività precedente verrà visualizzata nel sottomenu Estremamente riservato, accanto all'etichetta Progetto-Falcon. Tuttavia, per il momento la posizione dell'etichetta **Progetto - Falcon** sarà invariata.

11. Nel documento si noti come l'etichetta ha applicato una filigrana **RISERVATO - ProgettoFalcon** nella parte superiore del documento. L'etichetta Progetto - Falcon è stata configurata esattamente come l'etichetta creata, in cui la filigrana doveva essere visualizzata diagonalmente nella parte centrale della pagina. Quindi perché appare verso la parte superiore della pagina? La risposta è che si sta usando **Word per il Web**, che per impostazione predefinita lo visualizza come illustrato qui. Per vedere come apparirà a un utente che legge il documento, è necessario visualizzare il documento in **Visualizzazione di lettura**, operazione che verrà eseguita ora. <br/>

    Selezionare la scheda **Visualizza** e quindi nella barra multifunzione di Word selezionare **Visualizzazione di lettura**. Si noti che la filigrana viene visualizzata diagonalmente al centro del documento. Questo è il modo in cui la filigrana apparirà a qualcuno che legge il documento. Si noti che se si usa l'app desktop di Word, questa mostra la filigrana nel modo designato dall'etichetta, che in questo caso corrisponde a quello che si vede in questa Visualizzazione di lettura. <br/>

    Per uscire dalla Visualizzazione di lettura, selezionare **Modifica documento** nella barra dei menu nella parte superiore della pagina. Nel menu a discesa visualizzato, selezionare **Modifica**.

12. In questo primo test di convalida si rimuoverà l'etichetta di riservatezza applicata a questo documento. Una delle opzioni dei criteri di etichetta richiede agli utenti di fornire una giustificazione per rimuovere un'etichetta o per selezionare un'etichetta di classificazione inferiore. A questo punto si verificherà se questa impostazione funziona correttamente. <br/>

    Nel gruppo **Riservatezza** della barra multifunzione di Word selezionare la freccia giù. Si noti che nel menu a discesa visualizzato, accanto a **Altamente riservato**, viene visualizzato un segno di spunta. Tenere il mouse su **Altamente riservato** per visualizzare il sottomenu. Si noti che accanto a **Progetto - Falcon** viene visualizzato un segno di spunta. I segni di spunta indicano che l'etichetta corrente è applicata al documento.  <br/>
 
    Per rimuovere l'etichetta da questo documento, selezionare l'etichetta **Project - Falcon** visualizzata in questo menu a discesa.
    
13. Nella finestra **Giustificazione obbligatoria** visualizzata, selezionare l'opzione **Altro (spiega)**. Nel campo **Spiega perché stai modificando questa etichetta** immettere **Verificare cosa accade quando un'etichetta viene rimossa da un documento** e quindi selezionare **Cambia**.

14. Si noti che la filigrana nel documento è scomparsa. Nel gruppo **Riservatezza** della barra multifunzione di Word selezionare la freccia giù. Si noti che, nel menu a discesa visualizzato, mentre si visualizza **Altamente riservato** > **Progetto - Falcon**, non compaiono segni di spunta accanto a essi. Ciò indica che l'etichetta di riservatezza non è più applicata a questo documento.  

15. Per applicare di nuovo l'etichetta di riservatezza al documento, selezionare **Altamente riservato** > **Progetto - Falcon** nel menu a discesa. Si noti che la filigrana viene nuovamente visualizzata nel documento.

16. Il documento verrà ora salvato in modo che sia possibile condividerlo nell'attività successiva. Nell'angolo superiore sinistro della pagina, a destra dell'icona di Word, viene visualizzato un campo del nome del documento che contiene una freccia a discesa (Word può visualizzare **Document** o **Document1** come nome file temporaneo). Selezionare la freccia a discesa. Nel menu a discesa visualizzato verificare che il **Percorso** del file indichi **Holly Dickson > Documenti**. <br/>

    Nel campo **Nome file** rinominare il file in **ProtectedDocument1** e quindi selezionare al di fuori di questo menu del nome file (selezionare all'interno del documento). Si noti che il nuovo nome assegnato al file viene visualizzato nella barra del titolo. 

17. Lasciare aperta la scheda **ProtectedDocument1** che visualizza il documento. Si tornerà a questo documento nell'attività successiva per condividere il documento con Joni Sherman.

È stato appena creato correttamente un documento Word contenente l'etichetta Altamente riservato intitolata **Progetto - Falcon**. 


### Attività 5: proteggere un documento con Microsoft Purview Information Protection

Nell'attività precedente è stato creato un documento di Word ed è stato protetto con l'etichetta di riservatezza **Progetto - Falcon**. Questa etichetta ha inserito una filigrana nel documento. In questa attività si condividerà il documento creato con Joni Sherman e si limiterà a Joni l'autorizzazione "Solo visualizzazione". In questo modo sarà possibile vedere in che modo Microsoft Purview Information Protection protegge il documento in base ai parametri configurati.

Per verificare se la protezione assegnata al documento funziona, prima di tutto inviare tramite e-mail il documento a due persone, ossia a Joni Sherman e al proprio indirizzo e-mail personale. Quindi si verifica che Joni possa solo visualizzare il documento e non modificarlo, in più si verifica che non si possa accedere al documento dato che non è stato condiviso con l'utente corrente. Infine, si modificherà l'autorizzazione per il documento in modo che Joni possa modificarlo e le si invierà un'e-mail con questo documento aggiornato per il test. Lo scopo delle due e-mail a Joni, una con un link al documento che fornisce l'accesso di sola lettura e un'altra con un link al documento che fornisce la possibiltà di modificare il documento, è vedere in che modo Microsoft Entra ID Protection può fornire vari livelli di protezione dei documenti. 

1. In LON-CL1, nel browser Edge, si dovrebbe essere ancora connessi a Microsoft 365 come **Holly Dickson** dall'attività precedente, con la scheda **Word** aperta.

2. Nel browser Edge, selezionare la scheda **App | Microsoft 365** 

3. Nella pagina **App**, fare clic con il pulsante destro del mouse sul riquadro di **Outlook** e selezionare **Apri in una nuova scheda**. Verrà aperta la cassetta postale di Holly in Outlook sul Web in una nuova scheda del browser. 

4. In **Outlook sul Web**, selezionare **Nuovo messaggio** nella parte superiore della schermata.

5. Nel modulo relativo al messaggio e-mail, immettere le informazioni seguenti:

    - A: immettere **Joni** e quindi selezionare **Joni Sherman** dall'elenco utenti. 

    - CC: immettere il proprio indirizzo e-mail personale (NON quello di Holly, ma il proprio indirizzo e-mail personale), quindi selezionare il messaggio **Usa questo indirizzo: <your email address>** che comparirà

    - Aggiungere un oggetto: **Test documento protetto: autorizzazione di sola visualizzazione**

    - Corpo del messaggio: immettere **Apri il documento protetto allegato a questo messaggio di posta elettronica e provare a modificarlo.**

6. Nel corpo del messaggio, sotto il testo aggiunto nel passaggio precedente, verrà inserito un collegamento al documento creato nell'attività precedente. Tuttavia, per procedere, è necessario prima condividere il documento con Joni Sherman; in tal caso, verranno applicate autorizzazioni di **Sola visualizzazione**. Per procedere, è necessario uscire da questo messaggio di posta elettronica, tornare al documento e condividerlo con Joni. Dopo aver copiato il collegamento generato durante il processo di condivisione, è necessario tornare al messaggio di posta elettronica e incollare il collegamento. <br/>

    Nel browser Edge, selezionare la scheda **ProtectedDocument1**, che dovrebbe visualizzare ancora il documento creato nell'attività precedente. Nella parte superiore destra della pagina, sotto il nome e le iniziali di Holly Dickson, selezionare il pulsante **Condividi**. Nel menu a discesa visualizzato, selezionare **Condividi**.

7. Nella finestra visualizzata **Condividi "ProtectedDocument1"**, selezionare l'icona a forma di ingranaggio **Impostazioni collegamenti**) che si trova accanto al pulsante **Copia collegamento**. 

8. Nella finestra **Impostazioni collegamento** visualizzata selezionare l'opzione **Persone scelte**.
    
9. In **Altre impostazioni** l'opzione attuale è **Può modificare**. Si prevede condividere questo documento con Joni Sherman, garantendole solo le autorizzazioni di visualizzazione. Per apportare questa modifica alle autorizzazioni, selezionare **Può modificare**. Nel menu visualizzato, esaminare le opzioni disponibili. Si possibile notare che accanto a **Può modificare** è presente un segno di spunta, a indicare che questa è l’impostazione attuale. Per limitare Joni alle sole autorizzazioni di visualizzazione, selezionare **Può visualizzare** e quindi **Applica**.

10. Verrà visualizzata la finestra **Condividi "ProtectedDocument1"**. Immettere **Joni** nel campo **Aggiungi un nome, gruppo o indirizzo di posta elettronica**. Verrà visualizzato un elenco di utenti il cui nome inizia con **Joni**. Selezionare **Joni Sherman**.

11. Nella finestra **Condividi "ProtectedDocument1"**, posizionare il cursore del mouse sull'icona a forma di "occhio" che appare alla destra del nome di Joni. In questo modo dovrebbe apparire l'opzione **Può visualizzare**, che è l'impostazione attuale assegnata a lei per questo documento. L'icona a forma di "occhio" indica l'opzione "Può visualizzare". Selezionare il pulsante **Copia collegamento**. 

12. Una volta visualizzato il messaggio **Collegamento copiato** nella parte inferiore della finestra **Condividi "ProtectedDocument1"**, selezionare la "X" nell'angolo superiore della finestra per chiuderla.

13. Nel browser Edge, selezionare la scheda **Posta - Holly Dickson -Outlook** per tornare al messaggio di posta elettronica. Nel corpo del messaggio, sotto il testo aggiunto in precedenza, incollare (Ctrl+V) il collegamento al documento condiviso che è stato appena copiato negli appunti. Verrà visualizzato un collegamento per il file denominato **ProtectedDocument1.docx**. 

14. Selezionare **Invia**.

15. Verrà visualizzato un messaggio **I destinatari non possono accedere ai collegamenti** . Questo messaggio è stato generato da Microsoft Entra ID Protection dopo aver rilevato che nell'indirizzo e-mail è stato inserito il proprio indirizzo e-mail personale, il quale non ha l'autorizzazione per accedere al documento. Per questo test di lab, selezionare **Invia comunque**.

16. Passare a **LON-CL2**. 

17. Su **LON-CL2**, è necessario effettuare l'accesso a **Outlook sul Web** come **Lynne Robbins** dall'esercizio di lab precedente. Diconettersi dall'account di Lynne.

18. Nel browser Edge, chiudere tutte le schede tranne la scheda **Disconnetti**. In questa scheda, inserire il seguente URL nella barra degli indirizzi: **https://outlook.office365.com** 

19. Nella finestra **Scegli un account** selezionare **Usa un altro account**.

20. Nella finestra **Accedi**, immettere **JoniS@xxxxxZZZZZZ.onmicrosoft** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab) e quindi selezionare **Avanti**.

21. Nella finestra **Immetti password**, immettere la Nuova password utente che è stata precedentemente assegnata all'account di Joni e selezionare **Accedi**. 

22. Se viene visualizzata una finestra **Ti diamo il benvenuto**, selezionare la "X" per chiuderla.

23. Nella **Posta in arrivo** di Joni in **Outlook sul Web**, dovrebbe essere visualizzato il messaggio di posta elettronica appena inviato da Holly, con una riga dell'oggetto che indica che il documento ha l'autorizzazione di sola visualizzazione. Aprire il messaggio e-mail.

24. Nel messaggio e-mail, selezionare il file allegato per aprirlo.

25. Nella finestra **Opzioni di privacy** visualizzata, selezionare **Chiudi**. Il documento verrà aperto in **Word sul Web** in una nuova scheda del browser denominata **ProtectedDocument1.docx**. Tenere presente che il documento viene visualizzato nella visualizzazione di lettura di **Word sul Web**. Questo conferma che a Joni è stata assegnata l'autorizzazione di sola visualizzazione, senza possibilità di modifica del documento. Per verificarlo, provare a selezionare del testo all'interno del documento. Osservare il messaggio visualizzato: **Sola lettura. Questo documento è di sola lettura.** Prendere nota della filigrana specificata nel criterio **Project - Falcon**. <br/>

    Una volta terminata la verifica del documento, chiudere la scheda **ProtectedDocument1.docx** . 

26. Ora verificheremo cosa accade quando si tenta di aprire il documento inviato all'indirizzo di posta elettronica personale. Usare il telefono cellulare o il PC del corso per accedere alla cassetta postale personale. Aprire il messaggio di posta elettronica appena inviato da Holly all'indirizzo di posta elettronica personale e quindi tentare di aprire il file allegato. 

27. Poiché non si dispone dell'autorizzazione per accedere al documento, verrà visualizzata una finestra **Seleziona un account**. In uno scenario reale, è possibile accedere facoltativamente con un account autorizzato all'accesso al file o richiedere l'accesso dall'account **Holly@xxxxxZZZZZZ.onmicrosoft.com**. <br/>

    Ai fini di questo test, è stato appena verificato che non è possibile accedere al file perché non è stato condiviso con l'utente. È stato anche verificato che Joni è in grado di visualizzare solo il file, ma non modificarlo. Ora si modificheranno le autorizzazioni di condivisione per il file, in modo che Joni possa modificarle. Vedremo come questa esperienza differisce da quella appena completata. 

28. Passare a **LON-CL1**. 

29. In LON-CL1, nel browser Edge, dovrebbe comunque essere configurata la connessione a Microsoft 365 come **Holly Dickson** oltre che le schede aperte sia per **Word** che per **Outlook**. Selezionare la scheda **Posta elettronica - Holly Dickson - Outlook**. 

30. Nella cassetta postale di Holly, creare un altro messaggio di posta elettronica indirizzato a Joni Sherman. NON includere l'indirizzo e-mail personale nella riga CC. Nel modulo relativo al messaggio e-mail, immettere le informazioni seguenti:

    - A: immettere **Joni** e quindi selezionare **Joni Sherman** dall'elenco utenti. 

    - CC: lasciare vuoto

    - Aggiungere un oggetto: **Test documento protetto - Autorizzazione di modifica**

    - Corpo del messaggio: immettere **Apri il documento protetto allegato a questo messaggio di posta elettronica e provare a modificarlo.**

31. Proprio come con il messaggio e-mail precedente, ora è necessario condividere il documento con Joni, ma questa volta con l'autorizzazione di modifica. Per farlo, effettua i seguenti passaggi: <br/>

    - Selezionare la scheda **ProtectedDocument1** nel browser e quindi sul lato destro della barra dei menu selezionare il pulsante **Condividi** . Nel menu a discesa visualizzato, selezionare **Condividi**. 
    - Nella finestra **Condividi "ProtectedDocument1"**, immettere **Joni** nel campo **Aggiungi nome, gruppo o messaggio di posta elettronica** e quindi selezionare **Joni Sherman**.
    - A destra del nome di Joni è presente un'icona a forma di matita (**Puoi modificare**). Costituisce l'autorizzazione predefinita quando si condivide un documento. Selezionare il pulsante **Copia collegamento** per visualizzare cosa accade.
    - Prendere in considerazione il messaggio **Link copiato** visualizzato. Il messaggio indica che chiunque può modificare il documento, anche se è stato specificato il nome di Joni. Questo non è il risultato previsto, ossia di individuare Joni come unica persona che può modificare il documento. Per inserire tale restrizione, selezionare l'icona a forma di ingranaggio (**Impostazioni collegamento**) accanto al pulsante **Copia collegamento**. 
    - Nella finestra **Impostazioni collegamento** visualizzata selezionare l'opzione **Persone scelte**. Questa opzione è la chiave per limitare l'autorizzazione agli utenti selezionati. 
    - In **Altre impostazioni**, se viene visualizzata l'icona **Puoi modificare**, selezionare **Applica**. Tuttavia, se viene visualizzata l'opzione **Puoi visualizzare**, selezionare **Puoi visualizzare** e nel menu visualizzato, selezionare l'icona **Puoi modificare** e quindi **Applica.** 
    - Nella finestra **Condividi "ProtectedDocument1"** selezionare il pulsante **Copia collegamento**.
    - Prendere in considerazione il messaggio **Link copiato** visualizzato. Questa volta il messaggio indica che solo gli utenti specificati possono modificare il documento. In questo caso, la modifica sarà limitata a Joni, poiché è l'unica persona specificata. 
    - Selezionare la scheda **Posta elettronica - Holly Dickson - Outlook** nel browser e quindi incollare il collegamento nel corpo del messaggio di posta elettronica. 

32. Selezionare **Invia**.

33. Passare a **LON-CL2**. 

34. In **LON-CL2**, dovrebbe comunque essere configurato per **Outlook sul Web** come **Joni Sherman**. Nella **Posta in arrivo** di Joni dovrebbe essere visualizzato il messaggio di posta elettronica appena inviato da Holly, la cui riga Oggetto indica che il documento dispone dell'autorizzazione di modifica. Aprire il messaggio e-mail.

35. Nel messaggio e-mail, selezionare il file allegato per aprirlo.

36. Se Joni dispone dell'autorizzazione Solo visualizzazione, il documento viene aperto nel riquadro Visualizzazione di lettura. Di conseguenza, Joni non ha potuto modificare il documento. Questa versione del documento fornisce a Joni l'autorizzazione di modifica, quindi questa volta il documento deve essere aperto in modalità di modifica normale. Verificare che sia possibile immettere testo nel documento. 

    **Nota:** In questa attività è stato appena verificato che Microsoft Purview Information Protection ha protetto il documento in base ai parametri dei criteri PII configurati. Quando a Joni è stata assegnata l'autorizzazione Solo visualizzazione, il documento è stato aperto nella visualizzazione di lettura e non è stato possibile modificarlo. Quando a Joni è stata assegnata l'autorizzazione di modifica, il documento è stato aperto in Word e ha potuto modificarlo. Poiché Holly non ha condiviso il documento con l'utente, non è stato possibile aprirlo quando ha inviato il documento in un messaggio di posta elettronica alla cassetta postale personale. 

## Fine del Lab 3


# Complimenti. Hai completato l'ultimo lab di questo corso.
