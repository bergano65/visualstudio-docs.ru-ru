---
title: "IDebugDisassemblyStream2::GetCurrentLocation | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords: IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee82866b4938faaa14e591a2ac11c5e23bf2ab99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Возвращает идентификатор расположение кода, который представляет текущего расположения в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCurrentLocation(   
   UINT64* puCodeLocationId  
);  
```  
  
```csharp  
int GetCurrentLocation(   
   out ulong puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `puCodeLocationId`  
 [out] Возвращает идентификатор расположение кода. В разделе «Примечания» [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) метод описание идентификатора расположение в коде.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор расположение кода можно преобразовать в контекст кода путем вызова [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)