---
title: IEnumDebugFields::GetCount | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0143685e5e959b36c6d4bdcb9cc122fc7d7db10
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Этот метод возвращает количество элементов в перечислении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 [out] Возвращает число элементов в перечислении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является частью обычной COM-интерфейс перечисления которого указывает, что только Далее, клонирования, Skip и сброса необходимо реализовать.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)