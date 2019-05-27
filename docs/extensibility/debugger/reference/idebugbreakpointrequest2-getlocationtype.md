---
title: IDebugBreakpointRequest2::GetLocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7000e72ee69b90d873dd85689b97157e83dc6856
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212875"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
Возвращает тип местоположения точки останова этого запроса точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLocationType(
    BP_LOCATION_TYPE* pBPLocationType
);
```

```csharp
int GetLocationType(
    out enum_BP_LOCATION_TYPE pBPLocationType
);
```

## <a name="parameters"></a>Параметры
`pBPLocationType`\
[out] Возвращает значение из [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) перечисления, которое описывает расположение этого запроса точки останова.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_FAIL` Если `bpLocation` в соответствующем поле [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структура не является допустимой.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CDebugBreakpointRequest` объекта, который предоставляет[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс.

```
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)
{
    HRESULT hr;

    if (pBPLocationType)
    {
        // Set default BP_LOCATION_TYPE.
        *pBPLocationType = BPLT_NONE;

        // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.
        if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))
        {
            // Get the new BP_LOCATION_TYPE.
            *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
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
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
