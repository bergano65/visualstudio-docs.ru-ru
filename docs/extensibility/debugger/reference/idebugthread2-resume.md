---
title: IDebugThread2::Resume | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4997b8c711a67a3bb45529627e81e70b786acf00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915513"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Возобновляет выполнение потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

#### <a name="parameters"></a>Параметры
 `pdwSuspendCount`

 [out] Возвращает счетчик приостановок после операции возобновления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 При каждом вызове этого метода уменьшает счетчик приостановок возобновляется пока не достигнет 0 в это время выполнения. Этот счетчик приостановок отображается в **потоков** окно отладки.

 Для каждого вызова этого метода, должно существовать предыдущего вызова [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) метод. Счетчик приостановок определяет, сколько раз `IDebugThread2::Suspend` моменту вызова метода.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)