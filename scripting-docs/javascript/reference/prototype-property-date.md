---
title: "Свойство prototype (Date) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (Date)
Возвращает ссылку на прототип даты.  
  
## Синтаксис  
  
```  
  
date.prototype  
```  
  
## Заметки  
 Аргумент `date` представляет собой имя объекта.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей объекта Date.  Новые экземпляры объекта наследуют поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Date` метод, возвращающий значение наибольшего элемента массива, объявите функцию, добавьте ее в свойство `Date.prototype`, а затем используйте ее.  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] имеют свойство `prototype`, которое доступно только для чтения.  К прототипу можно добавлять свойства и методы, но невозможно присвоить объекту другой прототип.  Однако пользовательским объектам можно присваивать новый прототип.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]