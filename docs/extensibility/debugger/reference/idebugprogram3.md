---
title: IDebugПрограмма3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722646"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Этот интерфейс представляет собой программу, которая работает в процессе и расширяет [выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md) путем предоставления информации о потоке.

## <a name="syntax"></a>Синтаксис

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) и поставщик пользовательских портов реализуют этот интерфейс, чтобы представлять программу в процессе. Менеджер отладки сеанса (SDM) также реализует этот интерфейс для предоставления информации [для присоединения.](../../../extensibility/debugger/reference/idebugprogram2-attach.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 [Событие IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов на нескольких интерфейсах.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgram3`.

|Метод|Описание|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Выполняет программу. Поток возвращается, чтобы дать отладчику информацию о том, какой поток просматривает пользователь при выполнения.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Примечания
 Программа — это контейнер потоков, работающий в определенной архитектуре времени выполнения, в то время как процесс состоит из одной или нескольких программ.

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
