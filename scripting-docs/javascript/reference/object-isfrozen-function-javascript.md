---
title: "Функция Object.isFrozen (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "isFrozen - функция [JavaScript]"
  - "Object.isFrozen - функция [JavaScript]"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Функция Object.isFrozen (JavaScript)
Возвращает значение `true`, если существующие атрибуты и значения свойств не могут быть изменены в объекте и новые свойства не могут быть добавлены к объекту.  
  
## Синтаксис  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект для проверки.  
  
## Возвращаемое значение  
 Значение `true`, если выполняются все следующие условия:  
  
-   Объект является нерасширяемым, т. е. к объекту нельзя добавлять новые свойства.  
  
-   Атрибут `configurable` имеет значение `false` для всех существующих свойств.  
  
-   Атрибут `writable` имеет значение `false` для всех существующих свойств данных.  
  
 Если объект не имеет свойств, функция возвращает значение `true`, если объект не является расширяемым.  
  
## Исключения  
 Если аргумент `object` не является объектом, вызывается исключение `TypeError`.  
  
## Заметки  
 Если атрибут `configurable` свойства имеет значение `false`, атрибуты свойства невозможно изменить, а свойство не может быть удалено.  Когда атрибут `writable` имеет значение `false`, значение свойства данных изменить нельзя.  Когда `configurable` имеет значение `false`, а `writable` имеет значение `true`, атрибуты `value` и `writable` можно изменить.  
  
 Дополнительные сведения о задании атрибутов свойств см. в разделе [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Чтобы получить атрибуты свойства, можно использовать функцию [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Связанные функции  
 Следующие связанные функции предотвращают изменение атрибутов объекта.  
  
|Функция|Объект становится нерасширяемым.|`configurable` получает значение `false` для каждого свойства|`writable` получает значение `false` для каждого свойства|  
|-------------|--------------------------------------|-------------------------------------------------------------------|---------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true`, если все условия, отмеченные в следующей таблице, имеют значение true.  
  
|Функция|Расширяем ли объект?|`configurable` имеет значение `false` для всех свойств?|`writable` имеет значение `false` для всех свойств данных?|  
|-------------|--------------------------|-------------------------------------------------------------|----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Нет|  
|`Object.isFrozen`|Нет|Да|Да|  
  
## Пример  
 В следующем примере показано использование функции `Object.isFrozen`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)