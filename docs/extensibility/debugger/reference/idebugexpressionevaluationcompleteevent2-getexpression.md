---
title: IDebugExpressionEvaluationCompleteEvent2::GetExpression | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 96157885fa37edc9216086359a898e5191ce2444
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
Получает исходное выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExpression(   
   IDebugExpression2** ppExpr  
);  
```  
  
```csharp  
int GetExpression(   
   out IDebugExpression2 ppExpr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppExpr`  
 [out] Возвращает [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , представляющий выражение, которое было проанализировано.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает объект, который был создан при обращении к [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)