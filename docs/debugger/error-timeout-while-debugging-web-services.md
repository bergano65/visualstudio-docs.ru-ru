---
title: 'Ошибка: истекло время ожидания при отладке веб-служб | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efb77689c33d263723f146f9b2484748505406b6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460277"
---
# <a name="error-timeout-while-debugging-web-services"></a>Ошибка: время ожидания при отладке веб-служб
При выполнении шага с заходом в веб-службу XML из вызывающего кода в некоторых случаях может быть превышено время ожидания вызова, что не позволит продолжить отладку. Может отобразиться сообщение наподобие того, что приведено ниже.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Решение
 Во избежание этой проблемы задайте бесконечное время ожидания вызова веб-службы XML, как показано в следующем примере.

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>См. также
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
