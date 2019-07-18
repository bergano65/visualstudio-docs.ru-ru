---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce0fdafc6835fdccc87638e17d3bbd01a1415abb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313505"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Создает строковый объект, который имеет указанную длину.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pcstrString`\
[in] Строковое значение для создаваемого строкового объекта.

`uiLength`\
[in] Длина строки в байтах.

`ppObject`\
[out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный строковый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)