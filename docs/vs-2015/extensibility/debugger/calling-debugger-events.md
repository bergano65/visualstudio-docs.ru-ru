---
title: Вызов событий отладчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86c48d072baa53cf3f8ba0a6d903021e6c396afa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562433"
---
# <a name="calling-debugger-events"></a>Вызов событий отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вызов событий отладчика](https://docs.microsoft.com/visualstudio/extensibility/debugger/calling-debugger-events).  
  
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

