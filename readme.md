![alt text](<Без названия.png>)

# Что такое synch / async в JS ?
...
## Синхронный и асинхронный код в JavaScript отличаются тем, как они выполняются.

## Синхронный код в JavaScript выполняется последовательно, то есть каждая инструкция выполняется одна за другой. Это означает, что каждая следующая инструкция должна ждать, пока предыдущая не будет выполнена. Вот пример синхронного кода:
```js
console.log(1)
console.log(2)
console.log(3)

// Output 
// 1
// 2
// 3
```
## В этом примере сообщения будут выведены в том порядке, в котором они написаны, потому что код выполняется синхронно.
...

# Асинхронный код в JavaScript позволяет выполнять операции параллельно без блокировки выполнения остального кода. Это особенно полезно для операций, которые могут занять много времени, таких как чтение файла или запрос к серверу. Вот пример асинхронного кода:
```js
console.log(1);
setTimeout(() => {
  console.log(2);
}, 2000);
console.log(3);

// Output
// 1
// 3
// 2
```

## В этом примере  2 будет выведено через 2 секунды, но выполнение кода не остановится, чтобы дождаться этого. 3 будет выведено сразу после 1, не дожидаясь завершения таймера. Это происходит благодаря асинхронности JavaScript.

![alt text](<Без названия (1).png>)

# Каким образом можно написать асинхронный код в js ?

## 1. Callback : 

```js
function get(callback) {
    setTimeout(function() {
        let name = "Ismail";
        callback(name);
    }, 2000);
}

get(function(name) {
    console.log("Hello, " + name);
});

// Output

// Hello Ismail
```
## В этом примере функция get использует setTimeout для задержки выполнения функции обратного вызова на 2 секунды. После истечения этого времени функция обратного вызова вызывается с аргументом name, и в консоль выводится сообщение “Hello, Ismail”. Это простой пример использования setTimeout для создания асинхронного кода в JavaScript.
...

# 2. Promise :
```js
let promise = new Promise((res, rej) => {
  if (2 + 2 + 2 + 2 + 2 == 100 / 10) {
    return res("its right");
  }
  return rej("its wrong");
});
console.log(
  promise.then((data) => console.log(data).catch((err) => console.error(err)))
);

// Output 

// Its right
```
...

# 3. Async/Await : Async/await (асинхронное ожидание) в JavaScript — это мощный механизм для работы с асинхронным кодом. Давайте рассмотрим его на примерах.

## Async/await позволяет писать асинхронный код более легко и читаемо. Оно предоставляет синтаксический сахар для работы с Promises.

## Чтобы использовать async/await, объявите функцию с ключевым словом async. Затем используйте await перед Promise, чтобы приостановить выполнение функции до получения результата.
```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    // Делайте что-то с полученными данными
  } catch (error) {
    console.error('Ошибка при получении данных:', error);
  }
}
```
## В этом примере функция fetchData асинхронно получает данные с помощью fetch, дожидается ответа и затем обрабатывает полученные данные. Если что-то пошло не так, ошибка будет обработана в блоке catch.

## Async/await упрощает обработку асинхронных операций, делая код более понятным и удобным для разработчиков.
...

# API (Application Programming Interface) — это набор правил и соглашений, которые позволяют разным программам взаимодействовать друг с другом. REST API (Representational State Transfer) — это стиль архитектуры для построения веб-сервисов, основанный на принципах REST.
![alt text](rest_api.svg)

...

# Что такое Fetch ? 

## fetch() — это функция в JavaScript, которая используется для выполнения асинхронных HTTP-запросов. Она возвращает Promise, который разрешается в объект Response, представляющий ответ на запрос. Давайте рассмотрим, как использовать fetch() с async/await.


```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data); // Обработка полученных данных
  } catch (error) {
    console.error('Ошибка при получении данных:', error);
  }
}

fetchData();

```

# Fetch имеет 4 свойства : 

## 1. Get <br> 2. Post <br> 3. Put <br> 4. Delete! 