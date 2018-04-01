---
title: IDebugBinder::GetMemoryContext | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cb26d2a7cad34743fe877dd4cca23170a0f087a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Этот метод преобразует расположение объекта или адресе памяти в контексте памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описанием искомого объекта. Если `NULL`, затем с помощью `dwConstant` вместо него.  
  
 `dwConstant`  
 [in] Адрес памяти константы, например 0x5000.  
  
 `ppMemCxt`  
 [out] Возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, представляющий адрес объекта, или адрес в памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)