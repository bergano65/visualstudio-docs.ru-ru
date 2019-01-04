---
title: IDebugMemoryContext2::Compare | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 86ba475aa9eab6b6cd878f9051e5851611955cf1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851181"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Сравнивает контекста памяти для каждого контекста в заданном массиве так, как указывает флаги сравнения, возвращает индекс первого контекста, который соответствует.  
  
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
 [in] Значение из [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) перечисление, определяющее тип сравнения.  
  
 `rgpMemoryContextSet`  
 [in] Массив ссылок на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объектов для сравнения.  
  
 `dwMemoryContextSetLen`  
 [in] Число контекстов в `rgpMemoryContextSet` массива.  
  
 `pdwMemoryContext`  
 [out] Возвращает индекс первого контекста памяти, который удовлетворяет условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_COMPARE_CANNOT_COMPARE` Если невозможно сравнить двух контекстах.  
  
## <a name="remarks"></a>Примечания  
 Для поддержки всех типов сравнений нет модуля отладки (DE), но он должен поддерживать по крайней мере `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` и `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)