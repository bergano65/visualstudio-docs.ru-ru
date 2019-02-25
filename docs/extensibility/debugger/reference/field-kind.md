---
title: FIELD_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b965def820771b0bab883c1bdd9bf90d18414e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680378"
---
# <a name="fieldkind"></a>FIELD_KIND
Указывает тип поля, содержащегося в [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.

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

## <a name="members"></a>Участники
FIELD_KIND_TYPE указывает на то, что поле только для типа.

FIELD_KIND_SYMBOL указывает, что поле — это символ, с типом, имя и другие сведения.

FIELD_TYPE_PRIMITIVE указывает, что поле имеет тип-примитив.

FIELD_TYPE_STRUCT указывает на то, что поле структуры.

FIELD_TYPE_CLASS указывает, что поле является классом.

FIELD_TYPE_INTERFACE указывает, что поле является интерфейсом.

FIELD_TYPE_UNION указывает на то, что поле объединения.

FIELD_TYPE_ARRAY указывает, что поле является массивом.

FIELD_TYPE_METHOD указывает, что поле является методом.

FIELD_TYPE_BLOCK указывает, что поле представляет собой блок.

FIELD_TYPE_POINTER указывает, что поле является указателем.

FIELD_TYPE_ENUM указывает на то, что поле перечисляемого типа данных.

FIELD_TYPE_LABEL указывает на то, что поле метки.

FIELD_TYPE_TYPEDEF указывает на то, что поле является определением типа.

FIELD_TYPE_BITFIELD указывает на то, что поле битовое поле.

FIELD_TYPE_NAMESPACE указывает на то, что поле пространство имен.

FIELD_TYPE_MODULE указывает, что поле является модулем.

FIELD_TYPE_DYNAMIC указывает, что поле является динамическим.

FIELD_TYPE_PROP указывает, что поле является свойством.

FIELD_TYPE_INNERCLASS указывает на то, что поле вложенного класса.

FIELD_TYPE_REFERENCE указывает, что поле является ссылкой.

FIELD_TYPE_EXTENDED зарезервированная для будущего использования.

FIELD_SYM_MEMBER указывает, что поле является членом.

FIELD_SYM_LOCAL указывает, что поле является локальным.

FIELD_SYM_PARAMETER указывает, что поле является параметром.

FIELD_SYM_THIS указывает на то, что поле указателя «this».

FIELD_SYM_GLOBAL указывает, что поле является глобальным.

FIELD_SYM_PROP_GETTER указывает, что поле извлекает свойства.

FIELD_SYM_PROP_SETTER указывает, что поле задает свойства.

FIELD_SYM_EXTENDED зарезервированная для будущего использования.

FIELD_KIND_MASK указывает маску для типов полей.

FIELD_TYPE_MASK указывает маску для типов полей.

FIELD_SYM_MASK указывает маску для символьной информации.

## <a name="remarks"></a>Примечания
Возвращается из вызова [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) метод.

В зависимости от типа поля [QueryInterface](/cpp/atl/queryinterface) могут быть вызваны для [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс более определенной формы интерфейса. Например если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_METHOD`, затем можно вызвать `QueryInterface` на я`DebugField` для получения [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) интерфейс.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
