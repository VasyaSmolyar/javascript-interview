# javascript-interview

> ### Disclaimer
> Этот репозиторий написан в первую очередь автором для самообразования и подготовку к собеседованиям. Если Вы найдёте какой-то недочёт в ответах, то можете сообщить об этом.

## Оглавление

* [Javascript](#kotlin)

### Javascript

- #### Типы данных
  Стандарт ECMAScript определяет 8 типов:

  - 6 типов данных являющихся примитивами:
      - [Undefined](https://developer.mozilla.org/ru/docs/Glossary/Undefined) (Неопределённый тип) : `typeof instance === "undefined"`
      - [Boolean](https://developer.mozilla.org/ru/docs/Glossary/Boolean) (Булев, Логический тип) : `typeof instance === "boolean"`
      - [Number](https://developer.mozilla.org/ru/docs/Glossary/Number) (Число) : `typeof instance === "number"`
      - [String](https://developer.mozilla.org/ru/docs/Glossary/String) (Строка) : `typeof instance === "string"`
      - [BigInt](https://developer.mozilla.org/ru/docs/Glossary/BigInt) : `typeof instance === "bigint"`
      - [Symbol (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Symbol) (в ECMAScript 6) : `typeof instance === "symbol"`
  - [Null](https://developer.mozilla.org/ru/docs/Glossary/Null) (Null тип ) : `typeof instance === "object"`. Специальный примитив, используемый не только для данных но и в качестве указателя на финальную точку в [Цепочке Прототипов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Inheritance_and_the_prototype_chain);
  - [Object](https://developer.mozilla.org/ru/docs/Glossary/Object) (Объект) : `typeof instance === "object"`. Простая структура, используемая не только для хранения данных, но и для создания других структур, где любая структура создаётся с использованием ключевого слова `[new](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/new)`: new [Object](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object), new [Array](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array), new [Map (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map), new [Set](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Set), new [WeakMap](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/WeakMap), new [WeakSet](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/WeakSet), new [Date](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Date) и множество других структур;

  И здесь нам необходимо сделать предостережение относительно использования оператора `typeof` для определения типа структур, т.к. все структуры будут возвращать `"object"` при его использовании, так как назначение `typeof` — проверка типа данных, но не структур. Если проверить тип структуры всё же необходимо, то в этом случае желательно использовать оператор [instanceof](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/instanceof), так как именно он отвечает на вопрос о том, какой конструктор был использован для создания структуры.

  Стоит отметить два особых случая работы оператора `typeof`: возврат `"object"` для значения `null` и `"function"` для функций: первое принято считать ошибкой языка, сохраненной ради обратной совместимости, второе является условностью, удобной для проверки на принадлежность значения категории функций, где функция - это особый, "вызываемый", объект.

- #### 3начение примитивного типа
  **Примитив** (значение примитивного типа, примитивный тип данных) это данные, которые не являются [объектом](https://developer.mozilla.org/ru/docs/Glossary/Object) и не имеют [методов](https://developer.mozilla.org/ru/docs/Glossary/Method). В [JavaScript](https://developer.mozilla.org/ru/docs/Glossary/JavaScript) 7 простых типов данных: [string](https://developer.mozilla.org/ru/docs/Glossary/String), [number](https://developer.mozilla.org/ru/docs/Glossary/Number), [boolean](https://developer.mozilla.org/ru/docs/Glossary/Boolean), [null](https://developer.mozilla.org/ru/docs/Glossary/Null), [undefined](https://developer.mozilla.org/ru/docs/Glossary/Undefined), [symbol (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Symbol) (новое в [ECMAScript](https://developer.mozilla.org/ru/docs/Glossary/ECMAScript) 2015), [bigint](https://developer.mozilla.org/ru/docs/Glossary/BigInt).

  Все **примитивы** неизменяемы (immutable), то есть они не могут быть изменены. Важно не путать сам примитив с переменной, которой присвоено значение примитивного типа. Переменной может быть переприсвоено новое значение, но существующее значение примитивного типа не может быть изменено подобно объектам, массивам и функциям.

  За исключением `null` и `undefined`, все примитивные значения имеют объектный аналог, который оборачивает значение примитивного типа:

  - `[String](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String)` для string примитива.
  - `[Number](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Number)` для number примитива.
  - `[BigInt](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/BigInt)` для bigint примитива.
  - `[Boolean](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Boolean)` для boolean примитива.
  - `[Symbol](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Symbol)` для symbol примитива.

  Метод `[valueOf()](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf)` типа обёртки возвращает значение примитивного типа.

- #### null, undefined и не объявленные переменные
  **Необъявленные** переменные создаются, когда вы присваиваете значение идентификатору, который не был ранее создан при помощи `var`,`let` или `const`. Необъявленные переменные будут определены глобально, вне текущей области видимости. В строгом режиме, будет ошибка `ReferenceError`, когда вы попытаетесь назначить значение необъявленной переменной. Необъявленные переменные плохи так же, как и глобальные переменные. Избегайте их любой ценой! Чтобы проверить на их наличие, оберните код в блок `try`/`catch`.

  ```jsx
  function foo() {
    x = 1; *// ReferenceError в строгом режиме*
  }

  **foo();
  console.log(x);
  *// 1*
  ```

  Переменная `undefined` - это переменная, которая была объявлена, но ей не было присвоено значение. Ее тип `undefined`. Если переменной присвоить функцию, которая не возвращает никакого значения, то переменная также будет иметь значение `undefined`. Чтобы проверить это, сравните, используя оператор строгого равенства (`===`) или `typeof`, который вернет строку `'undefined'`. Обратите внимание, что вам не следует использовать оператор абстрактного сравнения для проверки, так как он также вернет `true`, если значение равно `null`.

  ```jsx
  var foo;
  console.log(foo); // undefined
  console.log(foo === undefined); // true
  console.log(typeof foo === 'undefined'); // true

  console.log(foo == null); // true. Неправильно, не используйте это для проверки!

  function bar() {}
  var baz = bar();
  console.log(baz); // undefined
  ```

  Переменной со значением `null` было явно присвоено значение `null`. Она отличается от `undefined` тем, что она была назначена явно. Чтобы проверить на `null`, просто сравните, используя оператор строгого равенства. Обратите внимание, что, как и выше, вы не должны использовать оператор абстрактного равенства (`==`) для проверки, так как он также вернет `true`, если значение равно `undefined`.

  ```jsx
  var foo = null;
  console.log(foo === null); // true
  console.log(typeof foo === 'object'); // true

  console.log(foo == undefined); 
  // true. Неправильно, не используйте это для проверки!
  ```
