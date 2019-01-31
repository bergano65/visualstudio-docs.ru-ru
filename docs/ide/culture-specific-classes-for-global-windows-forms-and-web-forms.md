---
title: Классы, соответствующие определенному языку и региональным параметрам, для глобальных форм Windows Forms и Web Forms
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c311e9c79e4f2861b8b52852ff7bb9b0217bf22c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948041"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Классы, соответствующие определенному языку и региональным параметрам, для глобальных форм Windows Forms и Web Forms

Для каждого языка и региональных параметров есть отдельное соглашение об отображении дат, времени, чисел, валюты и других сведений. Пространство имен <xref:System.Globalization> содержит классы, с помощью которых можно изменить отображение значений, зависящих от языка и региональных параметров, таких как:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Использование параметра языка и региональных параметров

Используйте язык и региональные параметры, хранимые либо в приложении, либо в панели управления **Региональные параметры**. С их помощью можно определять соглашения во время выполнения и форматировать сведения соответствующим образом. Дополнительные сведения о настройке языка и региональных параметров см. в статье [Практическое руководство. Указание значений языка и региональных параметров (пользовательского интерфейса) для глобализации веб-страниц ASP.NET](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Классы, автоматически форматирующие сведения в соответствии с настройками языка и региональных параметров, называются классами, *зависящими от языка и региональных параметров*. К некоторым методам, определяемым языком и региональными параметрами, относятся
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Некоторые функции, зависящие от языка и региональных параметров (в языке Visual Basic): `MonthName` и `WeekDayName`.

Например, в следующем коде показано, как с помощью метода <xref:System.IFormattable.ToString%2A> форматировать денежные единицы для выбранного языка и региональных параметров.

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Если для языка и региональных параметров задано значение fr-FR, в окне вывода появится следующее:

`100,00`

Если для языка и региональных параметров задано значение en-US, в окне вывода появится следующее:

`$100.00`

## <a name="see-also"></a>См. также

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)