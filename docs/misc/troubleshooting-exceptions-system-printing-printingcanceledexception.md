---
title: "Разрешение вопросов, связанных с исключениями: System.Printing.PrintingCanceledException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrintingCanceledException - исключение"
  - "System.Printing.PrintingCanceledException - исключение"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Printing.PrintingCanceledException
Исключение <xref:System.Printing.PrintingCanceledException> возникает, когда код пытается обратиться к отмененному заданию печати.  
  
## Примечания  
 Не забудьте добавить код для обработки этого исключения при создании приложения Windows Presentation Foundation \(WPF\), включающего функцию печати и позволяющего отменять печать. Необработанное исключение данного типа может привести к зависанию приложения Windows Presentation Foundation.  
  
## См. также  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)