---
title: "Управление программой | Microsoft Docs"
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
  - "Отладка элемента управления [отладка SDK] выполнения"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Управление программой
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отладка Visual Studio и продолжение работы пошагового выполнения, все следующие процедуры выполняются на уровне программы:  
  
-   Установка следующей выписку, т е параметра компьютер в следующей инструкции для выполнения в определенной среде кадра  
  
-   Выполнение, т е выйти из режима продолжит пошаговое выполнение  
  
-   Заход в следующей инструкции  
  
-   Продолжать работу с текущим режимом пошаговое выполнение  
  
-   Приостановка потоков, который содержит программа  
  
-   Возобновление потоков, который содержит программа  
  
> [!NOTE]
>  Чтобы просмотреть стек вызова реализуется на уровне потока.  Чтобы вывести данные кадра, просматривающего стек вызова для потока, необходимо реализовать все методы IEnumDebugFrameInfo2 интерфейс.  
  
## Методы управления программы  
 В следующей таблице показаны методы IDebugProgram2 необходимо реализовать для минимальной степени функциональной обработчик отладки \(DE\) и управление выполнения.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugProgram2:: Выполнить](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнять все потоки, который содержит программу из остановленного состояния.  Требуется для управления, выполнения.|  
|[IDebugProgram2:: Продолжить](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнять все потоки, который содержит программу из остановленного состояния.  Требуется для управления, выполнения.|  
|[IDebugProgram2:: Шаг](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в данном потоке.  Продолжает выполнять все другие потоки, который содержит программу.  Требуется для управления, выполнения.|  
  
 Для многопотоковых программ, необходимо также реализовать [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) метод и все методы   [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) интерфейс.  
  
## См. также  
 [Управление выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)