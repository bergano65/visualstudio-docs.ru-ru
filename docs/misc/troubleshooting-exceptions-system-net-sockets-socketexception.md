---
title: "Разрешение вопросов, связанных с исключениями: System.Net.Sockets.SocketException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "SocketException - класс"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Net.Sockets.SocketException
Исключение <xref:System.Net.Sockets.SocketException> вызывается классами <xref:System.Net.Sockets.Socket> и <xref:System.Net.Dns> при возникновении сетевой ошибки.  
  
## Полезные советы  
 **Проверьте свойство ErrorCode для определения причины возникновения ошибки сокета.**  
 Конструктор по умолчанию для класса <xref:System.Net.Sockets.SocketException> устанавливает для свойства <xref:System.Net.Sockets.SocketException.ErrorCode%2A> значение, отражающее последнюю ошибку сокета операционной системы.  
  
## См. также  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Использование протокола SSL](../Topic/Using%20Secure%20Sockets%20Layer.md)