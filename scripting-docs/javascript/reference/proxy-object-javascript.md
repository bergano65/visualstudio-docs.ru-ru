---
title: "Прокси-объект (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 489d329528e88c27df03ca0e6d6d1608a39446e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="proxy-object-javascript"></a>Прокси-объект (JavaScript)
Включает пользовательское поведение объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Параметры  
 `target`  
 Обязательный. Объект или функция, которую должен виртуализировать прокси-объект.  
  
 `handler`  
 Обязательный. Объект с методами (перехваты), которые реализуют пользовательское поведение.  
  
## <a name="remarks"></a>Примечания  
 Объект `Proxy` используется для перехвата внутренних низкоуровневых операций на другом объекте. Прокси-объекты можно использовать для перехвата, виртуализации объектов, ведения журнала, профилирования и иных целей.  
  
 Если перехват конкретной операции не был определен в обработчике прокси-объекта, эта операция будет выполнена целевым объектом.  
  
 Объект-обработчик определяет следующие методы (перехваты) для реализации пользовательского поведения. Приведенные здесь примеры не являются исчерпывающими. Для поддержки условного поведения по умолчанию в методе обработчика, используйте методы [отражают объекта](../../javascript/reference/reflect-object-javascript.md).  
  
|Синтаксис метода обработчика (перехват) |Примеры использования|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Перехват вызова функции.|  
|`construct: function(target, args)`|Перехват конструктора.|  
|`defineProperty: function(target, propertyName, descriptor)`|Перехват [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Перехват оператора `delete`.|  
|`enumerate: function(target)`|Перехват [for... в](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) инструкции [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) функции, и [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Перехват любых [считывания](../../javascript/creating-objects-javascript.md) свойства.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Перехват [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Перехват [функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Перехват `in` оператор, [метод hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md), а также другие методы.|  
|`isExtensible: function(target)`|Перехват [функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Перехват [функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Перехват [функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Перехват любых [setter](../../javascript/creating-objects-javascript.md) свойства.|  
|`setPrototypeOf: function(target, prototype)`|Перехват [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как создать прокси-объект для объекта-литерала с помощью перехвата `get`.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как создать прокси-объект для функции с помощью перехвата `apply`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]