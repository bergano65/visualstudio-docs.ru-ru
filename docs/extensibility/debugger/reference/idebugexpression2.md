---
title: IDebugExpression2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729690"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Этот интерфейс представляет собой разогнанные выражения, готовые к связыванию и оценке.

## <a name="syntax"></a>Синтаксис

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить разогнанные выражения, готовые к оценке.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок в [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) возвращает этот интерфейс. [GetExpressionExpression возвращает](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) интерфейс [IDebugExpressionExpression2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Эти интерфейсы доступны только тогда, когда отладка программы приостановлена и доступна рамка стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExpression2`.

|Метод|Описание|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Оценивает это выражение асинхронно.|
|[Прервать](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Окончание асинхронной оценки выражения.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Оценивает это выражение синхронно.|

## <a name="remarks"></a>Примечания
 Когда программа остановлена, диспетчер отладки сеанса (SDM) получает кадр стека из DE с вызовом на [EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Затем SDM вызывает [GetExpressionContext,](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) чтобы получить интерфейс [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) За этим следует призыв к [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) создать `IDebugExpression2` интерфейс, который представляет собой разображенные выражения готовы к оценке.

 SDM вызывает или [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) фактически оценить выражение и произвести значение.

 `IDebugExpressionContext2::ParseText`В реализации, DE использует `CoCreateInstance` функцию COM, чтобы мгновенно оценить выражение и получить интерфейс [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (см. пример в интерфейсе). `IDebugExpressionEvaluator` DE затем вызывает [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для того чтобы получить интерфейс [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Этот интерфейс используется в `IDebugExpression2::EvaluateSync` реализации и `IDebugExpression2::EvaluateAsync` для выполнения оценки.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
