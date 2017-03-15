---
title: "Оператор &quot;Return&quot; в операторе &quot;Function&quot;, &quot;Get&quot; или Operator должен возвращать значение. | Microsoft Docs"
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
  - "bc30654"
  - "vbc30654"
helpviewer_keywords: 
  - "BC30654"
ms.assetid: af0fb1fc-1b2e-4cae-9768-10965cda5506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;Return&quot; в операторе &quot;Function&quot;, &quot;Get&quot; или Operator должен возвращать значение.
Операторы `Return` должны использоваться для возврата значения в вызывающую процедуру. Для управления потоком выполнения команды нельзя использовать операторы `Return` сами по себе.  
  
 **Идентификатор ошибки**: BC30654  
  
### Исправление ошибки  
  
1.  Укажите значение, которое может возвращаться функцией или процедурой.  
  
2.  Используйте оператор `End`, чтобы вызвать выход программы из текущей процедуры.  
  
## См. также  
 [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)