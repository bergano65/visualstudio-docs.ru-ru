---
title: "Не удается инициализировать член &quot;&lt;имя_члена&gt;&quot; в выражении инициализатора объекта, поскольку он является общим. | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается инициализировать член &quot;&lt;имя_члена&gt;&quot; в выражении инициализатора объекта, поскольку он является общим.
Инициализаторы объектов не могут использоваться для инициализации любого члена класса, объявленного общим. Дополнительные сведения см. в разделе [Shared](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 **Идентификатор ошибки:** BC30991  
  
### Исправление ошибки  
  
1.  Проверьте определение класса, чтобы определить, какой член является общим.  
  
2.  Исключите инициализацию для этого члена из списка инициализатора объектов.  
  
## Пример  
 В следующем примере общим членом является `totalCustomers`.  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 Поскольку `totalCustomers` является общим, попытка задать его начальное значение в списке инициализатора объектов вызывает эту ошибку.  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [НЕ В СБОРКЕ. Общие члены в Visual Basic](http://msdn.microsoft.com/ru-ru/dbc3783f-83a2-4225-995d-c2d6d025663d)