# chat_java_socket
Chat con i Java Sockets

Esercitazione di Laboratorio: Chat TCP Multithread con Java Socket
L'esercitazione consiste nell'applicare i concetti di programmazione di rete e concorrenza per realizzare un'applicazione Client-Server completa: una chat multi-utente basata sul protocollo TCP.

Obiettivo
Il vostro compito è sviluppare due applicazioni Java distinte: un Server in grado di gestire connessioni multiple e un Client che permetta agli utenti di partecipare alla conversazione.
Il funzionamento è semplice: ogni messaggio inviato da un client deve essere ricevuto dal server, il quale provvederà a inoltrarlo a tutti gli altri client attualmente connessi.

Requisiti
Per garantire un'organizzazione del codice chiara e modulare, dovrete rispettare la seguente struttura. Il progetto finale dovrà contenere due cartelle separate: Client e Server.

Specifiche dell'Applicazione Server
Il server ha il compito di accettare connessioni, gestire la lista dei partecipanti e instradare i messaggi. Dovrà essere strutturato nelle seguenti tre classi:
- MainServer:
È la classe eseguibile che avvia il servizio.
Deve creare un ServerSocket per mettersi in ascolto su una porta a vostra scelta.
Deve accettare in un ciclo continuo le connessioni dei nuovi client. Per ogni client che si connette, dovrà creare e avviare un thread dedicato alla sua gestione.
- ListaClient:
Questa classe ha la responsabilità di mantenere e gestire l'elenco di tutti i client connessi al server.
Dovrà fornire i metodi necessari per aggiungere un nuovo client, rimuoverlo quando si disconnette e, soprattutto, per inviare un messaggio in broadcast a tutti i client presenti nella lista.
Attenzione: Questa risorsa sarà condivisa tra più thread, dovrete quindi assicurarvi che la gestione della lista avvenga in modo sicuro (thread-safe).
- ThreadConnessione:
Rappresenta il thread dedicato a gestire la comunicazione con un singolo client.
Il suo compito è quello di rimanere in ascolto costante dei messaggi provenienti dal suo client.
Quando riceve un messaggio, lo inoltra alla ListaClient affinché venga distribuito a tutti.
Deve anche gestire la disconnessione del client, assicurandosi che venga rimosso correttamente dalla lista condivisa.

Specifiche dell'Applicazione Client
Il client deve poter svolgere due attività in parallelo: inviare i messaggi scritti dall'utente e ricevere quelli inviati dagli altri. Per questo, utilizzerete un approccio multithread.
- ClientMain:
È la classe eseguibile che avvia il client.
Deve stabilire la connessione con il server tramite un Socket.
Una volta connesso, deve istanziare e avviare i due thread responsabili della comunicazione.
- ThreadInvio:
Questo thread è dedicato esclusivamente all'invio dei messaggi.
Il suo compito è leggere l'input da tastiera dell'utente e inviarlo al server attraverso il socket della connessione.
- ThreadRicevi:
Questo thread è dedicato esclusivamente alla ricezione dei messaggi.
Il suo compito è rimanere in ascolto dei messaggi provenienti dal server e stamparli a video sulla console dell'utente.

Modalità di Consegna
Al termine, consegnate su Github il progetto contenente la cartella principale, rinominato come CognomeNome_ChatTCP, la cui struttura interna contenga le cartelle Client e Server.
Buon lavoro!

