## Vlastnosti a metody

V JavaScriptovém programu si založte proměnnou `title` a uložte do ní **název svého oblíbeného filmu** (např. _Pán prstenů_). Proveďte následující úkoly.

1. Vypište do stránky **počet znaků** názvu.
1. Vypište název filmu převedený na **velká písmena**.
1. Vypište z názvu **prvních pět** písmen.
1. Vypište z názvu **posledních pět** písmen.

<details>
<summary><b>Řešení</b></summary>


```js
const title = "Lord of the Rings";​
document.body.innerHTML += title.length;
​document.body.innerHTML += `<br>`;​
​document.body.innerHTML += title.toUpperCase();​
​document.body.innerHTML += `<br>`;​
​document.body.innerHTML += title.slice(0, 5);
​document.body.innerHTML += `<br>`;​
​document.body.innerHTML += title.slice(title.length - 5, title.length)Ł
```


</details>

## E-maily

Vytvořte stránku, která bude pracovat s e-mailovými adresami ve formátu

```
jmeno.prijmeni@domena
```

Tedy například:

- `petr.novak@gmail.com`
- `romana.nejedla@czechitas.cz`
- `slavomir.ponuchalek@yahoo.com`

Postupujte dle následujících kroků.

1. Vytvořte jednoduchou webovou stránku s JavaScriptovým programem.
1. Nechte uživatele zadat jeho e-mail a uložte si jej do proměnné `email`.
1. Pomocí metody `indexOf` najděte v tomto e-mailu pozici znaku zavináč. Tuto pozici si uložte do proměnné `atIndex`.
1. Pomocí metody `slice` získejte z e-mailu první část představující uživatelské jméno uživatele.
1. Dále z e-mailu získejte název domény tedy například `gmail.com`.
1. Ze získaných informací vytvořte objekt, který bude vypadat například takto:
   ```js
   const parsedEmail = {
     userName: 'slavomir.ponuchalek',
     domain: 'yahoo.com',
   };
   ```
1. Pro kontrolu vypište tento objekt do stránky. Každou hodnotu vypište jako odstavec.

<details>
<summary><b>Řešení</b></summary>


```js
const email = prompt('Zadejte e-mail:');
const atIndex = email.indexOf('@');
const parsedEmail = {
  userName: email.slice(0, atIndex),
  domain: email.slice(atIndex + 1),
};
document.body.innerHTML =
  '<p>Uživatelské jméno: ' + parsedEmail.userName + '</p>';
document.body.innerHTML += '<p>Doména: ' + parsedEmail.domain + '</p>';
```


</details>

## Doručování

Vytvořte webovou stránku, kde uživatel zadá svoji adresu například pro účely doručení objednaného zboží. Požaduje **ulici**, **číslo domu**, **město** a **PSČ**.

1. Uložte všechny údaje do vhodně pojmenovaných proměnných.
1. Ze zadanách údajů sestavte pomocí interpolace řetězeců obsahující HTML ve formátu jako níže
   ```html
   <address>
     <p>Pod Stájemi 67</p>
     <p>12754 Klysnov</p>
   </address>
   ```
1. Pomocí `document.body.innerHTML` vložte sestavené HTML do stránky.

<details>
<summary><b>Řešení</b></summary>


```js
const street = prompt('Zadejte ulici:');
const houseNumber = prompt('Zadejte číslo domu:');
const city = prompt('Zadejte město:');
const zipCode = prompt('Zadejte PSČ:');

document.body.innerHTML = `
   <address>
      <p>${street} ${houseNumber}</p>
      <p>${zipCode} ${city}</p>
   </address>
`;
```


</details>

## Registrace na očkování

V předchozí lekci jsem vytvářeli stránku pro registraci na očkování. Chtěli jsme po uživateli jméno a věk. Nyní budeme chtít, aby uživatel zadal také heslo. To bychom v pozdější verzi aplikaci mohli použít například k přihlášení do systému.

Vytvořte novou stránku, nebo pokračujte ve stránce z předchozí lekce pro registraci na očkování.

1. Nejdříve nechte uživatele zadat všechny hodnoty, tedy **jméno**, **věk** i **heslo**. Uložte si je do dobře pojmenovaných proměnných.
1. Napište první podmínku, ve které zkontrolujte, že věk uživatele je větší nebo roven 65. Pokud ano, vypište do stránky „věk v pořádku“. Pokud uživateli není alespoň 65 let, vypište „nízký věk“.
1. Napište druhou podmínku, která zkontroluje, zda je zadané heslo delší než osm znaků. Pokud není, vypište „slabé heslo“. Heslo se bude kontrolovat pouze v případě, kdy uživatel splnil první podmínku (věk alespoň 65 let).

<details>
<summary><b>Řešení</b></summary>


```js
const name = prompt('Zadejte své jméno:');
const age = Number(prompt('Zadejte svůj věk:'));
const heslo = prompt('Zadejte nové heslo:');

if (age >= 65) {
  document.body.innerHTML += '<p>Věk je v pořádku</p>.';
  if (heslo.length <= 8) {
    document.body.innerHTML += '<p>Slabé heslo</p>.';
  } else {
    document.body.innerHTML += '<p>Heslo je v pořádku</p>.';
  }
} else {
  document.body.innerHTML += '<p>Nízký věk</p>.';
}
```



</details>

## Cena vstupenky

Pokusme se o základ jednoduchého rezervačního sestému pro vstupenky do divadla.

1. Založte si webovou stránku s JavaScriptem.
1. Nechte uživatele zadat jeho věk.
1. Vytvořte si proměnnou `plnaCena`, udávající základní cenu vstupenky a uložte do ní hodnotu `12`.
1. Vytvořte podmínku, která do proměnné `cena` uloží cenu spočítanou podle věku uživatele dle následujících pravidel:

- **0 euro** pro návštěvníky mladší 6 let,
- **65 % ze základní ceny** pro návštěvníky 6 až 26 let (žák, student),
- **100 % ze základní ceny** pro návštěvníky 27 až 64 let (dospělý),
- **50 % ze základní ceny** pro ostatní (senior).

1. Nezapomeňte na zaokrouhlování, ať nám cena vyjde v celých eurech.
1. Nakonec spočtenou cenu vypište s nějakou hezkou zprávou na výstup.

<details>
<summary><b>Řešení</b></summary>


```js
const plnaCena = 12;
let cena;
const age = Number(prompt('Zadejte svůj věk:'));
if (age < 6) {
  cena = 0;
} else if (age >= 6 && age <= 26) {
  cena = plnaCena * 0.65;
} else if (age >= 27 && age <= 64) {
  cena = plnaCena;
} else {
  cena = plnaCena * 0.5;
}
cena = Math.ceil(cena);
document.body.innerHTML += `<p>Cena lístku je ${cena} €.`;
```

Druhá možnost, plnou cenu bereme jako základní a v `if` testujeme jenom výjimky:

```js
const plnaCena = 12;
let cena = plnaCena;
const age = Number(prompt('Zadejte svůj věk:'));
if (age < 6) {
  cena = 0;
} else if (age >= 6 && age <= 26) {
  cena = plnaCena * 0.65;
} else if (age > 64) {
  cena = plnaCena * 0.5;
}
cena = Math.ceil(cena);
document.body.innerHTML += `<p>Cena lístku je ${cena} €.`;
```

Pro fajnšmekry třetí možnost s operátorem `*=`, který funguje podobně jako `+=`, ale pro násobení. Tato možnost
neodpovídá přesně zadání, protože vůbec nepotřebujeme proměnnou `plnaCena`:

```js
let cena = 12;
const age = Number(prompt('Zadejte svůj věk:'));
if (age < 6) {
  cena = 0;
} else if (age >= 6 && age <= 26) {
  cena *= 0.65;
} else if (age > 64) {
  cena *= 0.5;
}
cena = Math.ceil(cena);
document.body.innerHTML += `<p>Cena lístku je ${cena} €.`;
```


</details>