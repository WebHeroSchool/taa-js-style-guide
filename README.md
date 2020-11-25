*Черновик:*

# Style guide по написанию кода на JavaScript - Best practices

## 1. Строгое сравнение

Что бы избежать незапланированного изменения типа сравниваемых значений нужно использовать безопасное строгое сравнение.

✔ Хорошо:
```
const number = Infinity;
const string = 'Infinity';

if (number === sring) {
  // false
}
```

❌ Плохо:
```
if (number == sring) {
  // true
}
```


## 2. Make const, not var

Область видимости let и const ограничивается блоком кода или телом функции, var же игнорирует блоки и превращает переменные в глобальные, а это может привести к неожиданным эфектам связанными с переопределение значений переменных в глобальной области видимости.

✔ Хорошо:
```
let editableValue;
const makeUser = () => {
  // do logic
}
```

❌ Плохо:
```
var string = 'some text';
var number = 42;
```

## 3. КОНСТАНТЫ

Имена констант должны быть написаны ЗАГЛАВНЫМИ_БУКВАМИ, через нижнее подчеркивание

✔ Хорошо:
```
const PI = 3.14;
const MS_IN_YEAR = 6031536000000; 
```

❌ Плохо:
```
const pi = 3.14;
let PI = 3.14;
```

## 4. Eval()

Никогда не используй eval() - это ==не безопасно!==

Метод eval() выполняет JavaScript код, представленный строкой, а так как, передача строк в setInterval и setTimeout будет вести себя точно так же, то их можно использовать только с вложенной функцией.

✔ Хорошо:
```
const someFunction = () => {
  // some logic..
}

setTimeout(someFunction, 1500);
```

❌ Плохо:
```
setInterval("body.innerHTML += 'My new number: ' + i", 3000);
```

## 5. Точка с запятой

В конце строки должна стоять точка с запятой, это позволит избежать ошибок и повысит читаемость кода.

✔ Хорошо:
```
const number = 42;
console.log(number);
```

❌ Плохо:
```
const arr = [1, 2, 3, 4, 5]
console.log(arr)
```

## 6. Стрелочные функции

Используя стрелочную функцию, мы создаём функцию, которая выполняется в контексте this, а также это более короткий синтаксис.

✔ Хорошо:
```
[1, 2, 3].map(x => {
  const y = x + 1;
  return x * y;
});
```

❌ Плохо:
```
[1, 2, 3].map(function(x) {
  const y = x + 1;
  return x * y;
});
```

## 7. Свойства

Используйте точечную нотацию для доступа к свойствам.
Используйте скобочную нотацию [], когда название свойства хранится в переменной.

✔ Хорошо:
```
const person = {
  name: 'Anton',
  isAdmin: false,
}

const getProp = (obj, prop) => obj[prop];

const name = person.name; // Anton
const checkAdmin = getProp(person, 'isAdmin');  // false..
```

❌ Плохо:
```
console.log(person['name']);
```

## 8. Имена

Избегайте названий из одной буквы. Имя должно быть наглядным и отражать суть того, что происходит в коде.

### 8/1. camelCase, имена перенных и функфий

Имена функций и переменных должны начинаться с прописной буквы, если имя сотоит из 2х и более слов, то между ними убираются пробелы а каждое новое слово начинается с заглавной буквы.

Помимо правильного написания имен переменных и функций, нужно подбирать имена, что бы те максимально точно отражали их суть.

✔ Хорошо:
```
let myCart;
let formSendHandler;
let myName;
```

❌ Плохо:
```
let mycart;
let my-cart;
let moyaKorzina;
let vasya;
```

### 8/2. Именование классов в PascalCase нотации

Имя класса начинается с заглавной буквы, если имя состоит из несколькох слов, то каждое последующее слово начинается с заглавной буквы, а пробелы исключаются.

✔ Хорошо:
```
class User {
  constructor(name, isAdmin = false) {
    this.name = name;
    this.isAdmin = isAdmin;
  }
  
  displayInfo = () => {
    console.log(this.name, this.isAdmin);
  }
}

const user = new User('Anton');

user.displayInfo();
```

❌ Плохо:
```
class car {
  constructor(params) {
    // constructor..
  }
  
  method = () => {
    // logic..
  }
}

const car = new car(params);

car.method();
```















9. Завершите переключатели (switch) по умолчанию
Всегда завершайте операторы switch значением default. Даже если вы думаете, что в этом нет необходимости.
10.Объявляйте переменные для for вне циклов
11. Подключение скриптов в конце body
12. При использовании конструкции if .. else располагайте else на одной строке со скобкой закрывающей блок if.
13. Имена констант должны быть ЗАГЛАВНЫМИ_БУКВАМИ и через нижнее подчёркивание
14. Одна функция для одной задачи.
По возможности функция должна выполнять одну задачу, это облегчает дебаг и работу с вашим кодом другим разработчикам. Это также относится к вспомогательным функциям для общих задач. Если вы замечаете что делаете одно и тоже в нескольких функциях, лучше создать более универсальную вспомогательную функцию, и использовать ее где необходимо. Например, необходимо сделать вспомогательную функцию для создания ссылок:
15. Использовать значения параметров по умолчанию.




## 3. Условия, функции и кудрявые скобки

Тело функции записывается между кудрявых скобок, при этом открывающая скобка пишется на той же строке, что и имя функции или условие, а закрывающая на новой строке.

✔ Хорошо:
```
function funcName() {
  // body of function
}

if (true) {
  // do logic
}
```

❌ Плохо:
```
function funcName()
{
  // body of function
}

if (true) { // do logic }
```

## 4. Шаблонные строки

При необходимости использования переноса строки или логического выражения внутри строки нужно использовать шаблонные строки.

✔ Хорошо:
```
const html = `
  <h1>Header</h1>
  <p>Subtitle</p>
`;

const welcome = `Welcome to ${window.location.href}!`;
```

❌ Плохо:
```
const welcome = 'Welcome to ' + window.location.href + '!';
```

## 5. Горизонтальные отступы

2 пробела или табуляция настроенная на 2 пробела.

✔ Хорошо:
```
function makeCycle() {
  let value = 0;

  for (let i; i <= 10; i++) {
    // operations on value...
  }

  return value;
}
```

❌ Плохо:
```
function makeCycle() {
let value = 0;

for (let i; i <= 10; i++) {
// operations on value...
}

return value;
}
```

> Вопрос о табах и пробелах на мой взгляд спорный, так что это просто дань моде.

## 6. Вертикальные отступы

Логические блоки в функциях длжны быть отделены пустой строкой.

✔ Хорошо:
```
function makeCycle() {
  let value = 0;

  for (let i; i <= 10; i++) {
    // operations on value...
  }

  return value;
}
```

❌ Плохо:
```
function makeCycle() {
  let value = 0;
  for (let i; i <= 10; i++) {
    // operations on value...
  }
  return value;
}
```



## 8. Пробелы вокруг вложенного вызова

Отделить пробелами аргументы функции, если ими является результат выполнения другой функции.

✔ Хорошо:
```
const getFullName = (firstName, secondName) => `${firstName} ${secondName}`;

console.log( getFullName('John', 'Doe') );
```

❌ Плохо:
```
console.log(getFullName('John', 'Doe'));
```

## 9. Создание объекта через литерал, а не через конструктор

✔ Хорошо:
```
const user = {
  name: 'Anton',
  isAdmin: false,
}
```

❌ Плохо:
```
function User(name, isAdmin) {
  this.name = name;
  this.isAdmin = isAdmin;
};

const user = new User('Anton', false);
```


