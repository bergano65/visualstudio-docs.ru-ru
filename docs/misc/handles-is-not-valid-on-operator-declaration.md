---
title: "Handles не допускается в объявлении оператора | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Handles не допускается в объявлении оператора
[Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) содержит ключевое слово [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause).  
  
 Только процедура `Sub` может обрабатывать события. Процедура `Operator` делать этого не может. Дополнительные сведения об обработчиках событий см. в разделе [Практическое руководство. Вызов обработчика событий в Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md).  
  
 Процедура `Operator` требует обоих ключевых слов: `Public` и `Shared`, а оператор преобразования требует ключевого слова `Widening` либо `Narrowing`. Для получения дополнительной информации см. [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **Идентификатор ошибки:** BC33003  
  
### Исправление ошибки  
  
-   Если предполагается, что процедура будет обрабатывать события, перепишите ее как процедуру `Sub`.  
  
-   Если процедура должна определять оператор, удалите ключевое слово `Handles` из ее объявления.  
  
## См. также  
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)