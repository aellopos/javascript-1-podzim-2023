## Opakování DOM

1) JavaScriptem změň text nadpisu.
	
2) JavaScriptem změnit barvu nadpisu.
	 (CSS vlastnost: color)

3) Zvětšit velikost písma odstavce a/nebo ho udělat tučně nebo kurzívou.
	 (CSS vlastnosti: font-size, font-weight, font-style)

4) Vyměnit obrázek kočky za psa. Koček je všude dost, nepotřebujeme tu další.
	 (HTML atribut: src)

5) Přesunout čtvereček na jiné místo nebo ho otočit.
	 (nastav CSS vlastnost position na hodnotu 'absolute' a pak můžeš měnit
	 pozici prvku pomocí CSS vlastností top a left)

6) Vytvoř v CSS třídu s nějakými CSS vlastnostmi a zkuš ji přidat na libovolný
	 prvek na stránce.
	 (v CSS nastav třídě třeba barvu pozadí.)

<details>
<summary><b>Řešení</b></summary>

Obsah souboru `index.js`:

```js
const nadpis = document.querySelector("#nadpis");
nadpis.textContent = "Můj nový nadpis";
nadpis.style.color = "red";


const obrazek = document.querySelector("#foto");
obrazek.src = "pes.jpg";


const ctverecek = document.querySelector(".ctverecek");
ctverecek.style.position = "absolute";
ctverecek.style.top = "200px";
ctverecek.style.left = "350px";


const nadpis2 = document.querySelector("h2");
nadpis2.classList.add("pozadi");
```

</details>

## Eventy

Úkoly v tomto cvičení:
1) Při kliknutí myší na čtvereček ho otoč o 45 stupňů.
	 Budeš potřebovat událost click, vybrat čtvereček
	 na stránce a změnit mu příslušné vlastnosti.

2) Zkus čtvereček při druhém kliknutí zase vrátit zpátky.
	 Buď si musíš někde poznačit, je-li čtvereček otočený nebo ne
	 a podle toho mu správně měnit vlastnosti.
	 Nebo můžeš otočení čtverečku nastavit v CSS třídě, kterou budeš
	 na element přidávat nebo z něho odebírat. Když použijet pro
	 přepínání třídy metodu toggle, máš vše skoro bez práce.
	 Vyber si postup, který tobě připadá nejlépe pochopitelný.

3) Při stisknutí klávesy změň čtverečku barvu.
	 Budeš potřebovat událost keydown. Mysli na to, že tyto události
	 nelze nastavovat konkrétním elementům, ale musíš je nastavit pro
	 celou stránku na elementu <body>. (Je to logické. Jak bys stiskla
	 klávesu jen nad konkrétním elementem?)

	 Pokud chceš reagovat na konkrétní klávesu (a ne na stisk libovolné),
	 budeš si muset do obslužné funkce pro událost předat i objekt event,
	 který má vlastnost key, ve které je kód stisknuté klávesy.

<details>
<summary><b>Řešení</b></summary>

Obsah souboru `index.js`:

```js
const ctverecek = document.querySelector(".ctverecek");
ctverecek.addEventListener("click", () => {
	ctverecek.classList.toggle("otoceno");
})



const priStiskuKlavesy = (e) => {
	let ctverecek = document.querySelector(".ctverecek");

	console.log(e.key);
	if (e.key === "ArrowDown") {
		ctverecek.classList.toggle("pozadi");
	}
}

let body = document.querySelector("body");
body.addEventListener("keydown", priStiskuKlavesy);
```

</details>

## Piškvorky

Naprogramuj piškvorky. Na stránce máš vytvořenou tabulku
o velikosti 5x5 buňek, která má id="deska"<div className="">

Úkoly:

1) Reaguj na kliknutí na buňku v tabulce. Abychom nemuseli
událost click přidávat na každou buňku, přidáme ji pouze
na celou tabulku. Musíme potom rozpoznat, na kterou buňku
se ve skutečnosti kliklo.
Pomůže ti opět objekt event, který můžeš předat jako parametr
do funkce, která kliknutí obsluhuje. Objekt event má vlastnost
target, ve které je uložený odkaz na buňku.

2) Do prvku s id="natahu" zapiš, který hráč má aktuálně hrát.
Jestli X nebo O.

3) Po kliknutí do buňky zapiš znak hráče. X nebo O. Musíš zařídit,
aby se hráči střídali - tj. při prvním kliknutí se bude zapisovat X,
potom O, pak znovu X, atd.

4) Zařiď, aby se nezapisoval znak do buňky, pokud už v ní něco je.
Doposud šlo kliknout na buňku, kde už bylo X a zapsat do ní O.

5) Testování, zda jeden z hráčů vyhrál je poměrně složité a vysoko
nad znalosti získané z toho workshopu. Testování výhry máš ale od nás
připravené. Stačí na konci HTML odkomentovat připojení skriptu vyhra.js.

Pak můžeš ve svém programu použít funkci vyhral(hrac), která vrací hodnotu
true nebo false, zda daný hráč vyhrál.

Pokuid tedy budu chtít otestovat, zda vyhrál hráč X, můžu v kódu napsat:
if ( vyhral("X") ) {
	...
}

Na řádku 6 v souboru vyhra.js si můžeš nastavit, kolik stejných symbolů
vedle sebe stačí pro výhru. Standardně je nastaveno 3.

<details>
<summary><b>Řešení</b></summary>

Obsah souboru `index.js`:

```js
let aktualniHrac = "X";

const hraje = document.querySelector("#hraje");
const natahu= document.querySelector("#natahu");
const tabulka = document.querySelector("#deska")
natahu.textContent = aktualniHrac;


const priKliknuti = (event) => {

	let bunka = event.target;

	if (bunka.textContent === "") {
		bunka.textContent = aktualniHrac;

		if (vyhral(aktualniHrac)) {
			hraje.textContent = "Hráč " + aktualniHrac + " vyhrál!";
		}

		if (aktualniHrac === "X") {
			aktualniHrac = "O";
		} else {
			aktualniHrac = "X";
		}
		natahu.textContent = aktualniHrac;

	}

}

tabulka.addEventListener("click", priKliknuti)
```

</details>