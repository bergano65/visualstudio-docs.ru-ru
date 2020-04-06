---
title: IDebugProgramNode2::Attach_V7 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722143"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Устаревшие. НЕ ИСПОЛЬЗУЙТЕ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Параметры

`pMDMProgram`\
(в) [Интерфейс IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) который представляет программу для присоединения.

`pCallback`\
(в) Интерфейс [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) который будет использоваться для отправки событий отладки в SDM.

`dwReason`\
(в) Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, которое определяет причину присоединения.

## <a name="return-value"></a>Возвращаемое значение

Реализация должна всегда `E_NOTIMPL`возвращаться.

## <a name="remarks"></a>Примечания

> [!WARNING]
> По состоянию на Visual Studio 2005, этот `E_NOTIMPL`метод больше не используется и всегда должен вернуться . См интерфейс [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) можно посмотреть альтернативный подход, если узлам программы необходимо указать, что `GUID`он не может быть прикреплен или если узла программы просто устанавливается программа. В противном случае реализуем метод [Присоединения.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>До Визуальной студии 2005

Этот метод должен быть реализован только в том случае, если DE работает в адресном пространстве отладки программы. В противном случае, этот метод должен вернуться `S_FALSE`.

При вызове этого метода DE должен отправить объект события [IDebugEngineCreateEvent2,](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) если он еще не отправлен для данного экземпляра интерфейса [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) а также объектов событий [IDebugProgramCreate2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и [IDebugLoadCompleteEvent2.](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Объект события [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) отправляется, `dwReason` если `ATTACH_REASON_LAUNCH`параметр.

DE должен вызвать метод [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) на [объекте IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) поставляемом объектом событий [IDebugProgramCreateEvent2,](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и хранить `IDebugProgram2` GUID этой программы в данных экземпляра для объекта, реализованного DE.

## <a name="see-also"></a>См. также

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
