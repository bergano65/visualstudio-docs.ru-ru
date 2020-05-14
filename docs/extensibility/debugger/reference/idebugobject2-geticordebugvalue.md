---
title: IDebugObject2::GetICorDebugValue Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d52701b916650bc142038ffd96dcab8b05ec6da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726117"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Получает управляемый объект кода, представляющий значение, связанное с этим объектом.

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
(ваут) `IUnknown` интерфейс, представляющий этот псевдоним. Этот интерфейс можно запрашивать `ICorDebugValue` для интерфейса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Объект `ICorDebugValue` представляет собой интерфейс Common Language Runtime, представляющий ценность.

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
