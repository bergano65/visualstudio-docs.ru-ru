---
title: "Условный (тернарный) оператор (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "условный (тернарный) оператор"
  - "условные операторы"
  - "тернарный"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Условный (тернарный) оператор (?:) (JavaScript)
Возвращает одно из двух выражений в зависимости от условия.  
  
## Синтаксис  
  
```  
  
test ? expression1 : expression2  
```  
  
## Параметры  
 `test`  
 Любое логическое выражение.  
  
 `expression1`  
 Выражение, возвращаемое в том случае, если `test` равен `true`.  Может быть выражением с запятыми.  
  
 `expression2`  
 Выражение, возвращаемое в том случае, если `test` равен `false`.  С помощью запятой можно связать несколько выражений.  
  
## Заметки  
 Оператор `?:` можно использовать в качестве ярлыка оператора `if...else`.  Обычно его применяют в составе более крупного выражения, когда использовать оператор `if...else` нецелесообразно.  Например:  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 В следующем примере создается строка "Good evening.", если в текущий момент позже 6 вечера.  Эквивалентный код с оператором `if...else` будет таким:  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Пример мини\-приложения настройки от Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)