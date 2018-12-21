---
title: (Создание исключения)-диалоговое окно отладчика Microsoft Visual Studio | Документация Майкрософт
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5609f87063d3b2852b6a45f7174cfd3db90a1ccd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062736"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Отладчик Microsoft Visual Studio (создание исключения) - диалоговое окно
В программе возникло исключение. Это диалоговое окно сообщает о типе вызванного исключения. В коде должна быть предусмотрена обработка этого исключения. Для обработки исключения можно выбрать один из следующих вариантов:  
  
 **Break**  
 Разрешает передать выполнение в отладчик. До приостановки выполнения обработчик исключения не вызывается. Если продолжить выполнение после приостановки, будет вызван обработчик исключения.  
  
 **Continue**  
 Разрешает продолжить выполнение, давая возможность обработчику исключения обработать исключение. Этот вариант недоступен для определенных типов исключений. Команда **Продолжить** разрешает продолжить выполнение приложения. В случае приложения в машинном коде это приведет к повторному вызову исключения. В случае управляемого приложения либо произойдет завершение программы, либо исключение будет обработано главным приложением.  
  
> [!NOTE]
>  После возникновения необрабатываемого исключения в управляемом коде продолжение выполнения невозможно. Выбор **Продолжить** после возникновения необрабатываемого исключения в управляемом коде приведет к остановке отладки.  
  
 **Игнорировать**  
 Разрешает продолжить выполнение без вызова обработчика исключения. Поскольку обработчик исключения не вызывается, это может привести к усугублению проблемы, включая возникновение новых исключений и ошибок. Этот вариант недоступен для определенных типов исключений.  
  
## <a name="see-also"></a>См. также  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)   
 [Рекомендации по обработке исключений](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Обработка исключений](/cpp/windows/exception-handling-cpp-component-extensions)