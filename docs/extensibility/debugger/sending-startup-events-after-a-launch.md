---
title: Отправка события запуска после запуска | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6ffd1a47f4d1d82feecb35110151a8b32d7d245
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135758"
---
# <a name="sending-startup-events-after-a-launch"></a>Отправка события запуска после запуска
После прикрепления модуль отладки (DE) в программу она отправляет последовательность событий при запуске сеанса отладки.  
  
 Следующие события запуска отправляются обратно в сеансе отладки.  
  
-   Обработчик события создания.  
  
-   События создания программы.  
  
-   Создание и события загрузки модулей потока.  
  
-   Событие завершения загрузки, отправляемых, когда код загружены и готовы к запуску, но перед выполнением любого кода  
  
    > [!NOTE]
    >  Когда это событие дальше, инициализируются глобальные переменные и запустите программы запуска.  
  
-   Другие возможные потока создания и события загрузки модулей.  
  
-   Событие точки входа, которое сигнализирует, что программа достиг его главную точку входа, такие как **Main** или `WinMain`. Это событие обычно не отправляется Если DE присоединяет к программе, на котором уже выполняется.  
  
 Программно, DE в первый раз отправляет диспетчера сеанса отладки (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс, который представляет событие создания подсистемы, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , который представляет событие создания программы.  
  
 Это обычно следуют одна или несколько [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) события создания потоков и [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) события загрузки модулей.  
  
 Если код загружены и готовы к запуску, но перед выполнением любого кода DE отправляет SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) событие завершения нагрузки. Наконец, если программа не запущена, DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) входа точечное событие сигналов, что программа достиг его главную точку входа и готов для отладки.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления, выполнения](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)