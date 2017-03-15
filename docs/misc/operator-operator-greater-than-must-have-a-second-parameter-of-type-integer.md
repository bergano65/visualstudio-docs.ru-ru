---
title: "Оператор &quot;&lt;оператор&gt;&quot; должен иметь второй параметр типа Integer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;&lt;оператор&gt;&quot; должен иметь второй параметр типа Integer
Оператор битового сдвига объявлен со вторым параметром типа, отличного от `Integer`.  
  
 При использовании в выражении оператора сдвига вправо \(`>>`\) или сдвига влево \(`<<`\) укажите значение сдвига во втором операнде. Для этого операнда [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] позволяет указать любой тип данных, который расширяется до `Integer`. Однако определение второго операнда имеет тип строго `Integer`. Если вы определяете класс или структуру с оператором битового сдвига в этом классе или структуре, в определении должно быть указано `Integer` для второго операнда.  
  
 **Идентификатор ошибки:** BC33041  
  
### Исправление ошибки  
  
-   Измените определение оператора битового сдвига для возврата значения `Integer`.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Операторы поразрядного сдвига](/dotnet/visual-basic/language-reference/operators/bit-shift-operators)