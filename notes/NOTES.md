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

