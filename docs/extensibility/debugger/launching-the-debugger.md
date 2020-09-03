---
title: Запуск отладчика | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738455"
---
# <a name="launch-the-debugger"></a>Запуск отладчика
Для запуска отладчика необходимо отправить правильную последовательность методов и событий с соответствующими атрибутами.

## <a name="sequences-of-methods-and-events"></a>Последовательности методов и событий

1. Чтобы вызвать диспетчер отладки сеансов (SDM), выберите в меню **Отладка** пункт **запустить**. Дополнительные сведения см. [в разделе Запуск программы](../../extensibility/debugger/launching-a-program.md).

2. Модель SDM вызывает метод [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

3. В зависимости от модели процесса модуля отладки (DE) `IDebugProgramNodeAttach2::OnAttach` метод возвращает один из следующих методов, который определяет, что происходит дальше.

     Если `S_FALSE` возвращается, подсистема отладки (de) загружается в процесс виртуальной машины.

     -или-

     Если `S_OK` возвращает, то de загружается в процессе SDM. Затем SDM выполняет следующие задачи:

    1. Вызывает [жетенгинеинфо](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) для получения сведений о подсистеме de.

    2. Совместно создает значение DE.

    3. Вызывает [attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Параметр DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

5. Параметр DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

6. Параметр DE отправляет [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

7. Параметр DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с `EVENT_SYNC` атрибутом.

8. Параметр DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM с `EVENT_SYNC` атрибутом.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)
