---
title: 'Ошибка: Монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере запущен от имени другого пользователя | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
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
ms.openlocfilehash: aefcb3f358d6dc22b7ea8bcca1c43e79cd9c4414
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Ошибка: монитор удаленной отладки Visual Studio на удаленном компьютере запущен от имени другого пользователя
При выполнении удаленной отладки может появиться следующее сообщение об ошибке:  
  
 На удаленном компьютере монитор удаленной отладки Microsoft Visual Studio выполняется в контексте другого пользователя.  
  
## <a name="cause"></a>Причина  
 Это сообщение появляется, если отладка выполняется в режиме "без аутентификации" и пользователь, запустивший msvsmon, не является пользователем, запустившим Visual Studio.  
  
## <a name="solution"></a>Решение  
 Лучшим и наиболее безопасным решением является запуск монитора удаленной отладки (msvsmon.exe) под учетной записью пользователя, запустившего Visual Studio. Если сделать это невозможно, можно запустить монитор удаленной отладки под другой учетной записью с **разрешить отладку любому пользователю** параметром, выбранным в монитор удаленной отладки **параметры** диалоговое окно.  
  
> [!CAUTION]
>  Предоставление другим пользователям разрешения на подключение допускает вероятность случайного подключения к неправильному сеансу удаленной отладки. Отладка в **без проверки подлинности** режим, никогда не является безопасным и должен использоваться с осторожностью.
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)