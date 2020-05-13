---
title: BPREQI_FIELDS90 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737732"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Перечисляет допустимые значения, указывающие информацию, которая будет получена о запросе точки разрыва. Этот пересчет расширяет [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Поля
`BPREQI90_BPLOCATION`\
Инициализируйте или используйте `bpLocation` (место разрыва) поле [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.

`BPREQI90_LANGUAGE`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `guidLanguage` поле или структуру.

`BPREQI90_PROGRAM`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `pProgram` поле или структуру.

`BPREQI90_PROGRAMNAME`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `bstrProgramName` поле или структуру.

`BPREQI90_THREAD`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `pThread` поле или структуру.

`BPREQI90_THREADNAME`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `bstrThreadName` поле или структуру.

`BPREQI90_PASSCOUNT`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `bpPassCount` поле или структуру.

`BPREQI90_CONDITION`\
Инициализируйте или используйте `bpCondition` (условие брейк-пойнта) поле или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуру.

`BPREQI90_FLAGS`\
Инициализируйте или `BP_REQUEST_INFO` `BP_REQUEST_INFO2` используйте `dwFlags` поле или структуру.

`BPREQI90_ALLOLDFIELDS`\
Инициализация или использование `BP_REQUEST_INFO` всех полей для структуры.

`BPREQI90_VENDOR`\
Инициализация `guidVendor` или `BP_REQUEST_INFO2` использование поля структуры.

`BPREQI90_CONSTRAINT`\
Инициализация `bstrConstraint` или `BP_REQUEST_INFO2` использование поля структуры.

`BPREQI90_TRACEPOINT`\
Инициализация `bstrTracepoint` или `BP_REQUEST_INFO2` использование поля структуры.

`BPREQI90_MACROTRACEPOINT`\
Инициализация `bstrMacroTracepoint` или `BP_REQUEST_INFO2` использование поля структуры. BPREQI_ALLFIELDS не включает в себя это поле.

`BPREQI90_ALLFIELDS`\
Определяет все поля для `BP_REQUEST_INFO2` структуры.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
