---
title: "Ожидался VBArray | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Ожидался VBArray
Ожидался объект Visual Basic safeArray, но указанный объект не является таким объектом.  
  
```  
new VBArray(safeArray);  
```  
  
 Объекты VBArray доступны только на чтение и не могут создаваться непосредственно.  Аргумент safeArray является значением VBArray и должен был получить значение VBArray до передачи конструктору `VBArray`.  Это можно сделать только путем извлечения значения из существующего объекта ActiveX или другого объекта.  
  
### Исправление ошибки  
  
-   Убедитесь, что конструктору **VBArray** передаются только объекты **VBArray**.  
  
## См. также  
 [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)