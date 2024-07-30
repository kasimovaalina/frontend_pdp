Переменные объявляются с помощью custom property нотации, например `--main-color: black;`, и используются (или становятся доступны) через функцию `var()`. (например `color: var(--main-color);`).

С помощью `var()` можно определить _множество_ возворащаемых значений, на случай, если переменная неопределена.
```
.two {
  color: var(--my-var, red); /* red если --my-var не определена */
}

.three {
  background-color: var(
    --my-var,
    var(--my-background, pink)
  ); /* pink если --my-var и --my-background не определены */
}

.three {
  background-color: var(
    --my-var,
    --my-background,
    pink
  ); /* "--my-background, pink" будет воспринят как значение в случае, если --my-var не определена */
}
```
