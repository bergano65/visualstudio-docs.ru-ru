---
title: Процессы | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37aa4436baa449e702d5cb6f76078b2bb36311fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571954"
---
# <a name="processes"></a>Процессы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [процессов](https://docs.microsoft.com/visualstudio/extensibility/debugger/processes).  
  
С точки зрения архитектуры отладчика **процесс**:  
  
-   — Это контейнер для набора программ. Он аналогичен тесно процесс Windows, который является контейнером для набор потоков.  
  
-   Можно идентифицировать себя, имя, идентификатор или идентификатор физического.  
  
-   Можно перечислить все выполняющиеся программы (и их потоки).  
  
-   Можно описать сам, порт, на котором он выполняется в и компьютера, на котором он содержится.  
  
-   Можно создать один или несколько программ, завершения любой из программ, которые оно создает или вызвать остановку программы.  
  
-   Представленный [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, который создается при запуске процесса. Процесс запускается диспетчером либо сеанса отладки (SDM) или [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Размер пакета отладки можно подключить отладчик (DE) к процессу путем вызова [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Это означает, что DE присоединяет все возможные программы, выполняющейся в процессе, он может обрабатывать. Например если среда CLR DE подключается к процессу, он присоединяет только для программ, работающих под управлением управляемого кода.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка пакета](../../extensibility/debugger/debug-package.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)

