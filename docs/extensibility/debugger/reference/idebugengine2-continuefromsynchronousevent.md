---
title: IDebugEngine2::ContinueFromSynchronousEvent | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9e4a02fdccb15f959615c0e7e39d22a05c40ea2
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450468"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Вызывается диспетчером сеанса отладки (SDM), чтобы указать, что событие синхронной отладки, ранее отправленные модуль отладки (DE) SDM, были получены и обработаны.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

#### <a name="parameters"></a>Параметры
`pEvent`  
[in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий ранее отправленные синхронных событий, из которого должна продолжаться отладчика.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
DE необходимо убедиться, что он был источником события, представленного `pEvent` параметра.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CEngine` объект, реализующий [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс.

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
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
[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)  
[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
