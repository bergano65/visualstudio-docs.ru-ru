---
title: "Разрешение вопросов, связанных с исключениями: System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException - исключение"
  - "System.Workflow.Runtime.Hosting.PersistenceException - исключение"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Workflow.Runtime.Hosting.PersistenceException
Исключение <xref:System.Workflow.Runtime.Hosting.PersistenceException> генерируется, если служба постоянного хранения не может выполнить запрос.  
  
## Примечания  
 Служба <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> генерирует исключение <xref:System.Workflow.Runtime.Hosting.PersistenceException>, если она не может выполнить запрос на фиксацию обновления в базе данных, относящийся либо к завершенному контексту, либо к состоянию экземпляра потока работ.  
  
 Если служба сохранения реализована путем наследования от класса <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> или класса <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, можно генерировать исключение <xref:System.Workflow.Runtime.Hosting.PersistenceException> с соответствующим сообщением с целью оповещения о любой ошибке, которая не позволяет службе выполнить запрос, поступивший из среды выполнения потоков работ.  
  
 Дополнительные сведения см. в разделе <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>.  
  
## См. также  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)