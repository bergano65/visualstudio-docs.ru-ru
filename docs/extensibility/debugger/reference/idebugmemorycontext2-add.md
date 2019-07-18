---
title: IDebugMemoryContext2::Add | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1cafbf22e51f867948491e2925c085bd387ea84
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347089"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Добавляет указанное значение к текущему контексту и возвращает новый контекст.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Параметры
`dwCount`\
[in] Значение, добавляемое к текущему контексту.

`ppMemCxt`\
[out] Возвращает новый [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Контекст памяти — это адрес, поэтому добавление значения в адрес создает новый адрес, который требуется новый интерфейс контекста.

 Этот метод всегда должен создавать новый контекст, даже если Итоговый адрес находится вне области памяти, связанный с данным контекстом. Единственное исключение — если недостаточно памяти, выделяемой для нового контекста или `ppMemCxt` имеет нулевое значение (который является ошибкой).

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)