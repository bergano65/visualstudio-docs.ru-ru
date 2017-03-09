---
title: "После каждого оператора &quot;Inherits&quot; до первого объявления в классе должен присутствовать оператор &quot;Implements&quot; | Microsoft Docs"
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
  - "bc31053"
  - "vbc31053"
helpviewer_keywords: 
  - "BC31053"
ms.assetid: 8036a1a1-7e31-4c49-b74b-01601a548f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# После каждого оператора &quot;Inherits&quot; до первого объявления в классе должен присутствовать оператор &quot;Implements&quot;
Оператор `Implements` обнаружен в недопустимом положении.  
  
 **Идентификатор ошибки:** BC31053  
  
### Исправление ошибки  
  
-   Поместите операторы `Implements` сразу после операторов `Inherits`, но перед любыми объявлениями. Пример:  
  
    ```  
    Class Derived Inherits Base Implements One Sub SubOne() Implements One.Method1 ' Add code to implement the method. End Sub End Class  
    ```  
  
## См. также  
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)