---
title: IDebugArrayField::GetElementType | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 46a2a3066a84c78d08e07fab0c7da394acd2bb64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Получает тип элемента в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppType`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта, который описывает тип элемента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) объекта предполагает, что все элементы массива относятся к одному типу.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)