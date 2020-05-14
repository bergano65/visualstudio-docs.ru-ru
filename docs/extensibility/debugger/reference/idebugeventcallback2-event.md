---
title: IDebugEventCallback2::Событие Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729894"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Отправляет уведомления о событиях отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Параметры
`pEngine`\
(в) Объект [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) представляющий движок отладки (DE), отправляющий это событие. Для заполнения этого параметра требуется DE.

`pProcess`\
(в) Объект [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) представляющий процесс, в котором происходит событие. Этот параметр заполняется менеджером отладки сеанса (SDM). DE всегда проходит нулевое значение для этого параметра.

`pProgram`\
(в) Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий программу, в которой происходит это событие. Для большинства событий этот параметр не является нулевая величина.

`pThread`\
(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток, в котором происходит это событие. Для остановки событий этот параметр не может быть нулевой величиной, так как кадр стека получен из этого параметра.

`pEvent`\
(в) Объект [IDebugEvent2,](../../../extensibility/debugger/reference/idebugevent2.md) представляющий событие отладки.

`riidEvent`\
(в) GUID определяет, какой интерфейс событий `pEvent` получить от параметра.

`dwAttrib`\
(в) Комбинация флагов из перечисления [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 При вызове этого `dwAttrib` метода параметр должен соответствовать значению, возвращенному из `pEvent` [метода GetAttributes,](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) как это вызвано на объекте события, переданном в параметре.

 Все события отладки размещаются асинхронно, независимо от того, является ли само событие асинхронным или нет. При вызове DE этого метода значение возврата не указывает на то, было ли обработано событие, только то, было ли получено событие. На самом деле, в большинстве случаев событие не было обработано, когда этот метод возвращается.

## <a name="see-also"></a>См. также
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
