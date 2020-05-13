---
title: IDebugMemoryContext2::Сравните Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727493"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Сравнивает контекст памяти с каждым контекстом в данном массиве в порядке, указанном сравните флаги, возвращая индекс первого контекста, который совпадает.

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
(в) Значение из [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) перечисления, определяющее тип сравнения.

`rgpMemoryContextSet`\
(в) Массив ссылок на объекты [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) для сравнения.

`dwMemoryContextSetLen`\
(в) Количество контекстов в `rgpMemoryContextSet` массиве.

`pdwMemoryContext`\
(ваут) Возвращает индекс первого контекста памяти, удовлетворяет сравнение.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает, `E_COMPARE_CANNOT_COMPARE` если два контекста не могут быть сопоставлены.

## <a name="remarks"></a>Примечания
 Отладка двигателя (DE) не должны поддерживать все типы сравнений, `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`но `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`он должен поддерживать по крайней мере , и .

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
