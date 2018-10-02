---
title: 'CA1414: Пометьте логические аргументы P / Invoke с помощью атрибута MarshalAs | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5753affc1f635e322d17ea10617297d3ec71077a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591621"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1414: пометьте логические аргументы P / Invoke с помощью атрибута MarshalAs](https://docs.microsoft.com/visualstudio/code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas).

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод вызова неуправляемого объявление включает в себя <xref:System.Boolean?displayProperty=fullName> параметра или возвращаемого значения, но <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> параметра или возвращаемого значения не применяется атрибут.

## <a name="rule-description"></a>Описание правила
 Вызов метода доступа неуправляемого кода платформы и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Указывает поведение маршалинга, который используется для преобразования типов данных между управляемым и неуправляемым кодом. Типы много простых данных, такие как <xref:System.Byte?displayProperty=fullName> и <xref:System.Int32?displayProperty=fullName>, иметь единое представление в неуправляемом коде и не требуется указывать их поведение маршалинга; среда CLR автоматически предоставляет правильное поведение.

 <xref:System.Boolean> Тип данных имеет несколько представлений в неуправляемом коде. Когда <xref:System.Runtime.InteropServices.MarshalAsAttribute> не указан, по умолчанию, поведение для маршалинга <xref:System.Boolean> имеет тип данных <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Это 32-разрядное целое число, которое не во всех случаях. Логическое представление, которое требуется неуправляемый метод следует определить и сопоставить соответствующие <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool является тип bool Платформы Win32, которая всегда равна 4 байтам. Для C++ следует использовать значение UnmanagedType.U1 `bool` или другие типы 1 байт. Дополнительные сведения см. в разделе [маршалинг по умолчанию для логических типов](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.Runtime.InteropServices.MarshalAsAttribute> для <xref:System.Boolean> параметра или возвращаемого значения. Задайте значение атрибута в соответствующую <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Даже если поведение маршалинга по умолчанию не подходит, когда явно задано поведение код повышает удобство поддержки.

## <a name="example"></a>Пример
 В следующем примере показано два неуправляемого кода методы, помеченные с соответствующим <xref:System.Runtime.InteropServices.MarshalAsAttribute> атрибуты.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1901: объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Маршалинг по умолчанию для логических типов](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



