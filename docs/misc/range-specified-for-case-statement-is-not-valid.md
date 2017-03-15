---
title: "Диапазон, указанный для оператора Case, недопустим | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Диапазон, указанный для оператора Case, недопустим
Для оператора `Case` указан недопустимый диапазон.  
  
 При сравнении одного и того же выражения с различными значениями можно использовать операторы `Select...Case` вместо `If...Then...Else`. В то время как операторы `If` и `ElseIf` могут оценивать различные выражения в каждом операторе, оператор `Select` оценивает выражение только один раз и использует его при каждом сравнении. Каждый оператор `Case` может содержать более одного значения, диапазона значений или сочетания значений и операторов сравнения.  
  
 **Идентификатор ошибки:** BC40052  
  
### Исправление ошибки  
  
-   Укажите диапазон, включающий все значения, или используйте оператор `Case Else` для перехвата неопределенного значения.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Структуры решений](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)