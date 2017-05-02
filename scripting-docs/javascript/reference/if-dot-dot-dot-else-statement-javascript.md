---
title: "Оператор if...else (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if - оператор, if...else"
  - "циклические структуры, операторы if...else"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Оператор if...else (JavaScript)
В зависимости от значения выражения будет выполнена та или иная группа операторов.  
  
## Синтаксис  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## Параметры  
 `condition1`  
 Обязательный.  Выражение типа Boolean.  Если выражение `condition1` имеет значение `null` или `undefined`, выражение `condition1` обрабатывается как значение `false`.  
  
 `statement1`  
 Необязательный.  Оператор, выполняемый, если выражение `condition1` имеет значение **true**.  Может представлять собой составную инструкцию.  
  
 `condition2`  
 Проверяемое условие.  
  
 `statement2`  
 Необязательный.  Оператор, выполняемый, если выражение `condition2` имеет значение `true`.  Может представлять собой составную инструкцию.  
  
 `statement3`  
 Если оба выражения `condition1` и `condition2` имеют значения `false`, выполняется этот оператор.  
  
## Пример  
 Следующий код показывает, как использовать операторы `if`, `if else` и `else`.  
  
 Рекомендуется заключать выражения `statement1` и `statement2` в фигурные скобки \({}\) для повышения наглядности кода и исключения случайных ошибок.  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Условный \(тернарный\) оператор \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)