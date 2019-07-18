---
title: Процессы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c45fc70fe61c7221a8042d275dd44d69eb5d11e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351500"
---
# <a name="processes"></a>Процессы
В архитектуре отладчик *процесс*:

- — Это контейнер для набора программ. Он аналогичен тесно процесс Windows, который является контейнером для набор потоков.

- Можно идентифицировать себя, имя, идентификатор или идентификатор физического.

- Можно перечислить все выполняющиеся программы (и их потоки).

- Можно описать сам, порт, на котором он выполняется в и компьютера, на котором он содержится.

- Можно создать один или несколько программ, завершения любой из программ, которые оно создает или вызвать остановку программы.

- Представленный [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, который создается при запуске процесса. Процесс запускается диспетчером либо сеанса отладки (SDM) или [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Размер пакета отладки можно подключить отладчик (DE) к процессу путем вызова [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), что означает, что DE присоединяет все возможные программы, выполняющейся в процессе, он может обрабатывать. Например если среда CLR DE подключается к процессу, он присоединяет только для программ, работающих под управлением управляемого кода.

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Потоки](../../extensibility/debugger/threads.md)
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [Отладка пакета](../../extensibility/debugger/debug-package.md)
- [Отладка ядра](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)