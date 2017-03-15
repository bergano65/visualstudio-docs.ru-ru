---
title: "Разрешение вопросов, связанных с исключениями: System.DuplicateWaitObjectException | Microsoft Docs"
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
  - "DuplicateWaitObjectException - класс"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.DuplicateWaitObjectException
Исключение <xref:System.DuplicateWaitObjectException> генерируется, если в массиве объектов <xref:System.Threading.WaitHandle>, переданном в <xref:System.Threading.WaitHandle.WaitAll%2A> или в <xref:System.Threading.WaitHandle.WaitAny%2A>, имеются повторяющиеся дескрипторы операционной системы.  
  
## Полезные советы  
 **Убедитесь, что объекты WaitHandle, передаваемые в WaitAll или в WaitAny, являются уникальными.**  
 Массив <xref:System.Threading.WaitHandle> не может содержать несколько ссылок на один и тот же объект.  
  
### Примечания  
 Общеязыковая среда выполнения \(среда CLR\) предоставляет механизм синхронизации потоков, основанный на использовании синхронизационных объектов, ожидающих выполнения в массиве объектов <xref:System.Threading.WaitHandle> .  
  
## См. также  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)