---
title: IDebugThread2::GetThreadProperties | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadProperties
helpviewer_keywords:
- IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b32ec64123ef8db4724c7646c54af790fc7500a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714651"
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Получает свойства, описывающие этот поток.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetThreadProperties (
    THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES*     ptp
);
```

```csharp
int GetThreadProperties (
    enum_THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES[]         ptp
);
```

#### <a name="parameters"></a>Параметры
`dwFields`

 [in] Сочетание флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисления, определяющее, какие поля `ptp` должны быть заполнены.

`ptp`

 [in, out] Объект [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры, который заполняется свойства потока.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Сведения, возвращаемые из этого метода обычно отображается в **потоков** окно отладки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объект, реализующий [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) интерфейс.

```cpp
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,
                                      THREADPROPERTIES *ptp)
{
    HRESULT hr = E_FAIL;

    // Check for valid argument.
    if (ptp)
    {
        // Create an array of buffers at ptp the size of the
        // THREADPROPERTIES structure and set all of the
        // buffers at ptp to 0.
        memset(ptp, 0, sizeof (THREADPROPERTIES));

        // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.
        if (dwFields & TPF_ID)
        {
            // Check for successful assignment of the current thread ID to
            // the dwThreadId of the passed THREADPROPERTIES.
            if (GetThreadId(&(ptp->dwThreadId)) == S_OK)
            {
                // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator
                // of the passed THREADPROPERTIES.
                ptp->dwFields |= TPF_ID;
            }
        }

        hr = S_OK;
    }
    else
        hr = E_INVALIDARG;

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
