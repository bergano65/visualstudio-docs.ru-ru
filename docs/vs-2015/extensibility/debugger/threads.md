---
title: Потоки | Документация Майкрософт
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
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8070107a1befab999f2edd47d32e25e84266b86d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562090"
---
# <a name="threads"></a>Потоки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [потоков](https://docs.microsoft.com/visualstudio/extensibility/debugger/threads).  
  
С точки зрения архитектуры отладчика **поток**:  
  
-   — Основная единица вычислений. Поток последовательно выполняет свои инструкции в контексте одного вызова стека, перемещение из одной кодовой контекста в другую.  
  
-   Можно указать сам и программы, она выполняется и можно с именем, приостанавливать и возобновлять. Поток также можно перечислить его кадры стека связанные и, при некоторых условиях можно переместить на другой кадр стека. Учитывая контексте кадр стека, поток может возвращать его связан логический поток, если любой. Поток имеет свойства, такие как счетчик приостановок, который может быть отображен в окне "Потоки" интегрированной среды разработки.  
  
-   Представленный [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнения программы.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)

