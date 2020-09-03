---
title: BP_CONDITION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738101"
---
# <a name="bp_condition"></a>BP_CONDITION
Описывает условия, при которых срабатывает точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Участники
`pThread`\
Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий активный поток для приложения, содержащего точку останова.

`styleCondition`\
Значение из перечисления [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) , описывающее стиль условия этой точки останова.

`bstrContext`\
Расположение точки останова.

`bstrCondition`\
Условие срабатывания точки останова.

`nRadix`\
Основание системы счисления, используемое при вычислении любых числовых данных.

## <a name="remarks"></a>Remarks
Эта структура является членом структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Эта структура также передается в качестве параметра методам [сеткондитион](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) и [сеткондитион](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
