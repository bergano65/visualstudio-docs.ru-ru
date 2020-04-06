---
title: Вызов событий Debugger (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739165"
---
# <a name="call-debugger-events"></a>События отладки вызова
События в сеансах отладки происходят в определенном порядке.

## <a name="discussion"></a>Обсуждение
 Чтобы понять структуру вызовов между движком отладки (DE) и диспетчером отладки сеанса (SDM), следующий порядок вызовов событий, происходящих в типичном сеансе отладки:

1. [Прикрепление и отсоединение к программе](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)

3. [Прекращение программы](../../extensibility/debugger/terminating-a-program.md)

4. [Создание точки разрыва](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Когда точка разрыва связывается или становится неограниченной](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Ошибки точки разрыва](../../extensibility/debugger/breakpoint-errors.md)

7. [Попадание в точку останова](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Удаляние точки разрыва](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Ввод режима перерыва](../../extensibility/debugger/entering-break-mode.md)

10. [Переход в режиме перерыва](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Оценка выражения в режиме перерыва](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>См. также
- [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
