---
title: BPRESI_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737720"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Определяет информацию, которая будет получена об успешном разрешении точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Поля
`BPRESI_BPRESLOCATION`\
Инициализация/использование `bpResLocation` поля (место расположения точки разрыва) [структуры BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

`BPRESI_PROGRAM`\
Инициализация/использование `pProgram` `BP_RESOLUTION_INFO` поля структуры.

`BPRESI_THREAD`\
Инициализация/использование `pThread` `BP_RESOLUTION_INFO` поля структуры.

`BPRESI_ALLFIELDS`\
Определяет все поля.

## <a name="remarks"></a>Примечания
Прошел метод [GetResolutionInfo,](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) чтобы указать, какие поля [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры должны быть инициализированы.

Эти флаги также используются для `BP_RESOLUTION_INFO` указания того, какие поля структуры используются и действительны при возврате этой структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
