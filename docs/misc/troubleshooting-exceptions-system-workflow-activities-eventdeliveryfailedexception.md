---
title: "Разрешение вопросов, связанных с исключениями: System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
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
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException - исключение"
  - "EventDeliveryFailedException - исключение"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Workflow.Activities.EventDeliveryFailedException
Исключение <xref:System.Workflow.Activities.EventDeliveryFailedException> возникает при невозможности доставки возникшего на узле события экземпляру рабочего процесса. Как правило, событие возникает из <xref:System.Workflow.Activities.ExternalDataExchangeService> на экземпляре рабочего процесса. Этот класс не наследуется.  
  
## Примечания  
 Следующая строка добавляется в журнал событий при этом исключении: `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`.  
  
 При использовании рабочего потока конечного компьютера, можно получить исключение с сообщением: `Queue '{0}' is not enabled`. Это происходит, когда текущее состояние конечного компьютера не может обработать определенное событие. Например, сообщение приходит, когда некоторое состояние, отличное от текущего, содержит <xref:System.Workflow.Activities.EventDrivenActivity>, которая содержит <xref:System.Workflow.Activities.HandleExternalEventActivity>, которая представлена очередью `'{0}'`.  
  
## См. также  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)