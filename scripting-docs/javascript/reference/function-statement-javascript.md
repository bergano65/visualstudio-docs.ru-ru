---
title: "Оператор function (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "объявление функций"
  - "объявление функций, синтаксис"
  - "function - оператор"
  - "new - оператор"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Оператор function (JavaScript)
Объявляет новую функцию.  
  
## Синтаксис  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## Параметры  
 `functionname`  
 Обязательный.  Имя функции.  
  
 `arg1...argN`  
 Необязательный.  Необязательный список разделенных запятыми аргументов, которые понимает функция.  
  
 `statements`  
 Необязательный.  Один или более операторов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Заметки  
 Оператор `function` применяется для объявления функции с целью ее дальнейшего использования.  Код, содержащийся в разделе `statements`, не выполняется до вызова функции в скрипте.  
  
 Оператор [return](../../javascript/reference/return-statement-javascript.md) используется для возврата значения из функции.  Оператор `return` использовать не обязательно: программа вернет управление после достижения конца функции.  Если в функции не выполняется никакой оператор `return` или в операторе `return` отсутствует выражение, функция возвращает значение `undefined`.  
  
> [!NOTE]
>  Вызывая функцию, следует обязательно указывать скобки и все обязательные параметры.  При вызове функции без скобок возвращается ссылка на функцию, а не результаты функции.  
  
## Пример  
 В следующем примере показано использование оператора `function`.  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## Пример  
 Функция может быть присвоена переменной.  Это показано в следующем примере.  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)