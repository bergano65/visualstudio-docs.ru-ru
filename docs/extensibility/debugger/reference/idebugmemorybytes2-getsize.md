---
title: IDebugMemoryBytes2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c89e6c5c9ee2b60caef10c5f8378e699b4bc49d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324554"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Чтобы получить размер в байтах, памяти, представленный этим [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

## <a name="parameters"></a>Параметры
`pqwSize`\
[out] Возвращает размер в байтах памяти.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)