---
title: DEBUGPROP_INFO_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737403"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Определяет, какую информацию получить об объекте свойства отладки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Поля
`DEBUGPROP_INFO_FULLNAME`\
Инициализация/использование `bstrFullName` поля.

`DEBUGPROP_INFO_NAME`\
Инициализация/использование `bstrName` поля.

`DEBUGPROP_INFO_TYPE`\
Инициализация/использование `bstrType` поля.

`DEBUGPROP_INFO_VALUE`\
Инициализация/использование `bstrValue` поля.

`DEBUGPROP_INFO_ATTRIB`\
Инициализация/использование `dwAttrib` поля.

`DEBUGPROP_INFO_PROP`\
Инициализация/использование `pProperty` поля, содержащего интерфейс [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Указывается, что поле значения должно содержать автоматическое расширенное значение, если это возможно, для этого типа объекта.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Не рекомендуется.

`DEBUGPROP_INFO_VALUE_RAW`\
Не возвращайте никаких украшаемых значений или членов (то есть не форматировать значения).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Не возвращайте никаких специальных синтезированных значений (например, не следует вызывать `ToString()` объект для создания значения).

`DEBUGPROP_INFO_NONE`\
Указывает, что флаги не заданы.

`DEBUGPROP_INFO_STANDARD`\
Инициализация `dwAttrib` `bstrName`/использовать , , `bstrType`, и `bstrValue` поля.

`DEBUGPROP_INFO_All`\
Указывает маску всех флагов.

## <a name="remarks"></a>Примечания
Эти значения передаются методам [GetPropertyInfo,](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)и [EnumProperties,](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) чтобы указать, какие поля должны быть инициализированы [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структурой.

Эти значения также используются `dwFields` для `DEBUG_PROPERTY_INFO` члена структуры для указания того, какие поля структуры используются и действительны при возврате структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
