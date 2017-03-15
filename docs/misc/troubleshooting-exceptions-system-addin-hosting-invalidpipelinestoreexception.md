---
title: "Разрешение вопросов, связанных с исключениями: System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException - исключение"
  - "System.AddIn.Hosting.InvalidPipelineStoreException - исключение"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.AddIn.Hosting.InvalidPipelineStoreException
Исключение <xref:System.AddIn.Hosting.InvalidPipelineStoreException> генерируется, если каталог не найден, и у пользователя нет разрешения на доступ к корневому пути конвейера или пути к надстройке.  
  
## Примечания  
 В отличие от <xref:System.IO.DirectoryNotFoundException>, это исключение не передает какой\-либо информации о пути. Это мешает злоумышленникам намеренно указывать ошибочные пути и определять фактические пути, используя информацию, возвращаемую исключением.  
  
 Исключение генерируется следующими методами обнаружения, которые выполняют построение и обновление хранилища данных о надстройках и конвейерах: <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>, <xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Update%2A> и <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>.  
  
## См. также  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)