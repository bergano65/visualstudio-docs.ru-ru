---
title: CA1007. По возможности используйте универсальные объекты
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d7783bea936b04fcb600563dadea6a65ac5ef5e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236523"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007. По возможности используйте универсальные объекты

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Метод, видимый извне, содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName>, а включающая сборка предназначена для .NET Framework 2,0.

## <a name="rule-description"></a>Описание правила
Ссылочный параметр — это параметр, который изменяется с помощью `ref` ключевого слова (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Тип аргумента, передаваемый для ссылочного параметра, должен точно совпадать с типом ссылочного параметра. Чтобы использовать тип, производный от типа ссылочного параметра, необходимо сначала привести тип и присвоить переменной ссылочного типа параметра. Использование универсального метода позволяет передавать в метод все типы с ограничениями без предварительного приведения типа к типу ссылочного параметра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, сделайте метод универсальным и замените <xref:System.Object> параметр с помощью параметра типа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показана подпрограммы подкачки общего назначения, реализованная как неуниверсальные и универсальные методы. Обратите внимание, насколько эффективно перемещаются строки с помощью универсального метода по сравнению с неуниверсальным методом.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1005: Избегайте чрезмерных параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Не вкладывать универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Использование экземпляров универсальных обработчиков событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>См. также
[Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)