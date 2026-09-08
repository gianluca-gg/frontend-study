alcune cose da ricordare sul css:

- se vogliamo condividere delle regole, e abbiamo due elementi con due classi diverse, facciamo così:

.read,.unread {
    background-color: black;
}

se poi queste due classi hanno bisogno di regole specifiche che valgono solo in uno o nell'altro caso, facciamo più sotto:

.read {
    // regole
}

.unread {
    // altre regole
}

possiamo anche fare class chaining, per avere specificità e generalità insieme:

<div class="menu header"></div>
<div class="menu" id="subheader"></div>

.menu.header {
    //regole
}

.menu#subheader {
    //regole
}

oppure targettare tutti i figli di un antenato.

<div class="ancestor">
    <div class="child">
        <div class="child"></div>
    </div>
</div>

.ancestor .child {
    //regole
}

in questo caso sto targettando TUTTI i figli ".child".

Come vedi, ATTENZIONE: tra i due modi per targettare in css c'è una differenza fondamentale. nel primo caso non c'è lo spazio, nel secondo sì. Lo spazio cambia tutto: senza mi riferisco a concatenazioni, con mi riferisco a rapporto ancestor -> tutti i figli.

Di default, un'img non ha width e height settate nel css. Vengono utilizzate quelle dell'immagine originale (quelle del file, insomma).

Per non perdere le proporzioni, nel caso in cui vogliamo un'immagine più piccola, possiamo settare width o height ad AUTO:

.image {
    width: auto;
    height: 500px;
}

REGOLE PER LA SPECIFICITA' del css: id > classe > tipo. In caso di multipli riferimenti a id, classe, tipo, funziona comunque in senso gerarchico: multiple classi vengono "battute" da un singolo id, e una singola classe "batte" multipli tipi. cambia invece nel caso di selettori che pescano da selettori diversi: un id non batterà un selettore con id e classe.

Modello box per css, come funziona per i vari spacing che si possono inserire:

padding: aumentare spazio tra bordo del box e contenuto
border: aggiungere spazio tra il margin e il padding
margin: aggiungere spazio tra il bordo del box e i box adiacenti

boxes, border-box e content-box.

nel caso del content-box, un eventuale padding e border si aggiungono alla grandezza totale del box. quindi se ho un box 700 width e 200 height, se aggiungo padding 50 in ogni direzione questa renderà il box più grosso. se invece faccio border-box, il padding precedentemente citato si sottrarrà alla grandezza originale del box, mantenendolo complessivamente della stessa dimensione.

FLEX

un flex container è qualsiasi elemento che abbia all'interno la regola display: flex. un flex item è qualsiasi elemento che viva all'interno del container.

flex grow determina quanto è grande un flex item rispetto al contenitore e ai suoi "fratelli". se sono tutti a 1 condivideranno la stessa grandezza, se ad esempio uno dei 3 è 2 sarà più grande degli altri.

flex shrink, invece, determinerà se il flex item, nel caso in cui questi siano più grandi del contenitori stessi, si rimpicciolirà per essere contenuti nel loro ancestor flex

flex basis setta la grandezza iniziale dell'item.

se a flex basis metto auto, prenderà la width dell'item
flex: 1 è come dire flex grow 1, flex shrink 1, flex basis 0
flex auto è come dire flex grow 1, flex shrink 1, flex basis auto

JAVASCRIPT, VARIABILI

la differenza fondamentale tra let e const è che la prima è riassegnabile, la seconda no. esiste anche var, che ha delle caratteristiche particolari rispetto a let, tra cui l'unica condivisa è che è riassegnabile, ma è considerata obsoleta e non più utilizzata.

E' possibile copiare il valore di una variabile in un'altra variabile:

let message = 'Hello!';

newMessage = message;

alert(message) // Hello!
alert (newMessage) // Hello!

Una volta era possibile assegnare un valore a una variabile senza definirla con 'let'. E' ancora così se non inseriamo all'inizio del nostro codice 'use strict;'. 
Ricorda che se in javacript aggiungi un numero in stringa (o insomma una stringa in generale) a un numero il risultato sarà una stringa, dove il numero aggiunto verrà convertito in stringa. 'hello' + 2 = 'hello2'.
cos'è il % negli operatori javascript? dà come risultato il resto di un numero. 

alert( 5 % 2 ); // 1, the remainder of 5 divided by 2
alert( 8 % 3 ); // 2, the remainder of 8 divided by 3
alert( 8 % 4 ); // 0, the remainder of 8 divided by 4

Ricorda:

per incrementare un numero:

let counter = 2;
counter++;

per diminuire:

let counter = 2;
counter--;

aggiungerà o sottrarrà di 1.

I numeri

funzionano esattamente con l'ordine della matematica "normale". prima le parentesi, poi gli esponenziali da destra a sinistra, poi moltiplicazioni e divisioni, poi addizioni e sottrazioni, entrambi i gruppi da sinistra a destra.

= è un operatore, ma ha una priorità molto bassa. è il motivo per cui, una volta dichiarato appunto l'operatore = e a suo seguito un certo numero di operazioni coi numeri, l'operatore = sarà l'ultimo ad avere la precedenza, e immagazzinerà nella sua variabile il risultato delle operazioni.

L'assignment = ritorna un valore. (---continua a descrivere dopo)

Se in una operazione c'è una stringa, il risultato sarà sempre una stringa (quindi se ad esempio l'altro operando è un numero, verrà "trasformato" in string).

Per trasformare un numero da stringa a numero, usiamo Number.

per esempio:

let myNumber = "73";

myNumber = Number(myNumber) + 3 // myNumber ora è 77

NODE JS

node js è un ambiente che permette di runnare codice javascript al di fuori del browser. 

DATA TYPES

In javascript, esistono diversi tipi di data types. Le variabili non sono legate indissolubilmente a un tipo, questo significa che se il valore assegnato alla variabile è di un tipo specifico, possiamo riassegnarla in un secondo momento con un tipo diverso.

esempio:

let number = "12345"; // tipo stringa
number = 12345; // tipo number

Questo significa che Javascript, come altri linguaggi, è dinamically typed. Esistono diversi tipi, ma le variabili non sono legati a uno in particolare.

Tipo numero: oltre ai numeri, i valori numerici particolari sono Infinity, -Infinity e NaN.

Infinity rappresenta l'infinito matematico.  Vi si può riferire letteralmente, usando Infinity, oppure dividendo l'1 per 0.
NaN rappresenta un'operazione matematica errata o indefinita. Ad esempio alert(2 - "not a number") // NaN

BigInt
C'è un limite che il tipo numero può rappresentare come integrale. Sono tutti gli integrali maggiori di (253-1) e minori -(253-1).
In verità non è che un tipo numero non possa salvare un numero al di fuori di queste soglie, il problema è che ci sarà un errore di precisione che non garantisce la correttezza del risultato. 

String
Una stringa in Javascript deve essere racchiusa dalle virgolette.
Vanno bene: 
Double quotes: "Hello".
Single quotes: 'Hello'.
Backticks: `Hello`.

Sia le doppie che le singole virgolette sono le virgolette "normali". Non c'è differenza tra queste in JS. Le backticks, invece, danno la possibilità di avere funzioni aggiuntive. Possono farci aggiungere al loro interno espressioni e variabili.

let name = "John";

// embed a variable
alert( `Hello, ${name}!` ); // Hello, John!

// embed an expression
alert( `the result is ${1 + 2}` ); // the result is 3

Booleano
true and false. Generalmente con questi due valori diamo due significati: sì, corretto per true, no, incorretto per falso.

let nameFieldChecked = true; // yes, name field is checked
let ageFieldChecked = false; // no, age field is not checked

Il booleano è anche il value di una comparazione:

let isGreater = 4 > 1;

alert( isGreater ); // true

Null
Nessun tipo dei precedenti
Contiene solo il null value. Rappresenta "niente", "vuoto", o "valore sconosciuto". Ad esempio:

let age = null;

Qui si sta indicando che "age" è sconosciuto.

Undefined
Undefined significa -> valore non assegnato. Ad esempio, se una variabile è stata dichiarata ma non le è stato assegnato un valore, allora il valore sarà undefined:

let age;

alert(age); // shows "undefined"

Oggetti e simboli
Il tipo oggetto è speciale. Gli altri tipi sono chiamati "primitivi" perché i loro valori possono contenere soltanto una cosa, che sia una stringa o un numero. Al contrario, gli oggetti possono contenere collezioni di dati o entità più complesse. Il simbolo, invece, serve a dare un identificatore univoco agli oggetti.

Typeof
Ritorna il tipo di operando sotto forma di stringa. Utile quando vogliamo fare un check.

typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"  (1)

typeof null // "object"  (2)

typeof alert // "function"  (3)

Alcune precisazioni:

Math è un oggetto già impostato da javascript che ci dà tutta una serie di operazioni matematiche già pronte.
Il risultato di typeof null è "object". E' un errore riconosciuto di typeof. Null non è un object.
Typeof alert dà funzione, perché alert è una funzione.

Approfondimento sulle stringhe
Le stringhe hanno bisogno di essere racchiuse da DUE virgolette: una all'inizio, una alla fine. Se ne manchi una, riceverai errore.
Attenzione anche a usare lo stesso tipo di virgoletta: ' deve finire con ', o " con ".
Con i backticks posso fare due cose: inserire javascript all'interno della stringa ed estendere la stringa su più righe, dando il risultato perlappunto su più righe. Nelle stringhe normali bisogna usare \n per far andare il testo a capo.
Per inserire testo con virgolette all'interno di virgolette: o usi virgolette diverse, o usi \ prima delle virgolette.
Se concateniamo stringa e numero, il numero verrà comodamente convertito in automatico in stringa. 
Tip: se vogliamo convertire un numero in stringa o una stringa in numero, se possibile, si può usare Number o String.

ad esempio:

let myString = "123" // string

let myNum = Numbert(myString);
console.log(typeof myNum); // diventato number

let myNum = 123;
let myString = String(myNum);
console.log(myString); // string

String Methods

Passiamo in rassegna su alcuni metodi delle stringhe.

Length
Ci ritorna la lunghezza di una stringa.
let string = "abcd";

console.log(string.length) // 4

Estrarre il carattere di una stringa
Ci sono quattro metodi per farlo. at(position), charAt(position), charCodeAt(position) e [], per accedere a una proprietà come in un array.

charAt()
Ritorna il carattere in una posizione index specifica.
let text = "ciao";

let char = text.charAt(0); // "c"

charCodeAt()
Simile a charAt, ma ci restituisce l'UTF-16 code.

codePointAt()
Ci dice il codice Unicode.

Con ES2022 abbiamo ottenuto il metodo at().
Ritorna il carattere su uno specifico index. La differenza con charAt() è che at può lavorare anche sui numeri negativi.

concat()
Unisce due o più stringhe.
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2); // "Hello world"
Nota: fondamentalmente il concat sostituisce il + tra le diverse stringhe, snellendo il processo di concatenazione.

NOTA: tutti questi metodi ritornano una NUOVA stringa. La stringa originale rimane immutata. Questo perché le stringhe sono immutabili, non possono essere cambiate, soltanto sostituite.

Metodi per estrarre una parte di una stringa

slice() estrae una parte di una stringa e ritorna la parte estratta come nuova stringa. Due parametri: posizione d'inizio e posizione di fine.

let text = "Apple, Banana, Kiwi";
let part = text.slice(7, 13); // banana

Nota:
Se ometti il secondo parametro, il metodo farà uno slice di tutto il resto della stringa.

Substring() è simile a slice: la differenza è che tutti i parametri d'inizio e fine che dovessero essere inferiori di 0 vengono trattati come 0.

substr() è simile a slice, ma il secondo parametro specifica la lunghezza della parte estratta. 

Due metodi per upper e lowercase: toUpperCase() e toLowerCase(): rispettivamente, convertono il testo in maiuscolo e minuscolo.

Metodo trim()

Cancella lo spazio bianco prima e dopo una stringa, in entrambe le direzioni.

trimStart() è simile, ma cancella solo l'inizio.

trimEnd() è simile, ma cancella solo la fine.

Metodo repeat()
Ritorna una stringa con un numero di copie di una stringa. Ritorna una stringa NUOVA, e non cambia quella originale.

let text = "Hello world!";
let result = text.repeat(2); // Hello world! Hello world!

Metodo replace()
Sostituisce un valore specifico con un altro valore in una stringa.

let text = "Please visit Microsoft!";
let newText = text.replace("Microsoft", "W3Schools"); // "Please visit W3Schools!"

Nota:
Non cambia la stringa originale e ne ritorna una nuova. Cambia solo il PRIMO match.

nuovo metodo nel 2021, replaceAll().

let text = "I love cats. Cats are very easy to love. Cats are very popular."
text = text.replaceAll("Cats","Dogs");
text = text.replaceAll("cats","dogs"); // "I love dogs. Dogs are very easy to love. Dogs are very popular."

Così è possibile sostituire più parole contemporaneamente tramite l'utilizzo di regular expressions.

| Convertire stringhe in array |

split()
Si può convertire una stringa in array usando split()

Se il parametro è (""), la stringa verrà convertita in un array, che ritornerà i singoli caratteri:
let text = "Hi fox!";
const myArr = text.split(""); // ["H","i"," ","f","o","x","!"]

Se il parametro è (" "), la stringa ritornerà un array con le singole parole:

let text = "The quick brown fox.";
const myArr = text.split(" "); // ["The", "Quick", "Brown", "fox."]

Se ometto il separatore, l'array avrà l'intera stringa sull'index [0].

let text = "The quick brown fox.";
const myArr = text.split(); // ["The quick brown fox."]

NOTA:
usare split() su frasi che contengono emojis o caratteri complessi non è sicuro. 

String search methods

indexOf()
questo metodo ci permette di ritornare l'index della prima occorrenza di una string in una string (oppure ritorna -1 se la string non è stata trovata):
let text = "Please locate where 'locate' occurs!";
let index = text.indexOf("locate"); // 7

Dà la prima posizione dove trova la stringa. Ad esempio qua sopra è 7. E' la prima posizione dove si trova una stringa "locate".

lastIndexOf()
Uguale, ma al contrario: l'ultima occorrenza di una stringa in una stringa.

sia indexOf che lastIndexOf accettano un secondo parametro: la posizione dalla quale cominciare la ricerca.

let text = "Please locate where 'locate' occurs!";
let index = text.lastIndexOf("locate"); // 21

search()
Cerca una stringa in una stringa, e ritorna la posizione.

search() e indexOf() sembrano due metodi identici, ma la differenza è che search non può prendere un secondo parametro, e indexOf non può prendere regular expressions come parametri.

match()
Ritorna un array che contiene il risultato di far combaciare una stringa con un'altra stringa.