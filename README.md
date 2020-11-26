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

## 9. Завершите переключатели (switch) по умолчанию

Всегда завершайте операторы switch значением default. Даже если вы думаете, что в этом нет необходимости.

✔ Хорошо:
```
switch (comand) {
  case '/start':
    start();
    break;

  case '/search':
    search();
    break;

  case '/stop':
    stop();
    break;

  default:
    throw new Error('Unknown comand');
}
```

❌ Плохо:
```
switch (comand) {
  case '/start':
    start();
    break;

  case '/stop':
    stop();
    break;
}
```

## 10.Объявляйте переменные для for вне циклов

При таком подходе уменьшается нагрузка на движек, а следовательно повышается производительность кода.

✔ Хорошо:
```
const demo = document.querySelector('.demo');
const list = document.createElement('ul');

const create = (el, value) => {
  const newEl = document.createElement(el);
  newEl.innerHTML = value;

  return newEl;
}

for (let i = 0; i < 10; i++) {
  list.append( create('li', i) );
}

demo.innerHTML = list.innerHTML;
```

❌ Плохо:
```
const list = document.createElement('ul');
const create = (el, value) => {
  const newEl = document.createElement(el);
  newEl.innerHTML = value;

  return newEl;
}

for (let i = 0; i < 10; i++) {
  const demo = document.querySelector('.demo');

  list.append( create('li', i) );
  demo.innerHTML = demo + list.innerHTML;
}

```

## 11. Подключение скриптов в конце body

Работая с DOM важно, что бы к моменту выполнения программы сам DOM был уже сформирован.

✔ Хорошо:
```
<!DOCTYPE html>
<html>
  <head>
    // ...
  </head>
  <body>
    // ...
    <script src='./path/to/script.js'></script>
  </body>
</html>
```

❌ Плохо:
```
<head>
  // ...
  <script src='./path/to/script.js'></script>
</head>
```

## 12. При использовании конструкции if .. else располагайте else на одной строке со скобкой закрывающей блок if.

Если от else можно отказаться, то лучше так и сделать.

✔ Хорошо:
```
// examp 1:
if (true) {
  // do something..
} else {
  // do another..
}

// examp 2:
if (true) {
  // do something..
} return result;
```

❌ Плохо:
```
if (true) {
  // do something..
} 
else {
  // do another..
}
```

## 13. Одна функция для одной задачи.

По возможности функция должна выполнять одну задачу, это облегчает дебаг и работу с вашим кодом другим разработчикам. Это также относится к вспомогательным функциям для общих задач. Если вы замечаете что делаете одно и тоже в нескольких функциях, лучше создать более универсальную вспомогательную функцию, и использовать ее где необходимо.

✔ Хорошо:
```
const searchElement = (search, into = document) => into.querySelector(search);

const searchLastElement = (search, into = document) => {
  const el = into.querySelectorAll(search);

  return el[el.length-1];
}

const searchElements = (search, into = document) => into.querySelectorAll(search);

// ищем первый div в документе
const div = searchElement('div');

// ищем последний элемент списка в первом на странице списке
const lastLi = searchLastElement('li', 'ul');

// ищем все параграфы на 
const paragraphs = searchElements('p');
```

## 14. Использовать значения параметров по умолчанию.

Упрощает написание кода, объем кода, а так же работает как дополнительная "Защита от дурака" :P 

Примеры смотри в предыдущем пункте.
