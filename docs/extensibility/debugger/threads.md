---
title: Потоки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9759536e1b27018a3361bbb723b4cde0f88269e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333661"
---
# <a name="threads"></a>Потоки
В архитектуре отладчик *поток*:

- — Основная единица вычислений. Поток последовательно выполняет свои инструкции в контексте одного вызова стека, перемещение из одной кодовой контекста в другую.

- Можно указать сам и программы, в котором он выполняется в. Потоки можно с именем, приостанавливать и возобновлять. Поток также можно перечислить его кадры стека связанные и, при некоторых условиях можно переместить на другой кадр стека. Учитывая контексте кадр стека, поток может возвращать его связан логический поток, если любой. Поток имеет свойства, такие как счетчик приостановок, который может быть отображен в **потоков** окно интегрированной среды разработки.

- Представленный [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнения программы.

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Отладка ядра](../../extensibility/debugger/debug-engine.md)
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)