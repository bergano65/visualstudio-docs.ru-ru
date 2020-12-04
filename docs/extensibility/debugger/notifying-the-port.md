---
title: Уведомление порта | Документация Майкрософт
description: Узнайте, как будет уведомлен порт после запуска программы. Эта статья содержит подробное описание.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e9a838879e7c1eb590bb16cd12a6bf345de8031a
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606623"
---
# <a name="notify-the-port"></a>Уведомление порта
После запуска программы порт должен быть уведомлен следующим образом:

1. Когда порт получает новый узел программы, он отправляет событие создания программы обратно в сеанс отладки. Событие содержит интерфейс, представляющий программу.

2. Сеанс отладки запрашивает у программы идентификатор модуля отладки (DE), к которому можно присоединиться.

3. Сеанс отладки проверяет, находится ли параметр DE в списке разрешенных DEs для этой программы. Сеанс отладки получает этот список из параметров активной программы решения, изначально переданных ему пакетом отладки.

    Параметр DE должен находиться в списке допустимых, иначе он не будет присоединен к программе.

   Программным способом, когда порт впервые получает новый узел программы, он создает интерфейс [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) для представления программы.

> [!NOTE]
> Это не следует путать с `IDebugProgram2` интерфейсом, созданным позже модулем отладки (de).

 Порт отправляет событие создания программы [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) обратно в Диспетчер отладки сеансов (SDM) с помощью COM- `IConnectionPoint` интерфейса.

> [!NOTE]
> Это не следует путать с `IDebugProgramCreateEvent2` интерфейсом, который позже отправляется de.

 Вместе с интерфейсом событий порт отправляет интерфейсы [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)и [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , которые представляют порт, процесс и программу соответственно. Модель SDM вызывает [IDebugProgram2:: жетенгинеинфо](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) , чтобы получить идентификатор GUID для de, который может выполнять отладку программы. Идентификатор GUID изначально был получен из интерфейса [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

 Модель SDM проверяет, находится ли параметр DE в списке допустимых DEs. Модель SDM получает этот список из текущих параметров программы решения, изначально переданного ему пакетом отладки. Параметр DE должен находиться в списке допустимых или не будет присоединен к программе.

 После того, как удостоверение DE известно, модель SDM готова к присоединению к программе.

## <a name="see-also"></a>См. также
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)
- [Подключение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
