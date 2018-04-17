---
title: IDebugStackFrame2::GetPhysicalStackRange | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be53b50bc21d81c60f7131e8ed437ecb2ac2f16c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Возвращает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `paddrMin`  
 [out] Возвращает наименьшее физический адрес, связанный с данным кадром стека.  
  
 `paddrMax`  
 [out] Возвращает наибольший физический адрес, связанный с данным кадром стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые этим методом используется диспетчером сеанса отладки (SDM), чтобы отсортировать кадры стека.  
  
 Предполагается, что стек вызовов увеличился вниз, то есть, что добавлены новые кадры стека во все более младших адресов памяти. Архитектура среды выполнения необходимо указать физический стек диапазоны, соответствующие это предположение.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)