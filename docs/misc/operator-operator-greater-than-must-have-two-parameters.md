---
title: "Оператор &quot;&lt;оператор&gt;&quot; должен иметь два параметра | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;&lt;оператор&gt;&quot; должен иметь два параметра
Бинарный оператор определен с параметрами числом менее двух или более двух.  
  
 Бинарный оператор должен иметь ровно два параметра.  
  
 **Идентификатор ошибки:** BC33015  
  
### Исправление ошибки  
  
-   Измените определение, указав ровно два параметра.  
  
-   Если требуется только один параметр, необходимо определить унарный оператор.  
  
-   Если параметры не требуются или требуется более двух параметров, вы должны использовать [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement), чтобы определить процедуру `Function` вместо оператора.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)