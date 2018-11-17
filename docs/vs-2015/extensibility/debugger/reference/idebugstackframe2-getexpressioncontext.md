---
title: IDebugStackFrame2::GetExpressionContext | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96671c364703faa9bb70cf44e5df6e9d21c9dcfa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726584"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает контекст вычисления для оценки выражения в контексте текущего кадра стека и потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppExprCxt`  
 [out] Возвращает [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) объект, представляющий контекст для вычисления выражений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило контекст вычисления выражения могут рассматриваться как область для выполнения вычисления выражений. Вызовите [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метода для синтаксического разбора выражения, а затем вызвать итоговый [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) методы для оценки проанализированное выражение.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

