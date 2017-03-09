---
title: "Ошибка компилятора CS1934 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1934
Не удалось найти реализацию шаблона запроса для исходного типа "тип". Метод "метод" не найден. Рассмотрите возможность явного указания типа переменной диапазона "имя".  
  
 Эта ошибка возникает в том случае, если выражение запроса задает источник данных, для которого отсутствуют реализованные стандартные операторы запроса. Например, эта ошибка возникает, если указать `ArrayList` без предоставления явного типа переменной диапазона.  
  
### Исправление ошибки  
  
1.  В следующем примере решением является просто указание типа переменной диапазона:  
  
    ```  
    var q = from int x in list  
    ```  
  
## Пример  
 В следующем примере показан один из возможных способов получения ошибки CS1934:  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## См. также  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)