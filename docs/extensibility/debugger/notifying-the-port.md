---
title: Уведомление порта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b022cca2b69c8cb80b24fa34e3b020923cff4022
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689204"
---
# <a name="notify-the-port"></a>Уведомление порта
После запуска программы, порт должен быть уведомлен, следующим образом:

1. Порт, получив новый узел программы, он отправляет событие создания сеанса отладки. Событие несет с собой интерфейс, который представляет программу.

2. Сеанс отладки запрашивает программа для идентификатора модуля отладки (DE), которое можно присоединить к.

3. Сеанс отладки проверяет, находится ли DE включен в список допустимых DEs для этой программы. Сеанс отладки получает этот список из параметров активную программу решения, изначально переданные ему размер пакета отладки.

    DE должны находиться в список допустимых, иначе DE не будет присоединен к программе.

   Программным образом, когда порт сначала получает новый узел программы, он создает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для представления программы.

> [!NOTE]
>  Это не следует путать с `IDebugProgram2` интерфейса, созданного в более поздней версии ядром отладки (DE).

 Отправляет порт [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) события создания программы диспетчеру сеанса отладки (SDM) с помощью COM `IConnectionPoint` интерфейс.

> [!NOTE]
>  Это не следует путать с `IDebugProgramCreateEvent2` интерфейс, который отправляется DE позже.

 А также сам интерфейс событий, отправляет порт [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), и [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейсы, которые представляют порт, обрабатывать, и Программа, соответственно. Вызовы SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) для получения идентификатора GUID DE, который можно отлаживать программы. Идентификатор GUID, первоначально полученную из [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс.

 SDM проверяет, находится ли DE включен в список допустимых DEs. SDM получает этот список из параметров активную программу решения, изначально переданные ему размер пакета отладки. DE должны находиться в список допустимых, иначе он не будет присоединен к программе.

 После получения удостоверения DE SDM готовы присоединить ее к программе.

## <a name="see-also"></a>См. также
- [Запуск программы](../../extensibility/debugger/launching-a-program.md)
- [Присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)