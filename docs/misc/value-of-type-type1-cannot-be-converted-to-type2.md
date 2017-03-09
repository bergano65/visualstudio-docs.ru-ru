---
title: "Невозможно преобразовать значение типа &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot; | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно преобразовать значение типа &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot;
Оператор пытается преобразовать один тип данных в другой способом, который не определен. Далее приведены некоторые возможные причины этой ошибки:  
  
-   Преобразование указывает два типа данных, между которыми не существует преобразования. Примером этого является преобразование из значения `Boolean` в тип `Date`.  
  
-   Инициализация массива не включает фигурные скобки \(`{}`\), за которыми следует предложение `New`. В этом случае \<тип2\> имеет форму "1\-мерный массив типа \<тип\>".  
  
 **Идентификатор ошибки:** BC30311  
  
### Исправление ошибки  
  
-   Убедитесь, что выражение может быть преобразовано в целевой тип данных.  
  
-   Если \<тип2\> является массивом, убедитесь, что предложение `New`содержит круглые и фигурные скобки, за которыми следует имя типа. Следующий код иллюстрирует правильную инициализацию массива.  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## См. также  
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Практическое руководство. Инициализация переменной массива в Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)