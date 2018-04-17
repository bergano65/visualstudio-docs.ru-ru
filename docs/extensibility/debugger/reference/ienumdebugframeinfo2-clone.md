---
title: IEnumDebugFrameInfo2::Clone | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2::Clone
helpviewer_keywords:
- IEnumDebugFrameInfo2::Clone
ms.assetid: cdd10489-1772-47e3-815f-a6cfd32a3c60
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab9b334da3789960377794357ab119163a6d932d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugframeinfo2clone"></a>IEnumDebugFrameInfo2::Clone
Возвращает копию текущего перечисления в виде отдельного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Clone(  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugFrameInfo2 ppEnum  
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
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)