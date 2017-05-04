---
title: "Оператор for (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "циклические структуры, операторы for"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Оператор for (JavaScript)
Выполняет блок операторов, пока указанное условие имеет значение true.  
  
## Синтаксис  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## Параметры  
 `initialization`  
 Необязательный.  Выражение.  Данное выражение выполняется только один раз перед началом выполнения цикла.  
  
 `test`  
 Необязательный.  Выражение типа Boolean.  Если выражение `test` имеет значение `true`, выполняется оператор `statement`.  Если выражение `test` имеет значение `false`, выполнение цикла завершается.  
  
 `increment`  
 Необязательный.  Выражение.  Данное выражение увеличения выполняется в конце каждого прохода цикла.  
  
 `statement`  
 Необязательный.  Один или несколько операторов, выполняемых, если выражение `test` имеет значение **true**.  Может представлять собой составную инструкцию.  
  
## Заметки  
 Цикл `for` обычно используется, если цикл необходимо выполнить известное количество раз.  Цикл `for` удобно использовать для итерации всех элементов массива и для последовательной обработки.  
  
 Проверка условного выражения осуществляется до выполнения цикла, поэтому оператор `for` выполняется ноль или более раз.  
  
 В любой строке блока операторов цикла `for` можно использовать оператор `break`, чтобы выйти из цикла, или оператор `continue`, чтобы передать управление следующей итерации цикла.  
  
## Пример  
 В приведенном ниже примере оператор `for` выполняет заключенные в цикл операторы следующим образом.  
  
-   Сначала вычисляется начальное значение переменной `i`.  
  
-   Затем, если значение `i` меньше или равно 9, выполняются операторы `document.write` и повторно вычисляется значение `i`.  
  
-   Когда значение `i` становится больше 9, условие становится ложным и управление передается за пределы цикла.  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## Пример  
 Все выражения оператора `for` являются необязательными.  В следующем примере с помощью оператора `for` создается бесконечный цикл, для выхода из которого используется оператор `break`.  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)