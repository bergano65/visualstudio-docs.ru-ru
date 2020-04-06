---
title: IDebugClassField::EnumNestedEnums Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734404"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Создает регистратор для вложенных регистраторов этого класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список вложенных перечислений. Возвращает нулевую стоимость, если нет вложенных перечислений.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха, возвращает S_OK или возвращает S_FALSE, если Нет вложенных регистраторов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Каждый элемент перечисления представляет собой объект [IDebugEnumField,](../../../extensibility/debugger/reference/idebugenumfield.md) описывающий вложенный перечисление.

Перечисление, объявленное внутри класса, считается вложенным перечислением. Например, если:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Метод `EnumNestedEnums` возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) содержащий один объект [IDebugEnumField,](../../../extensibility/debugger/reference/idebugenumfield.md) представляющий перечисление. `NestedEnum`

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
