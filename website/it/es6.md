# ES6 con io.js

# ES6 on io.js

io.js è integrata con versioni moderne di [V8](https://code.google.com/p/v8/). Mantenendoci aggiornati con le ultime versioni
di questo motore, possiamo rendere disponibili le nuove caratteristiche delle [specifiche JavaScript ECMA-262](http://www.ecma-international.org/publications/standards/Ecma-262.htm) agli sviluppatori io.js in modo rapido, assieme a continui miglioramenti
nella stabilità e nelle prestazioni.

io.js is built against modern versions of [V8](https://code.google.com/p/v8/). By keeping up-to-date with the latest releases of this engine we ensure new features from the [JavaScript ECMA-262 specification](http://www.ecma-international.org/publications/standards/Ecma-262.htm) are brought to io.js developers in a timely manner, as well as continued performance and stability improvements.

La versione 1.2.0 di io.js viene rilasciata con la V8 4.1.0.14, che include caratteristiche di ES6 ben oltre la versione 3.26.33
che sarà rilasciata assieme a joyent/node@0.12.x.

Version 1.2.0 of io.js ships with V8 4.1.0.14, which includes ES6 features well beyond version 3.26.33 that will be shipped with joyent/node@0.12.x.

## Il flag --harmony non è più necessario

## No more --harmony flag

Con joyent/node@0.12.x (V8 3.26), il flag di runtime `--harmony` abilita le caratteristiche di ES6 **completed**, **staged** ed **in progress** tutte insieme, in blocco (con l'eccezione delle semantiche non-standard, non-harmony per `typeof`, che sono abilitate dal flag `--harmony-typeof`). Ciò implica che alcune caratteristiche bacate come i [proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) sono disponibili allo stessi livello dei [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), che hanno pochissimi difetti conosciuti o addirittura nessuno. Per questo motivo, sarebbe stato meglio o abilitare solo alcune caratteristiche utilizzando flag specifici, (es. `--harmony-generators`), o semplicemente abilitarle tutte ed usarne un insieme ridotto.


On joyent/node@0.12.x (V8 3.26), the `--harmony` runtime flag enabled all **completed**, **staged** and **in progress** ES6 features together, in bulk (with the exception of nonstandard/non-harmonious semantics for `typeof` which were hidden under `--harmony-typeof`). This meant that some really buggy or even broken features like [proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) were just as readily available for developers as [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), which had very little or even no known-issues. As such, it was best practice to either enable only certain features by using specific runtime harmony feature flags (e.g. `--harmony-generators`), or simply enable all of them and then use a restricted subset.

Con io.js@1.x (V8 4.1+), tutta questa complessità è stata risolta. Tutte le caratteristiche di harmony sono suddivise logicamente in tre gruppi per le caratteristiche **shipping**, **staged** ed **in progress**:

With io.js@1.x (V8 4.1+), all that complexity goes away. All harmony features are now logically split into three groups for **shipping**, **staged** and **in progress** features:

*	Tutte le caratteristiche **shipping**, quelle che V8 considera stabili, come i [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*),i [templates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings),i [nuovi metodi delle stringhe](https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_6_support_in_Mozilla#Additions_to_the_String_object) e molti altri, sono **abilitati di default con io.js** e **NON** richiedono l'uso di nessun flag particolare.

*   All **shipping** features, the ones that V8 has considered stable, like [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), [templates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings), [new string methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_6_support_in_Mozilla#Additions_to_the_String_object) and many others are turned **on by default on io.js** and do **NOT** require any kind of runtime flag.

*	Poi ci sono le caratteristiche **staged**, che sono caratteristiche quasi completate, ma che non sono ancora state testate completamente, o che non sono ancora aggiornate alle ultime versioni della specifica, e quindi non sono considerate stabili dal team di sviluppo di V8 (ad esempio potrebbero esserci dei casi particolari ancora da scoprire).
Questo è probabilmente lo stesso stato dei [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) nella versione 3.26. Queste sono il tipo di caratteristiche "usa a tuo rischio e pericolo" che ora richiedono un flag di runtime: `--es_staging` (o il suo sinonimo, `--harmony`).

*   Then there are **staged** features which are almost-completed features that haven't been completely tested or updated to the latest spec yet and therefore are not considered stable by the V8 team (e.g. there might be some edge cases left to discover). This is probably the equivalent of the state of [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) on 3.26. These are the "use at your own risk" type of features that now require a runtime flag: `--es_staging` (or its synonym, `--harmony`).

*	Infine, tutte le caratteristiche **in progress** possono essere attivate individualmente tramite il loro flag specifico (es. `--harmony_arrow_functions`), nonostante questo sia altamente sconsigliato, se non per finalità di test.

*   Finally, all **in progress** features can be activated individually by their respective harmony flag (e.g. `--harmony_arrow_functions`), although this is highly discouraged unless for testing purposes.


## Quali caratteristiche di ES6 sono attive di default (senza l'uso di nessun flag)?

## Which ES6 features ship with io.js by default (no runtime flag required)?


*   Block scoping

    *   [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

    *   [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

    *   `function`-in-blocks

    >Dalla v8 3.31.74.1, le dichiarazioni block-scoped sono [intenzionalmente implementate con una limitazione al codice in  strict mode che non corrisponde con le specifiche](https://groups.google.com/forum/#!topic/v8-users/3UXNCkAU8Es). Gli sviluppatori devono essere a conoscenza del fatto che questo cambierà man mano che la V8 migliorerà la sua aderenza specifiche ES6.

    >As of v8 3.31.74.1, block-scoped declarations are [intentionally implemented with a non-compliant limitation to strict mode code](https://groups.google.com/forum/#!topic/v8-users/3UXNCkAU8Es). Developers should be aware that this will change as v8 continues towards ES6 specification compliance.

*   Collections

    *   [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

    *   [WeakMap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)

    *   [Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)

    *   [WeakSet](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)

*   [Generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*)

*   [Binary e Octal literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Numeric_literals)

*   [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

*   [Nuovi metodi String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_6_support_in_Mozilla#Additions_to_the_String_object)

*   [Symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)

*   [Stringhe Template](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings)

Puoi trovare una lista più dettagliata, oltre ad un paragone con altri motori, sulla pagina del progetto [compat-table](https://kangax.github.io/compat-table/es6/) .

You can view a more detailed list, including a comparison with other engines, on the [compat-table](https://kangax.github.io/compat-table/es6/) project page.

## Quali caratteristiche di ES6 sono abilitate dal flag --es_staging?

## Which ES6 features are behind the --es_staging flag?

*   [Classi](https://github.com/lukehoban/es6features#classes) (strict mode only)
*   [Object literal extensions](https://github.com/lukehoban/es6features#enhanced-object-literals)

*   [`Symbol.toStringTag`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) (possibilità di definire i risultati di `Object.prototype.toString`)

## La mia infrastruttura è impostata per utilizzare il flag --harmony. Devo rimuoverlo?

il comportamento corrente del flag `--harmony` con io.js è di abilitare solo le caratteristiche **staged**. In effetti è un sinonimo di, `--es_staging`. Come menzionato prima, queste sono caratteristiche completate ma che non sono considerate ancora stabili. Se volete stare sicuri, specialmente in ambienti di produzione, considerate di rimuovere il flag finchè le caratteristiche non saranno disponibili di default su V8 e conseguentemente su io.js. Se mantenete il flag abilitato, preparatevi al fatto che upgrade futuri di io.js potrebbero rovinare il vostro codice, se V8 dovesse cambiare la sua semantica per seguire lo standard più fedelmente.

## I have my infrastructure set up to leverage the --harmony flag. Should I remove it?

The current behaviour of the `--harmony` flag on io.js is to enable **staged** features only. After all, it is now a synonym of `--es_staging`. As mentioned above, these are completed features that have not been considered stable yet. If you want to play safe, especially on production environments, consider removing this runtime flag until it ships by default on V8 and, consequently, on io.js. If you keep this enabled, you should be prepared for further io.js upgrades to break your code if V8 changes their semantics to more closely follow the standard.

## Come posso trovare quale versione di V8 è distribuita con una particolare versione di io.js?

io.js fornisce un modo semplice di elencare tutte le dipendenze e le corrispettive versioni che sono distribuite con una specifica versione dei binari, attraverso l'oggetto globale `process`. Nel caso della V8, scrivete queste istruzioni nel vostro terminale per scoprire la versione:

```sh
iojs -p process.versions.v8
```


## How do I find which version of V8 ships with a particular version of io.js?

io.js provides a simple way to list all dependencies and respective versions that ship with a specific binary through the `process` global object. In case of the V8 engine, type the following in your terminal to retrieve its version:

```sh
iojs -p process.versions.v8
```
