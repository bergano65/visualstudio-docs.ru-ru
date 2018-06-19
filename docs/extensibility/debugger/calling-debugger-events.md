---
title: Вызов события отладчика | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3960d464b1a6d44fb77eba23cd518fea1f2e5a39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100031"
---
# <a name="calling-debugger-events"></a>Вызов события отладчика
События в сеансы отладки, возникают в определенном порядке.  
  
## <a name="discussion"></a>Обсуждение  
 Чтобы понять шаблон вызовов между модуль отладки (DE) и диспетчера сеанса отладки (SDM), ниже представлены порядок вызова события, происходящие во время сеанса отладки обычно:  
  
1.  [Присоединение и отсоединение к программе](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Завершение программы](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Создание точки останова](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Если привязка точки останова или становится несвязанных](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Ошибки точки останова](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Достигнув точки останова](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Удаление точки останова](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Вход в режим приостановки](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Шаг с заходом в режиме приостановки выполнения](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)