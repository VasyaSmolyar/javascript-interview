# Javascript Interview

> ### Disclaimer
> Этот репозиторий написан в первую очередь автором для самообразования и подготовку к собеседованиям. Если Вы найдёте какой-то недочёт в ответах, то можете сообщить об этом.

## Оглавление

* [HTML](#HTML)
* [CSS](#CSS)
* [Javascript](#Javascript)

### HTML

- #### Для чего нужен DOCTYPE?
  **DOCTYPE** — это сокращение от **DOCument TYPE** (тип документа). DOCTYPE всегда связан с **DTD** — **Document Type Definition** (определение типа документа).

  DTD определяет как должны быть структурированы документы определенного типа (т.е. тег `button` может содержать в себе тег `span`, но не `div`), в то время как DOCTYPE объявляет, к какому DTD *предположительно* относится документ.

  Для веб-страниц объявление DOCTYPE необходимо. Он используется для того, чтобы сообщить пользовательскому агенту, к какой версии спецификаций HTML принадлежит ваш документ. Как только пользовательский агент распознал правильный DOCTYPE, он запустит режим **no-quirks**, соответствующий этому DOCTYPE, для чтения документа. Если пользовательский агент не распознает правильный DOCTYPE, он активирует режим **quirks**.

  DOCTYPE для стандарта HTML5 определяется как `<!DOCTYPE html>`.

- #### Разные языки
  Когда к серверу делается HTTP-запрос, то браузер пользователя обычно отсылает информацию о предпочитаемом языке в заголовке Accept-Language. Сервер может использовать эту информацию, чтобы вернуть версию документа на подходящем языке, если такая возможность есть. В возвращённом HTML-документе обязательно должен быть указан атрибут lang у тега <html>, к примеру <html lang="en">...</html>.

- #### Для чего нужны data- атрибуты?
  До того, как JavaScript-фреймворки стали популярны, фронтенд-разработчики использовали `data-` атрибуты чтобы хранить дополнительные данные прямо в DOM без хаков вроде нестандартных атрибутов или дополнительных свойств в DOM. Атрибуты этого семейства предназначены для хранения частных данных пользователя, для которых не существует более подходящих атрибутов или элементов на странице или в приложении.

  На сегодняшний день использование data-атрибутов не поощряется. Одной из причин является то, что пользователь может модифицировать данные в атрибуте, используя инспектор кода в браузере. Данные лучше хранить в самом JavaScript и обновлять DOM при помощи связывания данных через библиотеку или фреймворк.
  
- #### Из каких блоков состоит HTML5?
  - Семантика. Позволяет более точно описать из чего состоит контент.
  - Связанность. Позволяет общаться с сервером новыми и инновационными способами.
  - Офлайн и хранилище. Позволяют страницам хранить данные локально на клиентской стороне и более эффективно работать в офлайне.
  - Мультимедиа. Ставит создание видео и аудио на первое место в вебе.
  - 2D/3D-графика и эффекты. Позволяет расширить возможности презентации.
  - Производительность и интеграция. Обеспечивает большую скорость оптимизации и лучшее использование аппаратных средств.
  - Доступ к устройствам. Позволяет взаимодействовать с различными устройствами ввода и вывода.
  - Стилизация. Позволяет создавать более сложные темы оформления.

- #### cookie, sessionStorage и localStorage
  Все вышеупомянутые технологии являются механизмами хранения типа ключ-значение на клиентской стороне. Они могут хранить данные только как строки.

  |  | cookie | localStorage | sessionStorage |
  | --- | --- | --- | --- |
  | Инициатор | Клиент или сервер. Сервер может использовать заголовок Set-Cookie | Клиент | Клиент |
  | Срок хранения | Устанавливается вручную | Всегда | До закрытия вкладки |
  | Хранение между сессиями | Зависит от установки срока хранения | Да | Нет |
  | Отправка на сервер с каждым HTTP-запросом | автоматически, с помощью заголовка Cookie | Нет | Нет |
  | Емкость (на один домен) | 4 КБ | 5 МБ | 5 МБ |
  | Доступность | В любом окне | В любом окне | В той же вкладке |
  |  |  |  |  |

### CSS

  - #### TODO

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
- #### Оператор void
  Оператор `void` исполняет заданное выражение, а затем возвращает `undefined`.

  ```jsx
  const output = void 1;
  console.log(output);
  // Expected output: undefined

  void console.log('expression evaluated');
  // Expected output: "expression evaluated"

  void (function iife() {
    console.log('iife is executed');
  })();
  // Expected output: "iife is executed"

  void function test() {
    console.log('test function executed');
  };

  try {
    test();
  } catch (e) {
    console.log('test function is not defined');
    // Expected output: "test function is not defined"
  }
  ```
- #### IIFE - немедленно вызываемое функциональное выражение
  **Объясните, почему это не является IIFE: `function foo(){ }();`**

  IIFE расшифровывается как Immediately Invoked Function Expression - немедленно вызываемое функциональное выражение. Синтаксический анализатор JavaScript читает `function foo(){ } ();` как `function foo(){ }` и `();`, где первое выражение - это *объявление функции*, а второе (пара скобок) - попытка вызова функции, но так как имя не указано, он выдает ошибку `Uncaught SyntaxError: Unexpected token`.

  Вот два способа исправить это, которые заключаются добавление дополнительных скобок: `(function foo(){ })()` и `(function foo(){ }())`. Выражения, начинающиеся с `function`, считаются *объявлениями функций*. Оборачивая эту функцию внутри `()`, она становится *функциональным выражением*, которое затем может быть выполнено с последующим `()`. Подобные функции не отображаются в глобальной области видимости, и вы можете даже не указывать им имя, если вы не будете на них ссылаться.

  Вы также можете использовать оператор `void` - `void function foo(){ }()`. К сожалению, с таким подходом есть одна проблема. Выполнение данного выражения всегда возвращает `undefined`, поэтому, если ваше IIFE возвращает что-либо, вы не можете его использовать. Пример:

  ```jsx
  const foo = void (function bar() {
    return 'foo';
  })();
  console.log(foo); // undefined
  ```
- #### Что такое замыкание и как/для чего его используют?
  Замыкание - это комбинация функции и лексического окружения, в которой эта функция была объявлена. Слово "лексический" относится к тому факту, что лексическая область видимости использует место, где переменная объявлена в исходном коде, чтобы определить, где эта переменная доступна. Замыкания - это функции, которые имеют доступ к переменным внешней (замыкающей) функции - цепочке областей видимости даже после того, как внешняя функция вернулась.
- #### Каррирование

- #### Как работает прототипное наследование
  Все объекты в JavaScript имеют свойство `__proto__`,  которое является ссылкой на другой объект. Когда происходит обращение к свойству объекта, и если свойство не найдено в этом объекте, то механизм JavaScript просматривает прототип объекта, затем прототип прототипа и т.д. До тех пор, пока не найдет определенное свойство на одном из прототипов или до тех пор, пока он не достигнет конца цепочки прототипов. Такое поведение имитирует классическое наследование, но на самом деле это скорее [делегирование, чем наследование](https://davidwalsh.name/javascript-objects).

  ОО-подобный механизм свойств объектов в JavaScript обозначается [[Прототип]], который является внутренней характеристикой любого объекта, называемой его прототип-цепочкой - специальной ссылкой на другой объект. Это что-то вроде механизма области видимости, поскольку связь [[Prototype]] описывает, на какой альтернативный объект следует ссылаться, если вы запрашиваете свойство или метод вашего объекта, которого не существует.

  **Другими словами, вы указываете объект для делегирования поведения, если это поведение не определено для данного объекта.**

  ```jsx
  let animal = {
    eats: true,
    walk() {
      alert("Animal walk");
    }
  };

  let rabbit = {
    jumps: true,
    __proto__: animal
  };

  let longEar = {
    earLength: 10,
    __proto__: rabbit
  };

  // walk взят из цепочки прототипов
  longEar.walk(); // Animal walk
  alert(longEar.jumps); // true (из rabbit)
  ```

  Свойство `__proto__` — исторически обусловленный геттер/сеттер для `[[Prototype]]`

  Это распространённая ошибка начинающих разработчиков – не знать разницы между этими двумя понятиями.

  Обратите внимание, что `__proto__` — *не то же самое*, что внутреннее свойство `[[Prototype]]`. Это геттер/сеттер для `[[Prototype]]`.

  Свойство `__proto__` немного устарело, оно существует по 
  историческим причинам. Современный JavaScript предполагает, что мы 
  должны использовать функции `Object.getPrototypeOf/Object.setPrototypeOf` вместо того, чтобы получать/устанавливать прототип. 

  По спецификации `__proto__` должен поддерживаться только 
  браузерами, но по факту все среды, включая серверную, поддерживают его. 

  https://learn.javascript.ru/prototype-inheritance
- #### Как работает this
  Говоря максимально простым языком, значение `this` зависит от того, как вызывается функция.

  ## Случаи

  Если ключевое слово `new` используется при вызове функции, `this` внутри функции является совершенно новым объектом.

  ```jsx
  function ConstructorExample() {
      console.log(this);
      this.value = 10;
      console.log(this);
  }
  new ConstructorExample();
  // -> {}
  // -> { value: 10 }
  ```

  Если для вызова/создания функции используются `apply`, `call` или `bind`, то `this` внутри функции - это объект, который передается в качестве аргумента.

  ```jsx
  function fn() {
      console.log(this);
  }
  var obj = {
      value: 5
  };
  var boundFn = fn.bind(obj);
  boundFn();     // -> { value: 5 }
  fn.call(obj);  // -> { value: 5 }
  fn.apply(obj); // -> { value: 5 }
  ```

  Если функция вызывается как метод, например, `obj.method()`, то `this` - это объект, к которому принадлежит функция.

  ```jsx
  var obj = {
      value: 5,
      printThis: function() {
          console.log(this);
      }
  };
  obj.printThis(); // -> { value: 5, printThis: ƒ }
  ```

  Если функция вызывается без контекста, то есть она вызывается без условий, описанных в пунктах выше, то `this` является глобальным объектом. В браузере это объект `window`. В строгом режиме (`'use strict'`), `this` будет `undefined` вместо глобального объекта.

  ```jsx
  function fn() {
      console.log(this);
  }
  // If called in browser:
  fn(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
  ```

  Заметьте, что это правило аналогично правилу 3 - разница в том, что функция, не объявленная как метод, автоматически становится свойством глобального объекта window. Таким образом, это неявное обращение к методу. Когда мы вызываем `fn(),` это интерпретируется как `window.fn()`, так что это window.
  `console.log(fn === window.fn); // -> true`

  Если применяются несколько из вышеперечисленных правил, то правило, которое выше выигрывает и устанавливает значение `this`.

  Если функция является стрелочной функцией, то она игнорирует все вышеописанные правила и получает значение `this` из лексического окружения во время ее создания.

  ```jsx
  const obj = {
      value: 'abc',
      createArrowFn: function() {
          return () => console.log(this);
      }
  };
  const arrowFn = obj.createArrowFn();
  arrowFn(); // -> { value: 'abc', createArrowFn: ƒ }
  ```

  Библиотеки иногда намеренно привязывают значение this внутри своих функций. this привязывается к наиболее полезному значению для использования в функции. jQuery, например, привязывает this к элементу DOM, вызывающему событие, в обратном вызове этого события. Если библиотека имеет неожиданное значение this, которое не соответствует правилам, проверьте ее документацию. Скорее всего, оно привязывается с помощью bind.
- #### Делегирование событий

  Делегирование событий - это приём, заключающийся в добавлении 
  обработчиков событий к родительскому элементу, а не к дочерним 
  элементам. Обработчик будет срабатывать всякий раз, когда событие будет 
  запущено на дочерних элементах благодаря всплытию событий в DOM. 
  Преимущества этого приёма:

  - Экономит объем используемой памяти, т.к. для родительского элемента требуется только один обработчик.
  - Не нужно привязывать или убирать обработчики при добавлении и удалении элементов.


  ```html
  <ul id="parent-list">
    <li id="post-1">Item 1</li>
    <li id="post-2">Item 2</li>
    <li id="post-3">Item 3</li>
    <li id="post-4">Item 4</li>
    <li id="post-5">Item 5</li>
    <li id="post-6">Item 6</li>
  </ul>
  ```

  ```jsx
  // Get the element, add a click listener...
  document.getElementById("parent-list").addEventListener("click", function(e) {
    // e.target is the clicked element!
    // If it was a list item
    if(e.target && e.target.nodeName == "LI") {
      // List item found!  Output the ID!
      console.log("List item ", e.target.id.replace("post-", ""), " was clicked!");
    }
  });
  ```
- #### Function.length
  Свойство **`length`** определяет количество аргументов, ожидаемых функцией.

  ```jsx
  console.log(Function.length); /* 1 */

  console.log(function () {}.length); /* 0 */
  console.log(function (a) {}.length); /* 1 */
  console.log(function (a, b) {}.length); /* 2 и так далее */
  console.log(
    function (...args) {}.length,
  ); /* 0, остаточные параметры не считаются */
  ```
