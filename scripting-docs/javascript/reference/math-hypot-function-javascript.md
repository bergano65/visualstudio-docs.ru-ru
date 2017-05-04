---
title: "Функция Math.hypot (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция Math.hypot (JavaScript)
Возвращает квадратный корень из суммы квадратов аргументов.  
  
## Синтаксис  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### Параметры  
 `value1`  
 Обязательный.  Первое число.  
  
 `value2`  
 Необязательный.  Второе число.  
  
 `values`  
 Необязательный.  Одно или несколько чисел.  
  
## Заметки  
 Если один из аргументов имеет значение NaN, функция возвращает значение NaN.  Если аргументы не указаны, функция возвращает значение 0.  
  
## Пример  
 Ниже приведен пример использования функции `Math.hypot`.  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]