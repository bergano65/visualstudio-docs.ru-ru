---
title: Режим "Изменить и продолжить" (Visual C#) | Документация Майкрософт
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
ms.openlocfilehash: 62411229acd2d2f8462984789037fc832dac09b8
ms.sourcegitcommit: 822e61c69514e9f564d37ba6ca6832ccf7fbc60d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421645"
---
# <a name="edit-and-continue-visual-c"></a>Режим "Изменить и продолжить" (Visual C#)
 С помощью операции "Изменить и продолжить" для С# в процессе отладки можно вносить изменения в код в режиме приостановки выполнения. Изменения могут применяться без необходимости остановки и повторного запуска сеанса отладки. В режиме выполнения редактор исходного кода доступен только для чтения.

 Операция "Изменить и продолжить" поддерживает большинство изменений, которые могут потребоваться в ходе отладки, но существуют некоторые исключения. Дополнительные сведения см. в разделе [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Режим "Изменить и продолжить" поддерживают приложения UWP в Windows 10, а также 86- и 64-разрядные приложения для классических платформ .NET Framework 4.6 или более поздних версий (платформа .NET Framework поддерживается только для настольных компьютеров).

 > [!NOTE]
 > Не поддерживают платформы Silverlight 5, Windows 8.1 и приложения для них.

 Когда операция "Изменить и продолжить" включена, поддерживаемые изменения применяются автоматически при использовании команд отладчика, таких как **Продолжить**, **Шаг**, **Задать следующий оператор**, или при выполнении вычисления функции в окне отладчика.

 Дополнительные сведения см. в разделе [Практическое руководство. использовать режим "Изменить и продолжить" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование режима "Изменить и продолжить" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Создание и отладка выполняющегося кода XAML с помощью горячей перезагрузки XAML в Visual Studio](../xaml-tools/xaml-hot-reload.md)
