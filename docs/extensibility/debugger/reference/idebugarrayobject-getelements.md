---
title: "IDebugArrayObject::GetElements | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElements
helpviewer_keywords: IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60b267964b58dff8365ee6f769ee6b81f1bfb066
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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