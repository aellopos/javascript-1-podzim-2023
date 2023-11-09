## Výplata

1. Založte si novou prázdnou stránku s JavaScriptovým programem.
1. V programu spočítejte svůj **měsíční** příjem, víte-li, že pracujete **7 hodin denně** se **mzdou 320 Kč na hodinu**. Řekněme, že měsíc má **21 pracovních dní**.
1. Měsíční příjem vypište do stránky.
1. Pokud pracujete na živnostenský list, můžete si odečíst **60 %** příjmů jako paušál a ze zbytku zaplatíte **15% daň**. Spočítejte, jak velkou daň zaplatíte ze své výplaty. Pomocí funkce `Math.floor` zaokrouhlete výsledek dolů na celé koruny.
1. Daň také vypište do stránky.

<details>
<summary><b>Řešení</b></summary>


#### Měsíční příjem

```js
document.body.innerHTML += 21 * 7 * 320;
```

#### Daň

```js
document.body.innerHTML += '<br>';
document.body.innerHTML += Math.floor(21 * 7 * 265 * (1 - 0.6) * 0.15);
```


</details>

## Délka filmu

V programu kin se často uvádí délka filmu v minutách. Například rozšířená verze filmu :i[Pán prstenů: Dvě věže] trvá **223 minut**. My bychom ovšem délku filmu raději věděli **v hodinách a minutách**.

1. Za použití funkcí a operátorů z této lekce spočítejte, kolik **hodin a minut trvá film** :i[Pán prstenů: Dvě věže].
1. Obě hodnoty vypište do stránky.


<details>
<summary><b>Řešení</b></summary>


#### Počet celých hodin

```js
document.body.innerHTML += Math.floor(223 / 60);
```

#### A počet zbývajících minut

```js
document.body.innerHTML += '<br>';
document.body.innerHTML += 223 % 60;
```


</details>

## E-mail

1. Sestavte e-mailovou adresu tak, že sečtete dohromady vaše křestní jméno, znak tečka, vaše příjmení a koncovku `@mujmail.com`.
1. Celou e-mailovou adresu vypište do stránky.



<details>
<summary><b>Řešení</b></summary>


```js
'Franta' + '.' + 'Dobrota' + '@mujmail.com';
```


</details>

## Ultramaraton

Představte si, že jste pořadatelé ultramaratonského závodu. Závod začíná ve **tři hodiny odpoledne**, což ve 24hodinovém formátu zapíšeme jako **15**. Nejlepší běžec zvládne vaši brutální trasu za **10 hodin**. Doběhne tedy **v jednu hodinu ráno**, v našem formátu zapsáno jako **1**.

1. Založte si JavaScriptový program a uložte čas startu závodu do proměnné `start`.
1. Do proměnné `delka` uložte délku závodu pro nějakého běžce. Klidně může být pomalejší než náš šampion.
1. Do proměnné `konec` spočítejte, v kolik hodin závod pro našeho běžce skončí a vypište její obsah do stránky.
1. Vyzkoušejte různé délky a ověřte, že váš postup funguje.




<details>
<summary><b>Řešení</b></summary>


```js
const start = 15;
const delka = 10;
const konec = (start + delka) % 24;
document.body.innerHTML = 'Čas konce v hodinách: ' + konec;
```


</details>

## Náhodná čísla

Založte si JavaScriptový program a pomocí `document.body.innerHTML` a funkce `Math.random` zobrazte na stránce náhodné číslo. Zkuste stránku několikrát po sobě obnovit a ověřte si, že pokaždé obdržíte jiné číslo.



<details>
<summary><b>Řešení</b></summary>


```js
document.body.innerHTML = Math.random();
```


</details>

## Převod měny

1. Založte si novou prázdnou stránku s JavaScriptovým programem.
1. Dejme tomu, že si jako programátoři vyděláváte **20 euro na hodinu**. Uložte tuto hodnotu do proměnné `wageInEur`.
1. Spočítejte, kolik je vaše **hodinová mzda v českých korunách**, jestliže kurz eura je `24.55` Kč. Výsledek zaokrouhlete na celé koruny a uložte do proměnné :var[wageInCzk].
1. Vypište obsah proměnné :var[wageInCzk] do webové stránky tak, aby na stránce byl nadpis `h1` s obsahem:

   > Mzda v korunách: 532 Kč



<details>
<summary><b>Řešení</b></summary>


```js
const wageInEur = 20;
const rate = 24.55;
const wageInCzk = Math.round(wageInEur * rate);
document.body.innerHTML = '<h1>Mzda v korunách: ' + wageInCzk + ' Kč</h1>';
```



</details>