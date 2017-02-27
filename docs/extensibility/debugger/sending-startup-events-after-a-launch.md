---
title: "Отправка события запуска после запуска | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "события запуска отладки [отладка SDK]"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Отправка события запуска после запуска
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Только обработчик отладки \(DE\) вложен в программе, она отправляет ряд событий запуска обратно к сеансу отладки.  
  
 Стартовые события, отправляемые обратно к сеансу отладки, включают следующее:  
  
-   Событие создания обработчика.  
  
-   Событие создания программы.  
  
-   События загрузки создания и модуля потока.  
  
-   Отправленное событие загрузки полное, когда код загружен и подготавливает для запуска, но до любой код выполняется  
  
    > [!NOTE]
    >  Когда это событие продолжено, инициализируются глобальных переменных и выполнить запускаемых процедур.  
  
-   Возможно, другие создание и модуль потока загружает события.  
  
-   Событие точки входа, которое сообщает, что программа достигала свою главную точку входа, например **Главная** OR  `WinMain`.  Это событие обычно не отправляется, если DE вложение в программу, которая уже запущена.  
  
 Программно, DE сначала отправляет сеанс отладки \(SDM\) диспетчер [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс, представляющий событие создания обработчика, за которым следует  [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), который представляет событие создания программы.  
  
 Это обычно за одним или несколькими [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) событиях создания потока и  [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) события загрузки модуля.  
  
 Если код загружен и подготавливает для запуска, но до любой код выполнения отправляет SDM DE IDebugLoadCompleteEvent2 событие загрузки полное.  Наконец, если программа еще не запущена, то DE отправляет IDebugEntryPointEvent2 событие точки входа, сигнализируя, что программа достигла свою главную точку входа и готова для отладки.  
  
## См. также  
 [Контроль выполнения](../../extensibility/debugger/control-of-execution.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)