---
title: "Аргумент BasePath должен представлять собой путь к папке | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент BasePath должен представлять собой путь к папке
Аргумент `BasePath` должен содержать путь к папке. Возможно, строка была проанализирована неправильно и вы предоставили значение, не распознанное как допустимый путь.  
  
### Исправление ошибки  
  
-   Проверьте значение, указанное для `BasePath`, чтобы убедиться, что это допустимый путь к папке.  
  
## См. также  
 <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>   
 <xref:System.Resources.ResXResourceWriter.BasePath%2A>   
 <xref:System.Resources.ResXResourceReader.BasePath%2A>   
 [Практическое руководство. Анализ путей к файлам](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)