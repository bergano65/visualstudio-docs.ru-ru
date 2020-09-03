---
title: BP_PASSCOUNT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3177ff093aea9a6f52465bd606b22883249d6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737911"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Описывает количество и условия срабатывания условной точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Участники
`dwPassCount`\
Количество проходов через точку останова перед ее срабатыванием.

`stylePassCount`\
Значение из перечисления [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) , указывающее стиль числа проходов точки останова.

## <a name="remarks"></a>Remarks
Эта структура является членом структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .

Эта структура также передается в качестве параметра методам[сетпасскаунт](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) и[сетпасскаунт](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
