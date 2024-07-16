# Формы
## Нативные формы
Формы, в которых используются нативные тэги `<button>`, `<input>`, `<textarea>`, в том числе и сам тэг `<form>`!
Списочек с тэгами:
- `<input>`
- `<label>`
- `<select>`
- `<textarea>`
- `<button>`
- `<fieldset>`
- `<legend>`
- `<datalist>`
- `<output>`
- `<option>`
- `<optgroup>`
## Типы полей ввода
Полный список из W3Schools
- `<input type="button">`
- `<input type="checkbox">`
- `<input type="color">`
- `<input type="date">`
- `<input type="datetime-local">` //доизучить разницу
- `<input type="email">`
- `<input type="file">`
- `<input type="hidden">` //Скрытое поле, не отображается на странице, но передает данные при отправке формы.
- `<input type="image">`
- `<input type="month">`
- `<input type="number">`
- `<input type="password">`
- `<input type="radio">`
- `<input type="range">`
- `<input type="reset">` //Кнопка для сброса формы до начальных значений.
- `<input type="search">`
- `<input type="submit">`
- `<input type="tel">`
- `<input type="text">`
- `<input type="time">`
- `<input type="url">`
- `<input type="week">`
## Валидация на стороне клиента
- Встроенная валидация форм
    - required — определяет обязательное поле в форме для заполнения
    - minlength и maxlength — задает минимальную и максимальную длину текстовых данных/строк
    - min и max — минимальное и максимальное значения для числового поля
    - type — определяет тип данных 
    - pattern — с помощью регулярного выражения определяет шаблон, которому должны соответствовать данные
    Если данные, введённые в поле формы, соответствуют правилам перечисленных выше атрибутов, они считаются валидными, если нет — не валидными
    
    Когда элемент валиден, справедливы следующие утверждения:
      - Элемент соответствует CSS-псевдоклассу `:valid`, позволяющему стилизовать только валидные элементы.
      - Если пользователь пытается отправить данные, браузер отправит форму при условии, что ничто другое (например, JavaScript) не помешает ему это сделать

    Когда элемент не валиден, справедливы следующие утверждения:
      - Элемент соответствует CSS-псевдоклассу :invalid или, в зависимости от ошибки, другим псевдоклассам (например, :out-of-range), которые позволяют применять определённые стили к элементам, не являющимся валидными.
      - Если пользователь пытается отправить данные, браузер заблокирует форму и выведет сообщение об ошибке.
        
- JavaScript-валидация
    Форма:
    ```
    <form>
      <label for="mail"
        >I would like you to provide me with an e-mail address:</label
      >
      <input type="email" id="mail" name="mail" />
      <button>Submit</button>
    </form>
    ```
    
    Обработчик события:
    ```
    const email = document.getElementById("mail");
    
    email.addEventListener("input", function (event) {
      if (email.validity.typeMismatch) {
        email.setCustomValidity("I am expecting an e-mail address!");
      } else {
        email.setCustomValidity("");
      }
    });
    ```

## Стилизация
  - Стилизация checkbox
  - Стилизация dropdown select
  - ...
