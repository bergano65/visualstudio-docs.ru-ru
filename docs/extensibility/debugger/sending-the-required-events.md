---
title: Отправка требуемых событий Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712994"
---
# <a name="send-the-required-events"></a>Отправка необходимых событий
Используйте эту процедуру для отправки необходимых событий.

## <a name="process-for-sending-required-events"></a>Процесс отправки необходимых событий
 В этом порядке требуется следующее события при создании движка отладки (DE) и присоединении его к программе:

1. Отправить объект события [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) менеджеру отладки сеанса (SDM), когда DE инициализирован для отладки одной или нескольких программ в процессе.

2. При подключении программы к sDM отправьте объект событий [IDebugProgramCreateEvent2.](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Это событие может быть остановкой события, в зависимости от конструкции двигателя.

3. Если программа присоединена к запуску процесса, отправьте объект события [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM, чтобы уведомить IDE о новом потоке. Это событие может быть остановкой события, в зависимости от конструкции двигателя.

4. Отправьте объект события [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM, когда отладка программы будет завершена загрузка или при подключении к программе завершена. Это событие должно быть остановкой события.

5. Если приложение, которое будет отлажено запущено, отправьте объект события [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM, когда будет выполнена первая инструкция кода в архитектуре времени выполнения. Это событие всегда является остановкой события. При входе в сеанс отладки IDE останавливается на этом событии.

> [!NOTE]
> Многие языки используют глобальные инициализаторы или внешние, предварительно собранные функции (из библиотеки CRT или _Main) в начале своего кода. Если язык отладки программы содержит один из этих типов элементов до начальной точки входа, этот код запущен, и **main** событие `WinMain`точки входа отправляется при том, что точка входа пользователя, например основная или, будет достигнута.

## <a name="see-also"></a>См. также
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
