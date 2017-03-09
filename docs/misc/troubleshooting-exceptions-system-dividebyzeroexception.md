---
title: "Разрешение вопросов, связанных с исключениями: System.DivideByZeroException | Microsoft Docs"
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
  - "DivideByZeroException - класс"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.DivideByZeroException
Исключение <xref:System.DivideByZeroException> генерируется при попытке деления целого или десятичного значения на ноль.  
  
## Полезные советы  
 **Перед выполнением операции деления убедитесь, что делитель не равен нулю.**  
 В соответствии с правилами арифметики IEEE результатом деления числа с плавающей запятой на ноль может быть положительная или отрицательная бесконечность, а также нечисловое значение \(NaN\). Операции с плавающей запятой не генерируют исключений.  
  
## См. также  
 <xref:System.DivideByZeroException>   
 [Арифметические операторы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)