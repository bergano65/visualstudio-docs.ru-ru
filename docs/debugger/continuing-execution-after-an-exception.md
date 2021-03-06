---
title: Продолжение выполнения после исключения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7be214a950c8cc93d986f97834a848bd9ab824e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745650"
---
# <a name="continuing-execution-after-an-exception"></a>Возобновление выполнения после исключения
Когда отладчик прерывает выполнение из-за исключения, по умолчанию отображается **вспомогательное приложение исключения**. Если в диалоговом окне " **Параметры** " отключено средство **поддержки исключений** , появится помощник по **исключениям** (C# или Visual Basic) или диалоговое окно **исключения** (C++).

 Когда появится **Помощник по исключению** , можно попытаться устранить проблему, вызвавшую исключение.

## <a name="managed-and-native-code"></a>Управляемый и машинный код
 В управляемом и машинном коде можно продолжить выполнение в том же потоке после необработанного исключения. **Вспомогательный метод исключения** очищает стек вызовов до точки, в которой возникло исключение.

## <a name="mixed-code"></a>Смешанный код
 Если при отладке смешанного машинного и управляемого кода возникает необрабатываемое исключение, ограничения операционной системы не позволяют очистить стек вызовов. При попытке очистить стек вызовов с помощью контекстного меню отображается сообщение об ошибке, поясняющее, что при отладке смешанного кода отладчик не может вернуться в предыдущее состояние после возникновения необрабатываемого исключения.

## <a name="see-also"></a>См. также

- [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)