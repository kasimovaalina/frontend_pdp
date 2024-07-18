# Способы вставки
1. Как `<img>`:

   ```
   <img src="Hello_SVG.svg" />
   ```
2. Задать в качестве фона:

   ```
   #box { background-image: url("Hello_again.svg"); }
   ```
3. Тэг `<object>`:

   ```
   <object data="My_SVG.svg" type="image/svg+xml"></object>
   ```
4. Тэг `<embed>`:

   ```
   <embed src="My_SVG.svg" type="image/svg+xml" />
   ```
5. Тэг `<iframe>`:

   ```
   <iframe src="My_SVG.svg"></iframe>
    ```
_При использовании первых двух спосбов не получится реализовать интерактивную анимацию_
# Команды пути
Как правило, команды пути хранятся в атрибуте _**d**_, представляет из себя определение пути для рисования. Три элемента используют этот атрибут: `<path>`, `<glyph>`, и `<missing-glyph>`.
Каждая команда состоит из буквы и некоторых чисел, представляющих параметр команды. 
### Список команд:
- MoveTo: M, m
- LineTo: L, l, H, h, V, v
- Cubic Bézier Curve: C, c, S, s
- Quadratic Bézier Curve: Q, q, T, t
- Elliptical Arc Curve: A, a
- ClosePath: Z, z
### Пример 
```
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <path
    fill="none"
    stroke="red"
    d="M 10,30
       A 20,20 0,0,1 50,30
       A 20,20 0,0,1 90,30
       Q 90,60 50,90
       Q 10,60 10,30 z" />
</svg>
```
<img>
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <path
    fill="none"
    stroke="red"
    d="M 10,30
       A 20,20 0,0,1 50,30
       A 20,20 0,0,1 90,30
       Q 90,60 50,90
       Q 10,60 10,30 z" />
</svg>
</img>
# Анимации
## Способы анимации
1. CSS
2. SMIL
