# Блочная модель
Если элемент определён как блочный, то он будет вести себя следующим образом:

- Начнётся с новой строки.
- Будет расширяться вдоль строки таким образом, чтобы заполнить всё пространство, доступное в её контейнере. В большинстве случаев это означает, что блок станет такой же ширины, как и его контейнер, заполняя 100% доступного пространства.
- Будут применяться свойства `width` и `height`.
- Внешние и внутренние отступы, рамка будут отодвигать от него другие элементы.

Если элемент имеет тип отображения `inline` (строчный), то:

- Он не будет начинаться с новой строки.
- Свойства `width` и `height` не будут применяться.
- Вертикальные внешние и внутренние отступы, рамки будут применяться, но не будут отодвигать другие строчные элементы.
- Горизонтальные внешние и внутренние отступы, рамки будут применяться и будут отодвигать другие строчные элементы.

## Внутреннее и внешнее отображение
Каждый блок в CSS имеет _внешний_ тип отображения, который определяет, блочный он или строчный.
_Внутренний_ тип отображения, который определяет расположение элементов внутри них. По умолчанию элементы внутри блока располагаются в нормальном потоке: они ведут себя так же, как и любые другие блочные или строчные элементы.
Внутреннее отображение можно изменить с помощью значения свойства `display` `flex` или `grid`.

//дописать про отступы и рамку и прочее

