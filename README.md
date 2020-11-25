# Style guide по написанию кода на JavaScript

## 1. camelCase, имена перенных и функфий

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

## 2. Make const, not var

Область видимости let и const ограничивается блоком кода или телом функции, var же игнорирует блоки и превращает переменные в глобальные, а это может привести к неожиданным эфектам.

✔ Хорошо:
```
let editableValue;
const makeUser = () =>{
  // do logic
}
```

❌ Плохо:
```
var string = 'some text';
var number = 42;
```

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


## 7. Точка с запятой

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

## 8. Пробелы вокруг вложенного вызова

Отделить пробелами аргументы функции, если ими является результат выполнения другой функции.

✔ Хорошо:
```
const getFullName = (firstName, secondName) => `${firstName} ${secondName}`;

console.log(== ==getFullName('John', 'Doe')== ==);
```

❌ Плохо:
```
console.log(getFullName('John', 'Doe'));
```
