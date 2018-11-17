---
title: Завершение программы | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3bc26486db7cdc5f8a29477b4380041b506c4e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772915"
---
# <a name="terminating-a-program"></a>Завершение программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже приведено описание прекращения одной программы с одним потоком.  
  
## <a name="termination-process"></a>Завершение процесса  
  
1. Отправляет DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) допустимое [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) допустимое [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает метод [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) удаление программы из порта.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

