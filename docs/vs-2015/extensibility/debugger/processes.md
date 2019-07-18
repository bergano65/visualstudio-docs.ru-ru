---
title: Процессы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153670"
---
# <a name="processes"></a>Процессы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

С точки зрения архитектуры отладчика **процесс**:  
  
- — Это контейнер для набора программ. Он аналогичен тесно процесс Windows, который является контейнером для набор потоков.  
  
- Можно идентифицировать себя, имя, идентификатор или идентификатор физического.  
  
- Можно перечислить все выполняющиеся программы (и их потоки).  
  
- Можно описать сам, порт, на котором он выполняется в и компьютера, на котором он содержится.  
  
- Можно создать один или несколько программ, завершения любой из программ, которые оно создает или вызвать остановку программы.  
  
- Представленный [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, который создается при запуске процесса. Процесс запускается диспетчером либо сеанса отладки (SDM) или [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
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
