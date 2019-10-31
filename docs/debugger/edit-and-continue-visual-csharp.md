---
title: Изменить и продолжить (визуальный C#элемент) | Документация Майкрософт
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5d54673ee46c594bd1a4bea2990d3b9bbe90ce1f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188190"
---
# <a name="edit-and-continue-visual-c"></a>Режим "Изменить и продолжить" (Visual C#)
 С помощью операции "Изменить и продолжить" для С# в процессе отладки можно вносить изменения в код в режиме приостановки выполнения. Изменения могут применяться без необходимости остановки и повторного запуска сеанса отладки. В режиме выполнения редактор исходного кода доступен только для чтения.

 Операция "Изменить и продолжить" поддерживает большинство изменений, которые могут потребоваться в ходе отладки, но существуют некоторые исключения. Дополнительные сведения см. в разделе [Поддерживаемые изменения кодаC# (и Visual Basic)](../debugger/supported-code-changes-csharp.md).

 "Изменить и продолжить" поддерживается в UWP в Windows 10, а также в приложениях x86 и x64, предназначенных для .NET Framework 4,6 или более поздних версий (.NET Framework является только версией для настольных компьютеров).

 > [!NOTE]
 > Неподдерживаемые приложения и платформы включают ASP.NET 5, Silverlight 5 и Windows 8.1.

 Когда операция "Изменить и продолжить" включена, поддерживаемые изменения применяются автоматически при использовании команд отладчика, таких как **Продолжить**, **Шаг**, **Задать следующий оператор**, или при выполнении вычисления функции в окне отладчика.

 Дополнительные сведения см. [в разделе как использовать команду "изменить и продолжитьC#" ()](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование режима "Изменить и продолжить" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Запись и отладка выполняемого кода XAML с помощью горячей перезагрузки XAML в Visual Studio](../xaml-tools/xaml-hot-reload.md)
