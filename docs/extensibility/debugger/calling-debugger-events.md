---
title: "Вызов события отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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