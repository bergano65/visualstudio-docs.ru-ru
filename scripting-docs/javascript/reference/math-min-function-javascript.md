---
title: "Функция Math.min (JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min - метод"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция Math.min (JavaScript)
Возвращает наименьшее числовое выражение из набора.  
  
## Синтаксис  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## Заметки  
 Необязательные аргументы `number1, number2, ..., numberN` представляют собой числовые выражения для вычисления.  
  
 Если аргументы не предоставлены, то возвращается значение [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Если любой из аргументов имеет значение `NaN`, возвращается также значение `NaN`.  
  
## Пример  
 В следующем примере кода показано, как получить наименьшее из двух выражений.  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Функция Math.max](../../javascript/reference/math-max-function-javascript.md)