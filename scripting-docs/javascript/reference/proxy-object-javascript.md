---
title: "Прокси-объект (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Прокси-объект (JavaScript)
Включает пользовательское поведение объекта.  
  
## Синтаксис  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### Параметры  
 `target`  
 Обязательный.  Объект или функция, которую должен виртуализировать прокси\-объект.  
  
 `handler`  
 Обязательный.  Объект с методами \(перехваты\), которые реализуют пользовательское поведение.  
  
## Заметки  
 Объект `Proxy` используется для перехвата внутренних низкоуровневых операций на другом объекте.  Прокси\-объекты можно использовать для перехвата, виртуализации объектов, ведения журнала, профилирования и иных целей.  
  
 Если перехват конкретной операции не был определен в обработчике прокси\-объекта, эта операция будет выполнена целевым объектом.  
  
 Объект\-обработчик определяет следующие методы \(перехваты\) для реализации пользовательского поведения.  Приведенные здесь примеры не являются исчерпывающими.  Для поддержки условного поведения по умолчанию используйте в методе обработчика методы [Объект Reflect](../../javascript/reference/reflect-object-javascript.md).  
  
|Синтаксис метода обработчика \(перехват\)|Примеры использования|  
|-----------------------------------------------|---------------------------|  
|`apply: function(target, thisArg, args)`|Перехват вызова функции.|  
|`construct: function(target, args)`|Перехват конструктора.|  
|`defineProperty: function(target, propertyName, descriptor)`|Перехват [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Перехват оператора `delete`.|  
|`enumerate: function(target)`|Перехват оператора [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), функций [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), функции [Object.keys](../../javascript/reference/object-keys-function-javascript.md) и [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Перехват любых свойств [получения](../../javascript/creating-objects-javascript.md).|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Перехват [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Перехват [Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Перехват оператора `in`, [Метод hasOwnProperty \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) и других методов.|  
|`isExtensible: function(target)`|Перехват [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Перехват [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Перехват [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Перехват любых свойств [задания](../../javascript/creating-objects-javascript.md).|  
|`setPrototypeOf: function(target, prototype)`|Перехват [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## Пример  
 В следующем примере кода показано, как создать прокси\-объект для объекта\-литерала с помощью перехвата `get`.  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## Пример  
 В следующем примере кода показано, как создать прокси\-объект для функции с помощью перехвата `apply`.  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]