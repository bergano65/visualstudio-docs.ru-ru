---
title: "Операторы преобразования не могут выполнять преобразование из базового типа | Microsoft Docs"
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
  - "bc33030"
  - "vbc33030"
helpviewer_keywords: 
  - "BC33030"
ms.assetid: b19800ab-6a32-473f-b7ee-7de584e4ccae
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы преобразования не могут выполнять преобразование из базового типа
Оператор преобразования объявлен с типом параметра, от которого производится тип возврата.  
  
 Во время компиляции [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] считает, что существует предопределенное преобразование из любого ссылочного типа в любой тип в его иерархии наследования, то есть в любой тип, от которого он является производным или который является производным от него. Такое преобразование может вызвать сбой во время выполнения, однако компилятор не может предсказать результаты выполнения, поэтому он позволяет компилировать такие преобразования.  
  
 Так как компилятор считает, что это преобразование уже определено, он не позволяет переопределить его.  
  
 **Идентификатор ошибки:** BC33030  
  
### Исправление ошибки  
  
-   Полностью удалите это определение оператора. Он является предварительно определенным.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)