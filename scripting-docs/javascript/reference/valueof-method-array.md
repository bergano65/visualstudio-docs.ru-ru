---
title: "Метод valueOf (Array) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод valueOf (Array)
Возвращает примитивное значение указанного объекта.  
  
## Синтаксис  
  
```  
  
array.valueOf()  
```  
  
#### Параметры  
 Этот метод не имеет параметров.  
  
## Возвращаемое значение  
 Возвращает экземпляр массива.  
  
## Заметки  
 В следующем примере созданный экземпляр объекта массива совпадает с возвращаемым значением этого метода.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]