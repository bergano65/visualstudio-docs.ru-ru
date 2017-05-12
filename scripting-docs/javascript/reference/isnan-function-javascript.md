---
title: "Функция isNaN (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN - метод"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Функция isNaN (JavaScript)
Возвращает логическое значение, которое указывает, является ли значение зарезервированным значением `NaN` \(не числом\).  
  
## Синтаксис  
  
```  
isNaN(numValue)   
```  
  
## Возвращаемое значение  
 `true`, если значение преобразованное к типу `Number`, является `NaN`, в противном случае `false`.  
  
## Заметки  
 Требуемое значение `numValue` — значение, которое проверяется для `NaN`.  
  
 Этот метод обычно используется для проверки значений, возвращаемых методами `parseInt` и `parseFloat`.  
  
 Либо переменную, содержащую `NaN` или другое значение, можно сравнить саму с собой.  Если сравнение указывает на неравенство, то значение переменной равно `NaN`,  поскольку `NaN` является единственным значением, которое не равно самому себе.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## Пример  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## См. также  
 [Функция isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [Константа NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Функция parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Функция parseInt](../../javascript/reference/parseint-function-javascript.md)