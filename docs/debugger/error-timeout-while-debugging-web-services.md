---
title: "Ошибка: Время ожидания при отладке веб-служб | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd2a3847f8b356e6bac9c30336969a801e55710
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-timeout-while-debugging-web-services"></a>Ошибка: время ожидания при отладке веб-служб
При выполнении шага с заходом в веб-службу XML из вызывающего кода в некоторых случаях может быть превышено время ожидания вызова, что не позволит продолжить отладку. Может отобразиться сообщение наподобие того, что приведено ниже.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Решение  
 Во избежание этой проблемы задайте бесконечное время ожидания вызова веб-службы XML, как показано в следующем примере.  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)