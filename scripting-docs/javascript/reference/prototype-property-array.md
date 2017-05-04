---
title: "Свойство prototype (Array) | Microsoft Docs"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство prototype (Array)
Возвращает ссылку на прототип класса массива.  
  
## Синтаксис  
  
```  
  
array.prototype  
```  
  
## Заметки  
 Аргумент `array` представляет собой имя массива.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта наследуют поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Array` метод, возвращающий значение наибольшего элемента массива, объявите функцию, добавьте ее в свойство `Array.prototype`, а затем используйте ее.  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] имеют свойство `prototype`, которое доступно только для чтения.  К прототипу можно добавлять свойства и методы, но невозможно присвоить объекту другой прототип.  Однако пользовательским объектам можно присваивать новый прототип.  
  
 В списках методов и свойств для каждого встроенного объекта, содержащихся в данном справочнике по языку, указано, какие члены принадлежат прототипу объекта, а какие нет.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]