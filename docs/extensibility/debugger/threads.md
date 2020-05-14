---
title: Темы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712476"
---
# <a name="threads"></a>Потоки
В архитектуре отладчика *поток:*

- Является основной единицей вычислений. Поток последовательно выполняет свои инструкции в контексте одного стека вызовов, переходя от одного контекста кода к другому.

- Может идентифицировать себя и программу, в ней она работает. Потоки можно назвать, приостановить и возобновить. Поток также может перечислить связанные с ней кадры стека и при некоторых условиях может быть перемещен в другой кадр стека. Учитывая контекст кадра стека, поток может вернуть связанный с ним логический поток, если таковой имеется. Поток имеет свойства, такие как количество подтяжек, которые могут отображаться в окне **потоков** IDE.

- Представлен интерфейсом [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) обычно созданным движком отладки (DE) или виртуальной машиной в результате выполнения программы.

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Стек кадры](../../extensibility/debugger/stack-frames.md)
- [Двигатель debug](../../extensibility/debugger/debug-engine.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [Менеджер отладки сеанса](../../extensibility/debugger/session-debug-manager.md)
