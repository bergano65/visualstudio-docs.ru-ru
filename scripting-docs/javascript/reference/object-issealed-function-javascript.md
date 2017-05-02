---
title: "Функция Object.isSealed (JavaScript) | Microsoft Docs"
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
  - "isSealed - функция [JavaScript]"
  - "Object.isSealed [JavaScript]"
  - "свойства [JavaScript], атрибуты блокировки"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Функция Object.isSealed (JavaScript)
Возвращает значение `true`, если существующие атрибуты свойств не могут быть изменены в объекте и новые свойства не могут быть добавлены к объекту.  
  
## Синтаксис  
  
```javascript  
Object.isSealed(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект для проверки.  
  
## Возвращаемое значение  
 Значение `true`, если выполняются оба из следующих условий:  
  
-   Объект является нерасширяемым, т. е. к объекту нельзя добавлять новые свойства.  
  
-   Атрибут `configurable` имеет значение `false` для всех существующих свойств.  
  
 Если объект не имеет свойств, функция возвращает значение `true`, если объект не является расширяемым.  
  
## Исключения  
 Если аргумент `object` не является объектом, вызывается исключение `TypeError`.  
  
## Заметки  
 Если атрибут `configurable` свойства имеет значение `false`, атрибуты свойства невозможно изменить, а свойство не может быть удалено.  Когда атрибут `writable` имеет значение `false`, значение свойства данных изменить нельзя.  Когда `configurable` имеет значение `false`, а `writable` имеет значение `true`, атрибуты `value` и `writable` можно изменить.  
  
 Функция `Object.isSealed` не использует атрибут `writable` свойств для определения возвращаемого значения.  
  
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
|`Object.isSealed`|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## Пример  
 В следующем примере показано использование функции `Object.isSealed`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)