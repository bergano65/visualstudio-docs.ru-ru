---
title: "Функция Number.isFinite (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция Number.isFinite (Number) (JavaScript)
Возвращает логическое значение, указывающее, является ли значение конечным числом.  
  
## Синтаксис  
  
```  
Number.isFinite(numValue)   
```  
  
## Возвращаемое значение  
 `false`, если значение равно `NaN`, `+∞` или `-∞`; в противном случае — `true`.  
  
## Заметки  
  
## Пример  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применение**: [Объект Number](../../javascript/reference/number-object-javascript.md)