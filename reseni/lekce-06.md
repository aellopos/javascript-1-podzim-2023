## Základní validace

1. Vytvořte prázdnou stránku, do které vložte knihovnu `validator.js` a svůj JavaScript `index.js`.
1. Ověřte pomocí metody `validator.isEmail` platnost vaší e-mailovou adresu.
1. Pokud máte po ruce **platební kartu**, ověřte, že má platné číslo pomocí metody `isCreditCard`. Případně můžete otestovat kartu **4125010001000208**.
1. Do těla stránky vložte prázdný odstavec, který bude zobrazovat zprávu pro uživatele.
   ```html
   <p id="msg" class="msg"></p>
   ```
1. Napojte do stránky váš vlastní javascriptový soubor `index.js`.
1. Pomocí funkce `prompt` **požádejte uživatele o jeho e-mail**. V případě, že jde o platný e-mail, zobrazte v připraveném odstavci zprávu „**E-mail v pořádku**“. V opačném případě zobrazte „**Neplatný e-mail**“.
1. Pokud je e-mail platný, přidejte zároveň na odstavec CSS třídu `msg--valid`. V opačném případě použijte třídu `msg--invalid`. Přidejte do stránky soubor `style.css` a třídy nastylujte například tak, že `msg--valid` bude mít zelené pozadí a `msg--invalid` naopak červené.

   ```html
   <!-- index.html -->
   <link rel="stylesheet" href="style.css" />
   ```

   ```css
   /* style.css */
   .msg {
     color: white;
     padding: 10px;
   }
   .msg--valid {
     background-color: green;
   }
   .msg--invalid {
     background-color: red;
   }
   ```

1. Stránku postupně otestujte zadáním platné i neplatné adresy.

<details>
<summary><b>Řešení</b></summary>


```js
const email = prompt('Zadejte váš e-mail');

const isEmail = validator.isEmail(email);
const messageElement = document.querySelector('#message');

if (isEmail) {
  messageElement.textContent = 'E-mail v pořádku';
  messageElement.classList.add('msg--valid');
} else {
  messageElement.textContent = 'Neplatný e-mail';
  messageElement.classList.add('msg--invalid');
}
```


</details>

## Mimozemský život

Podívejte se na stránku [existuje-mimozemsky-zivot.cz](https://existuje-mimozemsky-zivot.cz/). Podle toho, v jakém období toto zadání čtete, se dozvíte, zda jsme již objevili život mimo planetu Zemi. Stránka zobrazuje pouze jednoduchou zprávu. Podobných stránek lze na internetu najít vícero. Například

- [sediuzbabis.cz](https://sediuzbabis.cz)
- [uzjepatek.cz](https://uzjepatek.cz)

Vytvořte podobnou stránku s vaším vlastním tématem.

1. Vytvořte prázdnou stránku, do které vložte knihovnu `Day.js`.
1. Vyberte si nějakou budoucí událost, jejíž datum je pevně určeno. Za pomoci knihovny `Day.js` vytvořte stránku zobrazující velké _ANO_ nebo _NE_ případně krátkou zprávu podle toho, zda už událost nastala či nikoliv.

#### Bonus

1. Publikuje vaši stránku přes [GitHub Pages](https://pages.github.com/) (případně [Netlify drop](https://app.netlify.com/drop) či jinou alternativu, pokud je znáte).

<details>
<summary><b>Řešení</b></summary>


```js
const today = dayjs();
const aliensFoundDate = dayjs('2042-11-06');
const pageTitleEl = document.querySelector('h1');

if (today.isAfter(aliensFoundDate)) {
  pageTitleEl.textContent = 'Mimozemšťané konečně objeveni!';
} else {
  pageTitleEl.textContent = 'Mimoze-co? Nevím, o čem to mluvíte.';
}
```


</details>

## Obsah elipsy

Zlovolní zahrádkáři nám chtějí ztížit výměru pozemků a proto si pořídíli pozemek ve tvaru elipsy.

![ellipse.png](../images/ellipse.png)

Z matematiky víme, že známe-li šířku a výšku elipsy, její obsah je _polovina šířky_ krát _polovina výšky_ krát _číslo π_ (tj. přibližně 3,14).

Založte si prázdnou stránku s JavaScriptovým souborem a napište funkci `ellipseArea`, která spočítá (**vrátí**) plochu pozemku dle zadané šířky a výšky. Číslo π najdete v JavaScriptu v proměnné `Math.PI`.

Funkci `ellipseArea` otestujte (např. pomocí `document.body.innerHTML +=` vypište výsledek volání pro různé hodnoty do stránky).

- Pro šířku `1` a výšku `2` by mělo vyjít `1.5707963267948966`.
- Pro `2` a `2` pak `3.141592653589793`.
<details>
<summary><b>Řešení</b></summary>


```js
const ellipseArea = (width, height) => {
  return (width / 2) * (height / 2) * Math.PI;
};

document.body.innerHTML += `<p>${ellipseArea(1, 2)}</p>`;
document.body.innerHTML += `<p>${ellipseArea(2, 2)}</p>`;
```



</details>

## Maximum ze dvou čísel

Napište funkci `max2`, která **vrátí větší ze dvou zadaných čísel**. V JavaScriptu už na toto funkce existuje, jmenuje se `Math.max`. Pro účely tohoto příkladu se budeme tvářit, že o ní nevíme.


<details>
<summary><b>Řešení</b></summary>


```js
const max2 = (a, b) => {
  if (a > b) {
    return a;
  } else {
    return b;
  }
};
```

</details>

## Kontrola DIČ

Všimněte si, že knihovna `validator.js` v době vzniku tohoto zadání neumí ověřit platnost českého DIČ (daňové identifikační číslo). Zkusme tedy takovou funkci napsat.

Formát DIČ sestává z předpony CZ a poté následuje devět nebo deset číslic. Tedy například

- CZ123456789
- CZ1234567890

Postupujte dle následujících kroků:

1. Vytvořte prázdnou stránku s JavaScriptem a knihovnou `validator.js`.
1. Vytvořte funkci `isDIC` s jedním parametrem `inputStr`, což bude řetězec, který chceme zkontrolovat.
1. Jako první ve funkci zkontrolujte, jestli je vstupní řetězce kratší než 11 znaků. V takovém případě nemá smysl dál nic dělat, protože vstup evidentně není DIČ. Vraťte tady z funkce `false`. Tím naše funkce končí. Všimněte si, že takto používáme vzor _časný návrat_.
1. Dále ve funkci zkontrolujte, jestli je vstupní řetězce delší než 12 znaků. V takovém případě opět vraťte `false`.
1. Dále si ve funkce do proměnné `prefix` uložte první dva znaky vstupního řetězce.
1. Pomocí podmínky zkontrolujte, že proměnná `prefix` obsahuje přesně znaky `CZ`. Pokud ne, ihned vraťte `false`.
1. Do promměné `digits` si uložte část vstupního řetězce od třetího znaku dále.
1. Použijte metodu `validator.isInt`, která umí zkontrolovat, zda řetězec obsahuje pouze číslice. Pokud metoda vrátí `false`, ihned také vraťte `false`.
1. Pokud funkce dospěla až do tohoto bodu, vstup prošel všemi testy. Můžeme vrátit `true`.
1. Vyzoušejte svoji funkci na různých vstupech a ověřte, že funguje. Nezapomeňte ověřit platná i neplatná DIČ.

#### Příklady platných DIČ:

- CZ123456789
- CZ1234567890

#### Příklady neplatných DIČ:

- 123
- ABC
- 1234567890
- 001234567890
- 1234567890CZ
- CZ12345678901
- CZ12345678
- CZA12345678



<details>
<summary><b>Řešení</b></summary>

```js
const isDIC = (inputStr) => {
  // kontrola délky
  if (inputStr.length < 11) {
    return false;
  }
  if (inputStr.length > 12) {
    return false;
  }

  // kontrola prefixu CZ
  const prefix = inputStr.slice(0, 2);
  if (prefix !== 'CZ') {
    return false;
  }

  // kontrola, že za prefixem jsou jen číslice
  const digits = inputStr.slice(2);
  if (!validator.isInt(digits)) {
    return false;
  }

  return true;
};
```

</details>