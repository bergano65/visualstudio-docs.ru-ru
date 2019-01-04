---
title: Вызов событий отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4b97ddde0e7cdcd258a8549f588257d90a365a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857336"
---
# <a name="call-debugger-events"></a>Вызов событий отладчика
События в сеансы отладки, возникают в определенном порядке.  
  
## <a name="discussion"></a>Обсуждение  
 Для лучшего понимания схемы вызовы между модуль отладки (DE) и диспетчер отладки сеансов (SDM), Далее представлен порядок вызова события, происходящие в ходе обычного сеанса отладки:  
  
1.  [Присоединение и отсоединение к программе](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Завершение программы](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Создание точки останова](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Когда точка останова привязывается или становится отменить привязку](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Ошибки точки останова](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Попадание в точку останова](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Удаление точки останова](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Переход в режим приостановки выполнения](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Шаг с заходом в режиме приостановки выполнения](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)