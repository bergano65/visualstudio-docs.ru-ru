---
title: "Объект Reflect (JavaScript) | Microsoft Docs"
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Объект Reflect (JavaScript)
Предоставляет методы для использования в перехватываемых операциях.  
  
## Синтаксис  
  
```  
Reflect.[method]  
```  
  
#### Параметры  
 `method`  
 Обязательный.  Имя одного из методов объекта `Reflect`.  
  
## Заметки  
 Создать экземпляр объекта Reflect с помощью оператора `new` нельзя.  
  
 Методы Reflect часто используются с [прокси\-элементами](../../javascript/reference/proxy-object-javascript.md), которые позволяют делегировать поведение по умолчанию, не включая его в код.  
  
 Объект Reflect предоставляет статический метод с тем же именем, что и у каждого прокси\-исключения.  Описания в таблице не являются исчерпывающими.  
  
|Метод|Описание|  
|-----------|--------------|  
|`Reflect.apply(target, thisArg, args)`|Аналог метода [apply](../../javascript/reference/apply-method-function-javascript.md) объекта Function.|  
|`Reflect.construct(target, args)`|Функция, эквивалентная оператору `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Аналог функции [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Возвращает значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.deleteProperty(target, propertyName)`|Аналог оператора `delete`.  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.enumerate(target)`|Аналог оператора [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) и функций [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) и [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Функция, эквивалентная любому свойству [getter](../../javascript/creating-objects-javascript.md).|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Аналог функции [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.getPrototypeOf(target)`|Аналог функции [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Аналог оператора `in`, метода [Метод hasOwnProperty \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) и других методов.  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.isExtensible(target)`|Аналог функции [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Аналог функции [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Аналог функции [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.set(target, propertyName, value, receiver)`|Аналог применения любого свойства [setter](../../javascript/creating-objects-javascript.md).  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.setPrototypeOf(target, prototype)`|Аналог функции [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).  Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
  
## Пример  
 В следующем примере кода показано, как использовать `Reflect.get` для записи прокси\-элемента, блокирующего операции get для свойств, которые начинаются с символа подчеркивания.  
  
```javascript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]