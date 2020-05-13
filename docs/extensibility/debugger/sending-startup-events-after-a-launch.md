---
title: Отправка событий запуска после запуска (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713017"
---
# <a name="send-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
После присоединения двигателя отладки (DE) к программе он отправляет серию событий запуска обратно в сеанс отладки.

 События запуска, отправленные обратно на сеанс отладки, включают:

- Событие создания двигателя.

- Событие создания программы.

- Создание потока и события загрузки модуля.

- Полное событие нагрузки, отправленное при загрузке кода и готовом к запуску, но до выполнения любого кода.

  > [!NOTE]
  > Когда это событие продолжается, глобальные переменные инициализируются и запускарутины запускаются.

- Возможныдругие другие события создания потока и загрузки модуля.

- Событие точки входа, которое сигнализирует о том, **Main** что `WinMain`программа достигла своей основной точки входа, например, Main или . Это событие обычно не отправляется, если DE прикрепляется к уже запущенной программе.

  Программно, DE сначала отправляет менеджеру отладки сеанса (SDM) интерфейс [IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) который представляет собой событие создания двигателя, а затем [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), который представляет событие создания программы.

  За этими событиями обычно следуют одно или несколько событий создания потоков [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) и события загрузки модуля [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Когда код загружен и готов к запуску, но до выполнения любого кода DE отправляет SDM в полное событие загрузки [IDebugLoadCompleteEvent2.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Наконец, если программа еще не запущена, DE отправляет событие точки входа [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) сигнализируя о том, что программа достигла своей основной точки входа и готова к отладке.

## <a name="see-also"></a>См. также
- [Контроль исполнения](../../extensibility/debugger/control-of-execution.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
