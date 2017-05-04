---
title: "Метод unshift (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift - метод"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод unshift (Array) (JavaScript)
Вставляет новые элементы в начале массива.  
  
## Синтаксис  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Объект `Array`.  
  
 `item1, item2,. . ., itemN`  
 Необязательный.  Элементы, которые необходимо вставить в начало объекта `Array`.  
  
## Заметки  
 Метод `unshift` вставляет элементы в начало массива, поэтому они располагаются в том порядке, в котором указаны в списке аргументов.  
  
## Пример  
 В следующем примере показано использование метода `unshift`.  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Метод shift \(Array\)](../../javascript/reference/shift-method-array-javascript.md)