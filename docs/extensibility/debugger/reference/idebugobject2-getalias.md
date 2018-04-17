---
title: IDebugObject2::GetAlias | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5917e0f78a2872cbd684830c8a03b1156a83734
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Получает псевдоним, связанный с этим объектом, если таковая имеется.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppAlias`  
 [out] Возвращает [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) объект, представляющий псевдоним для этого объекта; в противном случае возвращает значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Псевдоним для объекта создается с помощью вызова [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)