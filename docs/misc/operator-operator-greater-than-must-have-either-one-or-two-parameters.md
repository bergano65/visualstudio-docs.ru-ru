---
title: "Оператор &quot;&lt;оператор&gt;&quot; должен иметь один или два параметра | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;&lt;оператор&gt;&quot; должен иметь один или два параметра
Оператор, который может быть унарным или бинарным, определен либо без параметров, либо более чем с двумя параметрами.  
  
 Унарный оператор должен иметь один параметр, а бинарный — два.  
  
 **Идентификатор ошибки:** BC33016  
  
### Исправление ошибки  
  
-   Измените определение, указав один или два параметра.  
  
-   Если параметры не требуются или требуется более двух параметров, необходимо использовать [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement), чтобы определить процедуру `Function` вместо оператора.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)