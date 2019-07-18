---
title: IDebugProcess2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bea73c1bce5367d9686e835bb58dd99a83cc818
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314130"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Этот интерфейс представляет процесс, работающий с портом. Если порт локального порта, затем `IDebugProcess2` обычно представляет физического процесса на локальном компьютере.

## <a name="syntax"></a>Синтаксис

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком пользовательский порт, для управления программами как группу. Этот интерфейс должен реализовываться поставщика порта.

 Модуль отладки также реализует этот интерфейс, если он поддерживает запуск программы через [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс называется главным образом диспетчер отладки сеансов (SDM) для взаимодействия с группой программы, указанные в этом процессе.

 Вызовите [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) или [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) для получения этого интерфейса. Этот интерфейс также возвращается путем вызова `IDebugEngineLaunch2::LaunchSuspended`.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcess2`.

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Возвращает описание процесса.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, которые содержатся в этом процессе.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Возвращает заголовок, понятное имя или имя файла процесса.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Получает экземпляр этого процесса, запущенного на машины Server.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Завершает процесс.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Присоединяет к процессу.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, если SDM можно отсоединить процесс.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Отсоединяет отладчик от процесса.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Получает системный идентификатор процесса.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Получает глобальный уникальный идентификатор для этого процесса.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [УСТАРЕЛО]|Получает имя сеанса, который является отладка процесса.<br /><br /> [УСТАРЕЛО. СЛЕДУЕТ ВСЕГДА ВОЗВРАЩАЮТ `E_NOTIMPL`.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоков, выполняемых в процессе.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запрашивает выполнение кода в этот процесс остановки следующей программы.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Получает порт, который выполняется этот процесс.|

## <a name="remarks"></a>Примечания
 `IDebugProcess2` Содержит один или несколько [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейсов.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)