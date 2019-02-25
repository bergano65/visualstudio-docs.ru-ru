---
title: IDebugProperty3::GetCustomViewerCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4067fc314889e7aa991407c99ba949564b547087
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709152"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Возвращает количество пользовательских средств просмотра, которые могут быть доступны для этого свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

#### <a name="parameters"></a>Параметры
`pcelt`

 [out] Число пользовательских средств просмотра, доступные для этого свойства.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Чтобы обеспечить поддержку визуализаторов типов, этот метод перенаправляет вызов [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) метод. Если средство оценки выражений также поддерживает пользовательские средства просмотра для этого свойства типа, этот метод добавляет число пользовательских средств просмотра, к возвращенному значению.

Подробные сведения о различиях между визуализаторов типов и пользовательских средств просмотра, см. в разделе [визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CProperty** объекта, который предоставляет [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>См. также
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
