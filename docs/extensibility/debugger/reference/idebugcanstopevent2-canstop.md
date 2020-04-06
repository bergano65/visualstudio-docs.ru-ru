---
title: IDebugCanStopEvent2::CanStop Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734587"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Уведомляет отладоть движок (DE), стоит ли останавливаться в текущем месте кода или просто продолжать выполнение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Параметры
`fCanStop`\
(в) Ненулевой`TRUE`( ), если DE должен остановиться в текущем месте кода; в противном`FALSE`случае, ноль ().

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Получатель этого события обычно вызывает метод [GetReason,](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) чтобы определить причину, `IDebugCanStopEvent2::CanStop` по которой DE хочет остановиться, а затем вызывает метод с соответствующим ответом.

 Если DE останавливается, он отправляет событие, описывая причину остановки. Обычно отправляются два события: перерыв пользователя или сигнала, представленный интерфейсом [IDebugBreakEvent2,](../../../extensibility/debugger/reference/idebugbreakevent2.md) и событие точки разрыва, представленное интерфейсом [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

## <a name="see-also"></a>См. также
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
