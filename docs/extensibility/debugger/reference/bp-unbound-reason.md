---
title: BP_UNBOUND_REASON Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737775"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Дает причину, по которой точка разрыва была несвязана.

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

## <a name="fields"></a>Поля
`BPUR_UNKNOWN`\
Причина неизвестна.

`BPUR_CODE_UNLOADED`\
Код, содержащий точку разрыва, был выгружен.

`BPUR_BREAKPOINT_REBIND`\
Точка разрыва была отскок в другое место. Это может произойти после операций «Отработка» и «Продолжить» при движении точки разрыва или при привязке точки разрыва к файлу с недопустимыми путями.

`BPUR_ BREAKPOINT_ERROR`\
Точка разрыва определяется как по ошибке после того, как она связана. Это происходит с управляемыми точками разрыва, условия которых больше не действуют.

## <a name="remarks"></a>Примечания
Возвращается методом [GetReason.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
