---
title: BP_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02550141fb1857214d5bfd80d5dd86969bec9fba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737789"
---
# <a name="bp_type"></a>BP_TYPE
Определяет, находится ли точка разрыва в месте кода, является ли местоположение данных или другой тип точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Поля
`BPT_NONE`\
Не указывает тип точки разрыва.

`BPT_CODE`\
Определяет точку разрыва кода.

`BPT_DATA`\
Определяет точку разрыва данных.

`BPT_SPECIAL`\
Определяет точку разрыва, которая не является ни кодом, ни типом данных. Этот тип является амортизированным и не должен использоваться.

## <a name="remarks"></a>Примечания
Прошел в качестве параметра для методов [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [GetBreakpointType.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
