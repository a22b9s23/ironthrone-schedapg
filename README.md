Nuova Scheda PG
===============

La scheda PG sarà suddivisa in moduli. Il primo modulo sarà quello
dell'intestazione, seguito dalle informazioni generali, le statistiche, talenti
e difetti, le abilità, il mini-modulo dei linguaggi conosciuti,
l'equipaggiamento e la biografia

In ordine si andranno ora a definire quali sono le caratteristiche di ciascun
modulo e in che modo è possibile manipolare i codici per utilizzarne le funzioni
offerte.

Intestazione
------------

Campi d'interesse:

  * Avatar
  * Background
  * Nome Completo
  * Genere

Il codice completo del modulo è il seguente:

```html
<div class="module pg-header no-title" title="NOME-SFONDO">
  <span class="sex"><p title="GENERE"></p></span>
  <span class="avatar"><img style="top: 0px; left: 0px" src="URL-AVATAR"/></span>
  <span class="name"><h1>NOME "SOPRANNOME" COGNOME</h1></span>
</div>
```

### Avatar

L'avatar è l'immagine del prestavolto del PG. Le uniche limitazioni, oltre
quelle imposte dai vari regolamenti gdr (che da ora in avanti verranno
sottintese in ogni loro aspetto) riguardano le dimensioni dell'immagine.

Perché l'immagine sia nitida e non risulti sfocata o stirata, è necessario che
innanzitutto rispetti le dimensioni minime imposte dallo stile in uso
(attualmente 170x170) e inolte è necessario che le dimensioni siano
"quadrate". Questo perché il CSS farà in modo che l'immagine si adatti al suo
contenitore e dimensioni non quadrate rischiano di alterare il risultato finale.

Seppur non vi sia un limite massimo di dimensione, si consiglia di non scegliere
immagini troppo grandi (riducendole prima ove richiesto). Dimensioni
consigliate: 200x200.

Una volta scelta l'immagine, occorre caricarla su un sito di hosting e inserire
l'url al posto della diciture `URL-AVATAR`:

```html
<span class="avatar">
  <img style="top: 0px; left: 0px" src="URL-AVATAR"/>
</span>
```

### Background

L'immagine di background è fornita dallo staff ed è "hard-coded" in CSS. Basterà
modificare il `NOME-SFONDO` con una delle possibilità fornita dallo staff
stesso.

**Attenzione**: Rispettare maiuscole e minuscole è necessario, e anche l'utiizzo
di caratteri speciali come accenti o spazi, dove specificato.

```html
<div class="module pg-header no-title" title="NOME-SFONDO">
```

### Nome Completo

Il campo contiene nient'altro che il nome completo del PG stesso. Non ci sono
particolari indicazioni a riguardo. Per modificarlo, rimpiazzare il testo
all'interno dell'elemento `<h1>...</h1>`.

```html
<span class="name">
  <h1>NOME "SOPRANNOME" COGNOME</h1>
</span>
```
### Genere

Il genere può essere espresso con due possibilità. `Maschio` o `Femmina`. Anche
in questo caso occorre rispettare le minuscole e le maiuscole e basta modificare
l'apposito campo:

```html
<span class="sex"><p title="GENERE"></p></span>
```

Informazioni Generali
---------------------

Campi d'interesse:

  * Religione
  * Regione
  * Età
  * Status Sociale
  * Esperienza
  * Ricchezza
  * Punti Ferita
  * Valore Stordimento
  * Classi

La modifica della maggior parte dei campi in questa porzione di codice, è
abbastanza intuitiva. Ci si sofferma invece sugli ultimi 3 campi la cui modifica
può risultare un po' meno intuitiva. In tutti gli altri casi basta ricercare il
campo e modificare il testo all'interno del `<dd>...</dd>` corrispondente.

### Punti Ferita e Valore di Stordimento

La modifica dei suddetti campi può essere effettuata agendo sul valore
all'interno dell'elemento `<div class="value"><span>...</span></div>`. Per
esempio, si voglia assegnare un valore di `10` ai punti ferita:

```html
<div class="reduced-ironbox" style="grid-template-areas: 'name' 'value'; grid-template-columns: auto;">
  <div class="name"><span>Punti Ferita</span></div>
  <div class="value"><span>10</span></div>
</div>
```

La modifica del valore di stordimento è analoga.

### Classi

Per poter rappresentare molteplici classi a cui può appartenere un PG senza
dover appesantire troppo la scheda stessa, si è optato per una sorta di
contenitore scorrevole di "bottoni", ognuno dei quali rappresenta la classe e il
relativo livello.

Esprimere l'appartenza di un PG ad una determinata classe, diventa una
manipolazione degli elementi all'interno di questa lista. Il codice di base
dell'elemento, senza classi, è il seguente:

```html
<div class="reduced-ironbox classes">
  <div class="name"><span>Classi</span></div>
  <div class="modifier-list">...</div>
</div>
```

Le classi di appartenenza sono contenute all'interno dei puntini del `<div
class="modifier-lsit">...</div>`, e ogni elemento deve la seguente forma:

```html
<div>
  <div class="name"><a href="URL-CLASSE">NOME-CLASSE</div>
  <div class="value">VALORE</div>
</div>
```

Gli elementi in maiuscolo sono quelli da modificare. Al posto di `URL-CLASSE`
occorre inserire l'indirizzo della pagina completa della classe.


Statistiche
-----------

Campi d'interesse:

  * Forza
  * Destrezza
  * Costituzione
  * Intelligenza
  * Saggezza
  * Carisma

Ogni campo di questo modulo ha esattamente lo stesso comportamento, dunque basta
descriverne uno per capire come manipolare anche il resto. Ogni elemento
appartiene inanzitutto alla classe CSS `simple-ironbox` che per come è stata
definita, ha la seguente struttura:

  * Icona
  * Nome
  * Valore
  * Lista modificatori

È bene fare un po' di attenzione a queste 4 componenti perché torneranno anche
in seguito in modo simile per talenti, difetti ed equipaggiamento. Il codice di
un singolo elemento di questo tipo è il seguente (i puntini sono stati inseriti
in punti che verranno approfonditi subito dopo):

```html
<div class="simple-ironbox">
  <div class="icon">...</div>
  <div class="name">...</div>
  <div class="value">...</div>
  <div class="modifier-box">...</div>
</div>
```

### Icona

Il primo campo che compare è quello dell'icona. All'interno degli stili,
l'immagine inserita in questo campo verrà stirata e adattata alle dimensioni di
50x50px. Le raccomandazioni rimangono le stesse fatte per l'avatar, anche se in
questo caso le dimensioni consigliate sono di 75x75.

Per inserire l'immagine basta completare l'apposito campo con il seguente
codice:

```html
<div class="icon"><img src="LINK-IMMAGINE"></div>
```

### Nome e Valore

Il nome (o titolo) e il valore possono essere inseriti modificando gli appositi
campi con il testo desiderato all'interno del tag `<span>...</span>`:

```html
<div class="name"><span>NOME</span></div>
<div class="value"><span>VALORE</span></div>
```

### Lista Modificatori

Ogni modificatore associato all'elemento, può essere espresso all'interno di
questa lista che in CSS appartiene alla classe `modifier-box`. Gli elementi che
appartengono a questa classe definiscono:

  * Valore Somma, che rappresenta la somma dei modificatori.
  * Lista modificatori vera e propria.

Il codice completo di uno scatolotto di modificatori è il seguente:

```html
<div class="modifier-box">
  <div class="modifier"><span>VALORE-SOMMA</span></div>
  <div class="modifier-list">...</div>
</div>
```

Per il primo valore basta sostituire il testo `VALORE-SOMMA` con il valore
calcolato. Per inserire un modificatore in lista, occorre aggiungere al posto
dei puntini il seguente codice:

```html
<div>
  <div class="name">NOME-MODIFICATORE</div>
  <div class="value">VALORE</div>
</div>
```

Sostituendo gli oppportuni campi si ottiene l'elemento da aggiungere in lista. È
chiaro che, trattandosi di una lista, è possibile specificare anche più di un
modificatore, come nel caso delle classi PG. In caso occorra specificare più di
un modificatore, basta aggiungerli uno dopo l'altro al posto dei puntini,
facendo attenzione ad aprire e chiudere i tag in modo opportuno per evitare di
incorrere in problemi di visualizzazione con l'intera scheda.

**Nota**: I valori negativi sono gestiti in modo particolare dal codice. Per
inserire un valore negativo, basta l'elemento del valore cambia nel seguente:

```html
<div class="value negative">VALORE</div>
```

In poche parole, si aggiunge una classe all'elemento che ne rappresenta la
negatività. Questo farà in modo che il valore venga visualizzato in contrasto
con i valori positivi.

**Attenzione**: In caso di valori negativi, non bisogna aggiungere il carattere
`-` all'interno del campo valore. Questo perché sarà automaticamente fatto
mediante CSS, che si occuperà di aggiungere un `-` davanti alle cifre in caso di
valori negativi, o un `+` in caso di valori positivi.

Esempio per rappresentare un `-10` (notare come non è necessario inserire il
segno davanti alla prima cifra):

```html
<div class="value negative">10</div>
```

### Codice di Esempio Completo

Ora che abbiamo visto le singole componenti, possiamo analizzare un esempio
concreto tratto direttamente dalla statistica *Forza* presente in scheda:

```html
<div class="simple-ironbox">
  <div class="icon"><img src="#link-icona-forza"></div>
  <div class="name"><span>Forza</span></div>
  <div class="value"><span>0</span></div>
  <div class="modifier-box">
    <div class="modifier"><span>0</span></div>
    <div class="modifier-list">
      <div><div class="name">Modificatore Positivo</div><div class="value">1</div></div>
      <div><div class="name">Modificatore Negativo</div><div class="value negative">1</div></div>
    </div>
  </div>
</div>
```



Talenti e Difetti
-----------------

Campi d'interesse:

  * Icona
  * Nome
  * Annotazione

Il modulo di talenti e difetti è quello racchiuso all'interno dell'elemento:

```html
<div class="module talents no-show" title="Talenti e Difetti">
  <div class="info-container">
    <div class="simple-container no-value"><dt>Talenti</dt><dd>...</dd></dl></div>
    <div class="simple-container no-value"><dt>Difetti</dt><dd>...</dd></dl></div>
  </div>
</div>
```

Come sarà descritto di seguito, i primi puntini sono per i talenti, i secondi
per i difetti. L'intero modulo appartiene a 3 classi in totale, le prime due,
`module` e `talents` identificano il modulo corrente. La terza, vista qui per la
prima volta, `no-show`, rende trasparente il background del modulo. Questo per
aggiungere un po' di contrasto con il resto della scheda.

**OSS**: Per aggiungere il background presente invece nei moduli precedenti,
basta rimuovere la classe `no-show` e lasciarci le prime due.

L'aggiunta di talenti o difetti è analoga, e basta inserire il seguente elemento
al posto dei puntini:

```html
<div class="box-item">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
  <div class="name"><span>NOME-ELEMENTO</span></div>
  <div class="annotation"><span>ANNOTAZIONI-ELEMENTO</span></div>
</div>
```

### Icona

L'elemento destinato ad accogliere l'icona si comporta in modo analogo a quanto
descritto per le statistiche. Le dimensioni ne risentono in questo caso, e sono
fissate, dagli stili correnti, a 30x30.

**NB**: È possibile rimuovere completamente l'icona eliminando l'elemento
corrispondente:

```html
<div class="icon"><img src="#URL-IMMAGINE"/></div>
```

### Nome

È possibile modificare il nome del talento agendo sul testo all'interno
dell'elemento `<span>...</span>` del campo corrispondente.

### Annotazione

L'annotazione è un campo opzionale di dimensioni massime fissate destinata a
contenere maggiori informazioni sul talento o sul difetto in questione. Essendo
un campo opzionale, può essere rimosso tranquillamente dall'elemento. In caso,
invece, ci sia necessità di fornire maggiori informazioni, il testo dev'essere
inserito all'interno del campo `<span>...</span>` dell'elemento corrispondente.

### Esempi

Si vuole creare un talento (o difetto) chiamato "Test", senza icona e senza
annotazioni:

```html
<div class="box-item">
  <div class="name"><span>NOME-ELEMENTO</span></div>
</div>
```

Si vuole creare un talento (o difetto) chiamato "Test", con un icona (non
specificata nell'esempio), ma senza annotazione:

```html
<div class="box-item">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
  <div class="name"><span>NOME-ELEMENTO</span></div>
</div>
```

Abilità
-------

Campi di interesse:

  * Nome
  * Valore

Le abilità differiscono da talenti e difetti in quanto a visualizzazione su
scheda e funzionalità. Una singola abilità è descritta da un nome e un livello
corrispondente (quando presente).

```html
<div class="module perks no-show" title="Abilità">
  <div class="info-container">
    <dl class="simple-container"><dt>Abilità</dt><dd>
	  ...
    </dd></dl>
  </div>
</div>
```

### Elemento Abilità

Inserire un'abilità equivale ad aggiungere in lista, al posto dei puntini, un
elemento così descritto:

```html
<div class="button">
  <div class="name"><span>NOME-ABILITÀ</span></div>
  <div class="value"><span>VALORE</span></div>
</div>
```

È possibile che un'abilità non abbia un livello associato. In tal caso, il campo
del valore può essere omesso ed è necessario aggiungere la classe `no-value`
all'elemento, che si trasformerebbe nel seguente modo:

```html
<div class="button no-value">
  <div class="name"><span>NOME-ABILITÀ</span></div>
</div>
```

Linguaggi Conosciuti
--------------------

Campi d'interesse:

  * Nome
  * Parlato/Scritto

Quello dei linguaggi conosciuti è un piccolo modulo destinato a quel tipo di
abilità speciali che rappresentano il grado di conoscenza di un linguaggio. Il
modulo è descritto all'interno del codice:

```html
<div class="module language-skill no-show" data-title="Languages">
  <div class="info-container">
    <dl clas="simple-container"><dt>Linguaggi Conosciuti</dt><dd>
      ...
    </dd></dl>
  </div>
</div>
```

### Elemento Linguaggio

Un linguaggio conosciuto è rappresentato in scheda attraverso il nome del
linguaggio stesso e il grado di conoscenza. Due sono i gradi di conoscenza:
parlato e scritto. Un PG può essere in grado di esercitare entrambi, o solo uno
dei due.

L'elemento da aggiungere in lista, che rappresenta la conoscenza completa di un
linguaggio (parlato e scritto) è il seguente:

```html
<div class="box-item">
  <div class="name"><span>NOME-LINGUAGGIO</span></div>
  <div class="speak"></div>
  <div class="write"></div>
</div>
```

Il grado di conoscenza è rappresentato dalla presenza o meno dei due campi
successivi al nome, `speak` (parlato) e `write` (scritto). Si può rappresentare
un grado di conoscenza diverso semplicemente rimuovendo uno dei due campi.

Per esempio, un linguaggio parlato, ma non scritto, è rappresentato rimuovendo
il campo `write`:

```html
<div class="box-item">
  <div class="name"><span>NOME-LINGUAGGIO</span></div>
  <div class="speak"></div>
</div>
```

In modo analogo, se si vuole rimuovere il campo `speak`.

Equipaggiamento e Oggetti
-------------------------

Campi d'Interesse:

  * Icona
  * Nome
  * Peso
  * Quantità
  * Annotazione
  * Proprietà Particolari

Il modulo è descritto dal codice:

```html
<div class="module inventory no-show" data-title="Equipaggiamento e Oggetti">
  <div class="info-container">
    <dl class="simple-container"><dt>Equipaggiamento</dt><dd>
      <div class="inventory-panel">
        ...
      </div>
      <div class="armor-panel">
        ...
      </div>
    </dd></dl>
  </div>
</div>
```

I due puntini indicano rispettivamente la locazione degli oggetti in inventario
e la visualizzazione dei valori di difesa delle parti d'armatura. Il pannello
armatura sarà l'ultimo descritto in questa sezione. Per prima cosa, si procede
con la descrizione di un singolo elemento da inserire in inventario (dunque
all'interno dei primi puntini). Un esempio completo è il seguente:

```html
<div class="box-item">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
  <div class="name"><span>NOME-OGGETTO</span></div>
  <div class="weight"><span>PESO</span></div>
  <div class="quantity"><span>QUANTITÀ</span></div>
  <div class="annotation"><span>ANNOTAZIONI</span></div>
</div>
```

### Icona

Le raccomandazioni sono analoghe a quelle di talenti e difetti. Può essere
omessa rimuovendo per intero il campo corrispondente.

### Nome

Non ci sono raccomandazioni particolari riguardo il nome.

### Peso

È un valore numerico decimale. Non dev'essere specificata l'unità di misura. Può
essere omesso se l'oggetto non ha un peso specifico.

### Quantità

È un valore numerico intero. Può essere omessa quando si assume un valore
unitario.

### Annotazione

Le raccomandazioni sono analoghe a quelle di talenti e difetti. Il campo può
essere omesso rimuovendo l'intero campo corrispondente.

### Proprietà Particolari

Alcuni oggetti godono di proprietà specifiche. Un esempio di queste sono armi e
armature che hanno il loro modo per descrivere valori di attacco o di
difesa. Esistono tre tipi di oggetti speciali attualmente (che possono essere
completati con le caratteristiche descritte sopra aggiungendo o rimuovendo campi
opzionali). Sono oggetti speciali che godono di proprietà particolari, ma sono
comunque oggetti che possono essere tranquillamente inseriti in lista con il
seguente codice:

#### Arma

```html
<div class="box-item tag-weapon">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
  <div class="name"><span>NOME-ARMA</span></div>
  <div class="weight"><span>PESO</span></div>
  <div class="damage"><span>DANNO-ARMA</span></div>
</div>
```

#### Armatura

```html
<div class="box-item tag-armor">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
  <div class="name"><span>NOME-ARMATURA</span></div>
  <div class="weight"><span>PESO</span></div>
  <div class="dmg-reduction"><span>RIDUZIONE-DANNI</span></div>
  <div class="test-penalty"><span>PENALITÀ-PROVA</span></div>
  <div class="hardness"><span>DUREZZA</span></div>
  <div class="wound-points"><span>PUNTI-FERITA</span></div>
</div>
```

#### Scudo

```html
<div class="box-item tag-shield">
  <div class="icon"><img src="#URL-IMMAGINE"/></div>
   <div class="name"><span>NOME-SCUDO</span></div>
   <div class="weight"><span>PESO</span></div>
   <div class="dmg-reduction"><span>RIDUZIONE-DANNI</span></div>
   <div class="armor-bonus"><span>BONUS-ARMATURA</span></div>
   <div class="test-penalty"><span>PENALITÀ-PROVA</span></div>
</div>
```

### Pannello Armatura

Il pannello rende facile l'associazione tra diverse parti del corpo e il valore
di difesa corrispondente. Ci sono in totale 7 campi da completare e il seguente
codice dev'essere inserito all'interno dei secondi puntini:

```html
<div class="silhouette">
  <div class="head"><span>VALORE-TESTA</span></div>
  <div class="torso"><span>VALORE-TORSO</span></div>
  <div class="right-arm"><span>VALORE-BRACCIO-DESTRO</span></div>
  <div class="left-arm"><span>VALORE-BRACCIO-SINISTRO</span></div>
  <div class="right-leg"><span>VALORE-GAMBA-DESTRA</span></div>
  <div class="left-leg"><span>VALORE-GAMBA-SINISTRA</span></div>
  <div class="shield"><span>VALORE-SCUDO</span></div>
</div>
```

Il valore di default per parte è sempre `0`.

Biografia
---------

Campi d'interesse:

  * Descrizione Fisica
  * Storia e Psicologia

L'ultimo modulo è (attualmente) quello biografico, descritto dal codice:

```html
<div class="module biography" title="Biografia">
  <div class="info-container">
    <dl class="text-area">
      <dt>Descrizione Fisica</dt>
      <dd>TESTO-DESCRIZIONE-FISICA</dd>
    </dl>
    <dl class="text-area">
      <dt>Storia e Psicologia</dt>
      <dd>TESTO-STORIA-PSICOLOGIA</dd>
    </dl>
  </div>
</div>
```

Non ci sono raccomandazioni particolari. Le parti da modificare sono, come negli
altri casi, quelle in maiuscolo.
