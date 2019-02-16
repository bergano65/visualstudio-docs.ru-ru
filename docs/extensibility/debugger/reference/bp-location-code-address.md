---
title: BP_LOCATION_CODE_ADDRESS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e90801f17690b48ba82e9fa80fba345e206c50b2
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315928"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Описывает расположение точки останова по адресу в коде.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Участники
`bstrContext`  
Контекст точки останова, обычно имя метода или функции материал в стеке вызовов.

`bstrModuleUrl`  
URL-адрес модуля, содержащего точку останова.

`bstrFunction`  
Имя функции, содержащей точку останова.

`bstrAddress`  
Адрес точки останова, который анализируется с вычислитель выражений, чтобы привязать его к [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
