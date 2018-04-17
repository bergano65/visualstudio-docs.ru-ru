---
title: IEnumDebugPropertyInfo2::Clone | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f8d47d9d90d0fc380a409083ad0025751ab2091
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
Возвращает копию текущего перечисления в виде отдельного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает копию этого перечисления в виде отдельного объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Копия перечисления имеет том же состоянии, что и исходный во время вызова этого метода. Тем не менее копирования и исходного состояния отделены и могут изменяться по отдельности.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)