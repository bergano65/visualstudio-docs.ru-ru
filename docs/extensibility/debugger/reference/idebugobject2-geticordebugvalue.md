---
title: IDebugObject2::GetICorDebugValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edbacbaeac9a5172d8c3bb5b54ee38fff201a2bf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317366"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Возвращает объект управляемого кода, который представляет значение, связанное с данным объектом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
[out] `IUnknown` интерфейс, который представляет этот псевдоним. Этот интерфейс может запрашиваться для `ICorDebugValue` интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 `ICorDebugValue` Объект — это интерфейс среды CLR, который представляет значение.

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)