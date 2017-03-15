---
title: "Разрешение вопросов, связанных с исключениями: System.OverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OverflowException - класс"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.OverflowException
Исключение <xref:System.OverflowException> возникает, когда выполнение арифметической операции, операции приведения к типу или преобразования в проверяемом контексте приводит к переполнению. Переполнение возникает, если значение, полученное в результате выполнения операции, слишком велико для указанного типа, бесконечно, либо является нечисловым значением \(NaN\).  
  
## Полезные советы  
 **При приведении числа его значение должно быть допустимым и конечным.**  
 Исходное значение не может быть бесконечным или нечисловым значением.  
  
 **Убедитесь в отсутствии деления на ноль.**  
 Обычно это исключение возникает при делении на ноль.  
  
## Примечания  
 Исключение <xref:System.OverflowException> генерируется при переполнении в языках программирования, поддерживающих обнаружение переполнения. Например, в C\# для обнаружения условий переполнения используется ключевое слово `checked`. Исключение <xref:System.OverflowException> возникает только в проверяемом контексте.  
  
 Если результат арифметической операции с данными целочисленного или десятичного типа выходит за пределы диапазона целевого типа данных:  
  
-   Если операция задана в виде постоянного выражения, в проверяемом контексте возникает ошибка компиляции. Если же операция выполняется в ходе работы программы, создается исключение <xref:System.OverflowException>.  
  
-   В непроверяемом контексте результат усекается путем удаления старших разрядов, которые не помещаются в целевой тип данных.  
  
 Сведения о диапазонах значений типов данных см. в разделах [Типы данных](/dotnet/visual-basic/language-reference/data-types/data-type-summary), [Таблица целых типов](/dotnet/csharp/language-reference/keywords/integral-types-table) и [Таблица типов с плавающей запятой](/dotnet/csharp/language-reference/keywords/floating-point-types-table).  
  
## См. также  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)