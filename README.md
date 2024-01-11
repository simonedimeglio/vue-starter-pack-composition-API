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
