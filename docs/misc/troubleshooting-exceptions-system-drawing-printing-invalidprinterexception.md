---
title: "Разрешение вопросов, связанных с исключениями: System.Drawing.Printing.InvalidPrinterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "InvalidPrinterException - класс"
ms.assetid: e19b9b9c-2b0f-4839-85c0-ae75e1c356d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Drawing.Printing.InvalidPrinterException
Исключение <xref:System.Drawing.Printing.InvalidPrinterException> генерируется, когда предпринимается попытка доступа к принтеру с использованием недопустимых параметров принтера.  
  
## Полезные советы  
 **Убедитесь, что принтер существует.**  
 Наиболее распространенной причиной использования неправильных параметров принтера является ссылка на несуществующий принтер. Для получения дополнительной информации см. <xref:System.Drawing.Printing>.  
  
 **Убедитесь, что был установлен принтер по умолчанию.**  
 Если принтер не указан, обеспечьте, чтобы принтер по умолчанию был установлен. Дополнительные сведения см. в разделе <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>.  
  
## См. также  
 <xref:System.Drawing.Printing.InvalidPrinterException>   
 <xref:System.Drawing.Printing.PrinterSettings>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)