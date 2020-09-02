---
title: 'IDebugExpression2:: Abort | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8019d811f07373ba86059236013da645ff82c42a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163773"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод отменяет асинхронную оценку выражений, как это было начато вызовом метода [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 При отмене асинхронного вычисления выражения не отправляют событие [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) обратному вызову события, переданному методам [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
