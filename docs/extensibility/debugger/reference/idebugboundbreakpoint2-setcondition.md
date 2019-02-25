---
title: IDebugBoundBreakpoint2::SetCondition | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dcec65b22c728384fb199eecf461ec61317e348
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691687"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Задает или изменяет условие, связанное с данная связанная точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

#### <a name="parameters"></a>Параметры
 `bpCondition`

 [in] Значение из [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) перечисления, которое описывает условие.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова присваивается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).

## <a name="remarks"></a>Примечания
 Любое условие, который был ранее связан с этой точкой останова будет потеряно.

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)