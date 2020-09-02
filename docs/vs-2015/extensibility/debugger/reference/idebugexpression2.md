---
title: IDebugExpression2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568373"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет проанализированное выражение, готовое для привязки и вычисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы представить проанализированное выражение, готовое для оценки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) возвращает этот интерфейс. [Жетекспрессионконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает интерфейс [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Эти интерфейсы доступны только в том случае, если отлаживаемая программа приостановлена и доступен кадр стека.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExpression2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет это выражение.|  
|[Рвал](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает вычисление асинхронного выражения.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Синхронно вычисляет это выражение.|  
  
## <a name="remarks"></a>Remarks  
 При остановке программы Диспетчер отладки сеансов (SDM) получает кадр стека от DE к вызову [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем SDM вызывает [жетекспрессионконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения интерфейса [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . За этим следует вызов [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания `IDebugExpression2` интерфейса, который представляет проанализированное выражение, готовое к оценке.  
  
 Модель SDM вызывает либо [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , либо [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , чтобы фактически вычислить выражение и получить значение.  
  
 В реализации `IDebugExpressionContext2::ParseText` функция de использует COM- `CoCreateInstance` функцию для создания экземпляра средства оценки выражений и получения интерфейса [идебужекспрессионевалуатор](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (см. пример в `IDebugExpressionEvaluator` интерфейсе). Затем метод DE вызывает [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения интерфейса [идебугпарседекспрессион](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Этот интерфейс используется в реализации `IDebugExpression2::EvaluateSync` и `IDebugExpression2::EvaluateAsync` для выполнения оценки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
