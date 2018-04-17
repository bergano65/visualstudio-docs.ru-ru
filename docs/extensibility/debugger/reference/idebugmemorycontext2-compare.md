---
title: IDebugMemoryContext2::Compare | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9c72120a4153ed6d0d19a2cf2b7d3a9a9943801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Сравнивает контекст памяти для каждого контекста в заданном массиве так, обозначенном флаги сравнения, возвращает индекс первого контекста, который соответствует.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compare`  
 [in] Значение из [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) перечисления, определяющее тип сравнения.  
  
 `rgpMemoryContextSet`  
 [in] Массив ссылок на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объектов для сравнения.  
  
 `dwMemoryContextSetLen`  
 [in] Число контекстов в `rgpMemoryContextSet` массива.  
  
 `pdwMemoryContext`  
 [out] Возвращает индекс первого контекст в памяти, который удовлетворяет условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_COMPARE_CANNOT_COMPARE` , если не удается сравнить двух контекстов.  
  
## <a name="remarks"></a>Примечания  
 Не поддерживает все типы сравнений модуля отладки (DE), но он должен поддерживать по крайней мере `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` и `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)