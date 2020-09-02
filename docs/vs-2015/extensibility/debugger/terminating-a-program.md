---
title: Завершение работы программы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421867"
---
# <a name="terminating-a-program"></a>Завершение программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже приведено описание завершения одной программы с одним потоком.  
  
## <a name="termination-process"></a>Процесс завершения  
  
1. Параметр DE отправляет [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) с допустимым [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Параметр DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) с допустимым [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает [IDebugPortNotify2:: ремовепрограмноде](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) для удаления программы из порта.  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
