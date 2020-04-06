---
title: BP_REQUEST_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35a1202f4990f4f6370ad031c896ba85ebb6d816
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737897"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Содержит информацию, необходимую для реализации точки разрыва.

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
Комбинация флагов из [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисления, которая определяет, какие поля заполнены.

`guidLanguage`\
GUID языка.

`bpLocation`\
Структура [BP_LOCATION,](../../../extensibility/debugger/reference/bp-location.md) которая определяет тип местоположения точки разрыва.

`pProgram`\
Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий приложение, в котором происходит точка разрыва.

`bstrProgramName`\
Название приложения, в котором происходит точка разрыва.

`pThread`\
Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток, в котором происходит точка разрыва.

`bstrThreadName`\
Название потока, в котором происходит точка разрыва.

`bpCondition`\
Структура [BP_CONDITION,](../../../extensibility/debugger/reference/bp-condition.md) описывающая условия, при которых будет гореть точка разрыва.

`bpPassCount`\
Структура [BP_PASSCOUNT,](../../../extensibility/debugger/reference/bp-passcount.md) содержащая информацию о подсчете пропусков точки разрыва.

`dwFlags`\
Комбинация флагов из [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисления, которая определяет флаги для запрошенной точки разрыва.

## <a name="remarks"></a>Примечания
Эта структура возвращается методом [GetRequestInfo.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)

Если вам нужно получить поставщик апогея GUID, ограничение точки разрыва или точку трассировки, см. [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуру.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

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
