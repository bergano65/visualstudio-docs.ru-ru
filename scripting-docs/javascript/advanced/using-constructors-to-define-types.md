---
title: "Использование конструкторов для определения типов | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "функции конструирования"
  - "конструкторы, создание"
  - "создание объектов, функции конструирования"
  - "функции, функции конструирования"
  - "объекты, создание [JavaScript]"
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Использование конструкторов для определения типов
Конструктор — это функция, создающая экземпляр объекта [Object](../../javascript/objects-and-arrays-javascript.md) определенного типа.  Конструктор вызывается с помощью ключевого слова **new**.  Ниже приведено несколько примеров конструкторов для встроенных объектов JavaScript и пользовательских объектов.  
  
## Примеры конструкторов  
  
```javascript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 Конструктор функции содержит ключевое слово **this**, которое представляет собой ссылку на только что созданный пустой объект.  Он инициализирует новый объект путем создания свойств и присвоения им начальных значений.  После завершения работы конструктор возвращает ссылку на созданный объект.  
  
## Написание конструкторов  
 Объекты можно создавать с помощью оператора **new** совместно со стандартными функциями конструктора, такими как **Object\(\)**, **Date\(\)** и **Function\(\)**.  Также можно создавать пользовательские функции конструкторов, которые определяют собственные наборы свойств и методов.  Ниже приведен пример пользовательского конструктора.  
  
```javascript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 При вызове конструктора Circle необходимо указать значения для центральной точки и радиуса круга.  В результате создается объект Circle, содержащий три свойства.  Ниже показано, как создается экземпляр объекта Circle.  
  
```javascript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Все объекты, созданные с помощью пользовательского конструктора, имеют тип `object`.  В JavaScript имеется только шесть типов: `object`, `function`, `string`, `number`, `boolean` и `undefined`.  Дополнительные сведения см. в разделе [Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## См. также  
 [Использование метода bind](../../javascript/advanced/using-the-bind-method-javascript.md)