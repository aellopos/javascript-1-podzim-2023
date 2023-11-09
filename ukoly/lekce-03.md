## Očkování

Představte si, že vyrábíte registrační systém na očkování proti COVID-19. U každého registrovaného chceme evidovat jméno a věk.

1. Vytvořte webovou stránku, která se uživatele zeptá nejdříve na jméno a poté na věk. Tyto hodnoty si uložte do smysluplně pojmenovaných proměnných. Nezpomeňte věk převést na číslo.
1. Poté, co uživatel zadá všechny údaje, vypište do stránky odstavec s obsahem ve tvaru
   ```
   Květoslav Voňavý, věk: 67
   ```


<details>
<summary><b>Řešení</b></summary>


```js
const celeJmeno = prompt("Jake je vase jmeno a primeni?");
const vek = Number(prompt("Jaky je vas vek?"));
​
document.body.innerHTML += "<p>" + celeJmeno + ", vek: " + vek + "</p>";
```


</details>

## Výplata jako stránka

1. Vytvořte webovou stránku, která uživatele požádá o jeho hodinovou sazbu v korunách a spočítá jeho hrubou mzdu za předpokladu, že pracuje 8 hodin denně 21 dní v měsíci. Do stránky vypište výsledek zabalený do nějaké přívětivé formulace. Dbejte na to, abyste korektně převedli uživatelem zadanou hodnotu na číslo.
1. Nechte uživatele zadat nejen hodinovou sazbu, ale také počet hodin a dní v měsíci. Opět dejte pozor na správnou konverzi.

<details>
<summary><b>Řešení</b></summary>


```js
const hodinovaSazba = Number(prompt("Jaká je vaše hodinová sazba?"));
const pocetHodin = Number(prompt("Kolik hodin denně pracujete?"));
const pocetDni = Number(prompt("Kolik dní měsíčně pracujete?"));
​
document.body.innerHTML += "<p>Vaše vyplata činí " + (hodinovaSazba*pocetHodin*pocetDni) + " korun</p>";
```


</details>

## Realitka

Mějme následující objekt představující inzerát na stránkách nějaké realitní kanceláře.

```js
const apartment = {
  type: 'rent',
  disposition: '3+1',
  area: {
    floorage: 100,
    balcony: 2,
    units: 'sqm',
  },
  city: 'Prague',
  district: 'Old Town',
  price: {
    rent: 28000,
    fees: {
      water: 1000,
      energy: 2500,
      services: 560,
    },
    currency: 'czk',
  },
  ownership: 'personal',
  condition: 'renovated',
  status: 'free',
  floor: 3,
};
```

Vytvořte webovou stránku s JavaScriptem, zkopírujte si tento kód do vašeho programu a vyřešte následující úkoly.

1. Pomocí tečkové notace vypište do stránky dispozici bytu.
1. Vypište do stránky čistý nájem bez poplatků.
1. Vypište do stránky celý objekt představující výměru bytu.
1. Do separátních proměnných uložte město a městskou část. Vypište je do stránky.
1. Změnte stav inzerátu z `'free'` na `'taken'`.

<details>
<summary><b>Řešení</b></summary>


```js
const apartment = {
  type: 'rent',
  disposition: '3+1',
  area: {
    floorage: 100,
    balcony: 2,
    units: 'sqm',
  },
  city: 'Prague',
  district: 'Old Town',
  price: {
    rent: 28000,
    fees: {
      water: 1000,
      energy: 2500,
      services: 560,
    },
    currency: 'czk',
  },
  ownership: 'personal',
  condition: 'renovated',
  status: 'free',
  floor: 3,
};
​
document.body.innerHTML += "<p>Dispozice: "+ apartment.disposition +"</p>"
document.body.innerHTML += "<p>Najem bez poplatku: "+ apartment.price.rent +"</p>"
document.body.innerHTML += "<p>Vymera bytu: "+ apartment.area.floorage + apartment.area.units +"</p>"
​
const city = apartment.city;
const district = apartment.district;
​
document.body.innerHTML += "<p>Mesto: "+ city +"</p>"
document.body.innerHTML += "<p>Mestska cast: "+ district +"</p>"
​
apartment.status = "taken"
document.body.innerHTML += "<p>Stav inzeratu: "+ apartment.status +"</p>"
```


</details>

## Knihovna

1. V JavaScriptovém programu vytvořte objekt představující jednu knihu v knihovně. Uvažte, jaké vlastnosti může taková kniha mít. Rozhodně budeme chtít název, autora a počet stran. Přidejte do objektu alespoň tři další vlastnosti tak, aby obsahovaly čísla, řetězce i vnořený objekt.
1. Vytvořte alespoň jednu další knihu se stejnými vlastnostmi ale jinými hodnotami.`


<details>
<summary><b>Řešení</b></summary>


```js
const book = {
  title: 'Lord of the Rings',
  author: {
    name: 'John Ronald Reuel',
    surename: 'Tolkien',
    age: 81,
  },
  numberOfPages: 2057,
  movie: {
    year: 2000,
    director: {
      name: 'Peter',
      surname: 'Jackson',
    },
    actors: {
      actor1: {
        name: 'Orlando',
        surname: 'Bloom',
        characterName: 'Legolas',
      },
      actor2: {
        name: 'Elijah',
        surname: 'Wood',
        characterName: 'Frodo',
      },
      actor3: {
        name: 'Viggo',
        surname: 'Mortensen',
        characterName: 'Aragorn',
      },
    },
  },
};
```

</details>

## Očkování – objekty

Pokračujme v našem registračním systému na očkováni. Zatím se umíme uživatele zeptat na jméno a věk.

1. Vytvořte objekt `person`, do kterého vložte uživatelem zadané údaje. Objekt bude mít následující strukturu
   ```js
   {
     name: 'Květoslav Voňavý',
     age: 67,
   }
   ```
1. Přidejte do objektu `person` údaj o tom, v jakém jazyce si uživatel přeje komunikovat. Zjistěte jej z objektu `window`.
1. Poté, co uživatel zadá všechny údaje, vypište do stránky objekt `person` se všemi jeho vlastnostmi v nějakém hezkém formátu a zkontrolujte, že obsahuje správné informace.


<details>
<summary><b>Řešení</b></summary>


```js
const person = {
  name: prompt("Jaké je vaše jméno a příjmení?"),
  age: Number(prompt("Jaký je váš věk?")),
  language: window.navigator.language,
};
​
document.body.innerHTML += "<p>Zadané jméno: " + person.name + ", váš věk: " + person.age + "</p>";
document.body.innerHTML += "<p>Váš jazyk: " + person.language + "</p>";
document.body.innerHTML += "<p>Byli jste zaregistrováni na očkování.</p>";
```


</details>