---
title: "Тип параметра данного унарного оператора должен быть вмещающим типом &quot;&lt;имя_типа&gt;&quot; | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип параметра данного унарного оператора должен быть вмещающим типом &quot;&lt;имя_типа&gt;&quot;
В определении унарного оператора указан параметр с типом, отличным от типа класса или структуры, в которой определен оператор.  
  
 При определении оператора в классе или структуре по крайней мере один из параметров должен иметь тип класса или структуры. В случае унарного оператора единственный операнд должен иметь тип данного класса или структуры.  
  
 **Идентификатор ошибки:** BC33020  
  
### Исправление ошибки  
  
-   Измените тип параметра на тип класса или структуры, в которой определен оператор.  
  
-   Если вы хотите использовать один тип данных в качестве параметра, но другой — в качестве типа данных, возвращаемого в результате операции, определите вместо этого оператор преобразования.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)