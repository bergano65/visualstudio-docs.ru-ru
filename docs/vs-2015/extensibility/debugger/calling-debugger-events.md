---
title: Вызов событий отладчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146403"
---
# <a name="calling-debugger-events"></a>Вызов событий отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

События в сеансах отладки выполняются в определенном порядке.  
  
## <a name="discussion"></a>Разговор  
 Чтобы понять схему вызовов между модулем отладки (DE) и диспетчером отладки сеансов (SDM), ниже представлен порядок вызова событий, происходящих в типичном сеансе отладки.  
  
1. [Присоединение и отсоединение программы](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [Запуск отладчика](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Завершение программы](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Создание точки останова](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Когда точка останова привязывается или становится непривязанной](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Ошибки точки останова](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Попадание в точку останова](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [Удаление точки останова](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Вход в режим приостановки выполнения](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Пошаговое выполнение в режиме приостановки выполнения](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Обработка исключений](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
