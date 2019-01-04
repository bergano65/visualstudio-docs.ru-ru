---
title: IEnumDebugPortSuppliers2::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPortSuppliers2::Clone
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40e3f96ed4727dfb7b1ac40c263f22fd1acd6473
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916748"
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
Возвращает копию текущего перечисления как отдельный объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает копию этого перечисления как отдельный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Копия перечисления имеет то же состояние, что исходный во время вызова этого метода. Тем не менее копии и исходного состояния отделены и могут изменяться по отдельности.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)