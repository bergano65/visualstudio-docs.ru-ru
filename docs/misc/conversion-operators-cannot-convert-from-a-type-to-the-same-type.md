---
title: "Операторы преобразования не могут выполнять преобразование типа к этому же типу. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы преобразования не могут выполнять преобразование типа к этому же типу.
Оператор преобразования объявлен с одним и тем же типом для параметра и для возвращаемого значения.  
  
 Преобразование любого типа в самого себя не имеет смысла.  
  
 **Идентификатор ошибки:** BC33024  
  
### Исправление ошибки  
  
-   Измените тип параметра или возвращаемого значения. Один из них должен быть типом класса или структуры, в которой определен оператор. Другой должен быть другого типа.  
  
-   Если требуется выполнить преобразование содержимого параметра, используйте [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement) для определения процедуры `Function` вместо оператора.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)