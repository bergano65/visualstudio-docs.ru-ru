---
title: "Функция Object.freeze (JavaScript) | Microsoft Docs"
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
  - "freeze - функция"
  - "Object.freeze - функция"
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Функция Object.freeze (JavaScript)
Предотвращает изменение существующих атрибутов и значений свойств и исключает добавление новых свойств.  
  
## Синтаксис  
  
```javascript  
Object.freeze(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект, атрибуты которого требуется заблокировать.  
  
## Возвращаемое значение  
 Объект, переданный функции.  
  
## Исключения  
 Если аргумент `object` не является объектом, вызывается исключение `TypeError`.  
  
## Заметки  
 Функция `Object.freeze` выполняет следующие действия.  
  
-   Делает объект нерасширяемым, чтобы к нему невозможно было добавить новые свойства.  
  
-   Устанавливает для атрибута `configurable` значение `false` для всех свойств объекта.  Если атрибут `configurable` имеет значение `false`, атрибуты свойства невозможно изменить, а свойство не может быть удалено.  
  
-   Устанавливает для атрибута `writable` значение `false` для всех свойств данных объекта.  Когда атрибут `writable` имеет значение false, значение свойства данных изменить нельзя.  
  
 Дополнительные сведения о задании атрибутов свойств см. в разделе [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Чтобы получить атрибуты свойства, можно использовать функцию [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Связанные функции  
 Следующие связанные функции предотвращают изменение атрибутов объекта.  
  
|Функция|Объект становится нерасширяемым.|`configurable` получает значение `false` для каждого свойства|`writable` получает значение `false` для каждого свойства|  
|-------------|--------------------------------------|-------------------------------------------------------------------|---------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|`Object.freeze`|Да|Да|Да|  
  
 Следующие функции возвращают `true`, если все условия, отмеченные в следующей таблице, имеют значение true.  
  
|Функция|Расширяем ли объект?|`configurable` имеет значение `false` для всех свойств?|`writable` имеет значение `false` для всех свойств данных?|  
|-------------|--------------------------|-------------------------------------------------------------|----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Да|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## Пример  
 В следующем примере показано использование функции `Object.freeze`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)