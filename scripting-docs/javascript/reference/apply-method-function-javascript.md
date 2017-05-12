---
title: "Метод apply (Function) (JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply - метод"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод apply (Function) (JavaScript)
Вызывает функцию, подставляя указанный объект вместо значения `this` функции и указанный массив вместо аргументов функции.  
  
## Синтаксис  
  
```  
apply([thisObj[,argArray]])  
```  
  
## Параметры  
 `thisObj`  
 Необязательный.  Объект для использования в качестве объекта `this`.  
  
 `argArray`  
 Необязательный.  Набор аргументов для передачи в функцию.  
  
## Заметки  
 Если `argArray` не является допустимым объектом, то возникает ошибка "Ожидался объект".  
  
 Если ни один из аргументов `argArray` и `thisObj` не указан, в качестве объекта `thisObj` используется исходный объект `this`, которому не передаются никакие аргументы.  
  
## Пример  
 В следующем примере кода показано использование метода apply.  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Объект Function](../../javascript/reference/function-object-javascript.md)