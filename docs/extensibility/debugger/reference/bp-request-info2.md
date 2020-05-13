---
title: BP_REQUEST_INFO2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737879"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Содержит информацию, необходимую для реализации точки разрыва, включая GUID поставщика, ограничение и точку трассировки.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_REQUEST_INFO2 {
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
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
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
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
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

`guidVendor`\
GUID поставщика. Может быть нулевая стоимость.

`bstrConstraint`\
Наименование ограничения точки разрыва. Может быть нулевая стоимость.

`bstrTracepoint`\
Название точки трассировки. Может быть нулевая стоимость.

## <a name="remarks"></a>Примечания
Эта структура возвращается методом [GetRequestInfo2.](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
