---
title: IDebugStackКадр2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719511"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Этот интерфейс представляет собой единый кадр стека в стеке вызовов в определенном потоке.

## <a name="syntax"></a>Синтаксис

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс для представления кадра стека.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [EnumFrameInfo,](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) чтобы получить интерфейс [IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Call [Далее,](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) чтобы получить структуру `IDebugStackFrame2` [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) которая содержит интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugStackFrame2`.

|Метод|Описание|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Получает контекст кода для этого кадра стека.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Получает контекст документа для этого кадра стека.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Получает название кадра стека.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Получает описание кадра стека.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Получает машино-зависимое представление диапазона физических адресов, связанных с кадром стека.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Получает контекст оценки для выполнения оценки выражения в текущем контексте кадра стека и потока.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Получает язык, связанный с кадром стека.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Получает описание свойств, связанных с кадром стека.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Создает регистратор для свойств стек кадра.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Получает поток, связанный с кадром стека.|

## <a name="remarks"></a>Примечания
 Этот интерфейс получается только тогда, когда отладка программы была остановлена в точке разрыва (либо вызвана точкой разрыва, установленной пользователем, либо исключением). Из этого интерфейса можно получить контекст выражения для оценки выражений, список регистров может быть возвращен или стек вызовов может быть получен и изучен.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
