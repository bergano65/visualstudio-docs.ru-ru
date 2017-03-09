---
title: "Разрешение вопросов, связанных с исключениями: System.Windows.Xps.XpsWriterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException - исключение"
  - "XpsWriterException - исключение"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Windows.Xps.XpsWriterException
Исключение <xref:System.Windows.Xps.XpsWriterException> вызывается, если вызван метод объекта <xref:System.Windows.Xps.XpsDocumentWriter> или <xref:System.Windows.Xps.VisualsToXpsDocument>, несовместимый с текущим состоянием объекта.  
  
## Примечания  
 Например, это исключение вызывается при вызове метода `CancelAsync` любого из этих двух объектов, если объект не выполняет асинхронную операцию записи.  
  
## См. также  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)