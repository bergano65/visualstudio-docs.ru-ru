---
title: "Number.isSafeInteger (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (Number) (JavaScript)
Возвращает логическое значение, указывающее, можно ли безопасно представить число в JavaScript.  
  
## Синтаксис  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## Возвращаемое значение  
 `true`, если число находится в диапазоне от `Number.MIN_SAFE_INTEGER` до `Number.MAX_SAFE_INTEGER` включительно; в противном случае — `false`.  
  
## Заметки  
 В JavaScript безопасное целое число — это число двойной точности IEEE 754 до округления.  
  
## Пример  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применение**: [Объект Number](../../javascript/reference/number-object-javascript.md)