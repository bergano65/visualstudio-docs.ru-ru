---
title: IDebugProcess3::Continue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7d20a375644cbbac975f62db216377f271a2675
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314049"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
По-прежнему запускать этот процесс в остановленном состоянии. Сохраняется все предыдущие состояния выполнения (например, шаг), и снова выполните этот процесс.

> [!NOTE]
> Этот метод следует использовать вместо [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Continue(
   IDebugThread2* pThread
);
```

```csharp
int Continue(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий поток, чтобы продолжить.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается об этом процессе, независимо от того, как много процессов, отлаживаемых или процесса, в котором создается событие stopping. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто его никогда не было остановлено до завершения предыдущего выполнения. То есть, если поток в этот процесс выполнялась операция обходе и была остановлена из-за какой-либо процесс остановки, а затем `Continue` был вызван, указанный поток должен завершить исходной операции обходе.

 **Предупреждение** событии остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)