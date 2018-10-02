---
title: IDebugMemoryContext2::Compare | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4219994deb0490533207907d809e970d0fb303cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559814"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugMemoryContext2::Compare](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2-compare).  
  
Сравнивает контекста памяти для каждого контекста в заданном массиве так, как указывает флаги сравнения, возвращает индекс первого контекста, который соответствует.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

