---
title: "Функция Math.round (JavaScript) | Microsoft Docs"
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
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math - объект"
  - "Round - метод"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Функция Math.round (JavaScript)
Возвращает предоставленное числовое выражение, округленное до ближайшего целого числа.  
  
## Синтаксис  
  
```  
  
Math.round(  
number  
)   
```  
  
## Заметки  
 Обязательный аргумент `number` — значение, которое должно быть округлено до ближайшего целого числа.  
  
 Для положительных чисел: если дробная часть аргумента `number` больше или равна 0,5, возвращаемое значение равно наименьшему целому числу, большему, чем `number`.  Если дробная часть аргумента меньше 0,5, возвращаемое значение равно наибольшему целому числу, которое меньше или равно `number`.  
  
 Для отрицательных чисел: если дробная часть равна \-0,5, возвращаемое значение равно наименьшему целому числу, большему чем number.  
  
 Например, метод `Math.round(8.5)` возвращает значение 9, а метод `Math.round(-8.5)` — значение \-8.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Math](../../javascript/reference/math-object-javascript.md)  
  
## См. также  
 [Функция Math.random](../../javascript/reference/math-random-function-javascript.md)