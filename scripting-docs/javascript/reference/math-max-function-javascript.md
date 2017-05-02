---
title: "Функция Math.max (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max - метод"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция Math.max (JavaScript)
Возвращает наибольшее числовое выражение из представленного набора.  
  
## Синтаксис  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## Заметки  
 Необязательные аргументы `number1, number2, ..., numberN` представляют собой числовые выражения для вычисления.  
  
 Если аргументы не предоставлены, то возвращается значение [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Если любой из аргументов имеет значение `NaN`, возвращается также значение `NaN`.  
  
## Пример  
 В следующем примере кода показано, как получить наибольшее из двух выражений.  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Функция Math.min](../../javascript/reference/math-min-function-javascript.md)