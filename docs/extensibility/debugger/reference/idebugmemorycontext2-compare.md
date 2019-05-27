---
title: IDebugMemoryContext2::Compare | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f04000d3e2675f766ae343836320aa7433ade87d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211991"
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

## <a name="parameters"></a>Параметры
`compare`\
[in] Значение из [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) перечисление, определяющее тип сравнения.

`rgpMemoryContextSet`\
[in] Массив ссылок на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объектов для сравнения.

`dwMemoryContextSetLen`\
[in] Число контекстов в `rgpMemoryContextSet` массива.

`pdwMemoryContext`\
[out] Возвращает индекс первого контекста памяти, который удовлетворяет условию сравнения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_COMPARE_CANNOT_COMPARE` Если невозможно сравнить двух контекстах.

## <a name="remarks"></a>Примечания
 Для поддержки всех типов сравнений нет модуля отладки (DE), но он должен поддерживать по крайней мере `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` и `CONTEXT_SAME_SCOPE`.

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)