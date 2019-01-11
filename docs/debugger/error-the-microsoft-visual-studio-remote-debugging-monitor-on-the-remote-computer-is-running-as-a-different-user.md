---
title: 'Ошибка: На удаленном компьютере монитор удаленной отладки Microsoft Visual Studio выполняется в контексте другого пользователя'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d6d36844883b1acd51d169015a226d584c6c096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911303"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Ошибка: На удаленном компьютере монитор удаленной отладки Microsoft Visual Studio выполняется в контексте другого пользователя
При выполнении удаленной отладки может появиться следующее сообщение об ошибке:  
  
 На удаленном компьютере монитор удаленной отладки Microsoft Visual Studio выполняется в контексте другого пользователя.  
  
## <a name="cause"></a>Причина  
 Это сообщение появляется, если отладка выполняется в режиме "без аутентификации" и пользователь, запустивший msvsmon, не является пользователем, запустившим Visual Studio.  
  
## <a name="solution"></a>Решение  
 Лучшим и наиболее безопасным решением является запуск монитора удаленной отладки (msvsmon.exe) под учетной записью пользователя, запустившего Visual Studio. Если сделать это невозможно, можно запустить монитор удаленной отладки под другой учетной записью, выбрав параметр **Разрешить отладку любому пользователю** в диалоговом окне **Параметры** монитора удаленной отладки.  
  
> [!CAUTION]
>  Предоставление другим пользователям разрешения на подключение допускает вероятность случайного подключения к неправильному сеансу удаленной отладки. Отладка в режиме **Без аутентификации** никогда не является безопасной, и ее следует использовать с осторожностью.
  
## <a name="see-also"></a>См. также раздел  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)