---
title: EVENTATTRIBUTES Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737056"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Определяет атрибуты события.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Поля
`EVENT_ASYNCHRONOUS`\
Означает, что событие является асинхронным и никакого ответа на событие не требуется.

`EVENT_SYNCHRONOUS`\
Означает, что событие синхронное; ответ с помощью [continueFromSynusEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Означает, что это событие остановки. Должны быть объединены с любой `EVENT_ASYNCHRONOUS` или `EVENT_SYNCHRONOUS`.

`EVENT_ASYNC_STOP`\
Указывает на асинхронное событие остановки. В настоящее время такого мероприятия нет. Этот флаг является лишь заполнителем.

`EVENT_SYNC_STOP`\
Указывает на синхронное событие `EVENT_SYNCHRONOUS` `EVENT_STOPPING`остановки (комбинация и). Это значение используется движком отладки (DE) при отправке события остановки. Ответ производится с помощью вызова для [выполнения,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md), или [продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Указывает событие, которое немедленно и синхронно отправляется в IDE. Этот флаг сочетается с `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`другими `EVENT_SYNC_STOP` флагами, такими как , или указать тип события и тот факт, что механизм ответа (если таковой имеется) известен.

`EVENT_EXPRESSION_EVALUATION`\
Событие является результатом оценки выражения.

## <a name="remarks"></a>Примечания
Эти значения передаются `dwAttrib` в параметре метода [События.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
