---
title: Потоки | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712476"
---
# <a name="threads"></a>Потоки
В архитектуре отладчика *поток*:

- Является основной единицей вычислений. Поток последовательно выполняет свои инструкции в контексте одного стека вызовов, перемещая из одного контекста кода в следующий.

- Может идентифицировать себя и программу, в которой он выполняется. Потоки могут быть именованы, приостановлены и возобновлены. Поток также может перечислить связанные с ними фреймы стека, а при некоторых условиях можно переместить в другой кадр стека. При наличии контекста кадра стека поток может вернуть связанный логический поток, если он есть. Поток имеет свойства, такие как число приостановок, которые могут отображаться в окне **потоки** интегрированной среды разработки.

- Представляется интерфейсом [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения программы.

## <a name="see-also"></a>См. также раздел
- [Программы](../../extensibility/debugger/programs.md)
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)
