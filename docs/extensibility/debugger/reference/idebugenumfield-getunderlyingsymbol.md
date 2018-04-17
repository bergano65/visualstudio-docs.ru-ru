---
title: IDebugEnumField::GetUnderlyingSymbol | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 150ac86dc78581655b0d6369dbe9c8c57c1a23f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Этот метод возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющее имя перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описывающую имя этого перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Имя перечисления также содержит тип перечисления, который связан с областью памяти с помощью [привязки](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md)