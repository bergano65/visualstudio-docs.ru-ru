---
title: "Метод call (Function) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call - метод"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод call (Function) (JavaScript)
Вызывает метод объекта, заменяющего текущий объект.  
  
## Синтаксис  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## Параметры  
 `thisObj`  
 Необязательный параметр.  Объект , используемый в качестве текущего объекта.  
  
 `arg1, arg2, , argN`  
 Необязательный параметр.  Список аргументов, передаваемых методу.  
  
## Заметки  
 Метод `call` используется для вызова метода от имени другого объекта.  Он позволяет сменить объект `this` функции с исходного контекста на новый объект, заданный параметром `thisObj`.  
  
 Если объект `thisObj` не указан, то в качестве `thisObj` используется объект `global`.  
  
## Пример  
 В следующем примере кода демонстрируется применение метода `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Объект Function](../../javascript/reference/function-object-javascript.md)   
 [Метод apply \(Function\)](../../javascript/reference/apply-method-function-javascript.md)