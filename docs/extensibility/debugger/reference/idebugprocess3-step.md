---
title: IDebugProcess3::Step | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 296c76a386b72c3435a90e207dd76f9eeca56422
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412957"
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

#### <a name="parameters"></a>Параметры
 `pThread`

 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий поток, в настоящее время шаг.

 `sk`

 [in] Один из [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) значения.

 `step`

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