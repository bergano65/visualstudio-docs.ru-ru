---
title: BPERESI_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737764"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Определяет информацию, которая будет получена о неудачном разрешении точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Поля
`PERESI_BPRESLOCATION`\
Инициализация/использование `bpResLocation` поля (место расположения точки разрыва) [структуры BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Инициализация/использование `pProgram` `BP_ERROR_RESOLUTION_INFO` поля структуры.

`BPERESI_THREAD`\
Инициализация/использование `pThread` `BP_ERROR_RESOLUTION_INFO` поля структуры.

`BPERESI_MESSAGE`\
Инициализация/использование `bstrMessage` `BP_ERROR_RESOLUTION_INFO` поля структуры.

`BPERESI_TYPE`\
Инициализация/использование `dwType` (типа брейк-пойнта) поля `BP_ERROR_RESOLUTION_INFO` структуры.

`BPERESI_ALLFIELDS`\
Инициализация/использование `BP_ERROR_RESOLUTION_INFO` всех полей структуры.

## <a name="remarks"></a>Примечания
Прошел в качестве параметра для метода [GetResolutionInfo,](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) чтобы указать, какие поля [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры должны быть инициализированы.

Эти значения также используются для указания `BP_ERROR_RESOLUTION_INFO` того, какие поля в структуре используются, и действительны при возврате этой структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
