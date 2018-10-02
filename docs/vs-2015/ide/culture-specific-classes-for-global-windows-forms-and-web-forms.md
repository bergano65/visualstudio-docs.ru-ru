---
title: Классы, соответствующие определенному языку и региональным параметрам, для глобальных форм Windows Forms и Web Forms | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32de77cc098158f0775b3af378272542f8fd7d4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562964"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Классы, соответствующие определенному языку и региональным параметрам, для глобальных форм Windows Forms и Web Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для каждого языка и региональных параметров есть отдельное соглашение об отображении дат, времени, чисел, валюты и других сведений. Пространство имен <xref:System.Globalization> содержит классы, с помощью которых можно изменить отображение значений, зависящих от языка и региональных параметров, таких как <xref:System.Globalization.DateTimeFormatInfo>, **Calendar**, <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Использование параметра языка и региональных параметров  
 Но в большинстве случаев вы будете использовать параметр языка и региональные параметров, который можно хранится либо в приложении, либо в панели управления **Региональные параметры**. С его помощью можно автоматически определить соглашения во время выполнения и форматировать сведения соответствующим образом. Дополнительные сведения о настройке языка и региональных параметров см. в практических руководствах по [настройке языка и региональных параметров, а также языка и региональных параметров пользовательского интерфейса для глобализации Windows Forms](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) и [настройке языка и региональных параметров, а также языка и региональных параметров пользовательского интерфейса для глобализации веб-страниц ASP.NET](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Классы, автоматически форматирующие сведения в соответствии с настройками языка и региональных параметров, называются классами, зависящими от языка и региональных параметров. К некоторым методам, определяемым языком и региональными параметрами, относятся <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> и <xref:System.String.Format%2A?displayProperty=fullName>. Некоторые функции, зависящие от языка и региональных параметров (в языке Visual Basic): `MonthName` и `WeekDayName`.  
  
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
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)

