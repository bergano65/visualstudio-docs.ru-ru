---
title: "Функция Object.seal (JavaScript) | Microsoft Docs"
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
  - "Object.seal - функция"
  - "seal - функция"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция Object.seal (JavaScript)
Предотвращает изменение атрибутов существующих свойств и исключает добавление новых свойств.  
  
## Синтаксис  
  
```javascript  
Object.seal(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект, атрибуты которого требуется заблокировать.  
  
## Возвращаемое значение  
 Объект, переданный функции.  
  
## Исключения  
 Если аргумент `object` не является объектом, вызывается исключение `TypeError`.  
  
## Заметки  
 Функция `Object.seal` выполняет оба из следующих действий:  
  
-   Делает объект нерасширяемым, чтобы к нему невозможно было добавить новые свойства.  
  
-   Устанавливает для атрибута `configurable` значение `false` для всех свойств объекта.  
  
 Если атрибут `configurable` имеет значение `false`, атрибуты свойства невозможно изменить, а свойство не может быть удалено.  Когда `configurable` имеет значение `false`, а `writable` имеет значение `true`, атрибуты `value` и `writable` можно изменить.  
  
 Функция `Object.seal` не изменяет атрибут `writable`.  
  
 Дополнительные сведения о задании атрибутов свойств см. в разделе [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Чтобы получить атрибуты свойства, можно использовать функцию [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Связанные функции  
 Следующие связанные функции предотвращают изменение атрибутов объекта.  
  
|Функция|Объект становится нерасширяемым.|`configurable` получает значение `false` для каждого свойства|`writable` получает значение `false` для каждого свойства|  
|-------------|--------------------------------------|-------------------------------------------------------------------|---------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|`Object.seal`|Да|Да|Нет|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true`, если все условия, отмеченные в следующей таблице, имеют значение true.  
  
|Функция|Расширяем ли объект?|`configurable` имеет значение `false` для всех свойств?|`writable` имеет значение `false` для всех свойств данных?|  
|-------------|--------------------------|-------------------------------------------------------------|----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## Пример  
 В следующем примере показано использование функции `Object.seal`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Функция Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)