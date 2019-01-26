---
title: IDebugArrayObject::GetElements | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3aff1af823ceeb8a867cd6d4e3b5af3ddb7a1a37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55068723"
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
 [out] Возвращает [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) объект, который позволяет перечисление по всем элементам.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В качестве альтернативы использовать [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) и [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) методы для перебора элементов.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)