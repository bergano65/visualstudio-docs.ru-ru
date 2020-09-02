---
title: 'IDebugStackFrame2:: Жетекспрессионконтекст | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7aea3543401faa1e7a6fd3ab2d3de073b5e6b3bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164736"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает контекст оценки для вычисления выражения в текущем контексте кадра стека и потока.  
  
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
 заполняет Возвращает объект [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) , представляющий контекст для вычисления выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Как правило, контекст вычисления выражения можно рассматривать как область для вычисления выражений. Вызовите метод [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , чтобы проанализировать выражение, а затем вызвать результирующие методы [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для вычисления проанализированного выражения.  
  
## <a name="see-also"></a>См. также:  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
