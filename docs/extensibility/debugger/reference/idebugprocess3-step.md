---
title: IDebugProcess3::Step | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc3ffecf5a2760077c0a5da4f4508163a48ca1a4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313882"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Вызывает процесс, чтобы шаг одну инструкцию или инструкции.

> [!NOTE]
> Этот метод следует использовать вместо [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Параметры
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий поток, в настоящее время шаг.

`sk`\
[in] Один из [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) значения.

`step`\
[in] Один из [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) значения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В случае любой синхронизации потоков или связи между потоками, другие потоки в процессе следует запускать при отладке определенного потока.

 **Предупреждение** событии остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)