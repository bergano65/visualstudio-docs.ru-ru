---
title: "Разрешение вопросов, связанных с исключениями: System.Data.ReadOnlyException | Microsoft Docs"
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
  - "ReadOnlyException - класс"
ms.assetid: 1ac5da38-c5af-4fec-8fe1-1b9dd5069e59
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.ReadOnlyException
Исключение <xref:System.Data.ReadOnlyException> возникает при попытке изменить значение столбца, данные в котором только для чтения.  
  
## Полезные советы  
 **Откройте доступ к столбцу на чтение и запись.**  
 Это исключение вызывается при попытке изменить значение в столбце данных, доступном только для чтения. Для получения дополнительной информации см. <xref:System.Data.DataColumn>.  
  
 **Убедитесь, что данные изменяются в правильном столбце.**  
 Это исключение вызывается при попытке изменить значение в столбце данных, доступном только для чтения. Дополнительные сведения см. в разделе <xref:System.Data.DataColumn>.  
  
## См. также  
 <xref:System.Data.ReadOnlyException>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)