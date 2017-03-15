---
title: "Разрешение вопросов, связанных с исключениями: System.IO.PathTooLongException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "PathTooLongException - класс"
ms.assetid: 8912c425-bf91-42e3-82d8-bee6b2062db3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.PathTooLongException
Исключение <xref:System.IO.PathTooLongException> возникает, когда путь или имя файла длиннее, чем максимальная длина, определенная системой.  
  
## Полезные советы  
 **Убедитесь, что длина пути не превышает системное максимальное значение.**  
 Для платформ на основе Windows длина пути не должна превышать 248 знаков, а имена файлов — 260 знаков.  
  
## См. также  
 <xref:System.IO.PathTooLongException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Практическое руководство. Анализ путей к файлам](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)