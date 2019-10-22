---
title: 'CA1414: Пометьте логические аргументы P-Invoke с помощью MarshalAs | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652689"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Объявление метода вызова неуправляемого кода включает параметр <xref:System.Boolean?displayProperty=fullName> или возвращаемое значение, но атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> не применяется к параметру или возвращаемому значению.

## <a name="rule-description"></a>Описание правила
 Метод вызова платформы обращается к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> указывает поведение маршалинга, используемое для преобразования типов данных между управляемым и неуправляемым кодом. Многие простые типы данных, такие как <xref:System.Byte?displayProperty=fullName> и <xref:System.Int32?displayProperty=fullName>, имеют одно представление в неуправляемом коде и не нуждаются в спецификации их поведения при маршалинге. среда CLR автоматически предоставляет правильное поведение.

 Тип данных <xref:System.Boolean> имеет несколько представлений в неуправляемом коде. Если <xref:System.Runtime.InteropServices.MarshalAsAttribute> не указан, то поведением маршалинга по умолчанию для <xref:System.Boolean> типа данных является <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Это 32-разрядное целое число, которое не подходит во всех обстоятельствах. Логическое представление, необходимое для неуправляемого метода, должно быть определено и сопоставлено с соответствующим <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool — это тип BOOL Win32, который всегда равен 4 байтам. UnmanagedType. U1 следует использовать для C++ `bool` или других 1-байтовых типов. Дополнительные сведения см. в разделе [маршалирование по умолчанию для логических типов](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.Runtime.InteropServices.MarshalAsAttribute> к параметру <xref:System.Boolean> или возвращаемому значению. Присвойте атрибуту значение соответствующего <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Даже если подходит поведение маршалинга по умолчанию, код проще поддерживать, если явно указано поведение.

## <a name="example"></a>Пример
 В следующем примере показаны два метода вызова неуправляемого кода, помеченные соответствующими атрибутами <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1901: объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [маршалирование по умолчанию для логических типов](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [, взаимодействии с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
