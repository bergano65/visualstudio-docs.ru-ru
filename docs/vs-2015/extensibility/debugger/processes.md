---
title: Процессы | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 6428b6cb3a3bedac6b1deae35fd2cd7f501d70f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809887"
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

