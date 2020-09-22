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
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842744"
---
# <a name="sending-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После присоединения отладчика (DE) к программе отправляет в сеанс отладки ряд событий запуска.  
  
 События запуска, отправляемые обратно в сеанс отладки, включают следующее:  
  
- Событие создания подсистемы.  
  
- Событие создания программы.  
  
- Создание потоков и события загрузки модулей.  
  
- Событие завершения загрузки, отправленное при загрузке кода и готовности к выполнению, но до выполнения любого кода  
  
  > [!NOTE]
  > Когда это событие продолжает возобновлению, инициализируются глобальные переменные и запускаются подпрограммы запуска.  
  
- Возможно, другие события создания потоков и загрузки модулей.  
  
- Событие точки входа, которое сигнализирует, что программа достигла своей основной точки входа, например **Main** или `WinMain` . Это событие обычно не отправляется, если DE подключается к уже запущенной программе.  
  
  Программным способом метод DE сначала отправляет диспетчеру отладки сеанса (SDM) интерфейс [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , представляющий событие создания подсистемы, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), представляющий событие создания программы.  
  
  Обычно за ним следуют одно или несколько событий создания потока [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) и события загрузки модуля [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
  Когда код загружается и готов к запуску, но перед выполнением любого кода, отсылает событие [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load. Наконец, если программа еще не запущена, параметр DE отправляет событие точки входа [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , предупреждая о том, что программа достигла основной точки входа и готова к отладке.  
  
## <a name="see-also"></a>См. также:  
 [Управление выполнением](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
