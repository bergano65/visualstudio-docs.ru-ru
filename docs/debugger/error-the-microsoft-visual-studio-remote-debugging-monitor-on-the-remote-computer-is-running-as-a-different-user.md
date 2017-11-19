---
title: "Ошибка: Монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере запущен от имени другого пользователя | Документы Microsoft"
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
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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