---
title: "Разрешение вопросов, связанных с исключениями: System.Threading.SynchronizationLockException | Microsoft Docs"
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
  - "SynchronizationLockException - исключение"
  - "System.Threading.SynchronizationLockException - исключение"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Threading.SynchronizationLockException
Исключение возникает, если метод требует владения вызвавшим его потоком определенного `Monitor`, но поток им не владеет.  
  
## Примечания  
 Исключение <xref:System.Threading.SynchronizationLockException> вызывается путем вызова методов <xref:System.Threading.Monitor.Exit%2A>, <xref:System.Threading.Monitor.Pulse%2A>, <xref:System.Threading.Monitor.PulseAll%2A> и <xref:System.Threading.Monitor.Wait%2A> класса `Monitor` из несинхронизированного блока кода.  
  
## См. также  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)