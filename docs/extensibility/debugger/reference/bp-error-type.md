---
title: BP_ERROR_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738079"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Определяет тип ошибки точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Поля
`BPET_NONE`\
Указывает отсутствие ошибки точки разрыва.

`BPET_TYPE_WARNING`\
Укажите ошибку точки разрыва в стиле предупреждения.

`BPET_TYPE_ERROR`\
Укажите ошибку точки ошибки.

`BPET_SEV_HIGH`\
Указывает на ошибку точки разрыва высокой степени тяжести.

`BPET_SEV_GENERAL`\
Указывает ошибку точки разрыва средней степени тяжести.

`BPET_SEV_LOW`\
Указывает ошибку низкой степени тяжести точки разрыва.

`BPET_TYPE_MASK`\
Указывает ошибку точки разрыва в стиле маски.

`BPET_SEV_MASK`\
Указывает ошибку точки разрыва в стиле серьезности-маски.

`BPET_GENERAL_WARNING`\
Укажите ошибку точки разрыва в стиле общего предупреждения.

`BPET_GENERAL_ERROR`\
Укажите ошибку точки разрыва в стиле общего ошибки.

`BPET_ALL`\
Определяет все типы ошибок точки разрыва.

## <a name="remarks"></a>Примечания
Эти значения могут быть объединены `OR` с бигэром и использоваться для `dwType` члена [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры. Прошел в качестве параметра для метода [EnumErrorBreakpoints.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

Тип точки разрыва состоит из типа и серьезности. Это означает, что тип ошибки точки разрыва никогда не является просто типом (например, `BPET_TYPE_ERROR`,) или серьезностью (например,) `BPET_SEV_GENERAL`сам по себе. `BPET_GENERAL_WARNING`и `BPET_GENERAL_ERROR` предоставлять предопределенные значения для общих точек предупреждения и ошибок.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
