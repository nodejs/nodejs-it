## io.js è supportato da... 
* [Postmark](http://blog.postmarkapp.com/post/110829734198/its-official-were-getting-cozy-with-node-js) 
* [node-serialport](https://github.com/voodootikigod/node-serialport/issues/439)
* [Microsoft Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-nodejs-iojs/)

## io.js a più di 10000 stelle su GitHub
Il 13 Febbraio io.js ha raggiunto l'obiettivo delle 10000 stelle su Github. Non ce l'avremmo fatta senza il supporto della splendida comunità JavaScript. Grazie a tutti!

## io.js 1.2.0 rilasciato
* **stream**: Costruzione degli stream semplificata ([readable-stream/issues#102[(https://github.com/iojs/readable-stream/issues/102))
* **dns**: `lookup()` adesso accetta un booleano per l'opzione `'all'`, di default è `false` ma quando specificato `true` il metodo ritorna un array di tutti i nomi associati ad un indirizzo. Vedi  ([iojs/pull#744](https://github.com/iojs/io.js/pull/744))
* **assert**: Rimosso il confronto della proprietà `prototype` in `deepEqual()` ([iojs/issues#636](https://github.com/iojs/io.js/pull/636)); introdotto `deepStrictEqual()` come metodo clone di `deepEqual()` che svolge un controllo di uguaglianza sulle proprietà primitive  ([iojs/issues#639](https://github.com/iojs/io.js/pull/639)).
* **tracing**: Aggiunge [LTTng](http://lttng.org/) (Linux Trace Toolkit Next Generation) quando viene compilato con l'opzione `--with-lttng option`. Trace points match those available for DTrace and ETW. ([iojs/issues#702](https://github.com/iojs/io.js/pull/702))
* **docs**: Molta della documentazione aggiornata, vedi i cambiamenti individuali; aggiunte pagine dettagliate per errori specifici relativi a JavaScript, V8, e io.js.
* **npm** aggiornamento alla versione 2.5.1
* **libuv** aggiornamento alla versione 1.4.0, vedi il [ChangeLog](https://github.com/libuv/libuv/blob/v1.x/ChangeLog)
* Aggiunti nuovi collaboratori: 
  * Aleksey Smolenchuk (@lxe)
  * Shigeki Ohtsu (@shigeki)

## Porte aperte alla community internazionale
Vedi [l'atricolo originale](https://medium.com/@mikeal/how-io-js-built-a-146-person-27-language-localization-effort-in-one-day-65e5b1c49a62) su Medium.
* Aggiunti collaboratori interessati ai team di localizzazione.
* I team  hanno registrato gli account su Twitter e sui social media rilevanti.
* I team hanno trovato il loro modo preferito per contribuire e sono andati oltre, avvicinandosi a essere "community organizers" invece che solamente traduttori.

### Statistiche della localizzazione: 

* 146 persone si sono registrare per aiutare con la localizzazione nel primo giorno (ad ora più di 160)
* 27 community in lingua create il primo giorno (ad ora più di 29)

### Community in lingua

* [`iojs-bn`](https://github.com/iojs/iojs-bn) Bengali Community
* [`iojs-cn`](https://github.com/iojs/iojs-cn) Chinese Community 
* [`iojs-cs`](https://github.com/iojs/iojs-cs) Czech Community 
* [`iojs-da`](https://github.com/iojs/iojs-da) Danish Community 
* [`iojs-de`](https://github.com/iojs/iojs-de) German Community
* [`iojs-el`](https://github.com/iojs/iojs-el) Greek Community
* [`iojs-es`](https://github.com/iojs/iojs-es) Spanish Community
* [`iojs-fa`](https://github.com/iojs/iojs-fa) Persian Community 
* [`iojs-fi`](https://github.com/iojs/iojs-fi) Finnish Community
* [`iojs-fr`](https://github.com/iojs/iojs-fr) French Community
* [`iojs-he`](https://github.com/iojs/iojs-he) Hebrew Community
* [`iojs-hi`](https://github.com/iojs/iojs-hi) Hindi Community 
* [`iojs-hu`](https://github.com/iojs/iojs-hu) Hungarian Community
* [`iojs-id`](https://github.com/iojs/iojs-id) Indonesian Community
* [`iojs-it`](https://github.com/iojs/iojs-it) Italian Community
* [`iojs-ja`](https://github.com/iojs/iojs-ja) Japanese Community
* [`iojs-ka`](https://github.com/iojs/iojs-ka) Georgian Community
* [`iojs-kr`](https://github.com/iojs/iojs-kr) Korean Community
* [`iojs-mk`](https://github.com/iojs/iojs-mk) Macedonian Community
* [`iojs-nl`](https://github.com/iojs/iojs-nl) Dutch Community
* [`iojs-no`](https://github.com/iojs/iojs-no) Norwegian Community
* [`iojs-pl`](https://github.com/iojs/iojs-pl) Polish Community
* [`iojs-pt`](https://github.com/iojs/iojs-pt) Portuguese Community
* [`iojs-ro`](https://github.com/iojs/iojs-ro) Romanian Community
* [`iojs-ru`](https://github.com/iojs/iojs-ru) Russian Community
* [`iojs-sv`](https://github.com/iojs/iojs-sv) Swedish Community
* [`iojs-tr`](https://github.com/iojs/iojs-tr) Turkish Community
* [`iojs-tw`](https://github.com/iojs/iojs-tw) Taiwan Community
* [`iojs-uk`](https://github.com/iojs/iojs-uk) Ukranian Community

## io.js e Node.js
Leggi [l'articolo originale](https://medium.com/@iojs/io-js-and-a-node-js-foundation-4e14699fb7be) su Medium.
* Scott Hammond, CEO di Joyent, esprime il desiderio di riportare io.js in node.js.

#### In pochi mesi di io.js... 
* Il team _core_ è cresciuto fino a 23 collaboratori attivi,
* si sono creati molti gruppi di lavoro,
* è arrivato ad avere 29 team di localizzazione,
* ha portato più collaboratori al progetto di quanti ce ne siano stati nella storia di node.js, e
* siamo riusciti a rilasciare software di qualità ad un buon passo grazie al supporto di una community eccezionale.

> Siamo disposti a lasciarci il passato alle spalle me non possiamo sacrificare i progressi che abbiamo fatto o il principio di governance aperta che ci ha portato fin qui.

### Il futuro
* Gli incontri con la node.js foundation continuano a proseguire.
* Una volta che la node.js foundation si convertirà ad un modello di governance tecnica verrà aggiunta una segnalazione alla repository di io.js su GitHub sulla questione della collaborazione.

  * Questo problema verrà discusso e votato pubblicamente in un incontro che seguirà le regole della community che abbiamo già deciso.

> Per la comunità non cambia nulla.

### Cosa fare adesso
* Continua a mandare le tue pull requests a io.js,
* Collabora con uno dei 27 [team di localizzazione](https://github.com/iojs/website/issues/125)
* Collabora con i gruppi di lavoro del progetto ([streams](https://github.com/iojs/readable-stream), [website](https://github.com/iojs/website), [evangelism](https://github.com/iojs/website/labels/evangelism), [tracing](https://github.com/iojs/tracing-wg), [build](https://github.com/iojs/build), [roadmap](https://github.com/iojs/roadmap)) e
* Continua a usare io.js nelle tue applicazioni.
