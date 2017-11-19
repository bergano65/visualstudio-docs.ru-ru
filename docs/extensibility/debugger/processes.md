---
title: "Процессы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f295dd93580caee4b6288febf7e83c09736b6080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="processes"></a>Процессы
С точки зрения архитектуры отладчик **процесса**:  
  
-   — Это контейнер для набора программ. Он аналогичен тесно процесс Windows, который является контейнером для набора потоков.  
  
-   Могут идентифицироваться по имени, идентификатора или физических идентификатор.  
  
-   Можно перечислить все выполняющиеся программы (и их потоков).  
  
-   Можно описать сам, выполняемых в порт и компьютера, на котором он содержится.  
  
-   Можно создать одну или несколько программ, завершение программы, создаваемые им или вызвать программу остановить.  
  
-   Представленный [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, который создается при запуске процесса. Процесс запускается диспетчером либо сеанса отладки (SDM) или [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Отладочный пакет можно присоединить отладчик (DE) к процессу путем вызова [присоединение](../../extensibility/debugger/reference/idebugprocess2-attach.md). Это означает, что DE присоединяет выполняются в процессе, он может обрабатывать все возможные программы. Например если общеязыковая среда выполнения DE подключается к процессу, он присоединяет только для программ, выполняемых в управляемом коде.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка пакета](../../extensibility/debugger/debug-package.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)