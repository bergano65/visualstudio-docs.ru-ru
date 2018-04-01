---
title: IDebugBinder::GetFunctionObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8c46de6a59e8ad0f5bba1b6b1c88b69681e74a2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Этот метод возвращает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, используемый для создания параметров функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppFunction`  
 [out] Возвращает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс, который используется для создания параметров функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)