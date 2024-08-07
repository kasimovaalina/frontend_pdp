# Продвинутая работа с функциями
## Глобальный объект
Глобальный объект предоставляет переменные и функции, доступные в любом месте программы. По умолчанию это те, что встроены в язык или среду исполнения.
В браузере он называется window, в Node.js — global, в другой среде исполнения может называться иначе.
В браузере глобальные функции и переменные, объявленные с помощью `var` (не `let`/`const`!), становятся свойствами глобального объекта:
```
var gVar = 5;

alert(window.gVar); // 5 (становится свойством глобального объекта)
```
То же самое касается функций, объявленных с помощью синтаксиса Function Declaration (выражения с ключевым словом function в основном потоке кода, не Function Expression)
## Объекты функции, NFE
### Свойство `name`
Возвращает название функции 🤷‍♀️
### Свойство `length`
Содержит количество параметров функции в её объявлении.
### Собственные свойства
Можно добавить😋

## Named Function Expression (NFE)
Термин для Function Expression, у которого есть имя.
```
let sayHi = function func(who) { // <-- имя func
  alert(`Hello, ${who}`);
};
```
Есть две важные особенности имени func, ради которого оно даётся:
1. Оно позволяет функции ссылаться на себя же.
2. Оно не доступно за пределами функции.
Пример:
```
let sayHi = function func(who) {
  if (who) {
    alert(`Hello, ${who}`);
  } else {
    func("Guest"); // использует func, чтобы снова вызвать себя же
  }
};

sayHi(); // Hello, Guest

// А вот так - не cработает:
func(); // Ошибка, func не определена (недоступна вне функции)
```
## Синтаксис "new Function"
бэйсикалли создание функции передавая строчные аргументы, в том числе тело функции.
```
let sum = new Function('a', 'b', 'return a + b');

alert( sum(1, 2) ); // 3
```
не работает в замыкании! поскольку названия код сжимается минификатором и переменные, к которым обращается функция, больше так не называются.
## `setTimeout` и `setInterval`
- `setTimeout` — вызвать функцию единожды через какой-то интервал времени, по умолчанию 0
- `setInterval` — вызывать функцию периодически через какой-то интервал
## Декораторы и переадресация вызова, `call`/`apply`
### Пример декоратора
```
function slow(x) {
  // здесь могут быть ресурсоёмкие вычисления
  alert(`Called with ${x}`);
  return x;
}

function cachingDecorator(func) {
  let cache = new Map();

  return function(x) {
    if (cache.has(x)) {    // если кеш содержит такой x,
      return cache.get(x); // читаем из него результат
    }

    let result = func(x); // иначе, вызываем функцию

    cache.set(x, result); // и кешируем (запоминаем) результат
    return result;
  };
}

slow = cachingDecorator(slow); // переопределяем поведение функции с декоратором

alert( slow(1) ); // slow(1) кешируем
alert( "Again: " + slow(1) ); // возвращаем из кеша

alert( slow(2) ); // slow(2) кешируем
alert( "Again: " + slow(2) ); // возвращаем из кеша
```
### Пример с `func.call` для передачи контекста
```
let worker = { //какой-то объект
  someMethod() {
    return 1;
  },

  slow(x) {
    alert("Called with " + x);
    return x * this.someMethod(); // (*)
  }
};

function cachingDecorator(func) {
  let cache = new Map();
  return function(x) {
    if (cache.has(x)) {
      return cache.get(x);
    }
    let result = func.call(this, x); //'this' передаётся через call правильно
    cache.set(x, result);
    return result;
  };
}

worker.slow = cachingDecorator(worker.slow); // теперь сделаем её кеширующей

alert( worker.slow(2) ); // работает
alert( worker.slow(2) ); // работает, не вызывая первоначальную функцию (кешируется)
```
### `func.apply`
//TODO: дописать
