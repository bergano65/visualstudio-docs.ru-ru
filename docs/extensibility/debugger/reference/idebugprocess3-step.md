---
title: IDebugПроцесс3::Шаг Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723551"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Вызывает процесс, чтобы шаг ировать одну инструкцию или инструкцию.

> [!NOTE]
> Этот метод следует использовать вместо [Шага](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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
(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий шаг вперед потока.

`sk`\
(в) Одно из значений [STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
(в) Одно из значений [STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В случае синхронизации потоков или связи между потоками другие потоки в процессе должны работать при наступлении конкретного потока.

 **Предупреждение** Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
