---
title: "Оператор break (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break - оператор"
  - "do...while - оператор"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Оператор break (JavaScript)
Завершает выполнение текущего цикла или, если он используется в сочетании с меткой `label`, завершает работу связанного оператора.  
  
## Синтаксис  
  
```  
break [label];  
```  
  
## Заметки  
 Необязательный аргумент `label` задает метку оператора, работа которого завершается.  
  
 Оператор `break` обычно используется в операторах `switch` и циклах `while`, `for`, `for...in` и `do...while`.  Аргумент `label` чаще всего используется в операторах `switch`, но его можно использовать в любых операторах, простых и составных.  
  
 При выполнении оператора `break` выполняется выход из текущего цикла или оператора, выполнение скрипта продолжается с оператора, который идет следующим.  
  
## Примеры  
 В этом примере настраивается счетчик, значения которого должны изменяться от 1 до 99; однако оператор `break` прерывает цикл после 14 итераций.  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 В следующем примере кода оператор `break` относится к циклу `for`, которому предшествует оператор `Inner:`.  Когда `j` равняется 24, оператор `break` завершает выполнение этого цикла в программе.  Значения от 21 до 23 печатаются на каждой строке.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор с идентификатором](../../javascript/reference/labeled-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)