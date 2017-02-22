---
title: "Ошибка: время ожидания при отладке веб-служб | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "отладчик, ошибки веб-приложения"
  - "веб-службы XML, задержка при отладке"
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: время ожидания при отладке веб-служб
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При выполнении шага с заходом в веб\-службу XML из вызывающего кода в некоторых случаях может быть превышено время ожидания вызова, что не позволит продолжить отладку.  Может отобразиться сообщение наподобие того, что приведено ниже.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## Решение  
 Во избежание этой проблемы задайте бесконечное время ожидания вызова веб\-службы XML, как показано в следующем примере.  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## См. также  
 [Отладка веб\-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)