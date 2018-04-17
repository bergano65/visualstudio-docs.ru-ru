---
title: IDebugObject::GetManagedDebugObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c7b416ca9af4279e11cabbbf880a73891059df6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Создает копию объекта управляемого объекта в адресном пространстве ядро отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppObject`  
 [out] Возвращает [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объект, представляющий только что созданный управляемого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки. Возвращает значение E_FAIL, если этот [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр класса управляемого значения.  
  
## <a name="remarks"></a>Примечания  
 Это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект должен представлять экземпляр класса управляемого значения `System.Decimal` экземпляра. При наличии локальной копии издержки, связанные с вызовом [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключается.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)