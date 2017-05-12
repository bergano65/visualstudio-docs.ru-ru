---
title: "Функция Object.preventExtensions (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions - функция [JavaScript]"
  - "preventExtensions - функция [JavaScript]"
  - "запрет новых свойств [JavaScript]"
  - "свойства [JavaScript], запрет новых"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Функция Object.preventExtensions (JavaScript)
Предотвращает добавление новых свойств к объекту.  
  
## Синтаксис  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект, который требуется сделать нерасширяемым.  
  
## Возвращаемое значение  
 Объект, переданный функции.  
  
## Исключения  
 Если аргумент `object` не является объектом, вызывается исключение `TypeError`.  
  
## Заметки  
 Функция `Object.preventExtensions` делает объект нерасширяемым, чтобы к нему невозможно было добавить новые именованные свойства.  После того как объект сделан нерасширяемым, его нельзя сделать расширяемым.  
  
 Дополнительные сведения о задании атрибутов свойств см. в разделе [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Связанные функции  
 Следующие связанные функции предотвращают изменение атрибутов объекта.  
  
|Функция|Объект становится нерасширяемым.|`configurable` получает значение `false` для каждого свойства|`writable` получает значение `false` для каждого свойства|  
|-------------|--------------------------------------|-------------------------------------------------------------------|---------------------------------------------------------------|  
|`Object.preventExtensions`|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true`, если все условия, отмеченные в следующей таблице, имеют значение true.  
  
|Функция|Расширяем ли объект?|`configurable` имеет значение `false` для всех свойств?|`writable` имеет значение `false` для всех свойств данных?|  
|-------------|--------------------------|-------------------------------------------------------------|----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## Пример  
 В следующем примере показано использование функции `Object.preventExtensions`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)