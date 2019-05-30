---
title: (Создание исключения)-диалоговое окно отладчика Microsoft Visual Studio | Документация Майкрософт
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fd0035ca0764f3673e07b4e3289b87773c8349b
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261340"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Отладчик Microsoft Visual Studio (создание исключения) - диалоговое окно
В программе возникло исключение. Это диалоговое окно сообщает о типе вызванного исключения. В коде должна быть предусмотрена обработка этого исключения. Для обработки исключения можно выбрать один из следующих вариантов:

 **Break** разрешает выполнение переключиться в режим отладчика. До приостановки выполнения обработчик исключения не вызывается. Если продолжить выполнение после приостановки, будет вызван обработчик исключения.

 **По-прежнему** позволяет продолжить выполнение, давая возможность обработки исключения обработчика исключений. Этот вариант недоступен для определенных типов исключений. Команда **Продолжить** разрешает продолжить выполнение приложения. В случае приложения в машинном коде это приведет к повторному вызову исключения. В случае управляемого приложения либо произойдет завершение программы, либо исключение будет обработано главным приложением.

> [!NOTE]
> После возникновения необрабатываемого исключения в управляемом коде продолжение выполнения невозможно. Выбор **Продолжить** после возникновения необрабатываемого исключения в управляемом коде приведет к остановке отладки.

 **Игнорировать** позволяет продолжить выполнение без вызова обработчика исключения. Поскольку обработчик исключения не вызывается, это может привести к усугублению проблемы, включая возникновение новых исключений и ошибок. Этот вариант недоступен для определенных типов исключений.

## <a name="see-also"></a>См. также
- [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)
- [Рекомендации по обработке исключений](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Обработка исключений](/cpp/extensions/exception-handling-cpp-component-extensions)