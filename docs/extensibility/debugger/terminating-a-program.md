---
title: "Завершение программы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "программы, событий завершения"
  - "отладка [пакет SDK для отладки], завершение программы"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Завершение программы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Следующее описание завершения одной программы с одним потоком.  
  
## Процесс завершения  
  
1.  DE отправляет [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) с разрешенным  [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) с разрешенным  [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 Интегрированная среда разработки переходит в режим конструктора.  Вызовы ядра отладки или среды выполнения [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) удалить программу от порта.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)