# Blog in Vue3 (Composition API & Router)

Repo relativa alla creazione di un blog in Vue3 (Composition API, Router) utilizzata per le Academy Frontend dove trattiamo VueJs.

## Teoria relativa a Composition API 

Prendiamo in analisi questo componente Vue relativamente alla parte dello**`<script>`:** 

<img width="407" alt="1" src="https://github.com/simonedimeglio/vue-blog-composition-API/assets/78272736/ec7834a2-8453-4a86-af79-124048d80590">

Questa sezione, come già sappiamo, contiene la logica JavaScript del componente.

-   **`export default { ... }`:** Qui definisci il componente Vue. `name` è il nome del componente, e `setup`, `created`, e `mounted` sono **hook** del ciclo di vita del componente.
    
-   **`setup():`** È parte della Composition API ed è il punto in cui puoi iniziare a definire la logica del tuo componente.
    
-   **`created():`** È uno degli hook del ciclo di vita e viene chiamato quando il componente è stato creato.
    
-   **`mounted():`** È un altro hook del ciclo di vita e viene chiamato quando il componente è stato montato nel DOM.

In breve, quando il componente viene creato, `setup` viene chiamato per inizializzare la logica del componente, quindi `created` viene chiamato, e infine, quando il componente è montato nel DOM, `mounted` viene chiamato. Questi hook del ciclo di vita consentono di eseguire azioni specifiche in diversi momenti durante il ciclo di vita del componente.

Bene, **ora modifichiamo il file e ragioniamo su cosa abbiamo scritto**:

<img width="665" alt="2" src="https://github.com/simonedimeglio/vue-blog-composition-API/assets/78272736/7b79eb63-8cfc-4137-8ba9-6f0ddc286474">

Abbiamo detto che la funzione `setup` è un punto di ingresso principale per la Composition API. All'interno di questa funzione, stiamo dichiarando le variabili locali e le funzioni che desideriamo utilizzare nel nostro componente.

-   **Variabili Locali (`nome` ed `età`):** Stiamo dichiarando due variabili locali all'interno della funzione `setup`. Così queste variabili sono accessibili nel nostro template.

-   **Funzione `faiClick`:** Abbiamo una funzione `faiClick` dichiarata all'interno di `setup`. Questa funzione viene chiamata quando il pulsante viene cliccato e stamperà un messaggio sulla console.
        
-   **`return { nome, età, faiClick }`:** Questo blocco di `return` è **fondamentale**. Facendo ciò, rendiamo disponibili le variabili e le funzioni dichiarate in `setup` nel nostro template restituendole come parte di un oggetto. In questo modo, possiamo accedere a queste variabili e funzioni direttamente nel template.

Ottimo. Parliamo di **ref** adesso. 

<img width="839" alt="3" src="https://github.com/simonedimeglio/vue-blog-composition-API/assets/78272736/87a27a59-8269-4ddc-9b81-2850f3830d92">


La funzione `ref` in Vue 3 è un modo per dichiarare una "reference reattiva". Ogni reference reattiva può contenere un valore che può essere cambiato nel tempo. Ecco alcuni concetti chiave:

1.  **Reference Reattiva:**
    
    -   Una reference reattiva è un'astrazione fornita da Vue per rendere un valore reattivo nel sistema di reattività di Vue. Ciò significa che se il valore cambia, qualsiasi parte del tuo componente che dipende da questo valore verrà automaticamente aggiornata. (Cosa che succedeva nelle variabili che inserivamo sotto data()..)
    
2.  **Utilizzo di `ref`:**
    
    -   Possiamo utilizzare `ref` per dichiarare una reference reattiva. Ad esempio: `const paragrafo = ref(null)`.
    -   Inizializziamo la reference con `null` perché inizialmente non sappiamo quale sarà l'elemento del paragrafo. Sarà possibile omettere il valore `null` quando dichiariamo una reference con `ref`. Nel nostro esempio, `ref(null)` è stato utilizzato per inizializzare la reference con un valore iniziale nullo. Tuttavia, se non abbiamo bisogno di un valore iniziale, possiamo semplicemente dichiarare la reference senza argomenti (`ref()` ). Questo creerà una reference con un valore iniziale di `undefined`. Possiamo sempre assegnare un valore successivamente utilizzando `paragrafo.value = nuovoValore`.
    
3.  **Reference a Elementi del DOM:**
    
    -   Quando usiamo `ref` con un elemento del DOM (`<p ref="paragrafo">`), la reference `paragrafo` conterrà l'elemento DOM effettivo quando il componente viene montato.
4.  **Modifica degli Elementi del DOM:**
    
    -   Possiamo utilizzare la reference per modificare dinamicamente gli attributi o il contenuto degli elementi del DOM. Nel nostro caso, `paragrafo.value` rappresenta l'elemento HTML del paragrafo.


> Ma aspetta: questa cosa è simile al discorso "getElementBy ..." che usavamo con JavaScript Vanilla?

Sì, in un certo senso, la creazione di una reference reattiva con `ref` in Vue può essere paragonata a utilizzare `getElementById` o altri metodi simili in JavaScript puro (vanilla JS) per ottenere un riferimento a un elemento del DOM.

Tuttavia, ci sono alcune differenze chiave:

1.  **Reattività:**
    
    -   Quando usiamo `ref` in Vue, ottieniamo automaticamente la reattività. Ciò significa che se il valore associato alla reference cambia, le parti del nostro componente che dipendono da quel valore vengono automaticamente aggiornate. In vanilla JavaScript, dovremmo gestire manualmente gli aggiornamenti del DOM. Vediamo un bell'esempio di reattività tramite **ref**:
  
<img width="671" alt="4" src="https://github.com/simonedimeglio/vue-blog-composition-API/assets/78272736/b72b5a32-373e-44f9-b1eb-7c645a5ba709">

    
2.  **Integrazione con Vue:**
    
    -   Utilizzare `ref` è parte integrante della Composition API di Vue. Ci consente di organizzare il codice in modo più modulare e comprensibile, specialmente in progetti più complessi. Invece, l'uso diretto di `getElementById` è una pratica comune in JavaScript puro, ma potrebbe richiedere un codice più verboso e meno organizzato.

