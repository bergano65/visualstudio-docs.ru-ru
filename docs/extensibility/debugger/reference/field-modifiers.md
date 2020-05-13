---
title: FIELD_MODIFIERS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736856"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Определяет модификаторы для типа поля.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Поля
`FIELD_MOD_ACCESS_TYPE`\
Означает, что поле не доступно.

`FIELD_MOD_ACCESS_PUBLIC`\
Означает, что поле имеет открытый доступ.

`FIELD_MOD_ACCESS_PROTECTED`\
Означает, что поле защищено доступом.

`FIELD_MOD_ACCESS_PRIVATE`\
Означает, что поле имеет частный доступ.

`FIELD_MOD_NOMODIFIERS`\
Означает, что поле не имеет модификаторов.

`FIELD_MOD_STATIC`\
Означает, что поле статично.

`FIELD_MOD_CONSTANT`\
Означает, что поле является постоянным.

`FIELD_MOD_TRANSIENT`\
Означает, что поле является временным.

`FIELD_MOD_VOLATILE`\
Означает, что поле нестабильно.

`FIELD_MOD_ABSTRACT`\
Означает, что поле является абстрактным.

`FIELD_MOD_NATIVE`\
Означает, что поле является родным.

`FIELD_MOD_SYNCHRONIZED`\
Означает, что поле синхронизировано.

`FIELD_MOD_VIRTUAL`\
Означает, что поле виртуальное.

`FIELD_MOD_INTERFACE`\
Означает, что поле является интерфейсом.

`FIELD_MOD_FINAL`\
Означает, что поле является окончательным.

`FIELD_MOD_SENTINEL`\
Означает, что поле является дозорным.

`FIELD_MOD_INNERCLASS`\
Означает, что поле является внутренним классом.

`FIELD_TYPE_OPTIONAL`\
Указывает, что поле является необязательным.

`FIELD_MOD_BYREF`\
Означает, что поле является эталонным аргументом. Это специально для метода аргументов.

`FIELD_MOD_HIDDEN`\
Означает, что поле должно быть скрыто или представлено в другом контексте; например, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] статических местных жителей.

`FIELD_MOD_MARSHALASOBJECT`\
Означает, что поле представляет `IUnknown` объект с интерфейсом.

`FIELD_MOD_SPECIAL_NAME`\
Означает, что поле имеет специальное `.ctor` название, например, для конструктора (только).[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]

`FIELD_MOD_HIDEBYSIG`\
Означает, что поле `Overloads` имеет ключевое[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] слово применяется к нему (только).

`FIELD_MOD_WRITEONLY`\
Означает, что поле только для записи. Это значение не `FIELD_MOD_ALL`включено в , так как единственное использование таких полей только для записи для оценки функции. Пользователь должен явно запрашивать `FIELD_MOD_WRITEONLY` поля.

`FIELD_MOD_ACCESS_MASK`\
Указывает маску для доступа к полям.

`FIELD_MOD_MASK`\
Указывает маску для полевых модификаторов.

## <a name="remarks"></a>Примечания
Используется для `dwModifiers` члена [структуры FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

Эти значения также передаются методу [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) для фильтрации для определенных полей.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
