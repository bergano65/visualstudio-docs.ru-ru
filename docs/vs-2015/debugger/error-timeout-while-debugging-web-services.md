---
title: 'Ошибка: Время ожидания при отладке веб-служб | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568595"
---
# <a name="error-timeout-while-debugging-web-services"></a>Ошибка: время ожидания при отладке веб-служб
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: Timeout While Debugging Web Services](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
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



