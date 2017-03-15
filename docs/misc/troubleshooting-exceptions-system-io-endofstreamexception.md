---
title: "Разрешение вопросов, связанных с исключениями: System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "EndOfStreamException - класс"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.EndOfStreamException
Исключение <xref:System.IO.EndOfStreamException> возникает при попытке чтения за концом потока.  
  
## Полезные советы  
 **Проверьте, достигнут ли конец файла перед чтением.**  
 Используйте метод <xref:System.IO.StreamReader.Peek%2A> для проверки нахождения в конце файла до чтения из потока.  
  
## См. также  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Практическое руководство. Считывание из нового файла данных и запись в этот файл](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [Практическое руководство. Открытие файла журнала и добавление в него данных](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)