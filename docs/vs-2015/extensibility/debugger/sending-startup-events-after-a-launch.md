---
title: Отправка событий запуска после запуска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eeb378b09ffc3e12de8996d7feabbd20a4b40068
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991605"
---
# <a name="sending-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда модуль отладки (DE), подключенного к программе, он отправляет ряд событий запуска сеанса отладки.  
  
 Следующие события запуска, отправляемые сеанса отладки.  
  
- Событие создания ядра.  
  
- Событие создания программы.  
  
- Создание и события загрузки модулей потоков.  
  
- Событие завершения загрузки, когда код будет загружен и готов к выполнению, а также перед выполнением любого кода  
  
  > [!NOTE]
  >  Когда это событие продолжает выполнение, инициализируются глобальные переменные и запустите программы запуска.  
  
- Возможные других потоков, создания и события загрузки модулей.  
  
- Событие точки входа, которое сигнализирует, что программа достиг основной точки входа, такие как **Main** или `WinMain`. Обычно это событие, не отправляется при DE присоединяет к программе, на котором уже выполняется.  
  
  Программно, DE сначала отправляет диспетчер отладки сеансов (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс, который представляет событие создания ядра, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , который представляет событие создания программы.  
  
  Обычно загрузка сопровождается одним или несколькими [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) события создания потоков и [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) события загрузки модулей.  
  
  Когда код загружены и готовы к запуску, но до выполнения любого кода, DE отправляет SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) событие завершения загрузки. Наконец, если программа еще не запущен, DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) запись точечное событие, сигнализации, что программа достиг основной точки входа и готов для отладки.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
