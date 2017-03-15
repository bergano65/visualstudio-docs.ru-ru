---
title: "Разрешение вопросов, связанных с исключениями: System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException - класс"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.StrongTypingException
Исключение <xref:System.Data.StrongTypingException> возникает, когда пользователь обращается к значению <xref:System.DBNull> в типобезопасном <xref:System.Data.DataTable.DataSet%2A>.  
  
## Полезные советы  
 **Добавьте обработку StrongTypingException.**  
 Поместите код доступа к <xref:System.Data.DataTable.DataSet%2A> в блок `Try…Catch` и ловите <xref:System.Data.StrongTypingException>.  
  
## См. также  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Работа с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)