---
title: Запуск Debugger (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738455"
---
# <a name="launch-the-debugger"></a>Запуск отладчика
Запуск отладчика требует отправки правильной последовательности методов и событий с их соответствующими атрибутами.

## <a name="sequences-of-methods-and-events"></a>Последовательности методов и событий

1. Менеджер отладки сеанса (SDM) называется, выбрав меню **Debug,** а затем выбрав **Start**. Для получения дополнительной информации смотрите [запуск программы](../../extensibility/debugger/launching-a-program.md).

2. SDM вызывает метод [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. На основе модели процесса отладки `IDebugProgramNodeAttach2::OnAttach` двигателя (DE) метод возвращает один из следующих методов, который определяет, что произойдет дальше.

     При `S_FALSE` возврате, отладка двигателя (DE) должен быть загружен в процессе виртуальной машины.

     -или-

     При `S_OK` возврате DE должен быть загружен в процессе SDM. Затем SDM выполняет следующие задачи:

    1. Звонит [GetEngineInfo,](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) чтобы получить информацию о движке DE.

    2. Со-создает DE.

    3. Вызовы [Атташе](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

5. DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

6. DE отправляет [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

7. DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с `EVENT_SYNC` атрибутом.

8. DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM с `EVENT_SYNC` атрибутом.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)
