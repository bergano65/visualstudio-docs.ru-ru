---
title: DEBUGREF_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1adab87ed09ca2ff16d837da084d8cc0b76956fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318359"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Указывает, какую информацию нужно извлечь сведения об объекте debug ссылку.

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
Инициализация и использование `bstrName` в структуре.

`DEBUGREF_INFO_TYPE`\
Инициализация и использование `bstrType` в структуре.

`DEBUGREF_INFO_VALUE`\
Инициализация и использование `bstrValue` в структуре.

`DEBUGREF_INFO_ATTRIB`\
Инициализация и использование `dwAttrib` в структуре.

`DEBUGREF_INFO_REFTYPE`\
Инициализация и использование `dwRefType` в структуре.

`DEBUGREF_INFO_REF`\
Инициализация и использование `pReference` в структуре.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Поле значения должен содержать значение развернутый автоматически, если он доступен для этого типа объектов.

`DEBUGREF_INFO_NONE`\
Указывает, что флаги не установлены.

`DEBUGREF_INFO_ALL`\
Указывает маску флагов.

## <a name="remarks"></a>Примечания
Эти флаги передаются [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) и [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) методы, чтобы указать, какие поля [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры должны быть инициализированы.

Используется для `dwFields` членом `DEBUG_REFERENCE_INFO` структура указывает, какие поля используются и допустимым при возвращении структуры.

Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
