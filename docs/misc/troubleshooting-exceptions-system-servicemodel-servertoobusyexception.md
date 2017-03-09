---
title: "Разрешение вопросов, связанных с исключениями: System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException - исключение"
  - "ServerTooBusyException - исключение"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.ServiceModel.ServerTooBusyException
Исключение <xref:System.ServiceModel.ServerTooBusyException> возникает, когда сервер слишком занят, чтобы принять сообщение.  
  
## Примечания  
 Это исключение является наследником <xref:System.ServiceModel.CommunicationException>, представляющего класс восстановимых ошибок, которые могут случиться во время обмена данными между конечными точками. Надежные клиенты и службы приложений [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], предположительно, способны обработать эти исключения. Чтобы предотвратить перехват обработчиком более общего <xref:System.ServiceModel.CommunicationException> более конкретного <xref:System.ServiceModel.ServerTooBusyException>, перехватывайте это исключение до обработки <xref:System.ServiceModel.CommunicationException>.  
  
## См. также  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)