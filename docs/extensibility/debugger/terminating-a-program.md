---
title: Завершение программы | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: e1914d00af1eeda94ef1cf9129e637ce39306257
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276966"
---
# <a name="terminating-a-program"></a>Завершение программы
В следующем разделе описаны завершение одной программы с одним потоком.  
  
## <a name="termination-process"></a>Завершение процесса  
  
1.  Отправляет DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) допустимое [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) допустимое [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает метод [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) удаление программы из порта.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)