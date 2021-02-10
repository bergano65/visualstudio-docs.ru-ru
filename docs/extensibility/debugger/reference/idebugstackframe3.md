---
title: IDebugStackFrame3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5511624fb69015351d8cc37d6b27ad142a5956d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961187"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Этот интерфейс расширяет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для управления перехваченными исключениями.

## <a name="syntax"></a>Синтаксис

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для того же объекта, который реализует интерфейс [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для поддержки перехваченных исключений.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) для `IDebugStackFrame2` интерфейса, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Обрабатывает исключение для текущего кадра стека перед обработкой регулярных исключений.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Возвращает контекст кода, если была выполнена очистка стека.|

## <a name="remarks"></a>Remarks
 Перехваченное исключение означает, что отладчик может обработать исключение до того, как все обычные процедуры обработки исключений вызываются во время выполнения. Перехват исключения по сути означает, что время выполнения представляет собой обработчик исключений, даже если нет.

- [Интерцепткуррентексцептион](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) вызывается во время всех обычных событий обратного вызова исключений (Единственное исключение — при отладке кода в смешанном режиме (управляемый и неуправляемый код). в этом случае исключение не может быть перехвачено во время последнего обратного вызова. Если метод DE не реализуется `IDebugStackFrame3` или метод de возвращает ошибку из IDebugStackFrame3:: `InterceptCurrentException` (например `E_NOTIMPL` ,), отладчик будет выполнять обработку исключения обычным образом.

 Перехватывая исключение, отладчик может разрешить пользователю вносить изменения в состояние отлаживаемой программы, а затем возобновлять выполнение в момент возникновения исключения.

> [!NOTE]
> Перехваченные исключения разрешены только в управляемом коде, то есть в программе, которая выполняется в среде CLR.

 Модуль отладки указывает, что он поддерживает перехват исключений, присвоив параметру "Метрицексцептионс" значение 1 во время выполнения с помощью `SetMetric` функции. Дополнительные сведения см. в разделе [вспомогательные методы SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
