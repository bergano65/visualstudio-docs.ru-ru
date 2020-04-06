---
title: IDebugClassField::EnumNestedClasses Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734432"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Создает регистратор для классов, вложенных в этот класс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список вложенных классов. Возвращает нулевую стоимость, если нет вложенных классов.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха, возвращает S_OK или возвращает S_FALSE, если Нет вложенных классов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Каждый элемент перечисления — объект [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) описывающий вложенный класс.

Вложенный класс — это класс, определяемый внутри другого класса. Пример:

```
class RootClass {
   class NestedClass { }
};
```

В перечислении [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) будет содержаться `NestedClass` один объект, представляющий класс.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
