---
title: "Разрешение вопросов, связанных с исключениями: System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
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
  - "InstanceNotFoundException - исключение"
  - "System.ServiceModel.Persistence.InstanceNotFoundException - исключение"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.ServiceModel.Persistence.InstanceNotFoundException
Исключение <xref:System.ServiceModel.Persistence.InstanceNotFoundException> генерируется при следующих обстоятельствах:  
  
-   Операция, выполняется на экземпляре длительного обслуживания, который был помечен для завершения,  
  
-   Постоянный поставщик созданный <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> пытается заблокировать, разблокировать процесс, либо иначе обработать данные о состоянии, которые не найдены в базе данных.  
  
## См. также  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)