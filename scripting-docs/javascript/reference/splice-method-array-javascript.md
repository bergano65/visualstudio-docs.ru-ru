---
title: "Метод splice (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice - метод"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод splice (Array) (JavaScript)
Удаляет элементы из массива и при необходимости вставляет на их место новые элементы, возвращая удаленные элементы.  
  
## Синтаксис  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Объект `Array`.  
  
 `start`  
 Обязательный.  Позиция в массиве, с которой начинается удаление элементов \(индексация ведется с нуля\).  
  
 `deleteCount`  
 Обязательный.  Число удаляемых элементов.  
  
 `item1, item2,. . ., itemN`  
 Необязательный.  Элементы, которые необходимо вставить в массив вместо удаленных элементов.  
  
## Заметки  
 Метод `splice` изменяет `arrayObj`, удаляя указанное количество элементов, начиная с позиции `start`, и вставляя новые элементы.  Удаленные элементы возвращаются как новый объект `Array`.  
  
## Пример  
 В следующем примере кода показано использование метода `splice`.  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Метод slice \(массив\)](../../javascript/reference/slice-method-array-javascript.md)