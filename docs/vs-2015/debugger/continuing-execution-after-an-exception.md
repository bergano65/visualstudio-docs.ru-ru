---
title: Возобновление выполнения после исключения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702258"
---
# <a name="continuing-execution-after-an-exception"></a>Возобновление выполнения после исключения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Когда отладчик приостанавливает выполнение из–за возникновения исключения, появляется диалоговое окно. Для Visual Basic или C# диалоговое окно Помощник по [исключениям](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) отображается по умолчанию. Для C++ вы увидите диалоговое окно старое **исключение** . Если вы используете Visual Basic или C#, но отключили **Помощник по исключениям** в диалоговом окне " **Параметры** ", появится диалоговое окно " **исключение** ".  
  
 Когда откроется диалоговое окно **Помощник по исключениям** или **исключение** , можно попытаться устранить проблему, вызвавшую исключение.  
  
## <a name="managed-code"></a>Управляемый код  
 В случае управляемого кода можно возобновить выполнение в том же потоке после необработанного исключения. **Помощник по исключениям** очищает стек вызовов до точки, в которой возникло исключение.  
  
## <a name="native-code"></a>Машинный код  
 В случае машинного кода С/С++ имеются две возможности:  
  
- Можно нажать кнопку **прервать** и попробовать устранить проблему. Находясь в режиме приостановки выполнения, можно очистить стек вызовов, щелкнув правой кнопкой мыши кадр в окне **стека вызовов** и выбрав в контекстном меню команду **очистить до этого фрейма** . При продолжении отладки диалоговое окно **исключения** снова появляется, если проблема не исправлена. В противном случае диалоговое окно **исключения** не появится.  
  
- Можно нажать кнопку **продолжить** , чтобы продолжить выполнение, не пытаясь устранить проблему. Диалоговое окно **исключения** появляется снова.  
  
## <a name="mixed-code"></a>Смешанный код  
 Если при отладке смешанного машинного и управляемого кода возникает необрабатываемое исключение, ограничения операционной системы не позволяют очистить стек вызовов. При попытке очистить стек вызовов с помощью контекстного меню отображается сообщение об ошибке, поясняющее, что при отладке смешанного кода отладчик не может вернуться в предыдущее состояние после возникновения необрабатываемого исключения.  
  
## <a name="see-also"></a>См. также:  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)
