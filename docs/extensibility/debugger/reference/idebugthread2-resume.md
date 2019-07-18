---
title: IDebugThread2::Resume | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a312b18fead71b343fd1b9beafcf36c904bf1b24
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320137"
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

## <a name="parameters"></a>Параметры
`pdwSuspendCount`\
[out] Возвращает счетчик приостановок после операции возобновления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 При каждом вызове этого метода уменьшает счетчик приостановок возобновляется пока не достигнет 0 в это время выполнения. Этот счетчик приостановок отображается в **потоков** окно отладки.

 Для каждого вызова этого метода, должно существовать предыдущего вызова [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) метод. Счетчик приостановок определяет, сколько раз `IDebugThread2::Suspend` моменту вызова метода.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)