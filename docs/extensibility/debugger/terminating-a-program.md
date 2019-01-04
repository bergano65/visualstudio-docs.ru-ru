---
title: Завершение программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28be8f34602a3a175c40d630463686f0ca99c919
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958856"
---
# <a name="terminating-a-program"></a>Завершение программы
В следующем разделе описаны завершение одной программы с одним потоком.  
  
## <a name="termination-process"></a>Завершение процесса  
  
1. Отправляет DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) допустимое [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) допустимое [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает метод [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) удаление программы из порта.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)