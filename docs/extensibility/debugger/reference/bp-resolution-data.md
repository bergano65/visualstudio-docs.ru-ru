---
title: BP_RESOLUTION_DATA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b2d887c10721693468ed907175399074f890588
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317267"
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Описывает результат привязки точки останова по данным.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Участники
`bstrDataExpr`  
Выражения данных, привязанный.

`bstrFunc`  
Функция точки останова в данных привязка имени в (если таковые имеются).

`bstrImage`  
Имя модуля (например, MyModule.dll), привязка точки останова в данных которых была в.

`dwFlags`  
Значение из [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) перечисление, описывающее способ реализации точки останова в данных.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) структуры, который находится в свою очередь является членом [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структура, возвращенная [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
