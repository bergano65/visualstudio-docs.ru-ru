---
title: "Операторы преобразования не могут приводить к типу Object | Microsoft Docs"
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
  - "bc33028"
  - "vbc33028"
helpviewer_keywords: 
  - "BC33028"
ms.assetid: 064b478c-85a1-4e13-a292-d8aebb079cad
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы преобразования не могут приводить к типу Object
Оператор преобразования объявлен с возвращаемым типом [Тип данных Object](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Во время компиляции [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] считает, что существует предопределенное преобразование из любого ссылочного типа в любой тип в его иерархии наследования, то есть в любой тип, от которого он является производным или который является производным от него.`Object` — это универсальный тип данных в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], поэтому каждый тип является производным от `Object`.  
  
 Так как компилятор считает, что это преобразование уже определено, он не позволяет переопределить его.  
  
 **Идентификатор ошибки:** BC33028  
  
### Исправление ошибки  
  
-   Полностью удалите это определение оператора. Он является предварительно определенным.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Object как универсальный тип данных \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/5315bf21-2b22-45ab-98cd-5631dffbcb2f)