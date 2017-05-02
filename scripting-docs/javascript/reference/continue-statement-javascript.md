---
title: "Оператор continue (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue - оператор"
  - "do...while - оператор"
  - "циклические структуры, continue - оператор"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Оператор continue (JavaScript)
Останавливает текущую итерацию цикла и начинает новую итерацию.  
  
## Синтаксис  
  
```  
continue [label];  
```  
  
## Заметки  
 Необязательный аргумент `label` указывает оператор, к которому применяется метод `continue`.  
  
 Оператор `continue` можно использовать только в цикле `while`, `do...while`, **for** или `for...in`.  При выполнении оператора `continue` текущая итерация цикла останавливается, выполнение программы продолжается с начала цикла.  При этом в циклах различных типов выполняются следующие действия.  
  
-   Циклы `while` и `do...while` проверяют свое состояние; если оно имеет значение true, повторяют цикл.  
  
-   Циклы `for` выполняют выражение увеличения; если тестовое выражение имеет значение true, повторяют цикл.  
  
-   Циклы `for...in` переходят к следующему полю указанной переменной и повторяют цикл.  
  
## Примеры  
 В этом примере цикл выполняет перебор от 1 до 9.  Операторы между `continue` и концом тела оператора `for` пропускаются из\-за использования оператора `continue` вместе с выражением `(i < 5)`.  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 В следующем примере кода оператор `continue` относится к циклу `for`, которому предшествует метка `Inner:`.  Когда значение `j` достигает 24, оператор `continue` вызывает переход цикла `for` к следующей итерации.  При значениях от 21 до 23 и от 25 до 30 выполняется вывод на каждой строке.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор с идентификатором](../../javascript/reference/labeled-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)