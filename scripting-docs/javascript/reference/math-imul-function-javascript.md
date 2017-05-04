---
title: "Функция Math.imul (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция Math.imul (JavaScript)
Возвращает произведение двух чисел, которые обрабатываются как 32\-разрядные целые числа со знаком.  
  
## Синтаксис  
  
```  
Math.imul(x, y);  
```  
  
#### Параметры  
 `x`  
 Обязательный.  Первое число.  
  
 `y`  
 Обязательный.  Второе число.  
  
## Заметки  
 Эта функция используется для компиляторов, таких как Emscripten и Mandreel, в которых умножение целых чисел реализовано не так, как в JavaScript.  
  
## Пример  
 В следующем примере кода показано, как выполнять умножение с помощью функции `Math.imul`.  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]