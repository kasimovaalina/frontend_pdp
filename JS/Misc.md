# Каррирование
> Каррирование – это трансформация, которая превращает вызов f(a, b, c) в f(a)(b)(c). В JavaScript реализация обычно позволяет вызывать функцию обоими вариантами: либо нормально, либо возвращает частично применённую функцию, если количество аргументов недостаточно.

Пример
 ```
function curry(f) { // curry(f) выполняет каррирование
  return function(a) {
    return function(b) {
      return f(a, b);
    };
  };
}

// использование
function sum(a, b) {
  return a + b;
}

let curriedSum = curry(sum);

alert( curriedSum(1)(2) ); // 3
```
_Продвинутая_ реализация каррирования
```
function curry(func) {

  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      }
    }
  };

}
```
# Ссылочный тип
Ссылочный тип – это внутренний тип языка.

Чтение свойства, например, с точкой . в obj.method() возвращает не точное значение свойства, а специальное значение «ссылочного типа», в котором хранится как значение свойства, так и объект, из которого оно было взято.

Это нужно для последующего вызова метода (), чтобы получить объект и установить для него this.

Для всех остальных операций ссылочный тип автоматически становится значением свойства (в нашем случае функцией).

Вся механика скрыта от наших глаз. Это имеет значение только в особых случаях, например, когда метод динамически извлекается из объекта с использованием выражения.