---
title: IDebugExpression2::Abort | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 94cbeaa3231f06d70d8e9f70193ccb48cbd49b5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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