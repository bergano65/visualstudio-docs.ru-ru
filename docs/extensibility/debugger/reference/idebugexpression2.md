---
title: IDebugExpression2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114642"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Этот интерфейс представляет проанализированное выражение все готово для привязки и оценки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления выражения проанализированный готовое к вычислению.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) возвращает этот интерфейс. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса. Эти интерфейсы доступны только в том случае, если была приостановлена отлаживаемой программы и кадр стека не доступен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExpression2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет это выражение.|  
|[Прерывание](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет это выражение в синхронном режиме.|  
  
## <a name="remarks"></a>Примечания  
 Если программа остановлена, диспетчера сеанса отладки (SDM) получает кадра стека из DE вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем вызывает SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса. После этого идет путем вызова [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания `IDebugExpression2` интерфейс, который представляет проанализированное выражение, готовое к вычислению.  
  
 SDM вызывает метод [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для фактического вычислить выражение и получения значения.  
  
 В реализации `IDebugExpressionContext2::ParseText`, DE использует COM `CoCreateInstance` функции для создания экземпляра вычислитель выражений и получить [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейса (см. пример в `IDebugExpressionEvaluator` интерфейс). Затем вызывает DE [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейса. Этот интерфейс используется в реализации `IDebugExpression2::EvaluateSync` и `IDebugExpression2::EvaluateAsync` для выполнения вычисления.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)