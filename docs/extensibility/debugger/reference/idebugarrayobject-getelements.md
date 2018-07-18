---
title: IDebugArrayObject::GetElements | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae1d22af6796c2de72c763137c8f96feb7885407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099819"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Получает перечислитель всех элементов массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) объектом, который позволяет перечисление всех элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В качестве альтернативы используйте [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) и [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) методы для перебора элементов.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)