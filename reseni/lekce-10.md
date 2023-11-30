## Hesla

Vytvořte si repozitář ze šablony [cviceni-hesla](https://github.com/Czechitas-podklady-WEB/cviceni-hesla) se stránkou, která obsahuje tři různé funkce na generování hesel. Každá funkce vygeneruje heslo zadané délky s určitou bezpečnostní silou. Kód funkcí zkoumat nemusíte, obsahuje věci, které jsme zatím neprobírali.

Příklad samostatného použití jednotlivých funkcí:

```js
weakPassword(5); // → '01234'
```

```js
mediumPassword(8); // → '48140525'
```

```js
strongPassword(6); // → 'azc7mw'
```

Napište funkci `createAccount`, která se bude tvářit, že zakládá nový uživatelský účet. Funkce bude mít **dva parametry** `user` a `generatePassword`. **První bude uživatelské jméno** a **druhý bude funkce**, pomocí které se má vygenerovat heslo pro tento účet. Funkce `createAccount` **vrátí řetězec**, který bude obsahovat jméno uživatele a heslo vygenerované voláním funkce `generatePassword`. Funkci `generatePassword` při volání předejte **číslo 9** jako délku hesla.

Na konci javascriptového kódu vyzkoušejte založit více různých účtů s různými typy hesel. Například:

```js
document.body.innerHTML += `
	<p>${createAccount('Míša', weakPassword)}</p>
	<p>${createAccount('Řízek', mediumPassword)}</p>
	<p>${createAccount('Mápodčepicí', strongPassword)}</p>
`;
```

by mělo vepsat do stránky něco jako:

```text
Uživatel Míša s heslem 012345678
Uživatel Řízek s heslem 074031827
Uživatel Mápodčepicí s heslem mwwf9epts
```

<details>
<summary><b>Řešení</b></summary>

```js
const createAccount = (user, generatePassword) => {
  return `Uživatel ${user} s heslem ${generatePassword(9)}`;
};

document.body.innerHTML += `
	<p>${createAccount('Míša', weakPassword)}</p>
	<p>${createAccount('Řízek', mediumPassword)}</p>
	<p>${createAccount('Mápodčepicí', strongPassword)}</p>
`;
```

</details>

## E-mail podruhé

Pojďme dále rozvinout cvičení s [vyplňováním e-mailu](/vyvoj-webu/daweb/js1/funkce-obory/cv-funkce/e-mail-telo) z předchozí lekce.

1. Vytvořte si repozitář ze šablony [cviceni-email-podruhe](https://github.com/Czechitas-podklady-WEB/cviceni-email-podruhe).
1. Všimněte si funkce `goodbye`, která generuje pozdrav na konec e-mailu. Přidejte alespoň dvě další funkce, kde každá generuje k zadanému jménu jiný typ pozdravu. Například `formalGoodbye` pro velmi formální pozdravy jako „S uctivou poklonou…“, nebo naopak `rudeGoodbye` typu „Se měj…“, pokud se chcete rozloučit nevybíravě.
1. Upravte funkci `fillBody` tak, aby brala třetí parametr `goodbyeFunction` představující funkci, pomocí které se má vygenerovat závěrečný pozdrav. Vyzkoušejte zavolat funkci `fillBody` postupně s každou z vašich zdravících funkcí a ověřte, že vše správně funguje.

#### Ukázka použití

```js
fillSubject('Obchodní sdělení');
fillBody(
  'Kupte mycí prostředek, který vám vytře zrak, se slevou 50 %.',
  'Jan Čistý',
  formalGoodbye
);
```

nebo

```js
fillSubject('Pozvánka na oslavu narozenin');
fillBody('Zítra oslava. 18:00 ve Starý hospodě.', 'Patrik Veselý', rudeGoodbye);
```

<details>
<summary><b>Řešení</b></summary>

```js
const goodbye = (name) => {
  return 'S pozdravem ' + name;
};

const formalGoodbye = (name) => {
  return 'S uctivou poklonou ' + name;
};

const rudeGoodbye = (name) => {
  return 'Se měj. ' + name;
};

const fillSubject = (subject) => {
  document.querySelector('.email__subject').textContent = subject;
};

const fillBody = (body, name, goodbyeFunction) => {
  const bodyElement = document.querySelector('.email__body');
  bodyElement.innerHTML = body;
  const closingElement = document.querySelector('.email__closing');
  closingElement.textContent = goodbyeFunction(name);
};
```


</details>

## Kalkulačka

Vytvořte si repozitář ze šablony [cviceni-kalkulacka](https://github.com/Czechitas-podklady-WEB/cviceni-kalkulacka) se stránkou, která obsahuje číselník a displej jednoduché kalkulačky.

Zařiďte, aby se při kliknutí na libovolné tlačítko na displeji kalkulačky objevila cifra, která je na tlačíku napsaná. Postupujte dle návodu:

1. Nejprve vyrobte funkci s názvem `handleDigitClick`. To bude posluchač, který později navěsíme na všechna tlačítka.
1. Váš posluchač bude mít jeden parametr představující událost. Z vlastnosti `target` tohoto parametru získejte tlačíko, na které bylo kliknuto. Cifru zjístíte z jeho `textContent`.
1. Jakmile znáte cifru, vložte ji jako `textContent` na displej kalkulačky.
1. Pověste váš posluchač na všechna tlačítka s ciframi.
1. U běžné kalkulačky mačkáním tlačítek postupně sestavujeme nějaké víceciferné číslo. Zařiďte, aby cifry na displeji přibývaly jako na běžné kalkulačce (tj. nově přidaná cifra se přidá doprava, jako je na animaci výše). Také zaříďte, aby se na displej nedalo vložit delší než devíticiferné číslo.

#### Bonus

- Pomocí podmínky `if` zařiďte, aby číslo na displeji nezačínalo nulou, ledaže je tam nula samotná.

<details>
<summary><b>Řešení</b></summary>

```js
const display = document.querySelector('.display');

const handleDigitClick = (event) => {
  if (display.textContent.length >= 9) {
    return; // Uživatel se pokouší zadat delší číslo, než kolik máme číslic na displeji – nedovolíme mu to.
  }
  const digit = event.target.textContent;
  display.textContent += digit;
};

document.querySelector('#btn-0').addEventListener('click', handleDigitClick);
document.querySelector('#btn-1').addEventListener('click', handleDigitClick);
document.querySelector('#btn-2').addEventListener('click', handleDigitClick);
document.querySelector('#btn-3').addEventListener('click', handleDigitClick);
document.querySelector('#btn-4').addEventListener('click', handleDigitClick);
document.querySelector('#btn-5').addEventListener('click', handleDigitClick);
document.querySelector('#btn-6').addEventListener('click', handleDigitClick);
document.querySelector('#btn-7').addEventListener('click', handleDigitClick);
document.querySelector('#btn-8').addEventListener('click', handleDigitClick);
document.querySelector('#btn-9').addEventListener('click', handleDigitClick);
```

#### Bonus

```js
const handleDigitClick = (event) => {
  if (display.textContent.length >= 9) {
    return;
  }
  const digit = event.target.textContent;
  if (display.textContent === '0') {
    display.textContent = digit;
  } else {
    display.textContent += digit;
  }
};
```


</details>

## Newsletter

Podle postupu níže vyrobte stránku podobnou té na obrázku.

1. Založte si HTML stránku s JavaScriptem, třeba následujícím příkazem:
   ```sh
   npm init kodim-app@latest cviceni-newsletter-form html-css-js
   ```
1. Vložte do ní formulář s textovým políčkem a tlačítkem pro přihlášení k odběru.
1. Vytvořte posluchač pro událost `submit`. Jakmile uživatel zadá svůj e-mail a potvrdí přihlášení, zobrazte na stránce místo formuláře zprávu o úspěšném přihlášení k odběru.

1. Texty můžete vymyslet vlastní nebo využít následující:

   - Jednou za týden posíláme newsletter ze světa frontendu a UX.
   - Zadejte svůj e-mail a zůstaňte v obraze.
   - Odebírat
   - Děkujeme za váš zájem. Těšte se na novinky ze světa frontendu a UX na vaší adrese adresa@domena.cz.

1. Pokud máte čas a chuť, nastylujte stránku dle svého citu. Obrázek výše může posloužit jako inspirace.

:::solution

<details>
<summary><b>Řešení</b></summary>

```html
<form>
			<p>Jednou za týden posíláme newsletter ze světa frontendu a UX.</p>
			<p>Zadejte svůj e-mail a zůstaňte v obraze.</p>
			<input type="text" /> <button type="submit">Odebírat</button>
</form>
```

```js
const formular = document.querySelector('form')

const odebirat = (event) => {
	event.preventDefault()
	const input = document.querySelector('input')
	const email = input.value
	formular.textContent = `Děkujeme za váš zájem. Těšte se na novinky ze světa frontendu a UX na vaší adrese ${email}.`
}

formular.addEventListener('submit', odebirat)
```

</details>

## Objednávka

Podle postupu níže vyrobte stránku podobnou té na obrázku.

1. Založte si HTML stránku s JavaScriptem, třeba následujícím příkazem:
   ```sh
   npm init kodim-app@latest cviceni-newsletter-form html-css-js
   ```
1. Vložte do ní formulář s textovým políčkem a tlačítkem pro přihlášení k odběru.
1. Vytvořte posluchač pro událost `submit`. Jakmile uživatel zadá svůj e-mail a potvrdí přihlášení, zobrazte na stránce místo formuláře zprávu o úspěšném přihlášení k odběru.

1. Texty můžete vymyslet vlastní nebo využít následující:

   - Jednou za týden posíláme newsletter ze světa frontendu a UX.
   - Zadejte svůj e-mail a zůstaňte v obraze.
   - Odebírat
   - Děkujeme za váš zájem. Těšte se na novinky ze světa frontendu a UX na vaší adrese adresa@domena.cz.

1. Pokud máte čas a chuť, nastylujte stránku dle svého citu. Obrázek výše může posloužit jako inspirace.

:::solution

<details>
<summary><b>Řešení</b></summary>

```html
<form>
			<p>Jednou za týden posíláme newsletter ze světa frontendu a UX.</p>
			<p>Zadejte svůj e-mail a zůstaňte v obraze.</p>
			<input type="text" /> <button type="submit">Odebírat</button>
</form>
```

```js
const formular = document.querySelector('form')

const odebirat = (event) => {
	event.preventDefault()
	const input = document.querySelector('input')
	const email = input.value
	formular.textContent = `Děkujeme za váš zájem. Těšte se na novinky ze světa frontendu a UX na vaší adrese ${email}.`
}

formular.addEventListener('submit', odebirat)
```

</details>