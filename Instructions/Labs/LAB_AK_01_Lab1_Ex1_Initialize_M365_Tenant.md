## Tenant WWL: condizioni per l'utilizzo

Se, nell'ambito di una consegna di un corso con istruttore, viene fornito un tenant, tenere presente che il tenant viene messo a disposizione per supportare i lab pratici di tale corso. 

I tenant non devono essere condivisi o usati per scopi diversi dai lab pratici. Il tenant utilizzato in questo corso è un tenant di valutazione e non può essere utilizzato o reso accessibile dopo il termine della lezione e non è idoneo per l'estensione. 

I tenant non devono essere convertiti in un abbonamento a pagamento. I tenant ottenuti nell'ambito di questo corso rimangono di proprietà di Microsoft Corporation, che si riserva il diritto di accedervi e di recuperarli in qualsiasi momento. 

# Percorso di apprendimento 1. Lab 1. Esercizio 1. Inizializzare il tenant di Microsoft 365 

Adatum Corporation è una filiale di Contoso Electronics. Adatum esegue le applicazioni legacy (ad esempio Microsoft Exchange Server 2019) in una distribuzione locale. Tuttavia, di recente ha effettuato una sottoscrizione a Microsoft 365, creando in tal modo una distribuzione ibrida in cui deve sincronizzare le distribuzioni locali e cloud. 

In qualità di amministratore di Microsoft 365 per Adatum, si ha l'incarico di distribuire Microsoft 365 nella distribuzione ibrida di Adatum usando un ambiente lab virtualizzato. In questo esercizio si configurerà il tenant di valutazione di Microsoft 365 di Adatum e l'istruttore indicherà come ottenere le credenziali di Microsoft 365 nell'ambiente del lab. Tali credenziali verranno usate in tutti gli altri lab del presente corso. 

Nell'ambiente lab, il provider di hosting del lab ha già ottenuto un tenant di valutazione di Microsoft 365. Il provider di lab ha anche creato due account amministratore che verranno usati nell'ambiente lab della macchina virtuale: 

- Un account amministratore locale per l'ambiente locale di Adatum (Adatum\Administrator).
- Un account amministratore tenant predefinito in Microsoft 365 (il nome visualizzato per questo account utente è amministratore MOD). 

Si accederà al PC Client 1 (LON-CL1) usando l'account Adatum\Administrator locale. Quando si accede a Microsoft 365 per la prima volta, si usa inizialmente l'account amministratore tenant di Microsoft 365 (amministratore MOD). Si preparerà quindi il tenant di Microsoft 365 di Adatum per Microsoft Entra ID e per i lab successivi usando gli avvisi di controllo e Microsoft Graph PowerShell.


### Attività 1. Configurazione del profilo dell'organizzazione di Adatum

Nei laboratori di questo corso ci si eserciterà assumendo il ruolo di amministratore Microsoft 365 di Adatum, nella persona di Holly Dickson. A Holly è stato richiesto di configurare il profilo dell'azienda per il tenant di valutazione di Microsoft 365. In questa attività verranno configurate le opzioni necessarie per il tenant di Adatum. Non avendo ancora creato un account utente di Microsoft 365 personale (questa operazione verrà eseguita nell'esercizio del lab successivo), Holly accederà inizialmente a Microsoft 365 tramite l'account amministratore del tenant predefinito di Microsoft 365 e la password creata dal provider di hosting del lab. Tale account è l'account amministratore MOD, il cui alias è "admin". Il nome utente per tale account è admin@xxxxxZZZZZZ.onmicrosoft.com (dove xxxxxZZZZZZ è il prefisso del tenant assegnato dal provider di hosting del lab); il nome visualizzato per l'account sarà amministratore MOD.

1. Il provider di hosting del lab fornirà due password usate con gli account utente fittizi nel tenant di valutazione di Microsoft 365. All'account amministratore MOD, che è l'amministratore tenant predefinito, è stata assegnata la **password amministrativa**. A tutti gli altri utenti, anche a quelli a cui è stato assegnato un ruolo di amministratore, è stata assegnata la **password utente**. <br>

    Ai fini della sicurezza, Microsoft ha configurato il tenant di valutazione in modo che tutti gli utenti predefiniti debbano modificare la password al successivo accesso. Alcuni provider di hosting di lab potrebbero fornire due nuovi campi password, uno per gli amministratori (l'amministratore MOD e Holly Dickson) e uno per tutti gli altri utenti. Se questi due nuovi campi password vengono visualizzati nella macchina virtuale, immettere una nuova password per ognuno dei due. Questi nuovi valori delle password verranno archiviati nella macchina virtuale e saranno visualizzati nelle istruzioni del lab. <br>
 
    Altri provider di hosting del lab potrebbero non fornire questi nuovi campi password. Per questi ambienti, è necessario annotare manualmente la nuova password che si prevede di assegnare agli utenti che eseguono l'accesso. <br>

    Nell'elaborazione delle nuove password, tenere presenti le linee guida per le password di Microsoft: <br>

    - Un minimo di 8 caratteri, con almeno:
       - 1 carattere maiuscolo
       - 1 carattere minuscolo
       - 1 carattere speciale Le password non vengono convalidate in base ai requisiti di Microsoft fino a quando non si modifica la vecchia password al successivo accesso dell'utente.

2. Quando si apre l'ambiente macchina virtuale del provider di hosting del lab, è necessario iniziare con la macchina virtuale Client 1 (LON-CL1). Se l'ambiente della macchina virtuale viene aperto con uno degli altri computer (ad esempio LON-DC1), passare a **LON-CL1**.

3. Accedere a **LON-CL1** come account **amministratore** locale creato dal provider di hosting lab con la password **Pa55w.rd**. 

4. Sulla barra delle applicazioni nella parte inferiore della schermata, selezionare l'icona di **Microsoft Edge**. Se necessario, ingrandire la finestra del browser all'apertura.

5. Nel browser Edge, passare alla **home page di Microsoft 365** immettendo l'URL seguente nella barra degli indirizzi: **https://portal.office.com** 

6. Nella finestra di dialogo **Accedi** immettere il **nome utente amministrativo** fornito dal provider di hosting del lab (account amministratore MOD) per il tenant di valutazione di Microsoft 365. Il nome utente deve essere nel formato **admin@xxxxxZZZZZZ.onmicrosoft.com**, dove xxxxxZZZZZZ è il prefisso del tenant assegnato dal provider di hosting del lab. Selezionare **Avanti**. <br/>

    **Nota:** nelle istruzioni per i lab visualizzate nell'ambiente lab della macchina virtuale, il provider di hosting del lab può fornire la possibilità di selezionare il pulsante **Digita testo** (o equivalente) accanto ai dati della risorsa, ad esempio nomi utente, password, comandi di PowerShell e altri dati che devono essere immessi durante queste esercitazioni. Altri provider di hosting di lab possono fornire un metodo alternativo, ad esempio la possibilità di copiare e incollare tali informazioni. Questa funzionalità permette di riparmiare il tempo necessario per immettere manualmente le informazioni. 

7. Nella finestra di dialogo **Immettere la password** immettere la **password amministrativa** predefinita fornita dal provider di hosting del lab, quindi selezionare **Accedi**. 

8. Il provider di hosting del lab potrebbe aver configurato o meno l'account amministratore MOD per richiedere una nuova password all'accesso. Se ha impostato la richiesta della password, viene visualizzata la finestra di dialogo **Aggiorna la password**. In tal caso, immettere la **password amministrativa** fornita dal provider di hosting del lab nel campo **Password corrente**, quindi immettere la nuova password amministrativa nei campi **Nuova password** e **Conferma password** e selezionare **Accedi**.

9. Se viene visualizzata la finestra di dialogo **Rimanere connessi?** selezionare la casella di controllo **Non visualizzare più questo messaggio**, quindi selezionare **Sì.** 

10. Se viene visualizzata la finestra di dialogo **Benvenuto in Microsoft 365** al centro della schermata, non è possibile chiuderla. Quindi procedere selezionando due volte l'icona della freccia avanti a destra della finestra (**>**) e selezionare l'icona del segno di spunta per far avanzare le diapositive in questa finestra di messaggistica. 

11. Se viene visualizzata la finestra di dialogo **Trova altre app** o **Crea con Microsoft 365**, selezionare la **X** nell'angolo superiore delle caselle per chiuderla. Analogamente, se viene visualizzata la finestra di dialogo Accedere a Microsoft Edge, selezionare il pulsante **No grazie**.

12. La pagina **Benvenuto in Microsoft 365** viene visualizzata nel browser Edge nella scheda **Home | Microsoft 365**. Si tratta della home page di Microsoft 365 dell'amministratore MOD. <br/>

    Si noti che vengono visualizzati un'icona o un cerchio con "MA" (le iniziali dell'amministratore MOD) nell'angolo in alto a destra della schermata. In alcuni tenant di valutazione è visibile un'icona; in altri sono visibili le iniziali "MA" in un cerchio; tutto dipende dal fatto che il provider di hosting del lab abbia aggiunto un'icona all'account dell'amministratore MOD. L'icona o le iniziali rappresentano l'account **amministratore MOD**, ovvero l'account amministratore tenant creato dal provider di hosting del lab a cui si è appena effettuato l'accesso Se uno degli account utente di Microsoft 365 esistenti creati dal provider di hosting del lab ha una foto associata all'account, viene visualizzata la foto dell'utente anziché le sue iniziali quando si accede a Microsoft 365 in qualità di tale utente. Tuttavia, quando un utente come l'amministratore MOD non ha alcuna immagine assegnata, vengono visualizzate le iniziali dell'utente al posto dell'immagine o viene visualizzata un'icona se ne è stata assegnata una all'account dal provider di hosting del lab. <br/>

    Nella pagina **Benvenuto in Microsoft 365**, nell'elenco delle icone dell'applicazione visualizzate nel riquadro di spostamento, selezionare **Amministratore**. Verrà visualizzata l'**interfaccia di amministrazione di Microsoft 365** in una nuova scheda del browser. 

13. Nell’**interfaccia di amministrazione di Microsoft 365** selezionare **Mostra tutto** nel riquadro di spostamento, quindi selezionare **Impostazioni**. Nel gruppo **Impostazioni** selezionare **Impostazioni organizzazione**. 

14. Nella pagina **impostazioni dell'organizzazione**, la scheda **Servizi** viene visualizzata per impostazione predefinita. Selezionare la scheda **Profilo organizzazione**.

15. Nella scheda **Profilo organizzazione** selezionare **Informazioni sull'organizzazione** nell'elenco dei dati del profilo.

16. Nel riquadro **Informazioni sull'organizzazione** visualizzato immettere le informazioni seguenti: <br/>

    - Nome: **Adatum Corporation** (Nota: Adatum Corporation è una filiale di Contoso Inc. Il tenant di valutazione Microsoft ottenuto dal provider di hosting del lab per questo laboratorio potrebbe essere stato originariamente assegnato a Contoso. Se **Contoso** (o qualsiasi altro valore) viene visualizzato come nome dell'organizzazione, modificarlo in **Adatum Corporation**.

    - Indirizzo: **555 Main Street**

    - Città: **Redmond**

    - Stato o provincia: **Washington**

    - CAP o codice postale: **98052**

    - Telefono: non modificare

    - Contatto tecnico: non modificare

    - Lingua preferita: **inglese**

17. Seleziona **Salva**.

18. Nella parte superiore del riquadro **Informazioni sull'organizzazione** prendere nota del messaggio che indica che le modifiche sono state salvate. Selezionare l'icona a forma di **X** nell'angolo superiore destro del riquadro per chiuderlo.

19. Rimanere connessi a **LON-CL1** con Microsoft Edge aperto sull'**interfaccia di amministrazione di Microsoft 365** per l'attività successiva.

### Attività 2. Creare un tema personalizzato per il team del progetto pilota di Adatum

Nell'attività precedente si è appreso che quando un utente esegue l'accesso a Microsoft 365, il sistema visualizza la sua fotografia (se ne è stata fornita una) o le sue iniziali se non è stata fornita alcuna fotografia. Per Holly Dickson, l'amministratore Microsoft 365 di Adatum, non è sufficiente la visualizzazione di una foto o delle iniziali dell'utente connesso. Vuole creare un tema personalizzato per i membri del team del progetto pilota in modo che sia visualizzato anche il nome dell'utente connesso. Al termine del progetto pilota, se i membri del team del progetto pilota preferiscono questa impostazione, configurerà la stessa opzione nel tema predefinito, in modo che si applichi a tutti gli utenti. 

I temi personalizzati devono essere associati a uno o più gruppi di Microsoft 365. Pertanto, per implementare questa modifica, Holly deve prima creare un gruppo di Microsoft 365 per i membri del team del progetto pilota. Quindi, può creare un tema personalizzato associato a questo gruppo che consenta all'impostazione di visualizzare il nome dell'utente connesso. In questa attività verrà creato un gruppo di Microsoft 365 per i membri del team del progetto pilota Microsoft 365 di Adatum. Successivamente verrà creato un tema personalizzato che visualizza il nome dell'utente connesso e tale tema verrà assegnato al team del progetto pilota. Verranno inoltre esaminate altre opzioni che possono essere configurate con temi personalizzati e sarà possibile apportare qualunque modifica del colore desiderata.

**Importante:** al termine di questa attività si cercherà di salvare il tema personalizzato creato. L'interfaccia di amministrazione di Microsoft 365 presenta un problema noto della piattaforma, per cui a volte il tema personalizzato viene salvato correttamente e altre volte viene restituito un messaggio che indica "Non è stato possibile salvare il tema. Riprovare più tardi". Se viene visualizzato questo messaggio, non è possibile fare altro che procedere. Il tentativo di salvare il tema in un secondo momento restituisce in genere lo stesso errore. Questo problema non influirà sui laboratori futuri, tranne per il fatto che non permetterà di visualizzare il nome dell'utente accanto all'icona dell'utente o le iniziali nella riga dell'intestazione. Nonostante questo problema noto, è consigliabile eseguire comunque questa attività per acquisire esperienza nella creazione di un tema, anche se potrebbe non venire salvato nel tenant di valutazione.

1. Si dovrebbe essere ancora connessi a LON-CL1 come account **adatum\administrator** locale e nel browser Edge si dovrebbe essere ancora connessi a Microsoft 365 in qualità di **amministratore MOD**. 

2. Nell'**interfaccia di amministrazione di Microsoft 365** selezionare **Team e gruppi** nel riquadro di spostamento, quindi sotto a questo selezionare **Team e gruppi attivi**. 

3. Nella pagina **Team e gruppi attivi** è disponibile una scheda per visualizzare ognuno dei tipi di gruppo. La scheda **Gruppi di Teams e Microsoft 365** viene visualizzata per impostazione predefinita. In questa scheda vengono visualizzati i gruppi di Microsoft 365 esistenti.  <br/>

    Selezionare l'opzione **+Aggiungi un gruppo di Microsoft 365** visualizzata nella barra dei menu sopra l'elenco dei gruppi di Teams e Microsoft 365. Verrà avviata la procedura guidata **Aggiungi un gruppo di Microsoft 365**. 

4. Nella procedura guidata **Aggiungi un gruppo di Microsoft 365**, nella pagina **Configura le impostazioni di base** immettere il **progetto pilota M365** nel campo **Nome**, quindi immettere i **membri del team del progetto pilota di Microsoft 365** nel campo **Descrizione** (nota: anche se non si immette una descrizione, è comunque necessario selezionare ancora da questo campo per abilitare il pulsante **Avanti**). Selezionare **Avanti**.

5. Si assegnerà ora l'amministratore MOD come proprietario del gruppo di **progetti pilota M365**. Nella finestra **Assegna proprietari** selezionare **+Assegna proprietari**.
    
6. Nel riquadro **Assegna proprietari** visualizzato selezionare la casella di controllo accanto a **Amministratore MOD**, quindi selezionare il pulsante **Aggiungi (1)** nella parte inferiore del riquadro.

7. Nella pagina **Assegna proprietari** l'amministratore MOD dovrebbe essere visualizzato come proprietario del gruppo. Selezionare **Avanti**.

8. Verranno assegnati ora membri al gruppo del progetto pilota M365. Nella pagina **Aggiungi membri**, selezionare **+Aggiungi membri**.

9. Nel riquadro **Aggiungi membri** visualizzato, selezionare le caselle di controllo accanto agli utenti seguenti (in ordine alfabetico): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **Amministratore MOD**, **Nestor Wilke** e **Patti Fernandez**. Selezionare quindi il pulsante **Aggiungi (10)** nella parte inferiore del riquadro.

10. Nella pagina **Aggiungi membri** verificare che questi 10 utenti siano elencati come membri del gruppo. Se è stato tralasciato un utente, selezionare **+Aggiungi membri** e aggiungere uno dei 10 utenti tralasciato. Quando tutti i 10 utenti sono visualizzati in questa pagina, selezionare **Avanti**.

11. Nella pagina **Modifica impostazioni**, immettere le informazioni seguenti: <br/>

    - Immettere **m365pilotproject** nel campo **Indirizzo di posta elettronica del gruppo**.
    - Nel campo **Privacy**, selezionare **Privato**.
    - Nella sezione **Aggiungi Microsoft Teams al gruppo** verificare che la casella di controllo **Crea un team per questo gruppo** sia selezionata (selezionarla se è vuota), quindi selezionare **Avanti**.

12. Nella pagina **Verifica e completa l'aggiunta del gruppo** esaminare il contenuto immesso. Se è necessario apportare modifiche, selezionare **Modifica** nell'area specifica che richiede modifiche, effettuare eventuali correzioni necessarie e selezionare **Avanti** per tornare a questa pagina. Quando tutto è corretto, selezionare **Crea gruppo**.

13. Quando viene visualizzata la finestra relativa al **gruppo di progetti pilota M365 creato**, osservare il commento nella parte superiore della pagina secondo cui potrebbero essere necessari 5 minuti prima che il nuovo gruppo venga visualizzato nell'elenco dei Gruppi attivi.  </br>

    Selezionare **Chiudi**. Questo consente di ritornare alla pagina **Gruppi e team attivi**, che dovrebbe visualizzare la scheda **gruppi di Microsoft 365 e Teams**. Poiché il gruppo di progetti pilota M365 era un gruppo di Microsoft 365, dovrebbe essere visualizzato in questa scheda. Se necessario, selezionare l'opzione **Aggiorna** sulla barra dei menu fino a visualizzare il gruppo di progetti pilota M365 nell'elenco dei gruppi di Microsoft 365 e Teams.

14. Nell’**interfaccia di amministrazione di Microsoft 365** selezionare **Impostazioni** nel riquadro di spostamento, quindi selezionare **Impostazioni organizzazione**. 

15. Nella pagina **impostazioni dell'organizzazione**, la scheda **Servizi** viene visualizzata per impostazione predefinita. Selezionare la scheda **Profilo organizzazione**.

16. Nella scheda **Profilo organizzazione** viene visualizzato l'elenco dei dati del profilo dell'organizzazione. Nell'elenco dei dati selezionare **Temi personalizzati**.

17. Nel riquadro **Personalizza Microsoft 365 per l'organizzazione** visualizzato è possibile personalizzare il tema predefinito visualizzato dagli utenti dopo aver eseguito l'accesso a Microsoft 365 e aggiungere altri temi personalizzati. Si desidera creare un nuovo tema personalizzato che si applica solo ai membri del gruppo del **progetto pilota M365** creato in precedenza, quindi occorre selezionare l'opzione **+Aggiungi tema**.

18. Nel riquadro **Nuovo tema di gruppo** visualizzato, viene visualizzata per impostazione predefinita la scheda **Generale**. Immettere il **tema del progetto pilota M365** nel campo **Nome**.

19. Selezionare all'interno del campo **Gruppi**. Nell'elenco dei gruppi visualizzato selezionare il **progetto pilota M365** se viene visualizzato nell'elenco dei gruppi. <br/>

    **Nota:** se **il progetto pilota M365** non viene visualizzato nell'elenco dei gruppi, immettere **M365** nel campo **Gruppi**. Verrà visualizzata una casella dei risultati della ricerca che visualizza il gruppo del **progetto pilota M365**. Selezionare il **progetto pilota di M365**. 

20. Selezionare la casella di controllo **Visualizza il nome visualizzato dell'utente**. Questa è l'impostazione che Holly vuole personalizzare per i membri del team del progetto pilota di M365. Questa opzione visualizza il nome dell'utente connesso accanto alle sue iniziali in ogni intestazione di finestra.
 
21. Selezionare la scheda **Logo** ed esaminarne attentamente le opzioni. Eseguire la stessa operazione per la scheda **Colori**. Osservare le varie opzioni per il tema e per la personalizzazione disponibili per l'aggiornamento. <br/>

    Ai fini di questo lab, è possibile modificare una qualsiasi delle opzioni o lasciare invariati i valori predefiniti. Nell'ambiente reale, ad esempio, è possibile aggiungere il logo dell'azienda e impostare l'immagine di sfondo come predefinita per tutti gli utenti. Per questo lab, è possibile modificare i colori per il riquadro di spostamento, il colore del testo, dell'icona e il colore principale. <br/>

    **Proseguire ed esplorare le diverse opzioni per questo tema che verranno usate dai membri del team del progetto pilota di Microsoft 365. Apportare le modifiche desiderate.** <br/>

    **Suggerimento:** l'estetica di alcuni motivi di colore distrae gli utenti. Se si modifica uno qualsiasi dei colori, è consigliabile evitare di usare colori a contrasto elevato insieme, ad esempio colori fluorescenti e colori ad alta risoluzione come rosa brillante e bianco.

22. Seleziona **Salva**. 

    **Nota:** come accennato in precedenza all'inizio di questa attività, la piattaforma presenta un problema noto nell'interfaccia di amministrazione di Microsoft 365 per cui a volte viene salvato un nuovo tema personalizzato e altre volte viene restituito un messaggio che indica che "Non è stato possibile salvare il tema. Riprovare più tardi". Questo messaggio, nel caso in cui venga visualizzato, non avrà alcun effetto sui lab futuri. Poiché il tema personalizzato non è stato salvato, il sistema non visualizzerà il nome dell'utente accanto alla sua icona o le iniziali sulla riga dell'intestazione (inoltre eventuali modifiche ai colori che potrebbero essere state apportate non verranno visualizzate). È stato comunque chiesto di eseguire questa attività anche se si potrebbe visualizzare il messaggio suddetto per acquisire l'esperienza di creazione di un tema come questo. Pertanto, se viene visualizzato questo errore, ignorare il passaggio successivo, che verifica il tema personalizzato. Tuttavia, è comunque possibile eseguire i passaggi rimanenti dopo il passaggio successivo per ottenere informazioni sul tema predefinito. Indipendentemente dal fatto che il tema personalizzato sia stato salvato, chiudere il riquadro del **tema del progetto pilota di M365**.

23. Se il tema personalizzato non è stato salvato, andare al passaggio successivo. Tuttavia, se il tema personalizzato è stato salvato, selezionare l'icona **Aggiorna** nella parte superiore della schermata, a sinistra della barra degli indirizzi. Una volta aggiornata la schermata, il nome dell'**amministratore MOD** viene visualizzato a sinistra del cerchio con le iniziali MA oppure a sinistra dell'icona selezionata per questo account dal provider di hosting del lab. Quando i membri del team del progetto pilota di Microsoft 365 accedono a Microsoft 365 questo tema personalizzato visualizza il loro nome utente, allo stesso modo in cui viene visualizzato il nome dell'amministratore MOD. 

24. Nell'elenco dei dati del profilo dell'organizzazione selezionare **Temi personalizzati**.

25. Nel riquadro **Personalizza Microsoft 365 per l'organizzazione** visualizzato osservare come viene visualizzato il **tema predefinito** e il **tema del progetto pilota di M365** (se il tema è stato salvato nel passaggio precedente). Selezionare il **tema predefinito**. 

26. Nel riquadro **Tema predefinito** si noti che l'opzione **Visualizza il nome visualizzato dell'utente** non è selezionata per il tema predefinito. Se Holly deciderà successivamente di impostare l'opzione **Visualizza il nome visualizzato dell'utente** come funzionalità permanente, selezionerà questa opzione nel riquadro **Tema predefinito** in modo che si applichi a tutti gli utenti Adatum ed eliminerà il **tema del progetto pilota di M365**. <br/>

    **Nota:** se è stato visualizzato il messaggio di errore "Non è stato possibile salvare il tema. Riprovare più tardi". durante il tentativo precedente di salvare il tema personalizzato, selezionare l'opzione **Visualizza il nome visualizzato dell'utente** nel tema predefinito, quindi selezionare **Salva**. È opportuno comprendere ciò che accade quando questa opzione è selezionata, anche se non è stato possibile salvare il tema personalizzato. Se si imposta questa opzione sul tema predefinito, selezionare l'icona **Aggiorna** nella parte superiore della schermata, a sinistra della barra degli indirizzi. Una volta aggiornata la schermata, il nome dell'**amministratore MOD** viene visualizzato a sinistra del cerchio con le iniziali MA oppure a sinistra dell'icona selezionata per questo account dal provider di hosting del lab.
 
27. Chiudere il riquadro **Tema predefinito**.

28. Rimanere connessi a **LON-CL1** con Microsoft Edge aperto sull'**interfaccia di amministrazione di Microsoft 365** per l'attività successiva.

### Attività 3. Installare Microsoft Graph PowerShell 

Microsoft Graph PowerShell è necessario per eseguire diverse attività di configurazione durante l'installazione di Microsoft 365. Poiché gli esercizi futuri del lab eseguiranno diverse attività di questo tipo usando Windows PowerShell, è consigliabile iniziare dall'installazione del modulo Microsoft Graph PowerShell. Questo modulo consente di eseguire molte delle attività di amministrazione dell'utente e dell'organizzazione di Microsoft 365 tramite PowerShell. È ideale per le attività in blocco, ad esempio la reimpostazione delle password, i criteri delle password, la gestione delle licenze, la creazione di report e altro ancora.  

1. In LON-CL1, si dovrebbe comunque essere connessi come account **adatum\administrator** locale. Per installare Microsoft Graph PowerShell, è necessario aprire un'istanza con privilegi elevati di **Windows PowerShell**. Digitare **alimentazione** nella casella di ricerca visualizzata nell'angolo in basso a sinistra della barra delle applicazioni. Nell'elenco dei risultati della ricerca fare clic con il pulsante destro del mouse su **Windows PowerShell** (non selezionare Windows PowerShell ISE) e scegliere **Esegui come amministratore** nel menu a discesa visualizzato. 

2. Ingrandire la finestra di PowerShell. In **Windows PowerShell**, digitare il comando seguente al prompt dei comandi per installare il modulo Microsoft Graph PowerShell, quindi premere INVIO: <br/>

        Install-Module Microsoft.Graph -Scope CurrentUser

3. Viene richiesto di confermare che si vuole installare il modulo da un repository non attendibile (PSGallery). Immettere **A** per selezionare **[A] Sì a tutti** e quindi premere INVIO.  <br/>

    **Nota:** la risposta avvierà l'installazione di tutti i moduli secondari di Microsoft Graph. Al termine della visualizzazione di tutti i messaggi di installazione per ogni modulo secondario, il completamento dell'installazione di Microsoft Graph PowerShell richiederà circa altri 5-10 minuti. Nel frattempo, il cursore continuerà a lampeggiare sotto il messaggio del repository non attendibile. <br/>

    **Potrebbe essere un buon momento per fare una breve pausa.**

4. Un prompt dei comandi verrà visualizzato dopo l'installazione di Microsoft Graph PowerShell. Verrà ora visualizzato l'elenco dei moduli secondari installati. A tale scopo, eseguire il comando seguente:

        Get-InstalledModule Microsoft.Graph.* | select *name*

5. Verificare che l'elenco dei moduli secondari installati includa i tre moduli secondari seguenti, che verranno usati negli esercizi del lab successivi: 

    - Microsoft.Graph.Groups
    - Microsoft.Graph.Identity.DirectoryManagement
    - Microsoft.Graph.Users
    
    Se tutti e tre i moduli secondari vengono visualizzati nell'elenco dei moduli secondari installati, procedere con il passaggio successivo. Tuttavia, se uno di questi tre moduli secondari non viene visualizzato nell'elenco, eseguire il comando di PowerShell seguente per installare manualmente il modulo secondario mancante:

        Install-Module -Name <module name> -Scope CurrentUser

    Ad esempio, se il modulo Microsoft.Graph.Identity.DirectoryManagement non è stato installato, eseguire il comando seguente:

        Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. Le impostazioni dei criteri di esecuzione di PowerShell determinano quali script di PowerShell possono essere eseguiti in un sistema Windows. L'impostazione di questo criterio su **Senza restrizioni** consente a Holly di caricare tutti i file di configurazione ed eseguire tutti gli script. Al prompt dei comandi digitare il comando seguente e quindi premere INVIO:   <br/>

        Set-ExecutionPolicy unrestricted

    Se viene richiesto di verificare di voler modificare i criteri di esecuzione, immettere **A** per selezionare **[A] Sì a tutti.** 

7. Lasciare aperta la finestra di PowerShell, ma ridurla a icona. Verrà usata in un esercizio del lab successivo.


**Congratulazioni! Sono stati completati tutti i passaggi per inizializzare il tenant del lab. Ora è possibile eseguire gli esercizi del lab rimanenti.**

# Fine del lab 1
