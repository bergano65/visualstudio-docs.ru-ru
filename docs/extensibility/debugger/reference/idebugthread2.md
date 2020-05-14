---
title: IDebugThread2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718592"
---
# <a name="idebugthread2"></a>IDebugThread2
Этот интерфейс представляет собой поток, работающий в программе.

## <a name="syntax"></a>Синтаксис

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представлять поток выполнения в одной программе.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [GetThread,](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) чтобы получить этот интерфейс, представляющий в настоящее время активный поток.

 Этот интерфейс также используется при создании запроса на точку разрыва (см. [BP_REQUEST_INFO).](../../../extensibility/debugger/reference/bp-request-info.md)

 Этот интерфейс также возвращается при разрешении точки разрыва сопряжения или ошибки (см. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) и [BP_ERROR_RESOLUTION_INFO).](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugThread2`.

|Метод|Описание|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Извлекает список кадров стека для этого потока.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Возвращает имя потока.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Устанавливает название потока.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Получает программу, в которой выполняется поток.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Определяет, можно ли установить следующую выписку в данный кадр стека и контекст кода.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Устанавливает следующее утверждение в данный кадр стека и контекст кода.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Получает идентификатор системного потока.|
|[Приостановить](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Приостанавливает поток.|
|[Продолжить](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Возобновляет поток.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Получает свойства, описывающие поток.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Получает логический поток, связанный с этим физическим потоком.|

## <a name="remarks"></a>Примечания
 Поскольку один физический поток может работать `IDebugThread2` в нескольких программах, более чем одна из нескольких программ может представлять один и тот же физический поток.

 При возникновении точки разрыва или исключения событие отправляется по вызову [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Одним из аргументов для этого `IDebugThread2` метода является интерфейс, представляющий текущий поток. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) используется для получения интерфейса [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для текущего кадра стека.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
