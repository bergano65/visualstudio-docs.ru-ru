---
title: Прикрепление и отсоединение к программе Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739271"
---
# <a name="attaching-and-detaching-to-a-program"></a>Прикрепление и отсоединение к программе
Присоединение отладчика требует отправки правильной последовательности методов и событий с соответствующими атрибутами.

## <a name="sequence-of-methods-and-events"></a>Последовательность методов и событий

1. Менеджер отладки сеанса (SDM) вызывает метод [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    На основе модели процесса отладки `IDebugProgramNodeAttach2::OnAttach` двигателя (DE) метод возвращает один из следующих методов, который определяет, что произойдет дальше.

    При `S_FALSE` возврате двигатель отладки успешно присоединен к программе. В противном случае для завершения процесса присоединения называется метод [Присоединения.](../../extensibility/debugger/reference/idebugengine2-attach.md)

    При `S_OK` возврате DE загружается в том же процессе, что и SDM. SDM выполняет следующие задачи:

   1. Звонит [GetEngineInfo,](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) чтобы получить информацию о движке DE.

   2. Со-создает DE.

   3. Вызовы [Атташе](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

3. DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

4. DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с `EVENT_SYNC_STOP` атрибутом.

   Отсоединение от программы является простым, двухэтапным процессом:

5. SDM вызывает [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
