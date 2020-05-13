---
title: Уведомление порта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738325"
---
# <a name="notify-the-port"></a>Уведомить порт
После запуска программы порт должен быть уведомлен следующим образом:

1. Когда порт получает новый узлы программы, он отправляет событие создания программы обратно в сеанс отладки. Событие несет с собой интерфейс, представляющий программу.

2. Сеанс отладки запрашивает программу для идентификатора движка отладки (DE), который может прикрепляться к.

3. Сеанс отладки проверяет, находится ли DE в списке допустимых DEs для этой программы. Сеанс отладки получает этот список из активных настроек программы решения, первоначально переданных ему пакетом отладки.

    DE должен быть в допустимом списке, иначе DE не будет присоединен к программе.

   В программном плане, когда порт впервые получает новый узлы программы, он создает интерфейс [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) для представления программы.

> [!NOTE]
> Это не следует путать `IDebugProgram2` с интерфейсом, созданным позже движком отладки (DE).

 Порт отправляет событие создания программы [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) обратно в диспетчер сессии отладки `IConnectionPoint` (SDM) с помощью интерфейса COM.

> [!NOTE]
> Это не следует путать `IDebugProgramCreateEvent2` с интерфейсом, который отправляется позже DE.

 Наряду с самим интерфейсом событий, порт отправляет интерфейсы [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)и [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) которые представляют порт, процесс и программу, соответственно. SDM вызывает [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) для того чтобы получить GUID DE которое может отладить программу. GUID был первоначально получен из интерфейса [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM проверяет, есть ли DE в списке допустимых DEs. SDM получает этот список из активных настроек программы решения, первоначально переданных ему пакетом отладки. DE должен быть в допустимом списке, иначе он не будет присоединен к программе.

 Как только личность DE известна, SDM готов прикрепить ее к программе.

## <a name="see-also"></a>См. также
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)
- [Прикрепление после запуска](../../extensibility/debugger/attaching-after-a-launch.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
