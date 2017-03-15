---
title: "Исходным типом оператора преобразования не может быть интерфейс | Microsoft Docs"
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
  - "vbc33029"
  - "bc33029"
helpviewer_keywords: 
  - "BC33029"
ms.assetid: 0d0ee461-dd48-424b-b83a-484bfc648d4d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Исходным типом оператора преобразования не может быть интерфейс
Оператор преобразования объявлен с типом интерфейса для параметра.  
  
 Во время компиляции [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] определяет возможность выполнения предопределенного преобразования любого интерфейса в любой ссылочный тип. Такое преобразование может вызвать сбой во время выполнения, однако компилятор не может предсказать результаты выполнения, поэтому он позволяет компилировать такие преобразования.  
  
 Так как компилятор считает, что это преобразование уже определено, он не позволяет переопределить его.  
  
 **Идентификатор ошибки:** BC33029  
  
### Исправление ошибки  
  
-   Полностью удалите это определение оператора. Он является предварительно определенным.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)