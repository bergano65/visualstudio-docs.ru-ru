---
title: DEBUGREF_INFO_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737388"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Определяет, какую информацию получить об объекте отладки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Поля
`DEBUGREF_INFO_NAME`\
Инициализация/использование `bstrName` поля в структуре.

`DEBUGREF_INFO_TYPE`\
Инициализация/использование `bstrType` поля в структуре.

`DEBUGREF_INFO_VALUE`\
Инициализация/использование `bstrValue` поля в структуре.

`DEBUGREF_INFO_ATTRIB`\
Инициализация/использование `dwAttrib` поля в структуре.

`DEBUGREF_INFO_REFTYPE`\
Инициализация/использование `dwRefType` поля в структуре.

`DEBUGREF_INFO_REF`\
Инициализация/использование `pReference` поля в структуре.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Поле значений должно содержать автоматическое расширенное значение, если доступно, для этого типа объекта.

`DEBUGREF_INFO_NONE`\
Означает, что флаги не установлены.

`DEBUGREF_INFO_ALL`\
Указывает на маску флагов.

## <a name="remarks"></a>Примечания
Эти флаги передаются методам [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) и [GetReferenceInfo,](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) чтобы указать, какие поля [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры должны быть инициализированы.

Используется для `dwFields` члена `DEBUG_REFERENCE_INFO` структуры для указания того, какие поля используются и действительны при возврате структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
