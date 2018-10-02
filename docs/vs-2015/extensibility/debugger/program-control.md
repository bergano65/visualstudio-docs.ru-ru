---
title: Программы управления | Документация Майкрософт
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
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b213ee6eca5d132c663e86d6829b688952d150d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561667"
---
# <a name="program-control"></a>Элемент управления программой
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [управление программой](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-control).  
  
В Visual Studio отладки, все следующие пошагового выполнения и продолжая подпрограммы происходят на уровне программы.  
  
-   Установка следующего оператора, то есть Настройка компьютера следующей инструкции для выполнения в среде определенный кадр  
  
-   Выполнение, то есть продолжать выйти из режима пошагового выполнения  
  
-   Пошаговое выполнение следующей инструкции  
  
-   Продолжить текущий режим пошагового выполнения  
  
-   Приостановка потоков, содержащихся в программе  
  
-   Возобновление работы потоков, содержащихся в программе  
  
> [!NOTE]
>  Просмотр стека вызовов реализуется на уровне потока. Чтобы перечислить сведения о кадре, при просмотре стек вызовов для потока, должен реализовывать все методы объекта [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс.  
  
## <a name="methods-of-program-control"></a>Методы управления в программе  
 В следующей таблице показаны методы [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , должен быть реализован для модуля простейшей функциональной отладки (DE) и управление выполнением.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнение всех потоков, содержащихся в какой-либо программой в остановленном состоянии. Требуется для выполнения элемента управления.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнение всех потоков, содержащихся в какой-либо программой в остановленном состоянии. Требуется для выполнения элемента управления.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в данном потоке. Продолжает выполнение всех потоков, содержащихся в программе. Требуется для выполнения элемента управления.|  
  
 Для многопоточных программ, необходимо также реализовать [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) метод и все методы объекта [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)

