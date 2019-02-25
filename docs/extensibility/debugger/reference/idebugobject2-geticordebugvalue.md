---
title: IDebugObject2::GetICorDebugValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f31436390225e022069ef69f1557f4752f8c208
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695371"
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

#### <a name="parameters"></a>Параметры
 `ppUnk`

 [out] `IUnknown` интерфейс, который представляет этот псевдоним. Этот интерфейс может запрашиваться для `ICorDebugValue` интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 `ICorDebugValue` Объект — это интерфейс среды CLR, который представляет значение.

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)