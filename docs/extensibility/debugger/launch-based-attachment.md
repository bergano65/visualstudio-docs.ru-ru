---
title: Приложение на основе запуска Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738471"
---
# <a name="launch-based-attachment"></a>Вложение на основе запуска
Приложение на основе запуска к программе происходит автоматически. Когда процесс хостинга программы запускается SDM, вложение на основе запуска следует по пути, аналогичному методу ручного вложения. Для получения [информации, см.](../../extensibility/debugger/attaching-to-the-program.md)

## <a name="the-attaching-process"></a>Процесс присоединения
 Основным отличием является последовательность событий после вызова **Атташе:**

1. Отправить объект события **IDebugEngineCreateEvent2** в SDM. Для получения подробной информации [см.](../../extensibility/debugger/sending-events.md)

2. Вызов `IDebugProgram2::GetProgramId` метода на **интерфейсе IDebugProgram2,** передаваемый методу **Attach.**

3. Отправить объект события **IDebugProgramCreateEvent2,** чтобы уведомить SDM о том, что локальный объект **IDebugProgram2** был создан для представления программы DE.

4. Отправить объект события [IDebugThreadCreateEvent2,](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) чтобы уведомить SDM о создании нового потока для запущенного процесса.

## <a name="see-also"></a>См. также
- [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)
- [Включить отладку программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
