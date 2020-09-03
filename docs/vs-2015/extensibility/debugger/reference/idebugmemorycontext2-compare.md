---
title: 'IDebugMemoryContext2:: Compare | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163429"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Сравнивает контекст памяти с каждым контекстом в заданном массиве способом, указанным в параметре Compare flags, и возвращает индекс первого соответствующего контекста.  
  
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
 окне Значение из перечисления [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) , определяющее тип сравнения.  
  
 `rgpMemoryContextSet`  
 окне Массив ссылок на объекты [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) для сравнения.  
  
 `dwMemoryContextSetLen`  
 окне Количество контекстов в `rgpMemoryContextSet` массиве.  
  
 `pdwMemoryContext`  
 заполняет Возвращает индекс первого контекста памяти, удовлетворяющего условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_COMPARE_CANNOT_COMPARE` , если не удается сравнить два контекста.  
  
## <a name="remarks"></a>Remarks  
 Модуль отладки (de) не обязан поддерживать все типы сравнений, но должен поддерживать как минимум `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` и `CONTEXT_SAME_SCOPE` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
