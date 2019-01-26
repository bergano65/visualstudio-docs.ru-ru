---
title: IDebugStackFrame2::GetPhysicalStackRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fad5f1936312b91c69377064b17f844ba254f81a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009730"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Получает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.  
  
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
 [out] Возвращает наименьший физический адрес, связанный с данным кадром стека.  
  
 `paddrMax`  
 [out] Возвращает наибольший физический адрес, связанный с данным кадром стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые этим методом используется диспетчер отладки сеансов (SDM) для сортировки кадров стека.  
  
 Предполагается, что стек вызовов растет вниз, то есть, что с более низким адресами памяти добавляются новые кадры стека. Архитектура среды выполнения необходимо указать физический стек диапазоны, которые соответствуют это предположение.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)