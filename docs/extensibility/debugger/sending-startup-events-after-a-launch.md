---
title: Отправка событий запуска после запуска | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aefdf5e039f591ba6b9cd1fe0e1fce88e3b497c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923007"
---
# <a name="send-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
Когда модуль отладки (DE), подключенного к программе, он отправляет ряд событий запуска сеанса отладки.  
  
 Включать события запуска, отправляемые сеанса отладки:  
  
- Событие создания ядра.  
  
- Событие создания программы.  
  
- Создание и события загрузки модулей потоков.  
  
- Нагрузки событие завершения, когда код будет загружен и готов к выполнению, а также перед выполнением любого кода. 
  
  > [!NOTE]
  >  Когда это событие продолжает выполнение, инициализируются глобальные переменные и запустите программы запуска.  
  
- Возможные других потоков, создания и события загрузки модулей.  
  
- Событие точки входа, которое сигнализирует, что программа достиг основной точки входа, такие как **Main** или `WinMain`. Это событие не отправляется как правило, если DE присоединяет к программе, на котором уже выполняется.  
  
  Программно, DE сначала отправляет диспетчер отладки сеансов (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс, который представляет событие создания ядра, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , который представляет событие создания программы.  
  
  Эти события обычно следуют одна или несколько [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) события создания потоков и [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) события загрузки модулей.  
  
  Когда код загружены и готовы к запуску, но до выполнения любого кода, DE отправляет SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) событие завершения загрузки. Наконец, если программа не запущена, DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) запись точечное событие, сигнализации, что программа достиг основной точки входа и готов для отладки.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)