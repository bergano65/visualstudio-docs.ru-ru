---
title: Вызов событий отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b4a727b078d55227b557621b673ea39b36d790f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890922"
---
# <a name="call-debugger-events"></a>Вызов событий отладчика
События в сеансы отладки, возникают в определенном порядке.

## <a name="discussion"></a>Обсуждение
 Для лучшего понимания схемы вызовы между модуль отладки (DE) и диспетчер отладки сеансов (SDM), Далее представлен порядок вызова события, происходящие в ходе обычного сеанса отладки:

1. [Присоединение и отсоединение к программе](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)

3. [Завершение программы](../../extensibility/debugger/terminating-a-program.md)

4. [Создание точки останова](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Когда точка останова привязывается или становится отменить привязку](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Ошибки точки останова](../../extensibility/debugger/breakpoint-errors.md)

7. [Попадание в точку останова](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Удаление точки останова](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Переход в режим приостановки выполнения](../../extensibility/debugger/entering-break-mode.md)

10. [Шаг с заходом в режиме приостановки выполнения](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>См. также
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)