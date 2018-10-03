---
title: Отправка событий запуска после запуска | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21b98fccac32b50e6aec643a7b69832e65d53dd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570249"
---
# <a name="sending-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отправки запуска события после запуска](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-startup-events-after-a-launch).  
  
Когда модуль отладки (DE), подключенного к программе, он отправляет ряд событий запуска сеанса отладки.  
  
 Следующие события запуска, отправляемые сеанса отладки.  
  
-   Событие создания ядра.  
  
-   Событие создания программы.  
  
-   Создание и события загрузки модулей потоков.  
  
-   Событие завершения загрузки, когда код будет загружен и готов к выполнению, а также перед выполнением любого кода  
  
    > [!NOTE]
    >  Когда это событие продолжает выполнение, инициализируются глобальные переменные и запустите программы запуска.  
  
-   Возможные других потоков, создания и события загрузки модулей.  
  
-   Событие точки входа, которое сигнализирует, что программа достиг основной точки входа, такие как **Main** или `WinMain`. Обычно это событие, не отправляется при DE присоединяет к программе, на котором уже выполняется.  
  
 Программно, DE сначала отправляет диспетчер отладки сеансов (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс, который представляет событие создания ядра, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , который представляет событие создания программы.  
  
 Обычно загрузка сопровождается одним или несколькими [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) события создания потоков и [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) события загрузки модулей.  
  
 Когда код загружены и готовы к запуску, но до выполнения любого кода, DE отправляет SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) событие завершения загрузки. Наконец, если программа еще не запущен, DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) запись точечное событие, сигнализации, что программа достиг основной точки входа и готов для отладки.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)

