---
title: "Продолжение выполнения после исключения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9491eb19796c766d216af458ca122b1fa5032596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="continuing-execution-after-an-exception"></a>Возобновление выполнения после исключения
Когда отладчик приостанавливает выполнение из-за исключения, вы увидите **помощника по исправлению ошибок**, по умолчанию. Если вы отключили **помощника по исправлению ошибок** в **параметры** появится диалоговое окно, **помощник по исключениям** (C# или Visual Basic) или **исключения**  диалоговое окно (C++).  
  
 Когда **помощника по исправлению ошибок** отображается, можно попытаться устранить проблему, вызвавшую исключение.
  
## <a name="managed-and-native-code"></a>Управляемый и машинный код  
 В управляемом и машинном коде можно возобновить выполнение в том же потоке после необработанного исключения. **Помощника по исправлению ошибок** Очищать стек вызовов в точке, где возникло исключение.
  
## <a name="mixed-code"></a>Смешанный код  
 Если при отладке смешанного машинного и управляемого кода возникает необрабатываемое исключение, ограничения операционной системы не позволяют очистить стек вызовов. При попытке очистить стек вызовов с помощью контекстного меню отображается сообщение об ошибке, поясняющее, что при отладке смешанного кода отладчик не может вернуться в предыдущее состояние после возникновения необрабатываемого исключения.  
  
## <a name="see-also"></a>См. также  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)