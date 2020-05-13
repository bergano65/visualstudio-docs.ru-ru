---
title: IDebugBreakpointBoundEvent2:EnumBoundBreakpoints Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f208c52bd45953aaad9efab9b6b65b15b3b759c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735358"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Создает перечисление моментов, которые были связаны на этом событии.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugBoundPointspoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) который перечисляет все точки разрыва, связанные с этим событием.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`. Возвращает, `S_FALSE` если нет связанных точек разрыва; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Список связанных брейк-пойнтов предназначен для тех, кто связан с этим событием, и может быть не весь список моментов разрыва, связанных с ожидавной точкой разрыва. Чтобы получить список всех точек разрыва, привязанных к ожидавшейся точке разрыва, позвоните в метод [GetPendingBreakpoint,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) чтобы получить связанный объект [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) а затем позвоните в метод [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) чтобы получить объект [IEnumDebugBoundBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) содержащий все связанные точки разрыва для ожидающего разрыва.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **CBreakpointSetEventBase,** который предоставляет интерфейс [IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>См. также
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
