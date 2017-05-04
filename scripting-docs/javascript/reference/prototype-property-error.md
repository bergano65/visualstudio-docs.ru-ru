---
title: "Свойство prototype (Error) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (Error)
Возвращает ссылку на прототип ошибки.  
  
## Синтаксис  
  
```  
  
error.prototype  
```  
  
## Заметки  
 Аргумент `error` представляет собой имя ошибки.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей объекта Error.  Новые экземпляры объекта наследуют поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Error` метод, возвращающий значение наибольшего элемента массива, объявите функцию, добавьте ее в свойство `Error.prototype`, а затем используйте ее.  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] имеют свойство `prototype`, которое доступно только для чтения.  К прототипу можно добавлять свойства и методы, но невозможно присвоить объекту другой прототип.  Однако пользовательским объектам можно присваивать новый прототип.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]