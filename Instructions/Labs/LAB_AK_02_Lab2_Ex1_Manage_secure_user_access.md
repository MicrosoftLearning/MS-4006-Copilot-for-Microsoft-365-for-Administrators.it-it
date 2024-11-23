# Percorso di apprendimento 2 - Lab 2 - Esercizio 1: Gestire l'accesso sicuro agli utenti 

Le organizzazioni devono garantire che l'accesso ai dati aziendali in Microsoft 365 sia sempre sicuro. Microsoft 365, e a sua volta Copilot per Microsoft 365, spesso visualizzano dati sensibili e riservati, inclusi messaggi di posta elettronica, documenti, informazioni sui clienti e proprietà intellettuale. L'accesso non autorizzato a Microsoft 365 può causare violazioni di dati, furti di identità e altre attività dannose. Proteggendo l'accesso agli utenti, le organizzazioni possono impedire a coloro che non sono autorizzati di accedere ai dati aziendali e potenzialmente evitare l'uso improprio o la perdita di dati aziendali quando si utilizza Microsoft 365 e Copilot per Microsoft 365.

Nell'esercizio riportato nel seguente Lab, si continuerà a ricoprire il ruolo di Holly Dickson, il nuovo Amministrazione Microsoft 365 di Adatum. Si eseguiranno diverse funzioni di gestione utenti per preparare Adatum alla successiva distribuzione di Copilot per Microsoft 365. Si inizierà creando un account utente di Microsoft 365 per Holly, a cui verrà assegnato il ruolo di amministratore globale di Microsoft 365. 

**Nota:** l'ambiente VM fornito dal provider di hosting del lab include più di 20 account utente di Microsoft 365 esistenti, oltre a un numero elevato di account utente locali esistenti. In tutti i lab di questo corso verranno usati diversi account utente di Microsoft 365 esistenti. Anche se è stato creato l'account amministratore MOD dal provider di hosting del lab, si creerà comunque l'account utente per Holly Dickson, dal momento che costituisce procedura consigliata possedere più di un utente a cui assegnare il ruolo di amministratore globale di Microsoft 365. Ciò fornirà anche l'esperienza di creare un account utente di Microsoft 365, nel caso in cui non si abbia familiarità con il processo.

Holly ha quindi chiesto al CTO di Adatum di distribuire l'autenzicazione a più fattori (MFA) per Microsoft Entra e il blocco intelligente di Microsoft Entra. Queste funzionalità consentiranno di rafforzare la gestione delle password di tutta l'organizzazione in preparazione per Copilot per Microsoft 365. Il blocco intelligente verrà distribuito usando la gestione dei criteri di gruppo. 


### Attività 1. Creare un account utente per l'amministratore di Microsoft 365 di Adatum

Holly Dickson è il nuovo Amministrazione Microsoft 365 di Adatum. Poiché non le è stato configurato un account utente di Microsoft 365, Holly ha inizialmente eseguito l'accesso a Microsoft 365 come account amministratore MOD (amministratore globale predefinito) riportato nel lab precedente. Nel corso di questa attività, in cui si continuerà ad accedere come amministratore MOD, si creerà un account utente di Microsoft 365 per Holly. All'account Holly, si assegnerà anche il ruolo di amministratore globale di Microsoft 365. Questo ruolo fornirà a Holly le autorizzazioni necessarie per eseguire tutte le funzioni amministrative all'interno di Microsoft 365. Dopo questa attività, si eseguirà l'accesso usando il nuovo account di Holly e si eseguiranno tutti i lab rimanenti usando l'utente tipo di Holly. 

**Nota licenza:** prima di creare l'account di Holly, verificare il numero di licenze disponibili. In questo modo, si noterà che, mentre il tenant del lab fornisce 20 licenze di Microsoft 365 E5 (senza Teams) e 20 licenze di Microsoft Teams Enterprise, tutte queste licenze sono già state assegnate agli account utente esistenti creati dal provider di hosting del lab. Di conseguenza, è necessario prima annullare un'assegnazione per ogni licenza da un utente esistente, in modo da poterla assegnare a Holly.

**Importante:** come procedura consigliata nella distribuzione reale, è sempre necessario annotare le credenziali del primo account amministratore globale (in questo lab si tratta dell'account amministratore MOD, il cui nome utente è admin@xxxxxZZZZZZ.onmicrosoft.com, dove xxxxxZZZZZZ è il prefisso del tenant assegnato dal provider di hosting del lab). È consigliabile archiviare queste informazioni sull'account per motivi di sicurezza. **Questo account deve essere un'identità NON personalizzata** che possiede i privilegi più elevati possibili in un tenant. **Non** deve essere attivata l'autenticazione a più fattori perché non è personalizzata. Poiché il nome utente e la password per questo primo account amministratore globale vengono in genere condivisi tra più utenti, l'account costituisce un obiettivo perfetto per gli attacchi; pertanto, è sempre consigliabile che le organizzazioni creino account amministratore del servizio personalizzati (ad esempio, un amministratore di Exchange, un amministratore di SharePoint e così via) e mantengano il minor numero possibile di amministratori globali personali. Per gli amministratori globali personali creati nella distribuzione reale, ognuno di essi deve essere mappato a un singolo utente (ad esempio Holly Dickson) e devono avere applicata l'autenticazione a più fattori (MFA) di Microsoft Entra.

1. Nella macchina virtuale **LON-CL1** **l'interfaccia di amministrazione di Microsoft 365** deve essere ancora aperta nel browser Microsoft Edge dall'esercizio del lab precedente. Accedere a Microsoft 365 come **amministratore MOD**. 

2. Poiché si aggiunge un nuovo utente, è necessario iniziare controllando la disponibilità delle licenze prima di aggiungere l'account utente. Nel riquadro di spostamento dell'**interfaccia di amministrazione di Microsoft 365** selezionare **Fatturazione** per espandere il gruppo Fatturazione e quindi selezionare **Licenze**. 

3. Nella pagina **Licenze** viene visualizzata per impostazione predefinita la scheda **Sottoscrizioni**. Nell'elenco di sottoscrizioni, prendere nota di quelle a **Microsoft 365 E5 (senza Teams)** e di quelle a **Microsoft Teams Enterprise**, che non hanno licenze disponibili. Il tenant del lab fornisce 20 licenze per ogni sottoscrizione, ma sono state assegnate tutte le 40 licenze. Poiché è necessario assegnare a Holly sia una licenza di **Microsoft 365 E5 (senza Teams)** che una licenza di **Microsoft Teams Enterprise**, è prima necessario annullare l'assegnazione delle licenze da un account utente esistente al fine di renderle disponibili per Holly. 

4. Nel riquadro di spostamento dell'**interfaccia di amministrazione di Microsoft 365**, selezionare **Utenti**, quindi **Utenti attivi**. Nell'elenco **Utenti attivi** verrà visualizzato l'elenco degli account utente esistenti creati dal provider di hosting del lab. Poiché Christie Cline passerà a un nuovo ruolo nella società e non farà più parte del progetto pilota di Microsoft 365, si annullerà l'assegnazione delle licenze **Microsoft 365 E5 (senza Teams)** e **Microsoft Teams Enterprise** dal suo account, in modo da poterle riassegnare al nuovo account di Holly Dickson.

5. Nella pagina **Utenti attivi**, nell'elenco di utenti, selezionare **Christie Cline** (selezionare il nome con collegamento ipertestuale di Christie e non la casella di controllo accanto al nome).

6. Nel riquadro visualizzato di **Christie Cline**, viene visualizzata per impostazione predefinita la scheda **Account**. Selezionare la scheda **Licenze e app**. In **Licenze (2)**, selezionare le caselle di controllo accanto a **Microsoft 365 E5 (senza Teams)** e **Microsoft Teams Enterprise** per eliminarle, quindi selezionare **Salva modifiche**. Dopo aver salvato le modifiche, chiudere il riquadro **Christie Cline**. 

7. Ora è possibile creare un account utente per Holly Dickson, che è il nuovo Amministratore Microsoft 365 di Adatum. In questo modo, si assegnerà a Holly il ruolo di amministratore globale di Microsoft 365, che le consentirà l'accesso globale alla maggior parte delle funzionalità di gestione e dei dati in Microsoft Online Services. A Holly verranno assegnate anche le due licenze appena annullate da Christie Cline. <br/>

    Nella finestra **Utenti attivi**, selezionare l'opzione **Aggiungi un utente** visualizzata nella barra dei menu sopra l'elenco di utenti attivi. Verrà avviata la procedura guidata **Aggiungi un utente**.

8. Nella pagina **Configura le impostazioni di base** della procedura guidata **Aggiungi un utente**, immettere le informazioni seguenti:

    - Nome: **Holly**

    - Cognome: **Dickson** 

    - Nome visualizzato: digitando in questo campo viene visualizzato **Holly Dickson**.

    - Nome utente: **Holly** <br/>
    
        **IMPORTANTE:** A destra del campo **Nome utente** è presente il campo dominio. Verrà precompilato con il dominio cloud **xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab).<br/>
    
    - Deselezionare la casella di controllo **Crea automaticamente una password**, che visualizzerà un nuovo campo per l'immissione di una password definita dall'amministratore.

    - Immettere la nuova password amministrativa nel campo **Password** visualizzato 

    - Deselezionare la casella di controllo **Richiedi all'utente di cambiare la password al primo accesso** 

9. Selezionare **Avanti**. Se viene visualizzata la finestra di dialogo **Salva password** nella parte superiore della schermata, selezionare **Mai**.

10. Nella pagina **Assegna le licenze dei prodotti**, immettere le seguenti informazioni: <br/>

    - Selezionare la località: **Stati Uniti**

    - Licenze: nell'opzione **Assegna una licenza del prodotto all'utente** selezionare le caselle di controllo **Microsoft 365 E5 (no Teams)** e **Microsoft Teams Enterprise**

11. Selezionare **Avanti**.

12. Nella pagina **Impostazioni facoltative** selezionare la freccia a discesa a destra di **Ruoli**. 

13. Nella sezione **Ruoli** selezionare l'opzione **Accesso all'interfaccia di amministrazione**. Selezionando questa opzione, i ruoli di amministratore di Microsoft 365 usati più di frequente sono abilitati di seguito.  <br/>

    **Nota:** tutti i ruoli di amministratore verranno visualizzati se si seleziona **Mostra tutti per categoria**, l'opzione visualizzata dopo l'ultimo ruolo comune Per Holly, non è necessario visualizzare tutti i ruoli di amministratore per categoria, perché ad Holly verrà assegnato il ruolo di amministratore globale visualizzato nell'elenco dei ruoli di uso comune.

14. Selezionare la casella di controllo **Amministratore globale**. <br/>

    **Nota:** verrà visualizzato un messaggio di avviso che indica che Adatum ha già 7 amministratori globali. In un ambiente normale, ciò sarebbe eccessivo e non consigliato. Ai fini di questo lab, il provider di hosting del lab ha assegnato il ruolo di amministratore globale all'amministratore MOD e a sei altri account utente, cosa non comune in una distribuzione reale. Tuttavia, ai fini di questo lab nell'ambiente lab fittizio Adatum, ignorare questo messaggio. **Detto questo, le procedure consigliate da seguire prevedono di avere da due a quattro amministratori globali nelle distribuzioni reali di Microsoft 365.** 

15. Selezionare **Avanti**.

16. Nella finestra **Verifica e termina** rivedere le selezioni effettuate. Se è necessario modificare qualcosa, selezionare il collegamento **Modifica** appropriato e apportare le modifiche necessarie. In caso contrario, se tutto è corretto, selezionare **Completa l'aggiunta**. 

17. Nella pagina **Holly Dickson aggiunta agli utenti attivi**, nella sezione **Dettagli utente**, selezionare l'opzione **Mostra** per verificare che la password di Holly sia la stessa **password amministrativa** fornita dal provider di hosting del lab per l'account amministratore tenant (ad esempio, l'account amministratore MOD).  <br/>

    **Nota:** se è stata immessa accidentalmente una password diversa, quando si torna alla pagina **Utenti attivi**, sarà necessario selezionare l'icona **Reimposta una password** (l'icona della chiave visualizzata quando si passa il puntatore del mouse sull'account di Holly) per modificare la password con il valore corretto.

18. Selezionare **Chiudi**.

19. Rimanere connessi alla macchina virtuale Client 1 (LON-CL1) con l'interfaccia di amministrazione di Microsoft 365 aperta nel browser per l'attività successiva.


### Attività 2. Aggiornare il gruppo di progetti pilota di Microsoft 365

Dopo aver completato l'attività precedente, si dovrebbe essere ancora connessi all'**interfaccia di amministrazione di Microsoft 365** come account **amministratore MOD**. In questa attività si inizierà a implementare il progetto pilota di Microsoft 365 di Adatum come Holly Dickson, il nuovo amministratore di Microsoft 365 di Adatum. Pertanto, si inizierà questa attività disconnettendosi da Microsoft 365 come amministratore MOD e si accederà nuovamente come Holly. 

In un'attività precedente è stato creato un gruppo di Microsoft 365 per i membri del team del progetto pilota di Adatum in modo da poter creare un tema personalizzato per tale gruppo. In questa attività si aggiungerà Holly a questo gruppo. 

1. Nella macchina virtuale LON-CL1 l'**interfaccia di amministrazione di Microsoft 365** deve essere ancora aperta nel browser Microsoft Edge dall'attività precedente. Accedere a Microsoft 365 come **amministratore MOD**. <br/>

    Nella scheda **Interfaccia di amministrazione di Microsoft 365**, nell'angolo superiore destro della schermata, si noti che sono visualizzati il nome e dell'amministratore MOD e l'icona del megafono. Il nome viene visualizzato perché il tema personalizzato creato nell'esercizio lab precedente e associato a un gruppo di utenti del progetto pilota di Microsoft 365 includeva l'amministratore MOD. Tenere presente questo aspetto dopo aver eseguito nuovamente l'accesso come Holly Dickson. <br/>

    Selezionare l'icona dell'utente o il cerchio con le iniziali "MA" per **amministratore MOD** nell'angolo in alto a destra del browser. Nella finestra **Amministratore MOD** selezionare **Esci.** <br/>
    
    **Importante:** quando si esce da un account utente e si accede come un altro utente, è necessario chiudere tutte le schede del browser, ad eccezione della scheda **Disconnetti**. Si tratta di una procedura consigliata che consente di evitare confusione durante la chiusura delle finestre associate all'utente precedente. Dopo aver disconnesso l'account amministratore MOD, chiudere tutte le altre schede del browser, ad eccezione della scheda **Disconnetti**. 
    
2. Nel browser Microsoft Edge, nella scheda **Disconnetti**, immettere l'URL seguente nella barra degli indirizzi per accedere nuovamente a Microsoft 365: **https://portal.office.com**. 

3. Nella finestra **Scegli un account** viene visualizzato solo l'account amministratore tenant dell'amministratore MOD (l'account admin@xxxxxZZZZZZ.onmicrosoft.com) appena disconnesso. Selezionare **Usa un altro account**. 

4. Nella finestra **Accedi**, immettere **Holly@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab). Selezionare **Avanti**.

5. Nella finestra **Immetti password**, inserire la nuova password amministrativa assegnata all'account di Holly e quindi selezionare **Accedi**. 

6. Se viene visualizzata la finestra di dialogo **Rimanere connessi?** selezionare la casella di controllo **Non visualizzare più questo messaggio**, quindi selezionare **Sì.** 

7. Se viene visualizzata la finestra di dialogo **Benvenuto in Microsoft 365** al centro della schermata, non è possibile chiuderla. Quindi procedere selezionando due volte l'icona della freccia avanti a destra della finestra (**>**) e selezionare l'icona del segno di spunta per far avanzare le diapositive in questa finestra di messaggistica. 

8. Se viene visualizzata una finestra **Crea con Microsoft 365**, selezionare la **X** nell'angolo superiore della finestra per chiuderla. 

9. Nel browser Edge viene visualizzata la pagina **Benvenuto in Microsoft 365** nella scheda **Home | Microsoft 365**. Questa è la home page di Microsoft 365 di Holly. Prendere in considerazione che le iniziali di Holly vengono visualizzate nell'angolo superiore a destra dello schermo; tuttavia, il nome di Holly non viene visualizzato. Questo perché l'account di Holly non esisteva quando sono stati aggiunti gli utenti del progetto pilota di Microsoft 365 al gruppo associato al tema personalizzato nell'esercizio del lab precedente. Poiché quando accede al sistema, Holly vuole visualizzare il suo nome nella parte superiore di ogni finestra di Microsoft 365, desidera prima che venga aggiunto il proprio account al gruppo di utenti del progetto pilota di Microsoft 365. <br>

    Nella colonna delle icone dell'applicazione visualizzata nel riquadro di spostamento sul lato della schermata, selezionare **Amministratore**. Verrà aperta **l'interfaccia di amministrazione di Microsoft 365** in una nuova scheda del browser. 

10. Nell'**interfaccia di amministrazione di Microsoft 365** selezionare **Team e gruppi** nel riquadro di spostamento, quindi sotto a questo selezionare **Team e gruppi attivi**. 

11. Nella pagina **Team e gruppi attivi** è disponibile una scheda per visualizzare ognuno dei tipi di gruppo. La scheda **Gruppi di Teams e Microsoft 365** viene visualizzata per impostazione predefinita. In questa scheda, selezionare **Progetto pilota M365**.

12. Nel riquadro del **progetto pilota M365** visualizzato, per impostazione predefinita viene visualizzata la scheda **Generale**. Selezionare la scheda **Appartenenza**.

13. Nella scheda **Appartenenza**, viene visualizzata per impostazione predefinita la sottoscheda **Proprietari** nel riquadro di spostamento visualizzato sul lato del riquadro. Selezionare la sottoscheda **Membri** visualizzata sotto di essa.

14. Nella scheda **Membri**, selezionare **+Aggiungi membri**

15. Nel riquadro **Aggiungi membri del gruppo al progetto pilota M365** visualizzato, selezionare **Cerca per nome o indirizzo di posta elettronica** all'interno del campo. Nell'elenco di utenti visualizzati, scorrere verso il basso e selezionare **Holly Dickson**. Selezionare il pulsante **Aggiungi (1)** e quindi chiudere il riquadro **Aggiungi membri del gruppo al progetto pilota M365** dopo aver aggiunto Holly al gruppo.

16. Rimanere collegati a LON-CL1 con l'**interfaccia di amministrazione di Microsoft 365** aperta nel browser per l'attività successiva.


### Attività 3: Creare un criterio di accesso condizionale per implementare l'autenticazione a più fattori

Come indicato nel corso, esistono tre modi per implementare l'autenticazione a più fattori, con i criteri di accesso condizionale, con le impostazioni predefinite per la sicurezza e con l'autenticazione a più fattori legacy per utente (non consigliata per le organizzazioni di grandi dimensioni). In questo esercizio si abiliterà l'autenticazione a più fattori tramite un criterio di accesso condizionale, ovvero il metodo consigliato da Microsoft. Adatum ha dato indicazioni a Holly di abilitare l'autenticazione a più fattori per tutti gli utenti di Microsoft 365, sia interni che esterni. Tuttavia, allo scopo di testare l'implementazione del progetto pilota di Microsoft 365 di Adatum, Holly vuole escludere i membri del gruppo di progetti pilota M365 dalla necessità di usare l'autenticazione a più fattori per accedere. Al termine del progetto pilota, Holly aggiornerà i criteri rimuovendo l'esclusione di questo gruppo dal requisito MFA. I criteri includeranno anche altri due requisiti. Richiederà l'autenticazione a più fattori per tutte le app cloud e richiederà l'autenticazione a più fattori anche se un utente accede da una posizione attendibile. 

1. Nella macchina virtuale LON-CL1 l'**interfaccia di amministrazione di Microsoft 365** deve essere ancora aperta nel browser Microsoft Edge dall'attività precedente. Accedere a Microsoft 365 come **Holly Dickson**.
   
2. **Nell'interfaccia di amministrazione di Microsoft 365**, in **Interfacce di amministrazione**, selezionare **Identità**. In questo modo si apre l'interfaccia di amministrazione di Microsoft Entra in una nuova scheda del browser. Se viene visualizzata una finestra **Seleziona un account**, selezionare l'**account di Holly Dickson**.

3. **Nell'interfaccia di amministrazione di Microsoft Entra**, selezionare **Protezione** nel riquadro di spostamento e quindi selezionare **Accesso condizionale**.

4. Nella pagina **Accesso condizionale | Panoramica**, selezionare **Criteri** nel riquadro di spostamento centrale.

5. Nella pagina **Accesso condizionale | Criteri**, selezionare **+Nuovo criterio** nella barra degli strumenti in alto.

6. Nella finestra **Nuovo criterio di accesso condizionale**, immettere **MFA per tutti gli utenti di Microsoft 365** nel campo **Nome**.

7. Si inizierà definendo il requisito MFA per gli utenti. In **Utenti**, selezionare **0 utenti e gruppi selezionati**. In questo modo vengono visualizzate due schede: **Includi** ed **Escludi**.

8. Nella scheda **Includi** selezionare **Tutti gli utenti**. Verrà visualizzato il messaggio di avviso seguente: Questo tema verrà affrontato nei due passaggi successivi.

9. Selezionare la scheda **Escludi**. Per evitare il blocco del sistema, come indicato nel messaggio di avviso precedente, è opportuno escludere gli amministratori globali, in questo caso Holly. Holly desidera inoltre escludere gli altri membri del gruppo del progetto pilota Microsoft 365 per facilitare e accelerare i test. Quando Microsoft 365 sarà attivo in Adatum, Holly rimuoverà il gruppo del progetto pilota dall'elenco Escludi per questo criterio di accesso condizionale, mantenendo esclusi solo se stessa, l'amministratore MOD e alcuni altri amministratori globali. Per il momento, tuttavia, Holly desidera escludere l'intero gruppo del progetto pilota. <br/>

    A tale scopo, selezionare la casella di controllo **Utenti e gruppi**. 

10. Nella finestra visualizzata **Seleziona utenti e gruppi esclusi**, selezionare il gruppo del progetto pilota Microsoft 365. La scheda **Tutti** è visualizzata per impostazione predefinita. Per trovare rapidamente il gruppo del progetto pilota, selezionare la scheda **Gruppi**. Nell'elenco dei gruppi attivi, selezionare la casella di controllo accanto al gruppo **Progetto pilota M365**, quindi selezionare il pulsante **Seleziona** in fondo alla finestra. Tornare alla finestra **Nuovo criterio di accesso condizionale**, notare il messaggio visualizzato nella sezione **Utenti**. 

11. A questo punto verrà definirà il requisito dell'autenticazione a più fattori per tutte le app cloud. In **Risorse di destinazione**, selezionare **Nessuna risorsa di destinazione selezionata**. In questo modo vengono visualizzate due schede: **Includi** ed **Escludi**.

12. Selezionare il campo a discesa **Selezionare a che cosa si applica questo criterio** per visualizzare le varie opzioni nel menu a discesa. Selezionare **App cloud**. 

13. Nella scheda **Includi**, notare che l'impostazione predefinita è **Nessuna**. Se questa impostazione non è stata modificata, nessuna app cloud richiederà l'autenticazione a più fattori, inclusa Microsoft 365. Pertanto, anche se è stato creato questo criterio e selezionata l'opzione per richiedere l'autenticazione a più fattori per tutti gli utenti, lasciando l'impostazione **Risorse di destinazione** su **Nessuna**, gli utenti che accedono a Microsoft 365 non saranno tenuti a utilizzare l'autenticazione a più fattori. <br/>

    Nella scheda **Includi**, selezionare l'opzione **Seleziona app**. In questo modo, vengono visualizzate due sezioni: **Modifica filtro** e **Seleziona**. Nella sezione **Seleziona**, selezionare **Nessuno**. 

14. Nel riquadro visualizzato **Seleziona app cloud**, scorrere l'elenco delle applicazioni per visualizzare tutte le diverse applicazioni per le quali è possibile richiedere l'autenticazione a più fattori. **NON selezionare nessuna app.** È possibile scorrere questo elenco per avere un'idea della granularità con cui è possibile richiedere l'autenticazione a più fattori, qualora si decida di limitarne l'applicazione a specifiche applicazioni nelle implementazioni reali.  <br/>

    Per Adatum, Holly desidera richiedere l'autenticazione a più fattori per tutte le applicazioni cloud, una pratica aziendale più comune rispetto alla selezione di applicazioni specifiche. Nella scheda **Includi**, selezionare l'opzione **Tutte le app cloud**. Adatum non escluderà alcuna app cloud dall'autenticazione MFA. È possibile selezionare la **scheda Escludi** se si desidera visualizzare le opzioni disponibili. Funziona essenzialmente come la scheda **Includi**. È possibile visualizzare questa scheda, ma NON selezionare le app cloud per l'esclusione. 

15. Infine, verrà definito il requisito MFA per tutte le postazioni di accesso degli utenti. In alcuni scenari, le organizzazioni possono richiedere l'MFA solo se un utente accede da una postazione non attendibile. Tuttavia, Adatum desidera richiedere l'MFA per tutti gli utenti inclusi, indipendentemente dal luogo in cui effettuano l'accesso. <br/>

    In **Condizioni**, selezionare **0 condizioni selezionate**. In questo modo viene visualizzato un elenco di condizioni potenziali che il criterio prenderà in considerazione per la verifica. Per questo esercizio del lab, nella **condizione Percorsi**, selezionare **Non configurato**. In questo modo viene visualizzato un interruttore **Configura** e due schede: **Includi** ed **Escludi**. Entrambe le schede sono attualmente disabilitate.

16. Impostare l'interruttore **Configura** su **Sì**, che abilita le due schede. 

17. Nella scheda **Includi**, verificare che sia selezionata l'opzione **Qualsiasi rete o posizione** (selezionarla se necessario). Selezionare la scheda **Escludi**. Se l'organizzazione riconosce determinati indirizzi IP o intervalli di indirizzi come "attendibili," è possibile escludere il requisito MFA quando un utente accede da una di queste posizioni. Tuttavia, Adatum desidera richiedere l'MFA per tutti i tentativi di accesso degli utenti, indipendentemente dalla posizione. Sono compresi gli accessi di utenti interni ed esterni. Verificare che l'opzione **Reti e posizioni selezionati** sia selezionata e che nella sezione **Selezione** sia indicato **Nessuno**. Senza specificare alcuna posizione selezionata, questa impostazione assicura che nessuna posizione sia esclusa dall'autenticazione a due fattori. 

18. Nella sezione **Controlli di accesso**, nel gruppo **Concedi**, selezionare **0 controlli selezionati**. In questo modo verrà visualizzato il riquadro **Concedi**.

19. Nel riquadro visualizzato **Concedi**, verificare che l'opzione **Concedi accesso** sia selezionata (selezionarla se necessario). Notare tutti i controlli di accesso disponibili che possono essere abilitati con questo criterio. Questo criterio richiederà solo MFA, quindi selezionare la casella di controllo **Richiedi autenticazione a più fattori**. Fare clic sul pulsante **Seleziona** nella parte inferiore del riquadro **Concedi**, che chiuderà il riquadro. 

20. Nella parte inferiore della finestra **Nuovo criterio di accesso condizionale**, nel campo **Abilita criterio**, selezionare **Abilita**.

21. Prendere in considerazione il messaggio di avviso e le opzioni visualizzati nella parte inferiore della pagina che avvisano di non rimanere disconnessi. Selezionare l'opzione **Comprendo che il mio account sarà influenzato da questo criterio. Procedere comunque.** In realtà, il ruolo di Holly non sarà influenzato, in quanto membro del gruppo di progetti pilota M365 escluso da questo criterio.

22. Selezionare il pulsante **Crea** per creare il criterio.

23. Nella finestra **Accesso condizionale | Criteri**, verificare che venga visualizzato il criterio **autenticazione a più fattori per tutti gli utenti di Microsoft 365** e che il relativo **stato** sia impostato su **On**.

24. Rimanere connessi a LON-CL1 con tutte le schede del browser Microsoft Edge aperte per l'attività successiva.


### Attività 4. Testare l'autenticazione a più fattori per un utente incluso ed escluso

Per testare i criteri di accesso condizionale appena creati, disconnettersi da Microsoft 365 come Holly e accedere di nuovo come Adele Vance. Adele non è membro del gruppo di progetti pilota M365, pertanto Microsoft Entra deve richiedere che usi MFA durante l'accesso. Dopo aver eseguito l'accesso come Adele e aver verificato che l'autenticazione a più fattori funzioni, disconnettersi come Adele e accedere di nuovo come Holly. Poiché Holly fa parte del gruppo del progetto pilota M365 escluso dall'uso di MFA nei criteri di accesso condizionale, non è necessario usare MFA durante l'accesso come Holly. Analogamente, non sarà necessario usare l'autenticazione a più fattori quando si accede in qualità dei vari membri del gruppo di progetti pilota M365 nei restanti lab di questo corso.

**Importante:** per implementare l'autenticazione a più fattori, è necessario usare il telefono cellulare per ricevere un codice di verifica in modo che sia possibile immetterlo nel tenant come seconda forma di autenticazione. Se non si dispone di un telefono, è comunque possibile testare i criteri di accesso condizionale. Per gli studenti che non hanno un telefono, quando accedono come Adele Vance, il sistema richiederà di accedere con una seconda forma di autenticazione. A questo punto, è sufficiente annullare l'accesso e accedere di nuovo come Holly, operazione che non richiederà l'autenticazione a più fattori. Anche se non si completerà l'accesso MFA per Adele, sarà comunque possibile verificare che il sistema obblighi ad usarlo durante il tentativo di accesso.

1. Nella macchina virtuale LON-CL1 l'**interfaccia di amministrazione di Microsoft 365** deve essere ancora aperta nel browser Microsoft Edge dall'attività precedente. Accedere a Microsoft 365 come **Holly Dickson**. Si inizierà eseguendo la disconnessione da Microsoft 365. Nella scheda dell'**interfaccia di amministrazione di Microsoft 365** selezionare il nome di Holly nell'angolo in alto a destra del browser. Nella finestra **Holly Dickson** visualizzata selezionare **Esci.** 
    
2. Dopo aver eseguito la disconnessione da Microsoft 365 come Holly, chiudere la sessione del browser per cancellare la cache. Selezionare quindi l'icona **Edge** sulla barra delle applicazioni per aprire una nuova sessione del browser. Nel browser passare alla **Home page di Microsoft 365** immettendo l'URL seguente nella barra degli indirizzi: **https://portal.office.com/** 

3. Nella finestra **Scegli un account** selezionare **Usa un altro account**. 

4. Nella finestra **Accedi**, immettere **AdeleV@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab), quindi selezionare **Avanti**. Nella finestra **Immettere la password**, immettere la **password utente** fornita dal provider di hosting del lab e selezionare **Accedi**.

5. Poiché l'autenticazione a più fattori è abilitata per tutti gli utenti ad eccezione dei membri del gruppo di progetti pilota M365 (di cui Adele non è membro), viene visualizzata la finestra **Sono necessarie altre informazioni**. Selezionare **Avanti**. Verrà restituita la pagina **Microsoft Authenticator** , che rappresenta il punto di partenza per l'accesso con MFA. <br/>

    **Importante:** se non si dispone di un telefono, non è possibile procedere oltre quando si tenta di accedere come Adele. Anche se non è possibile completare l'accesso, è stato verificato che la prima parte dei criteri di accesso condizionale funziona, poiché richiede a Adele di accedere tramite MFA. A questo punto, passare al passaggio 18 in modo da poter accedere di nuovo come Holly.

6. Nella pagina **Microsoft Authenticator** visualizzata è possibile scaricare questa app per dispositivi mobili o usare un metodo diverso per la verifica MFA. Ai fini di questo lab è consigliabile usare il telefono cellulare, per non dover dedicare del tempo all'installazione dell'app Microsoft Authenticator, che è probabile che non venga usata nuovamente dopo questo corso. Selezionare l'opzione **Desidero configurare un metodo diverso** nella parte inferiore della pagina (**Importante:** NON confondere questo collegamento con il messaggio **Voglio usare un'app di autenticazione diversa** visualizzato immediatamente sopra). 

7. Nella finestra di dialogo **Scegli un metodo diverso** visualizzata, selezionare la freccia a discesa nel campo **Quale metodo si vuole usare?**, selezionare **Telefono** e poi **Conferma**. 

8. Nella finestra **Telefono** visualizzata, nel campo **Quale numero di telefono si vuole usare?**, selezionare il paese o l'area geografica e quindi nel campo accanto immettere il proprio numero di telefono (nel formato **nnn-nnn-nnnn).** Verificare che sia selezionata l'opzione **Ricevi un codice**, quindi selezionare **Avanti**.

9. Recuperare il codice di verifica dal messaggio di testo inviato al proprio telefono.

10. Nella finestra **Telefono** immettere il codice di verifica a 6 cifre nel campo codice e selezionare **Avanti**. Quando nella finestra **Telefono** viene visualizzato un messaggio che indica che il telefono è stato registrato correttamente, selezionare **Avanti**.

11. Nella pagina **Operazione riuscita** selezionare **Fatto**.

12. Microsoft ha implementato nuovi criteri di sicurezza nei tenant di valutazione usati nei lab di training. Tutti gli account utente di test predefiniti sono configurati in modo che gli studenti debbano modificare la password iniziale al successivo accesso. Questo problema si è verificato in precedenza quando si è eseguito l'accesso a Microsoft 365 come amministratore MOD nel primo esercizio del lab. Ora è necessario cambiare password per Adele. <br>

    Nella finestra **Aggiorna la password** visualizzata immettere la **password utente** fornita dal provider di hosting del lab nel campo **Password corrente**. Quindi, nei campi **Nuova password** e **Conferma password** immettere la nuova password utente definita per tutti gli utenti di test all'inizio del lab. Fare clic su **Accedi**.

13. Se viene visualizzata la finestra di dialogo **Rimanere connessi?** selezionare la casella di controllo **Non visualizzare più questo messaggio**, quindi selezionare **Sì.** 

14. Se viene visualizzata una finestra di dialogo **Ti diamo il benvenuto in Microsoft 365**, premere la freccia DESTRA due volte e quindi selezionare il segno di spunta.

15. Se viene visualizzata una finestra **Crea con Microsoft 365**, selezionare la **X** per chiuderla.

16. Nella pagina **Ti diamo il benvenuto in Microsoft 365**, selezionare l'icona **Word** visualizzata nella colonna delle icone dell'app sul lato sinistro della schermata. Verrà aperto **Microsoft Word Online**. In questo modo, si verifica la corretta accessibilità a un'applicazione di Microsoft 365 dopo l'autenticazione tramite MFA.  <br/>

    **Importante:** è stato confermato il corretto funzionamento della prima parte dei criteri di accesso condizionale creati. Il criterio stabilisce che un utente non appartenente al team del progetto pilota di Microsoft 365 debba effettuare l'accesso tramite MFA. Il funzionamento è stato confermato durante un accesso eseguito con l'account di Adele. A questo punto, si effettua la disconnessione dall'account di Adele e si accede con l'account di Holly, per verificare il corretto funzionamento anche della seconda parte dei criteri di accesso condizionale. L'uso di autenticazione a più fattori NON è richiesto durante l'accesso con l'account di Holly, in quanto appartenente al gruppo del progetto pilota di Microsoft 365, escluso dall'obbligo di MFA nei criteri di accesso condizionale.

17. Nella scheda **interfaccia di amministrazione di Microsoft 365**, selezionare l'icona per l'account di Adele nell'angolo superiore destro del browser. Nella finestra **Adele Vance** visualizzata, selezionare **Disconnetti**. <br/>
    
18. Chiudere la sessione del browser per cancellare la cache. Selezionare l'icona **Edge** sulla barra delle applicazioni per aprire una nuova sessione del browser. Nel browser, passare alla **home page di Microsoft 365** immettendo l'URL seguente nella barra degli indirizzi: **https://portal.office.com/** 

19. Nella finestra **Seleziona un account**, selezionare **Holly@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab) e quindi selezionare **Avanti.** Nella finestra **Immetti password**, inserire la nuova password amministrativa definita per tutti gli utenti di test all'inizio del lab, successivamente assegnata all'account di Holly. Fare clic su **Accedi**.

20. Poiché l'MFA è richiesta per tutti gli utenti, ad eccezione dei membri del team del progetto pilota M365 (di cui Holly fa parte), l'MFA non sarà necessaria. Poiché l'MFA non è necessaria, il sistema visualizza la **Home page di Microsoft 365** nella scheda **Home | Microsoft 365**. 

21. Se viene visualizzata una finestra di dialogo **Ti diamo il benvenuto in Microsoft 365**, premere la freccia DESTRA due volte e quindi selezionare il segno di spunta.

22. Se viene visualizzata una finestra **Crea con Microsoft 365**, selezionare la **X** per chiuderla.

23. Nella pagina **Ti diamo il benvenuto a Microsoft 365**, selezionare l'icona **Amministratore** nel riquadro laterale per passare all'**interfaccia di amministrazione di Microsoft 365**. <br/>

    **Importante:** è stato confermato il corretto funzionamento della seconda parte dei criteri di accesso condizionale creati. Il criterio esclude i membri del gruppo del progetto pilota di Microsoft 365 dall'obbligo di accesso tramite MFA. Holly, essendo membro di questo gruppo, non è stata tenuta ad accedere tramite MFA.

24. Rimanere connessi a LON-CL1 con l'**interfaccia di amministrazione di Microsoft 365** aperta nel browser.


### Attività 5: implementare il blocco intelligente di Microsoft Entra

Il CTO di Adatum ha richiesto l'implementazione di blocco intelligente di Microsoft Entra, una soluzione progettata per impedire agli utenti malintenzionati di indovinare le password degli utenti o usare metodi di forza bruta per accedere alla rete. Il blocco intelligente è in grado di distinguere gli accessi effettuati da utenti legittimi, gestendoli in modo appropriato, da quelli provenienti da aggressori o fonti sconosciute, applicando misure di protezione adeguate. 

Il CTO è impaziente di implementare il blocco intelligente, poiché consentirà di bloccare gli aggressori garantendo al contempo agli utenti di Adatum l'accesso continuo ai propri account e la possibilità di mantenere la produttività. Il CTO ha incaricato Holly di configurare il blocco intelligente affinché impedisca agli utenti di riutilizzare le stesse password e di scegliere password troppo semplici o comuni. 

**Nota:** è possibile gestire le impostazioni dei criteri di blocco dell'account sia tramite l'Editor Gestione Criteri di gruppo che tramite la funzionalità di blocco intelligente di Microsoft Entra. Questa attività di lab illustra come accedere a ciascun metodo, sebbene le impostazioni di Blocco intelligente saranno aggiornate esclusivamente in Microsoft Entra. È necessario usare il controller di dominio dell'azienda (LON-DC1) per accedere all'Editor Gestione Criteri di gruppo. 

1. Nelle attività precedenti, è stato usato LON-CL1. In questa attività, invece, verrà usato il controller di dominio di Adatum, LON-DC1. <br/>

    Passare a **LON-DC1**.

2. In **LON-DC1**, è necessario selezionare **CTRL+ALT+CANC** per accedere. L'istruttore fornirà la guida su come trovare questa opzione nell'ambiente della macchina virtuale. Accedere a LON-DC1 usando l'account amministratore locale di Adatum creato dal provider di hosting del lab (**Amministratore**) con la password **Pa55w.rd**.

3. In LON-DC1, **Gestione server** viene avviato automaticamente all'avvio. In **Gestione server**, selezionare **Strumenti** nella barra dei menu in alto a destra e nel menu a discesa, selezionare **Gestione Criteri di gruppo.** Ingrandire la finestra **Gestione Criteri di gruppo** visualizzata.

4. Modificare i criteri di gruppo che contengono le impostazioni relative al blocco dell'account dell'organizzazione. Se necessario, nell'albero della console radice nel riquadro laterale, espandere **Forest:Adatum.com**, quindi espandere **Domini** e quindi espandere **Adatum.com**.  <br/>

    In **Adatum.com**, fare clic con il pulsante destro del mouse su **Criterio dominio predefinito** e quindi selezionare **Modifica** nel menu.

5. Espandere la finestra **Editor Gestione Criteri di gruppo** visualizzata.

6. Nell'albero **Criterio dominio predefinito** nel riquadro laterale, in **Configurazione computer**, espandere **Criteri**, espandere **Impostazioni di Windows**, espandere **Impostazioni di protezione**, quindi espandere **Criteri account**.

7. Nella cartella **Criteri account**, selezionare **Criteri di blocco account**.

8. Come evidenziato nel riquadro visualizzato, nessuno dei parametri relativi al blocco intelligente risulta attualmente definito. Invece di gestire questi parametri di blocco tramite l'Editor Gestione Criteri di gruppo, verrà usata l'interfaccia di amministrazione di Microsoft Entra. Sebbene sia possibile usare l'Editor Gestione Criteri di gruppo, questo metodo è generalmente riservato agli ambienti Active Directory locali. L'Editor è stato mostrato per consentire di conoscere questa alternativa. Tuttavia, per le organizzazioni che usano esclusivamente servizi basati sul cloud, come Microsoft 365, o che trovano più semplice l'uso dell'interfaccia di amministrazione di Microsoft Entra rispetto all'accesso all'Editor Gestione criteri di gruppo, risulta preferibile usare l'**interfaccia di amministrazione di Microsoft Entra** per configurare i valori corrispondenti nel contesto di Entra ID. <br/>  

    È importante notare che il comportamento del blocco e le opzioni di personalizzazione variano tra i due metodi. Con l'Editor Gestione Criteri di пruppo, è possibile esercitare un controllo più dettagliato sulle impostazioni dei criteri, inclusi parametri come Soglia di blocchi dell'account, Durata del blocco e Reimposta conteggio blocco account dopo. Tuttavia, l'uso di questo metodo richiede una buona conoscenza dei Criteri di gruppo e dell'amministrazione di Active Directory. Al contrario, i criteri di blocco account in Microsoft Entra offrono possibilità di personalizzazione più limitate. Tuttavia, risulta più semplice da usare, pur mancando alcune delle opzioni di ottimizzazione disponibili in Criteri di gruppo. <br/>

    Per Adatum, Holly ha optato per l'interfaccia di amministrazione di Microsoft Entra per configurare i criteri di blocco account aziendali. Nella barra delle applicazioni nella parte inferiore della schermata, selezionare l'icona **Microsoft Edge**. Se necessario, ingrandire la finestra del browser all'apertura.

9. Nel browser Edge, passare alla **home page di Microsoft 365** immettendo l'URL seguente nella barra degli indirizzi: **https://portal.office.com** 

10. Nella finestra di dialogo **Accedi**, è necessario accedere come Holly Dickson. Immettere **Holly@xxxxxZZZZZZ.onmicrosoft.com**, dove xxxxxZZZZZZ è il prefisso del tenant assegnato dal provider di hosting del lab. Selezionare **Avanti**. <br/>

11. Nella finestra di dialogo **Immetti password**, immettere la nuova password amministrativa assegnata all'account di Holly e quindi selezionare **Accedi**. 

12. Nella finestra di dialogo **Rimanere connessi?**, selezionare la casella di controllo **Non mostrare più** e quindi selezionare **Sì**. Nella finestra di dialogo **Salva password** visualizzata, selezionare **Mai**.

13. Se viene visualizzata la finestra di dialogo **Benvenuto in Microsoft 365** al centro della schermata, non è possibile chiuderla. Quindi procedere selezionando due volte l'icona della freccia avanti a destra della finestra (**>**) e selezionare l'icona del segno di spunta per far avanzare le diapositive in questa finestra di messaggistica. 

14. Se viene visualizzata una finestra **Trova altre app** o **Crea con Microsoft 365**, selezionare la **X** nell'angolo superiore delle finestre per chiuderle. 

15. Nella pagina **Benvenuto in Microsoft 365**, nell'elenco delle icone delle applicazioni visualizzate nel riquadro della finestra laterale, selezionare **Amministratore**. Verrà aperta l'**interfaccia di amministrazione di Microsoft 365** in una nuova scheda del browser. 

16. Nell’**interfaccia di amministrazione di Microsoft 365** selezionare **Mostra tutto** nel riquadro di spostamento. In **Interfacce di amministrazione**, selezionare **Identità**, che visualizza l'**interfaccia di amministrazione di Microsoft Entra** in una nuova scheda.

17. Nell'**interfaccia di amministrazione di Microsoft Entra**, selezionare **Protezione** nel riquadro di spostamento e quindi selezionare **Metodi di autenticazione**.

18. Nella pagina **Metodi di autenticazione | Criteri**, nel riquadro centrale nella sezione **Gestisci**, selezionare **Protezione password**.

19. Nella finestra **Metodi di autenticazione | Protezione password**, nel riquadro dei dettagli a destra, immettere le informazioni seguenti:

    - Nella sezione **Blocco intelligente personalizzato**:

        - **Soglia di blocco**: questo campo specifica il numero di tentativi di accesso non riusciti consentiti a un account prima che venga bloccato per la prima volta. L'impostazione predefinita è 10. Ai fini dei test, Adatum ha richiesto di impostare il valore su **3**.

        - **Durata del blocco in secondi**: è la durata in secondi di ciascun blocco. Il valore predefinito è 60 secondi (1 minuto). Adatum ha richiesto di modificare il valore in **90** secondi.

    - Nella sezione **Password vietate personalizzate**:

        - **Imponi elenco personalizzato**: selezionare **Sì**

        - **Elenco Password vietate personalizzate:** inserire i seguenti valori, premendo INVIO dopo ciascun valore in modo che ogni valore venga riportato su una riga separata:

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Mai4get!!**

    - Nella sezione **Modalità**, selezionare **Applicata**

20. Selezionare **Salva** nella barra dei menu nella parte superiore della pagina.

21. Ora è necessario testare la funzionalità della password vietata. Selezionare l'icona utente di Holly Dickson nell'angolo superiore destro della schermata e nel menu visualizzato, selezionare **Visualizza account**. 

22. Nella finestra **Account personale** visualizzata, nel riquadro **Password**, selezionare **Modifica password**.

23. Verrà aperta una nuova scheda che visualizza la finestra **Modifica password**. Nel campo **Password precedente**, immettere la password esistente di Holly, ovvero la nuova password amministrativa. <br/>

    Immettere **Never4get!!** nei campi **Crea nuova password** e **Conferma nuova password**, quindi selezionare **Invia**. Osservare il messaggio di errore che si riceve.

24. Nel browser, chiudere la scheda **Modifica password**. 

25. Si eseguirà ora il test della funzionalità soglia di blocco. Per procedere, usare l'account di Patti Fernandez. Selezionare l'icona utente di Holly Dickson nell'angolo in alto a destra della schermata e, nel menu visualizzato, selezionare **Disconnetti**.  

26. Dopo aver eseguito la disconnessione come Holly, verrà visualizzata la finestra **Seleziona un account** nella scheda **Accedi a Microsoft Entra**. Come procedura consigliata, alla disconnessione da un servizio online Microsoft come utente e al nuovo accesso come altro utente, chiudere tutte le schede del browser, ad eccezione della scheda **Disconnetti** o **Accedi**. In questo caso, chiudere le altre schede ora e lasciare aperta la scheda **Accedi** .  <br/>

    Nella finestra **Scegli un account** selezionare **Usa un altro account**. 

27. Nella finestra **Accedi**, inserire **pattif@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso tenant assegnato dal proprio provider di hosting del lab) e quindi selezionare **Avanti**. 

28. Nella finestra **Immetti password**, inserire qualsiasi combinazione casuale di lettere e numeri e quindi selezionare **Accedi**. Prendere in considerazione la visualizzazione del messaggio di errore password non valida. 

    Ripetere questo passaggio altre 2 volte. 
    
    Poiché si imposta la **soglia di blocco, in ** su **3**, viene visualizzato un messaggio di errore che indica che l'account è bloccato dopo il terzo tentativo di accesso non riuscito. <br/>

    **Nota:** se non si riceve questo messaggio di blocco dopo il terzo tentativo, il sistema non ha ancora completato la propagazione di questa soglia di blocco nel servizio. L'applicazione di queste modifiche richiede alcuni minuti. Attendere alcuni minuti e quindi eseguire di nuovo l'accesso con una password fittizia. Il test di questo lab ha riportato risultati variabili. La modifica a volte si propaga quasi immediatamente in modo che venga bloccato dopo il terzo tentativo di accesso. Altre volte servono da 5 a 10 minuti prima che venga visualizzato il messaggio di blocco. Continuare questo processo fino a quando non si riceve il messaggio di blocco, a quel punto l'account di Patti verrà temporaneamente bloccato per impedire l'accesso non autorizzato.

29. Non sarà possibile accedere nuovamente come Patti fino alla durata del **blocco di 90 secondi** impostata in precedenza. <br/>

    Dopo il blocco, attendere 90 secondi e quindi accedere di nuovo come **pattif@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant assegnato dal provider di hosting del lab). Nel campo **Password**, immettere la password di Patti, ovvero la **password utente** fornita dal provider di hosting del lab. 
 
30. Come si ricorderà, tutti gli account utente di test predefiniti nel tenant di valutazione vengono configurati in modo che sia necessario modificare la password iniziale al successivo accesso. La visualizzazione della finestra **Aggiorna la password** attesta che il tentativo di accesso usando la password effettiva di Patti ha avuto esito positivo. <br>

    **Nota:** NON è necessario completare il processo di accesso per Patti, perché si tratta dell'ultimo esercizio del lab tramite il controller di dominio LON-DC1. È possibile chiudere tutte le applicazioni in LON-DC1.
 
# Procedere al Lab 2 - Esercizio 2
