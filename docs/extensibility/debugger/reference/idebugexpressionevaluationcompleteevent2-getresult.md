---
title: "IDebugExpressionEvaluationCompleteEvent2::GetResult | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8950a69c5086616bc5f0b3177e5c6aa9aad9dfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Возвращает результат вычисления выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppResult`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результат вычисления выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Возвращенный [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект содержит значение вычисленного выражения. Обратите внимание, что это значение может быть сложное значение, например массива окончательный результат должен быть числовое или строковое значение, которое отображается для пользователя.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)