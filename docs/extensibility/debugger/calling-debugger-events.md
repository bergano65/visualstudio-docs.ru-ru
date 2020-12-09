---
title: Вызов событий отладчика | Документация Майкрософт
description: События в сеансах отладки выполняются в определенном порядке. В этой статье приводится порядок вызова событий, происходящих в типичном сеансе отладки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 832b42e62731a087048b4aa50e19b74c408343c5
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914392"
---
# <a name="call-debugger-events"></a>События отладчика Call
События в сеансах отладки выполняются в определенном порядке.

## <a name="discussion"></a>Разговор
 Чтобы понять схему вызовов между модулем отладки (DE) и диспетчером отладки сеансов (SDM), ниже представлен порядок вызова событий, происходящих в типичном сеансе отладки.

1. [Присоединение и отсоединение программы](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)

3. [Завершение программы](../../extensibility/debugger/terminating-a-program.md)

4. [Создание точки останова](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Когда точка останова привязывается или становится непривязанной](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Ошибки точки останова](../../extensibility/debugger/breakpoint-errors.md)

7. [Достижение точки останова](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Удаление точки останова](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Вход в режим приостановки выполнения](../../extensibility/debugger/entering-break-mode.md)

10. [Пошаговое выполнение в режиме приостановки выполнения](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>См. также раздел
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
