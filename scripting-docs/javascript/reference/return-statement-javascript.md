---
title: "Оператор return (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function - оператор"
  - "return - оператор"
  - "return - оператор, существующие функции в скрипте"
  - "return - оператор, синтаксис"
  - "прерывание выполнения"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор return (JavaScript)
Завершает выполнение текущей функции и возвращает значение из этой функции.  
  
## Синтаксис  
  
```  
  
return[(][expression][)];   
```  
  
## Заметки  
 Необязательный аргумент *expression* — это значение, возвращаемое из функции.  Если этот аргумент не указывается, функция не возвращает значение.  
  
 Оператор `return` используется для остановки выполнения функции и возвращения значения *expression*.  Если аргумент *expression* опущен или в функции не выполняется оператор `return`, то выражению, вызвавшему текущую функцию, присваивается значение undefined.  
  
## Пример  
 В следующем примере показано использование оператора `return`.  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## Пример  
 В следующем примере показано использование оператора `return` для возврата функции.  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)