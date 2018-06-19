---
title: Использование конструкторов для определения типов | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569184"
---
# <a name="using-constructors-to-define-types"></a>Использование конструкторов для определения типов
Конструктор — это функция, создающая экземпляр объекта [Object](../../javascript/objects-and-arrays-javascript.md) определенного типа. Конструктор вызывается с помощью ключевого слова **new**. Ниже приведено несколько примеров конструкторов для встроенных объектов JavaScript и пользовательских объектов.  
  
## <a name="constructor-examples"></a>Примеры конструкторов  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 Конструктор функции содержит ключевое слово **this**, которое представляет собой ссылку на только что созданный пустой объект. Он инициализирует новый объект путем создания свойств и присвоения им начальных значений. После завершения работы конструктор возвращает ссылку на созданный объект.  
  
## <a name="writing-constructors"></a>Написание конструкторов  
 Объекты можно создавать с помощью оператора **new** совместно со стандартными функциями конструктора, такими как **Object()**, **Date()** и **Function()**. Также можно создавать пользовательские функции конструкторов, которые определяют собственные наборы свойств и методов. Ниже приведен пример пользовательского конструктора.  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 При вызове конструктора Circle необходимо указать значения для центральной точки и радиуса круга. В результате создается объект Circle, содержащий три свойства. Ниже показано, как создается экземпляр объекта Circle.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Все объекты, созданные с помощью пользовательского конструктора, имеют тип `object`. В JavaScript имеется только шесть типов: `object`, `function`, `string`, `number`, `boolean` и `undefined`. Дополнительные сведения см. в статье [Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## <a name="see-also"></a>См. также  
 [Использование метода bind](../../javascript/advanced/using-the-bind-method-javascript.md)