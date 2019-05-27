---
title: IDebugEventCallback2::Event | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a947f473fe7dc1fcf3e7b5b2b96d13edc3098218
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201149"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Отправляет уведомление о событиях отладки.

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
[in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , представляющий модуль отладки (DE), который отправляет это событие. Для заполнения этого параметра требуется DE.

`pProcess`\
[in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий процесс, в котором происходит событие. Этот параметр заполняется диспетчером сеанса отладки (SDM). DE всегда передает значение null для этого параметра.

`pProgram`\
[in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в котором происходит это событие. Для большинства событий этот параметр не имеет значение null.

`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит это событие. Для события остановки, этот параметр не может иметь значение null, кадр стека при получении от этого параметра.

`pEvent`\
[in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий событие отладки.

`riidEvent`\
[in] Идентификатор GUID, определяющий интерфейс событий, который нужно получить из `pEvent` параметра.

`dwAttrib`\
[in] Сочетание флагов из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 При вызове этого метода `dwAttrib` должен соответствовать значение, возвращаемое из [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) переданный метода, вызываемого на объекте события `pEvent` параметра.

 Все события отладки учитываются асинхронно, независимо от того, ли событие сам является асинхронным, или нет. При использовании DE вызывает этот метод, возвращаемое значение указывает ли событие обработано, только ли получения события. На самом деле в большинстве случаев это событие не была обработана при возвращении данного метода.

## <a name="see-also"></a>См. также
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)