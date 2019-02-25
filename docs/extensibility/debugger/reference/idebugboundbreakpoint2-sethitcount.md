---
title: IDebugBoundBreakpoint2::SetHitCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac7cbfa337bfdcf54d213b299badc9ca56d8dcba
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716315"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Задает количество обращений к связанная точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

#### <a name="parameters"></a>Параметры
 `dwHitCount`

 [in] Число попаданий для задания.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова присваивается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).

## <a name="remarks"></a>Примечания
 Число попаданий — количество раз, когда данная точка останова возникло во время выполнения текущего сеанса.

 Как правило, этот метод вызывается подсистемой отладки, чтобы обновить текущий счетчик числа попаданий в эту точку останова.

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)