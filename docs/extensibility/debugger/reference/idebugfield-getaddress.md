---
title: IDebugField::GetAddress | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6e43d7540ad48eac1ff8603ef41b38f8d247ae0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Этот метод возвращает адрес отладки поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppAddress`  
 [out] Возвращает адрес как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)