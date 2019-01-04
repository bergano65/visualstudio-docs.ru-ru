---
title: IDebugExpression2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d493da63aaac406ea1fef0f33abbcef528ead61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866992"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Этот интерфейс представляет проанализированное выражение готовой для привязки и оценки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, представляющий проанализированное выражение, готовое к вычислению.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) возвращает этот интерфейс. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс. Эти интерфейсы доступны только в том случае, когда был приостановлен отлаживаемой программы и доступен кадр стека.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExpression2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет это выражение.|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет это выражение синхронно.|  
  
## <a name="remarks"></a>Примечания  
 Когда программа остановлена, диспетчер отладки сеансов (SDM) получает кадр стека от DE вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем вызывает SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс. Затем следует вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания `IDebugExpression2` интерфейс, который представляет проанализированное выражение, готовое к вычислению.  
  
 Голосовой звонок SDM [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для фактически вычислит значение выражения и получения значения.  
  
 В реализации `IDebugExpressionContext2::ParseText`, DE использует COM `CoCreateInstance` функции для создания экземпляра вычислитель выражений и получить [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейса (см. пример в `IDebugExpressionEvaluator` интерфейс). Затем вызывает DE [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейс. Этот интерфейс используется в реализации `IDebugExpression2::EvaluateSync` и `IDebugExpression2::EvaluateAsync` для выполнения оценки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)