---
title: IDebugEngine2::Прикрепить Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731215"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Прикрепляет движок отладки (DE) к программе или программам. Вызывается менеджером отладки сеанса (SDM), когда DE работает в процессе sDM.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Параметры
`pProgram`\
(в) Массив объектов [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) которые представляют программы, к которым следует прикрепить. Это портовые программы.

`rgpProgramNodes`\
(в) Массив объектов [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) представляющих узлы программы, по одному для каждой программы. Узлы программы в этом массиве представляют `pProgram`те же программы, что и в . Узлы программы даны так, что DE может определить программы, чтобы прикрепить к.

`celtPrograms`\
(в) Количество программ и/или узлов программы `pProgram` `rgpProgramNodes` в массивах и массивах.

`pCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) который будет использоваться для отправки событий отладки в SDM.

`dwReason`\
(в) Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, которое определяет причину присоединения этих программ. Дополнительные сведения см. в разделе «Примечания».

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Существует три причины для присоединения к программе:

- `ATTACH_REASON_LAUNCH`указывает на то, что DE прикрепляется к программе, потому что пользователь запустил процесс, который ее содержит.

- `ATTACH_REASON_USER`указывает, что пользователь явно запросил DE присоединение к программе (или процессу, содержащего программу).

- `ATTACH_REASON_AUTO`означает, что DE прикрепляется к конкретной программе, поскольку она уже отлаждает другие программы в определенном процессе. Это также называется автоматическим крепом.

  Когда этот метод вызывается, DE необходимо отправить эти события в последовательности:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (если он еще не был отправлен для конкретного экземпляра двигателя отладки)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Кроме того, если причина присоединения, `ATTACH_REASON_LAUNCH`DE необходимо отправить [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) событие.

   Как только DE получает объект [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) соответствующий отладке программы, его можно запросить для любого частного интерфейса.

   Перед вызовом методов узла программы в `pProgram` массиве, предоставленном или, `rgpProgramNodes`олицетворение, если это необходимо, должно быть включено на `IDebugProgram2` интерфейсе, который представляет узла программы. Как правило, однако, этот шаг не является необходимым. Для получения дополнительной информации [см.](../../../extensibility/debugger/security-issues.md)

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
