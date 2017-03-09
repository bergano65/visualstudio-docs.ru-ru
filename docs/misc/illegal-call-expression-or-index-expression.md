---
title: "Недопустимое выражение вызова или индекса. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимое выражение вызова или индекса.
Значение в круглых скобках после выражения не является процедурой, свойством или массивом.  
  
 Эту ошибку может вызывать следующий код.  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 Поскольку `Nothing` не принимает аргументы или индексы, его нельзя использовать со скобками.  
  
 **Идентификатор ошибки:** BC32303  
  
### Исправление ошибки  
  
-   Удалите круглые скобки и значение, которое в них заключено.  
  
## См. также  
 [Практическое руководство. Вызов процедуры, возвращающей значение](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [Практическое руководство. Вызов процедуры, которая не возвращает значение](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [NOTINBUILD Практическое руководство. Помещение значения в массив](http://msdn.microsoft.com/ru-ru/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [NOTINBUILD Практическое руководство. Получение значения из массива](http://msdn.microsoft.com/ru-ru/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [Практическое руководство. Запись значения в свойство](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [Практическое руководство. Получение значения из свойства](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)