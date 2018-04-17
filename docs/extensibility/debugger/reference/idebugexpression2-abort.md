---
title: IDebugExpression2::Abort | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f4809fcf8e6947309182ff595ad2784b873f529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Этот метод отменяет асинхронное выражение вычисления начала работы с помощью вызова [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После отмены асинхронного выражения вычисления не отправляются [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) событий в обратный вызов события, передаваемый [присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) методы.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)