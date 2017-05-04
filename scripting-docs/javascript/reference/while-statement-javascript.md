---
title: "Оператор while (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "циклические структуры, операторы while"
  - "Оператор while"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Оператор while (JavaScript)
Выполняет оператор или набор операторов до тех пор, пока указанное условие не будет равно `false`.  
  
## Синтаксис  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Параметры  
 `expression`  
 Обязательный параметр.  Логическое выражение, проверяемое перед каждой итерацией цикла.  Если `expression` имеет значение `true`, цикл выполняется.  Если `expression` имеет значение `false`, цикл завершается.  
  
 `statements`  
 Необязательный параметр.  Один или несколько операторов для выполнения, пока `expression` равно `true`.  
  
## Заметки  
 Оператор `while` проверяет `expression` перед первым выполнением цикла.  Если `expression` равно `false` в этот раз, цикл никогда не выполнится.  
  
## Пример  
 В следующем примере показано использование оператора `while`.  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)