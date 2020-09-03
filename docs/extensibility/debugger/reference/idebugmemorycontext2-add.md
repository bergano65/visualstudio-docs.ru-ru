---
title: 'IDebugMemoryContext2:: Add | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727483"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Добавляет указанное значение в текущий контекст и возвращает новый контекст.

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
окне Значение, добавляемое в текущий контекст.

`ppMemCxt`\
заполняет Возвращает новый объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Контекст памяти — это адрес, поэтому при добавлении значения в адрес создается новый адрес, для которого требуется новый интерфейс контекста.

 Этот метод всегда должен создавать новый контекст, даже если полученный адрес находится вне области памяти, связанной с этим контекстом. Единственным исключением является то, что память не может быть выделена для нового контекста или если `ppMemCxt` является значением NULL (это ошибка).

## <a name="see-also"></a>См. также раздел
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
