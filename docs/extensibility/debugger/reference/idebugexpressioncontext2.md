---
title: IDebugExpressionContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 559115358910fe3445ab12000d1e113167c7da82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874184"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Этот интерфейс представляет контекст для вычисления выражений

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления контекста, в котором можно вычислить выражение.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызов [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает данный интерфейс. Этот интерфейс доступен только в том случае, когда был приостановлен отлаживаемой программы и доступен кадр стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExpressionContext2`.

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Извлекает имя в контекст оценки.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Выполняет синтаксический анализ текстового выражения для оценки.|

## <a name="remarks"></a>Примечания
 Контекст оценки может рассматриваться в качестве области действия для выполнения вычисления выражений.

 Когда программа остановлена, диспетчер отладки сеансов (SDM) получает кадр стека от DE вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем вызывает SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения `IDebugExpressionContext2` интерфейс. Затем следует вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, готовое к вычислению.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)