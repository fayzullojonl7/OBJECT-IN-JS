# OBJECT-IN-JS
---

## 🧠 Что такое объект в JS?
**Объект (object)** — это **набор свойств**, где **каждое свойство имеет ключ (имя)** и **значение**. Ключ всегда строка (или символ), значение — вообще что угодно: число, строка, массив, функция, другой объект, даже жизнь… ну, почти 😄

---

## 📦 Создание объектов

### 1. Через литерал объекта:
```js
const user = {
  name: "Alice",
  age: 25,
  isAdmin: false
};
```

### 2. Через `new Object()`:
```js
const user = new Object();
user.name = "Alice";
```

### 3. С помощью функции-конструктора:
```js
function User(name, age) {
  this.name = name;
  this.age = age;
}
const user1 = new User("Bob", 30);
```

### 4. Через `class` (синтаксический сахар):
```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
const user2 = new User("Eve", 22);
```

---

## 🛠 Работа со свойствами

### Чтение:
```js
console.log(user.name);
console.log(user["age"]);
```

### Добавление:
```js
user.city = "Dushanbe";
```

### Удаление:
```js
delete user.age;
```

### Проверка наличия свойства:
```js
console.log("name" in user); // true
```

---

## 🔁 Перебор свойств

```js
for (let key in user) {
  console.log(key, user[key]);
}
```

---

## ⚡ Методы объекта

```js
const car = {
  brand: "Toyota",
  start() {
    console.log("Vroom! Car started.");
  }
};

car.start();
```

---

## 🎯 `this` в объекте

```js
const person = {
  name: "John",
  greet() {
    console.log(`Hi, I'm ${this.name}`);
  }
};
person.greet(); // Hi, I'm John
```

> ⚠️ `this` зависит от контекста вызова! Если потерять контекст, `this` может стать undefined или window/global.

---

## 🧩 Вложенные объекты

```js
const user = {
  name: "Sam",
  contact: {
    email: "sam@example.com",
    phone: "123-456"
  }
};
console.log(user.contact.email);
```

---

## 📋 Object methods (стандартные штуки)

| Метод | Что делает |
|-------|-------------|
| `Object.keys(obj)` | массив ключей |
| `Object.values(obj)` | массив значений |
| `Object.entries(obj)` | массив пар `[ключ, значение]` |
| `Object.assign(target, source)` | копирует свойства |
| `Object.freeze(obj)` | замораживает объект (нельзя менять) |
| `Object.seal(obj)` | нельзя добавлять/удалять свойства, но можно менять значения |
| `Object.hasOwnProperty(key)` | проверка, что ключ — свой собственный, а не унаследованный |

---

## 🧠 Прототипы и наследование (чуть посложнее, но важно)

JS-объекты могут наследовать свойства и методы через **прототипную цепочку**.

```js
const animal = {
  eats: true
};

const dog = Object.create(animal);
dog.barks = true;

console.log(dog.eats); // true (наследовано от animal)
```

---

## 🧨 Деструктуризация

```js
const user = { name: "Ann", age: 28 };
const { name, age } = user;
console.log(name); // Ann
```

---

## 🌐 JSON — объект в формате текста
```js
const json = JSON.stringify(user); // Объект → строка
const obj = JSON.parse(json);     // Строка → объект
```

---

## 💪 Хитрости и фишки

- Объекты передаются **по ссылке**, а не по значению.
- Уникальные ключи можно задавать через **Symbol**.
- Можно делать **динамические ключи**:
  ```js
  const key = "score";
  const player = {
    [key]: 100
  };
  ```

---

## 🌟 Заключение
Объекты — **мозг JavaScript**. Почти всё в JS — объект: массивы, функции, даже ты, когда программируешь ночью — объект с методом `drinkCoffee()` 😂
