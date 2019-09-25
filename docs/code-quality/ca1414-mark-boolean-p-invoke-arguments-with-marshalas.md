---
title: CA1414. Пометьте логические аргументы P/Invoke атрибутом MarshalAs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234673"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414. Пометьте логические аргументы P/Invoke с помощью MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Объявление метода вызова неуправляемого кода <xref:System.Boolean?displayProperty=fullName> включает параметр или возвращаемое значение <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> , но атрибут не применяется к параметру или возвращаемому значению.

## <a name="rule-description"></a>Описание правила
Метод вызова платформы обращается к неуправляемому коду и определяется с помощью `Declare` ключевого слова в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или. <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.MarshalAsAttribute>Задает поведение маршалинга, используемое для преобразования типов данных между управляемым и неуправляемым кодом. Многие простые типы данных, такие как <xref:System.Byte?displayProperty=fullName> и <xref:System.Int32?displayProperty=fullName>, имеют одно представление в неуправляемом коде и не нуждаются в спецификации их поведения при маршалинге. среда CLR автоматически предоставляет правильное поведение.

Тип <xref:System.Boolean> данных имеет несколько представлений в неуправляемом коде. Если параметр <xref:System.Runtime.InteropServices.MarshalAsAttribute> не указан, поведением маршалинга по умолчанию <xref:System.Boolean> для типа данных является <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Это 32-разрядное целое число, которое не подходит во всех обстоятельствах. Логическое представление, необходимое для неуправляемого метода, должно быть определено и сопоставлено с соответствующим <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool — это тип BOOL Win32, который всегда равен 4 байтам. UnmanagedType. U1 следует использовать для C++ `bool` или других однобайтовых типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, примените <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> к параметру или возвращаемому значению. Присвойте атрибуту значение соответствующего <xref:System.Runtime.InteropServices.UnmanagedType>значения.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Даже если подходит поведение маршалинга по умолчанию, код проще поддерживать, если явно указано поведение.

## <a name="example"></a>Пример

В следующем примере показаны методы вызова неуправляемого кода, помеченные <xref:System.Runtime.InteropServices.MarshalAsAttribute> соответствующими атрибутами.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Связанные правила
[CA1901 Объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101 Задание маршалирования для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)