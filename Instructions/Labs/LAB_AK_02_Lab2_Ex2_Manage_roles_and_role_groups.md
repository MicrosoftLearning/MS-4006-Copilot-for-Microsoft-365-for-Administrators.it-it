# Percorso di apprendimento 2 - Lab 2 - Esercizio 2: Gestire ruoli e gruppi di ruoli

In questo esercizio si continuerà a svolgere il ruolo di Holly Dickson, il nuovo amministratore Microsoft 365 di Adatum. Come parte del progetto pilota di Microsoft 365 di Adatum, la delega di amministrazione verrà gestita assegnando i ruoli di amministratore Microsoft 365 a diversi account utente di Microsoft 365 creati precedentemente dal provider di hosting del lab. Questo esercizio fornirà esperienza nell'uso di tre diversi metodi per assegnare questi ruoli: 1) assegnando un ruolo direttamente a un account utente nella interfaccia di amministrazione di Microsoft 365, 2) creando un gruppo di ruoli, assegnando i ruoli al gruppo di ruoli e assegnando quindi il gruppo di ruoli a un utente nell'interfaccia di amministrazione di Microsoft 365 e infine 3) assegnando un ruolo a un utente tramite Windows PowerShell. Dopo aver assegnato i ruoli di amministratore di Microsoft 365 a diversi account utente esistenti, si verificheranno quindi le assegnazioni verificando che gli utenti abbiano le autorizzazioni necessarie per agire in conformità ai ruoli. 


### Attività 1: assegnare un ruolo di amministratore nell'interfaccia di amministrazione di Microsoft 365

A Holly Dickson è stato assegnato il ruolo di amministratore globale di Microsoft 365. Continuando nel ruolo di Holly, verrà utilizzata l'interfaccia di amministrazione di Microsoft 365 per assegnare i diritti di amministratore a uno degli utenti di Adatum. In questa attività verrà assegnato il ruolo di amministratore fatturazione all'account utente di Diego Siciliani.

1. L'esercizio precedente del lab è stato completato su LON-DC1. È ora necessario tornare a **LON-CL1** per eseguire le attività amministrative di Microsoft 365 in questo esercizio lab. Come procedura consigliata, le tipiche attività amministrative di Microsoft 365 devono essere eseguite su un PC client anziché sul controller di dominio dell'azienda.  <br/>

    Passare a **LON-CL1**. 

2. In **LON-CL1**, nell'**interfaccia di amministrazione di Microsoft 365** aperta nel browser Edge, dovrebbe essere ancora attiva la connessione come Holly Dickson da un esercizio lab precedente. Nel riquadro di spostamento, selezionare **Utenti**, quindi **Utenti attivi**. 

3. Selezionare **Diego Siciliani** dall'elenco **Utenti attivi**.  <br/>

    **Nota:** selezionare il nome Diego; non selezionare la casella di controllo a sinistra del suo nome. La casella di controllo solitamente viene usata per la selezione di più utenti quando si desidera eseguire una delle azioni relative all'utente nella barra dei menu visualizzata sopra l'elenco degli utenti, ad esempio **Gestisci licenze prodotto** e **Gestisci ruoli**. Selezionando il nome di un utente, verrà aperto il riquadro delle proprietà specifico per tale utente.

4. Nel riquadro **Diego Siciliani** visualizzato, la scheda **Account** viene mostrata per impostazione predefinita. Scorrere verso il basso in questa scheda fino alla sezione **Ruoli** e selezionare **Gestisci ruoli**. 

5. Nella finestra **Gestisci ruoli di amministratore** l'opzione **Utente (nessun accesso all'interfaccia di amministrazione)** è attualmente selezionata per impostazione predefinita. Poiché si desidera assegnare a Diego un ruolo di amministratore, selezionare l'opzione **Accesso all'interfaccia di amministrazione**. In questo modo viene abilitato un elenco di ruoli di amministratore di uso comune da cui effettuare la selezione. 

6. Diego è stato promosso ad Amministratore fatturazione, ma poiché questo ruolo non viene visualizzato nell'elenco dei ruoli di uso comune, scorrere verso il basso e selezionare **Mostra tutto per categoria**. 

7. Nell'elenco dei ruoli ordinati per categoria scorrere verso il basso fino alla categoria **Altro**, selezionare la casella di controllo **Amministratore fatturazione** e quindi selezionare **Salva modifiche**. <br/>

    **Suggerimento:** notare il messaggio visualizzato nella parte superiore del riquadro dopo il salvataggio della modifica del ruolo di amministratore. Il messaggio fornisce la procedura consigliata riportata di seguito da ricordare quando si gestiscono i ruoli amministrativi nelle distribuzioni reali: **concedere agli utenti solo l'accesso necessario assegnando il ruolo meno permissivo.**

8. Nella finestra **Gestisci ruoli di amministratore**, selezionare la **X** nell'angolo superiore destro della schermata per chiuderla. Questo consente di ritornare all'elenco **Utenti attivi**. 

9. Rimanere connessi a LON-CL1 e all'interfaccia di amministrazione di Microsoft 365 come Holly Dickson.

### Attività 2: assegnare un ruolo di amministratore tramite un gruppo di ruolo nell'interfaccia di amministrazione di Microsoft 365

Nell'attività precedente è stato assegnato un ruolo di amministratore direttamente all'account utente di Diego Siciliani dall'interfaccia di amministrazione di Microsoft 365. In questa attività i ruoli saranno invece assegnati usando un gruppo di ruoli. Verrà creato un gruppo di ruolo di sicurezza a cui verranno assegnati i ruoli di gestione degli utenti, quindi verrà assegnato il gruppo di ruolo all'account utente di Lynne Robbin nell'interfaccia di amministrazione di Microsoft 365.

1. In LON-CL1 dovrebbe essere ancora attiva la connessione di Holly Dickson all'interfaccia di amministrazione di Microsoft 365. In caso contrario, procedere ora.

2. Nell'**interfaccia di amministrazione di Microsoft 365**, selezionare **Team e gruppi** nel riquadro di spostamento, quindi selezionare **Team e gruppi attivi**. 

3. Nella pagina **Team e gruppi attivi** la scheda **Team e gruppi di Microsoft 365** viene visualizzata per impostazione predefinita. Selezionare la scheda **Gruppi di sicurezza**.

4. Nella scheda **Gruppi di sicurezza** selezionare **+Aggiungi un gruppo di sicurezza** dalla barra dei menu. In questo modo viene avviata la procedura guidata **Aggiungi un gruppo di sicurezza**.

5. Nella procedura guidata **Aggiungi un gruppo di sicurezza**, nella pagina **Configura le impostazioni di base** immettere **Gruppo di ruoli gestione utente** nel campo **Nome**. Immettere **Questo gruppo di ruoli contiene i ruoli di gestione degli utenti** nel campo **Descrizione**. Selezionare **Avanti**.

6. Nella pagina **Modifica impostazioni** selezionare la casella di controllo **Ruoli di Azure AD che possono essere assegnati al gruppo**, quindi selezionare **Avanti**.

7. Nella pagina **Rivedi e termina l'aggiunta del gruppo**, verificare le impostazioni. Se è necessario modificare alcune impostazioni, selezionare l'opzione **Modifica** appropriata e procedere. Quando tutte le impostazioni sono corrette, selezionare **Crea gruppo**.

8. Dopo aver creato il **gruppo di ruoli Gestione utenti**, selezionare **Chiudi**.

9. Dopo aver creato il gruppo di ruoli, è necessario assegnargli i ruoli corrispondenti. Nella pagina **Team e gruppi attivi** viene visualizzata la scheda **Gruppi di sicurezza**. Selezionare il **Gruppo di ruoli gestione utenti ** per aprire il relativo riquadro dei dettagli.

10. Nel riquadro **Gruppo di ruoli gestione utenti** viene visualizzata per impostazione predefinita la scheda ** Generale**. Selezionare **Gestisci ruoli** in **Ruoli**.

11. Nel riquadro **Gestire ruoli di amministratore** visualizzato, selezionare l'opzione **Accesso all'interfaccia di amministrazione **. Nell'elenco dei ruoli di amministratore comuni visualizzati direttamente sotto questa opzione, selezionare le caselle di controllo **Amministratore utenti** e **Responsabile del successo dell'esperienza utente** . Quindi, selezionare l'opzione **Mostra tutti per categoria**. Scorrere verso il basso fino alla categoria **Identità**. Si noti che il ruolo **Amministratore utenti** è già selezionato, poiché è stato selezionato in precedenza nell'elenco dei ruoli di uso comune. In questa categoria **Identità** selezionare il ruolo **Amministratore di supporto tecnico**, quindi selezionare **Salva modifiche**. 

12. Nel riquadro **Gestire ruoli di amministratore** i tre ruoli selezionati dovrebbero essere visualizzati sotto l'opzione **Accesso all'interfaccia di amministrazione**. Selezionare la **X** nell'angolo in alto a destra del riquadro per chiuderlo.

13. Nella scheda **Gruppi di sicurezza** selezionare **Gruppo di ruoli gestione utenti**. Nel riquadro **Gruppo di ruoli gestione utenti** visualizzato verificare che i tre ruoli siano visualizzati nella sezione **Ruoli**. Chiudere questo riquadro.

14. Dopo aver assegnato i ruoli al gruppo di ruoli, è necessario assegnare il gruppo di ruoli all'account utente di Lynne Robbin. Nell'**interfaccia di amministrazione di Microsoft 365** selezionare **Utenti attivi**.

15. Nella pagina **Utenti attivi** selezionare **Lynne Robbins**. 

16. Nel riquadro **Lynne Robbins** viene visualizzata per impostazione predefinita la **scheda Account**. Nell'attività precedente, quando è stato assegnato il ruolo Amministratore fatturazione all'account di Diego Siciliani, è stata selezionata l'opzione **Gestisci ruoli** nella sezione **Ruoli**. Tuttavia, poiché si assegneranno i ruoli di Lynne tramite un gruppo di ruoli, è necessario assegnare Lynne come membro del gruppo di ruoli Sicurezza appena creato. È attraverso l'assegnazione di gruppo che Lynne erediterà i ruoli assegnati al gruppo di ruoli. Di conseguenza, nella sezione **Gruppi** selezionare **Gestisci gruppi**. 

17. Nel riquadro **Gestisci gruppi** selezionare **+Assegna appartenenze**.

18. Nel riquadro **Assegna appartenenza** selezionare la casella di controllo **Gruppo di ruolo gestione utenti**, quindi selezionare **Aggiungi(1)**.

19. Una volta visualizzata una notifica **salvata** nella parte superiore della pagina, chiudere questo riquadro. 

20. Per verificare che Lynne abbia ereditato i ruoli assegnati al gruppo di ruoli di gestione utenti, selezionare **Lynne Robbins** dall'elenco degli utenti attivi. 

21. Nel riquadro **Lynne Robbins**, nella scheda **Account** visualizzata per impostazione predefinita, dovrebbero essere visualizzati i tre ruoli di gestione utenti assegnati a Lynne. Selezionare **Gestisci ruoli** in **Ruoli**.

22. Nel riquadro **Gestire ruoli di amministratore** visualizzato, nell'opzione **Accesso all'interfaccia di amministrazione** osservare i tre ruoli selezionati e il nome del gruppo da cui sono stati assegnati a Lynne. Si noti anche che i tre ruoli sono disattivati. Ciò indica che non è possibile deselezionarli da questa finestra. Poiché i ruoli sono stati assegnati a Lynne da un gruppo di ruoli che li conteneva, è possibile annullare l'assegnazione dei ruoli solo rimuovendo Lynne come membro del gruppo di ruoli. Hai appena verificato che Lynne sia assegnata a questi ruoli. Chiudere questo riquadro **Gestire ruoli di amministratore**.

23. Rimanere connessi a LON-CL1 e all'interfaccia di amministrazione di Microsoft 365 come Holly Dickson.

### Attività 3. Assegnare un ruolo di amministratore tramite Windows PowerShell  

In questa attività si userà Windows PowerShell per assegnare un ruolo a un account utente. In questo modo si proverà ad eseguire questa funzione di gestione in PowerShell, poiché alcuni amministratori preferiscono eseguire questo tipo di manutenzione con PowerShell.  

In questa attività Holly vuole assegnare a Patti Fernandez il ruolo di amministratore del supporto del servizio. Per aggiungere un utente a un ruolo di amministratore usando il modulo Microsoft Graph PowerShell, è prima necessario ottenere l'ID oggetto dell'utente e l'ID oggetto del ruolo. Se il ruolo non è ancora stato abilitato (ovvero non è stato assegnato a un utente o non è stato abilitato fisicamente), è necessario abilitare il ruolo prima di poterlo assegnare a un utente tramite PowerShell. In questa attività, verrà abilitato il ruolo Amministratore del supporto del servizio prima di assegnarlo a Patti Fernandez.

PowerShell consente anche di visualizzare tutti gli utenti assegnati a un ruolo specifico, possibilità che può essere molto importante quando si verifica la distribuzione di Microsoft 365. In questa attività si apprenderà anche come usare PowerShell per visualizzare tutti gli utenti assegnati a un ruolo specifico. 

1. In LON-CL1 selezionare l'icona di Windows PowerShell sulla barra delle applicazioni, rimasta aperta da un lab precedente. Se la finestra di PowerShell è stata chiusa, aprire un'istanza con privilegi elevati usando la stessa istruzione di prima. 

2. La sessione di PowerShell deve comunque essere connessa a Microsoft Graph PowerShell dal lab precedente in cui è stato recuperato un gruppo eliminato tramite PowerShell. Tuttavia, se PowerShell è stato chiuso in precedenza ed è stato appena riaperto, importare il sottomodulo Microsoft.Graph.Identity.DirectoryManagement seguendo i passaggi dell'esercizio lab precedente. 

3. Per eseguire attività di manutenzione utente di Microsoft 365 in Microsoft Graph PowerShell, è necessario importare prima il sottomodulo Microsoft.Graph.Users e richiedere autorizzazioni di lettura/scrittura. Per importare questo modulo secondario, al prompt dei comandi digitare il comando seguente, quindi premere INVIO:   <br/>

        Import-Module Microsoft.Graph.Users

4. Nell'esercizio del lab precedente è stata effettuata la connessione a Microsoft Graph e sono state richieste le autorizzazioni "Directory.ReadWrite.All" per eseguire i cmdlet che hanno ripristinato il gruppo eliminato. Per aggiornare gli oggetti Utente e ruolo in questa attività, Holly deve ora richiedere le autorizzazioni di lettura/scrittura per ogni oggetto. Per richiedere tali autorizzazioni, al prompt dei comandi digitare il comando seguente, quindi premere INVIO:  <br/>

        Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

5. Nella finestra **Scegli un account** visualizzata, selezionare l'account di Holly Dickson. 

6. Nella finestra di dialogo **Autorizzazioni richieste** visualizzata, selezionare la casella di controllo **Consenso per conto dell'organizzazione** e quindi selezionare **Accetta**.

7. Holly vuole assegnare **Patti Fernandez** al ruolo di **Amministratore del supporto dei servizi**. Per assegnare questo ruolo tramite PowerShell di Microsoft Graph, è prima necessario ottenere l'ID oggetto del ruolo Amministratore del supporto dei servizi in modo che sia possibile assegnarlo a Patti. In PowerShell di Microsoft Graph è tuttavia possibile assegnare solo i ruoli che sono stati "abilitati". I ruoli abilitati sono quei ruoli che sono stati abilitati da un modello di ruolo oppure che sono già stati assegnati agli utenti tramite PowerShell o l'interfaccia di amministrazione di Microsoft 365. <br/>

    **Importante:** prima di eseguire questo passaggio, verificare che la finestra di PowerShell sia in modalità schermo intero. Il nome del ruolo viene visualizzato nella colonna finale nell'estremità destra della schermata. Se non si è in modalità schermo intero, non verrà visualizzato il nome del ruolo associato a ogni ID oggetto. 

    Per visualizzare tutti i ruoli abilitati in Microsoft 365, al prompt dei comandi immettere il comando seguente, quindi premere INVIO: <br/>
    
        Get-MgDirectoryRole    <br/>

    **Nota:** questo comando visualizza i ruoli che sono stati abilitati finora in Microsoft 365. Se in questo elenco è presente il ruolo di Amministratore del supporto dei servizi, è possibile procedere direttamente con il passaggio 13 per assegnare il ruolo a Patti. Tuttavia, poiché l'Amministratore del supporto dei servizi non è incluso in questo elenco di ruoli abilitati, è necessario eseguire i passaggi da 8 a 12 per abilitare il ruolo dal modello di ruolo corrispondente, prima di poter assegnare Patti al ruolo nel passaggio 13. 

8. Per abilitare un ruolo in PowerShell di Microsoft Graph, è prima necessario individuare il modello per ottenere l'ID oggetto del modello. È necessario conoscere l'ID oggetto del modello per abilitare il ruolo dal modello. Esistono due modi in cui è possibile visualizzare i modelli di ruolo: mediante la visualizzazione dell'intero elenco di modelli di ruolo oppure del solo modello per un ruolo specifico. Come esperienza di apprendimento, verranno eseguiti entrambi i metodi in modo da poterne comprendere le differenze. <br/>

    Per iniziare, verrà visualizzato l'elenco completo dei modelli di ruolo insieme al relativo ID oggetto e al nome visualizzato. A tale scopo, digitare il comando seguente e quindi premere INVIO: <br/>

        Get-MgDirectoryRoleTemplate | Format-List Id, DisplayName   <br/>

    Come si può vedere dopo aver eseguito questo comando, è necessario scorrere l'elenco dei modelli di ruolo per cercare il ruolo Amministratore del supporto dei servizi. È facile notare che si tratta di un'operazione noiosa. In alternativa, utilizzare il comando seguente per eseguire una query per uno specifico modello di ruolo, in questo caso il modello di ruolo "Amministratore del supporto dei servizi": <br/>

        Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator"   <br/>

    Dopo aver eseguito questo comando, è possibile osservare che viene visualizzato solo il modello di ruolo richiesto. Ovviamente, possono verificarsi situazioni in cui è necessario visualizzare l'intero elenco di modelli di ruolo. Tuttavia, quando è necessario cercare un singolo modello di ruolo, l'esecuzione del secondo comando di PowerShell sarà molto più efficiente rispetto a scorrere l'intero elenco di modelli.
    
9. Dopo aver eseguito la query sul modello di ruolo Amministratore del supporto dei servizi nel passaggio precedente, evidenziare il relativo **ID** (ad esempio, fe930be7-5e62-47db-91af-98c3a49a38b1) e premere **CTRL+C** per copiarlo negli Appunti (l'evidenziazione scompare durante la copia).

10. Verrà quindi creata una variabile che acquisisce gli attributi per il modello Amministratore del supporto dei servizi. Quando si digita il comando seguente, premere **CTRL+V** per incollare l'ID modello Amministratore del supporto dei servizi copiato negli Appunti nel passaggio precedente. <br/>

    Al prompt dei comandi, digitare il seguente comando e premere Invio: <br/>

        $ServiceSupportRoleTemplate = @{ RoleTemplateID = "paste in template ID here" }  <br/>

    Ad esempio: $ServiceSupportRoleTemplate = @{ RoleTemplateID = "fe930be7-5e62-47db-91af-98c3a49a38b1" }

11. È ora possibile abilitare il ruolo Amministratore del supporto dei servizi in base agli attributi del modello acquisiti nella variabile $ServiceSupportRoleTemplate. Digitare il comando seguente e premere INVIO:  <br/>

        New-MgDirectoryRole -BodyParameter $ServiceSupportRoleTemplate

12. Per verificare che il ruolo Amministratore del supporto dei servizi sia stato abilitato, digitare il comando seguente e premere INVIO. Questo comando consente di visualizzare l'elenco dei ruoli abilitati:  <br/>
            
        Get-MgDirectoryRole <br/>

    **Nota:** il comando visualizza l'ID oggetto di tutti i ruoli abilitati, incluso il ruolo Amministratore del supporto dei servizi appena abilitato dal relativo modello. Successivamente nel passaggio 15 verrà copiato e incollato l'ID oggetto del ruolo Amministratore del supporto dei servizi quando Patti verrà assegnata al ruolo.

13. Per assegnare Patti Fernandez al ruolo Amministratore del supporto dei servizi appena abilitato, è prima necessario ottenere l'ID oggetto per l'account utente di Patti. A tale scopo, digitare il comando seguente e premere INVIO: <br/>

        Get-MgUser | Format-List ID, DisplayName

14. Ora che sono entrambi noti l'ID oggetto del ruolo Amministratore del supporto dei servizi recentemente abilitato e l'ID oggetto dell'account utente di Patti, è possibile assegnare il ruolo a Patti. Per completare il processo, seguire questa procedura: <br/>

    a. Nel comando precedente è stato visualizzato l'elenco degli utenti attivi. Evidenziare l'**ID** per l'account di Patti e copiarlo (**CTRL+C**) negli Appunti. L'evidenziazione scompare dopo la copia negli Appunti.  <br/>

    b. Eseguire il comando seguente per creare una variabile contenente l'oggetto directory per l'account utente di Patti. Quando si digita questo comando, incollare (**CTRL+V**) l'ID appena copiato per l'account utente di Patti. <br/>

        $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/paste in Patti's user account ID here" }  <br/>

    Ad esempio: $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/22fddbf7-42d2-4698-be65-ebc972a023e3" }

    c. Nel passaggio 12 è stato visualizzato l'elenco dei ruoli abilitati. Evidenziare l'ID per il ruolo Amministratore del supporto del servizio e copiarlo (**CTRL+C**) negli Appunti. <br/>

    d. Eseguire il comando seguente che assegna la variabile contenente l'account utente di Patti ($UserObject) al ruolo della directory. Quando si digita questo comando, incollare (**CTRL+V**) l'ID appena copiato per il ruolo Amministratore del supporto del servizio. <br/> 

        New-MgDirectoryRoleMemberByRef -DirectoryRoleId 'paste in the ID of the role here' -BodyParameter $UserObject
                
15. Si vuole ora verificare che Patti sia stato assegnato al ruolo Amministratore del supporto del servizio. In precedenza è stato copiato l'ID oggetto di questo ruolo negli Appunti ed è stato incollato nel comando precedente. È consigliabile incollarlo anche in questo comando. Digitare il comando seguente e premere INVIO:
    
        Get-MgDirectoryRoleMember -DirectoryRoleId 'paste in the ID of the role here' 
                
16. Il comando precedente visualizza solo gli ID degli utenti assegnati al ruolo selezionato. Tuttavia, è possibile associare l'ID visualizzato all'ID di Patti per verificare che al suo account sia stato assegnato il ruolo di **Amministratore del supporto del servizio**. Come si può notare, Patti è l'unico utente assegnato al ruolo. 

17. Ripetere ora questo processo per visualizzare tutti gli utenti assegnati al ruolo di amministratore globale. Ripetere il passaggio 15 per verificare il numero di utenti Adatum assegnati al ruolo di **amministratore globale**. Per completare questo comando, è prima necessario copiare (**CTRL+C**) l'ID del ruolo di amministratore globale negli Appunti. È possibile trovare questo ID nell'elenco dei ruoli abilitati durante l'esecuzione del passaggio 12. <br/>

    **Avviso:** copiare l'ID del ruolo di amministratore globale e NON l'ID del modello di ruolo di amministratore globale.

18. Verificare che siano presenti più utenti Adatum a cui è stato assegnato il ruolo di amministratore globale. In uno scenario reale, l'amministratore di Microsoft 365 potrebbe usare questo comando di PowerShell per monitorare il numero di amministratori globali presenti nella distribuzione di Microsoft 365. Quindi rimuoverebbe il ruolo di amministratore globale da tutti gli utenti che effettivamente non dovrebbero averlo (tenere presente che le linee guida consigliate indicano di avere tra 2 e 4 amministratori globali in una distribuzione di Microsoft 365, a seconda delle dimensioni dell'organizzazione).  <br/>

    Nel caso di questo lab, mentre il provider di hosting del lab ha assegnato il ruolo di amministratore globale a utenti diversi dall'amministratore MOD (e si è assegnato tale ruolo a Holly Dickson), questi utenti saranno lasciati invariati. In questa distribuzione fittizia di Adatum non è necessario perdere tempo rimuovendo questo ruolo dai propri account. Inoltre, alcune delle attività future del lab si basano sul fatto che a questi utenti venga assegnato il ruolo di amministratore globale. <br/>

    **IMPORTANTE:** tenere presente che nella distribuzione reale l'amministratore di Microsoft 365 dovrebbe monitorare periodicamente il ruolo di amministratore globale per mantenere il numero di utenti assegnati tra 2 e 4.
    
19. Lasciare aperta la sessione di Windows PowerShell per gli esercizi futuri del lab, ma ridurla al minimo prima di passare all'attività successiva.


### Attività 4. Convalidare le assegnazioni di ruoli 

In questa attività si inizierà esaminando le proprietà amministrative di due utenti, Joni Sherman e Lynne Robbins. Si accederà quindi alla home page di Microsoft 365 nella macchina virtuale Client 2 (LON-CL2) come utente, per confermare alcune delle modifiche apportate durante la gestione delle loro deleghe amministrative nelle attività precedenti. Infine, in qualità di Lynne Robbins, si eseguiranno due importanti attività di manutenzione dell'account utente: reimpostazione delle password e blocco degli account utente.

1. In LON-CL1 dovrebbe essere ancora attiva la connessione di Holly Dickson all'interfaccia di amministrazione di Microsoft 365. In caso contrario, procedere ora.

2. Nell'**interfaccia di amministrazione di Microsoft 365**, se non sono visualizzati gli **utenti attivi**, passare alla rispettiva pagina.  

3. Nell'elenco **Utenti attivi** selezionare **Joni Sherman**. 

4. Nella finestra delle proprietà di **Joni Sherman** viene visualizzata per impostazione predefinita la scheda **Account**. Nella sezione **Ruoli** occorre indicare che Joni non ha **Nessun accesso di amministratore**. Fare clic sulla **X** nell'angolo in alto a destra per chiudere la finestra delle proprietà relative a Joni.

5. Nell'elenco **Utenti attivi** selezionare **Lynne Robbins**. 

6. Nella finestra delle proprietà di **Lynne Robbins** dovrebbe essere indicato che a Lynne è stato assegnato il ruolo di **amministratore utente**. Chiudere la finestra delle proprietà relative a Lynne.

7. Passare alla macchina virtuale Client 2 (**LON-CL2**).

8. Nella schermata di accesso di **LON-CL2** accedere come account **amministratore** locale con la password **Pa55w.rd**.

9. Se viene visualizzata la finestra **Reti**, selezionare **Sì**.

10. Sulla barra delle applicazioni selezionare l'icona di **Microsoft Edge**. Ingrandire la finestra del browser Edge, se necessario.

11. Nel browser **Edge** passare a **https://portal.office.com**. 

12. Si inizierà accedendo a Microsoft 365 come **Joni Sherman**. Nella finestra **Accedi** immettere **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal proprio provider di hosting del lab). Avendo eseguito l'accesso come Joni Sherman, immettere questa **password utente** fornita dal provider di hosting del lab nella finestra **Immettere la password**. <br>

    Nella finestra di dialogo **Aggiorna la password**, immettere la **password utente** fornita dal provider di hosting del lab nel campo **Password attuale**. Quindi, immettere la nuova password utente nei campi **Nuova password** e **Conferma password** e selezionare **Accedi**.

13. Nella finestra **Rimanere connessi?** selezionare la casella di controllo **Non visualizzare più questo messaggio**, quindi selezionare **Sì**. Se viene visualizzata la finestra **Salva password**, selezionare **Mai**.

14. Se al centro della pagina viene visualizzata la finestra di dialogo **Benvenuto in Microsoft 365**, selezionare due volte la freccia in avanti (>) e quindi il segno di spunta per chiuderla.

15. Se viene visualizzata la finestra **Trova altre app** o la finestra **Crea con Microsoft 365** o qualsiasi altra finestra di tipo introduttivo, selezionare la **X** nell'angolo superiore della finestra per chiuderla.

16. Nella finestra **Benvenuto in Microsoft 365**, ovvero la home page di Microsoft 365 di Joni, viene visualizzato un riquadro di spostamento sul lato della schermata che indica le applicazioni a cui l'utente ha l'autorizzazione per accedere. In questo riquadro **App** si noti come l'opzione **Admin** non viene visualizzata. Il motivo è che a Joni non è mai stato assegnato un ruolo di amministratore di Microsoft 365. 

17. Si dovrà quiindi effettuare la disconnessione da Microsoft 365 come Joni. In **Microsoft Edge**, in alto a destra della pagina **Benvenuto in Microsoft 365**, selezionare l'icona utente corrispondente per **Joni Sherman** (il cerchio nell'angolo superiore con l'immagine di Joni) e, nella finestra **Joni Sherman** visualizzata, selezionare **Esci.** 

18. Accedere ora nuovamente a Microsoft 365 come **Lynne Robbins**. Nella scheda del browser **Edge** corrente dovrebbe essere visualizzato un messaggio che indica **Joni, ti sei disconnesso.** In questa finestra è possibile accedere di nuovo come Joni o accedere come un altro utente. <br/>

    Selezionare **Passa a un altro account** e nel campo **Indirizzo di posta elettronica** visualizzato immettere **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (in cui xxxxxZZZZZZ è il prefisso del tenant fornito dal provider di hosting del lab), quindi selezionare **Accedi.** Nella finestra **Immettere la password**, immettere la **password utente** fornita dal provider di hosting del lab e selezionare **Accedi**. <br>

    Nella finestra di dialogo **Aggiorna la password**, immettere la **password utente** fornita dal provider di hosting del lab nel campo **Password attuale**. Quindi, immettere la nuova password utente nei campi **Nuova password** e **Conferma password** e selezionare **Accedi**. 

19. Se viene visualizzata la finestra di dialogo **Benvenuto in Microsoft 365**, selezionare due volte la freccia in avanti (>) e quindi il segno di spunta per chiudere la finestra.

20. Se viene visualizzata la finestra **Trova altre app** o la finestra **Crea con Microsoft 365** o qualsiasi altra finestra di tipo introduttivo, selezionare la **X** nell'angolo superiore della finestra per chiuderla.

21. Nella finestra **Benvenuto in Microsoft 365**, ovvero la home page di Microsoft 365 di Lynne, si noti che nel riquadro di spostamento sul lato della schermata è visualizzata l'icona **Amministratore**. Questa icona viene visualizzata perché a Lynne è stato assegnato un ruolo di amministratore di Microsoft 365. Selezionare l'icona **Amministratore** per aprire l'interfaccia di amministrazione di Microsoft 365.

22. Nell'**interfaccia di amministrazione di Microsoft 365**, selezionare **Utenti** nel riquadro di spostamento, quindi **Utenti attivi**. 

23. Come **Amministratore utenti**, Lynne ha l'autorizzazione per modificare le password utente. Lynne è stata recentemente contattata da **Diego Siciliani** e da **Pradeep Gupta**, che hanno riferito entrambi che le loro password potrebbero essere compromesse. Per i criteri aziendali di Adatum, Lynne deve reimpostare le password su un valore temporaneo e quindi forzare gli utenti a reimpostarle al successivo accesso.   <br/>

    Nell'elenco **Utenti attivi**, spostando il mouse da un account utente a un altro, osservare l'icona **della chiave (Reimposta una password)** visualizzata a destra del nome di ogni utente. Selezionare l'icona a forma di chiave visualizzata a destra del nome di **Diego Siciliani**.

24. Nella finestra **Reimposta una password** per Diego, se nella casella di controllo **Crea automaticamente una password** è presente un segno di spunta, selezionare la casella per deselezionarlo. Ciò consentirà a Lynne di assegnare manualmente a Diego una password temporanea.  

25. Immettere **diego** nel campo **Password**. Si noti che a destra della password il sistema visualizza un messaggio che indica che si tratta di una password **debole**. Osservare anche il messaggio visualizzato sotto il campo che indica i requisiti per una password complessa. Infine, si noti che il pulsante **Reimposta una password** nella parte inferiore del riquadro non è abilitato. **Questo pulsante verrà abilitato solo dopo aver immesso una password complessa**.  

26. Verificare che la casella di controllo **Richiedi a questo utente di modificare la propria password al primo accesso** sia selezionata (in caso contrario selezionarla per visualizzare un segno di spunta). Immettere **Pa55w.rd** nel campo **Password**. Si noti che il campo **Password** indica che si tratta di una password complessa. <br/>

    Tuttavia, fare clic sulla casella di controllo **Richiedi a questo utente di modificare la password al primo accesso** per deselezionarla. Si noti il messaggio di errore visualizzato che indica che la password (Pa55w.rd) contiene una parola, una frase o una serie di numeri che la rende facilmente individuabile. In questo caso, è stata immessa una variante della parola **password**, che attiva questo errore. Il sistema consente di immettere questa password se si forza l'utente a modificarla al primo accesso. Tuttavia, se non si forza l'utente a immettere una password diversa al primo accesso, questa password non è consentita.

27. Dopo questi due tentativi non riusciti di immissione di una password, Lynne ha deciso di lasciare che Microsoft 365 generi automaticamente una password. Selezionare la casella di controllo **Crea automaticamente una password** in modo da visualizzare un segno di spunta. 
    
28. La password generata automaticamente sarà solo una password temporanea perché Lynne vuole forzare Diego a modificarla al successivo accesso. Verificare quindi che la casella di controllo **Richiedi all'utente di cambiare la password al primo accesso** visualizzi un segno di spunta. Se la casella è deselezionata, selezionarla in modo che visualizzi un segno di spunta.

29. Selezionare **Reimposta password**.

30. Se viene richiesto di salvare la password, selezionare **mai** per chiudere la finestra.

31. Dovrebbe essere visualizzato un messaggio di errore che indica che non è possibile reimpostare la password di Diego perché gli è stato assegnato un ruolo di amministratore. Nel caso di Diego, gli è stato assegnato il ruolo di amministratore fatturazione in precedenza in questo esercizio di laboratorio. Poiché solo gli amministratori globali possono modificare la password di un altro amministratore e dato che Lynne non è un amministratore globale, dovrà chiedere a Holly Dickson di apportare questa modifica. Nel riquadro **Reimposta password** selezionare **Chiudi**. 

32. Se viene visualizzata una finestra con una richiesta di sondaggio, selezionare **Annulla**.

33. Si vuole ora modificare la password di Pradeep Gupta. Nell'elenco **Utenti attivi** selezionare l'icona della **chiave (Reimposta una password)** visualizzata a destra di **Pradeep Gupta**. 

34. Nella finestra **Reimposta password** visualizzata per Pradeep, verificare che nella casella di controllo **Crea automaticamente una password** sia presente un segno di spunta. In caso contrario, selezionare questa casella in modo che il sistema generi automaticamente una password per Pradeep.  <br/>

    Si tratta solo di una password temporanea perché Lynne vuole forzare Pradeep a modificarla al successivo accesso. Verificare quindi che la casella di controllo **Richiedi all'utente di cambiare la password al primo accesso** visualizzi un segno di spunta. Se la casella è deselezionata, selezionarla in modo che visualizzi un segno di spunta.
    
35. Selezionare il pulsante** Reimposta password**.

36. Nella finestra **La password è stata reimpostata** dovrebbe essere visualizzato un messaggio che indica che è stata reimpostata correttamente la password per Pradeep. Selezionare **Chiudi**.

37. La direzione ha recentemente scoperto che il nome utente di Alex Wilber potrebbe essere stato compromesso. Di conseguenza, a Lynne viene chiesto di bloccare l'account di Alex in modo che nessuno possa accedere con il suo nome utente fino a quando la direzione non è in grado di stabilire l'entità del problema. Nell'elenco **Utenti attivi** selezionare la casella di controllo a sinistra del nome di **Alex Wilber** (NON selezionare il nome di Alex).  <br/>

    **Importante:** poiché si eseguirà un comando globale anziché un comando associato all'account di Alex, solo l'account di Alex deve essere selezionato nell'elenco degli utenti attivi. Se è selezionato un altro account utente, è necessario deselezionarlo prima di procedere. Scorrere l'elenco degli utenti attivi e verificare che non sia selezionato alcun altro account utente. Se è selezionato un account diverso da Alex, fare clic sulla casella di controllo dell'account per deselezionarla. **Solo l'account di Alex Wilber deve essere selezionato.**

38. Nella barra dei menu nella parte superiore della pagina selezionare l'icona con i **puntini di sospensione (...)** per visualizzare un menu a discesa con azioni aggiuntive. Nel menu visualizzato selezionare **Modifica stato di accesso**.

39. Nel riquadro **Blocca l'accesso** visualizzato, verificare che l'indirizzo di posta elettronica di Alex sia visualizzato sotto l'intestazione **Blocca l'accesso**. Selezionare la casella di controllo **Blocca l'accesso dell'utente**, quindi selezionare **Salva modifiche.** 

40. La finestra **Blocca l'accesso** dovrebbe visualizzare un messaggio che indica che l'accesso di Alex è stato bloccato (e nessuno può accedere con il nome utente di Alex nel caso in cui il nome utente sia stato effettivamente compromesso). Inoltre, Alex verrà disconnesso automaticamente dai servizi Microsoft entro 60 minuti. Selezionare l'icona a forma di **X** nell'angolo superiore destro del riquadro per chiuderlo. 

41. Lynne è appena stata informata che il nome utente di **Nestor Wilke** è stato potenzialmente compromesso. Ripetere i passaggi da 37 a 40 per impedire a Nestor di accedere (e impedire a chiunque altro di usare il suo nome utente per accedere). <br/>

    Quando si è tentato di bloccare l'accesso di Nestor, si dovrebbe aver ricevuto un messaggio di errore che indica che **Non è possibile salvare le modifiche**. Il motivo per cui è stato visualizzato questo errore è che Nestor è un amministratore globale, mentre Lynne non lo è. Solo un amministratore globale può impedire a un altro amministratore globale di accedere. Lynne dovrà chiedere a Holly Dickson di apportare questa modifica. <br/>

    Chiudere il riquadro **Blocca l'accesso**.

42. In precedenza si è bloccato l'accesso di Alex Wilber. Per verificare se è bloccato, si tenterà di accedere come Alex. Disconnettersi da Microsoft 365 selezionando l'icona utente corrispondente a **Lynne Robbins** (il cerchio con la foto di Lynne nell'angolo superiore) e nella finestra **Lynne Robbins** visualizzata selezionare **Esci.** 

43. Si consiglia di chiudere tutte le schede del browser, ad eccezione della scheda **Esci** dopo aver effettuato la disconnessione. Nella scheda **Esci** passare a **https://portal.office.com**. 

44. Nella finestra **Scegli un account** selezionare **Usa un altro account**. Nella finestra **Accedi** immettere **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (dove xxxxxZZZZZZ è il prefisso del tenant fornito dal proprio provider di hosting del lab). Nella finestra **Immettere la password** immettere la **password utente** fornita dal provider di hosting del lab.  <br/>

    Verrà visualizzata la finestra **Scegli un account** e dovrebbe essere visualizzato un messaggio di errore che indica che **l'account è stato bloccato è che è necessario contattare il responsabile dell'assistenza per sbloccarla, quindi riprovare.** Si è appena verificato che Alex (o qualcuno che ha ottenuto il suo nome utente e la sua password) non può accedere. <br/>

    **Nota:** l'implementazione completa del blocco dell'account può richiedere alcuni minuti. Fino a quando il blocco non è stato implementato nel sistema, Alex potrebbe comunque essere in grado di accedere, ma nessuno dei servizi di Microsoft 365 sarà disponibile per lui e non saranno visualizzati nel portale di Microsoft 365. Una volta sbloccato un account, i servizi diventeranno nuovamente disponibili. <br/>

    Se è possibile accedere come Alex, disconnettersi e attendere alcuni minuti. Potrebbe essere un buon momento per fare una breve pausa. Quindi tentare di accedere nuovamente come Alex. A questo punto, si dovrebbe aver ricevuto il messaggio di errore che indica che l'account di Alex è stato bloccato per l'accesso. 
    
45. Tornare a **LON-CL1**. 

46. In **LON-CL1** si dovrebbe essere ancora collegati a **Microsoft 365** come Holly Dickson nel browser Edge. L'elenco **Utenti attivi** dovrebbe essere visualizzato, come in precedenza in questa attività, nell'**interfaccia di amministrazione di Microsoft 365**. 

47. Dopo ulteriori indagini, il CTO di Adatum ha stabilito che l'account di Alex Wilber, in realtà, non è stato compromesso; pertanto ha chiesto a Holly di rimuovere il blocco all'account utente di Alex. Ripetere i passaggi da 37 a 40 per sbloccarne l'account. Si noti che nella finestra **Blocca l'accesso**, al passaggio 39 è ora visualizzata invece la finestra **Sblocca l'accesso**.  <br/>

    Nella finestra **Sblocca l'accesso** è attualmente selezionata la casella di controllo **Blocca l'accesso dell'utente**. Fare clic su questa casella di controllo per deselezionarla, quindi selezionare **Salva modifiche**. <br/>
    
    **IMPORTANTE:** viene visualizzato un messaggio di avviso che indica che potrebbero essere necessari fino a 15 minuti prima che Alex possa accedere di nuovo. Dati i limiti di tempo del training, **NON** provare a verificare se Alex può accedere di nuovo. Se lo si desidera, provare ad accedere come Alex in un secondo momento, durante una pausa o se si ha tempo e si vuole eseguire una verifica. Per il momento, rimanere all'interno di LON-CL1 e chiudere semplicemente la finestra **Sblocca l'accesso**.
    
48. In LON-CL1 lasciare aperto il browser e tutte le schede e passare all'esercizio successivo. 


# Fine del lab 2

