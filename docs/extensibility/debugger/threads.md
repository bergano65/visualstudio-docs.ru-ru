---
title: Потоки | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 456ec81c5f39f533bddd58d0a9e4d9d5889f066d
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276638"
---
# <a name="threads"></a>Потоки
В архитектуре отладчик *поток*:  
  
-   — Основная единица вычислений. Поток последовательно выполняет свои инструкции в контексте одного вызова стека, перемещение из одной кодовой контекста в другую.  
  
-   Можно указать сам и программы, в котором он выполняется в. Потоки можно с именем, приостанавливать и возобновлять. Поток также можно перечислить его кадры стека связанные и, при некоторых условиях можно переместить на другой кадр стека. Учитывая контексте кадр стека, поток может возвращать его связан логический поток, если любой. Поток имеет свойства, такие как счетчик приостановок, который может быть отображен в **потоков** окно интегрированной среды разработки.  
  
-   Представленный [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнения программы.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)