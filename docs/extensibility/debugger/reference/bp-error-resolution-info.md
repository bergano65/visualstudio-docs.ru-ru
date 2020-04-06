---
title: BP_ERROR_RESOLUTION_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738083"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Описывает разрешение точки разрыва ошибки, включая местоположение, программу и поток.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Участники
`dwFields`\
Комбинация значений из [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) перечисления, определяющая, какие поля этой структуры заполнены.

`bpResLocation`\
[Профсоюз BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) который определяет местоположение разрешения точки разрыва.

`pProgram`\
Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий приложение, в котором произошла ошибка точки разрыва.

`pThread`\
Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток, на котором работает приложение, генерируемый ошибкой точки разрыва.

`bstrMessage`\
Строка, содержащая любое сообщение предупреждения или ошибки в результате этого разрешения ошибок.

`dwType`\
Значение из [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) перечисления, которое определяет тип ошибки точки разрыва.

## <a name="remarks"></a>Примечания
Эта структура возвращается из метода [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
