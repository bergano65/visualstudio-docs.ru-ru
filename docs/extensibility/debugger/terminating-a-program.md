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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 729d37c36782cd1786124c94796f610931473f0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704895"
---
# <a name="terminating-a-program"></a>Завершение программы
В следующем разделе описаны завершение одной программы с одним потоком.

## <a name="termination-process"></a>Завершение процесса

1. Отправляет DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) допустимое [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) допустимое [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает метод [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) удаление программы из порта.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)