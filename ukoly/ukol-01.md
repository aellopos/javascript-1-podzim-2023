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