---
title: "Разрешение вопросов, связанных с исключениями: System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException - класс"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Net.HttpListenerException
Исключение <xref:System.Net.HttpListenerException> возникает при ошибке обработки HTTP\-запроса.  
  
## Полезные советы  
 Убедитесь в отсутствии попыток зарегистрировать уже зарегистрированный префикс URI.  
 Если префикс URI уже зарегистрирован, то данное исключение произойдет.  
  
 Убедитесь в правильности запроса HTTP.  
 Это исключение вызывается классом <xref:System.Net.HttpListener> и связанными с ним классами при возникновении ошибки во время инициализации <xref:System.Net.HttpListener> или во время создания или отправки ответа на запрос HTTP.  
  
 Если используется метод `HttpListenerPrefixCollection.Add`, убедитесь, что `uriPrefix` ещё не был добавлен.  
 Это исключение будет вызвано, если другой <xref:System.Net.HttpListener> уже добавил префикс `uriPrefix`.  
  
## См. также  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)