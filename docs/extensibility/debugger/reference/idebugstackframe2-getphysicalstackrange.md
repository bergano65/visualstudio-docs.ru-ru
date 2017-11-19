---
title: "IDebugStackFrame2::GetPhysicalStackRange | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords: IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b57cc7b5959f82b5f02c4939d6645c30c1c706
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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