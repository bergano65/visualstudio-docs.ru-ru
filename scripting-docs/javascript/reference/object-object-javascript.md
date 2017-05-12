---
title: "Объект Object (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "object"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object - объект"
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Объект Object (JavaScript)
Предоставляет функции, общие для всех объектов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Синтаксис  
  
```  
  
obj  
 = new Object([value])   
```  
  
## Параметры  
 `obj`  
 Обязательный.  Имя переменной, которой присваивается объект `Object`.  
  
 *value*  
 Необязательный.  Любой из примитивных типов данных [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(число, логическое значение или строка\).  Если параметр value является объектом, объект возвращается без изменений.  Если параметр *value* имеет значение `null`, **не определен** или не указан, создается объект без содержимого.  
  
## Заметки  
 Объект `Object` присутствует во всех остальных объектах [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]; все его методы и свойства доступны во всех остальных объектах.  Методы могут заново определяться в пользовательских объектах и вызываются [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в соответствующее время.  Метод **toString** является примером часто переопределяемого метода `Object`.  
  
 В этом справочнике по языку описание каждого метода `Object` включает и информацию по умолчанию, и информацию по реализации отдельных встроенных объектов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Требования  
 `Object Object` появился в [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)].  Некоторые элементы следующих списков были представлены в более поздних версиях.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Object Object`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство \_\_proto\_\_](../../javascript/reference/proto-property-object-javascript.md)|Указывает прототип для объекта.|  
|[Свойство constructor](../../javascript/reference/constructor-property-object-javascript.md)|Указывает функцию, которая создает объект.|  
|[Свойство prototype](../../javascript/reference/prototype-property-object-javascript.md)|Возвращает ссылку на прототип класса объектов.|  
  
## Функции  
 В следующей таблице перечислены функции объекта `Object Object`.  
  
|Функция|Описание|  
|-------------|--------------|  
|[Функция Object.assign](../../javascript/reference/object-assign-function-object-javascript.md)|Копирует значения из одного или нескольких объектов источников в целевой объект.|  
|[Функция Object.create](../../javascript/reference/object-create-function-javascript.md)|Создает объект, который имеет указанный прототип и содержит указанные свойства \(необязательно\).|  
|[Функция Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|Добавляет одно или несколько свойств в объект и изменяет атрибуты существующих свойств.|  
|[Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|Добавляет свойство в объект или изменяет атрибуты существующего свойства.|  
|[Функция Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Предотвращает изменение существующих атрибутов и значений свойств, а также добавление новых свойств.|  
|[Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Возвращает определение свойства данных или свойства метода доступа.|  
|[Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Возвращает имена свойств и методов объекта.|  
|[Функция Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Возвращает символьные свойства объекта.|  
|[Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|Возвращает прототип объекта.|  
|[Функция Object.is](../../javascript/reference/object-is-function-javascript.md)|Возвращает значение, определяющее, совпадают ли два значения.|  
|[Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Возвращает значение, которое указывает, можно ли добавлять в объект новые свойства.|  
|[Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Возвращает значение `true`, если объект не допускает изменение существующих атрибутов и значений свойств, а также добавление новых свойств.|  
|[Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Возвращает значение `true`, если объект не допускает изменение существующих атрибутов свойств, а также добавление новых свойств.|  
|[Функция Object.keys](../../javascript/reference/object-keys-function-javascript.md)|Возвращает имена перечисляемых свойств и методов объекта.|  
|[Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Предотвращает добавление новых свойств к объекту.|  
|[Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Предотвращает изменение атрибутов существующих свойств, а также добавление новых свойств.|  
|[Функция Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)|Задает прототип объекта.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Object Object`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в иерархии прототипов другого объекта.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Возвращает объект, преобразованный в строку на основе текущего языкового стандарта.|  
|[Метод toString](../../javascript/reference/tostring-method-object-javascript.md)|Возвращает строковое представление объекта.|  
|[Метод valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## См. также  
 [Объекты JavaScript](../../javascript/reference/javascript-objects.md)