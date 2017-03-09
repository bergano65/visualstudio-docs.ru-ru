---
title: "Разрешение вопросов, связанных с исключениями: System.IO.InternalBufferOverflowException | Microsoft Docs"
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
  - "InternalBufferOverflowException - класс"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.InternalBufferOverflowException
Исключение <xref:System.IO.InternalBufferOverflowException> возникает при переполнении внутреннего буфера.  
  
## Полезные советы  
 **При использовании FileSystemWatcher отфильтровывайте ненужные уведомления об изменениях.**  
 В FileSystemWatcher при получении уведомления об изменении файла система сохраняет эти изменения в буфере, который компонент создает и передает в различные прикладные программные интерфейсы приложений. Если за короткое время произошло большое количество изменений, буфер может переполниться, что приведет к исключению <xref:System.IO.InternalBufferOverflowException>, при котором все изменения будут потеряны. Чтобы буфер не переполнялся, для фильтрации ненужных уведомлений об изменениях следует использовать свойства <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> и <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A>. Для получения дополнительной информации см. <xref:System.IO.FileSystemWatcher>.  
  
## Примечания  
 С помощью свойства <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A> можно также увеличить размер внутреннего буфера. Однако увеличение размера буфера повлияет на производительность, поэтому лучше держать как можно меньший буфер.  
  
## См. также  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)