---
title: "Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "ServiceBusyException - исключение"
  - "System.IdentityModel.Selectors.ServiceBusyException - исключение"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.ServiceBusyException
Исключение <xref:System.IdentityModel.Selectors.ServiceBusyException> вызывается, чтобы показать, что служба CardSpace занята обработкой других запросов. CardSpace не ставит запросы в очередь и может обслуживать только один запрос единовременно.  
  
 Проверьте, не выполняется ли другой экземпляр CardSpace. Если он выполняется, завершите его, остановив процесс icardagt.exe из диспетчера задач.  
  
## См. также  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)