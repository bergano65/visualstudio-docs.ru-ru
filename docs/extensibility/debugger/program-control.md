---
title: "Программы управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb69afe513010a7da4b4a85669bbc5f145f8dbc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="program-control"></a>Управление программой
В Visual Studio отладки, все следующие проверки и продолжением процедуры происходит на уровне программ.  
  
-   Установка следующего оператора, то есть Настройка компьютера следующей инструкции для выполнения в среде определенного кадра  
  
-   То есть выполнение, продолжение для выхода из режима пошагового выполнения  
  
-   Пошаговое выполнение следующей инструкции  
  
-   Продолжить текущий режим пошагового выполнения  
  
-   Приостановка потоков, содержащихся в рамках программы  
  
-   Возобновление работы потоков, содержащихся в рамках программы  
  
> [!NOTE]
>  Для просмотра стека вызовов реализуется на уровне потока. Чтобы перечислить сведения о кадре, при просмотре стек вызова для потока, необходимо реализовать все методы [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейса.  
  
## <a name="methods-of-program-control"></a>Методы управления в программе  
 В следующей таблице показаны методы [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , должен быть реализован как минимум функциональной отладчик (DE) и управление выполнением.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнение всех потоков, содержащихся в программе в остановленном состоянии. Требуется для управления выполнением.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнение всех потоков, содержащихся в программе в остановленном состоянии. Требуется для управления выполнением.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в данном потоке. Продолжает работу других потоков, содержащиеся в программе. Требуется для управления выполнением.|  
  
 Для многопоточных программ должны также реализовать [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) метод и все методы [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)