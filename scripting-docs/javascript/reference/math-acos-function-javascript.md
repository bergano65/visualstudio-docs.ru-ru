---
title: "Функция Math.acos (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos - метод"
  - "arcosine - метод"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Функция Math.acos (JavaScript)
Возвращает арккосинус \(или обратный косинус\) числа.  
  
## Синтаксис  
  
```  
Math.acos(number)  
```  
  
#### Параметры  
 Обязательный аргумент `number` — числовое выражение.  
  
## Возвращаемое значение  
 Арккосинус аргумента `number`, в радианах.  
  
## Пример  
 В следующем коде показано, как использовать функцию `acos`.  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## Заметки  
 **Применение**: [Объект Math](../../javascript/reference/math-object-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Функция Math.asin](../../javascript/reference/math-asin-function-javascript.md)   
 [Функция Math.atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Функция Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Функция Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Функция Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Объект Math](../../javascript/reference/math-object-javascript.md)