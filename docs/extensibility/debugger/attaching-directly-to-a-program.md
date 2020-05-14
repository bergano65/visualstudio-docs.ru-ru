---
title: Присоединение непосредственно к программе Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739260"
---
# <a name="attach-directly-to-a-program"></a>Прикрепите непосредственно к программе
Пользователи, которые хотят отладить программы в процессе, который уже запущен, обычно следуют этому процессу:

1. В IDE выберите команду **Debug Processes** из меню **«Инструменты».**

    Откроется диалоговое окно **Процессы**.

2. Выберите процесс и нажмите кнопку **"Прикрепить".**

    Появляется диалоговая коробка **Attach to Process,** в ней перечислены все двигатели отладки (DE), установленные на машине.

3. Укажите DEs для отладки выбранного процесса, а затем нажмите **OK**.

   Пакет отладки запускает сеанс отладки и передает ему список DEs. Сеанс отладки, в свою очередь, передает этот список вместе с функцией обратного вызова в выбранный процесс, а затем просит процесс перечислить свои запущенные программы.

   Программно, в ответ на запрос пользователя, пакет отладки мгновенно сеанс отладки менеджера (SDM) и передает список выбранных DEs к нему. Наряду со списком, отладка пакет проходит SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) интерфейс. Пакет отладки передает список DEs выбранному процессу, позвонив в [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Затем SDM вызывает [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) в порту для перечисления программ, работающих в процессе.

   С этого момента каждый отладка двигателя прилагается к программе точно так же подробно, как подробно в [Присоединение после запуска,](../../extensibility/debugger/attaching-after-a-launch.md)с двумя исключениями.

   Для повышения эффективности DEs, которые реализуются для совместного использования адресного пространства с SDM, сгруппированы таким образом, чтобы каждый DE имеет набор программ, к которым он будет прикрепляться. В этом случае [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) вызывает [IDebugEngine2::Прикрепите](../../extensibility/debugger/reference/idebugengine2-attach.md) и передает ему массив программ для присоединения.

   Второе исключение состоит в том, что события запуска, отправляемые DE, прикрепляющимися к уже запущенной программе, обычно не включают событие точки входа.

## <a name="see-also"></a>См. также
- [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
