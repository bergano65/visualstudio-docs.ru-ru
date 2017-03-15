---
title: "Процессы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], обрабатывает"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Процессы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В терминах архитектуры отладчика, a **процесс**.  
  
-   Контейнер для набора служебных программ.  Она тесно аналогичн к процессу windows, который контейнер для набора потоков.  
  
-   Можно указать по имени, идентификатору или физическим идентификатором.  
  
-   Может перечислить все выполняющиеся программы \(и их потоки\).  
  
-   Позволяет описать, порт он выполняется внутри и компьютер, содержащего данный элемент.  
  
-   Позволяет создать одну или несколько программ, завершить все программы, он создает или вызвать программу остановить.  
  
-   Представляет  IDebugProcess2 интерфейс, который создается при запуске процесса.  Процесс запущен любым сеанс отладки \(SDM\) или диспетчер [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Пакет отладки может вложить отладчик \(DE\) для процесса путем вызова [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Это означает, что DE вложение ко всем возможным программам, запущенным в процессе, она может обработать.  Например, если среда CLR DE вложение в процесс, то вложение только к программам, выполняющих управляемый код.  
  
## См. также  
 [Programs](../../extensibility/debugger/programs.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка пакета](../../extensibility/debugger/debug-package.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)