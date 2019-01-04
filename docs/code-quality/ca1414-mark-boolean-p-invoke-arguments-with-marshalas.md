---
title: CA1414. Пометьте логические аргументы P/Invoke атрибутом MarshalAs
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 31159ec2e90c96579940f276f1d0410cdf3dadb1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931441"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414. Пометьте логические аргументы P/Invoke с помощью MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод вызова неуправляемого объявление включает в себя <xref:System.Boolean?displayProperty=fullName> параметра или возвращаемого значения, но <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> параметра или возвращаемого значения не применяется атрибут.

## <a name="rule-description"></a>Описание правила
 Вызов метода доступа неуправляемого кода платформы и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Указывает поведение маршалинга, который используется для преобразования типов данных между управляемым и неуправляемым кодом. Типы много простых данных, такие как <xref:System.Byte?displayProperty=fullName> и <xref:System.Int32?displayProperty=fullName>, иметь единое представление в неуправляемом коде и не требуется указывать их поведение маршалинга; среда CLR автоматически предоставляет правильное поведение.

 <xref:System.Boolean> Тип данных имеет несколько представлений в неуправляемом коде. Когда <xref:System.Runtime.InteropServices.MarshalAsAttribute> не указан, по умолчанию, поведение для маршалинга <xref:System.Boolean> имеет тип данных <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Это 32-разрядное целое число, которое не во всех случаях. Логическое представление, которое требуется неуправляемый метод следует определить и сопоставить соответствующие <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool является тип bool Платформы Win32, которая всегда равна 4 байтам. Для C++ следует использовать значение UnmanagedType.U1 `bool` или другие типы 1 байт.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.Runtime.InteropServices.MarshalAsAttribute> для <xref:System.Boolean> параметра или возвращаемого значения. Задайте значение атрибута в соответствующую <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Даже если поведение маршалинга по умолчанию не подходит, когда явно задано поведение код повышает удобство поддержки.

## <a name="example"></a>Пример

В следующем примере показан неуправляемого кода методы, помеченные с соответствующим <xref:System.Runtime.InteropServices.MarshalAsAttribute> атрибуты.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Связанные правила
 [CA1901: Объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Укажите тип маршалинга для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)