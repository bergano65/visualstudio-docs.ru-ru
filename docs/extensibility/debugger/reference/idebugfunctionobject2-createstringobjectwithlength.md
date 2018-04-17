---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01accfb86161880be3d155a0f1751ebd9ac0a5a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Создает объект string, имеющего указанную длину.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcstrString`  
 [in] Строковое значение для объекта string.  
  
 `uiLength`  
 [in] Длина строки в байтах.  
  
 `ppObject`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный строковый объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)