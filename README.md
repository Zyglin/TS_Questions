### Содержание

| № | Вопрос |
|---|---|
| 1 | [Что такое TypeScript и чем он отличается от JavaScript?](#что-такое-typescript-и-чем-он-отличается-от-javascript) |
| 2 | [Каковы преимущества использования TypeScript?](#каковы-преимущества-использования-typescript) |
| 3 | [Явная типизация и выведение типов](#явная-типизация-и-выведение-типов) |
| 4 | [Примитивные типы TypeScript](#примитивные-типы-typescript) |
| 5 | [Специальные типы any и unknown](#специальные-типы-any-и-unknown) |
| 6 | [Аннотация @ts-ignore](#аннотация-ts-ignore) |
| 7 | [Размеченное объединение (Discriminated Union)](#размеченное-объединение-discriminated-union) |
| 8 | [Массивы в TypeScript](#массивы-в-typescript) |
| 9 | [Псевдонимы типов (Type Aliases)](#псевдонимы-типов-type-aliases) |
| 10 | [Типизация функций](#типизация-функций) |
| 11 | [Специальный тип void](#специальный-тип-void) |
| 12 | [Интерфейс объекта (Object Interface)](#интерфейс-объекта-interface) |
| 13 | [Модификаторы частей объекта ? и readonly](#модификаторы-частей-объекта--и-readonly) |
| 14 | [Доступ к частям объектного типа](#доступ-к-частям-объектного-типа) |
| 15 | [Интерфейс функционального объекта](#интерфейс-словаря-dictionary-interface) |
| 16 | [Интерфейс словаря и Array-Like объекта](#array-like-объект) |
| 17 | [Тип-перечисление enum и const enum](#тип-перечисление-enum) |
| 18 | [Объединение нескольких enum](#объединение-нескольких-enum) |
| 19 | [Кортежи (Tuples)](#кортежи-tuples) |
| 20 | [Модификатор readonly](#модификатор-readonly) |
| 21 | [Наследование и объединение интерфейсов](#наследование-и-объединение-интерфейсов) |
| 22 | [Полиморфизм подтипов](#полиморфизм-подтипов-subtype-polymorphism) |
| 23 | [Класс объекта в TypeScript](#класс-объекта-object-class) |
| 24 | [Объединение типов (Union Types)](#объединение-типов-union-types) |
| 25 | [Специальный тип never](#специальный-тип-never) |
| 26 | [Разница между interface и type](#разница-между-interface-и-type) |
| 27 | [Модификатор override](#модификатор-override) |
| 28 | [Модификатор accessor](#модификатор-accessor) |
| 29 | [Оператор satisfies](#оператор-satisfies) |
| 30 | [Небезопасные приведения типов](#небезопасные-приведения-типов-unsafe-type-assertions) |
| 31 | [Проблемные приведения типов](#проблемные-приведения-типов-problematic-type-assertions) |
| 32 | [Декораторы классов](#декораторы-классов-class-decorators) |
| 33 | [Декораторы методов класса](#декораторы-методов-класса-method-decorators) |
| 34 | [Декораторы свойств класса](#декораторы-свойств-класса-property-decorators) |
| 35 | [Агрегация метаинформации](#агрегация-метаинформации-metadata-aggregation) |
| 36 | [Декораторы статических частей класса](#декораторы-статических-частей-класса) |
| 37 | [Глобальные типы и формат .d.ts](#глобальные-типы-и-формат-dts) |
| 38 | [Оператор declare](#оператор-declare) |
| 39 | [Расширение globalThis](#расширение-globalthis) |
| 40 | [Типизация JavaScript-модуля на TypeScript](#типизация-модуля-на-javascript) |
| 41 | [Разбиение одного .d.ts на множество файлов](#разбиение-одного-dts-на-множество-файлов) |
| 42 | [Сборка TypeScript с генерацией .d.ts типов](#сборка-typescript-с-генерацией-dts-типов) |
| 43 | [tsc и tsc-cli](#tsc) |

# Что такое TypeScript и чем он отличается от JavaScript?

TypeScript — это строго типизированный язык программирования, разработанный компанией Microsoft. TypeScript является надстройкой над JavaScript, то есть любой корректный JavaScript-код является также корректным TypeScript-кодом.

Главное отличие TypeScript от JavaScript — наличие **статической типизации**.

JavaScript является динамически типизированным языком:

```javascript
let value = 10;

value = "Hello";
```

В JavaScript такая операция допустима, так как тип переменной определяется во время выполнения программы.

---

В TypeScript типы проверяются во время компиляции:

```typescript
let value: number = 10;

value = "Hello";
```

Компилятор выдаст ошибку:

```text
Type 'string' is not assignable to type 'number'
```

---

## Как работает TypeScript?

TypeScript не выполняется напрямую в браузере или Node.js.

Сначала код компилируется в JavaScript:

```
TypeScript (.ts)
        |
        v
TypeScript Compiler (tsc)
        |
        v
JavaScript (.js)
        |
        v
Browser / Node.js
```

Пример:

TypeScript:

```typescript
function add(
    a: number,
    b: number
): number {

    return a + b;
}
```

После компиляции:

```javascript
function add(a, b) {
    return a + b;
}
```

Типы удаляются, так как JavaScript их не поддерживает.

---

## Основные отличия TypeScript и JavaScript

| JavaScript                                | TypeScript                           |
| ----------------------------------------- | ------------------------------------ |
| Динамическая типизация                    | Статическая типизация                |
| Ошибки обнаруживаются во время выполнения | Ошибки обнаруживаются при компиляции |
| Нет интерфейсов                           | Есть интерфейсы и типы               |
| Нет строгого контроля данных              | Есть проверка типов                  |
| Подходит для небольших скриптов           | Подходит для больших приложений      |
| Файлы `.js`                               | Файлы `.ts`                          |

---

# Каковы преимущества использования TypeScript?

## 1. Раннее обнаружение ошибок

TypeScript позволяет найти ошибки до запуска приложения.

JavaScript:

```javascript
function getUser(id) {

    return id.name;

}

getUser(10);
```

Ошибка появится только во время выполнения.

---

TypeScript:

```typescript
function getUser(
    id: number
) {

    return id.name;

}
```

Компилятор сразу сообщит об ошибке.

---

## 2. Улучшенный автокомплит

Редакторы кода лучше понимают структуру программы.

Например:

```typescript
interface User {

    name: string;

    age: number;

}


const user: User = {
    name: "John",
    age: 25
};


user.
```

Редактор предложит:

```
user.name
user.age
```

---

## 3. Безопасный рефакторинг

При изменении структуры данных TypeScript показывает все места, которые нужно исправить.

Например:

Было:

```typescript
interface User {
    name:string;
}
```

Стало:

```typescript
interface User {
    name:string;
    age:number;
}
```

TypeScript найдет объекты, где отсутствует `age`.

---

## 4. Улучшенная читаемость кода

Типы являются документацией.

Без TypeScript:

```javascript
function createUser(data) {

}
```

Непонятно, какой объект ожидается.

---

С TypeScript:

```typescript
function createUser(
    data: User
): User {

}
```

Сразу понятно, какие данные используются.

---

## 5. Удобство работы в больших проектах

TypeScript особенно полезен в:

* Больших frontend-приложениях.
* Backend на Node.js.
* Командной разработке.
* Проектах с длительной поддержкой.

---

# Явная типизация и выведение типов

В TypeScript существует два способа определения типа:

1. Явное указание типа.
2. Автоматическое выведение типа.

---

# Явная типизация (Explicit Typing)

Разработчик самостоятельно указывает тип.

Синтаксис:

```typescript
let variable: type;
```

Пример:

```typescript
let age: number = 25;

let name: string = "John";

let active: boolean = true;
```

---

Для функций:

```typescript
function sum(
    a: number,
    b: number
): number {

    return a + b;

}
```

Здесь:

* `a` — число.
* `b` — число.
* результат функции — число.

---

Для объектов:

```typescript
const user: {
    name: string;
    age: number;
} = {

    name: "John",

    age: 25
};
```

---

# Выведение типов (Type Inference)

TypeScript самостоятельно определяет тип на основе значения.

Пример:

```typescript
let age = 25;
```

TypeScript автоматически определяет:

```typescript
let age: number;
```

---

Еще пример:

```typescript
const name = "John";
```

TypeScript понимает:

```typescript
const name: string;
```

---

Функции:

```typescript
function multiply(
    a: number,
    b: number
) {

    return a * b;

}
```

TypeScript автоматически определит:

```typescript
(): number
```

---

## Когда использовать явную типизацию?

Обычно рекомендуется указывать типы:

* Для публичных функций.
* Для параметров функций.
* Для сложных объектов.
* Для API моделей.

---

Пример:

```typescript
function getUser(
    id: number
): User {

}
```

---

А для простых переменных можно использовать inference:

```typescript
const count = 0;
```

---

# Примитивные типы TypeScript

TypeScript поддерживает основные примитивные типы JavaScript.

---

# number

Используется для всех чисел.

```typescript
let age: number = 25;

let price: number = 99.99;
```

Включает:

* Целые числа.
* Дробные числа.
* `Infinity`.
* `NaN`.

---

# string

Строковые значения.

```typescript
let name: string = "John";
```

Также:

```typescript
let message: string = `
Hello ${name}
`;
```

---

# boolean

Логический тип.

```typescript
let isActive: boolean = true;
```

---

# null

Отсутствие значения.

```typescript
let value: null = null;
```

---

# undefined

Значение не определено.

```typescript
let value: undefined = undefined;
```

---

# bigint

Для больших чисел.

```typescript
let big: bigint = 100n;
```

---

# symbol

Уникальные идентификаторы.

```typescript
const id: symbol = Symbol();
```

---

# object

Любой объект.

```typescript
let user: object = {
    name:"John"
};
```

Но чаще используют интерфейсы:

```typescript
interface User {

    name:string;

}
```

---

# Специальные типы any и unknown

TypeScript имеет специальные типы для случаев, когда тип неизвестен.

Основные:

* `any`
* `unknown`

---

# any

`any` отключает проверку типов.

Переменная может содержать любое значение.

Пример:

```typescript
let value: any;

value = 10;

value = "Hello";

value = true;
```

---

Можно выполнять любые операции:

```typescript
let data: any = "hello";

data.toFixed();
```

TypeScript не выдаст ошибку.

---

## Недостатки any

`any` убирает преимущества TypeScript.

Пример:

```typescript
let user: any = {};

console.log(user.name.test());
```

Ошибка появится только во время выполнения.

---

Использовать `any` рекомендуется только:

* При работе со старым JavaScript-кодом.
* Когда тип действительно неизвестен.
* При временной миграции проекта.

---

# unknown

`unknown` также позволяет хранить любое значение, но требует проверки типа перед использованием.

Пример:

```typescript
let value: unknown;

value = "Hello";

value = 10;
```

---

Но нельзя:

```typescript
value.toUpperCase();
```

Ошибка:

```
Object is of type 'unknown'
```

---

Нужно сначала проверить тип:

```typescript
if (typeof value === "string") {

    console.log(
        value.toUpperCase()
    );

}
```

---

# any vs unknown

| any                         | unknown                 |
| --------------------------- | ----------------------- |
| Отключает проверку типов    | Сохраняет безопасность  |
| Можно делать любые операции | Нужна проверка типа     |
| Опасный тип                 | Безопасная альтернатива |
| Используется редко          | Рекомендуется           |

---

# Пример использования unknown

Обработка данных из API:

```typescript
function processData(
    data: unknown
) {

    if (
        typeof data === "string"
    ) {

        console.log(
            data.length
        );

    }

}
```

---

# Аннотация `@ts-ignore`

`@ts-ignore` — это специальная директива TypeScript, которая отключает проверку типов для следующей строки кода.

Используется, когда разработчик сознательно хочет проигнорировать ошибку TypeScript.

---

## Синтаксис

```typescript
// @ts-ignore
const value: number = "hello";
```

TypeScript не покажет ошибку, несмотря на то что строка присваивается переменной типа `number`.

---

## Пример

Без `@ts-ignore`:

```typescript
const age: number = "25";
```

Ошибка:

```text
Type 'string' is not assignable to type 'number'
```

С `@ts-ignore`:

```typescript
// @ts-ignore
const age: number = "25";
```

Ошибка будет проигнорирована.

---

## Когда используется `@ts-ignore`?

Основные случаи:

### 1. Работа со сторонними библиотеками без типов

Например:

```typescript
// @ts-ignore
import oldLibrary from "old-library";
```

---

### 2. Временное отключение проверки при миграции JavaScript → TypeScript

Например, большой проект постепенно переводится на TypeScript.

---

### 3. Работа с ошибочным или нестандартным API

---

## Почему не рекомендуется часто использовать?

`@ts-ignore` скрывает реальные ошибки.

Например:

```typescript
// @ts-ignore
user.name.toUpperCase();
```

Если `user.name` равен `undefined`, ошибка появится только во время выполнения.

---

## Альтернатива — `@ts-expect-error`

Более безопасный вариант:

```typescript
// @ts-expect-error
const age: number = "hello";
```

Отличие:

* `@ts-ignore` просто игнорирует ошибку.
* `@ts-expect-error` ожидает ошибку и сообщит, если ошибки больше нет.

Пример:

```typescript
// @ts-expect-error
const value: number = 10;
```

TypeScript выдаст ошибку:

```text
Unused '@ts-expect-error' directive
```

---

# Размеченное объединение (Discriminated Union)

Discriminated Union — это объединение нескольких типов (`union`), где каждый тип имеет общее поле-идентификатор (discriminator), позволяющий TypeScript определить конкретный вариант.

Чаще всего используется с полем:

```typescript
type
```

или

```typescript
kind
```

---

## Пример без Discriminated Union

```typescript
interface Circle {
    radius: number;
}


interface Square {
    side: number;
}


type Shape = Circle | Square;
```

Проблема:

```typescript
function area(shape: Shape) {

}
```

TypeScript не знает, какой объект пришел.

---

## Использование discriminator

Добавляем общее поле:

```typescript
interface Circle {

    kind: "circle";

    radius: number;

}


interface Square {

    kind: "square";

    side: number;

}


type Shape = Circle | Square;
```

Теперь TypeScript может определить тип.

---

## Использование

```typescript
function getArea(shape: Shape): number {

    switch(shape.kind) {

        case "circle":

            return Math.PI *
                shape.radius *
                shape.radius;


        case "square":

            return shape.side *
                shape.side;

    }

}
```

TypeScript понимает:

```typescript
shape.radius
```

доступен только для `Circle`.

---

## Пример с состояниями API

Очень распространенный случай:

```typescript
type LoadingState = {

    status: "loading";

};


type SuccessState = {

    status: "success";

    data: User[];

};


type ErrorState = {

    status: "error";

    message: string;

};


type State =
    | LoadingState
    | SuccessState
    | ErrorState;
```

Использование:

```typescript
function render(state: State) {

    if(state.status === "success") {

        console.log(state.data);

    }


    if(state.status === "error") {

        console.log(state.message);

    }

}
```

---

## Преимущества Discriminated Union

* Безопасная работа с несколькими вариантами данных.
* Автоматический narrowing типов.
* Удобная обработка состояний.
* Меньше ошибок во время выполнения.

Используется часто в:

* Redux actions.
* API состояниях.
* UI состояниях.
* State machines.

---

# Массивы в TypeScript

TypeScript позволяет создавать типизированные массивы.

---

## Массив одного типа

### Синтаксис через `[]`

```typescript
const numbers: number[] = [
    1,
    2,
    3
];
```

---

```typescript
const names: string[] = [
    "John",
    "Mike"
];
```

---

Попытка добавить другой тип:

```typescript
numbers.push("hello");
```

Ошибка:

```text
Argument of type 'string' is not assignable to parameter of type 'number'
```

---

## Синтаксис через Array<T>

Аналогичный вариант:

```typescript
const numbers: Array<number> = [
    1,
    2,
    3
];
```

---

Для сложных типов:

```typescript
interface User {

    id:number;

    name:string;

}


const users: Array<User> = [];
```

---

## Массив объектов

```typescript
const users: User[] = [

    {
        id:1,
        name:"John"
    },

    {
        id:2,
        name:"Alex"
    }

];
```

---

## Массив нескольких типов (Union)

```typescript
const values: (string | number)[] = [

    "Hello",

    10,

    "World"

];
```

---

## Readonly массивы

Массив нельзя изменить:

```typescript
const numbers: readonly number[] = [
    1,
    2,
    3
];
```

Нельзя:

```typescript
numbers.push(4);
```

---

## Tuple (кортеж)

Массив фиксированной структуры:

```typescript
const user: [
    string,
    number
] = [
    "John",
    25
];
```

---

# Псевдонимы типов (Type Aliases)

Type Alias — это создание собственного имени для существующего типа.

Создается с помощью ключевого слова:

```typescript
type
```

---

## Простой пример

```typescript
type UserId = number;


const id: UserId = 10;
```

---

## Псевдоним объекта

```typescript
type User = {

    name:string;

    age:number;

};
```

Использование:

```typescript
const user: User = {

    name:"John",

    age:25

};
```

---

## Псевдоним Union типов

```typescript
type Status =
    "loading"
    | "success"
    | "error";
```

Использование:

```typescript
let status: Status;

status = "loading";
```

---

## Псевдонимы функций

```typescript
type Calculate = (
    a:number,
    b:number
) => number;
```

Использование:

```typescript
const sum: Calculate =
(
    a,
    b
) => {

    return a + b;

};
```

---

## Type Alias vs Interface

| Type Alias                                 | Interface                      |
| ------------------------------------------ | ------------------------------ |
| Может описывать любые типы                 | В основном объекты             |
| Поддерживает union                         | Не поддерживает union напрямую |
| Поддерживает примитивы                     | Только структуры               |
| Нельзя расширить через declaration merging | Можно расширять                |

---

Пример:

```typescript
type ID = string | number;
```

Через interface такое сделать нельзя.

---

# Типизация функций

TypeScript позволяет типизировать:

* параметры;
* возвращаемое значение;
* функции как переменные;
* callback-функции.

---

# Типизация параметров

JavaScript:

```javascript
function sum(a,b){

}
```

TypeScript:

```typescript
function sum(
    a:number,
    b:number
){

}
```

---

# Типизация возвращаемого значения

```typescript
function sum(
    a:number,
    b:number
): number {

    return a + b;

}
```

---

Если функция ничего не возвращает:

```typescript
function log(
    message:string
): void {

    console.log(message);

}
```

---

# Необязательные параметры

Используется `?`.

```typescript
function greet(
    name?: string
){

}
```

Теперь параметр может отсутствовать.

---

Использование:

```typescript
greet();

greet("John");
```

---

# Параметры по умолчанию

```typescript
function greet(
    name:string = "Guest"
){

}
```

---

# Rest параметры

```typescript
function sum(
    ...numbers:number[]
): number {

    return numbers.reduce(
        (a,b)=>a+b,
        0
    );

}
```

---

# Типизация функции через Type Alias

```typescript
type Operation = (
    a:number,
    b:number
) => number;
```

---

Использование:

```typescript
const multiply: Operation =
(
    a,
    b
) => {

    return a * b;

};
```

---

# Callback функции

```typescript
function process(
    value:number,
    callback:(x:number)=>void
){

    callback(value);

}
```

Использование:

```typescript
process(
    10,
    value => console.log(value)
);
```

---

# Перегрузка функций (Function Overload)

Позволяет описать несколько вариантов вызова функции.

Пример:

```typescript
function getValue(
    value:string
):string;


function getValue(
    value:number
):number;


function getValue(value:any){

    return value;

}
```

Теперь:

```typescript
const a = getValue("hello");

const b = getValue(10);
```

имеют разные типы.

---

# Специальный тип `void`

`void` — это специальный тип TypeScript, который используется для обозначения отсутствия возвращаемого значения у функции.

Обычно применяется для функций, которые выполняют действие, но ничего не возвращают.

---

## Пример

```typescript
function logMessage(
    message: string
): void {

    console.log(message);

}
```

Функция выполняет вывод в консоль, но не возвращает значение.

---

Если попытаться вернуть значение:

```typescript
function logMessage(): void {

    return "Hello";

}
```

TypeScript выдаст ошибку:

```text
Type 'string' is not assignable to type 'void'
```

---

## Отличие `void` от `undefined`

Хотя `void` связан с `undefined`, это разные понятия.

`undefined` — это конкретное значение:

```typescript
let value: undefined = undefined;
```

`void` — это указание, что функция ничего не возвращает:

```typescript
function test(): void {

}
```

---

## Функции обратного вызова

Часто `void` используется в callback-функциях:

```typescript
const buttonClick = (
    callback: () => void
) => {

    callback();

};
```

Callback может выполнять любые действия, но его результат игнорируется.

---

## `void` в стрелочных функциях

```typescript
const print = (
    text: string
): void => {

    console.log(text);

};
```
# Интерфейс объекта (Interface)

`interface` — это конструкция TypeScript для описания структуры объекта.

Интерфейс определяет:

* какие свойства должны быть;
* их типы;
* какие методы доступны.

---

## Создание интерфейса

```typescript
interface User {

    id: number;

    name: string;

    email: string;

}
```

---

Использование:

```typescript
const user: User = {

    id: 1,

    name: "John",

    email: "john@test.com"

};
```

---

Если отсутствует обязательное свойство:

```typescript
const user: User = {

    id: 1,

    name: "John"

};
```

Ошибка:

```text
Property 'email' is missing
```

---

# Интерфейс методов

Интерфейс может описывать функции:

```typescript
interface User {

    name: string;


    sayHello(): string;

}
```

Реализация:

```typescript
const user: User = {

    name: "John",

    sayHello() {

        return "Hello";

    }

};
```

---

# Расширение интерфейсов

Интерфейсы могут наследоваться.

Используется `extends`.

```typescript
interface Person {

    name: string;

}


interface Employee extends Person {

    salary: number;

}
```

Теперь:

```typescript
const employee: Employee = {

    name: "John",

    salary: 5000

};
```

---

# Интерфейсы классов

Класс может реализовывать интерфейс через `implements`.

```typescript
interface Animal {

    name: string;

    move(): void;

}


class Dog implements Animal {

    name = "Bob";


    move() {

        console.log("Run");

    }

}
```

---

# Модификаторы частей объекта `?` и `readonly`

TypeScript позволяет изменять свойства объектов с помощью специальных модификаторов.

Основные:

* `?` — необязательное свойство.
* `readonly` — свойство только для чтения.

---

# Необязательные свойства `?`

По умолчанию все свойства интерфейса обязательны.

```typescript
interface User {

    id: number;

    name: string;

    age: number;

}
```

Объект обязан содержать все поля.

---

Чтобы сделать свойство необязательным:

```typescript
interface User {

    id: number;

    name: string;

    age?: number;

}
```

Теперь допустимо:

```typescript
const user: User = {

    id: 1,

    name: "John"

};
```

---

Необязательное свойство имеет тип:

```typescript
number | undefined
```

---

Пример проверки:

```typescript
if(user.age) {

    console.log(user.age);

}
```

---

# readonly свойства

`readonly` делает свойство доступным только для чтения после создания объекта.

Пример:

```typescript
interface User {

    readonly id: number;

    name: string;

}
```

---

Создание:

```typescript
const user: User = {

    id: 1,

    name: "John"

};
```

---

Изменение:

```typescript
user.id = 2;
```

Ошибка:

```text
Cannot assign to 'id' because it is a read-only property
```

---

Но обычные свойства можно менять:

```typescript
user.name = "Alex";
```

---

# readonly массивы

Обычный массив:

```typescript
const numbers: number[] = [
    1,
    2,
    3
];
```

Можно:

```typescript
numbers.push(4);
```

---

Readonly массив:

```typescript
const numbers: readonly number[] = [
    1,
    2,
    3
];
```

Нельзя:

```typescript
numbers.push(4);
```

---

# Доступ к частям объектного типа

TypeScript позволяет получать типы отдельных частей объекта.

Для этого используются:

* `keyof`
* индексированный доступ (`T[K]`)
* `typeof`

---

# Оператор `keyof`

`keyof` получает список ключей объекта в виде union-типа.

Пример:

```typescript
interface User {

    id: number;

    name: string;

    age: number;

}
```

Использование:

```typescript
type UserKeys = keyof User;
```

Результат:

```typescript
"id" | "name" | "age"
```

---

Пример:

```typescript
let key: keyof User;

key = "name";

key = "id";
```

Недопустимо:

```typescript
key = "email";
```

---

# Индексированный доступ к типам

Можно получить тип конкретного свойства.

Пример:

```typescript
interface User {

    id: number;

    name: string;

}
```

Получение типа:

```typescript
type UserName =
    User["name"];
```

Результат:

```typescript
string
```

---

Получение нескольких свойств:

```typescript
type UserData =
    User["id" | "name"];
```

Результат:

```typescript
number | string
```

---

# Использование с `keyof`

Часто используется для безопасного доступа к объектам:

```typescript
function getValue<T, K extends keyof T>(
    obj: T,
    key: K
) {

    return obj[key];

}
```

---

Использование:

```typescript
const user = {

    id: 1,

    name: "John"

};


getValue(
    user,
    "name"
);
```

Тип результата:

```typescript
string
```

---

# Оператор `typeof`

`typeof` позволяет получить тип существующей переменной.

Пример:

```typescript
const user = {

    id: 1,

    name: "John"

};


type User = typeof user;
```

Теперь:

```typescript
type User = {
    id:number;
    name:string;
}
```

---

# Интерфейс функционального объекта (Function Interface)

В TypeScript интерфейс может описывать не только структуру объекта, но и **сигнатуру функции**.

Такой интерфейс определяет:

* какие параметры принимает функция;
* какие типы параметров используются;
* какой тип возвращается.

---

## Создание интерфейса функции

Синтаксис:

```typescript
interface InterfaceName {

    (
        параметры
    ): возвращаемыйТип;

}
```

Пример:

```typescript
interface Calculate {

    (
        a: number,
        b: number
    ): number;

}
```

Теперь переменная может хранить только функцию с такой сигнатурой:

```typescript
const sum: Calculate = (
    a,
    b
) => {

    return a + b;

};
```

---

Если функция имеет неправильную сигнатуру:

```typescript
const sum: Calculate = (
    a: string,
    b: string
) => {

    return a + b;

};
```

TypeScript выдаст ошибку:

```text
Type '(a: string, b: string) => string' is not assignable to type 'Calculate'
```

---

## Интерфейс функции с дополнительными свойствами

Функции в JavaScript являются объектами, поэтому они могут иметь свойства.

Пример:

```typescript
interface Counter {

    (start: number): string;

    interval: number;

}
```

Использование:

```typescript
const counter = (
    start: number
) => {

    return `Start: ${start}`;

};


counter.interval = 1000;
```

---

## Интерфейс callback-функции

Часто используется для описания обработчиков:

```typescript
interface ClickHandler {

    (
        event: MouseEvent
    ): void;

}


const handleClick: ClickHandler = (
    event
) => {

    console.log(event);

};
```

---

# Интерфейс словаря (Dictionary Interface)

Интерфейс словаря описывает объект, у которого ключи неизвестны заранее, но имеют определенный тип.

Используется **index signature**.

---

## Синтаксис

```typescript
interface Dictionary {

    [key: string]: type;

}
```

---

## Пример

```typescript
interface UserDictionary {

    [id: string]: string;

}
```

Теперь объект:

```typescript
const users: UserDictionary = {

    "1": "John",

    "2": "Alex"

};
```

---

Можно обращаться через ключ:

```typescript
console.log(users["1"]);
```

Результат:

```text
John
```

---

## Словарь объектов

Например, хранение пользователей по id:

```typescript
interface User {

    id: number;

    name: string;

}


interface UserDictionary {

    [id: string]: User;

}
```

Использование:

```typescript
const users: UserDictionary = {

    "1": {
        id:1,
        name:"John"
    },

    "2": {
        id:2,
        name:"Alex"
    }

};
```

---

## Ограничение типов ключей

Индекс может быть:

* `string`
* `number`
* `symbol`

Пример:

```typescript
interface Dictionary {

    [key: number]: string;

}
```

---

# Array-Like объект

Array-Like объект — это объект, который похож на массив, но не является настоящим массивом.

Он обычно имеет:

* числовые индексы;
* свойство `length`.

---

Пример:

```javascript
const arrayLike = {

    0: "Hello",

    1: "World",

    length: 2

};
```

---

В TypeScript можно описать такой объект:

```typescript
interface ArrayLike<T> {

    [index: number]: T;

    length: number;

}
```

---

Использование:

```typescript
const users: ArrayLike<string> = {

    0: "John",

    1: "Alex",

    length: 2

};
```

---

## Отличие Array и Array-Like

| Array                               | Array-Like             |
| ----------------------------------- | ---------------------- |
| Настоящий массив                    | Объект с индексами     |
| Есть методы `map`, `filter`, `push` | Может не иметь методов |
| `Array.isArray()` возвращает true   | Возвращает false       |

---

Пример:

```typescript
const arr = ["a", "b"];

arr.map(x => x);
```

Работает.

---

Array-like:

```typescript
const obj = {
    0:"a",
    1:"b",
    length:2
};
```

Метод:

```typescript
obj.map();
```

Ошибка.

---

# Тип-перечисление enum

`enum` — это специальный тип TypeScript, который позволяет создавать набор именованных констант.

Используется для представления фиксированного набора значений.

---

## Числовой enum

```typescript
enum Direction {

    Up,

    Down,

    Left,

    Right

}
```

TypeScript автоматически присвоит значения:

```typescript
Up = 0
Down = 1
Left = 2
Right = 3
```

---

Использование:

```typescript
let direction: Direction;

direction = Direction.Up;
```

---

## Явное указание значений

```typescript
enum Status {

    Success = 200,

    NotFound = 404,

    ServerError = 500

}
```

Использование:

```typescript
const code = Status.Success;
```

---

## Строковый enum

Можно использовать строки:

```typescript
enum Role {

    Admin = "ADMIN",

    User = "USER",

    Guest = "GUEST"

}
```

---

Использование:

```typescript
const role: Role = Role.Admin;
```

---

Преимущество строковых enum:

* легче читать;
* удобнее при работе с API;
* нет обратного отображения.

---

# Reverse Mapping у числовых enum

Числовые enum создают двустороннее отображение.

Пример:

```typescript
enum Color {

    Red,

    Green

}
```

После компиляции:

```javascript
{
    0:"Red",
    1:"Green",
    Red:0,
    Green:1
}
```

Можно:

```typescript
Color.Red;
```

Получить:

```text
0
```

И наоборот:

```typescript
Color[0];
```

Получить:

```text
Red
```

---

# Const enum

`const enum` — это оптимизированная версия enum.

Значения вставляются напрямую во время компиляции.

---

Пример:

```typescript
const enum Direction {

    Up,

    Down

}


let direction = Direction.Up;
```

После компиляции:

```javascript
let direction = 0;
```

---

## Отличия enum и const enum

| enum                                   | const enum        |
| -------------------------------------- | ----------------- |
| Создает объект во время выполнения     | Не создает объект |
| Можно использовать динамический доступ | Нельзя            |
| Больше памяти                          | Оптимизирован     |
| Есть reverse mapping                   | Нет               |

---

Пример:

Обычный enum:

```typescript
Status["Success"]
```

Работает.

---

`const enum`:

```typescript
Direction["Up"]
```

Ошибка.

---

# Объединение нескольких enum

В TypeScript нельзя напрямую объединять enum через наследование.

Например:

```typescript
enum A {

    X

}


enum B {

    Y

}
```

Нельзя:

```typescript
enum C extends A, B {}
```

---

## Способ 1: Использование union типов

Самый распространенный вариант:

```typescript
enum UserRole {

    Admin = "ADMIN",

    User = "USER"

}


enum SystemRole {

    Guest = "GUEST"

}


type Role =
    UserRole
    | SystemRole;
```

Теперь:

```typescript
let role: Role;

role = UserRole.Admin;

role = SystemRole.Guest;
```

---

## Способ 2: Объединение объектов

```typescript
enum Admin {

    Create = "CREATE",

    Delete = "DELETE"

}


enum User {

    Read = "READ"

}


const Permissions = {

    ...Admin,

    ...User

};
```

Использование:

```typescript
Permissions.Create;
```

---

## Способ 3: Общий enum

Иногда проще создать один enum:

```typescript
enum Permission {

    Create = "CREATE",

    Read = "READ",

    Delete = "DELETE"

}
```

---

# Кортежи (Tuples)

Кортеж — это массив фиксированной длины, где каждый элемент имеет определенный тип.

В обычном массиве:

```typescript
const values = [
    "John",
    25
];
```

TypeScript может определить:

```typescript
(string | number)[]
```

---

Кортеж:

```typescript
const user: [
    string,
    number
] = [

    "John",

    25

];
```

Здесь:

* первый элемент всегда `string`;
* второй элемент всегда `number`.

---

## Доступ к элементам

```typescript
console.log(user[0]);
```

Тип:

```typescript
string
```

---

```typescript
console.log(user[1]);
```

Тип:

```typescript
number
```

---

# Необязательные элементы tuple

Используется `?`.

```typescript
type User = [

    string,

    number?

];
```

Теперь:

```typescript
const user1: User = [
    "John"
];


const user2: User = [
    "John",
    25
];
```

---

# Rest элементы tuple

Можно использовать оператор `...`.

```typescript
type Numbers = [

    string,

    ...number[]

];
```

Допустимо:

```typescript
const values: Numbers = [

    "sum",

    1,

    2,

    3

];
```

---

# Readonly tuple

Нельзя изменять:

```typescript
const point: readonly [
    number,
    number
] = [

    10,
    20

];
```

Нельзя:

```typescript
point[0] = 5;
```

---

# Использование tuple

## React useState

Один из самых известных примеров:

```typescript
const [
    count,
    setCount
] = useState<number>(0);
```

`useState` возвращает tuple:

```typescript
[
    number,
    Dispatch<number>
]
```

---

## Координаты

```typescript
type Point = [

    number,

    number

];


const position: Point = [

    10,

    20

];
```

---

## Ответ API

```typescript
type Response = [

    boolean,

    string

];


const result: Response = [

    true,

    "Success"

];
```

---

# Модификатор `readonly`

`readonly` — это модификатор TypeScript, который делает свойство объекта доступным только для чтения после инициализации.

Он запрещает изменение значения свойства после создания объекта.

---

## Использование в интерфейсах

```typescript
interface User {

    readonly id: number;

    name: string;

}
```

Создание объекта:

```typescript
const user: User = {

    id: 1,

    name: "John"

};
```

Изменение обычного свойства разрешено:

```typescript
user.name = "Alex";
```

Изменение `readonly` свойства запрещено:

```typescript
user.id = 2;
```

Ошибка:

```text
Cannot assign to 'id' because it is a read-only property
```

---

## Использование в типах

```typescript
type Product = {

    readonly code: string;

    price: number;

};
```

---

## `readonly` в классах

```typescript
class User {

    readonly id: number;


    constructor(id: number) {

        this.id = id;

    }

}
```

После создания:

```typescript
const user = new User(1);

user.id = 2;
```

Ошибка.

---

## `readonly` массивы

Обычный массив:

```typescript
const numbers: number[] = [
    1,
    2,
    3
];

numbers.push(4);
```

Разрешено.

---

Readonly массив:

```typescript
const numbers: readonly number[] = [
    1,
    2,
    3
];
```

Нельзя:

```typescript
numbers.push(4);
```

Ошибка:

```text
Property 'push' does not exist on type 'readonly number[]'
```

---

## `Readonly<T>`

TypeScript имеет встроенный Utility Type:

```typescript
interface User {

    name: string;

    age: number;

}


type ReadonlyUser = Readonly<User>;
```

Получается:

```typescript
{
    readonly name: string;
    readonly age: number;
}
```

---

# Наследование и объединение интерфейсов

Интерфейсы в TypeScript могут расширять другие интерфейсы через `extends`.

Это позволяет создавать новые типы на основе существующих.

---

# Наследование интерфейсов

Пример:

```typescript
interface Person {

    name: string;

    age: number;

}


interface Employee extends Person {

    salary: number;

}
```

Теперь `Employee` содержит все свойства `Person`:

```typescript
const employee: Employee = {

    name: "John",

    age: 30,

    salary: 5000

};
```

---

## Множественное наследование интерфейсов

Интерфейс может расширять несколько интерфейсов:

```typescript
interface Address {

    city: string;

}


interface Contact {

    email: string;

}


interface User extends Address, Contact {

    name: string;

}
```

Использование:

```typescript
const user: User = {

    name: "John",

    city: "Paris",

    email: "test@test.com"

};
```

---

# Объединение интерфейсов (Declaration Merging)

TypeScript позволяет объявлять интерфейс несколько раз.

Они автоматически объединяются.

---

Пример:

```typescript
interface User {

    name: string;

}


interface User {

    age: number;

}
```

TypeScript объединит их:

```typescript
interface User {

    name: string;

    age: number;

}
```

---

Использование:

```typescript
const user: User = {

    name: "John",

    age: 25

};
```

---

## Отличие `extends` и объединения

| extends                        | Declaration Merging      |
| ------------------------------ | ------------------------ |
| Создает новый интерфейс        | Объединяет существующие  |
| Используется явно              | Происходит автоматически |
| Работает между разными именами | Требует одинаковое имя   |

---

# Полиморфизм подтипов (Subtype Polymorphism)

Полиморфизм подтипов — это способность использовать объект одного типа там, где ожидается другой тип, если он является его подтипом.

В TypeScript это основано на **структурной типизации**.

---

## Структурная типизация

TypeScript проверяет не имя типа, а его структуру.

Например:

```typescript
interface Animal {

    name: string;

}


interface Dog {

    name: string;

    breed: string;

}
```

`Dog` содержит все свойства `Animal`, поэтому он является подтипом.

---

Можно:

```typescript
const dog: Dog = {

    name: "Rex",

    breed: "Husky"

};


const animal: Animal = dog;
```

Работает.

---

## Пример функции

```typescript
function printAnimal(
    animal: Animal
) {

    console.log(animal.name);

}
```

Можно передать:

```typescript
printAnimal(dog);
```

Хотя функция ожидает `Animal`.

---

# Полиморфизм через классы

```typescript
class Animal {

    move() {

        console.log("Moving");

    }

}


class Dog extends Animal {

    move() {

        console.log("Running");

    }

}
```

Использование:

```typescript
let animal: Animal;

animal = new Dog();

animal.move();
```

Результат:

```text
Running
```

---

## Зачем нужен полиморфизм?

Позволяет:

* писать универсальный код;
* заменять реализации;
* использовать наследование;
* создавать расширяемые архитектуры.

---

# Класс объекта (Object Class)

В TypeScript класс — это шаблон для создания объектов.

Класс объединяет:

* свойства;
* методы;
* конструктор;
* модификаторы доступа.

---

## Создание класса

```typescript
class User {

    name: string;


    constructor(name: string) {

        this.name = name;

    }


    sayHello(): string {

        return `Hello ${this.name}`;

    }

}
```

---

Создание объекта:

```typescript
const user = new User("John");

console.log(
    user.sayHello()
);
```

Результат:

```text
Hello John
```

---

# Модификаторы доступа классов

TypeScript поддерживает:

* `public`
* `private`
* `protected`

---

## public

Доступен везде.

```typescript
class User {

    public name: string;

}
```

---

## private

Доступен только внутри класса.

```typescript
class User {

    private password: string;

}
```

Нельзя:

```typescript
user.password;
```

---

## protected

Доступен внутри класса и наследников.

```typescript
class User {

    protected id: number;

}


class Admin extends User {

    showId() {

        console.log(this.id);

    }

}
```

---

# Абстрактные классы

`abstract` используется для создания базовых классов.

```typescript
abstract class Animal {

    abstract makeSound(): void;

}
```

Нельзя создать:

```typescript
new Animal();
```

Но можно наследовать:

```typescript
class Dog extends Animal {

    makeSound() {

        console.log("Woof");

    }

}
```

---

# Объединение типов (Union Types)

Union Type позволяет переменной иметь несколько возможных типов.

Используется оператор:

```typescript
|
```

---

## Пример

```typescript
let id: string | number;
```

Теперь:

```typescript
id = 10;

id = "abc";
```

Оба варианта допустимы.

---

## Union с объектами

```typescript
interface User {

    name: string;

}


interface Admin {

    permissions: string[];

}


type Account =
    User | Admin;
```

---

Использование:

```typescript
const account: Account = {

    name: "John"

};
```

или:

```typescript
const account: Account = {

    permissions: [
        "delete"
    ]

};
```

---

# Narrowing типов

При работе с union нужно определить конкретный тип.

---

## typeof

```typescript
function print(
    value: string | number
) {

    if(typeof value === "string") {

        console.log(
            value.toUpperCase()
        );

    }

}
```

---

## in

```typescript
function check(
    user: User | Admin
) {

    if("permissions" in user) {

        console.log(
            user.permissions
        );

    }

}
```

---

## instanceof

```typescript
if(value instanceof Date) {

    console.log(value.getTime());

}
```

---

# Union vs Intersection

Union:

```typescript
type Result =
    string | number;
```

Означает:

> Может быть строкой ИЛИ числом.

---

Intersection:

```typescript
type User =
    Person & Employee;
```

Означает:

> Должен содержать свойства обоих типов.

---

# Специальный тип `never`

`never` — это специальный тип TypeScript, который обозначает значение, которое **никогда не возникает**.

Используется для функций, которые:

* никогда не завершаются;
* всегда выбрасывают ошибку;
* содержат недостижимый код.

---

## Функция, которая всегда выбрасывает ошибку

```typescript
function throwError(
    message: string
): never {

    throw new Error(message);

}
```

Такая функция никогда не возвращает значение.

---

## Бесконечный цикл

```typescript
function infiniteLoop(): never {

    while(true) {

    }

}
```

Функция не может завершиться, поэтому ее тип — `never`.

---

## Отличие `never` от `void`

`void` означает:

> Функция завершилась, но ничего не вернула.

Пример:

```typescript
function log(): void {

    console.log("Hello");

}
```

Функция завершится.

---

`never` означает:

> Функция никогда не завершится и не вернет значение.

Пример:

```typescript
function fail(): never {

    throw new Error();

}
```

---

## `never` в проверке исчерпывающих вариантов

Часто используется с `switch` для проверки всех вариантов.

Пример:

```typescript
type Status =
    | "loading"
    | "success"
    | "error";


function checkStatus(
    status: Status
) {

    switch(status) {

        case "loading":
            return "Loading";


        case "success":
            return "Success";


        case "error":
            return "Error";

    }

}
```

Если добавить новый статус:

```typescript
type Status =
    | "loading"
    | "success"
    | "error"
    | "pending";
```

TypeScript может обнаружить, что обработан не весь список.

---

Использование функции проверки:

```typescript
function assertNever(
    value: never
): never {

    throw new Error(
        "Unexpected value"
    );

}
```

Пример:

```typescript
function checkStatus(
    status: Status
) {

    switch(status) {

        case "loading":
            return;


        case "success":
            return;


        case "error":
            return;


        default:
            assertNever(status);

    }

}
```

---

# Разница между `interface` и `type`

`interface` и `type` используются для создания собственных типов в TypeScript.

Они имеют много общего, но отличаются возможностями.

---

# Interface

`interface` используется преимущественно для описания структуры объектов.

Пример:

```typescript
interface User {

    id: number;

    name: string;

}
```

---

# Type Alias

`type` создает псевдоним любого типа.

Пример:

```typescript
type User = {

    id: number;

    name: string;

};
```

---

# Основные различия

| Interface                        | Type                        |
| -------------------------------- | --------------------------- |
| Только объектные структуры       | Любые типы                  |
| Поддерживает `extends`           | Использует intersection `&` |
| Поддерживает declaration merging | Не поддерживает             |
| Хорош для публичных API          | Хорош для сложных типов     |

---

# 1. Объединение типов

`type` поддерживает union:

```typescript
type ID =
    string | number;
```

Через interface такое невозможно.

---

# 2. Intersection

Type:

```typescript
type User = {

    name:string;

};


type Admin = {

    permissions:string[];

};


type AdminUser =
    User & Admin;
```

---

В interface:

```typescript
interface AdminUser 
extends User, Admin {

}
```

---

# 3. Declaration Merging

Interface можно объявить несколько раз:

```typescript
interface User {

    name:string;

}


interface User {

    age:number;

}
```

TypeScript объединит:

```typescript
interface User {

    name:string;

    age:number;

}
```

---

С `type`:

```typescript
type User = {

    name:string;

};


type User = {

    age:number;

};
```

Ошибка:

```text
Duplicate identifier 'User'
```

---

# 4. Primitive типы

`type` может создавать примитивы:

```typescript
type ID = number;
```

Interface:

```typescript
interface ID {

}
```

для такого случая использовать нельзя.

---

# Когда использовать interface?

Обычно:

* модели объектов;
* публичные контракты;
* классы;
* библиотеки.

Пример:

```typescript
interface User {

    id:number;

    name:string;

}
```

---

# Когда использовать type?

Обычно:

* union;
* intersection;
* сложные вычисляемые типы.

Пример:

```typescript
type Result =
    Success | Error;
```

---

# Модификатор `override`

`override` — это модификатор TypeScript, который используется при переопределении метода или свойства родительского класса.

Он показывает, что член класса намеренно заменяет реализацию из базового класса.

---

## Пример без override

```typescript
class Animal {

    move() {

        console.log("Moving");

    }

}


class Dog extends Animal {

    move() {

        console.log("Running");

    }

}
```

Код работает.

---

## С `override`

```typescript
class Animal {

    move() {

        console.log("Moving");

    }

}


class Dog extends Animal {

    override move() {

        console.log("Running");

    }

}
```

---

Теперь TypeScript проверяет:

* существует ли такой метод в родителе;
* совпадает ли его сигнатура.

---

## Ошибка при неправильном переопределении

```typescript
class Dog extends Animal {

    override fly() {

    }

}
```

Ошибка:

```text
This member cannot have an 'override' modifier because it is not declared in the base class
```

---

## Зачем нужен override?

Он помогает:

* избежать случайных ошибок;
* улучшить читаемость;
* безопасно изменять родительские классы.

---

## `noImplicitOverride`

Можно включить обязательное использование:

```json
{
    "compilerOptions": {
        "noImplicitOverride": true
    }
}
```

Теперь все переопределения должны иметь `override`.

---

# Модификатор accessor

Accessor — это специальные методы доступа к свойствам объекта:

* `get`
* `set`

Они позволяют контролировать чтение и изменение данных.

---

# Getter (`get`)

Getter позволяет получать значение как обычное свойство.

Пример:

```typescript
class User {

    firstName: string;

    lastName: string;


    constructor(
        firstName:string,
        lastName:string
    ){

        this.firstName = firstName;

        this.lastName = lastName;

    }


    get fullName(): string {

        return `${this.firstName} ${this.lastName}`;

    }

}
```

Использование:

```typescript
const user = new User(
    "John",
    "Smith"
);


console.log(
    user.fullName
);
```

Результат:

```text
John Smith
```

---

# Setter (`set`)

Setter контролирует изменение значения.

```typescript
class User {

    private _age:number = 0;


    set age(
        value:number
    ){

        if(value < 0){

            throw new Error(
                "Invalid age"
            );

        }

        this._age = value;

    }


    get age(){

        return this._age;

    }

}
```

Использование:

```typescript
const user = new User();

user.age = 25;

console.log(
    user.age
);
```

---

## Зачем нужны accessor?

Используются для:

* валидации данных;
* скрытия внутреннего состояния;
* вычисляемых свойств;
* контроля доступа.

---

# Оператор `satisfies`

`satisfies` — оператор TypeScript, появившийся в версии TypeScript 4.9.

Он проверяет, соответствует ли значение определенному типу, но при этом **сохраняет исходный тип выражения**.

---

## Пример

```typescript
type Config = {

    url:string;

    timeout:number;

};


const config = {

    url:"api.com",

    timeout:5000

} satisfies Config;
```

TypeScript проверяет:

* есть ли `url`;
* есть ли `timeout`;
* правильные ли типы.

---

Но тип переменной остается:

```typescript
{
    url:string;
    timeout:number;
}
```

---

# Отличие `satisfies` от аннотации типа

Аннотация:

```typescript
const config: Config = {

    url:"api.com",

    timeout:5000

};
```

Переменная получает тип:

```typescript
Config
```

---

`satisfies`:

```typescript
const config = {

    url:"api.com",

    timeout:5000

} satisfies Config;
```

Проверяет соответствие, но сохраняет точный тип.

---

## Пример с лишним свойством

```typescript
type User = {

    name:string;

};


const user = {

    name:"John",

    age:25

} satisfies User;
```

Ошибка:

```text
Object literal may only specify known properties
```

---

## `satisfies` с объектами конфигурации

Частый пример:

```typescript
type Routes = {

    home:string;

    profile:string;

};


const routes = {

    home:"/",

    profile:"/profile"

} satisfies Routes;
```

Теперь:

```typescript
routes.home
```

имеет точный тип:

```typescript
"/"
```

а не просто:

```typescript
string
```

---

# `satisfies` vs `as`

## Type Assertion (`as`)

```typescript
const value =
    data as User;
```

Говорит TypeScript:

> Считай это User, даже если есть сомнения.

---

## `satisfies`

```typescript
const value =
    data satisfies User;
```

Говорит:

> Проверь, что объект соответствует User.

---

`satisfies` безопаснее, потому что не отключает проверку типов.

---

# Небезопасные приведения типов (Unsafe Type Assertions)

Небезопасное приведение типов — это принудительное указание TypeScript считать значение определенным типом без проверки фактического соответствия.

Используется оператор:

```typescript
as
```

или синтаксис:

```typescript
<Type>
```

TypeScript доверяет разработчику и не проверяет, является ли приведение корректным во время выполнения.

---

## Пример

```typescript
const value: unknown = "Hello";

const text = value as string;
```

TypeScript считает, что `value` является строкой.

---

Но если значение другое:

```typescript
const value: unknown = 123;

const text = value as string;

console.log(text.toUpperCase());
```

Во время выполнения возникнет ошибка:

```text
TypeError: text.toUpperCase is not a function
```

---

## Пример с DOM

Частый случай:

```typescript
const input =
    document.getElementById("email")
    as HTMLInputElement;


input.value = "test@test.com";
```

TypeScript не знает реальный тип элемента, поэтому разработчик указывает его вручную.

---

# Почему приведение считается небезопасным?

Потому что TypeScript работает только на этапе компиляции.

После компиляции:

```typescript
const value = data as User;
```

превращается в обычный JavaScript:

```javascript
const value = data;
```

Информация о типах полностью удаляется.

---

# Более безопасный вариант — Type Guard

Вместо:

```typescript
const user =
    data as User;
```

лучше:

```typescript
function isUser(
    value: unknown
): value is User {

    return (
        typeof value === "object" &&
        value !== null &&
        "name" in value
    );

}
```

Использование:

```typescript
if(isUser(data)) {

    console.log(data.name);

}
```

---

# Проблемные приведения типов (Problematic Type Assertions)

Некоторые приведения TypeScript запрещает, потому что типы слишком разные.

---

## Пример

```typescript
const value = "hello" as number;
```

Ошибка:

```text
Conversion of type 'string' to type 'number' may be a mistake
```

Причина:

`string` и `number` не имеют достаточного пересечения.

---

## Двойное приведение через unknown

Иногда разработчики обходят проверку:

```typescript
const value =
    "hello" as unknown as number;
```

Теперь TypeScript разрешит код.

---

Но:

```typescript
console.log(value + 10);
```

Результат:

```text
hello10
```

или другая неожиданная логика.

---

## Когда используется двойное приведение?

Редко:

* работа со сторонними библиотеками;
* несовершенные типы;
* миграция старого JavaScript-кода.

---

## Почему это опасно?

Такой код:

```typescript
data as unknown as SomeType
```

фактически отключает систему типов.

TypeScript больше не может гарантировать безопасность.

---

# Декораторы классов (Class Decorators)

Декораторы — это специальные функции, которые позволяют изменять или добавлять поведение классам, методам, свойствам и параметрам.

Используются через символ:

```typescript
@
```

---

## Включение декораторов

В `tsconfig.json`:

```json
{
    "compilerOptions": {
        "experimentalDecorators": true
    }
}
```

---

# Синтаксис декоратора класса

```typescript
function Decorator(
    constructor: Function
) {

}
```

Использование:

```typescript
@Decorator
class User {

}
```

---

## Пример

```typescript
function Logger(
    constructor: Function
) {

    console.log(
        "Class created:",
        constructor.name
    );

}


@Logger
class User {

    constructor(
        public name:string
    ) {}

}
```

При объявлении класса:

```text
Class created: User
```

---

# Изменение класса через декоратор

Декоратор может вернуть новый класс.

Пример:

```typescript
function AddTimestamp(
    constructor: Function
) {

    constructor.prototype.createdAt =
        new Date();

}


@AddTimestamp
class User {

}
```

Теперь экземпляр класса получает новое свойство.

---

# Где используются декораторы классов?

* Dependency Injection.
* ORM.
* Валидация моделей.
* Метаданные.
* Фреймворки.

Примеры:

* Angular использует декораторы для компонентов и сервисов.
* NestJS использует декораторы для контроллеров и зависимостей.

---

# Декораторы методов класса (Method Decorators)

Методовый декоратор применяется к методам класса.

Он получает:

1. объект прототипа;
2. имя метода;
3. описание свойства.

---

## Сигнатура

```typescript
function Decorator(
    target: Object,
    propertyKey: string,
    descriptor: PropertyDescriptor
) {

}
```

---

## Пример логирования

```typescript
function Log(
    target: Object,
    propertyKey: string,
    descriptor: PropertyDescriptor
) {

    const original =
        descriptor.value;


    descriptor.value =
    function(...args:any[]) {

        console.log(
            "Arguments:",
            args
        );

        return original.apply(
            this,
            args
        );

    };

}
```

Использование:

```typescript
class Calculator {


    @Log
    sum(
        a:number,
        b:number
    ) {

        return a + b;

    }

}
```

---

Вызов:

```typescript
calculator.sum(2,3);
```

Вывод:

```text
Arguments: [2,3]
```

---

# Возможности декораторов методов

Можно:

* логировать вызовы;
* измерять время выполнения;
* добавлять кеширование;
* проверять права доступа;
* изменять поведение метода.

---

## Пример измерения времени

```typescript
function Measure(
    target:Object,
    key:string,
    descriptor:PropertyDescriptor
){

    const method =
        descriptor.value;


    descriptor.value =
    function(...args:any[]){

        console.time(key);

        const result =
            method.apply(
                this,
                args
            );

        console.timeEnd(key);

        return result;

    };

}
```

---

# Декораторы свойств класса (Property Decorators)

Property Decorator применяется к свойствам класса.

Используется для:

* добавления метаданных;
* регистрации свойств;
* создания ORM-моделей.

---

## Сигнатура

```typescript
function Decorator(
    target:Object,
    propertyKey:string
){

}
```

---

## Пример

```typescript
function Required(
    target:Object,
    propertyKey:string
){

    console.log(
        `Property ${propertyKey}`
    );

}


class User {

    @Required
    name:string;

}
```

Результат:

```text
Property name
```

---

# Пример создания метаданных

```typescript
const requiredFields =
    new Set<string>();


function Required(
    target:Object,
    key:string
){

    requiredFields.add(key);

}


class User {

    @Required
    name:string;


    @Required
    email:string;

}
```

Теперь можно хранить список обязательных полей.

---

# Ограничения property decorators

Property decorator:

* не получает `descriptor`;
* не может напрямую изменить значение свойства;
* используется в основном для метаданных.

---

# Порядок выполнения декораторов

Если есть несколько декораторов:

```typescript
@First
@Second
class User {}
```

Они применяются снизу вверх:

```text
Second → First
```

---

Для методов:

```typescript
@First
@Second
method(){}
```

Порядок такой же.

---

# Современные декораторы TypeScript

TypeScript поддерживает два варианта:

1. **Legacy decorators**

   * включаются через `experimentalDecorators`;
   * используются в Angular/NestJS.

2. **Stage 3 ECMAScript decorators**

   * современный стандарт JavaScript;
   * имеют другой API.

---

# Агрегация метаинформации (Metadata Aggregation)

Агрегация метаинформации — это процесс сбора и хранения дополнительной информации о классах, методах, свойствах или параметрах во время компиляции или выполнения программы.

В TypeScript метаданные часто используются вместе с декораторами.

Основные применения:

* Dependency Injection;
* ORM-системы;
* валидация объектов;
* сериализация;
* построение схем данных.

---

## Включение поддержки метаданных

Для работы с метаданными обычно используются:

```json
{
    "compilerOptions": {
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true
    }
}
```

Опция:

```text
emitDecoratorMetadata
```

заставляет TypeScript генерировать дополнительную информацию о типах.

---

## Пример с декоратором

```typescript
function Injectable(
    constructor: Function
) {

}
```

Использование:

```typescript
@Injectable
class UserService {

}
```

TypeScript может сохранить информацию о классе:

```typescript
UserService
```

и его зависимостях.

---

## Библиотека reflect-metadata

Часто используется пакет:

```typescript
import "reflect-metadata";
```

Он добавляет API для работы с метаданными.

---

Пример:

```typescript
Reflect.defineMetadata(
    "role",
    "admin",
    User
);
```

Получение:

```typescript
const role =
    Reflect.getMetadata(
        "role",
        User
    );
```

---

## Пример Dependency Injection

```typescript
class Database {

}


class UserService {

    constructor(
        private db: Database
    ) {}

}
```

Фреймворк может получить информацию:

```text
UserService требует Database
```

и автоматически создать зависимость.

---

# Декораторы статических частей класса

Статические части класса принадлежат самому классу, а не его экземплярам.

Пример:

```typescript
class User {

    static count = 0;

}
```

Декораторы могут применяться к:

* статическим методам;
* статическим свойствам.

---

# Декоратор статического метода

Пример:

```typescript
function Log(
    target: Object,
    propertyKey: string,
    descriptor: PropertyDescriptor
) {

    console.log(propertyKey);

}
```

Использование:

```typescript
class User {

    @Log
    static create() {

        return new User();

    }

}
```

---

Для статического метода:

```typescript
target
```

будет самим классом:

```typescript
User
```

а не:

```typescript
User.prototype
```

---

# Декоратор статического свойства

Пример:

```typescript
function Column(
    target: Object,
    propertyKey: string
) {

    console.log(propertyKey);

}


class User {

    @Column
    static tableName = "users";

}
```

---

# Отличие декораторов экземпляра и статических частей

| Тип                  | target             |
| -------------------- | ------------------ |
| Свойство экземпляра  | `prototype` класса |
| Метод экземпляра     | `prototype` класса |
| Статическое свойство | сам класс          |
| Статический метод    | сам класс          |

---

# Глобальные типы и формат `.d.ts`

Файлы `.d.ts` — это файлы деклараций TypeScript.

Они содержат только описания типов и не содержат реализации.

---

Пример обычного JavaScript:

```javascript
function sum(a,b){

    return a+b;

}
```

Описание типов:

```typescript
declare function sum(
    a:number,
    b:number
):number;
```

---

Файл:

```
math.d.ts
```

может содержать:

```typescript
declare function sum(
    a:number,
    b:number
):number;
```

Теперь TypeScript знает о функции.

---

# Зачем нужны `.d.ts`?

Используются для:

* типизации JavaScript библиотек;
* описания внешних API;
* добавления типов без изменения исходного кода;
* хранения глобальных типов.

---

# Пример декларации библиотеки

Есть JavaScript библиотека:

```javascript
// library.js

function hello(name){

    return `Hello ${name}`;

}
```

Создаем:

```
library.d.ts
```

Содержимое:

```typescript
declare function hello(
    name:string
):string;
```

Теперь TypeScript понимает:

```typescript
hello("John");
```

---

# DefinitelyTyped

Большая часть типов для JavaScript библиотек хранится в репозитории:

[DefinitelyTyped GitHub repository](https://github.com/DefinitelyTyped/DefinitelyTyped?utm_source=chatgpt.com)

Устанавливаются через:

```bash
npm install @types/package-name
```

Например:

```bash
npm install @types/node
```

---

# Глобальные декларации

Можно создавать глобальные типы:

```typescript
declare global {

    interface Window {

        userId:number;

    }

}
```

Теперь:

```typescript
window.userId;
```

имеет тип:

```typescript
number
```

---

# Оператор `declare`

`declare` используется для сообщения TypeScript:

> Этот объект существует во время выполнения, но его реализация находится где-то еще.

---

## Объявление переменной

JavaScript:

```javascript
window.myApp = {};
```

TypeScript:

```typescript
declare const myApp: {

    version:string;

};
```

Использование:

```typescript
console.log(
    myApp.version
);
```

---

# Объявление функции

```typescript
declare function calculate(
    value:number
):number;
```

Реализации нет.

TypeScript просто знает о ее существовании.

---

# Объявление класса

```typescript
declare class User {

    name:string;

    constructor(
        name:string
    );

}
```

---

# `declare module`

Используется для описания модулей без типов.

Например:

```typescript
declare module "my-library" {

    export function hello(
        name:string
    ):string;

}
```

Теперь:

```typescript
import { hello }
from "my-library";
```

будет типизирован.

---

# Расширение `globalThis`

`globalThis` — это универсальный объект глобальной области видимости JavaScript.

Он работает во всех средах:

* браузер;
* Node.js;
* Web Worker.

---

## Примеры

В браузере:

```javascript
window
```

В Node.js:

```javascript
global
```

Общий вариант:

```javascript
globalThis
```

---

## Расширение типа globalThis

Можно добавить собственные свойства.

Пример:

```typescript
declare global {

    var appVersion:string;

}
```

Теперь:

```typescript
globalThis.appVersion = "1.0.0";
```

---

# Расширение Window через globalThis

Например, добавляем глобальный объект:

```typescript
declare global {

    interface Window {

        apiUrl:string;

    }

}
```

Использование:

```typescript
window.apiUrl =
    "https://api.com";
```

---

# Расширение встроенных объектов

Можно расширять существующие типы.

Например:

```typescript
declare global {

    interface Array<T> {

        first():T;

    }

}
```

Теперь:

```typescript
const numbers = [1,2,3];

numbers.first();
```

TypeScript будет знать о методе.

---

# Важный момент

Если файл содержит:

```typescript
declare global {}
```

он должен быть модулем.

Добавляют:

```typescript
export {};
```

Пример:

```typescript
export {};

declare global {

    interface Window {

        appName:string;

    }

}
```

---

# Типизация модуля на JavaScript

TypeScript позволяет добавлять типизацию для JavaScript-модулей, у которых нет встроенных типов.

Для этого используются **файлы деклараций `.d.ts`**.

Файл `.d.ts` описывает:

* функции;
* классы;
* переменные;
* объекты;
* экспортируемые значения модуля.

При этом он не содержит реализации.

---

## Пример JavaScript-модуля

Допустим, есть библиотека:

```javascript
// math.js

export function sum(a, b) {

    return a + b;

}
```

TypeScript не знает типы этой функции.

---

Создаем файл:

```text
math.d.ts
```

Описание:

```typescript
export function sum(
    a: number,
    b: number
): number;
```

Теперь TypeScript понимает:

```typescript
import { sum } from "./math";

const result = sum(10, 20);
```

Тип результата:

```typescript
number
```

---

# Типизация npm-пакета JavaScript

Структура пакета:

```
my-library/
│
├── index.js
├── index.d.ts
└── package.json
```

---

`index.js`:

```javascript
function hello(name) {

    return `Hello ${name}`;

}

module.exports = {
    hello
};
```

---

`index.d.ts`:

```typescript
export function hello(
    name:string
):string;
```

---

`package.json`:

```json
{
    "name": "my-library",
    "main": "index.js",
    "types": "index.d.ts"
}
```

Поле:

```json
"types"
```

указывает TypeScript, где искать декларации типов.

---

# Использование `declare module`

Если библиотека не имеет `.d.ts`, можно создать собственное описание.

Например:

```typescript
declare module "my-library" {

    export function hello(
        name:string
    ):string;

}
```

Теперь:

```typescript
import { hello }
from "my-library";
```

будет типизирован.

---

# Типизация модулей без типов

Например:

```typescript
import library from "old-library";
```

Ошибка:

```text
Could not find declaration file for module 'old-library'
```

Создаем:

```
src/types/old-library.d.ts
```

Содержимое:

```typescript
declare module "old-library" {

    const value:any;

    export default value;

}
```

---

Теперь ошибка исчезнет.

---

# Разбиение одного `.d.ts` на множество файлов

В больших проектах один файл деклараций становится неудобным.

Типы можно разделять на несколько файлов.

---

## Пример структуры

```
types/
│
├── index.d.ts
├── user.d.ts
├── product.d.ts
└── api.d.ts
```

---

## user.d.ts

```typescript
interface User {

    id:number;

    name:string;

}
```

---

## product.d.ts

```typescript
interface Product {

    id:number;

    price:number;

}
```

---

## index.d.ts

Можно объединить:

```typescript
/// <reference path="./user.d.ts" />
/// <reference path="./product.d.ts" />
```

---

Теперь TypeScript знает все типы.

---

# Использование `typeRoots`

В `tsconfig.json` можно указать папку с глобальными типами:

```json
{
    "compilerOptions": {

        "typeRoots": [
            "./node_modules/@types",
            "./src/types"
        ]

    }
}
```

Теперь TypeScript автоматически ищет декларации в:

```
src/types
```

---

# Использование модулей в `.d.ts`

Если файл является модулем:

```typescript
export interface User {

    id:number;

}
```

Его можно импортировать:

```typescript
import { User }
from "./types";
```

---

# `index.d.ts` как точка входа

Часто структура библиотеки:

```
library/
│
├── src/
│   ├── user.ts
│   └── api.ts
│
├── dist/
│   ├── index.js
│   └── index.d.ts
```

`index.d.ts`:

```typescript
export * from "./user";

export * from "./api";
```

---

# Сборка TypeScript с генерацией `.d.ts` типов

TypeScript может автоматически создавать декларационные файлы при компиляции.

Используется опция:

```json
"declaration": true
```

---

## tsconfig.json

Пример:

```json
{
    "compilerOptions": {

        "declaration": true,

        "outDir": "./dist"

    }
}
```

---

Исходный файл:

```
src/user.ts
```

```typescript
export class User {

    constructor(
        public name:string
    ) {}

}
```

---

После сборки:

```
dist/
│
├── user.js
└── user.d.ts
```

---

`user.d.ts`:

```typescript
export declare class User {

    name:string;

    constructor(
        name:string
    );

}
```

---

# Основные настройки генерации типов

## `declaration`

Создает `.d.ts`:

```json
{
    "declaration": true
}
```

---

## `declarationMap`

Создает карты для перехода к исходникам:

```json
{
    "declarationMap": true
}
```

Создает:

```
user.d.ts.map
```

---

## `emitDeclarationOnly`

Создает только типы:

```json
{
    "emitDeclarationOnly": true
}
```

Результат:

```
user.d.ts
```

Без:

```
user.js
```

---

## `declarationDir`

Отдельная папка для типов:

```json
{
    "declarationDir": "./types"
}
```

---

# Сборка библиотеки TypeScript

Пример:

```
src/
│
├── index.ts
└── user.ts
```

`index.ts`:

```typescript
export * from "./user";
```

---

`tsconfig.json`:

```json
{
    "compilerOptions": {

        "target": "ES2020",

        "module": "ESNext",

        "declaration": true,

        "outDir": "dist"

    },

    "include": [
        "src"
    ]
}
```

---

Команда:

```bash
tsc
```

Создаст:

```
dist/
│
├── index.js
├── index.d.ts
├── user.js
└── user.d.ts
```

---

# `tsc`

`tsc` — это официальный компилятор TypeScript.

Полное название:

```
TypeScript Compiler
```

Он преобразует:

```
.ts
```

в:

```
.js
```

---

## Установка

Глобально:

```bash
npm install -g typescript
```

Проверка:

```bash
tsc --version
```

---

## Компиляция файла

```bash
tsc app.ts
```

Результат:

```
app.js
```

---

## Компиляция проекта

Если есть:

```
tsconfig.json
```

достаточно:

```bash
tsc
```

---

# Основные команды `tsc`

## Создать tsconfig

```bash
tsc --init
```

Создает:

```
tsconfig.json
```

---

## Режим наблюдения

```bash
tsc --watch
```

или:

```bash
tsc -w
```

Автоматическая пересборка при изменениях.

---

## Проверка типов без генерации файлов

```bash
tsc --noEmit
```

Используется в CI.

---

## Указать файл конфигурации

```bash
tsc -p ./tsconfig.prod.json
```

---

# `tsc-cli`

`tsc-cli` — это CLI-интерфейс для работы с TypeScript Compiler.

Однако стандартный пакет TypeScript уже содержит CLI-команду:

```bash
tsc
```

После установки:

```bash
npm install typescript
```

доступна:

```bash
npx tsc
```

---

## Локальное использование

Обычно в проектах используют:

```bash
npx tsc
```

или через npm scripts:

```json
{
    "scripts": {

        "build": "tsc",

        "watch": "tsc -w"

    }
}
```

Запуск:

```bash
npm run build
```

---

# Отличие глобального и локального `tsc`

| Глобальный                      | Локальный                              |
| ------------------------------- | -------------------------------------- |
| Установлен через `npm -g`       | Установлен в проект                    |
| Общая версия для всех проектов  | Версия закреплена                      |
| Может создавать несовместимости | Рекомендуется для командной разработки |

---


# Краткий ответ для собеседования

**Что такое TypeScript?**

> TypeScript — это надстройка над JavaScript со статической типизацией. Он добавляет проверку типов на этапе компиляции, интерфейсы, generics и другие возможности, но после компиляции превращается в обычный JavaScript.

**Преимущества TypeScript:**

> Основные преимущества — раннее обнаружение ошибок, лучший автокомплит, безопасный рефакторинг, улучшенная читаемость и удобство поддержки больших проектов.

**Явная типизация и inference:**

> Явная типизация — разработчик самостоятельно указывает типы. Выведение типов — TypeScript автоматически определяет тип на основе значения.

**Примитивные типы:**

> Основные типы TypeScript: string, number, boolean, null, undefined, bigint, symbol, object, массивы и tuples.

**any и unknown:**

> `any` полностью отключает проверку типов, а `unknown` позволяет хранить любое значение, но требует проверки типа перед использованием. В современном TypeScript предпочтительнее использовать `unknown`, а не `any`.

**`@ts-ignore`:**

> Специальная директива TypeScript, которая отключает проверку типов для следующей строки. Используется редко, например при работе с библиотеками без типов или при миграции проекта.

**Discriminated Union:**

> Это объединение типов с общим полем-идентификатором, которое позволяет TypeScript автоматически определить конкретный вариант типа и безопасно работать с ним.

**Массивы:**

> В TypeScript массивы имеют типизацию через `type[]` или `Array<type>`. Можно создавать массивы примитивов, объектов, union-типов и readonly массивы.

**Type Alias:**

> Type Alias позволяет создать собственное имя для существующего типа через ключевое слово `type`. Используется для объектов, union, функций и сложных типов.

**Типизация функций:**

> В TypeScript можно указывать типы параметров, возвращаемое значение, callback-функции и создавать типы функций через `type` или интерфейсы. Это обеспечивает проверку корректности вызовов функций на этапе компиляции.

**void:**

> `void` — специальный тип TypeScript, который используется для функций без возвращаемого значения. Например, функции логирования или callback-функции.

**Перегрузка функций:**

> Function overload позволяет описать несколько вариантов вызова одной функции с разными параметрами и возвращаемыми типами, сохраняя строгую типизацию.

**Interface:**

> Interface описывает структуру объекта: его свойства, методы и их типы. Используется для контрактов между частями приложения и поддерживает наследование через `extends`.

**Модификаторы `?` и `readonly`:**

> `?` делает свойство необязательным, а `readonly` запрещает изменение свойства после создания объекта.

**Доступ к частям объектного типа:**

> Для работы с отдельными свойствами типов используются `keyof`, индексированный доступ `T[K]` и `typeof`. Они позволяют создавать безопасные универсальные функции и получать типы отдельных полей объектов.

**Интерфейс функционального объекта:**

> Интерфейс функции описывает сигнатуру функции: параметры и возвращаемый тип. Также может описывать функции с дополнительными свойствами.

**Интерфейс словаря:**

> Dictionary Interface использует index signature `[key: string]: type` и описывает объекты с динамическими ключами одного типа.

**Array-Like объект:**

> Это объект с числовыми индексами и свойством `length`, похожий на массив, но без обязательного наличия методов массива.

**enum и const enum:**

> `enum` создает набор именованных констант и существует во время выполнения. `const enum` полностью заменяется значениями во время компиляции и не создает JavaScript-объект.

**Объединение enum:**

> Enum нельзя расширять через наследование, поэтому обычно используют union типов или объединение объектов через spread.

**Кортежи:**

> Tuple — это массив фиксированной длины с определенными типами элементов. Используется, когда важен порядок и тип каждого элемента, например в `useState` или при работе с координатами.

**readonly:**

> `readonly` делает свойства объектов и классов доступными только для чтения после инициализации. Используется для создания неизменяемых данных.

**Наследование интерфейсов:**

> Интерфейсы могут расширять другие интерфейсы через `extends`. Также TypeScript поддерживает declaration merging — объединение интерфейсов с одинаковым именем.

**Полиморфизм подтипов:**

> Это возможность использовать объект одного типа там, где ожидается другой тип, если его структура соответствует ожидаемому типу. TypeScript использует структурную типизацию.

**Класс объекта:**

> Класс — это шаблон для создания объектов, содержащий свойства, методы, конструктор и модификаторы доступа.

**Объединение типов:**

> Union Type позволяет указать несколько возможных типов через оператор `|`. Для безопасной работы с union используются проверки типов и narrowing.

**never:**

> `never` — специальный тип TypeScript, который описывает значения, которые никогда не возникают. Используется для функций, которые выбрасывают ошибки, бесконечных циклов и проверки исчерпывающих вариантов.

**interface vs type:**

> Interface предназначен в основном для описания объектов и поддерживает наследование и объединение деклараций. Type более универсален и позволяет создавать union, intersection и псевдонимы любых типов.

**override:**

> `override` указывает, что метод или свойство класса переопределяет член родительского класса. TypeScript проверяет корректность такого переопределения.

**Accessor:**

> Accessor — это методы `get` и `set`, которые позволяют контролировать чтение и изменение свойств объекта.

**satisfies:**

> `satisfies` проверяет соответствие значения определенному типу, но сохраняет исходный тип выражения. Используется для безопасной проверки конфигурационных объектов и сложных структур данных.

**Небезопасные приведения типов:**

> Это использование `as` или другого способа принудительно указать TypeScript определенный тип без проверки. Они опасны, потому что могут привести к ошибкам во время выполнения.

**Проблемные приведения типов:**

> Это случаи, когда TypeScript не может безопасно преобразовать один тип в другой. Обход через `unknown as Type` отключает проверку и должен использоваться только в крайних случаях.

**Декораторы классов:**

> Декораторы классов — функции, которые получают конструктор класса и могут добавлять или изменять поведение класса.

**Декораторы методов:**

> Декораторы методов позволяют изменять поведение методов, например добавлять логирование, кеширование или проверку доступа.

**Декораторы свойств:**

> Декораторы свойств применяются к полям класса и обычно используются для добавления метаданных или регистрации свойств. Они не имеют доступа к самому значению свойства.

**Агрегация метаинформации:**

> Это сбор дополнительной информации о классах, методах и свойствах во время компиляции или выполнения. В TypeScript часто используется вместе с декораторами и `reflect-metadata`.

**Декораторы статических частей класса:**

> Применяются к статическим свойствам и методам класса. В отличие от обычных декораторов, `target` у них является самим классом, а не его `prototype`.

**`.d.ts` файлы:**

> Это декларационные файлы TypeScript, которые содержат только описания типов без реализации. Используются для типизации JavaScript библиотек и глобальных объектов.

**`declare`:**

> Оператор `declare` сообщает TypeScript о существовании переменной, функции, класса или модуля, реализация которых находится вне текущего файла.

**Расширение `globalThis`:**

> Позволяет добавлять собственные глобальные переменные и расширять стандартные глобальные типы JavaScript через декларации TypeScript.

**Типизация JavaScript-модуля:**

> JavaScript-модули типизируются через декларационные файлы `.d.ts`, где описываются экспортируемые функции, классы и переменные без реализации.

**Разбиение `.d.ts`:**

> Большие файлы деклараций можно разделять на несколько `.d.ts` файлов и объединять через `reference`, `export` или настройку `typeRoots`.

**Генерация `.d.ts`:**

> TypeScript умеет автоматически создавать декларационные файлы при сборке через опцию `declaration: true`. Они используются для публикации библиотек и поддержки типов.

**`tsc`:**

> `tsc` — официальный компилятор TypeScript, который преобразует `.ts` файлы в JavaScript и выполняет проверку типов.

**`tsc-cli`:**

> CLI для TypeScript предоставляет команды компиляции, проверки типов, создания конфигурации и режима наблюдения. В современных проектах обычно используется встроенный CLI из пакета `typescript` через `npx tsc`.
