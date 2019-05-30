---
title: BP_LOCATION_DATA_STRING | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: cf8e2958f55ca13ab050302a24ad9e5ae185d81a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353094"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Используется для задания точки останова по данным, которые основаны на строку, пользователь может ввести в интегрированной среде разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Участники
`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в который происходит точки останова.

`bstrContext`\
Контекст точки останова в коде, обычно имя метода или функции материал в стеке вызовов.

`bstrDataExpr`\
Строка данных пользователь вводит задается точка останова.

`dwNumElements`\
Число элементов в строке данных, в котором происходит точки останова.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
