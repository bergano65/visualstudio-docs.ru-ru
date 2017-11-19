---
title: "Потоки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 150e27c4b8df06784848829bfe713773cf9d48a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="threads"></a>Потоки
С точки зрения архитектуры отладчик **поток**:  
  
-   Является основной единицей вычисления. Поток последовательно выполняет его в контексте инструкции стека вызовов одного, перемещение из одной кодовой контекста в другую.  
  
-   Можно определить себя и программы, он работает и можно с именем, приостанавливать и возобновления. Поток также можно перечислить кадрах стека связанной и при некоторых условиях можно переместить на другой кадр стека. Заданном контексте кадр стека, поток может возвращать его связанный логический поток, если таковые имеются. Поток имеет свойства, такие как счетчик приостановок, который может быть отображен в окне "Потоки" интегрированной среды разработки.  
  
-   Представленный [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) интерфейс, обычно создаются с помощью модуля отладки (DE) или виртуальной машины, в результате выполнения программы.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)