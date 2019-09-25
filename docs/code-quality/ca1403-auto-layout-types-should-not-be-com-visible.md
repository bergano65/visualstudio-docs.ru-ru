---
title: CA1403. Типы с автомакетом не должны быть видимыми для COM
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234824"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403. Типы с автомакетом не должны быть видимыми для COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Видимый тип значения модели COM помечен <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> атрибутом, для <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>которого задано значение.

## <a name="rule-description"></a>Описание правила

<xref:System.Runtime.InteropServices.LayoutKind>типы макета управляются средой CLR. Макет этих типов может изменяться в разных версиях .NET, что приводит к нарушению работы клиентов COM, которые предполагают наличие определенного макета. Если атрибут не C#задан, то Visual Basic и C++ компиляторы указывают [LayoutKind. Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) для типов значений. <xref:System.Runtime.InteropServices.StructLayoutAttribute>

Если не указано иное, все открытые, неуниверсальные типы видимы для COM, а все типы, не являющиеся открытыми и универсальные, невидимы для COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. Включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` значением, а тип <xref:System.Runtime.InteropServices.ComVisibleAttribute> должен быть `true`помечен значением.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибута на [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) или [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)или сделайте тип невидимым для com.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан тип, нарушающий правило, и тип, соответствующий правилу.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1408 Не использовать двойное ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также

- [Квалифицировать типы .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)