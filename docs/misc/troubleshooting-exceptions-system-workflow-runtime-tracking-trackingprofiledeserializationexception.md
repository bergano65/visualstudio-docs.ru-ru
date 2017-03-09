---
title: "Разрешение вопросов, связанных с исключениями: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException - исключение"
  - "TrackingProfileDeserializationException - исключение"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
Исключение <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> генерируется, если невозможна десериализация XML\-документа в <xref:System.Workflow.Runtime.Tracking.TrackingProfile> с помощью <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer>.  
  
## Примечания  
 При создании этого исключения <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> передает сообщение с описанием его причин. В некоторых случаях <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> предоставляет список ошибок и предупреждений проверки, которые были получены при попытке десериализации <xref:System.Workflow.Runtime.Tracking.TrackingProfile>. Если такой список предоставляется, то он хранится в свойстве <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A>.  
  
## См. также  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)