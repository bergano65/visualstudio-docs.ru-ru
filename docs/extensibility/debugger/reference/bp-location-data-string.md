---
title: BP_LOCATION_DATA_STRING | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 056b7efc01b9536184c3e443156e27e328bdd2b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689100"
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
`pThread` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в который происходит точки останова.

`bstrContext` Контекст точки останова в коде, обычно имя метода или функции материал в стеке вызовов.

`bstrDataExpr` Строка данных пользователь вводит задается точка останова.

`dwNumElements` Число элементов в строке данных, в котором происходит точки останова.

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
