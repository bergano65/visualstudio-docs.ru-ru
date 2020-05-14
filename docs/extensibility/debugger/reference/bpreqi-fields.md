---
title: BPREQI_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737746"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Укажите информацию, которая будет получена о запросе точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Поля
`BPREQI_BPLOCATION`\
Инициализация/использование `bpLocation` поля (точки разрыва) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.

`BPREQI_LANGUAGE`\
Инициализация/использование `guidLanguage` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_PROGRAM`\
Инициализация/использование `pProgram` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_PROGRAMNAME`\
Инициализация/использование `bstrProgramName` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_THREAD`\
Инициализация/использование `pThread` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_THREADNAME`\
Инициализация/использование `bstrThreadName` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_PASSCOUNT`\
Инициализация/использование `bpPassCount` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_CONDITION`\
Инициализация/использование `bpCondition` (условие брейк-пойнта) поля `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.

`BPREQI_FLAGS`\
Инициализация/использование `dwFlags` `BP_REQUEST_INFO` поля `BP_REQUEST_INFO2` или структуры.

`BPREQI_ALLOLDFIELDS`\
Инициализация/использование всех `BP_REQUEST_INFO` полей для структуры.

`BPREQI_VENDOR`\
`guidVendor` Инициализация/использование `BP_REQUEST_INFO2` области структуры.

`BPREQI_CONSTRAINT`\
`bstrConstraint` Инициализация/использование `BP_REQUEST_INFO2` области структуры.

`BPREQI_TRACEPOINT`\
`bstrTracepoint` Инициализация/использование `BP_REQUEST_INFO2` области структуры.

`BPREQI_ALLFIELDS`\
Определяет все поля для `BP_REQUEST_INFO2` структуры.

## <a name="remarks"></a>Примечания
Прошел в качестве аргумента [в GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) и [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) методы, чтобы указать, какие поля [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры должны быть инициализированы.

Эти флаги также используются для `BP_REQUEST_INFO` `BP_REQUEST_INFO2` указания того, какие поля и структуры используются и действительны при возврате каждой структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
