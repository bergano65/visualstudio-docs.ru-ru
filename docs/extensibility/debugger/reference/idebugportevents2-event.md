---
title: IDebugPortEvents2::Событие Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725247"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Этот метод отправляет события, которые обозначает создание и разрушение процессов и программ в порту.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Параметры
`pMachine`\
(в) Объект [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) представляющий сервер отладки (есть [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]один для каждого экземпляра), в котором произошло событие.

`pPort`\
(в) Объект [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md) представляющий порт, в котором произошло событие.

`pProcess`\
(в) Объект [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) представляющий процесс, в котором произошло событие.

`pProgram`\
(в) Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий программу, в которой произошло событие.

`pEvent`\
(в) Объект [IDebugEvent2,](../../../extensibility/debugger/reference/idebugevent2.md) идентифицирующие событие. Возможные события следующие:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
(в) GUID этого мероприятия. Поскольку событие отбрасывается на [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) перед вызовом этого метода, этот идентификатор упрощает определение того, какое событие отправляется.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
