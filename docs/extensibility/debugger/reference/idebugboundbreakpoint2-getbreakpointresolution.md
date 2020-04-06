---
title: IDebugBoundBreakpoint2:GetBreakpointРазрешение (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab88009eb1c1bbbd59bbad2dfcbf62567db3941f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735579"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Получает разрешение точки разрыва, описывающая эту точку разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Параметры
`ppBPResolution`\
(ваут) Возвращает интерфейс [IDebugBreakpointResolution2,](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) представляющий один из следующих:

- Объект разрешения точки разрыва, описывающий местоположение в коде, где была связана точка разрыва кода.

- Местоположение данных, в котором связана точка разрыва данных.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращается, `E_BP_DELETED` если состояние объекта точки разрыва `BPS_DELETED` установлено (часть [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).

## <a name="remarks"></a>Примечания
Позвоните в метод [GetBreakpointType,](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) чтобы определить, является ли разрешение точки разрыва для кода или данных.

## <a name="example"></a>Пример
В следующем примере показано, как `CBoundBreakpoint` реализовать этот метод для простого объекта, который предоставляет интерфейс [IDebugBoundBreakpoint2.](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
