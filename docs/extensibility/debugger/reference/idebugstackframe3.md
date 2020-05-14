---
title: IDebugStackFrame3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719470"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Этот интерфейс расширяет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для обработки перехваченных исключений.

## <a name="syntax"></a>Синтаксис

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для поддержки перехваченных исключений.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` на интерфейс, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных от `IDebugStackFrame3` [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md)предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Ручки исключения для текущего кадра стека перед обычной обработкой исключений.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Возвращает контекст кода, если произошел стек.|

## <a name="remarks"></a>Примечания
 Перехваченное исключение означает, что отладчик может обработать исключение до того, как к времени выполнения будут вызваны любые обычные процедуры обработки исключений. Перехват исключения по существу означает, что время выполнения делает вид, что есть обработчик исключений, даже если нет.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) вызывается во время всех обычных событий обратного вызова исключения (единственное исключение, если вы отлаживаете код смешанного режима (управляемый и неуправляемый код), и в этом случае исключение не может быть перехвачено во время обратного вызова последнего шанса). Если DE не реализуется, `IDebugStackFrame3`или DE возвращает ошибку от IDebugStackFrame3::`InterceptCurrentException` `E_NOTIMPL`(например), то отладчик будет обрабатывать исключение нормально.

 Перехватив исключение, отладчик может позволить пользователю внести изменения в состояние отладки программы, а затем возобновить выполнение в точке, где было брошено исключение.

> [!NOTE]
> Перехваченные исключения допускаются только в управляемом коде, т.е. в программе, которая работает в рамках общего языкового runtime (CLR).

 Отладка двигателя указывает, что он поддерживает перехват исключений, установив "metricExceptions" `SetMetric` на значение 1 во время выполнения с помощью функции. Для получения дополнительной [SDK Helpers for Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)информации см.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
