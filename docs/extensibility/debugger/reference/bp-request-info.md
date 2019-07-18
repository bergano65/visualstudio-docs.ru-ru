---
title: BP_REQUEST_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25967fa5ddc6f827435c03c2883eacb522c79f42
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353008"
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
Содержит сведения, необходимые для реализации точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_REQUEST_INFO {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление, указывающее, какие поля заполнены.

`guidLanguage`\
GUID языка.

`bpLocation`\
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру, которая указывает тип точки останова.

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий приложение, в котором происходит точки останова.

`bstrProgramName`\
Имя приложения, в котором происходит точки останова.

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит точки останова.

`bstrThreadName`\
Имя потока, в котором происходит точки останова.

`bpCondition`\
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структуру, которая описывает условия, при которых точка останова будет срабатывать.

`bpPassCount`\
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуру, содержащую сведения о подсчете pass точки останова.

`dwFlags`\
Сочетание флагов из [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисления, указывающее флаги для запрошенного точки останова.

## <a name="remarks"></a>Примечания
Эта структура возвращается [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) метод.

Если вам необходимо получить идентификатор GUID поставщика ядра отладки, ограничение точки останова или точки трассировки, см. в разделе [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
