---
title: IDebugПроцесс2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723799"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Этот интерфейс представляет собой процесс, работающий в порту. Если порт является локальным `IDebugProcess2` портом, то обычно представляет собой физический процесс на локальной машине.

## <a name="syntax"></a>Синтаксис

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован поставщиком пользовательских портов для управления программами как группы. Этот интерфейс должен быть реализован поставщиком порта.

 Отладка двигателя также реализует этот интерфейс, если он поддерживает запуск программы через [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс вызывается в первую очередь менеджером отладки сеанса (SDM) для взаимодействия с группой программ, определенных в этом процессе.

 Позвоните [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) или [GetProcess,](../../../extensibility/debugger/reference/idebugport2-getprocess.md) чтобы получить этот интерфейс. Этот интерфейс также возвращается по вызову `IDebugEngineLaunch2::LaunchSuspended`.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcess2`.

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Получает описание процесса.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, содержащиеся в этом процессе.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Получает название, дружеское имя или название файла процесса.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Получает экземпляр сервера машины, на который работает этот процесс.|
|[Завершить](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Прекращает процесс.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Прикрепляется к процессу.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, может ли SDM отсоединить процесс.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Отсеивайте отладчика от процесса.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Получает идентификатор системного процесса.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Получает глобально уникальный идентификатор для этого процесса.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> (УМОРИЛСЯ)|Получает название сеанса, который отладит процесс.<br /><br /> «УМОРИЛСЯ. ВСЕГДА ДОЛЖНЫ `E_NOTIMPL`ВОЗВРАЩАТЬСЯ.|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоки, работающие в процессе.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запросы о прекращении следующей программы, работая с кодом в этом процессе.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Получает порт, на который работает этот процесс.|

## <a name="remarks"></a>Примечания
 В `IDebugProcess2` интерфейсе IDebugProgram2 содержится один или несколько интерфейсов [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
