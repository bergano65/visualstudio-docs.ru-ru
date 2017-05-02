---
title: "Оператор do...while (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while - оператор"
  - "прерывание циклов"
  - "циклические структуры, do и do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Оператор do...while (JavaScript)
Один раз выполняет блок операторов, а затем повторяет выполнение цикла до тех пор, пока условное выражение не возвратит значение `false`.  
  
## Синтаксис  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Параметры  
 `statement`  
 Обязательный параметр.  Оператор, который должен выполняться, если значение выражения `expression` равно `true`.  Могут быть составными операторами.  
  
 `expression`  
 Обязательный параметр.  Выражение, которое можно привести к логическому значению `true` или `false`.  Если `expression` имеет значение `true`, то цикл выполняется повторно.  Если `expression` имеет значение `false`, то цикл завершается.  
  
## Заметки  
 В отличие от оператора `while`, цикл `do...while` выполняется один раз до вычисления значения условного выражения.  
  
 В любой строке блока `do…while` можно использовать оператор `break`, чтобы программа вышла из цикла, или оператор `continue`, чтобы перейти непосредственно к выражению `while`.  
  
## Пример  
 В следующем примере инструкции в цикле `do...while` продолжают выполняться до тех пор, пока значение переменной `i` остается меньше 10.  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## Пример  
 В следующем примере, операторы внутри цикла выполняются один раз, даже если условие не выполняется.  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)   
 [Оператор с идентификатором](../../javascript/reference/labeled-statement-javascript.md)