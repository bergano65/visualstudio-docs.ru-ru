---
title: Запуск отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ffe0405b1e07bfb7825607e17088f0f75796197
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889440"
---
# <a name="launch-the-debugger"></a>Запуск отладчика
Запуск отладчика требуется отправить правильную последовательность методов и событий с использованием их соответствующие атрибуты.

## <a name="sequences-of-methods-and-events"></a>Последовательности методы и события

1. Диспетчер отладки сеансов (SDM) называется, выбрав **Отладка** меню, а затем выбрать **запустить**. Дополнительные сведения см. в разделе [запускать программу](../../extensibility/debugger/launching-a-program.md).

2. Вызовы SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.

3. На основе модели процесса отладки ядра (DE), `IDebugProgramNodeAttach2::OnAttach` метод возвращает одно из следующих методов, которые определяет, что будет дальше.

     Если `S_FALSE` возвращает модуль отладки (DE), будет необходимо загрузить процессе виртуальной машины.

     -или-

     Если `S_OK` возвращает, DE необходимо загрузить в процессе из SDM. SDM выполняет следующие задачи:

    1. Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) получить сведения из DE.

    2. Совместно создает DE.

    3. Вызовы [присоединить](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Отправляет DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) для SDM с `EVENT_SYNC` атрибута.

5. Отправляет DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.

6. Отправляет DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.

7. Отправляет DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) для SDM с `EVENT_SYNC` атрибута.

8. Отправляет DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) для SDM с `EVENT_SYNC` атрибута.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)