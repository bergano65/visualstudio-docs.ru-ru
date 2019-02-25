---
title: BP_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2fab9a97ef944b153287a58671193324aecf52c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711479"
---
# <a name="bptype"></a>BP_TYPE
Определяет точку останова в месте кода, — это расположение данных или — еще один тип точки останова.

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

## <a name="members"></a>Участники
BPT_NONE указывает не тип точки останова.

BPT_CODE задает точку останова кода.

BPT_DATA задает точки останова по данным.

Указывает BPT_SPECIAL введите точку останова, которая не является ни код, ни данных. Этот тип является устаревшим и не должны использоваться.

## <a name="remarks"></a>Примечания
Переданный в качестве параметра для [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) методы.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
