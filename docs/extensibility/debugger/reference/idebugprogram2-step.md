---
title: IDebugПрограмма2::Шаг Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722758"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Выполняет шаг.

> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [Step.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Параметры
`pThread`\
(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий шаг вперед потока.

`sk`\
(в) Значение из перечисления [STEPKIND,](../../../extensibility/debugger/reference/stepkind.md) которое определяет вид шага.

`step`\
(в) Значение из перечисления [STEPUNIT,](../../../extensibility/debugger/reference/stepunit.md) которое определяет единицу шага (например, по заявлению или инструкции).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В случае синхронизации потоков или связи между потоками другие потоки в программе должны работать при наступлении определенного потока.

> [!WARNING]
> Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
