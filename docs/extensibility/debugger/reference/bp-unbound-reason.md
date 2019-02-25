---
title: BP_UNBOUND_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65393f6e162cb15ded7a0e598e360c7ce90bb3cd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717667"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Предоставляет причину, по которой был отсоединен точку останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="members"></a>Участники
BPUR_UNKNOWN Причина неизвестна.

Код, который содержит точку останова BPUR_CODE_UNLOADED был выгружен.

Точка останова BPUR_BREAKPOINT_REBIND были привязаны повторно в другом месте. Это может произойти после изменения и продолжить работу, если точка останова перемещается или привязана точка останова в файл с путем, который больше не является допустимым.

Чтобы находиться в состоянии ошибки, после привязки определяется BPUR_ BREAKPOINT_ERROR точки останова. Это происходит для управляемых точек останова, условия которых больше не действительны.

## <a name="remarks"></a>Примечания
Возвращенный [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
