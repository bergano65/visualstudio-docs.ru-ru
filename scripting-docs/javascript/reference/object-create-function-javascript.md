---
title: "Функция Object.create (JavaScript) | Microsoft Docs"
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
  - "create - функция [JavaScript]"
  - "Object.create - функция [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Функция Object.create (JavaScript)
Создает объект, который имеет указанный прототип и \(необязательно\) содержит указанные свойства.  
  
## Синтаксис  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### Параметры  
 `prototype`  
 Обязательное.  Объект для использования в качестве прототипа.  Может принимать значение `null`.  
  
 `descriptors`  
 Необязательный параметр.  Объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], содержащий один или несколько дескрипторов свойств.  
  
 *Свойство данных* — это свойство, которое может получать и задавать значение.  Дескриптор свойства данных содержит атрибут `value`, а также атрибуты `writable`, `enumerable` и `configurable`.  Если последние 3 атрибута не заданы, по умолчанию они получают значение `false`.  *Свойство метода доступа* вызывает предоставленную пользователем функцию при каждом получении или задании значения.  Дескриптор свойства метода доступа содержит атрибут `set`, атрибут `get` или оба эти атрибута.  Для получения дополнительной информации см. [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Возвращаемое значение  
 Новый объект с указанным внутренним прототипом, содержащий указанные свойства, если они были предоставлены.  
  
## Исключения  
 Исключение `TypeError` создается при выполнении любого из следующих условий:  
  
-   Аргумент `prototype` не является объектом и не имеет значение `null`.  
  
-   Дескриптор в аргументе `descriptors` имеет атрибут `value` или `writable` и атрибут `get` или `set`.  
  
-   Дескриптор в аргументе `descriptors` имеет атрибут `get` или `set`, который не является функцией.  
  
## Заметки  
 Эту функцию можно использовать с параметром `null` `prototype`, чтобы прекратить использование цепи прототипов.  Созданный объект не будет иметь прототипа.  
  
## Пример  
 В следующем примере создается объект с использованием прототипа `null` и добавлением двух перечислимых свойств.  
  
```javascript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## Пример  
 В следующем примере создается объект, имеющий тот же внутренний прототип, что и объект Object.  Как видно, он имеет тот же прототип, что и объект, созданный с использованием литерала объекта.  Функция [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) получает прототип исходного объекта.  Чтобы получить дескриптор свойства объекта, можно использовать функцию [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```javascript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## Пример  
 В следующем примере создается объект, имеющий тот же внутренний прототип, что и объект Shape.  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Метод isPrototypeOf \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Создание объектов](../../javascript/creating-objects-javascript.md)