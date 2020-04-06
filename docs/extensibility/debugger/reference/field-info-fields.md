---
title: FIELD_INFO_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736904"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Определяет, какую информацию получить об объекте [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Поля
`FIF_FULLNAME`\
Инициализация/использование `bstrFullName` поля в [структуре FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Инициализация/использование `bstrName` `FIELD_INFO` поля в структуре.

`FIF_TYPE`\
Инициализация/использование `bstrType` `FIELD_INFO` поля в структуре.

`FIF_MODIFIERS`\
Инициализация/использование `bstrModifiers` `FIELD_INFO` поля в структуре.

## <a name="remarks"></a>Примечания
Эти значения также передаются в качестве аргумента методу [GetInfo,](../../../extensibility/debugger/reference/idebugfield-getinfo.md) чтобы указать, какие поля [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры должны быть инициализированы.

Эти значения также используются `dwFields` в `FIELD_INFO` составе структуры для обозначения того, какие поля используются и действительны.

Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
