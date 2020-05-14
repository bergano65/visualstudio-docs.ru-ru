---
title: Обязательные интерфейсы поставщиков портов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713150"
---
# <a name="required-port-supplier-interfaces"></a>Необходимые интерфейсы портовых поставщиков
Поставщик порта должен реализовать интерфейс [IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Поставщик порта поставляет порты и реализует их. Таким образом, он должен работать следующие интерфейсы:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Описывает порт и перечисляет все процессы, работающие на порту.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Обеспечивает запуск и прекращение процессов в порту.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Обеспечивает механизм для программ, работающих в контексте этого порта, чтобы уведомить его о создании и разрушении узлов программы. Для получения дополнительной [Program nodes](../../extensibility/debugger/program-nodes.md)информации см.

- `IConnectionPointContainer`

  Обеспечивает точку соединения для [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Эксплуатация поставщика порта
 Поглотитель [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) получает уведомления при создании и уничтожении программ в порту. Порт обязан отправить [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) при создании процесса и [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) при уничтожении процесса в порту. Порт также обязан отправлять [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) при создании программы и [IDebugProgramDestroyEvent2,](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) когда программа будет уничтожена в процессе выполнения в порту.

 Порт обычно отправляет программы создавать и уничтожать события в ответ на методы [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) и [RemoveProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) соответственно.

 Поскольку порт может запускать и прекращать как физические процессы, так и логические программы, следующие интерфейсы также должны быть реализованы движком отладки:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Описывает физический процесс. По крайней мере, должны быть реализованы следующие методы:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Предоставляет возможность для SDM, чтобы прикрепить и отделить себя от процесса.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Описывает логическую программу. По крайней мере, должны быть реализованы следующие методы:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Предоставляет возможность для SDM, чтобы прикрепить к этой программе.

## <a name="see-also"></a>См. также
- [Внедрение поставщика портов](../../extensibility/debugger/implementing-a-port-supplier.md)
