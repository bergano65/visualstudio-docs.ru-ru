---
title: "Функция Object.assign (Object) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция Object.assign (Object) (JavaScript)
Копирует значения из одного или нескольких исходных объектов в целевой объект.  
  
## Синтаксис  
  
```  
Object.assign(target, ...sources );  
```  
  
#### Параметры  
 `target`  
 Обязательный.  Объект, в который копируются перечисляемые свойства.  
  
 `...sources`  
 Обязательный.  Один или несколько объектов, из которых копируются перечислимые свойства.  
  
## Исключения  
 Эта функция выдает `TypeError`, если возникает ошибка назначения, которая завершает операцию копирования.  `TypeError` выдается, если целевое свойство недоступно для записи.  
  
## Заметки  
 Эта функция возвращает целевой объект.  Из исходной объекта в целевой копируются только *перечислимые собственные* свойства.  Эту функцию можно использовать для объединения и клонирования объектов.  
  
 Источники `null` или `undefined` обрабатываются как пустые объекты и ничего не добавляют целевому объекту.  
  
## Пример  
 В следующем примере кода показано, как объединить объект с помощью функции `Object.assign`.  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## Пример  
 В следующем примере кода показано, как клонировать объект с помощью функции `Object.assign`.  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]