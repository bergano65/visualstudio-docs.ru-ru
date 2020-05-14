---
title: Процессы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738246"
---
# <a name="processes"></a>Процессы
В архитектуре отладчика *процесс:*

- Является контейнером для набора программ. Он тесно аналогин процессу Windows, который представляет собой контейнер для набора потоков.

- Может идентифицировать себя по имени, идентификатору или физическому идентификатору.

- Можно перечислить все запущенные программы (и их потоки).

- Может описать себя, порт он работает в, и машина, которая содержит его.

- Может создать одну или несколько программ, прекратить любую из создаваемых ею программ или привести к остановке программы.

- Представлен интерфейсом [IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) который создается при запуске процесса. Процесс запускается либо менеджером отладки сеанса (SDM), либо [LaunchSuspended.](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

  Пакет отладки может прикрепить движок отладки (DE) к процессу, позвонив [в Attach,](../../extensibility/debugger/reference/idebugprocess2-attach.md)что означает, что DE прикрепляется ко всем возможным программам, работающим в процессе, который он может обрабатывать. Например, если общий язык времени выполнения DE прикрепляется к процессу, он прикрепляется только к программам, которые работают управляемый код.

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Потоков](../../extensibility/debugger/threads.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [Пакет debug](../../extensibility/debugger/debug-package.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
