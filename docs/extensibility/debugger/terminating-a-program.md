---
title: Завершение работы программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712511"
---
# <a name="terminating-a-program"></a>Завершение программы
В следующем разделе описывается завершение одной программы с одним потоком.

## <a name="termination-process"></a>Процесс завершения

1. Параметр DE отправляет [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) с допустимым [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Параметр DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) с допустимым [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает [IDebugPortNotify2:: ремовепрограмноде](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) для удаления программы из порта.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
