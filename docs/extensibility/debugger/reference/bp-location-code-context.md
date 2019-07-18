---
title: BP_LOCATION_CODE_CONTEXT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_CONTEXT
helpviewer_keywords:
- BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 95d09c81fa12e6f06157aeb28aa6b1837f95009e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353086"
---
# <a name="bplocationcodecontext"></a>BP_LOCATION_CODE_CONTEXT
Описывает расположение точки останова, которая привязано непосредственно к адресу в отлаживаемой программы.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_CONTEXT {
    IDebugCodeContext2* pCodeContext;
} BP_LOCATION_CODE_CONTEXT;
```

## <a name="members"></a>Участники
`pCodeContext`\
[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , определяющий положение точки останова в коде.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
