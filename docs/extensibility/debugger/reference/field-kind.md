---
title: FIELD_KIND Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cafe4a34745f3b34070f7d8fed1a246c806375a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736864"
---
# <a name="field_kind"></a>FIELD_KIND
Определяет вид поля, содержащегося в объекте [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Поля
`FIELD_KIND_TYPE`\
Означает, что поле является только типом.

`FIELD_KIND_SYMBOL`\
Означает, что поле является символом с типом, именем и другой информацией.

`FIELD_TYPE_PRIMITIVE`\
Означает, что поле является примитивным типом данных.

`FIELD_TYPE_STRUCT`\
Означает, что поле является структурой.

`FIELD_TYPE_CLASS`\
Означает, что поле является классом.

`FIELD_TYPE_INTERFACE`\
Означает, что поле является интерфейсом.

`FIELD_TYPE_UNION`\
Означает, что поле является союзом.

`FIELD_TYPE_ARRAY`\
Означает, что поле представляет собой массив.

`FIELD_TYPE_METHOD`\
Означает, что поле является методом.

`FIELD_TYPE_BLOCK`\
Означает, что поле является блоком.

`FIELD_TYPE_POINTER`\
Означает, что поле является указателем.

`FIELD_TYPE_ENUM`\
Означает, что поле является перечисленным типом данных.

`FIELD_TYPE_LABEL`\
Означает, что поле является меткой.

`FIELD_TYPE_TYPEDEF`\
Означает, что поле является typedef.

`FIELD_TYPE_BITFIELD`\
Означает, что поле является битовым полем.

`FIELD_TYPE_NAMESPACE`\
Означает, что поле является пространством имен.

`FIELD_TYPE_MODULE`\
Означает, что поле является модулем.

`FIELD_TYPE_DYNAMIC`\
Означает, что поле является динамическим.

`FIELD_TYPE_PROP`\
Означает, что поле является свойством.

`FIELD_TYPE_INNERCLASS`\
Означает, что поле является внутренним классом.

`FIELD_TYPE_REFERENCE`\
Означает, что поле является эталоном.

`FIELD_TYPE_EXTENDED`\
Зарезервировано для последующего использования.

`FIELD_SYM_MEMBER`\
Означает, что поле является членом.

`FIELD_SYM_LOCAL`\
Означает, что поле локальное.

`FIELD_SYM_PARAMETER`\
Означает, что поле является параметром.

`FIELD_SYM_THIS`\
Означает, что поле является "этим" указателем.

`FIELD_SYM_GLOBAL`\
Означает, что поле является глобальным.

`FIELD_SYM_PROP_GETTER`\
Означает, что поле извлекает свойства.

`FIELD_SYM_PROP_SETTER`\
Означает, что поле устанавливает свойства.

`FIELD_SYM_EXTENDED`\
Зарезервировано для последующего использования.

`FIELD_KIND_MASK`\
Указывает маску для видов полей.

`FIELD_TYPE_MASK`\
Указывает маску для типов полей.

`FIELD_SYM_MASK`\
Указывает маску для информации о символах.

## <a name="remarks"></a>Примечания
Возвращается с вызова на метод [GetKind.](../../../extensibility/debugger/reference/idebugfield-getkind.md)

В зависимости от типа поля, [queryInterface](/cpp/atl/queryinterface) можно вызвать на [интерфейсе IDebugField](../../../extensibility/debugger/reference/idebugfield.md) для более конкретной формы интерфейса. Например, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_METHOD`возвращается, `QueryInterface` вы`DebugField` можете вызвать I, чтобы получить интерфейс [IDebugMethodField.](../../../extensibility/debugger/reference/idebugmethodfield.md)

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
