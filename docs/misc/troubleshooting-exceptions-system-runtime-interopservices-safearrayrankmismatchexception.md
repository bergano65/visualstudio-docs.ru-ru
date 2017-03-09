---
title: "Разрешение вопросов, связанных с исключениями: System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException - класс"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Runtime.InteropServices.SafeArrayRankMismatchException
Исключение <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> возникает, если ранг входящего безопасного массива SAFEARRAY не совпадает с рангом, указанным в управляемой подписи.  
  
## Полезные советы  
 **Убедитесь, что массив имеет необходимое число измерений.**  
 Поскольку ранг и границы безопасного массива нельзя определить из библиотеки типов, предполагается, что ранг равен 1, а нижняя граница — 0. Ранг и границы должны быть определены в управляемой сигнатуре, которая создается с помощью программы [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md).  
  
## См. также  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Default Marshaling for Arrays](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)