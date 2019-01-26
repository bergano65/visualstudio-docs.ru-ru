---
title: IDebugMemoryContext2::Subtract | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53f919cb0c70d93c9888eb979846bc9b228c2e18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035358"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Вычитает указанное значение из текущего контекста и возвращает новый контекст.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCount`  
 [in] Число байтов памяти, чтобы уменьшить.  
  
 `ppMemCxt`  
 [out] Возвращает новый [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контекст памяти — это адрес, поэтому значение вычитается из адреса создает новый адрес, который требуется новый интерфейс контекста.  
  
 Этот метод всегда должен создавать новый контекст, даже если Итоговый адрес находится вне области памяти, связанный с данным контекстом. Единственное исключение — если недостаточно памяти, выделяемой для нового контекста или `ppMemCxt` имеет нулевое значение (который является ошибкой).  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)