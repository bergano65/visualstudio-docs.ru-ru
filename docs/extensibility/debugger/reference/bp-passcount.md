---
title: BP_PASSCOUNT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d51e0fc895c104c1a18ef079c6784384e4cedbb4
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316695"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Описывает число и условия, на которых запускается условную точку останова.

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
`dwPassCount`  
Сколько раз для передачи через точку останова перед порождением его.

`stylePassCount`  
Значение из [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) число проходов перечисления, задающее стиль точки останова.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структуры.

Эта структура также передается в качестве параметра[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) и[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) методы.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)  
[BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
