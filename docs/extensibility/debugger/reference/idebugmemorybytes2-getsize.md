---
title: IDebugMemoryBytes2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d8ac99883e2e7d25095a7a9f60eb5b5fe23c531
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007806"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Чтобы получить размер в байтах, памяти, представленный этим [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pqwSize`  
 [out] Возвращает размер в байтах памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)