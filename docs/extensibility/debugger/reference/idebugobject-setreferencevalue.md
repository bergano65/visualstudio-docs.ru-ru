---
title: IDebugObject::SetReferenceValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e107408b27ffcbb057452030172a49d8027b422
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958414"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Задает значения этого объекта ссылки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект, представляющий новое значение ссылки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод выполняет это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ссылка на объект на значение объекта, указанного в `pObject` параметра, извлекайте любой предыдущей ссылке. Обратите внимание, это `IDebugObject` объект уже должен быть ссылочным типом.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)